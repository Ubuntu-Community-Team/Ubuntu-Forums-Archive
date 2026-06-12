---
title: "vmware and root login"
date: 2008-10-16
forum: Security
---

### Post by poldie on 2008-10-16
I'm going crazy trying to log into vmware server beta 2 onto my Ubuntu 8.4.1 installation. .  I've installed it, hopefully successfully, following these instructions here:

[http://www.howtoforge.com/how-to-install-vmware-server-2-on-an-ubuntu-8.04-desktop](http://www.howtoforge.com/how-to-install-vmware-server-2-on-an-ubuntu-8.04-desktop)

It's asking me to log in as root, and I can't.  I've tried creating a password for root with:

sudo passwd root

and it doesn't object, but when I try and log in I get the message:

Login failed due to a bad username or password.

Which is what I get when I deliberately type the password in wrongly.

When I try logging in using the user I normally use (the one created by Ubuntu during install), it says:

You do not have permissions to login to the server.

Someone suggested that sudo passwd root won't work, and that I should try:

sudo -s
passwd root

but although this also lets me set the password, it results in no difference when I try and log into vmware.

My sudoers file, in case this is relevant, is as follows:

--------------------------------
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
--------------------------------

Am I missing some basic principle of Linux security here?  I'm a bit new to all this.

---

### Post by cdenley on 2008-10-16
Setting a root password is not recommended, but the command you posted should work. You were able to login as your regular user before, but after setting a root password, you can't login as anyone? Did you check caps lock and num lock?

---

### Post by poldie on 2008-10-16
> **cdenley said:**
> Setting a root password is not recommended, but the command you posted should work. You were able to login as your regular user before, but after setting a root password, you can't login as anyone? Did you check caps lock and num lock?

I'm just trying to log into vmware using root. I have no problems with my normal user (poldie) which I use to log into Ubuntu, and I have no problems using poldie's password when I install software etc.  Nothing has been broken by me installing vmware or trying to give a password to root.  I've never used root before, and I've never logged into vmware before. I only installed it a couple of days ago. I thought you had to use the root user to log into vmware.

---

### Post by cdenley on 2008-10-16
Sorry, I assumed you were trying to login to your virtual machine, not a vmware web console. I'm not familiar with that version of vmware, so I'm not sure how it's trying to authenticate or if it requires you to set a root password. You're probably not going to get any help setting a root password here.
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
However, you can see if a root password is set by trying to authenticate as root:
```

su

```
or by making sure there is not a "!" in your password hash
```

sudo getent shadow root

```

---

### Post by poldie on 2008-10-16
> **cdenley said:**
> Sorry, I assumed you were trying to login to your virtual machine, not a vmware web console. I'm not familiar with that version of vmware, so I'm not sure how it's trying to authenticate or if it requires you to set a root password. You're probably not going to get any help setting a root password here.
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
However, you can see if a root password is set by trying to authenticate as root:
```

su

```
or by making sure there is not a "!" in your password hash
```

sudo getent shadow root

```


I understand the point of that page you linked to.  I'm not trying to do anything dodgy, or which would appear to require special priviledges.  I don't understand why I need to be logged in as anything to use vmware - I just want to install XP, for those few remaining tasks I need Windows for.  I have no idea why I need to log in as root for that, but it seems I do.  

There's no ! in my hash.

When I type su it prompts for a password. When I enter the password of the account I'm logged in as, it says:

su: Authentication failure

but when I type in the password I've tried to assign to root, it says:

Your account has expired; please contact your system administrator
su: User account has expired

Although I'm not sure why it would be checking the root password when I'm logged in as someone else.  Just to make clear, previously I've never used the root account for anything at all.  If it's not created as part of the standard install then it wouldn't even have existed.  And I only want to use it because that's what I've read on that vmware page I linked to.  I can't believe I'm the only person to have this problem, but when I've looked for help, other people have been sorted by the sudo command I posted in my first comment.



Edit:  I seem to have fixed it.  It seems that my root account had expired. I unlocked it and changed the password and tried again, and it worked.  I'm not sure how repeatable this is going to be.  I understand the concerns about letting linux newbs like myself loose as root and would be happy to do this sort of thing some other way.

---

### Post by koenn on 2008-10-18
> **poldie said:**
>  ... and would be happy to do this sort of thing some other way.
what happens if you start vmware with sudo, like
```
sudo vmware
```
or change its launcher to execute 'gksu vmware' (without the qoutes)
?

---

### Post by poldie on 2008-10-19
> **koenn said:**
> what happens if you start vmware with sudo, like
```
sudo vmware
```
or change its launcher to execute 'gksu vmware' (without the qoutes)
?

I didn't start it with anything - it was accessed via a webpage using firefox.

I've given up on it.  When I finally got it working XP was sluggish and painful to use.  I can't use visual studio like that, as if I'm on another machine use remote desktop.  If using a virtual machine isn't exactly like using an actual machine then I have no use for them.  

I was juggling files for space too. I gave the vm 8 gigs but that's not enough for xp, vs and sql server.  So I formatted my drive, put XP on, then a fresh 8.4.1, and it's all looking good.  The point of using xp in a vm was to reduce my use of Windows to the bare minimum, but I can do that quite happily by 1) having a dual boot, so I have to stop what I'm doing to use xp, and 2) installing nothing in xp except what I need.  For everything else it'll be back into ubuntu.

Thanks for the help.

---

### Post by xoddam on 2008-10-23
I have a few points to add:

You don't need to be root to be the administrator user for VMware Server.  You can set the admin user to be yourself.  The setting is one of the prompts offered by vmware-config.pl, or you can actually edit it by hand in the file /etc/vmware/hostd/authorization.xml.  It may be possible to have more than one admin user if you add stanzas to this file, I haven't tried it.

*Only* if the admin user is root, do you need to unlock the root account and set a root password.  If it's a non-root user, you can type your own username and password into the vmware browser interface.

If you want to be able to use the desktop of your virtual machine with reponsiveness comparable to using a real machine, VMware Server 2 may not be the best software for you as it only provides a 'remote'-style admin and desktop interface, even for a user sitting at the host machine (for your purposes this is a step backwards from earlier versions of VMware Server).

You may find it possible to run Visual Studio directly on Linux using Wine or Crossover.  Or if that's too much hassle, other virtualisation solutions that are likely more responsive than VMware Server include Parallels, VirtualBox and of course VMware Workstation.

---

### Post by pkozlenk on 2008-12-12
Xoddam - your information helped me with the same issue. Not sure if it was the best thing to do but I edited the xml file you mentioned /etc/vmware/hostd/authorization.xml and changed what was shown as 'root' to my login name. Fixed the problem. I am using 8.10 and so far so good. Now that I am logged in - the fun begins...

---

### Post by bodhi.zazen on 2008-12-13
> **pkozlenk said:**
> Xoddam - your information helped me with the same issue. Not sure if it was the best thing to do but I edited the xml file you mentioned /etc/vmware/hostd/authorization.xml and changed what was shown as 'root' to my login name. Fixed the problem. I am using 8.10 and so far so good. Now that I am logged in - the fun begins...

This is a bit of an old thread ...

With Server 2.x (no longer beta) you can set the admin user during the installation (if you are paying attention, it is easy to over look).

---

### Post by digg1980 on 2009-09-11
Hi,

Although I am not sure how to enable remote root login with that specific version of VMware, I know that it has never been recommended to allow it. I have seen even articles on how to enable it on VMware ESX if that help you can find one at: 
**[VMware VI3 How to Enable Root Shell Access]("http://www.virtualizationteam.com/virtualization-vmware/vmware-vi3-root-shell-access.html")**


I still don't recommend you to do so with any version of VMware unless you really have to.

Enjoy,
Erick

---

