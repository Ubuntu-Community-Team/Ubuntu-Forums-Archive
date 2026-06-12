---
title: "So my sound won't work anymore..."
date: 2007-12-19
forum: System76 Support
---

### Post by Royal_Pwner on 2007-12-19
I can't make it work. No matter what. Help?

Error screenie attached.

---

### Post by weverjames on 2007-12-19
I am having the same problem.   No sound!  It happened after an update.  It said the sound card is not recognized or I don't have the gstreamer plugin installed.  It is installed !!
Please HELP!  HELP! help! help!  HELP!

---

### Post by Royal_Pwner on 2007-12-19
This is *really* bad.
please help.

---

### Post by octathlon on 2007-12-19
Have you run the System76 driver since the update?  That should do it.

---

### Post by Peneus on 2007-12-19
Hello,

I am having the same problem. Even after running 
system76 driver after the update. I have Daru2 with gutsy on it.

---

### Post by thomasaaron on 2007-12-20
Please confirm that you have the latest driver installed. It should be 2.1.3. To do this, go to System > Administration > System76 Driver > About.

If you have the correct driver version, run it with the Install Tab and the Install Button. Then REBOOT your computer.

Did that fix it?

If not, go to System > Preferences > Sound and press the first "TEST" button.
Do you get an error? What are you seeing?

Best,
Tom

---

### Post by thecomputerdoc on 2007-12-20
I experienced the same thing. I have a system 76 serval running ubuntu 7.1 Gusty. and have a generic kernel. The following things were my error audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured. 

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Being that I have a generic kernel this did the job for me. But read the article from techie below.:lolflag:


Then just run this command
sudo apt-get install linux-backports-modules-generic

Try the very simple solution proposed by LinuxTechie at

[http://linuxtechie.wordpress.com/200...work-in-gutsy/](http://linuxtechie.wordpress.com/200...work-in-gutsy/)

---

### Post by thomasaaron on 2007-12-20
You should not have to delete the sound control icon.
Running the system76 driver and rebooting should fix the problem.

Do you still get that error after running the driver?

---

### Post by uconvert on 2007-12-20
I have no sound either. I have an ASUS Z62FM (the same as Gazelle Value gazv4) and have been using the System76  Drivers. 

This happened once before, but drivers fixed it, but not this time. I am following suggestions on this thread and "lost sound with today's update," nothing works.

Please help, don't let the grinch steal my Christmas:mad:

---

### Post by Royal_Pwner on 2007-12-20
that link is a 404 error.

I tried to run the sys76 driver but nothing happened.

---

### Post by thomasaaron on 2007-12-20
Royal_Pwne,

What do you mean "nothing happened"?

Do you mean that when you pushed the button it just disappeared?
Or that it ran but didn't fix the problem AFTER rebooting?

And what computer do you have?

---

### Post by Royal_Pwner on 2007-12-20
After I put in the pass for administrative tasks, nothing happened.
I rebooted, still not fixed.

I have a serval performance.
200gb 7200rpm harddrive
nvidia 8600 graphics
2gb of ram
bluetooth
15.4" wxga+ screen

---

### Post by thomasaaron on 2007-12-20
OK, I just ran into this problem with a Serval here in the shop.
After updating, sound died. Running the driver and rebooting did not fix it.
Turned out that there was another kernel upgrade awaiting me!

I went to a terminal and entered these commands:
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

Then, I opened the System 76 driver and ran it (Install Tab / Install Button).

Then, I** rebooted**, and sound works.

Please try it again. I had to do it **twice** for some reason.

Once you've done all of that, go to System > Preferences > Sound and click the first "Test" button. What happens?

Best,
Tom

---

### Post by Peneus on 2007-12-20
Hello Tom,

As you suggested I did what you said twice and clicked on test sound and this is what I get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."

So it is still broken.
I have a Daru2 with  Gutsy and  system76 driver version 2.1.3.
 
Thanks

---

### Post by betes on 2007-12-20
just fyi-

I had no sound as well, with same symptoms as OP.  I updated the driver and rebooted and it was fixed, the kernal upgrade wasn't necessary (or had already happened through the system updater I suppose). (I have a Gazv5).

---

### Post by Royal_Pwner on 2007-12-20
That's the problem. My system76 drivers don't do anything. I enter the password, and nothing happens.

I don't know what's wrong.

---

### Post by Royal_Pwner on 2007-12-20
I ran it in terminal using
sudo system76-driver

and it said there was no module called gobject.
I have that stuff installed, though.

---

### Post by thomasaaron on 2007-12-21
UCONVERT,

You need to follow the advice on the following thread:
[http://ubuntuforums.org/showthread.php?t=641619](http://ubuntuforums.org/showthread.php?t=641619)

ROYAL_PWNER,

That's strange. Please answer the following questions:
1. Which Serval Perfomance to you have? (Look on the bottom for the model
number if you don't know.)

2. What version of Ubuntu are you running? (if you don't know: uname -r)

3. What desktop environment are you running? (K/X)ubuntu?

The reason I ask is this: If the System76 driver is throwing an error related to Gobject, it makes me wonder if you're running current Ubuntu or an older version with a correspondingly older version of Python.

---

### Post by Royal_Pwner on 2007-12-21
FL90 is the model.

I'm running 2.6.22-14-generic.

I'm running just plain ubuntu.
My python is the latest version.

I'm so confused, and I really need sound. One of the main uses of my computer is media.

---

### Post by DesiArnez6 on 2007-12-21
Sorry I haven't posted much, some health issues recently.
Anyway I have The Gazv4 with Feisty 7.04 Ubuntu (GNOME),

Many times after updates, the sound went out and the volume controls changes (with less options), a System 76 Driver Update, or System Restore always seemed to do the trick... not this time, tried twice, still no sound :(

---

### Post by thomasaaron on 2007-12-21
DeziArnez6,

You need to follow the advice on the following thread:
[http://ubuntuforums.org/showthread.php?t=641619](http://ubuntuforums.org/showthread.php?t=641619)


Royal_Pwner,

Double-click your speaker icon. In the resulting window, go to Edit > Preferences and select all available check boxes.

Now, describe your sound control settings under each tab. (Playback, Recording, Switches)

---

### Post by uconvert on 2007-12-21
Hey Folks~

 I found the problem for my machine (Gazv4).
I posted the fix on this thread
[http://ubuntuforums.org/showthread.php?t=644710&page=2](http://ubuntuforums.org/showthread.php?t=644710&page=2)

Good luck

---

### Post by Royal_Pwner on 2007-12-21
I can't even get that far. Screenie attached.

---

### Post by thomasaaron on 2007-12-21
Hi, Royal_Pwner.

(What does that mean, by the way? Interesting.)

Please send me an email at support(at)system76(dot)com.
I want to send you a .deb file to install. I think it might help.

Please also include in your email the output of...

uname -r
cat /proc/asound/version
and the version of your System 76 Driver
Your order number or the name the computer was ordered under

...for my refernece.

Best,
Tom

---

### Post by Royal_Pwner on 2007-12-21
I just sent the e-mail. Thanks.

---

### Post by DesiArnez6 on 2007-12-21
For me atleast, problem seems solved. Thanks Tom
 I went here as you said:
[http://ubuntuforums.org/showthread.php?t=641619](http://ubuntuforums.org/showthread.php?t=641619)

And found this advice:

"You might also try double-clicking on your speaker icon.
In the resulting window, go to edit > preferences and select all available checkboxes.

Then, go to the "switches" tab and try enabling/disabling (ext amp)"

After following that advice, the sound options look more normal, and sound is restored :)

---

### Post by Peneus on 2007-12-21
Dear Tom,

Could you post how you solve  Royal_Pwner problem. 
It looks like I am having the exact problem. 

(Daru2,gutsy,system76 driver version 2.1.3)
Thanks

---

### Post by Rowan187 on 2007-12-22
This is what happened to me when I switched to Gutsy (panV2). So i decided to not run the driver and that helped fine except for graphics card issues and a really slow boot, but after a bit of using it I realized I don't really like Gutsy, so I went back to Feisty on this laptop. If all else fails, maybe go with that option. Or keep working with the System76 team, it might be hard because they can't physically fix the problem for you, but they won't give up on you. They're awesome. I wish everyone with sound issues the best of luck, and I hope Hardy Herron (spelling?) goes in a better direction.

---

### Post by Canucktom on 2007-12-23
Hi all,

I had similar problems as described here. After an update, I had no sound at all.

As I found out after a while, the problem was the systems76 driver 2.1.3. I could not even restore the system or install the drivers with this version.
But as soon as I uninstalled 2.1.3 and went back to 2.1.1 everything is just fine.
Hopefully this helps some of you guys.

I am running Gutsy on a Gazellev4.

Tom

---

### Post by Peneus on 2007-12-23
Hello All,
I did what Canucktom did and it worked for me. Hopefully this helps systems76 staff fixing the problem. 
Thanks Caucktom. 

(Daru2,Gutsy,system76 -2.1.1)

Best,

---

### Post by zacharydanger on 2007-12-24
Much thanks, Canucktom!

I also had this exact problem on my Daru2, Gutsy, 2.6.22-14-generic kernel, System76 Driver 2.1.3 after some recent updates.

Rolling back to System76 Driver 2.1.1 solved the problem for me, too.

---

### Post by thomasaaron on 2007-12-24
Hello, all.  This was the deal with Royal_Pwner's comptuer.

There is a broken dependency in his System 76-driver. Python is throwing an error relating to the gobject module.

We discovered this by running the driver from a terminal (system76-driver).
The driver will crash from the onset and thow the aforementioned error.

If you guys have this same problem, please email me and let me know. I will be unable to do testing from my end until 12/3, as I'm out of state.  Meanwhile, I'm pointing Carl to this thread so he can have a look at it.


I've got a .deb file that will get your sound back up if the driver doesn't do the trick. Just send me an email (support@....).

---

### Post by asmiller-ke6seh on 2007-12-24
> **thomasaaron said:**
> I will be unable to do testing from my end until 12/3, as I'm out of state.

Do you mean until 01/03/2008? because you posted this an hour ago - on 12/24/2007.

Have a Merry Xmas, and a Happy New Year.

---

### Post by Royal_Pwner on 2007-12-25
I managed to lose my entire system trying to partition.
Could one of you resend that deb file?
And the system 76 driver?
Thanks. I'm really ****ed right now, I need sound.

---

### Post by zacharydanger on 2007-12-25
> **zacharydanger said:**
> Much thanks, Canucktom!

I also had this exact problem on my Daru2, Gutsy, 2.6.22-14-generic kernel, System76 Driver 2.1.3 after some recent updates.

Rolling back to System76 Driver 2.1.1 solved the problem for me, too.

Whoops, it seems as if I've spoken too soon. I've only gotten a partial return of my sound. When I boot my Daru2 I get the initial login window chime, but once I've actually logged in the normal startup sound doesn't play. Right now, the only place I've discovered that I can get sound to play are Amarok and Xine.

Any chance I could get ahold of that magical .deb?

UPDATE: I tried the system76 driver's restore functionality and now my sound is back and usable in everything. 

System > Administration > System76 Driver > Restore System [tab] > Restore followed by a reboot has at least my system's sound up and running.

---

### Post by thomasaaron on 2007-12-26
Royal_Pwner,

You should not need the .deb. Just download the System76 driver and run the restore function. This should now fix your sound. If it does not, send me an email at support.

Make sure you've got these bases convered:
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

Here are the instructions for getting/running the driver:

Make sure you're connected to the Internet.

From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.1.3.deb](http://planet76.com/repositories/system76-driver-2.1.3.deb)
sudo dpkg -i system76-driver-2.1.3.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

Reboot your computer.

---

### Post by Royal_Pwner on 2007-12-26
Wow, awesome.
It works now, after the reinstall.
Sweet.

Now, to deal with all that homework...

---

### Post by cwej on 2007-12-31
just as a data point-- 

After the last Ubuntu update that actually updated the Linux kernel (a couple weeks ago?-- last week) my sound didn't work either after the required reboot. However, having seen this before, I simply ran the System 76 driver (System --> system 76 Driver --> Install Drivers (tab) --> Install (arrow button). 

Et voila! Sound works again after install (takes a few minutes) and reboot.

The moral to the story is that I've been conditioned to expect that after a kernel update, the driver must be reinstalled. Makes sense...

---

### Post by thomasaaron on 2008-01-02
That is correct. 

ALSA is compiled against the kernel, so when kernel updates come down, ALSA goes belly up. The System76 driver just recompiles ALSA against the newer kernel.

---

### Post by Peneus on 2008-01-03
Thanks a lot guys.
That worked for me.

---

### Post by blue900 on 2008-01-16
I helped My Daughter get a SERP3 Serval Performance for Collage 
After a fresh install Kubuntu and Following the System76 Restore to new Guide, I was still not getting any sound. All the above posts helped me be confidant it should have been working. After checking and rechecking everything (sometimes I'm slow) I tried the Head Phone jack and it was working. What I was missing was, be sure the Front Sound Chanel is unmuted and Turned UP. I'm new to Laptops. 
The Kubuntu works Great on this Very nice Laptop she is Thrilled.
System76 is great, the laptop is great.

---

### Post by thomasaaron on 2008-01-17
Good job figuring it out.

Glad you guys like the machine. It's a sweety, huh?

---

### Post by zacharydanger on 2008-02-10
After some more recent updates, the sound on my daru2 went out **again**. This time (system76-driver 2.1.3) the driver's restore function didn't work. However, rolling back to driver version 2.1.0 and running the restore did the trick.

Running the restore from 2.1.0 also seemed to take a bit longer than 2.1.3. Almost as if 2.1.3 wasn't reinstalling the drivers it needed.

Just in case anyone else is in the same boat...

---

### Post by thomasaaron on 2008-02-11
That's strange that 2.1.3 didn't work. I'll have to try to replicate that.

Just a note, I noticed you put **"again"** in bold. I'm not sure if you realized it,
but whenever a kernel update comes down the pike from Ubuntu, it is likely to kill your sound. That's because ALSA is compiled against the kernel. If the kernel changes, ALSA must be re-compiled against the new kernel. That's what the driver is for.

---

