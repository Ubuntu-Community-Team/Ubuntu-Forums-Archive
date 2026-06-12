---
title: "how do i set up a simple telnet service for a friend to access"
date: 2008-05-24
forum: Server Platforms
---

### Post by CrinkElite on 2008-05-24
Hi folks I've recently been messing about with telnet and now I want to set up a simple telnet service on my machine to enable a trusted friend to remotely access/ftp files on my system.

 I am using Ubuntu gutsy and he's running winxp.

 It would be better if he could access the service using winxp's native telnet client. the service will not be permanent so security is not a major concern but it must require a username + password login.

also my machine is behind a home wireless network gateway. is there anything I should know about routing the connection. (netgear-wgt*** router)

thanks for reading and thanks in advance.

---

### Post by ivze on 2008-05-24
Search "telnet server" in Synaptic. 
But, may be, the man on XP install Putty (SSH client), which size is <1Mb. The matter is that SSH and SFTP work out-of-the-box in Ubuntu + security.

---

### Post by CrinkElite on 2008-05-24
thanks for the heads up. I already tried installing "telnetd" using the synaptic package manager but for some reason when I try to load it from the terminal i get

***@***-desktop:~$ telnetd
The program 'telnetd' can be found in the following packages:
 * inetutils-telnetd
 * krb5-telnetd
Try: sudo apt-get install <selected package>
bash: telnetd: command not found
***@***-desktop:~$ 

then i tried 

***@***-desktop:~$ sudo apt-get install telnetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
telnetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
***@***-desktop:~$ 


any ideas?

---

### Post by Steve413z on 2008-05-24
you should probably use SSH instead of Telnet, because SSH is encrypted, and just have him use "Putty" SSH client

using telnet is just asking for your computer to get hacked

---

### Post by ivze on 2008-05-24
You did sudo apt-get install telnetd and nothing works =) ?
Make sudo apt-get install openssh-server, and you will immediately have remote access to your box with the ability to log in as any regular user of the system.
This is another reason, why you should use ssh :) .

---

### Post by pdwerryhouse on 2008-05-24
> **CrinkElite said:**
> 
***@***-desktop:~$ sudo apt-get install telnetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
telnetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Ok, this means that telnetd is already installed. It runs from inetd - you can see what services are configured for that by looking at /etc/inetd.conf

inetd probably isn't running (or may not even be installed). You can install it with:

apt-get install openbsd-inetd

If it's installed already, and not started, then run it with:

/etc/init.d/openbsd-inetd start

And then presumably you'd want it to run every time you boot, so you can enable that with:

update-rc.d openbsd-inetd defaults

---

### Post by windependence on 2008-05-24
Just FYI, telnet is highly insecure. Everything is passed in plain text. You should use ssh instead.

-Tim

---

### Post by nix4me on 2008-05-24
I second the recommendation of using SSH.  And have him use Putty.  Putty is free download.

---

### Post by CrinkElite on 2008-05-25
Thanks for all the info. I'll probably go with the openSSH.

---

