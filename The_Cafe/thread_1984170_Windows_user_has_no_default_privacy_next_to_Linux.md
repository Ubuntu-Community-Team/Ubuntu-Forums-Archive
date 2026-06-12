---
title: "Windows user has no default privacy next to Linux"
date: 2012-05-21
forum: The Cafe
---

### Post by black veils on 2012-05-21
people living together who share a computer, one uses Windows, the other uses a Linux OS like Ubuntu. the Ubuntu person can simply snoop all the Windows files, so the Windows user would have to research software to keep their files private.

(i know, no matter what, things cannot be totally private. and if there is physical access to the computer, sooner or later it can be broken into etc.)


any Windows users here in that situation?  what do you use to prevent your files from being snooped by the Linux user?

---

### Post by thatguruguy on 2012-05-21
What?

---

### Post by wyliecoyoteuk on 2012-05-21
Truecrypt?

---

### Post by Lucradia on 2012-05-21
> **black veils said:**
> people living together who share a computer, one uses Windows, the other uses a Linux OS like Ubuntu. the Ubuntu person can simply snoop all the Windows files, so the Windows user would have to research software to keep their files private.

(i know, no matter what, things cannot be totally private. and if there is physical access to the computer, sooner or later it can be broken into etc.)


any Windows users here in that situation?  what do you use to prevent your files from being snooped by the Linux user?

Pidgin doesn't provide encryption for passwords. Neither does Windows Live Messenger:

[http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords)

So what makes you think that anything can be done?

---

### Post by Dragonbite on 2012-05-21
I dunno.. I tried snooping on my wife's laptop from my laptop and while I could see my own files too easily, getting into my wife's only showed an empty folder.  So now I have to find out what setting is different between hers and mine and change (mine).

On the other hand, some of it is open because Windows is trying to make it easier to share files including music and video files, with other computers in your home-group.

Otherwise I usually get asked for my username and password to get into the computer.

---

### Post by Dr. C on 2012-05-21
The only way to do this is to encrypt the respective partition. With Windows this can be done, with Bitlocker or with TrueCrypt. With Ubuntu one can easilly encrypt the /home partition. By the way the Windows user can also read the GNU / Linux files [http://www.howtoforge.com/access-linux-partitions-from-windows]("http://www.howtoforge.com/access-linux-partitions-from-windows") so it works both ways.

---

### Post by snowpine on 2012-05-21
> **black veils said:**
> people living together who share a computer, one uses Windows, the other uses a Linux OS like Ubuntu. the Ubuntu person can simply snoop all the Windows files, so the Windows user would have to research software to keep their files private.

(i know, no matter what, things cannot be totally private. and if there is physical access to the computer, sooner or later it can be broken into etc.)


any Windows users here in that situation?  what do you use to prevent your files from being snooped by the Linux user?

It's not "snooping"... it is a "feature not a bug" that your files are easy to recover if something bad happens, like a user gets locked out... and guess what? anyone with physical access to your machine can "snoop" your Ubuntu files too. ;)

Encryption is the best solution; there are some good suggestions above.

---

### Post by roelforg on 2012-05-21
My way is to move the files to a linux system.
My most sensitive files are secured by encfs with encryption set to paranoid and a 32 char key.

---

### Post by ubuntu27 on 2012-05-21
> **Lucradia said:**
> Pidgin doesn't provide encryption for passwords. Neither does Windows Live Messenger:

[http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords)

So what makes you think that anything can be done?
[URL="http://www.cypherpunks.ca/otr/"]
Pidgin-OTR[/URL] encrypts the conversation. :popcorn: (Not the password though)

---

### Post by wilee-nilee on 2012-05-21
> **black veils said:**
> people living together who share a computer, one uses Windows, the other uses a Linux OS like Ubuntu. the Ubuntu person can simply snoop all the Windows files, so the Windows user would have to research software to keep their files private.

(i know, no matter what, things cannot be totally private. and if there is physical access to the computer, sooner or later it can be broken into etc.)


any Windows users here in that situation?  what do you use to prevent your files from being snooped by the Linux user?

If you think you have any privacy at all anywhere look again, you don't. :)

---

### Post by roelforg on 2012-05-21
> **wilee-nilee said:**
> If you think you have any privacy at all anywhere look again, you don't. :)

One can get very close, though...
(my friend once called me paranoid because i had a file that was encrypted... 10 times over with different passwords (as in, i encrypted the encrypted file, repeat 10 times) and because i have 2 physical firewalls with ids on super paranoia mode)

---

### Post by JDShu on 2012-05-21
My experience with the UNIX permission system (disclaimer: on solaris, although it should be the same on linux) has been quite bad, to be honest. Unless users are specifically trained to understand how permissions work, there are all sorts of annoying issues to deal with.

---

### Post by KiwiNZ on 2012-05-21
Privacy is in the hands of the beholder.

---

### Post by wilee-nilee on 2012-05-21
> **roelforg said:**
> One can get very close, though...
(my friend once called me paranoid because i had a file that was encrypted... 10 times over with different passwords (as in, i encrypted the encrypted file, repeat 10 times) and because i have 2 physical firewalls with ids on super paranoia mode)

That is only protection after you have gathered it from the web. :)

---

### Post by szymon_g on 2012-05-21
have you ever heard about an encryption? you can use multi-platform solutions like Truecrypt /AKA Realcrypt/ or use BittLocker/EFS (on windows only)

---

### Post by AllRadioisDead on 2012-05-21
They have sharing enabled. Of course you can view their public files.

---

### Post by codingman on 2012-05-21
The dumb thing about windows and linux dual-boot is that from linux, you can see all the linux files (obviously) and all the windows files too, but within windows, you can't see the linux files.

[CENTER][COLOR="blue"]Yippee for linux![/COLOR][/CENTER]

---

### Post by roelforg on 2012-05-21
> **wilee-nilee said:**
> That is only protection after you have gathered it from the web. :)

Did i mention that you can't even ping on my net without it showing up on my monitor?
And when stuff's encrypted pretty good, that's another wall.
My sensitive files can only be accessed by someone at the console if i'm there because i close the encrypted fs immediatly when done.

When i shut my systems down, i also kill the second firewall and the switch and i unplug the entire system (though that's because stuff's pretty loud, my room sounds better than movie effects when i flick the switch)

But, then again, i'm rather paranoid when it comes to what others are doing on/to/around my systems.
Most'll have enough by setting up a personal firewall, av, encrypted home (add an extra encrypted fs if you've got extrasensitive stuff), proper popup/ad/flash block (those are still some of the weaker points of a browser) and knowledge to avoid certain sites, know what you're installing, recognise classic virus signs, never give out personal data to every site (only if they've got good reason to ask for it, i almost never give my phone number for example) and have a good spamfilter.
That should be enough (if not overkill) for the avg. home user.

---

### Post by wilee-nilee on 2012-05-21
> **roelforg said:**
> Did i mention that you can't even ping on my net without it showing up on my monitor?
And when stuff's encrypted pretty good, that's another wall.
My sensitive files can only be accessed by someone at the console if i'm there because i close the encrypted fs immediatly when done.

When i shut my systems down, i also kill the second firewall and the switch and i unplug the entire system (though that's because stuff's pretty loud, my room sounds better than movie effects when i flick the switch)

But, then again, i'm rather paranoid when it comes to what others are doing on/to/around my systems.
Most'll have enough by setting up a personal firewall, av, encrypted home (add an extra encrypted fs if you've got extrasensitive stuff), proper popup/ad/flash block (those are still some of the weaker points of a browser) and knowledge to avoid certain sites, know what you're installing, recognise classic virus signs, never give out personal data to every site (only if they've got good reason to ask for it, i almost never give my phone number for example) and have a good spamfilter.
That should be enough (if not overkill) for the avg. home user.

If it makes you feel safe that's all that matters now isn't it, you don't have to convince me,  Just your therapist. :)

If it helps to know I have my own therapist.

---

### Post by Frogs Hair on 2012-05-21
I am on a Windows non sharing home network with a dual boot and none of the computers can see the contents of the others, although the map is visible. I would review the settings on the Windows computers.

---

### Post by KiwiNZ on 2012-05-21
O privacy thou art lovely

---

### Post by roelforg on 2012-05-21
> **wilee-nilee said:**
> If it makes you feel safe that's all that matters now isn't it, you don't have to convince me,  Just your therapist. :)

 It boiles down to:
Know your net (the biggest threat is always from within. Why else do you think i firewalled my own private subnet off of the rest of the house with a seperate firewall?)
Encrypt your stuff (with backup ofcourse)
Never give out more info then needed
Stay away from spam
Never underestimate the power of flash based ads/stuff (flash is known to be leaky so only enable it when needed, i even went so far as to disable it everywhere but youtube)
Know what to watch out for
Have a good av
Don't install everything you see (this is very true for binary packages)

So... Shrink, how much are you gonna charge me? :popcorn:

But windows actually makes it hard to do most of these things and the defaults it has have more holes in them than swiss cheese.

---

### Post by Lucradia on 2012-05-21
> **KiwiNZ said:**
> Privacy is in the hands of the beholder.

Wouldn't it be more along the lines of the beholder?

/lolface

---

### Post by roelforg on 2012-05-22
> **Lucradia said:**
> Wouldn't it be more along the lines of the beholder?

/lolface

Isn't it the point that you're the only beholder of your data?

---

### Post by Skara Brae on 2012-05-22
I am only little more than a n00b... And maybe this is very n00b'ish of me, but I keep my "private" files on USB flash drives (and save that somewhere safe, if need be).

I can access my Linux partitions (Ubuntu and Xubuntu) from within XP. I installed some program for that some months ago, just out of curiosity. I barely use it, though.

---

### Post by Dragonbite on 2012-05-22
> **wilee-nilee said:**
> If it makes you feel safe that's all that matters now isn't it, you don't have to convince me,  Just your therapist. :)

If it helps to know I have my own therapist.

Only if you can trust your therapist 8-[

---

### Post by forrestcupp on 2012-05-22
> **snowpine said:**
> It's not "snooping"... it is a "feature not a bug" that your files are easy to recover if something bad happens, like a user gets locked out... and guess what?

I completely agree. That's one of the beautiful things about Linux. I don't know how many times someone has screwed up their Windows machine, and I've plugged in a LiveUSB to back up all their precious files that they thought were gone forever. If they would have encrypted them, in some cases they *would* have been gone forever.

---

### Post by CharlesA on 2012-05-22
Physical access = root access. If you want your files to be unreadable, encrypt them.

---

### Post by forrestcupp on 2012-05-22
> **CharlesA said:**
> Physical access = root access. If you want your files to be unreadable, encrypt them.

Exactly. You could boot to a LiveUSB on a computer that has Ubuntu on it and alter any file you want on the root of that computer's filesystem. It's not just Windows.

---

### Post by Dragonbite on 2012-05-22
> **forrestcupp said:**
> I completely agree. That's one of the beautiful things about Linux. I don't know how many times someone has screwed up their Windows machine, and I've plugged in a LiveUSB to back up all their precious files that they thought were gone forever. If they would have encrypted them, in some cases they *would* have been gone forever.

Same here, except it is usually ME who is screwing things up!

I haven't been encrypting my Linux system either because when I distro-hop or try and upgrade it just gets in the way.

---

