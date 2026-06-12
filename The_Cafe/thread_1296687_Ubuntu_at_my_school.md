---
title: "Ubuntu at my school"
date: 2009-10-20
forum: The Cafe
---

### Post by Jekshadow on 2009-10-20
After an entire computer lab went down because Deep Freeze caused an infinite-boot loop with WinXP (They had to reinstall and reconfigure every one), I decided to try and pitch Ubuntu to my school. I showed them Ubuntu (via a nice Live CD) and at first they completely freaked out when they learned that it did not come with an antivirus (these are Windows sys admins, everything (including the firewall) runs Windows 2000/Server '03/XP). After a long explanation of why Ubuntu did not need an antivirus they were worried about user integration. They use LDAP and I explained that Ubuntu can use LDAP for user authentication. I also added on that they could lock down the desktop using Lockdown. By this point they seemed to be interested, but they insist on a Deep-Freeze like system. I tried to explain to them that the permissions system of Linux (and any other *NIX OS) makes it so you cant screw anything up unless you are root, or are in the /etc/sudoers file, but they refused to believe me/admit anything actually worked by default. I have thought of several systems and I would like some input on what should be best:

1) Mount /boot and / as read only, and mount /home as the user's directory of the file server (can FTP/SAMBA be used here?)

2) Have a basic startup script do verification checks on all files, and restore the ones that have changed (I was thinking MD5s)

---

### Post by JoshuaRL on 2009-10-21
Congrats man, well done to have them consider it!

> **Jekshadow said:**
> 
1) Mount /boot and / as read only, and mount /home as the user's directory of the file server (can FTP/SAMBA be used here?)


Well, you'd have to be able to execute.  Otherwise, OS no worky.  If you made a special fstab line that mounted a smb share, I'm pretty sure you could load /home from their.  But I'd have to try it to make sure.

But by far, an easier idea would be to use [Edubuntu](http://www.edubuntu.com/) and [LTSP.](https://help.ubuntu.com/community/UbuntuLTSP)

And you should make a big push for using Linux of some sort for any servers they run.  That is where you will get them comfortable with the OS.  That's the biggest hurdle, in my opinion.

---

### Post by Jekshadow on 2009-10-21
> **JoshuaRL said:**
> 
And you should make a big push for using Linux of some sort for any servers they run.  That is where you will get them comfortable with the OS.  That's the biggest hurdle, in my opinion.

That might be harder for the web servers, as a good portion of their website runs on ASP, know of any good ASP interpreters for Ubuntu?

As for the file server and proxy server, they might be more willing. Sometimes their proxy server can be really slow, even though you can get 5-6MB/s when using a protocol not proxied (such as FTP), and I think squid may help there, as they have also expressed interest in blocking by filetype (blocking executables). Also, I might recommend ProFTPd + OpenSSH + SAMBA for their file server, maybe they will even forward ports 21 and 22 to their file server so we can access the files from home. It would be possible to have OpenSSH auto chroot to their home directory so they cannot do anything but access their files from home.

A LTSP solution may work, if the applications are run client-side.

---

### Post by JoshuaRL on 2009-10-21
> **Jekshadow said:**
> That might be harder for the web servers, as a good portion of their website runs on ASP, know of any good ASP interpreters for Ubuntu?

As for the file server and proxy server, they might be more willing. Sometimes their proxy server can be really slow, even though you can get 5-6MB/s when using a protocol not proxied (such as FTP), and I think squid may help there, as they have also expressed interest in blocking by filetype (blocking executables). Also, I might recommend ProFTPd + OpenSSH + SAMBA for their file server, maybe they will even forward ports 21 and 22 to their file server so we can access the files from home. It would be possible to have OpenSSH auto chroot to their home directory so they cannot do anything but access their files from home.

A LTSP solution may work, if the applications are run client-side.

Not sure about ASP, haven't messed with it at all.  File and proxy is one area you want to hit, for sure.  Samba is sweet.  I've got an old P3 corporate desktop with a 500GB IDE slammed in there that's had over 100 days of cumulative uptime (stupid >1 minute power outages) with no problems.  Permissions are simple, via chown and chmod, and since you're using the Microsoft smb protocol, it doesn't really let you change permission levels on the server.  Pretty neat, if you have that figured out.

If you want to forward ports to the outside, I'd suggest making it non-standard ones.  For instance, you could port forward ssh traffic to the outside, use 22122 instead of 22 and just have inbound 22122 traffic go to the server on port 22.  Makes things more secure.  But otherwise, good idea.  Nothing like being able to troubleshoot from your pajamas.

---

### Post by Jekshadow on 2009-10-21
> **JoshuaRL said:**
> 
If you want to forward ports to the outside, I'd suggest making it non-standard ones.  For instance, you could port forward ssh traffic to the outside, use 22122 instead of 22 and just have inbound 22122 traffic go to the server on port 22.  Makes things more secure.  But otherwise, good idea.  Nothing like being able to troubleshoot from your pajamas.

I prefer 2222 for SSH, and 2121 for FTP, but that is always a good idea. As for the short power outages, get a cheap UPC for about $100, I have one and my debian server has been up for about ~200 days now, even though it only provides about an hour of power. Even when the power goes out, it stays up.

---

### Post by Pasdar on 2009-10-22
I always giggle on the inside when someone claims to be a computer expert and comes from some lame ICT study and at the same time can't tell me what Linux is/how to use it... has only learnt how to set windows policies in his years of study... doesn't anything about hardware, etc, etc, etc, etc....

---

### Post by davidshere on 2009-10-22
Students should also have access to and be familiar with Windows machines.  

When I was in high school in the early to mid 90s (before Windows 95), the school had many Macs and only two PCs.  Back then most people at the school were convinced that Macs were awesome and PCs were just stupid.  Little did they realize that most places of work had exclusively PCs, and the students coming out of the school would have no clue how to use them.  

Same conditions exist today.  Most businesses use Windows, not Ubuntu.  My workplace recently installed an ERP that only runs on Windows (Syspro), cementing our use of Windows for many years to come.  We had briefly considered a web-based ERP (Open For Buisiness) that would have allowed us to (hopefully) change most of our machines to Ubuntu, but we ended up not going that route.

---

### Post by openfly on 2009-10-22
yeah ubuntu needs way more than antivirus...

---

### Post by marco123 on 2009-10-22
> **openfly said:**
> yeah ubuntu needs way more than antivirus...

I know; how on earth will they be safe if "Spybot Search and Destroy" wont run on Linux. :)

---

