---
title: "HD operations lite flashes every second..?"
date: 2010-03-31
forum: Security
---

### Post by DonaldJ on 2010-03-31
HD operations indicator-lite flashes every second, on all my hd's..?  What is the OS doing?..  Is this a security breach?..  Does this mean that my files are being uploaded at about 10K per second..?  Or is this just a software checking status every second..?  What does what, that engages the hd every second..?  Please tell...

---

### Post by cariboo on 2010-03-31
I wouldn't say it happens every second, but the drive light on my computers flash fairly regularly.

---

### Post by cariboo on 2010-03-31
I wouldn't say it happens every second, but the drive light on my computers flash fairly regularly. Linux delays hard drive writes for various reason, so you will see hard drive activity.

---

### Post by lisati on 2010-03-31
> **cariboo907 said:**
> I wouldn't say it happens every second, but the drive light on my computers flash fairly regularly.

Ditto. A coupe of reasons come to mind. There could be some legitimate background task (such as "update manager") that gets called up every so often, which would account for some of the activity.

---

### Post by DonaldJ on 2010-03-31
I thought it might be update manager, so I disabled it.  
Now the little light flashes twice every second in this fresh install U-910.

---

### Post by bodhi.zazen on 2010-03-31
> **DonaldJ said:**
> I thought it might be update manager, so I disabled it.  
Now the little light flashes twice every second in this fresh install U-910.

Linux is fairly disk intense. You can modify this by making a few modifications.

See : [http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

more specific see the section "Maximize your use of RAM" 

You can google for other options.

---

### Post by ricyaun on 2010-03-31
> **lisati said:**
> Ditto. A coupe of reasons come to mind. There could be some legitimate background task (such as "update manager") that gets called up every so often, which would account for some of the activity.

Everybody is going to say I am paranoid again, but here we go.  Unless you have downloaded an app for monitoring process activity for Linux then the HDD should quiet right down immediately after boot up.  You might get a brief spat of autoeth0, or proprietary driver activity then it should be quiet.  I have had no Ubuntu install that I have done do this until I opened a browser.  Then in the case of an instant messenger being active or your browser pinging which may be getting taken from the hdd there should be no hdd activity, and certainly nothing rhythmic.  This a sign of resource usage meant to slow your computer down.  More than likely there is no function attached to it.  Especially if that is a pristine install that has no more than been updated.
As bodhi pointed out earlier to a person concerned with a rootkit scan you must establish a control.
Here is how you do that.  Immediately after an install go to Update manager and untick the auto update, before any updating occurs.  Then watch your activity led.  It should be very quiet.  At first you may get the autoeth0 and restricted hardware drivers available.  bodhi is right about the fact that these alerts come directly from the hdd, and not from RAM.  Also make sure to have your computer hooked to the router, and the router disconnected fro0m the Internet.
Next update the OS.  It won't be fully functional until you do.  Then monitor the activity led for a very few minutes after the update.  I have found it should still be very quiet.  Also while the update is happening pay attention to your download speed.  Despite what people may think it should be fairly stable.  It will fluctuate some but if it is making big swings something funny is going on.  Possibly a redirect.
The only time I have seen this is when I just got hacked, and I knew I had just had Internet activity for no reason.  The slow down in the machine is perceptible.  Also you may find that this increases with time.   
Download and read the Harden Linux guide.  The 1st chapter speaks to much of this.

In case somebody wants to make a Windows reference that OS is busy longer after boot up but should also quiet down after a while.  Unless you have a periodic real time heuristic scanner located in some funky security software you have downloaded it should be quiet.  The only thing in a Windows XP OS to do this is every 3 days an autodefrag utility may or may not wake up.  That thing is unreliable about that at best, and is based on the computer not being busy.

---

### Post by OpSecShellshock on 2010-03-31
In my experience, this kind of activity has been caused by file indexing. That tends to happen during idle time (if meat-memory serves).

---

### Post by wirelessmonkey on 2010-03-31
What OpSec said, plus the disk caching to memory.  I'm sorry ricyuan, but you're incorrect.  iotop will show you what is going on with your disk, if you're truly curious.

---

### Post by DonaldJ on 2010-03-31
B Z..  If max-tweaking ram is "it", then it should be packaged into a feature.. with optional on/off switches, all possible choices, and easy/smooth switch-overs.. thinks I...  
Isn't that what "ubuntu" implies, with-in its core..?

---

### Post by bodhi.zazen on 2010-03-31
> **DonaldJ said:**
> B Z..  If max-tweaking ram is "it", then it should be packaged into a feature.. with optional on/off switches, all possible choices, and easy/smooth switch-overs.. thinks I...  
Isn't that what "ubuntu" implies, with-in its core..?

I think you should look at my blog and understand the implications of the changes. The title of the section is perhaps misleading that way, ant it is somewhat out of context ...

linux is more disk intensive then you might imagine and my tweaks might work well for a netbook, but not so great for a server. The "defaults" will always be conservative that way.

---

### Post by DonaldJ on 2010-03-31
If it's "indexing", it matches the frequencies of the indicator flashes, if it's about 10K per quick flash.. 7 to 13 tiny quick flashes for every bright flash.. as does downloading pix files, but is about 20 times faster when the memory is processing other commands and processes...
If the system indexes at about 10K per second.. if it's indexing to index..  or if it's compressing data to quick-send, at start of boot, or at shut-down..  both processes sound the same from the hd...

---

