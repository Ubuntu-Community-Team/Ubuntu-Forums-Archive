---
title: "Introducing a semi-newbie - 3D issues?"
date: 2005-12-24
forum: The Cafe
---

### Post by quincunx on 2005-12-24
Hello everyone, I just installed Ubuntu 5.1 tonight.  I used Slackware in 1993-96, and decided not to return to Linux (at home) until it was made practical.  I guess I'll see if that wish came true!

Now if I can get something other than this brown wallpaper!

I had difficulties with my 3D acceleration in another distro, anyone familiar with setting up 3Dfx voodoo2?  Could that be what my onboard Intel 810 is using?  If not, then I need to remove some hardware and reinstall perhaps.

-Quincunx

---

### Post by gsdefender on 2005-12-24
Well, 3Dfx only produced 3D acceleration boards, and I don't remember any collaboration with Intel (the i810 is by far more recent). You should try to be more specific about your troubles, since the Ubuntu installer (like many others) should be able to configure the board automagically.

---

### Post by erikpiper on 2005-12-24
BTW, Go to the system menu (By the applications one), Select Preferences, and select "desktop Backround"

---

### Post by quincunx on 2005-12-24
[QUOTE=erikpiper]BTW, Go to the system menu (By the applications one), Select Preferences, and select "desktop Backround"[/QUOTE]

And what's this supposed to do?  The default installation comes with three kinds of wallpaper:
1. Brown
2. wide-screen Brown, and 
3. a cartoon girl in-front of a brown (& orange) background (with "edubuntu" in the lower corner).

btw, right-clicking on the desktop and choosing "Change desktop background" is much easier.

I really can't stand brown.  I've harldly met someone that can; so Brown really isn't "for the people".  I would have expected the default install to have many colors available in case you're one of the 5.9 billion people who also can't stand the color brown.  I spent some time downloading wallpaper last night, but I guess I didn't have write permissions for the folder I was saving to (/usr/share/backgrounds); and Firefox pretended like the downloads were going okay.  After thinking I had downloaded 10 or so files, I found only the three that I saved to my Desktop survived.

Is there no root account, btw?  I'm confused since after installing I was never asked to make a root password.  How do I get to that god-like state where permissions are someone else's problem ;)

I'm still surprised that there's no blue, or green, or purple, or yellow, or option-other-than-brown wallpaper in the default install.  It's like I just installed something that wasn't finished and got shipped a little early.  It would have been nice to spend the first few hours learning more about my system rather than finding/downloading/then loosing wallpaper to keep my eyes from hurting.

---

### Post by quincunx on 2005-12-24
[QUOTE=gsdefender]Well, 3Dfx only produced 3D acceleration boards, and I don't remember any collaboration with Intel (the i810 is by far more recent). You should try to be more specific about your troubles, since the Ubuntu installer (like many others) should be able to configure the board automagically.[/QUOTE]


Here's a thread I started on this issue:
[http://ubuntuforums.org/showthread.php?t=107887](http://ubuntuforums.org/showthread.php?t=107887)

If you can help that would be great, see the above thread for more details about my system/situation.

---

### Post by kaamos on 2005-12-24
> **quincunx]And what's this supposed to do?  The default installation comes with three kinds of wallpaper:
1. Brown
2. wide-screen Brown, and 
3. a cartoon girl in-front of a brown (& orange) background (with "edubuntu" in the lower corner).

btw, right-clicking on the desktop and choosing "Change desktop background" is much easier.

I really can't stand brown.  I've harldly met someone that can said:**
> 

Calm down man. Anyway if you don't like the wallpapers that ship with an OS, download something else and use that. Or disable the wallpaper, if it's that big of a deal. Anyway, I suggest you read these:

[http://en.wikipedia.org/wiki/Superuser](http://en.wikipedia.org/wiki/Superuser)
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

For your failed efforts to download files: you do not have write permissions outside your home directory. Why?
[quote]Separation of administrative privileges from normal user privileges makes an operating system more resistant to viruses and other malicious software

---

### Post by erikpiper on 2005-12-24
Why did you use edubuntu? Do you have kids?


Windows, BTW comes with only one wallpaper (At least on my Thinkpad)

---

### Post by quincunx on 2005-12-25
> **kaamos]Calm down man. Anyway if you don't like the wallpapers that ship with an OS, download something else and use that. Or disable the wallpaper, if it's that big of a deal. Anyway, I suggest you read these:

[http://en.wikipedia.org/wiki/Superuser](http://en.wikipedia.org/wiki/Superuser)
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

...I'm cool, just couldn't figure out how selecting other brown wallpaper would help my situation  said:**
> 
For your failed efforts to download files: you do not have write permissions outside your home directory. Why?


I'm not sure why, unless that's a rhetorical question with the pasted quote being the "answer".  I know about admin vs. user privs.  What I'm wondering is, how do I log in as root.  Or does Ubuntu not have a root user?  I figured during install that I would have been asked to make a root password, but that never happened.  My concern is that there's a default root password and I haven't set it yet; but what apears to be happening is the root password is the same as the user password...?  

I just think it's strange that I was never notified that I couldn't write to the directory.   I would have expected a message telling me that I can't save in that location. That's the only thing I'm finding difficult with Linux so far, I click buttons, etc and get silence in return.  After a while I might find out why I got silence instead of the intended result, but and error message could have easily saved me hours worth of "work".  I'm willing to stick with it for a while.  Once I get my 3D acceleration taken care of, I'll be set.

---

### Post by briancurtin on 2005-12-25
this will shed some light on the root issue: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

sudo is used instead of root for security reasons. im new to ubuntu but not really to linux, and i found myself using "su root" still at times. it takes a little bit getting used to but its not a bad system.

---

### Post by kaamos on 2005-12-25
[QUOTE=quincunx]What I'm wondering is, how do I log in as root.  Or does Ubuntu not have a root user?  I figured during install that I would have been asked to make a root password, but that never happened.  My concern is that there's a default root password and I haven't set it yet; but what apears to be happening is the root password is the same as the user password...?[/QUOTE]

Yeah, the wiki page for rootsudo is a good thing to read as well. Anyway, your root password does not exist unless you have set it yourself. So it's not the same as the user password. But the user can gain root privilidges (if he/she is part of a group that has rights to use sudo) for example by "sudo su".

Hope you get your 3d acceleration running soon. :)

---

### Post by quincunx on 2005-12-25
[QUOTE=briancurtin]this will shed some light on the root issue: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

sudo is used instead of root for security reasons. im new to ubuntu but not really to linux, and i found myself using "su root" still at times. it takes a little bit getting used to but its not a bad system.[/QUOTE]


Thanks for the link!  Yea, it's different not having root, but it's simple and works... two things that go together well ;)

---

### Post by poofyhairguy on 2005-12-25
For graphic apps (all but gedit) use "gksudo" instead of sudo. for example:

```
gksudo nautilus
```

Gives you a Godlike nautilus.

---

