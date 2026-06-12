---
title: "OpenSSH server with samba"
date: 2011-08-06
forum: Server Platforms
---

### Post by camping147 on 2011-08-06
So I am sort of new to ubuntu but I was able to set up an ubuntu server VM  that has openssh package installed and that is what I am using it for. I am currently using it with rsa public key auth and I use it to connect back to my home network so I can rdp. I use putty and tunneling to connect via RDP using localhost. My question is that I have a home server using samba shares and I want to be able to access them with I connect via putty in much the same way I would locally i.e. //hostname. I was looking in the manual for sshd_config and there was an option for Gateway ports. I think that option is maybe what I am looking for. 
 
What I guess would be the ideal situation would be if you log in, you type in the hostname and the shares pop up and you can search just like if you were locally. How should I go about this. I dont care if anyone who connects has access to the shares: that is sorta of how i want it configured. 
 
Also would it be easier to just mount the samba file shares and use something like winscp to transfer the files that way?
 
Thank you.
 
I am running ubuntu 11.04

---

### Post by HermanAB on 2011-08-06
NFS is the easiest file sharing system.   Samba is the most difficult.

---

### Post by camping147 on 2011-08-06
I know nfs is easier but pretty much all my data that i would want to share is on a windows machine so that would take a long time to migrate all that over into linux.

---

### Post by headvampyre@hotmail.co.uk on 2011-08-06
Enough with all this crap about NFS. Its has its uses, but its far from useful in this scenario.

Try reading this: [http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php)

---

