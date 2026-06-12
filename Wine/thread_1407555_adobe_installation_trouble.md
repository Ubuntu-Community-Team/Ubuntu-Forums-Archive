---
title: "adobe installation trouble"
date: 2010-02-15
forum: Wine
---

### Post by selvavicto on 2010-02-15
i have tried install adobe photoshop cs4 i got the following result
  

selva@selva-desktop:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for selva: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
selva@selva-desktop:~$ wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
--2010-02-15 21:56:57--  [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
Resolving [www.kegel.com](www.kegel.com)... 
216.92.86.126
Connecting to [www.kegel.com|216.92.86.126|:80](www.kegel.com|216.92.86.126|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 142409 (139K) [text/plain]
Saving to: `winetricks.1'

100%[======================================>] 1,42,409    2.75K/s   in 74s     

2010-02-15 21:58:20 (1.89 KB/s) - `winetricks.1' saved [142409/142409]

selva@selva-desktop:~$ chmod +x winetricks
selva@selva-desktop:~$ ./winetricks msxml6 gdiplus gecko vcrun2005 ie6
err:winedevice:load_driver cannot open key L"\\Registry\\Machine\\System\\CurrentControlSet\\Services\\STM", err=0
err:winedevice:ServiceMain driver L"STM" failed to load
Executing wine msiexec /i /home/selva/.winetrickscache/msxml6_x86.msi
fixme:msi:MSI_OpenDatabaseW open failed r = 8003001e for L"C:\\windows\\temp\\msib53.tmp"
Note: command 'wine msiexec /i /home/selva/.winetrickscache/msxml6_x86.msi' returned status 91.  Aborting.
selva@selva-desktop:~$ sh winetricks msxml6 gdiplus gecko vcrun2005
err:winedevice:load_driver cannot open key L"\\Registry\\Machine\\System\\CurrentControlSet\\Services\\STM", err=0
err:winedevice:ServiceMain driver L"STM" failed to load
Executing wine msiexec /i /home/selva/.winetrickscache/msxml6_x86.msi
fixme:msi:MSI_OpenDatabaseW open failed r = 8003001e for L"C:\\windows\\temp\\msi744.tmp"
Note: command 'wine msiexec /i /home/selva/.winetrickscache/msxml6_x86.msi' returned status 91.  Aborting.
selva@selva-desktop:~$ 


ple help me..... will the screen be good in linux as in windows

---

### Post by Madspyman on 2010-02-16
The latest version of wine from the ppa has a bug that won't allow the CS4 installer to work, you have to install Photoshop using an older version of Wine 1.1.17, this tutorial should help, [http://freeasinbeard.org/post/105517877/running-photoshop-cs4-on-linux-using-wine]("http://freeasinbeard.org/post/105517877/running-photoshop-cs4-on-linux-using-wine").

After that you can upgrade back to the latest version of Wine and Photoshop should work fine.

---

