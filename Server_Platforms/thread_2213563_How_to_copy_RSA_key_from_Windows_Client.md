---
title: "How to copy RSA key from Windows Client?"
date: 2014-03-27
forum: Server Platforms
---

### Post by ally2 on 2014-03-27
Howdy all

I have a Ubuntu 12.04 Server setup and I am in the process of securing the box I have generated the RSA using Putty Key generator on the Windows XP Client, The next question is simply how to I copy this key to the Ubuntu Server.

I log into it remotely by Putty via Windows XP

Many Thanks

---

### Post by Lars Noodén on 2014-03-27
WinSCP might do it.  But the key is text so if you are careful, all you need to do is copy and paste it into a file on the remote machine.  Just be sure that your method does not break any lines or add any characters.

---

### Post by ally2 on 2014-03-27
Hi there I am not to familiar with WinSCP will have to have a look at this, I was thinking initially of slight more long winded approach of  creating a SAMBA share and getting the file that way, But that kind of defeats the object as I initially want to be able to secure the server. 

Another method I thought of was formatting a USB stick as EXT3 Or 4 and mounting it on the server and getting the file that way.

Is WinSCP easy to use?

---

### Post by Lars Noodén on 2014-03-27
Others would have to answer about WinSCP, I don't use that OS.  FileZilla would also work.  

About the file transfer via sneakernet, that works too if your system can read EXT2, EXT3 or EXT4.  If you use FAT or NTFS then the [file permissions](https://help.ubuntu.com/community/FilePermissions) will get screwed up if it is the private key you are also transferring.  In that case you need to re-set the private key to 600 and preferably have in a directory that is 700.  But if you are just setting up key-based logins to the server you only need to transfer the public key over to the server.

---

### Post by steeldriver on 2014-03-27
Do you currently have password-based SSH access to the server? if so you can just copy from puttygen to the Windows clipboard, then right-click-paste it into the file over the existing connection - either by editing the authorized_keys file in nano/vim or just appending using cat

```
cat >> ~/.ssh/authorized_keys
<right-click-paste>
<Ctrl-d>

```

Remember to copy the key from the frame in the puttygen window (where it says "Public key for pasting into an OpenSSH authorized_keys file") NOT by saving the key to file (which will be in putty format)

---

### Post by ally2 on 2014-03-27
Yes I currently have password authentication setup I never realized you can paste information from a Windows Box to Ubuntu Server through Putty I will try the above

Many Thanks

---

### Post by ally2 on 2014-03-27
Mark this as solved people :) WinSCP awesome tool

Thank you for the heads up guys

---

