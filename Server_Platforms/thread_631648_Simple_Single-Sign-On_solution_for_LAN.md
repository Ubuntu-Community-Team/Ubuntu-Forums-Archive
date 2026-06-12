---
title: "Simple Single-Sign-On solution for LAN"
date: 2007-12-04
forum: Server Platforms
---

### Post by tofagerl on 2007-12-04
Is there any way to install a _simple_ (let me stress this: simple!) Single Sign On solution for a home network. Security is not an issue, only convenience. I work with several VMware machines on a daily (hell, hourly) basis, and I use the same username/password on all of them, yet I still have to login again and again and again... and again...

I've tried setting up an OpenLDAP server with Kerberos, but it is very complicated, and I am not that smart. A step-by-step solution or even a single package to install would be great :)

---

### Post by HermanAB on 2007-12-04
Configure Samba as a PDC.  See the Samba web site for the official howto.

---

### Post by crouton on 2007-12-05
I think tofagerl wants 'passthrough authentication' where you sign into your computer, and said authentication is forwarded to other services/machines.  Internet Explorer does this if you are in a domain and load a webpage from a domain server - it will try the current user's credentials first and only prompt if that attempt fails.  Samba as a PDC provides SSO, and you could certainly join physical/virtual machines to that domain, but you still have to sign-on to each machine.

If you're connecting via SSH, the following should help you out...

> **"http://www.fredshack.com/docs/openssh.html"]
Sessions with pass-through authentication

This method comes in handy when you usually connect to more than one machine during a session. The trick is to run applications which are automatically authenticated. This is achieved by a combination of the programs ssh-add and ssh-agent. man ssh-add reads: "The authentication agent must be running and must be an ancestor of the current process for ssh-add to work." Huh?  said:**
>  Enter ssh-add in the same terminal and the key will be loaded into memory, asking you for the password, if you have protected the key with one. Now you can start SSH sessions from this terminal without having to give any passwords, provided you set up the SSH 'config' file accordingly, which will be discussed on the next page.

If you want 'ssh-agent' to be the 'ancestor' of all virtual terminals in a session, add the command eval $(ssh-agent) to your personal X startup files, either '~/.xinitrc', if you are starting X from the console, or '~/.xsession', if you are booting directly into X. Then run ssh-add and all terminals you will open during this session will be authenticated. Other useful options are ssh-add -l which lists the key(s) currently kept in memory, and ssh-add -d which removes an identity from the system memory. 



Best of luck and please let us know if this helped, or if you found a different way of achieving your goal.

---

### Post by tofagerl on 2007-12-06
Yup, Crouton pretty much has it down. 

I worked it out by generating public keys from all my machines, and making a  mother-of-all authorized_keys file that I then copied to all my machines. 

I dread the day I have to make a new public key though...

---

