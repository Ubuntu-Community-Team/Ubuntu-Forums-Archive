---
title: "share folders with Windows XP"
date: 2008-01-31
forum: Virtualisation
---

### Post by Matt26 on 2008-01-31
is there anything that needs to be done to make an NTFS volume mounted in Ubuntu 7.10 accessible from a Windows XP Pro guest VM on VMware Workstation 6.0?  i just added 2 NTFS volumes in Ubuntu to my VM's shared folders.  i can see the icons for the volumes under Windows XP when i go into Network Places, VMware Shares etc, but they do not show up as folders, just icons that have no association to anything... i tried mapping a network drive to them but cannot access... i can ping the host Ubuntu within XP VM, and disabling firewall had no effect.  any suggestions?  thanks.

---

### Post by Matt26 on 2008-01-31
i just installed samba on Ubuntu which i thought might be required for this to work but i still can't access these volumes...

---

### Post by fjgaude on 2008-02-01
Do you get asked for a password when you click on the icons?

If so you have to enter your samba password in a Ubuntu terminal:

```
sudo smbpasswd -a yourloginname
```

That will get you going, I think.

---

### Post by Matt26 on 2008-02-01
no i don't get asked for a password- the icons are blank- in other words they are the same as icons with no file association (like when you try to open a file and it says it cannot find the application to open the file with, please choose from the list...) but when i try to open these files nothing happens at all- no prompts, no error messages.

i did find out how to access the folders via shares on Ubuntu with samba installed, and when i went to access the ubuntu machine from XP it was asking me for the username/password you mentioned- is this prompt looking for ubuntu or windows credentials?  and what does the command you mentioned actually do (sudo smbpasswd -a yourloginname)?  thanks.

---

### Post by reyhan on 2008-02-01
maybe you should install Winscp in your windows Xp 
you can get winscp grom here [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

---

### Post by fjgaude on 2008-02-01
The command places your Ubuntu password in the Ubuntu samba password place. While in Windows you are being asked for Ubuntu password.

You see your workgroup that is common in samba and in Windows, eh?

---

### Post by Matt26 on 2008-02-01
thanks i will try that out when i have a chance...

i see 2 different workgroups now under XP- HOME which is my Windows workgroup, and MSHOME, which is where i can access Ubuntu from- i'm guessing this is how samba shows a linux system under Windows, correct?

---

### Post by Matt26 on 2008-02-01
you mentioned that Windows is looking for the Ubuntu password when prompted- would this be the samba username/password or my regular user account?  i have tried both my regular account and root credentials and neither work.

---

### Post by fjgaude on 2008-02-01
If Windows is asking for a password it would be for the samba one, for to go from NTFS through ext3 filesystems you need samba.

You should use only one workgroup... it's the one you have in the shares setup in Ubuntu. Delete, erase the one you don't wish to use. Whichever you pick is what is used in both Windows and Ubuntu.

It's the password you gave when you did the smbpasswd command.

---

### Post by Matt26 on 2008-02-01
the volumes that i am accessing on Ubuntu are NTFS, so would samba still be necessary for this access?

---

### Post by fjgaude on 2008-02-01
As far as I know, yes. You go from Windows to Ubuntu then to Windows.

It should work. You are coming from a virtual OS in a real OS and that real OS is the one seeing the NTFS file system.

There is likely a way for you to have the mounted NTFS drive seen more directly by the virtual OS but I can't think of a way just now.

---

