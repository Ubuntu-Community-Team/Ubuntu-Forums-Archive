---
title: "How do I get Ubuntu not to prompt for a password?"
date: 2009-08-06
forum: Security
---

### Post by mayagamer on 2009-08-06
Ubuntu is so good.But when I dialed to net,when I opened the sources.list,when I mount a USB-hdd I must input a password.

I do not need security,I only need speed.

So what should I do?

---

### Post by Bölvaður on 2009-08-06
Install a different distro [SIZE="1"](for speed get Gentoo or Arch with lightweight desktop manager like fluxbox)[/SIZE] and only use the admin account. Make a script to enter your password on login.

But be truthful, is it really about speed or is it about lack of linux understanding by the user (like lets say... your grand parents) or just laziness?

The other option is to get to know your way around the system and learn to touchtype your own password, it doesnt really take any time at all to add sudo or even gksu in front of a program's name and enter your password... except if you have a proper password that is 100 characters long.

---

### Post by barnex on 2009-08-06
EDIT: it's better not to enable the root account.

---

### Post by Cheesemill on 2009-08-06
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by slakkie on 2009-08-06
Sure, tell people to go about the same way as MS. I never have to type in a password to mount a disk. Plug it in, automounts, done.

If I umount it and need it back, then yes, but unplugging/plugging it again does the trick.

Using the ROOT account is BAD for DAILY work. You don't need much permissions to go about in Linux, any default user can use a system if properly setup.

---

### Post by mayagamer on 2009-08-06
If it is for me , no problem.
But it is for my parents. They don't know anything of computer, except icq and news from web.
If they need to input password again and again, they will power off the PC.

Is there really no method to avoid inputting password in ubuntu?

---

### Post by rizman on 2009-08-06
I've been using ubuntu for about 3 months now and I never need to enter a password in daily usage. Only if I do some administrative tasks like using apt-get or whatever. I haven't had the need for using the root account and believe me, I already did a lot of poking around in system files.

The only password your parents will need is when logging in.

The first time you'll mount a disk, Ubuntu will ask for a password. However, their should be a checkbox saying "Remeber authentication" (or similar) check it and Ubuntu will remember the password for the disk. At least, that's how it works for an NTFS partition. Not sure about USB disks, but I'd guess it's the same.

You have to remeber that a Linux OS is not Windows. That's something you learn. The first few days of ubuntu were confusing for me too because I tried to do things the way it is done in Windows. But I quickly learned to adapt (hurray for the Command Line). Now, at work (windows machine), I'm already missing the bash.

Sorry, I disgressed a little bit :-)

---

### Post by slakkie on 2009-08-06
Yeah, don't run root commands.

---

### Post by sasho_zl on 2009-08-06
> **mayagamer said:**
> If it is for me , no problem.
But it is for my parents. They don't know anything of computer, except icq and news from web.
If they need to input password again and again, they will power off the PC.

Is there really no method to avoid inputting password in ubuntu?

They wouldn't need root privileges to run firefox or chat client..

---

### Post by mayagamer on 2009-08-06
> **rizman said:**
> I've been using ubuntu for about 3 months now and I never need to enter a password in daily usage. Only if I do some administrative tasks like using apt-get or whatever. I haven't had the need for using the root account and believe me, I already did a lot of poking around in system files.

The only password your parents will need is when logging in.

The first time you'll mount a disk, Ubuntu will ask for a password. However, their should be a checkbox saying "Remeber authentication" (or similar) check it and Ubuntu will remember the password for the disk. At least, that's how it works for an NTFS partition. Not sure about USB disks, but I'd guess it's the same.

You have to remeber that a Linux OS is not Windows. That's something you learn. The first few days of ubuntu were confusing for me too because I tried to do things the way it is done in Windows. But I quickly learned to adapt (hurray for the Command Line). Now, at work (windows machine), I'm already missing the bash.

Sorry, I disgressed a little bit :-)

I'm learn to use Ubuntu
But my parents don't want to learn , they only want ICQ and Web directly without any password.

by the way , I have many partition in 2 harddisks with scsi, every time my parents  startup computer, they must input password to mount them. And also to dial to Adsl mordem with password.

---

### Post by The Cog on 2009-08-06
> I have many partition in 2 harddisks with scsi, every time my parents  startup computer, they must input password to mount them. 
You should enter the details of these disks into /etc/fstab file so that they get mounted automatically at every boot. Editing that file will need a password of course, but afterwards they won't need to mount them by hand again.
> And also to dial to Adsl mordem with password.
I haven't had to dial with a modem with Linux for years, and don't remember how. But I'm sure if you make a separate post asking, someone will be able to tell you how to set up so a password isn't needed for this.

And...
You say you don't need security, then say you want to connect to the internet and browse the web. If you are connecting to the internet, then you **do** need security, whether you think so or not.

---

### Post by koenn on 2009-08-06
> **The Cog said:**
> 
You say you don't need security, then say you want to connect to the internet and browse the web. If you are connecting to the internet, then you **do** need security, whether you think so or not.
*especially* if it's computer-illiterate people like your parents who are using the computer while connecting to the internet

and you *definitely* don't want them to do that with root privileges

---

### Post by rookcifer on 2009-08-06
> **mayagamer said:**
> If it is for me , no problem.
But it is for my parents. They don't know anything of computer, except icq and news from web.

These are precisely the types of users who should NOT have admin access.  They need security.

---

### Post by rizman on 2009-08-06
> **mayagamer said:**
> I'm learn to use Ubuntu
by the way , I have many partition in 2 harddisks with scsi, every time my parents  startup computer, they must input password to mount them.

If those are NTFS partitions, this might help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

It explains how to permanently mount NTFS partitions without fooling around with fstab and without the need of a password every time you want to mount them.

---

### Post by asbesto on 2009-08-06
I had a thread closed because I request help about how to get rid of all those passwords confirmations by PolicyKit, considering that I'm on my own computer without any other user than me

:shock:

About some password confirmations and how to bypass them, there's an howto somewhere in this forum, about enabling a normal user to do stuff without have the same password asked again and again and again - HERE IT IS: 

[http://ubuntuforums.org/showthread.php?t=435906]("http://ubuntuforums.org/showthread.php?t=435906")

About the polkit, I noticed that simply adding the username on /etc/PolicyKit/PolicyKit.conf and maybe the wheel group can help shutting off all those unuseful and redundant requests. 

This has nothing to do with root login, that is to be avoided as hell, because is too dangerous at all.

---

### Post by aysiu on 2009-08-06
> **Cheesemill said:**
> [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
Yes, mayagamer--please read this link. It will answer all your questions.

---

