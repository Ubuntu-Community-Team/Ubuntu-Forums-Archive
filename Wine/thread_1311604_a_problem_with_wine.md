---
title: "a problem with wine"
date: 2009-11-02
forum: Wine
---

### Post by Aralon56 on 2009-11-02
Hi i seem to be having a problem with wine no matter what i try to install or do even typing 'wine help' i seem to get the same message every time.

wine: could not load L"C:\\windows\\system32\\help.exe": Module not found
aralon56@aralon56-desktop:~$ fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7e36e984, overlapped 0x7e36e968): stub

i am using Ubuntu 9.10 and wine 1.0.1 with wine tricks enabled

Any help would be gr8 :D :D 

Thanks

---

### Post by hikaricore on 2009-11-02
What are you trying to accomplish?

> wine help

 ^ Doesn't do anything and never has.

I'm not sure what those fixme messages are because I don't get them, but I suspect they're caused by dlloverides (winetricks).
Please let us know what you're attempting to do or we can't really assist you.

Most likely you should just start wine from scratch if everything crashes.
Test this to see if it works:

> wine ~/.wine/drive_c/windows/notepad.exe

---

### Post by Aralon56 on 2009-11-02
I am trying to install perfect world and i get the same message with perfect world as i did with 'wine help' :D i tried what u said with notepad as a test and this is what i got 

aralon56@aralon56-desktop:~$ wine ~/.wine/drive_c/windows/notepad.exe 
fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7e36e984, overlapped 0x7e36e968): stub

i have uninstalled wine and reinstalled and it still hasnt worked :D

---

### Post by hikaricore on 2009-11-02
But uninstalling and reinstalling doesn't remove your .wine directory.

I suggest starting from scratch and only installing the extra libraries you actually NEED /w winetricks.

[COLOR="DarkRed"]**Using this will completely remove anything you've installed through wine.**[/COLOR]
> sudo apt-get remove --purge wine
[COLOR="DarkRed"]**You have been warned.**[/COLOR]

---

### Post by Aralon56 on 2009-11-03
Thanks that was gr8 i installed the latest version and every thing seems to working :D

---

