---
title: "Loved 9.10, disappointed in 10.04...?!?"
date: 2010-05-02
forum: Testimonials &amp; Experiences
---

### Post by Cobra_MX5 on 2010-05-02
Hello, I'd like to share my experience with 10.04...

I started using Ubuntu last September (about 8 months now), and almost never looked back since. I first installed 9.04 JJ on my laptop, which, apart from one or two minor incompatibilities (kernel panics caused by the broadcom sta wireless driver, fixed by using the b43 driver), went like a dream on my laptop. I then installed 9.10 KK on my desktop pc as well as a friend's laptop and also upgraded my laptop from JJ to KK. Only problems I've encountered are:

- cannot login using laptop's fingerprint reader from 'hibernate' or 'suspend'
- laptop takes long to hibernate due to some BT (i guess) problems (message "hci0 failed to resubmit" or something like that)
- panel drawers lag after using for the first time
- vnc does not refresh screen on remote machine with compiz enabled (i know this is a problem with the nvidia drivers)

All of these are minor problems, easy to avoid.

Fast forward to April 2010: stuck on my pc screen waiting for 10.04 to be released... I have read that this new ubuntu version will boot faster than ever before and suspend - hibernate even fasterer (:D) due to the removal of HAL. I have also read it will be syncable with my new iphone, which is one of the very few reasons I still use windows (rarely).

So quickly after the new version is released, I format my laptop (for several reasons) and install it there... Set up what is needed (wifi, fingerprint reader etc), and then... dissapointment. The computer does boot faster than ever, which is good, but:

- *still* cannot login using laptop's fingerprint reader from 'hibernate' or  'suspend'
- laptop *still* takes long to hibernate due to some BT (i guess) problems  (message "hci0 failed to resubmit" or something like that)
- panel drawers *still* lag after using for the first time
- vnc *still* does not refresh screen on remote machine with compiz enabled (i  know this is* the same* problem with the nvidia drivers)

In addition to these, new problems appear:

- in order to do everything with my fingerprint, I need to press "enter" after i swipe my finger
- whenever i ssh into another machine, i need to enter the password, whereas in the past it was saved the first time i did it
- iphone syncability... what? i was hoping to be able to sync contacts with the pc (after all it is just a sqlite database!), but only way to do that is by syncing with ubuntu one, which is only free for 30 days. Sorry, but I don't need this feature that much so that i have to pay to get it...! But even syncing music... what? I can't find out how to do this, Rythmbox is not user-friendly at all (this is why i have been using amarok to play music)!!! And even if I try to access the phone via nautilus, all i get is a 

"Could not display "afc://-long number-
The file is of an unknown type"

Am I the only one who is having problems with 10.04? Don't get me wrong, I love ubuntu and I will definately keep on using it, it's just that I was expecting a better system with more features and some of the problems solved, but all I see is the same system, with none of the problems solved but some new problems added, that boots faster than before...!

I'd be glad if anyone can help with any of the problems...

Thanks,
Pavlos

---

### Post by sixthwheel on 2010-05-02
Rythmbox is a little tricky at first, but once you figure it out it's pretty usable.
I use it in conjunction with GTKPOD for organizing and making playlists on my I-Pod.

The only problem I discovered with Lucid so far, is that my webcam does not work with Skype.
I'm still dual booting with Karmic, but it would be nice not having to go back and forth.
This is why I was so happy to delete Windows..Now I have to run back and forth within ubuntu.:(

---

### Post by Tamlynmac on 2010-05-02
> Cobra_MX5

I'd be glad if anyone can help with any of the problems...

Might I suggest you post a thread for each of the problems in the appropriate help section(s), as this isn't a support section of the forum.

Thanks for sharing your T&E and Good Luck.

---

### Post by Cobra_MX5 on 2010-05-02
More problems keep coming up...

What bothers me is the fact that I'm having trouble with things that in 9.04 and 9.10 worked flawlessly in 3 computers...!

I think I'll move back to 9.10...

---

### Post by WinterRain on 2010-05-02
> **Cobra_MX5 said:**
> 

Am I the only one who is having problems with 10.04?

I'm not of the people having problems. I can't imagine it getting any better.  Perhaps your next computer purchase should be one with ubuntu preinstalled. It will work great then. Good luck to you.

---

### Post by sixthwheel on 2010-05-02
> **WinterRain said:**
> I'm not of the people having problems. I can't imagine it getting any better.  Perhaps your next computer purchase should be one with ubuntu preinstalled. It will work great then. Good luck to you.
I've been noticing that when you reply to someone having problems with Lucid, the only answer you seem to come up with is that Lucid is just working for you perfectly.

That is fantastic, however that doesn't help the OP any.
There are a whole bunch of people it seems, to have a lot of problems with Lucid, after trouble free experiences with earlier Ubuntu releases.

Someone being frustrated with problems, don't really want to hear cheer leading, they need help.

---

### Post by Tamlynmac on 2010-05-02
> sixthwheel
Someone being frustrated with problems, don't really want to hear cheer leading, they need help. 	

 Lets keep in mind that the T&E is not a support section of the forums. Nor is it for debating purposes. Each person has their own opinion and I believe they should be permitted to express it in a non-confrontational way - in this section. Assuming one follows the T&E sectional guidelines and the COC.

Should WinterRain post satisfaction with the release and said post only expresses WinterRain's opinion and doesn't engaging in a debate. Then IMHO WinterRain is in compliance with sectional guidelines. Especially, when other members violate the sectional guidelines by either providing support or debating.

Just my $0.02 and of course I could be wrong.

---

### Post by uRock on 2010-05-02
Should've tried the LiveCD first.:(

I don't use an iPhone, so I can't be of much help on that.

I just recently started using Rhythmbox and man do I love it. I here Banshee is good, too. I'll give it a shot one day.

---

### Post by cariboo on 2010-05-02
Fingerprint readers have been a bit of a problem for quite a while, in most cases people can't even use them to login, this is the first time I've heard of anyone having a problem with hibernate because of the fingerprint reader. Have you checked [launchpad]("https://bugs.launchpad.net/") to see if anyone else is suffering from the same problem? If you can't find anything, please submit a bug, as the devs can't fix a problem if they don't know about it.

---

### Post by jbowen7 on 2010-05-02
I had overly high hopes for this release, and though I'm not experiencing the problems in this forum I'm still a little overwhelmed.

I'm finding the my boot time to the grub really quick, but grub loading takes quite a while to get to the gnome.

Also HAS ANYONE BEEN NOTICING ISSUES WITH APT? (apt-get autoremove is not removing all folders and is not removing scripts from /etc/rc*.d , nor from /etc/init) Perhaps I should start my own forum on this topic.

Also locate seems to be damaged... It's not revealing directories that I know exist.

Furthermore... gdm is freezing at seemingly random times.

This feels like a beta release, maybe there will be a service pack 1 release!!
Other than a few bugs.. Good job. I'll continue my support.

---

### Post by WinterRain on 2010-05-02
> **jbowen7 said:**
> maybe there will be a service pack 1 release!!


In a sense, there will be. 2 months from now there will be 10.04.1, then 10.04.2, then 10.04.3, etc. If you are already using it, you don't need to reinstall, just keep it updated. In a couple months it will be really solid. But it works flawless for me so far.

---

### Post by MidBSD on 2010-05-02
> **jbowen7 said:**
> Also locate seems to be damaged... It's not revealing directories that I know exist.

I don't know if you've already tried 'updatedb' but if not, give that a try and see if the directories appear again.

---

### Post by 3rdalbum on 2010-05-03
Ubuntu One is free - it's not "free for 30 days", it's free unless you want to get more storage.

---

### Post by Cobra_MX5 on 2010-05-03
I'm not having a problem with hibernate, I just can't log in with me pinky (:D) from hibernation...

I know Ubuntu One is free (as in freedom), but syncing iphone contacts with ubuntu one isn't.

I did try the live cd first, I always do, but when one uses a live cd they don't install software!

I was expecting 10.04 to be much better than 9.10 and a problem-solver, but it wasn't, not for me at least. Plus, 10 sec difference in boot time is nothing compared to all the other problems I had.

Actually, everything about my installation of 10.04 was wrong, I couldn't even set up my email accounts in thunderbird correctly.

So I took a deep breath and downloaded Fedora 12... It's now happily installed in my laptop, everything is working OK, setting up thunderburd (the same version as the one in 10.04) took no more than 3 minutes, fingerprint access works like a dream, but...

- setting up is a bit trickier than in ubuntu
- installing google earth requires manually downloading and installing 239042934 rpm packages (although most programs install very quickly and dependencies are solved on their own)
- in general, ubuntu feels more responsive and quicker
- it probably doesn't get any better than the ubuntu community and support...

I'll give Fedora a chance, though (though I'm certainly not removing Ubuntu from my desktop pc), and if it  doesn't work for me I might give 10.04 another shot on a fresh install and see again what works and what doesn't...

---

### Post by uRock on 2010-05-03
> **Cobra_MX5 said:**
> I did try the live cd first, I always do, but when one uses a live cd they don't install software!
I install programs while running the LiveCD almost every time I use the LiveCD. How else do ya get to see if your system is compatible with the versions of the programs the release is using? Mostly every program in Ubuntu Software Store can be installed on the LiveCD.

---

### Post by Cobra_MX5 on 2010-05-03
> **uRock said:**
> I install programs while running the LiveCD almost every time I use the LiveCD. How else do ya get to see if your system is compatible with the versions of the programs the release is using? Mostly every program in Ubuntu Software Store can be installed on the LiveCD.

You are right about that, it's just that I didn't have problems with 9.10 or 9.04 on any of the computers I installed them on, so I surely wasn't expecting new problems to come up with 10.04...

On the other hand, I wanted to format the HDD on my laptop either way, in order to change the partitions, so I'm not complaining at all about that.

Anyways, got a bit fed up with Fedora's slower-than-slowness-itself package manager and installed 9.10 again...! :D:D:D

---

