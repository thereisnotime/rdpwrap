INSTALL of RDP Wrapper and Autoupdater
--------------------------------------

Automatically:

```powershell
# Install RDP Wrapper
New-Item -ItemType Directory -Path "$env:ProgramFiles\RDP Wrapper"
cd "$env:ProgramFiles\RDP Wrapper"
Invoke-WebRequest -Uri 'https://github.com/stascorp/rdpwrap/releases/download/v1.6.2/RDPWrap-v1.6.2.zip' -OutFile "$env:ProgramFiles\RDP Wrapper\rdpwrap.zip"
Expand-Archive -Path "$env:ProgramFiles\RDP Wrapper\rdpwrap.zip" -DestinationPath "$env:ProgramFiles\RDP Wrapper"
# Install autoupdater
Invoke-WebRequest -Uri 'https://github.com/asmtron/rdpwrap/raw/master/autoupdate.zip' -OutFile "$env:ProgramFiles\RDP Wrapper\autoupdate.zip"
Expand-Archive -Path "$env:ProgramFiles\RDP Wrapper\autoupdate.zip" -DestinationPath "$env:ProgramFiles\RDP Wrapper"
Start-Process "$env:ProgramFiles\RDP Wrapper\helper\autoupdate__enable_autorun_on_startup.bat"
Start-Process "$env:ProgramFiles\RDP Wrapper\install.bat"
# Restart RDP service
Restart-Service TermService - Force
# Try to reboot the PC if its not working
Write-Host "All done!"
```

Or manually:

1. Download "RDPWrap-v1.6.2.zip" [LINK#1](https://github.com/stascorp/rdpwrap/releases) or [LINK#2](https://sabercathost.com/e2bm/RDPWrap-v1.6.2.zip) and extract all files to the "%ProgramFiles%\RDP Wrapper" directory

    DO NOT use other directories to install/extract the RDP Wrapper files.
    USE ONLY the "%ProgramFiles%\RDP Wrapper" directory (normally C:\Program Files\RDP Wrapper)


2. Download [autoupdate.zip](https://github.com/asmtron/rdpwrap/raw/master/autoupdate.zip) and extract all files to the "%ProgramFiles%\RDP Wrapper" directory


3. To enable autorun of autoupdate.bat on system startup, run the following helper batch file as administrator:

    "%ProgramFiles%\RDP Wrapper\helper\autoupdate__enable_autorun_on_startup.bat"


4. Set in your Antivirus or Windows Defender an exclusion on the folder "%ProgramFiles%\RDP Wrapper" to prevent the deletion of RDP Wrapper files


5. Now you can use the autoupdate batch file to install and update the RDP Wrapper. Please run autoupdate.bat as administrator:

   "%ProgramFiles%\RDP Wrapper\autoupdate.bat"
