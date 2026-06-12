---
title: "security updates in ubuntu server?"
date: 2009-07-08
forum: Server Platforms
---

### Post by bitpush on 2009-07-08
hi all,

i apologize for my completely noobish question, but i need some help understanding security updates for ubuntu server.

i have been running desktop versions of ubuntu for a few years now.  when i want to do updates in desktop, i can just click away and life is good!

in an effort to stop my dependence on a gui, i have recently installed jaunty server and am a bit lost on how to do my security updates.  when i log in, i see:


21 packages can be updated.
32 updates are security updates.


is it really just apt-get update, apt-get upgrade?  can i see and choose what is being installed?  what's the best way to do this?

thanks for your help.  i have searched, but obviously not enough.

---

### Post by Kareeser on 2009-07-08
Correct, apt-get is the utility you use to update your package list and upgrade your installed programs.

When you run "apt-get upgrade", a prompt will appear, detailing the packages to be updated, and what will happen when you say yes.

Give it a shot!

```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libtiff4 squirrelmail
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 736kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by gombadi on 2009-07-08
> 
is it really just apt-get update, apt-get upgrade? can i see and choose what is being installed? what's the best way to do this?


Yes it is that easy :-)

I use the -s command line option first to see what it will update and if all looks fine just remove the -s and let it go.

```

apt-get upgrade -s

```
then if all looks fine press the up arrow key, remove the -s and ...
```

apt-get upgrade

```

If I want to select some packages only I do an

```

apt-get install <packagename> <packagename> ... -s

```

then remove the -s when I am happy with what it is going to do.

---

### Post by Thirtysixway on 2009-07-08
To do kernel upgrades, do sudo apt-get dist-upgrade

---

### Post by bitpush on 2009-07-09
hi all,

thanks for your replies.  i tried the update/upgrade as:

```
sudo apt-get update
sudo apt-get upgrade
```but it didn't seem to work.  even with a lot of relevant repository output after the "update" command, i saw:

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-restricted-modules-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```and i still show the following when i log in:

```
21 packages can be updated.
32 updates are security updates.
```i'm not sure what to do here.  any ideas?

thanks again for your help!

---

### Post by KJKJava on 2009-07-22
Unless there is a better way to refresh the MOTD, rebooting got rid of that message for me.

---

### Post by cariboo on 2009-07-22
The MOTD changes for me on every time I log in with ssh. If you have no intentions of rebooting, I use:

```
sudo aptitude update && aptitude safe-upgrade
```

so that there are no surprises.

---

