---
title: "Four questions"
date: 2007-04-29
forum: Server Platforms
---

### Post by karni on 2007-04-29
Hi, I posted this in the beginners forum [[here](http://ubuntuforums.org/showthread.php?t=427849)], but it was suggested that I repost it in this forum. I haven't used Ubuntu much, but I do have some basic experience of using a unix-like command line interface.

I am using Ubuntu 7.04 Server Edition; it was installed earlier today, and I am having a few minor teething problems.

Basically, I've created a new user called 'guy' by doing
```
sudo groupadd guy
sudo useradd -g guy guy
```

Now doing this doesn't actually create a home directory for guy (ie /home/guy) so I've tried doing it with my login (the one set up originally). So essentially I've cd'd to /home. Using mkdir guy doesn't work, cos it says I don't have permission. Using sudo mkdir guy doesn't tell me there's anything wrong, but it doesn't create the directory either. (Also it doesn't actually ask for my password.)

What am I doing wrong?



Next question:
Should I later wish to make guy an admin (ie allow him to use sudo) is it simply a case of
```
sudo usermod -G admin guy
```
?



Question 3:
I am going to be using SFTP to access the /var/www directory a lot. I generally use WinSCP for this. How do I tell WinSCP to tell my server that I'm an admin? At the moment I am being told 'access denied' for anywhere other than my home directory. Do I need to change the group that /var/www belongs to or something?



Final question: I've installed Ubuntu 7.04 Server Edition - does this by default only have a command line interface (as that's all I'm getting)? Is it possible to install a GUI on it? Just it would be a little more user friendly (also responsibility for this system gets passed on to a new person once a year, and it's quite possible that next year's person will never have used linux or unix before, and will thus be completely bewildered by the command line!)

Anyway, thanks for helping, I've recently moved from running Apache on WinXP to Ubuntu, and am a bit intimidated by it all! (Apologies if this is posted in the wrong place - please move it if it is!)

---

### Post by Nonno Bassotto on 2007-04-29
Q2) You can let guy be able to use sudo by adding him to the /etc/sudoers file. You cannot normally edit this file, for security reasons, but you can use the dedicated visudo. So you do something like
```

sudo visudo

```
Please type
```

man visudo

```
to learn what you need to type exactly in the file.

Q3) You should give guy the ownership of some subfolder of /var/www, for example /var/www/siteofguy. You can do this by typing
```

gksudo nautilus

```
You will have a file manager with root permissions. Browse to the appropriate folder and change ownership with right-click->Properties.

---

### Post by RichGuk on 2007-04-30
> **karni said:**
> 
Question 3:
I am going to be using SFTP to access the /var/www directory a lot. I generally use WinSCP for this. How do I tell WinSCP to tell my server that I'm an admin? At the moment I am being told 'access denied' for anywhere other than my home directory. Do I need to change the group that /var/www belongs to or something?


Simple way would be to just change the group of /var/www, I'd get someone else to confirm this not to sure how secure it is.

```
sudo chown root:admin /var/www
```


> **karni said:**
> 
Final question: I've installed Ubuntu 7.04 Server Edition - does this by default only have a command line interface (as that's all I'm getting)? Is it possible to install a GUI on it? Just it would be a little more user friendly (also responsibility for this system gets passed on to a new person once a year, and it's quite possible that next year's person will never have used linux or unix before, and will thus be completely bewildered by the command line!)

I'm unsure about GNOME, as I use KDE but yeah the server edition is just a CLI, you can install a GUI on top (which is what I do, as it comes with less kak that Kubuntu does). 

Install X first,

```
sudo apt-get install xorg xorg-dev
```

Then install KDE (someone else will have to tell you the GNOME packages, but its prob gnome-something).

```
sudo apt-get install kde-core kdm
```

And if you want if you want some of the Kubuntu looks, like its KDM theme then install 

```
sudo apt-get install kubuntu-default-settings
```

Then just install the extra stuff you'll want on top like synaptic, alsa, etc.

I hope this helps,

Rich

---

### Post by elst on 2007-05-01
You'll find the Debian replacements for the standard account management tools a bit friendlier - adduser, addgroup, deluser, and delgroup.

I'm not really sure why useradd etc. are still shipped. Perhaps it's for compatibility or standards compliance.

---

### Post by MJN on 2007-05-02
> **elst said:**
> I'm not really sure why useradd etc. are still shipped. Perhaps it's for compatibility or standards compliance.

It's because adduser etc is just a script which, besides doing lots of other helpful things, calls the useradd binary file and hence it still has to exist.

Mathew

---

### Post by elst on 2007-05-02
Thanks for the info - I'd just assumed it was a binary.

```
$ head /usr/sbin/adduser
#!/usr/bin/perl

# adduser: a utility to add users to the system
# addgroup: a utility to add groups to the system
my $version = "3.100";

# Copyright (C) 1997, 1998, 1999 Guy Maor <maor@debian.org>
# Copyright (C) 1995 Ted Hajek <tedhajek@boombox.micro.umn.edu>
#                     Ian A. Murdock <imurdock@gnu.ai.mit.edu>
# Bugfixes and other improvements Roland Bauerschmidt <rb@debian.org>
```

---

