---
title: "SSH open screen says packages can be updates, but won't"
date: 2010-05-22
forum: Server Platforms
---

### Post by CyberCowboy on 2010-05-22
I've got a lucid server that when I first ssh into it is telling me 

```
System load:    0.19               Memory usage: 0%   Processes:       154
  Usage of /home: 0.2% of 102.67GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

**154 packages can be updated.**
0 updates are security updates.
```

The line in bold is what concerns me.  If I do a 
```
sudo aptitude update
```
and then
```
sudo aptitude safe-upgrade
```

I get 
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

```

Why is it telling me I have updates and then not updating?

---

### Post by tr333 on 2010-05-23
Try running the following command and see what output you get:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by koenn on 2010-05-23
> **CyberCowboy said:**
> I've got a lucid server that when I first ssh into it is telling me 

```
System load:    0.19               Memory usage: 0%   Processes:       154
  Usage of /home: 0.2% of 102.67GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

**154 packages can be updated.**
0 updates are security updates.
```

The line in bold is what concerns me.  If I do a 
```
sudo aptitude update
```
and then
```
sudo aptitude safe-upgrade
```

I get 
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

```

Why is it telling me I have updates and then not updating?

maybe the 154 packages belong top a newer release and you'd need a release upgrade to get them, not simply an apt-get upgrade ?

or the 154 packages have dependencies that safe-upgrade won't handle

---

### Post by damo12 on 2011-04-22
I'm having a similar problem on a new server I've just built.  It is 10.04.2 64bit.  When I access it through SSH I get the message:

```
76 packages can be updated.
52 updates are security updates.
```

If I access it through Webmin I am told that:

```
No packages available to be updated were found
```

Webmin is scheduled to check for updates every hour and install any updates.

I have tried running:

```
sudo aptitude update
sudo aptitude upgrade
sudo apt-get update && sudo apt-get upgrade
sudo aptitude safe-upgrade
```

I have also left the server overnight in case the message needed to be updated overnight and have rebooted the server several times but each time I get the same message when I SSH into the machine.

Any help would be greatly appreciated.

Thanks

---

### Post by egpetrich on 2011-04-23
Something in a recent update may have dumped text into your /etc/motd.tail. It happened to me, and I have seen notes from other people describing the same symptoms.

Edit /etc/motd.tail and delete any text showing system information and update info. This information is generated each time you login by scripts in /etc/update-motd.d, so it shouldn't be in /etc/motd.tail. Right now, my file contains only:
```

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

```

---

### Post by damo12 on 2011-04-23
Thanks for the help.  I've deleted the text and it appears to have gone away.  I'll keep an eye on it over the next few days and let you know if anything changes.

Thanks again.

---

### Post by tgwaste on 2012-12-08
The problem here is apt-get update isnt doing what update-manager does apparently.

when you see those messages launch update-manager gui and I assure you those packages will be there ready to install.  They are not bogus messages.

so the real question is, what is the command line equivalent to do what update-manager does?

---

### Post by howefield on 2012-12-08
Old thread back to sleep.

---

