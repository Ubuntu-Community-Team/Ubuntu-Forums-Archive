---
title: "I've Been Attacked!! Help!!"
date: 2007-08-03
forum: Server Platforms
---

### Post by fnx.lv on 2007-08-03
Or at least I'm almost certain I've been attacked...Here's the story.

I was playing Wesnoth in full screen mode when all of a sudden my screen blinks and I see Wesnoth in windowed mode.  I don't know how or why this happened.  So immediately I open Firestarter and sure enough there's a suspicious entry under Active Connections:

Stacheldraht

So naturally I google this. Taken from wikipedia: Stacheldraht (German for barbed wire) is a piece of software written by Mixter for Linux and Solaris systems which acts as a distributed denial of service (DDoS) agent. The tool detects and automatically enables source address forgery.  

oh no!!! Further reading tells me its a piece of malware formed in 1999 I believe.  There's also a lengthy article on the University of Washington's website [http://staff.washington.edu/dittrich/misc/stacheldraht.analysis](http://staff.washington.edu/dittrich/misc/stacheldraht.analysis) if anyone's interested.  I haven't read it all myself yet.  (I will after this post) What else can I do?

Is my entire system compromised? Passwords? Personal info? Yikes! 

Any advice? Have you guys heard of this and if so should I reinstall/reformat everything? I hope posting this doesn't spread it to the forums...if it does..then I guess this post is good as deleted :(

I thought Linux was supposed to be ultra super duper secure or something? :/  If there's any other info you guys need in order to help me asses this situation I'll be glad to help (logs, etc.) But I don't really  know how to go about it.  I've only been using Linux for just over a month and this is not the first time I feel less than fully secure.  Open source is great, but doesn't that mean its also open to everyone else? Especially those who know how to hijack systems? Efficiently?

EDIT: It's now been a few minutes since I first saw Stacheldraht and now its gone from Firestarter.  He/she/it went away! (they knew I was watching them. or worse...they did what they had to do!! )))
------
Edit:  I ended up reinstalling.  Guess it was my fault to begin with.  Should have read these posts earlier :/

---

### Post by dreadlord_chris on 2007-08-03
Now, while your system is still clean:
```

sudo apt-get install rkhunter chkrootkit

```
[rkhunter]("http://freshmeat.net/projects/rkhunter/") and [chkrootkit]("http://freshmeat.net/projects/chkrootkit/") are both utilities that check for various system compromises.

I use them both...

---

### Post by dannyboy79 on 2007-08-03
> **fnx.lv said:**
> Or at least I'm almost certain I've been attacked...Here's the story.

I was playing Wesnoth in full screen mode when all of a sudden my screen blinks and I see Wesnoth in windowed mode.  I don't know how or why this happened.  So immediately I open Firestarter and sure enough there's a suspicious entry under Active Connections:

Stacheldraht

So naturally I google this. Taken from wikipedia: Stacheldraht (German for barbed wire) is a piece of software written by Mixter for Linux and Solaris systems which acts as a distributed denial of service (DDoS) agent. The tool detects and automatically enables source address forgery.  

oh no!!! Further reading tells me its a piece of malware formed in 1999 I believe.  There's also a lengthy article on the University of Washington's website [http://staff.washington.edu/dittrich/misc/stacheldraht.analysis](http://staff.washington.edu/dittrich/misc/stacheldraht.analysis) if anyone's interested.  I haven't read it all myself yet.  (I will after this post) What else can I do?

Is my entire system compromised? Passwords? Personal info? Yikes! 

Any advice? Have you guys heard of this and if so should I reinstall/reformat everything? I hope posting this doesn't spread it to the forums...if it does..then I guess this post is good as deleted :(

I thought Linux was supposed to be ultra super duper secure or something? :/  If there's any other info you guys need in order to help me asses this situation I'll be glad to help (logs, etc.) But I don't really  know how to go about it.  I've only been using Linux for just over a month and this is not the first time I feel less than fully secure.  Open source is great, but doesn't that mean its also open to everyone else? Especially those who know how to hijack systems? Efficiently?

EDIT: It's now been a few minutes since I first saw Stacheldraht and now its gone from Firestarter.  He/she/it went away! (they knew I was watching them. or worse...they did what they had to do!! )))
------
Edit:  I ended up reinstalling.  Guess it was my fault to begin with.  Should have read these posts earlier :/

you really need to look at what ports you have open and the vulnurabilities of each of those open ports and protocols that use them.

netstat -pant

will show you all ports that are listening. if they have a 0.0.0.0.22, that means that they are listening on the external host, not just localhost. any that are 127.0.0.1 are obviously only listening for connections from the localhost (the loopback interface). You could always be sure that you have a backup solution in place so you don't have to reinstall each time you think you were hacked. I have used Tripwire which is also great. Immediately after a new install, install tripwire, it'll take a snapshot of your system and then it'll check files against the snapshot and tell if they changed. 

chkrootkit and rkhunter are invaluable also as the above poster mentioned

---

### Post by fnx.lv on 2007-08-03
I have used chkrootkit before and it always comes up without finding anything.  After the attack I ran the program and again nothing.  But I haven't tried rkhunter.  

Thanks for the replies.  I will try those out.

---

### Post by Geir102 on 2007-08-04
Hi just testet rkhunter on my system got 

Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initram                                                                             fs (directory)Please inspect:  /dev/.static (directory)  /dev/.udev (directory)                                                                               /dev/.initramfs (directory)

Is this a problem?

---

### Post by yabbadabbadont on 2007-08-04
> **Geir102 said:**
> Hi just testet rkhunter on my system got 

Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initram                                                                             fs (directory)Please inspect:  /dev/.static (directory)  /dev/.udev (directory)                                                                               /dev/.initramfs (directory)

Is this a problem?

Those are normal.

---

