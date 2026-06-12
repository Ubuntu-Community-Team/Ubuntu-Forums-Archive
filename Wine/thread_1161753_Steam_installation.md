---
title: "Steam installation"
date: 2009-05-17
forum: Wine
---

### Post by gavoby on 2009-05-17
Hi there I have downloaded steam but cant install it. I am using wine to install it but it says

gav@gav-desktop:~$ wine msiexec /i SteamInstall.msi
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:advapi:LookupAccountNameW (null) L"gav" (nil) 0x32f87c (nil) 0x32f880 0x32f874 - stub
fixme:advapi:LookupAccountNameW (null) L"gav" 0x12a990 0x32f87c 0x12bc20 0x32f880 0x32f874 - stub
err:msi:ITERATE_Actions Execution halted, action L"WiseStartup" returned 1627
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msi158d.tmp"
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msi3fa.tmp"

  and 'installation prematurely ended because of error'
 Ideas anyone?

---

### Post by asdfoo on 2009-05-17
> **gavoby said:**
> Hi there I have downloaded steam but cant install it. I am using wine to install it but it says

gav@gav-desktop:~$ wine msiexec /i SteamInstall.msi
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:advapi:LookupAccountNameW (null) L"gav" (nil) 0x32f87c (nil) 0x32f880 0x32f874 - stub
fixme:advapi:LookupAccountNameW (null) L"gav" 0x12a990 0x32f87c 0x12bc20 0x32f880 0x32f874 - stub
err:msi:ITERATE_Actions Execution halted, action L"WiseStartup" returned 1627
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msi158d.tmp"
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msi3fa.tmp"

  and 'installation prematurely ended because of error'
 Ideas anyone?


try with a clean prefix...

mv ~/.wine ~/.wine-old
msiexec /i SteamInstall.msi

---

### Post by gavoby on 2009-05-17
gav@gav-desktop:~$ mv ~/.wine ~/.wine-old
gav@gav-desktop:~$ msiexec /i SteamInstall.msi
wine: created the configuration directory '/home/gav/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d0259e8, overlapped 0x7d0259cc): stub

fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/gav/.wine' has been updated.
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"SteamInstall.msi"
 
this is what happened after i tried.

---

### Post by lightstream on 2009-05-17
where is the steam MSI file? From the looks of it, you are in your home directory - by default downloads are often saved to the desktop. Do **cd ~/Desktop** then try again.

---

### Post by gavoby on 2009-05-17
can you explain in detail im not really sure what you mean? im not too good at these things.
thanks

---

### Post by lightstream on 2009-05-17
The **cd** command is just to change directory - when you are on the command line (in Terminal), you always have a current directory, and it starts as being your home folder indicated by the tilde ~.

So when you open the Terminal, enter the following command to change your current directory to your Desktop folder:

```
cd Desktop
```

Then try to run the MSI as before:

```
msiexec /i SteamInstall.msi
```

Also what version of Ubuntu are you running - Hardy Heron or Jaunty Jackelope? And what version of wine are you running (type **wine --version** on the command line to find out), and how did you install it?

---

