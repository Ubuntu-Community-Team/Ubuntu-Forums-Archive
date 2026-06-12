---
title: "[SOLVED] Huge PAM and reboot problem..."
date: 2008-03-17
forum: Server Platforms
---

### Post by FofBorg on 2008-03-17
Has anyone seen this problem before...

I have followed this tutorial [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760) in order to create a LDAP / SAMBA PDC server... Except some differences in drives setup, domain name and user name  eveything is identical, setupwise...

My problem is the following... After a reboot I am incapable of login into the system, much less get my windows machines to join the domain...

My SSH services and othe remote services refuse to start, so I'm stuck with the standard login but this one freezes up right after the password with no messages, except a timeout afer 60 seconds... And it get even worse if I try from an LDAP account, it freezes right after the username entry....


Now, here comes where is get really, really weird...

I have copied the nsswitch.conf with the LDAP entries into a file that I called nsswitch.conf.new...

This file thus contain this :

```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd: compat ldap
group: compat ldap
shadow: compat ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Before doing those modifications, the tutorial specified to create a backup file called nsswitch.conf.original... This file contains :

```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```


If I boot up in "safe mode" and copy the nsswitch.conf.original over nsswitch.conf like so:

cp /etc/nsswitch.conf.original /etc/nsswitch.conf

and then type "exit"...  I see the services start normaly and when O get the console, I can log with my Linux account, nothing unusual...

I log using my admin account and copy nsswitch.conf.new over nsswitch.conf, what is weird is that I can now log using both my LDAP and Linux account, has was intended...

getent passwd et getent group shows both the LDAP and Linux users and groups...

Not only this, but I can also join the NT Domain from Windows machine and log into the NT machines using the LDAP account (that was the intent of the exercise in the first place, see if I can get Windows out, one piece at a time :) )

If I exit the account and go back to the login prompt, I can login, no problem, with Linux or LDAP account

It works... Until I reboot the machine for whatever reason...  Then, I need to boot back in safe mode and redo the procedure...

At first I though the bind_policy was still on hard of something like that, but everything seems AOK...

I'm don't know where to look, cranking the log levels and debug to maximum was marginaly usefull as it just validated that my setup were good...

I'm flabergasted... I'm missing something obvious, I can feel it...

Anyone has a suggestion, or pointers as to what might be going wrong with my setups or machine ???

Could it be a bug of some type ???

I'm trying to get this situation resoved, but if all else fails, is there a way to add some cp commands to move the original file in place before the services starts and place the new file right after the service started up ???

I'm beginning to beleive in a ghost in the machine and I don't think this is a good thing in IT :lolflag:

---

### Post by braas on 2008-03-18
I'm experiencing someting like this.

None of PAM/LDAP enabeled services are starting up.
"getent passwd" does not show the LDAP entries.
And logging in on a local "/etc/passwd" account does not succeed eighter. (I did only wait for a few minutes though, so maybe eventualy it could succeed).

I booted the system in rescue mode, and after starting some daemons
I have partialy functional system again.

So now I've also started "the" LDAP tunnel by hand, and are able to login again with a local account, but getent still does not give me the LDAP accounts.

Furthemore I have to add, that I've experienced problems earlier, and it all started when we moved from starting an LDAP tunnel in /etc/inittab to an upstart script. 
Problems started when upgrading from feisty to edgy, bu I've managed to tackle that. This situation dos not give me any clues eighter though.

This is my /etc/nsswitch.conf
===================
#
# Example configuration of GNU Name
Service Switch functionality.
# If you have the `glibc-doc' and
`info' packages installed, try:
# `info libc "Name Service
Switch"' for information about this file.

passwd:         files ldap
group:          files
ldap
shadow:         files
ldap

hosts:          files dns
mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:           
db files

netgroup:       nis

=====================

---

### Post by FofBorg on 2008-03-18
In both case it smells like a bug...  But before filling something, I would love to have an opinion from a person more knowlegeable then I...

On another note, anyone knows where the PAM code is located ???  I'm having problems interpreting some of the log entries and would like to maybe add some of my own to try to figure out what is going on...

I though I knew what those were used for, but can someone add some information because what I have is pretty sketchy...

What I think I know is has follow...
nmbd is a NetBIOS name server that provide NetBIOS over IP naming services to clients...

smbd is the server daemon that provides filesharing and printing services to Windows clients

I use both of them but...

winbind is a service to resolve user and group information from Windows NT servers This package provides the winbindd daemon, which provides a service for the Name Service Switch.

Humm...

Those are definitions found over the net...  The problem is that winbind just appreared in my radar out of nowhere in examples over the net... I guess the question is, Should I use it ?

I'm actually using the Ubuntu server to act like a Windows NT/XP domain controler / authenticator... Is it considered a NT server for all intents and purposes ???

And what about Ldapsam Editposix ???  Where does it fit in the big picture ???

So many choices, so little time... :)

---

### Post by FofBorg on 2008-03-18
By the way Braas, try what I descrided in my post...

1) Boot in safe mode
2) Copy your nsswitch.conf into nsswitch.conf.new
3) Remove all reference to ldap in your nsswitch.conf and save it.
4) Copy your nsswitch.conf has nsswitch.conf.original
5) type "exit" from the safe mode, you should see your services start without any intervention... Exactly like it does on my machine...
6) When the logon prompt shows up, log into your administrative account
7) Copy your nsswitch.conf.new over nsswitch.conf
8) Do getent group

If you can see "Domain Admins" and other NT group, your are having EXACTLY the same problem I have...

You will authenticate against your LDAP without problem and will be able to authenticate your Windows users without problem or even  join new windows machine on your samba domain...

The Weirdest thing is that this setup will be fonctionnal until you reboot... that's the part that makes no sens in my book... Why ???

---

### Post by braas on 2008-03-18
In my case I have no business with samba. 
It's just PAM/LDAP/getent.

As I can get a partial operational system when I start my LDAP tunnel,
I suspect it has something to do with nssswitch.

I had found something like a quick fix by defining a timout on the LDAP
connection made by nsswitch, but I do not like that.

I'm not a noob with linux (10+ years of experience) but I can not find
any logging which indicates the source of this problem.

I do not suspect the PAM stack yet. For me it's upstart which is part
of the problem. But Upstart is not very elaborate int it's messages to :-(

PS: if I come to it anytime soon, I will describe the sequence of events which my machine has to go through.
that might provide a bot more insight....

---

### Post by rickyjones on 2008-03-18
Was that my guide?

You need to begin slapd before the system loggers. In /etc/rc2.d move the "SXXslapd" file to an S # before all the other init scripts. I believe "S09slapd" will work.

Reboot and it should be working now.

-Richard

---

### Post by braas on 2008-03-18
I will try your nsswitch proposition.

If it fails, I loose contact with the machine. So I want to take measures for a safe fall-back. I don't have direct access to the machine.

---

### Post by FofBorg on 2008-03-18
Yes Richard, I think it was yours...

Very helpful by the way, except for this small glitch :)

Might be a good idea to add the instruction on how to start the slapd service before the syslog one...


I'll try what you suggest and give you news back...

---

### Post by FofBorg on 2008-03-18
Success...

It works like a charm... Thanks a lot Richard...

I now have a fully working Windows Server (undercover Ubuntu Server 7.10 :lolflag: )

What a relief...

---

### Post by FofBorg on 2008-03-18
Braas,

Your problem seem to be a variant of mine... Try Richard's trick, it worked flawlessly, all services started without complaint and the login system now works flawlessly...

---

### Post by rickyjones on 2008-03-18
> **FofBorg said:**
> Success...

It works like a charm... Thanks a lot Richard...

I now have a fully working Windows Server (undercover Ubuntu Server 7.10 :lolflag: )

What a relief...

I'm glad it worked!

-Richard

---

### Post by steckelfisch on 2008-03-22
I'm testing right now.

My system got stuck in runlevel 'S' by-the-way.
I checked some scripts in /etc/init.d and came across this:

=====
root@hv1:/etc/rcS.d# /etc/init.d/libnss-ldap 
Usage: /etc/init.d/libnss-ldap {start|stop|restart|force-reload}

root@hv1:/etc/rcS.d# /etc/init.d/libnss-ldap restart
touch: kan touch &lsquo;/lib/init/rw/libnss-ldap.bind_policy_soft&rsquo; niet uitvoeren: Bestand of map bestaat niet

root@hv1:/etc/rcS.d# ls /lib/init/
mountall-net-fs           readlink                  vars.sh      
=====
(the part you do not understand is Dutch.)
The file /lib/init/rw/libnss-ldap.bind_policy_soft is not found, 

So it seems to me that the package nss-ldap is corrupted.

I replaced it with nss-ldapd. See what happens...

---

### Post by steckelfisch on 2008-03-23
And I've survived a reboot. 

The nsswitch.conf replaced without the ldap reference. Replacing the nsswitch.conf with the original one (with ldap) does not give me the LDAP accounts though. But now I have some space to investigate and test again.

---

### Post by sunithreddy on 2008-07-16
I have tried this on my ubuntu machine and it seemed to work. However on Centos5 which is my production machine the same problem reoccured. 
another question i have is, 
doesnt the line in nsswitch.conf w
passwd files ldap

mean first check on the local files and then try to reach the ldap server
Then why should the boot fail if the slapd process is not running.

---

