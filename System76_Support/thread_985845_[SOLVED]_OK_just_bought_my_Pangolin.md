---
title: "[SOLVED] OK just bought my Pangolin"
date: 2008-11-18
forum: System76 Support
---

### Post by ResumeMan on 2008-11-18
Was getting frustrated with my current laptop's lid flopping all over the place. Was either spend probably $200 to replace the hinges on an almost-5-year-old machine or take the plunge :)

```
Pangolin Performance (PAN-P4) = $1,079.00
       Operating System Ubuntu 8.10 (Intrepid Ibex) 64 Bit Linux
       Display Resolution 15.4" WXGA Super Clear Glossy LCD (1280 x 800)
       Processor Core 2 Duo P8400 2.26 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
       Memory 4 GB - DDR2 800 MHz - 2 DIMMs
       Hard Drive 320 GB 5400 RPM SATA II
       Optical Drive CD-RW / DVD-RW
       Wireless 802.11 agn
       Bluetooth Bluetooth
       Extra Battery no extra battery
       Extra AC Adapter no extra AC adapter
       Car AC Adapter no car AC adapter
       Laptop Bag no bag
       Hardware Warranty 1 Yr. Ltd. Warranty and Technical Support
```

Support guys -- I had it shipped to a different address than my billing addy (so manual confirm), and requested 3-day shipping -- can I expect it to arrive in CA by next Weds (i.e. so I'll have it over the long weekend)?

Thanks

---

### Post by thomasaaron on 2008-11-18
Probably not. There is a 5-day build process before shipping. 
Could potentially arrive before the weekend, though.

You'd probably be better off requesting status via email to sales, though.

sales(at)system76(dot)com

---

### Post by jeamer on 2008-11-18
wow, insane what you can get for the money these days! I paid the exact same for the pangolin value a few years ago, and it certainly didn't look as sweet as this machine!

---

### Post by Lee_Machine on 2008-11-18
another reason why I bought a S76 Pangolin over a Macbook Pro that has almost the same specs AND it's $900 cheaper.

---

### Post by ResumeMan on 2008-11-26
> **ResumeMan said:**
> 

Support guys -- I had it shipped to a different address than my billing addy (so manual confirm), and requested 3-day shipping -- can I expect it to arrive in CA by next Weds (i.e. so I'll have it over the long weekend)?



Arrived today! Wohoo! Great so far. The mouse pad buttons are a little "tough" and with the fingerprint reader between them I'm having trouble "middle clicking," but otherwise it's really sweet so far.

I'll post more thoughts when I've had time to fiddle with it some.

---

### Post by ResumeMan on 2008-11-28
OK so I've now been playing with this for a few days and for the most part it's excellent. Very fast and smooth, and generally pleasant to work with.

I'm having a few problems relating to power management though:

1. _Lost Sound on Resume_ This is the same problem reported [here]("http://ubuntuforums.org/showthread.php?t=908816&highlight=pangolin+sound+resume") and addressed in this [bug report]("https://bugs.launchpad.net/system76/+bug/302160") except that I'm running Intrepid. I tried re-running the S76 driver (version 2.2.8 ), but no luck. Should I contribute to the existing bug report? Start another since it's a different OS? Any ideas?

2. _Can't reboot properly_ This has me a little weirded out. When I reboot, Ubuntu begins to start up, but then goes to a blank gray screen. I've tried sitting on it for several minutes, and nothing happens. To get up again, I need to hold the start button to turn it off and then restart (and everything is fine). Any idea what's happening here??

Thanks, I realize it's a holiday weekend, so I'm not expecting an instant response.

---

### Post by ResumeMan on 2008-11-28
Oh, here is what I've done since I got it. I certainly may have missed something but this should be most of it.

1. Nos. 3 through 8 and 10 in [this ]("http://davestechsupport.com/blog/2008/10/31/10-things-to-do-after-you-install-ubuntu-linux/")how-to. I imported a couple of existing Windows VDIs into VirtualBox

2. Installed Crossover Linux Pro and installed Rosetta Stone and World of Warcraft (trial edition) using it.

3. Installed Freeciv and Freecol.

4. Installed Gmount-iso and Htop.

5. Installed Samba client and moified /etc/fstab to auto-mount some shares.

6. Installed RealPlayer and VLC.

I think that's pretty much it. If I think of any other tweaks I made I'll add to the list.

---

### Post by ResumeMan on 2008-11-28
So now the sound does seem to be working on resume. Go figure. It seems, possibly that it may bork after it's been suspended for awhile, but not when it's only suspended briefly. I'll keep tracking it...

---

### Post by thomasaaron on 2008-12-01
Run your System76 Driver and reboot. It adds a line to your alsa-base file that is required for sound after resuming. If that doesn't work, then we still may have a bug to squash.

---

### Post by ResumeMan on 2008-12-01
> **thomasaaron said:**
> Run your System76 Driver and reboot. It adds a line to your alsa-base file that is required for sound after resuming. If that doesn't work, then we still may have a bug to squash.

I will certainly try that this evening -- but has the driver changed since the weekend?? I've already run the driver and rebooted (or tried to -- see Item #2 on my list of concerns [any comment on that one btw?]) and the sound is still hinky. Done it a couple times actually.

On further use of the thing this weekend, the sound sometimes works on resume and sometimes doesn't -- and sometimes it doesn't work for a while and then starts working at some point.

Oh, I've also had the "network disabled" bug that someone mentioned. I haven't had a chance to try the fix mentioned, and it hasn't been a big deal, but I thought I'd mention it.

---

### Post by thomasaaron on 2008-12-01
You should be running version 2.2.7 of the driver. Go to System > Admin > Sys76 Driver > About to check it. If not, you can download that version from [http://planet76.com/repositories](http://planet76.com/repositories).

Regarding the blank screen, does it do that every time, or is it intermittent?

---

### Post by ResumeMan on 2008-12-01
> **thomasaaron said:**
> You should be running version 2.2.7 of the driver. Go to System > Admin > Sys76 Driver > About to check it. If not, you can download that version from [http://planet76.com/repositories](http://planet76.com/repositories).

Regarding the blank screen, does it do that every time, or is it intermittent?

It's actually 2.2.8; I shouldn't backtrack should I?

I think the gray screen is every time. At least very close to it.

---

### Post by thomasaaron on 2008-12-01
I'm sorry. I meant 2.2.8.
That is perfect.

---

### Post by ResumeMan on 2008-12-02
OK, so the sound issue is "sometimes" an issue. Some resumes it comes back and the sound is fine, sometimes there's no sound, and other times it has no sound when I resume, but the sound kicks in after awhile.

Interestingly, the "about" on the on the S76 Driver says 2.2.8, but when I run it, it says "Complete -- 2.2.7." And the latest version on the webpage here: [http://planet76.com/repositories/](http://planet76.com/repositories/) says v 2.2.7. Am I running the latest version?

The gray screen doesn't happen every single time, but pretty close to it. And a little patience shows it isn't dead; in about 2-1/2 minutes, the gray screen goes black then it goes to the BIOS screen, and boots normally. So it does work, but it's kind of weird and is concerning me.

---

### Post by thomasaaron on 2008-12-03
> Start another since it's a different OS?

What does that mean? You're not running Ubuntu? If your system76 driver is running, I'm assuming you're running [K/X]Ubuntu? If so, that could be part of the problem, and we're not really set up to test with those. Please clarify.
> 

[QUOTE]Interestingly, the "about" on the on the S76 Driver says 2.2.8, but when I run it, it says "Complete -- 2.2.7." And the latest version on the webpage here: [http://planet76.com/repositories/](http://planet76.com/repositories/) says v 2.2.7. Am I running the latest version?

You're running the latest version. 2.2.8 hasn't been posted yet. Still more work being done on it. That's probably why it reports 2.2.7.

> The gray screen doesn't happen every single time, but pretty close to it. And a little patience shows it isn't dead; in about 2-1/2 minutes, the gray screen goes black then it goes to the BIOS screen, and boots normally. So it does work, but it's kind of weird and is concerning me. 


Please describe exactly when the gray screen appears in the boot process. And let me know if it is from a fresh start-up or on resuming from suspend.

---

### Post by ResumeMan on 2008-12-03
> **thomasaaron said:**
> What does that mean? You're not running Ubuntu? If your system76 driver is running, I'm assuming you're running [K/X]Ubuntu? If so, that could be part of the problem, and we're not really set up to test with those. Please clarify.

It means I'm running Ubuntu 8.10, not 8.04. The title of the [bug report]("https://bugs.launchpad.net/system76/+bug/302160") was "Hardy Panp4n no sound on resume after HIbernate" so I didn't know if I should start a new bug for the new version.



> Please describe exactly when the gray screen appears in the boot process. And let me know if it is from a fresh start-up or on resuming from suspend.

It's when I reboot the machine entirely. I recall, though I'm not 100% sure, that it happens whether or not I have suspended/resumed since the last boot. 

This happens at shutdown. When I request a restart, the Ubuntu splash screen pops up with the orange meter, and when it reaches the end of the meter, at the point I would normally expect the screen to go black for a second or so as it shuts off, the gray screen appears. It's grayish-white, with some mottled dark gray/black streaks. As I said, it appears to clear after about 2.5 minutes and goes to the boot screen. At that point everything appears to function normally.

---

### Post by thomasaaron on 2008-12-03
Please forgive me. I'm not trying to belabor this, but...

> I'm not 100% sure, that it happens whether or not I have suspended/resumed since the last boot.

...could you please test this. To properly focus my efforts, I really need to know if this is connected in some way to suspend/resume. 

If it is, the problem is slightly more forgivable, as suspending has been a work in progress for a long time with Linux. While it's 500% better than it was a year and a half ago, there are still issues to iron out.

If suspend/resume is not involved, we can rule that out and focus our efforts elsewhere.

---

### Post by ResumeMan on 2008-12-04
OK so it appears that the weird grey screen happens *on shutdown when i am logged in.* So if I am sitting at the Gnome desktop and either choose shutdown or restart, it happens (if I tell it to shut down, the grey screen simply appears for a couple minutes before it shuts off). And it happens whether or not I have suspended/resumed since last time I powered up.

But if I either shut down or reboot when at the Ubuntu login screen, all's good.

Note that I'm going to be out of the country for  a few days starting in the morning (w/o the laptop), so feel free to put this problem on ice through the weekend as I won't be trying any fixes :)

Thanks

---

### Post by thomasaaron on 2008-12-04
Are you shutting down all running applications before shutting down the computer? Or are you leaving something open? If so, what?

---

### Post by ResumeMan on 2008-12-07
Shutting down all applications. In my tests the other day, I was frequently rebooting (or shutting down) immediately after logging in after the previous restart.

---

### Post by thomasaaron on 2008-12-08
Please turn off your desktop effects (System > Preferences > Appearance > Visual Effects > None) and see if the problem still occurs.

---

### Post by BlazinNightSkye on 2008-12-10
I just ordered the exact same laptop and specs, i cant wait to get it! I have a preference for Kubuntu, will i have any problems running it?

---

### Post by ResumeMan on 2008-12-11
> **thomasaaron said:**
> Please turn off your desktop effects (System > Preferences > Appearance > Visual Effects > None) and see if the problem still occurs.

That sounded like a silver bullet when I read it, but unfortunately, no help. With desktop effects off, it still did it.

---

### Post by thomasaaron on 2008-12-11
Based on this...
> OK so it appears that the weird grey screen happens on shutdown when i am logged in. So if I am sitting at the Gnome desktop and either choose shutdown or restart, it happens (if I tell it to shut down, the grey screen simply appears for a couple minutes before it shuts off). And it happens whether or not I have suspended/resumed since last time I powered up.

But if I either shut down or reboot when at the Ubuntu login screen, all's good.

...I would say it is definitely related to some configuration. Try creating another user account. See if the problem happens there. If not, you can transfer stuff to the new account, delete the old account, and then rename the new account to the same name as the old one.

---

### Post by ResumeMan on 2008-12-12
Allrighty then.

I do believe I have isolated the trigger for the grey screen. No idea *why,* but I think I now know *when.*

It's after connecting to my wireless network for the first time with a user. FWIW I've got a Linksys wireless-G router. I have run other laptops using both Ubuntu and Windows on this network and never encountered a glitch.

I created a new user as you suggested, and when I rebooted it worked just fine. I logged back in, and for whatever reason decided to hook into the wireless. I rebooted again and -- grey screen.

So I created another user, logged in, rebooted, all was well. I did it  once or twice more, and again, all was fine. Logged into the network, rebooted, and -- grey screen.

So having said that, I think that my statement that the incident is not triggered from the login screen is incorrect. In those tests, I had rebooted into the login screen, and then immediately rebooted -- so I had obviously never connected to the network...

Very strange, let me know if there is anything else I can test.

---

### Post by earrame on 2008-12-14
> **BlazinNightSkye said:**
> I have a preference for Kubuntu

Before this System76 Pangolin arrived on my doorstep I had used KDE for about seven years or so. While researching which notebook computer to buy I kept looking into kbuntu systems. I finally decided to go with System76. Gnome is very nice but I miss KDE. I'm not going to persue a switch to kbuntu but if I start seeing info here and there about success stories temptation may over come me.

---

### Post by BlazinNightSkye on 2008-12-14
> **earrame said:**
> Before this System76 Pangolin arrived on my doorstep I had used KDE for about seven years or so. While researching which notebook computer to buy I kept looking into kbuntu systems. I finally decided to go with System76. Gnome is very nice but I miss KDE. I'm not going to persue a switch to kbuntu but if I start seeing info here and there about success stories temptation may over come me.

Well i plan on being one of those people who run KDE over gnome on my new laptop, i get it friday. I will keep you posted how it goes!

---

### Post by thomasaaron on 2008-12-15
ResumeMan,

That sounds pretty solid. If you haven't done so thus far, please install the backports modules: ```
sudo apt-get install linux-backports-modules-intrepid
``` and see if that corrects the problem. I doubt it will, but it's a good place to start.

Also, I doubt any of the other computers have this particular wirless card, and I'm not getting this complaint from elsewhere, so there may be some conflict there.

What is the model number of your router?

Also, please post attach the files that these commands create on your desktop *after* the next failure, and we'll have a look.
```

cat /var/log/syslog > ~/Desktop/syslog.txt
cat /var/log/daemon.log > ~/Desktop/daemon.log
```

---

### Post by ResumeMan on 2008-12-15
> **thomasaaron said:**
> ResumeMan,

That sounds pretty solid. If you haven't done so thus far, please install the backports modules: ```
sudo apt-get install linux-backports-modules-intrepid
``` and see if that corrects the problem. I doubt it will, but it's a good place to start.

It told me that the backports modules were already the most recent version.

> Also, I doubt any of the other computers have this particular wirless card, and I'm not getting this complaint from elsewhere, so there may be some conflict there.

What is the model number of your router?

It's a Linksys WRT54GS. I've never updated the firmware; the firmware version is v2.07.1.

> Also, please post attach the files that these commands create on your desktop *after* the next failure, and we'll have a look.
```

cat /var/log/syslog > ~/Desktop/syslog.txt
cat /var/log/daemon.log > ~/Desktop/daemon.log
```

Attached

---

### Post by thomasaaron on 2008-12-16
OK. I have to give it some more thought, but these errors look interesting... But they have nothing to do with wifi.


> Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Dec 15 20:42:19 ubuntu pulseaudio[6768]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 15 20:42:19 ubuntu pulseaudio[6770]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 15 20:42:19 ubuntu pulseaudio[6770]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 15 20:42:34 ubuntu x-session-manager[6675]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Dec 15 20:42:35 ubuntu pulseaudio[6770]: module-x11-xsmp.c: X11 session manager not running.
Dec 15 20:42:35 ubuntu pulseaudio[6770]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by ResumeMan on 2008-12-16
Hmmmm...well I don't know anything about this stuff, but the one thing that I'll bring back from upthread is that, frequently but not always, when I resume from suspend I have no sound.

Since the grey-screen happens even unrelated to suspending that probably isn't it, but -- couldn't hurt to mention it.

---

### Post by thomasaaron on 2008-12-16
OK, I'm almost positive this has something to do with pulseaudio. You have a ton of pulse audio errors. I'm pretty sure your problem is related to this...

I see the same pulseaudio errors primarily related to firefox and virtual box.

So, just a few clarification questions:

1. Are you running VirtualBox?
2. Have you downloaded any plugins for Firefox?
3. Does the problem occur if you boot your computer up but *never* open virtualbox (assuming you have it) or firefox? Or any other sound-related programs, for that matter.
4. You are running Ubuntu, right? Not Kubuntu?

i.e. Let's try to narrow this down as much as possible... While you're doing that, I'll keep researching these logs.

EDIT: Please include the output of: uname -r

---

### Post by ResumeMan on 2008-12-16
1. Yes. I don't actually *run* it that often, but it's installed.
2. My add-ons are:[INDENT]Foxmarks
InFormEnter
TorrentFlux-Add (I think this is unsupported by Mozilla)
Ubuntu Mods
Adblock Plus
Answers

I think I'm using the beta Flash player for 64 bit, but I think this was even happening before I installed it.
[/INDENT]
3. Yes. If I just boot, login (automatically connecting to wireless) and reboot, it happens.
4. Ubuntu as installed in the factory.

---

### Post by ResumeMan on 2008-12-17
Missed the follow-up

> **thomasaaron said:**
> 
EDIT: Please include the output of: uname -r

2.6.27-7-generic

---

### Post by thomasaaron on 2008-12-18
You may want to update your computer. I'm running 2.6.27-9-generic. So, you are a bit behind. If your update icon isn't showing, you can go to a terminal and run these commands...

```
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade
```

...to bring everything up to date. Let's see if that helps. If not, we shall follow the rabbit hole deeper still.

---

### Post by ResumeMan on 2008-12-18
No kidding? I've only had it for 3 weeks and there've been two updates!

Actually I did have an update notification yesterday, but I don't think I saw anything about the kernel.

OK I will do that this evening and see if that helps...

---

### Post by thomasaaron on 2008-12-18
OK. If it doesn't work, go to System > Admin > Software Sources > Update (tab) and enable proposed. Then run those commands. Let me know what the output of...

```
uname -r

```
...is when you're finished.

---

### Post by ResumeMan on 2008-12-18
OK I did all that.

I added the repo and did the update. Note that on "Update" I got an error because apparently the public key wasn't loaded for the Medibuntu repository. But I did some research and added the keyring. No error there anymore.

During the kernel update (it's version  -10 now btw) I must have made a mistake when it was asking me what I wanted to do with menu.lst; it just moved ahead without asking me whether to make modifications. So when I rebooted it just went into version -7. I edited the Grub menu to add -10 (which was a little scary!). 

I rebooted into kernel version 10, the screen showed a bunch of checks, including an error on VBox, which wasn't a surprise (I learned on another computer that you have to recompile the VBox kernel when you upgrade the Linux one). Running uname -r results in "2.6.27-10-generic"

I decided to try rebooting w/o messing with VBox since you said a lot of errors were associated with that.. Grey screen.

I rebooted again, and recompiled the VBox kernel as directed by VBox. Grey screen. Tried it fresh. Grey screen.

Sooooo....bring a flashlight down that hole Mr. Aaron, and say hi to Bre'er Rabbit for me ;)

Thanks for all your effort, I know this is a knotty one...

---

### Post by thomasaaron on 2008-12-19
Let's test with the -9 kernel. The -10 kernel is a proposed kernel, and it might have some bugs left in it.

First, run this command:
sudo apt-get install linux-restricted-modules-`uname -r`
Is the problem still there?

Let's start eliminating possibilities. First, let's eliminate the wireless card as a cause (if we can...). Right-click on the networking icon and disable wireless. Then see if the problem happens. If it still happens, you can go ahead and re-enable wireless and move to the next step.

Let's eliminate the nVidia driver as the problem. Go to System > Admin > Hardware drivers and disable the 177 nvidia driver. Hopefully this will get us running on nV (which sucks and will give you lousy resolution... but does the problem still occur?

---

### Post by ResumeMan on 2008-12-20
OK so first of all I don't think I was ever given the option to use the -9 kernel; I was using -7 out of the box, and when I upgraded it went straight to 10. Are by chance all the kernels included recursively? That is, could I re-edit my Grub menu to include a -9 option? If not how can I install it?

Anyhow, continuing on with 10 -- I disabled wireless and the problem still occurred. That said, when I rebooted, it logged right back into the network; is there a way to turn it "off" so that it has to be manually reactivated?

So then I did the nvidia thing. And it didn't solve the problem -- but it may have revealed it...

When I shut down, after the shut-down splash, instead of going to the mottled grey screen, it went to a black screen with the following writing:

```
acpid exiting
[129.476365] CIFS VFS: Server Not Responding
[129.476447] CIFS VFS: CMD 50 Mid 516
```

And then after about a minute it repeated the two lines after the "acpid" line, then in another minute or so it rebooted.

I rebooted again, and it did the exact same thing, except it said Mid 138 instead of 516; then a third time Mid 29.

A quick google search showed somebody responding thusly:
> cmd 50 is an SMBtrans2 call. Can you get ethereal/wireshark capture traces from a system in this state ? 

Anyhow hope this gives you a clue...

Edit: To be clear, I use SMBclient to access a local LAN Samba fileserver and use it routinely. I might have left that off of my initial descriptions of the things I've done since I got it.

---

### Post by ResumeMan on 2008-12-20
In case it helps, here is the relevant portion of my /etc/fstab file:

```
#Samba shares on Dell
//192.168.1.5/SharedDocs /media/Dell_Share   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
#Samba shares on gPC Server
//192.168.1.50/GDead /media/GDead   smbfs  auto,credentials=/root/.credentials,uid=1000,gid=1000,umask=003,user   0 0
//192.168.1.50/files1 /media/server   smbfs  auto,credentials=/root/.credentials,uid=1000,gid=1000,umask=003,user   0 0
```

I have a Windows desktop ("Dell") with a folder I've chosen to share via the windows interface, and a Ubuntu computer ("gPC") with a Samba server.

On my other laptop, file sharing is a bit of a problem as well. When I suspend/resume, the share links "break" and I can't access or mount them. I actually need to unmount them and then re-mount. On the Pangolin, there is no apparent problem with the shares on resume (apart from the errors in the previous post).

---

### Post by ResumeMan on 2008-12-20
...and that right there is the problem.

I unmounted all three shares, and rebooted, and it worked just fine. So my earlier troubleshooting was slightly incorrect -- the problem wasn't that I had connected to **wifi**, it was that when I logged in it mounted the **file shares**.

I tried selectively unmounting the Windows share, and then selectively unmounting the two Ubuntu shares, and the problem happened in each case. So I'm thinking the solution may take one of three forms:

1. Did I screw something up in the /etc/fstab? I really don't know anything about what those commands mean and was just following [this guide]("http://ubuntuforums.org/showthread.php?t=280473"). If there's something I should tweak, that would be fine.

2. As I understand it, there are a series of scripts that get executed when shutting down, right? I may just need to put a new script that unmounts the shares. But I don't know too much about that either, and would look for step-by-step instructions.

3. Is there a mechanism, other than Samba server, to share files between Unix machines? I will still maintain the Samba shares as I have other Windows computers that need access to those files, but if there is a way to share more directly between the Pangolin and the Linux desktop, that would be fine. I really don't need the share to the Windows box, I only have that mounted because it's there. Indeed, I was hoping that the problem was just that one share, in which case I would have just dropped that one.

I'm glad I at least know what the issue is!

---

### Post by jdb on 2008-12-20
> **ResumeMan said:**
> ...and that right there is the problem.

I unmounted all three shares, and rebooted, and it worked just fine. So my earlier troubleshooting was slightly incorrect -- the problem wasn't that I had connected to **wifi**, it was that when I logged in it mounted the **file shares**.

I tried selectively unmounting the Windows share, and then selectively unmounting the two Ubuntu shares, and the problem happened in each case. So I'm thinking the solution may take one of three forms:

1. Did I screw something up in the /etc/fstab? I really don't know anything about what those commands mean and was just following [this guide]("http://ubuntuforums.org/showthread.php?t=280473"). If there's something I should tweak, that would be fine.

2. As I understand it, there are a series of scripts that get executed when shutting down, right? I may just need to put a new script that unmounts the shares. But I don't know too much about that either, and would look for step-by-step instructions.

3. Is there a mechanism, other than Samba server, to share files between Unix machines? I will still maintain the Samba shares as I have other Windows computers that need access to those files, but if there is a way to share more directly between the Pangolin and the Linux desktop, that would be fine. I really don't need the share to the Windows box, I only have that mounted because it's there. Indeed, I was hoping that the problem was just that one share, in which case I would have just dropped that one.

I'm glad I at least know what the issue is!

Samba is primarily for interfacing with windows machines.

For linux to linux NFS is the way to go for file sharing and CUPS for printer sharing.

jdb

---

### Post by rtrahan on 2008-12-21
> **ResumeMan said:**
> Was getting frustrated with my current laptop's lid flopping all over the place. Was either spend probably $200 to replace the hinges on an almost-5-year-old machine or take the plunge :)

```
Pangolin Performance (PAN-P4) = $1,079.00
       Operating System Ubuntu 8.10 (Intrepid Ibex) 64 Bit Linux
       Display Resolution 15.4" WXGA Super Clear Glossy LCD (1280 x 800)
       Processor Core 2 Duo P8400 2.26 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
       Memory 4 GB - DDR2 800 MHz - 2 DIMMs
       Hard Drive 320 GB 5400 RPM SATA II
       Optical Drive CD-RW / DVD-RW
       Wireless 802.11 agn
       Bluetooth Bluetooth
       Extra Battery no extra battery
       Extra AC Adapter no extra AC adapter
       Car AC Adapter no car AC adapter
       Laptop Bag no bag
       Hardware Warranty 1 Yr. Ltd. Warranty and Technical Support
```

Support guys -- I had it shipped to a different address than my billing addy (so manual confirm), and requested 3-day shipping -- can I expect it to arrive in CA by next Weds (i.e. so I'll have it over the long weekend)?

Thanks

So how do you like it? I just ordered the exact same specs from System 76....

---

### Post by ResumeMan on 2008-12-21
Rather than make this thread even more cluttered than it already is, I started a [new one]("http://ubuntuforums.org/showthread.php?t=1017882") for a review. 

Reader's Digest version: I like it a lot, and have gotten very good support for what I didn't like (i.e. see this thread ;))

---

### Post by ResumeMan on 2008-12-21
So -- I set up NFS using [this guide]("http://ubuntuforums.org/showthread.php?t=249889"), and modified my fstab to get rid of all the Samba shares and put in the 2 NFS shares I need. The one tweak I needed to make was to configure my server firewall to allow connections from the Pangolin's IP address.

Now I have the shares working, and do not seem to have any problems rebooting. Seems as though, problem solved.

---

### Post by thomasaaron on 2008-12-22
Excellent work!

---

