---
title: "Basic SSH server"
date: 2008-08-12
forum: Server Platforms
---

### Post by eXDee on 2008-08-12
Hey there,
Decided to try out xubuntu, since i don't have time to tweak fedora to exactly as i want anymore, and i wanted to switch to XFCE instead of KDE. I pretty much know basics, but mainly fedora related, since thats what i dived straight into.

Anyway, first task of my xubuntu box is to work as a ssh server that i can connect to from any windows computer through putty. 
i've installed openssh server and turned off root login, but i think it needs a bit more security.
I'll run it on a nonstandard port by the way of router port forwarding, so don't have to change that in the ssh config.

I've heard of using public/private keys and read the wiki, but i think i still need a bit of help. What i think would make a fairly good security layer would be to carry the private key on my usb flash drive with putty portable (windows), and then once authenticated with the key automatically by putty, i also have to input my password after. That way if loose my drive its still secure. The box won't be on 24/7, probably only during the day on select days.
Is this possible? Also im probably going to enable SSH port forwarding/tunneling.

Oh and one other thing, i've discovered windows wake on network activity works very well on the HTPC for clients to connect to mediaportal tv server. Any chance i can wake from S3 in xubuntu?
Cheers guys.

---

### Post by Lars Noodén on 2008-08-12
Actually the key itself would be locked with a pass phrase, so you need bot the key itself and the key's pass phrase to log in.  However, keep in mind that Windows is prone to keylogging (and someone could always put a keylogger dongle between the keyboard and the computer)

To generate the keys, use ssh-keygen
   [http://www.openbsd.org/cgi-bin/man.cgi?query=ssh-keygen](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh-keygen)

To use the keys with PuTTy try this:
   [http://www.ualberta.ca/CNS/RESEARCH/LinuxClusters/pka-putty.html](http://www.ualberta.ca/CNS/RESEARCH/LinuxClusters/pka-putty.html)

(I use SSH and SSHd a lot, but neither use nor condone the use of MS Windows in any context, especially networked environments, so you'll have to verify for yourself if the UAlberta page is accurate.  But at the least it points you to what you should be searching for on the net.)

(FWIW, having a non-standard port won't help all that much except against some primitive scans.  If the port's open, it'll be found.  If it's found, it will get identified...)

Depending on what you want to do on the server, you'll want to adjust the configuration:
[http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config)

Keep in mind the idea of least privilege.  You can set up several accounts for tasks that required vastly different levels of access.  Also, /etc/sudoers is your friend.

---

### Post by gtdaqua on 2008-08-12
If you are too much in to ssh securiute, consider'denyhosts'; it is an excellent package that will ban IPs that do brute-force attack via ssh. It can block at other ports and services as well. You can even configure to setup mail alerts once an attack has been blocked and the IP banned.

---

### Post by eXDee on 2008-08-12
Thanks.
Good idea on a different user, would it be possible to setup a user which all they can do is have ports forwarded, ie use putty to make it a SOCKS proxy so what i can have a secure tunnel?
When they login to SSH they cannot run any commands, just ports can be forwarded for use as a secure tunnel to the internet

Thanks for the reminder on denyhosts, i had that on fedora when my only protection to the main account was a password.

---

### Post by Lars Noodén on 2008-08-12
I've set up such accounts from time to time, allowing only port forwarding, or a limited set of programs.  

Make sure files and directories are not owned by that account, but that the necessary files can be read and (where necessary) written.  (See using restricted shells for ideas. e.g. rksh, rbash, etc.) The "ForceCommand" option in sshd_config is another possibility.  

Change the shell for that account to /bin/false or something equivalent.  

Use the options -f and -N:
  ssh -i foo_rsa -fN -L 1999:localhost:110   foo@10.10.10.11

AFAIK, there will probably be some problem with timeout unless you change sshd_config to allow idle connections.  Look at "ClientAliveCountMax" and "ClientAliveInterval" or "ForceCommand" for ideas.

However, all that will give you connections which you must break manually.  One time I chose to use a loop to keep the connection open and monitor when it was broken (by other factors):

e.g. 
    ssh -i foo_rsa -L 1999:localhost:110   foo@10.10.10.11 "while date;do sleep 180;done"

Jot down notes and try one change at a time, so that debugging is easier.


FWIW, Here's a brief overview of port forwarding:
[http://www.redhatmagazine.com/2007/11/06/ssh-port-forwarding/](http://www.redhatmagazine.com/2007/11/06/ssh-port-forwarding/)

---

