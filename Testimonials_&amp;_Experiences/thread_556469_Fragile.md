---
title: "Fragile"
date: 2007-09-21
forum: Testimonials &amp; Experiences
---

### Post by mikeize on 2007-09-21
<vent>

Ubuntu is pissing me off, can I just say that?  It's so damn touchy!  So much of what I try to get to work ends up irreparably (as far as I'm concerned) wrecking my installation.  Compiz I can kind of understand being unstable, but SOUND?  I know, I know...  I did it wrong, right?  Well I guess I did, but I researched how to do it first, and it still broke!  And besides that, it shouldn't be so effing hard (impossible) to fix/restore and smooth things out!
One thing that attracted me to Ubuntu was its reputation for being customizable...  but for me it seems that the more I customize it, the less usable it becomes.  
The worst thing is how unforgiving it is.  For example;  my sound was working, but only with one application at a time, so I looked around for how to fix that.  I waded through probably twenty or thirty pages of information on that one subject, and couldn't get anything to work.  In fact, my sound stopped working completely!  And then, I looked around for a fix to that problem...  looking, reading, asking...  nothing worked!
I know this must sound familiar to some people, because there are hundreds of unsolved critical problem threads on this site alone.
Okay, so after several reinstalls due to a wrecked system, I got wise and put my home directory on a separate partition so I wouldn't have to keep setting all my preferences, backing up docs etc.  
Well, trying to set up ntfs r/w support, system got fubar'd again (oh I tried to fix it, believe me!)  but I figured I could just wipe the root and reinstall.  So I did, and it wouldn't boot.  I was digging around in fstab and menu.lst (using the live cd), trying to repair grub with the super grub disk.  Nothing.  So finally I reinstalled, wiping root and home partitions, and it booted!  Hoo-ray!  But wtf is the point of having a separate home partition, if you can't keep it when you reinstall?  Wtf is the point of customization or open-source principles if the system is unusable.  Don't get me wrong, when it works I love it, and I'm not permanently rebooting into XP (yet), but it is killing me!  I just built this new computer, and the whole time I was thinking about all the cool stuff I could do with Ubuntu on some decent hardware (not bleeding edge, but good).  Instead, its been a huge headache.  I've been staying up till 3am, poring over forums and blogs and support pages...  Dammit I just want to watch a movie with all my speakers working!  And if I mess it up, I want to be able to reset my changes.
So that's it.  That's my Ubuntu testimonial.  I doubt anyone will read the whole thing, probably shouldn't (I wouldn't, lol).  So yeah, I'm not leaving, but I'm pretty cynical about this whole thing now.
</vent>

-mike
If you can't tell, I'm frustrated.

---

### Post by LaRoza on 2007-09-21
Your post is difficult to read, so I didn't really read the entire thing.

You might want to use another distro:

* Pardus
* PCLinuxOS
* Mepis
* Mandriva
* LinuxMint

---

### Post by Mazza558 on 2007-09-21
Wait until Gutsy is released, and then try again.

---

### Post by karellen on 2007-09-21
one of the most certain things in the linux world is that - in 99% of cases - a new release is better than the previous one

---

### Post by wolfen69 on 2007-09-21
with all the problems you're having, i would suggest downloading and installing gutsy gibbon now [http://cdimage.ubuntulinux.org/daily-live/current/?C=S;O=A](http://cdimage.ubuntulinux.org/daily-live/current/?C=S;O=A)  it can't hurt at this point. good luck.

---

### Post by SnTholiday on 2007-09-21
> **karellen said:**
> one of the most certain things in the linux world is that - in 99% of cases - a new release is better than the previous one

6.10 (Edgy) gave me so many problems I stopped using Ubuntu for awhile. I am finding 7.04 to be much better.

---

### Post by madc on 2007-09-21
> **mikeize said:**
> 

 So yeah, I'm not leaving, but I'm pretty cynical about this whole thing now.



haha...as i am looking myself 1-2 years ago...as you can see, i haven't abandoned linux, as you won't either! tell me excately what is your problem with sound, so i will try to help you!;)

---

### Post by mikeize on 2007-09-21
Thanks for the comments (everybody).  At the moment, I'm not sure what I'm going to do.  Right now, I have a fresh install so it's running anyway.  Obviously I'm not too excited about jumping back in again, tweaking it and adding programs and functions-- knowing that there's a good possibility of having to start over again.

Re: trying other distros...  thanks, I might.  But as I said, when ubuntu is working I really like it a lot.  I have it on my laptop, and it works great!  On the other hand, I haven't really messed with it much there.  

At any rate I think I may give Gutsy a try first.  It's a thought I had earlier, but honestly I was/am afraid that it would be even less stable than Feisty (what I'm running now, btw).  I'd be interested to hear more from any of you who have made the switch from FF to GG.  -did you upgrade or fresh install?  -were you able to leave your /home partition (if applicable) untouched?  -any specific problems that have/have not been fixed in that release?

I'll be checking into gutsy myself, but personal experience from other users would be appreciated.  Thanks everybody.

-mike

---

### Post by LaRoza on 2007-09-21
Don't upgrade unless you need to or want to, my advice.

If you do, I would recommend a clean install after running it live.

You can copy the contents of your home folder, all the dot folders, to keep your settings.

---

### Post by mikeize on 2007-09-21
> **LaRoza said:**
> Don't upgrade unless you need to or want to, my advice.

If you do, I would recommend a clean install after running it live.

You can copy the contents of your home folder, all the dot folders, to keep your settings.

Thanks, I will run it live 

Also, what do you mean by "dot folders"?  **(edit: nevermind, got it)**

-mike

---

### Post by zero244 on 2007-09-22
In case you weren't aware of it......if you setup three partitions for your install. One for /Root, another one for /home and the third for the swap file. This makes doing a fresh install much easier to customize because many of your settings and wallpapers etc will remain intact.
So its a less painful restore for a upgrade or fresh install.
Just remember not to format your /home partition.
Hang in there you will eventually master Linux.
Good Luck.

---

### Post by lancest on 2007-09-22
I have found myself dealing with a little anger in years past when I had to deal with a few Linux setup and install problems. These always get resolved and you will find ways to automate your tweaks in advance (if any).  Also being careful in acquiring hardware. This is the price of your learning and freedom from a proprietary OS. Later you will be thankful  you had a few trials. Of course newer versions of Ubuntu/Linux tend to eliminate these headaches. (For years I had to dual boot because some of my printers did not work and did not trust OO completely.) Those days are gone and Ubuntu just works!  Gutsy is not perfect yet but getting great!

---

### Post by mikeize on 2007-09-23
> **zero244 said:**
> In case you weren't aware of it......if you setup three partitions for your install. One for /Root, another one for /home and the third for the swap file. This makes doing a fresh install much easier to customize because many of your settings and wallpapers etc will remain intact.
So its a less painful restore for a upgrade or fresh install.
Just remember not to format your /home partition.
Hang in there you will eventually master Linux.
Good Luck.

Hey zero, thanks!

Actually, I DID do this, and still had some trouble-- I wasn't able to boot ubuntu until I wiped my home partition too.  I don't know why!  When I go to install, I check the drive (partition) I want to use as root, name it "/", and I make sure that  my home partition is named "/home" (but not checked since this would format it).  And yes, a swap partition too.
 Is there a better way?  I think I must be doing something wrong.  Should this cause trouble when doing kernel or version upgrades?  

Lancest:

Thanks for the encouragement!  I'm running the gutsy live cd at the moment, --still debating whether or not to install it...  probably will give it try, anyway...



-mike

---

### Post by mikeize on 2007-09-24
Gutsy is installed and seems to be working well!  ALL of my sound issues are resolved, though I did have to fix the alsa drivers manually.  I seem to have the /home partition thing working also, so I feel a lot better about that whole thing.  I've enabled desktop effects (extra), but haven't tried compiz or anything like that yet.  My only problem right now is that "gksudo nautilus" doesn't work!  Nothing happens.  I even installed "nautilus-gksu" from synaptic, and it won't show up in the context menu either.  Well, let me reboot...

-mike

EDIT:  Okay, reboot did it!  All systems go (so far), Gutsy seems good!

---

### Post by dondad on 2007-10-05
> **mikeize said:**
> Hey zero, thanks!

Actually, I DID do this, and still had some trouble-- I wasn't able to boot ubuntu until I wiped my home partition too.  I don't know why!  When I go to install, I check the drive (partition) I want to use as root, name it "/", and I make sure that  my home partition is named "/home" (but not checked since this would format it).  And yes, a swap partition too.
 Is there a better way?  I think I must be doing something wrong.  Should this cause trouble when doing kernel or version upgrades?  

Lancest:

Thanks for the encouragement!  I'm running the gutsy live cd at the moment, --still debating whether or not to install it...  probably will give it try, anyway...



-mike

I have a separate partition for my /home directory and ran into the same problem: Reinstall, no boot. As far as I can tell the problem had something to do with one of the configuration files. What I ended up doing was deleting the dot files one by one (making guesses as to the most likely culprit) and it eventually booted OK.

Not sure if I was right, but it looks to me like you need to delete the old configuration fles from your home directory before you do a reload if you want it totally clean.

---

