---
title: "VirtualBox 6.1 and Windows 10 shared folder issue"
date: 2023-01-22
forum: Virtualisation
---

### Post by wjmacfarland on 2023-01-22
I've installed the vbox guest additions and mounted a shared directory from Windows in VirtualBox 6.1

This directory appears as/in /media/sf-NAMEOFDIRECTORY I have set permissions from Ubuntu to 755 to access it.

However, I see permission denied when I try to access it.

I've tried sharing the directory from Windows 10 to "Everyone" but this does nothing to fix it. I've also enabled full control.

I've confirmed the guest additions are running in Ubuntu via lsmod.

I've also confirmed in the network and sharing center that I'm using a private network.

Under advanced settings for network and sharing, I have network discovery on as well as file and printer sharing.

Under all networks for network and sharing, I have password protected sharing disabled and public sharing enabled.

I've tried asking OpenAI's playground for help, but it doesn't provide any that I can understand.

Anyone have any idea?

---

### Post by howefield on 2023-01-22
Thread moved to the "*Virtualisation*" forum.

---

### Post by wjmacfarland on 2023-01-22
Thanks, I thought this would have been a general question =P~

---

### Post by TheFu on 2023-01-22
> **wjmacfarland said:**
>  
This directory appears as/in /media/sf-NAMEOFDIRECTORY I have set permissions from Ubuntu to 755 to access it.

However, I see permission denied when I try to access it. 

Please post the Unix permissions using the 'ls -la' command on that directory.
It has been almost a decade since I used vbox on a Windows host and I never used it on Linux VM hosts, but I to recall that a specific device had to be mounted inside Linux to access the host storage.  The vbox manual is online and very comprehensive.  My notes from 2008 say this:
> 
1.    Load the Client OS Extensions.
2.    Verify that `lsmod | grep vbox` shows the vboxfs module.
3.    Configure the extension to export a directory – I told it to share c:\Data from my Vista-64 host as “Data”
4.    `sudo mount     -t vboxsf      Data     /Data` – yes, the device is just the plain “Data” and it doesn’t show up in /dev like it should.


Beware that this type of sharing breaks some hostOS security and that file locking has never worked well with the vboxfs driver.  BTW, the mount command using "vboxsf" is isn't a typo.  The virtualbox team probably made a typo back in 2005 and never fixed it.  vboxfs ... "virtual box file system" makes sense, not vboxsf, which is correct.

---

### Post by wjmacfarland on 2023-01-22
ls -la (from the /media directory, as I cannot open the directory) shows:

drwxrwx---  1  root  vboxsf  8192  Jan  22  10:05  sf_static_cms_builder

I'm fine with things being a little less secure as I'm relying on the security of my network and Windows installation.

I had to manually type this in because bi-directional clipboard doesn't work either. Probably for the same reason...

---

### Post by TheFu on 2023-01-22
```
drwxrwx--- 1 root vboxsf 8192 Jan 22 10:05 sf_static_cms_builder
```
shows the problem.  Only root and members of the vboxsf group can access that storage.  Normal Unix permissions always apply, so you need to force the owner to be whatever you like, same for the group.  If you like, you could allow read-only access by using a
```
sudo chmod 775 sf_static_cms_builder
```
This doesn't change anything inside that directory, so the permissions inside there would need to matter too.

For foreign file systems, I have doubts that chmod will work. Mount options are usually the way to control foreign file systems link NTFS or exFAT when directly mounted.  I don't have any clue what virtualbox does/required.  Again the virtualbox manual is online and there should be a chapter about this.  Did you review that?  [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

If the guest additions aren't working, it could be due to a new kernel. Reinstalling the guest additions is required whenever a new kernel is updated. In theory, dkms would do that automatically, but if it doesn't, manually reinstalling them could work.

---

### Post by Morbius1 on 2023-01-22
> **wjmacfarland said:**
> ls -la (from the /media directory, as I cannot open the directory) shows:

drwxrwx---  1  root  vboxsf  8192  Jan  22  10:05  sf_static_cms_builder

I'm fine with things being a little less secure as I'm relying on the security of my network and Windows installation.

I had to manually type this in because bi-directional clipboard doesn't work either. Probably for the same reason...
I'm getting confused here. Are you a member of the vboxsf group?

Run this command to find out:
```
id
```
If not add yourself:
```
sudo gpasswd -a $USER vboxsf
```
Then logoff ( the Linux vbox guest ) and log in again.

---

### Post by wjmacfarland on 2023-01-22
Thanks! This fixed it!

---

### Post by TheFu on 2023-01-23
Nice, elegant solution from Morbius1.

If SOLVED, please mark this thread as SOLVED using the "Thread Tools" button near the top.  That helps the community greatly, especially those seeking answers.

---

### Post by wjmacfarland on 2023-01-23
Thanks, it's marked now.

---

