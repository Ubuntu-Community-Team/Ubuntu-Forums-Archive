---
title: "Used computer - I want to become the superuser"
date: 2010-08-18
forum: Security
---

### Post by mhundhammer on 2010-08-18
I am a beginner user of Ubuntu.  I just bought a netbook off craigslist and the seller was unable to deactivate his superuser status.  I want to either change the superuser password or upgrade my basic user profile to the superuser profile.  Is this possible?  When I tried using commands this is what popped up, 
matt@john-laptop:~$ sudo passwd root
[sudo] password for matt: 
matt is not in the sudoers file.  This incident will be reported.
matt@john-laptop:~$ sudo adduser username
[sudo] password for matt: 
matt is not in the sudoers file.  This incident will be reported.

P.S. I am Matt and the guy I bought the computer from is John
Help!?

---

### Post by Bachstelze on 2010-08-18
Boot a Live CD, mount root partition, edit group file with

```
sudo nano -w /mnt/etc/group
```

Add yourself to the admin group. Unmount. Reboot.

---

### Post by kerry_s on 2010-08-18
> **mhundhammer said:**
> I am a beginner user of Ubuntu.  I just bought a netbook off craigslist and the seller was unable to deactivate his superuser status.  I want to either change the superuser password or upgrade my basic user profile to the superuser profile.  Is this possible?  When I tried using commands this is what popped up, 
matt@john-laptop:~$ sudo passwd root
[sudo] password for matt: 
matt is not in the sudoers file.  This incident will be reported.
matt@john-laptop:~$ sudo adduser username
[sudo] password for matt: 
matt is not in the sudoers file.  This incident will be reported.

P.S. I am Matt and the guy I bought the computer from is John
Help!?

at boot hold the shift key to get in to the menu.
select the recovery mode(2nd option)
select root shell
type-> visudo
add your user to the sudoers
matt ALL=(ALL) ALL


it would be safer for you to do a clean install.

---

### Post by OpSecShellshock on 2010-08-18
If you bought it then the best thing to do would be to reinstall. I don't think you'll be able to create an installation image on USB without admin privileges, so you'll probably have to use another computer to do that.

---

### Post by alphaamanitin on 2010-08-18
Please note I am not accusing OP of anything.

I find these types of posts very interesting.  This is exactly what I would do if I got a password protected computer and wanted to access the data from it.  Of course if I wanted to do that I would probably use google and not a forum.  Anyway, I concur with OpSpecShellshock-just do a complete reinstall.  This way you will not have any of the other person's junk on the computer, think of all the junk programs, files, and other settings that you may not want and how much time you could spend trying to get rid of them all.

AlphaA

---

### Post by mailc on 2010-08-18
> **mhundhammer said:**
> I am a beginner user of Ubuntu. ....  I want to either change the superuser password or upgrade my basic user profile to the superuser profile.  
Help!?

As you were advised, make a new beginning.

This is what I would do:

- Use a USB stick (2GB) to make a live disk
- start the laptop with this USB stick 
- open a terminal and type: ' sudo shred -vfz -n 1 /dev/sdx '  (replace the x with the drive letter -- likely 'a' )
- let it shred 
- reinstall Ubuntu

Let us know

---

### Post by FuturePilot on 2010-08-18
> **OpSecShellshock said:**
> If you bought it then the best thing to do would be to reinstall. I don't think you'll be able to create an installation image on USB without admin privileges, so you'll probably have to use another computer to do that.

Actually you can. ;)

---

### Post by OpSecShellshock on 2010-08-18
Well there you go, then. No barriers to proper reinstallation.

[Go forth and download.]("http://www.ubuntu.com/netbook/get-ubuntu/download")

---

### Post by alphaamanitin on 2010-08-19
> **mailc said:**
> As you were advised, make a new beginning.

This is what I would do:

- Use a USB stick (2GB) to make a live disk
- start the laptop with this USB stick 
- open a terminal and type: ' sudo shred -vfz -n 1 /dev/sdx '  (replace the x with the drive letter -- likely 'a' )
- let it shred 
- reinstall Ubuntu


Is shredding it really necessary?  Would a new install wipe everything as well?  Particularly if you did a reformat?

AlphaA

---

### Post by tjktyler on 2010-08-19
Yes, shredding is necessary. Shredding is different that simply formatting; it mathematically destroys the data by flipping the individual bits that make up the filesystem many, many times, completely destroying the data. Formatting just makes the data unaccessable, but it could still be read. 
For most users, however, this is completely unnecessary. But out of respect for the previous owner, I would recommend it.

---

### Post by CharlesA on 2010-08-19
Personally I'd run dban on it then do a clean install.

I would never use a used machine with the same OS on it, as you never know what was done on it or if it was compromised.

---

### Post by pricetech on 2010-08-19
> **houndi said:**
> how to write bootable cd i want to write xp in my cd how can burn that to format my system

You won't, or at least shouldn't, find help with that anywhere on these forums.  Buy XP if you want XP.

And please don't hijack someone else's thread.

---

### Post by pricetech on 2010-08-19
Reinstalling is your best option.  You never know what the seller may have done, intentionally or otherwise, that might leave you with a less than optimum system.

A simple zero fill of the hard drive will clean it well enough for your install, but dban wouldn't hurt a thing either, and it's easy to download and burn the ISO to disk.  I think they still make a floppy version, though I haven't looked in a while.

---

### Post by mhundhammer on 2010-08-19
Thank you all so much for your help.  I tried to reinstall ubuntu on the netbook using the directions offered on the Ubuntu website.  After downloading the system off the internet I tried to download the operating system onto the an 8GB USB stick for reboot.  After 94% of the download had been completed an error message popped up that said [Errno 5] Input/output error.  After restarting the download onto my USB stick  two more times I gave up and deleted the Ubuntu operating system download.  While I didn't run into any administrative restraints (since I am still not the superuser on this operating system) I still couldn't make a USB boot drive.  Am I going to be able to do a reinstall with my 8GB USB stick?  Should I make partitions? Right now I'm following OP's advice and downloading Ubuntu netbook onto my macbook and then I'm going to try and download that onto the USB stick so I can reboot this thing with the USB.  Gosh this is frustrating.  Any answers would help.  Also, I'd like to dispel any worriers in the forum about this being a stolen netbook or that I'm trying to get information off of it.  First off, there is no information on it.  John, the guy i bought it from, never used it.  He just installed Ubuntu and forgot how to remove himself from being the superuser.  I want to use this computer for travel.  Nothing more, nothing less.   
Thanks again for all your help in getting this thing going for me.  I'm really excited about using a Linux operating system!

---

### Post by mailc on 2010-08-19
[mhundhammer]("http://ubuntuforums.org/member.php?u=1132490"),

nobody is accusing you of anything. I hope that you continue in your attempts and soon you'll see that it was well worth it.  I also had trouble at the beginning (and still have trouble at times)  but I just completely removed XP and am using only Ubuntu.

Please look at post # 8  - you have a link there for downloading your type of Ubuntu. First download the iso version and than write it to your USB.  See also the instructions.

To clean the netbook you can use various methods,   including the link for shred that I gave you. 

Let us know. Somebody will always be willing to help.

---

### Post by mailc on 2010-08-19
Again post#8 has a link for downloading ' ubuntu-10.04-netbook-i386.iso  '  .  

 Here is the link again:

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

But I just noticed that you're using a Mac  and in glancing over the instructions , it appears that they are a bit more complicated for a Mac  and the recommendation was made that a CD be used (I assume that you cannot use a CD).

So why not use your netbook with Ubuntu to download the iso file?    You do not need administrative passwords to make this download.  Then follow the simple instructions to write to your USB  (lclick on System --> Administration --> Startup Disk Creator )

---

### Post by mhundhammer on 2010-08-20
Thank you all so much.  I have successfully reinstalled Ubuntu on my netbook.  I did not end up shredding anything because the previous user had not done anything but install ubuntu and surf the web.  I am so stoked to be a part of such a supportive online community.  Open source or bust.  ;)

---

### Post by alphaamanitin on 2010-08-20
> **mhundhammer said:**
>  Also, I'd like to dispel any worriers in the forum about this being a stolen netbook

I do apologize if you thought I was trying to claim that you were, even though I said I was not.  As I stated, I assume anybody who actually was trying to steal data would not ask a reputable forum about it.  I merely wanted to use the topic to point out that we should at least keep thoughts like these in mind because some one may eventually try to use the forums that way and we should not be helping them.  

Again, sorry if you felt I was accusing you of anything.

AlphaA

---

