---
title: "Encrypted home dir and /etc/fstab mount"
date: 2012-04-24
forum: Security
---

### Post by paulwall on 2012-04-24
Hello,
 
I have a laptop with an encrypted home directory and a shared folder on my synology NAS to mount on boot automatically.
 
**```
/etc/fstab (/usr/.creds)
```**
If I setup this shared folder to be mount in /etc/fstab (credentials in /usr/.creds) it works.
 
**```
/etc/fstab (/home/paul/.creds)
```**
If I setup this shared folder to be mount in /etc/fstab (credentials in /home/user/.creds) it won't work because the directory is encrypted until login and therefore the .creds can't be read.
 
My question is now.. If I place the .creds in /usr folder, the password can be read from this file if you place the HDD in another computer, or not?
 
I looks to me as the file is better placed in encrypted home directory?
 
What about a script to be run after login to mount this share? But to mount a share you need root permissions.
 
```
sudo gnome-schedule
``` and run the script on reboot would work but how to wait until the user is logged in? Currently used sleep 60 in script, but what if the user log's in after 2min?
 
What I can do.. but what won't work as I want ;)
1) Run a script after login without root permissions (cant mount share)
2) Run a script after reboot with gnome-schedule / sleep 60 in script (wont work on every case)
 
Please someone can help me out?

---

### Post by paulwall on 2012-04-25
plz anyone :idea:

---

### Post by bodhi.zazen on 2012-04-25
It does not really matter where you put the file, if you reference it in fstab, the file has to be decrypted to mount the share.

And if it has to be decrypted, then the location is irrelevant.

You can put it in /etc/.fstab 

Regardless of location, file should be owned by root , permissions of 400

If you *must* have it encrypted, put it on /etc/.fstab , encrypt it with gpg, and decrypt with a script that runs at login.

---

