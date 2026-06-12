---
title: "Syncing iPod to iTunes in VMWare Windows Guest"
date: 2007-11-15
forum: Virtualisation
---

### Post by phillywize on 2007-11-15
Hey all,

Any thoughts on syncing an iPod to iTunes running in a Windows VMWare guest?  Anyone else doing it?  How's it going?

I know there are many FOSS options out there, and Gutsy comes with support, but this is a situation when I just have to say I'm stuck on iTunes.  I've made this arrangement work by using iTunes installed on a Windows running under VMWare server.

My main issue is coordinating USB handling between Gutsy and the VM.  Gutsy recognizes and mounts the iPod...if I then mount the iPod under Windows (in VMware, VM>Removable Devices>USB Devices>Apple iPod), I get an unsafe ejection error from linux.  What I've been doing is (duh) unmounting in linux, then mounting as above in the Windows VM, and it all works great...when it works.

Here are my outstanding issues:

- VMWare does not reliably recognize that my iPod is connected -- usually I have to leave it plugged in for a few minutes before VMWare discovers it and can make it available to Windows.

- This crazy back and forth arrangement appears to have corrupted my iPod on one occasion, necessitating a full restore.  Of course, the iPod itself worked fine -- allowing full access to everything I had on it -- notwithstanding that iTuness thought it was corrupted.  Also, linux could read the thing just fine.

- Occasionally, without *actually]* corrupting the iPod, windows will only recognize it as a corrupted iPod - but when I eject and reconnect it, it's all good (notwithstanding the one time it was really corrupted and required a restore).

Other than that, I think this is a good arrangement.

Here's what I've done to make it work:

- Kept my iTunes directory on my linux partition, shared with the VM by way of samba...much more comfortable than either (a) giving the VM  access to a real drive (not a great option since I'd have to install an ext3 driver in windows anyway); or (b) sticking my music library into a virtual disk (yikes).

- I use firefly/mt-daapd to share my library from linux, rather than iTunes.  A little more flexible.  And it's kind of trippy to see my library as a share in iTunes.

- Other than that, not much.


Anyhow, anyone else doing it?  How's it going?  Happy to lend a hand where I can.

---

### Post by phillywize on 2007-11-18
Well, I know *someone* will eventually search for, and find this thread, so I'll post my progress to date:

(Please note, **this is _not_ a howto!**  For starters, I don't know what I'm doing or why it works.  This is all basically the epistemological equivalent of sorcery.  So I can't really tell you how to do it...but if you're having similar problems, or know a sure solution, please, let's do talk.  In the meantime, this is what's working, more or less, for me.)

I've had some reliability problems with syncing since my last post.  At one point I couldn't get iTunes in my Windows guest to recognize my iPod properly -- no matter what I did, it told me that it detected a corrupt iPod that would have to be restored (i.e., blanked and then everything loaded back onto it).

Unwisely, I went for this time consuming operation.  It worked, but then the next time I went to sync, the same thing happened (iTunes:  "you have a corrupt iPod, etc.").  This time I didn't do the restore...instead I did some more monkeying.  Here's what has worked most reliably (although not flawlessly) for me:

- With Windows running in VM, connect my iPod with the USB cable.  The Ubuntu host recognizes and mounts the iPod.

- If I immediately check under VM>Removable Devices>USB Devices>Apple iPod, there's no iPod...yet.  I wait a few minutes, and usually it shows up there.  It has no check mark next to it, which, I divine, means that the potential iPod USB connection is known to VMWare, but the connection is not made yet.  So as not to make further trouble for myself (by damaging the iPod file system), I eject it from the Ubuntu host.

- Miraculously, it remains known to VMWare.

- I then select the iPod in VM>Removable Devices>USB Devices>Apple iPod.  Windows then recognizes and mounts the iPod.

- I start iTunes, which, after some cogitation, recognizes and syncs my iPod.  This process also seems to work with iTunes already running.  I don't think it's the most delicate aspect of it.

When I've tried to let select the option in iTunes to make the iPod available in windows as a drive, it generally causes trouble:  iTunes unmounts and remounts the iPod to effect the change, but when it's remounted, iTunes thinks it's corrupted (which it isn't).

Anyhow, we'll see how this goes.  I'll keep talking to myself here in hopes that it will start a helpful dialog, or otherwise be useful.  But remember, I don't know what I'm doing.  :-D

---

### Post by flaggh on 2007-11-19
I have been trying for months to get my iPod to sync through iTunes in a virtual guest XP install.  I have used exactly the same steps as you and can only get as far as having XP detect a removable storage device.  The VMware menu lists Apple iPod under USB devices but XP does not properly detect the iPod.  I've tried using both VMware server and Virtualbox with no success on either one.  I have not tried the new VMware server beta, is that the one you are using?

My computer is an older laptop that only has USB 1.1 ports.  I never had any problems syncing my iPod when XP was the base OS.  I've synced using banshee and gtkpod but would still prefer using iTunes.  I've even tried RockBox but quickly removed that after it kept freezing up on me.  

I believe my older laptop hardware is to blame for my syncing problems in VMs, but I cannot think of any way to confirm this.

---

### Post by phillywize on 2007-11-19
> **flaggh said:**
> I have been trying for months to get my iPod to sync through iTunes in a virtual guest XP install.  I have used exactly the same steps as you and can only get as far as having XP detect a removable storage device.  The VMware menu lists Apple iPod under USB devices but XP does not properly detect the iPod.  I've tried using both VMware server and Virtualbox with no success on either one.  I have not tried the new VMware server beta, is that the one you are using?

My computer is an older laptop that only has USB 1.1 ports.  I never had any problems syncing my iPod when XP was the base OS.  I've synced using banshee and gtkpod but would still prefer using iTunes.  I've even tried RockBox but quickly removed that after it kept freezing up on me.  

I believe my older laptop hardware is to blame for my syncing problems in VMs, but I cannot think of any way to confirm this.

I'm using VMWare Server 1.0.3, and have not tried the beta.  I would think that if anything, the USB 1.1 would be an advantage inasmuch as it's more basic (and ubiquitous).  But I could be wrong about that.

Have you tried syncing with iTunes running already?

Also, have you tried ejecting your ipod from XP?  I've noticed that when I eject, windows itself recognizes that there's an iPod in the set of devices being deactivated.  That might be helpful on the off chance that your problem is more with windows than with the vm.

Sorry not to be of more help!  I'm the paradigmatic ubuntu user.  Tech savvy, willing to mess around, but at the end of the day, not terribly knowledgeable in the finer points of linux.

---

### Post by phillywize on 2007-11-20
> **flaggh said:**
> I have been trying for months to get my iPod to sync through iTunes in a virtual guest XP install.  I have used exactly the same steps as you and can only get as far as having XP detect a removable storage device.  The VMware menu lists Apple iPod under USB devices but XP does not properly detect the iPod.

You know, here's another thing that has worked for me:  after you have windows recognize that you have *something* plugged into a USB port -- and I assume at this point, "Apple iPod" is recognized and checked off in VMWare, eject from within Windows, leaving the VMWare setting alone (don't uncheck "Apple iPod").  Disconnect the iPod, and plug it back in.

I know, you've been at this a long time, so you probably tried it already, but just in case.  I have noticed that sometimes Windows recognizes my iPod as corrupt the first time around, but if I do the above once or twice, it finally gets it.

---

### Post by flaggh on 2007-11-20
Thanks for taking the time to think about this and offer suggestions.  My experiments trying to get this to work have not always been so methodical so I've lost track of the exact conditions I've used in the past.  I will definitely give these a try next chance I get and report back.

---

### Post by casposa on 2007-11-21
that's a great workaround! it works! yes....I'm finally going to kick out my windows partition...(as a have a classic ipod...native linux libraries and programs don't work yet...)

---

### Post by phillywize on 2007-11-21
> **casposa said:**
> that's a great workaround! it works! yes....I'm finally going to kick out my windows partition...(as a have a classic ipod...native linux libraries and programs don't work yet...)

Glad it worked...what problems were you having (detecting as corrupt, etc.), and what worked?  I think it will be helpful for future readers to document what does and doesn't work.

I have been enjoying continuing success with the approach I set out.  As long as I follow the rules, the system seems pretty robust.

One thing I haven't been able to do is sync photos -- that somehow triggers redetection of the iPod as corrupt when I try to sync photos (iTunes actually sees two iPods, though only one is plugged in:  the actual iPod, and the "phantom" corrupt one).

Anyhow, it would be nice to have a fix, rather than this odd semi-workaround.

---

### Post by flaggh on 2007-11-22
I've tried the methods you've suggested and still no luck with my VMware guest XP installation recognizing my iPod.  Thanks for the ideas anyway!

---

### Post by phillywize on 2007-11-24
> **flaggh said:**
> I've tried the methods you've suggested and still no luck with my VMware guest XP installation recognizing my iPod.  Thanks for the ideas anyway!

Yeah, I just tried an XP VM with my iPod, and following the steps I set out above for doing it with W2k, and no luck.  Something's different about XP.

---

### Post by phillywize on 2007-11-24
I think the best bet is to search around the VMWare forums.  Found this, a kernel patch, which is said to have worked (umm, around 2005, but still with the 2.6 kernel). 

[http://communities.vmware.com/message/295175#295175](http://communities.vmware.com/message/295175#295175)

 I'd have to dust off my limited kernel compilation skills, and figure out how to apply a patch like this to do it.  Not high on my list at the moment.

With a little more research, it looks like it's a race between Virtualbox and VMWare on this issue, since neither can presently sync an iPod reliably with iTunes running under a Windows XP guest on a 2.6.x linux kernel host.  I am following the virtualbox progress in [this thread]("http://ubuntuforums.org/showthread.php?t=475365").

Go figure.

---

### Post by flaggh on 2007-11-28
After reading how you tried and failed to get your iPod to work in an XP guest, I dug up a copy of Win2k and created a VM to see if I could try and reproduce your success in a Win2k guest OS and it detected my iPod!  I haven't had the chance to try syncing it yet, but this is definitely a step forward!  Hopefully tonight I'll have the opportunity to play with it some more.  I'll keep you updated.

---

### Post by phillywize on 2007-11-29
> **flaggh said:**
> After reading how you tried and failed to get your iPod to work in an XP guest, I dug up a copy of Win2k and created a VM to see if I could try and reproduce your success in a Win2k guest OS and it detected my iPod!  I haven't had the chance to try syncing it yet, but this is definitely a step forward!  Hopefully tonight I'll have the opportunity to play with it some more.  I'll keep you updated.


Cool.  A further indication that part of the issue is XP is that I installed a Win2k VM under Virtual Box, and it also works for syncing my ipod to itunes, more or less to the same extent as Win2k did under VMWare Server.  XP doesn't work for me on VMWare or VB.  Win2k works on both.  Go figure.  Reading the VMWare and VB forums, it seems that both companies are aware of the problem, and working on a solution, although nothing that I know of has been released.  In the last analysis, this doesn't seem to be an actual *Ubuntu* issue, but so it goes.  Gotta talk about it somewhere.

---

### Post by phillywize on 2007-12-01
BTW, if you're using Win2k, the last version of iTunes to support it is 7.3.2.6 -- you'll need to poke around the Apple website to find it, but they have it available for Win2k users.  I think mostly what later versions do is give support to iPhone and 6G ipods.  What else, I don't know, but it doesn't seem to be anything that has made a difference to me.

---

### Post by flaggh on 2007-12-03
As I first reported, when I initially plugged in my ipod, it was successfully detected in Win2k and popped up in iTunes.  Every subsequent attempt however has not yielded the same results.  I spent quite a bit of time this weekend trying to get it to work.  I haven't given up yet, but my patience is running thin considering how slow Win2k runs as a guest OS on my antique laptop.  It would be so awesome if someone made some sort of VMware Appliance specifically for syncing the iPod with iTunes that excluded all the extra junk that isn't necessary.  I've heard of specific applications that gamers use to "lighten" an installation and I may give one of those a try to make my own custom "iTunes VM".  I also haven't tried Win2k on VirtualBox yet and will give that a try when I have the opportunity.

---

### Post by phillywize on 2007-12-04
I don't blame you.  This is definitely one of the more intractable software issues I've run into.  I suspect it's that the iPod uses some proprietary usb voodoo that makes VB and VMware flip out.  Given the hew and cry in the user forums on those sites, I think it's only a matter of time...but that may still be a looooong time.

Of course, my latest issue is that VB doesn't support audio cd's well or at all so far as I can gather (if I'm wrong, I'm happy to be corrected).  So... I have my iTunes running (now) on a Win2k VB machine, but to add CD's, I have to rip them in iTunes running under XP in VMWare.  Big pain.  I like aac, and haven't been able to make faac-encoded files work in itunes reliably.

But that's a story for another thread...

---

### Post by reader4 on 2007-12-19
I've been doing this for about a year now with pretty good success.  I have had more trouble recently, but the trouble is really that I cannot restart Ubuntu often because I have simulations running in the background that take days to complete.  I have typically followed the same procedure as in the first post, though sometimes it seems to help to start the VM after the iPod is connected.  It could be coincidence, but I have had more problems with Gutsy.  I'm using the same VM as with Feisty, but with more trouble (I had almost no trouble before).

Here are a few things I have noticed with Gutsy:

- Sometimes it seems to help to restart Ubuntu and try again.  Not sure why.  I have tried restarting HAL before with some luck, but usually a full system restart is more likely to make the iPod appear in the VM device list.  More often than not, the iPod shows up as an "unrecognized device" in XP even when connected through the VM.  This could be due to USB 1.1/2.0 issues, or a corrupted iPod (though Ubuntu reads it just fine).  I am going to rebuild the iPod tonight and retest tomorrow.

- Upgrading the iPod firmware always kills the guest OS.  Instead, I use this process (found it on the web somewhere, but I didn't write it down... sorry to whomever I am stealing from):

Retrieve the update firmware from C:\Documents and Settings\<name>\Application Data\Apple Computing\iPod Updates (or similar).  The zipped file is "iPod_13.<version>.ipsw".

Unzip the file to extract "Firmware-13.<firmware version>" (eg, Firmware-13.6.2.1) and copy it to the current directory (or go to the directory containing the Firmware file).

In this example, the iPod node is /dev/sdc, but check using:
$ cat /proc/partitions

Make a backup of the current firmware:
$ dd if=/dev/sdc1 of=Firmware_Backup

Then update the firmware and eject the iPod:
$ dd if=Firmware-13.6.2.3 of=/dev/sdc1
$ sudo eject /dev/sdc

The iPod will probably restart itself, update and be ready to go.  If it needs to be powered on manually, cover the middle two pins (data pins) on the USB cable and plug in to the USB port to provide power only without a mounting connection.


Maybe USB 2.0 support in VMware will help in the future...

---

### Post by giostau on 2007-12-27
Hi all,

i have similar problems with my ipod....

i used to have a 5.5g 30gb ipod witch was syncing almost fine with the itune library under winXP guest....

yesterday, i received a 6g 160gb ipod and there is no way i can make the guest system recognize it!!!
vmware server detects the ipod (under vm-> removable devices etc)
but when i select it to connect, it does nothing....
well almost nothing...
windows understands that a usb device has been connected, it understands that there is an ipod connected, but that's all!!!
the ipod doesn't appear in itunes, and in "my computer" there isn't a removable device....

any ideas???

thanks in advance!!!

---

### Post by pyite on 2007-12-27
I have a new 3G nano video.  It doesn't really work at all in VMware.

When I plug it in and check the VMware check box, it shows up in Windows.  However, starting iTunes causes a nice friendly BSOD in VMware, and Windows restarts.

@$&%@

:confused:

---

### Post by phillywize on 2007-12-31
I've had enough success syncing with iTunes under Windows 2000 running on VirtualBox 1.5.2 that it's become my solution until something better comes along.  What I've noticed, and I think this has been said by me and others above (who are no doubt wiser), is that the whole thing works much better with a win2k guest than winxp.  I can't get a Win XP guest to work as consistently with respect to syncing an ipod. (in my case an 80 gb 5.5g)

However, Virtual Box 1.5.4 just came out, and I'm gonna try that -- looks like they've been monkeying with the USB support, and hopefully it amounts to a fix.  I'd love to switch to a Win XP guest since Win 2k only runs a legacy version of iTunes.

Out of town at the moment, so can't give 1.5.4 a whirl...if anyone has better luck with it than VMware or VB 1.5.2, do share!

---

### Post by rpkehoe on 2008-01-05
> **pyite said:**
> I have a new 3G nano video.  It doesn't really work at all in VMware.

When I plug it in and check the VMware check box, it shows up in Windows.  However, starting iTunes causes a nice friendly BSOD in VMware, and Windows restarts.

@$&%@

:confused:

I have been having the same problem since I got a nano 3g.  I have tired just about everything, vmware, vbox, various versions.  I also briefly tried the new vmware beta, but I found it to be clunky and very slow (no more client, all web based).  For awhile I thought this was a ubuntu issue with /proc/bus/usb being gone, but it sounds like a more complicated issue than that.

Thanks for all your suggestions in this thread, I have already corrupted one ipod and am trying to avoid doing that again, so I am being a little more careful.  I have even broken down and down what I really didn't want to, which is dual boot.  Unfortunately, it is the only reliable method right now.

Keep the advice coming.

---

### Post by rpkehoe on 2008-01-05
I am trying so slightly different voodoo to try to the ipod to work in the vm.  I mounted the ipod in ubuntu as normal, then remounted it with --rbind under my home directory (which is setup as a samba share so I can access it in vmware).  I can then map the ipod as a network drive in windows, but itunes does not recognize it as an attached ipod.

Does anyone have any suggestions of how I might trick itunes to using the network drive or to fake xp as treating a mapped network drive as an attached usb drive?

---

### Post by phillywize on 2008-01-06
> **rpkehoe said:**
> I am trying so slightly different voodoo to try to the ipod to work in the vm.  I mounted the ipod in ubuntu as normal, then remounted it with --rbind under my home directory (which is setup as a samba share so I can access it in vmware).  I can then map the ipod as a network drive in windows, but itunes does not recognize it as an attached ipod.

Does anyone have any suggestions of how I might trick itunes to using the network drive or to fake xp as treating a mapped network drive as an attached usb drive?

Clever; unfortunately I don't have any ideas.  iTunes is a pretty tough customer when it comes to managing ipods.

---

### Post by phillywize on 2008-01-06
Tried VirtualBox 1.5.4 and XP -- same problem; iTunes recognizes an iPod in "Recovery mode."  Windows, on the other hand, seems to have recognized the iPod and installed drivers.  But it did this under 1.5.2.

Windows 2000 continues to work like a charm under 1.5.4.

---

### Post by flaggh on 2008-01-07
> **rpkehoe said:**
> I am trying so slightly different voodoo to try to the ipod to work in the vm.  I mounted the ipod in ubuntu as normal, then remounted it with --rbind under my home directory (which is setup as a samba share so I can access it in vmware).  I can then map the ipod as a network drive in windows, but itunes does not recognize it as an attached ipod.

Does anyone have any suggestions of how I might trick itunes to using the network drive or to fake xp as treating a mapped network drive as an attached usb drive?

I have also considered the possibility of doing exactly this.  I'm sure it's not impossible to trick iTunes into thinking a folder or drive is an ipod but how to implement it is beyond the scope of my knowledge.  If anybody has more information on doing this, I would be very interested in giving it a try.

---

### Post by airtonix on 2008-01-11
curious: you guys doing this becuase you like the user interface of appleOS on ipod? or you need the extras like vcard, ical and snazzy photo transitions?

i've replaced mine with rockbox, only thing todo now is to get the rockbox dev team making a vcard viewer and ical viewer.

wont need anything to do with apple apart from the ipod itself then.

ps: rockbox can zoom into jpeg images, whereas the appleOS cant.

as far as a i can see, only thing the appleOs has going for it is : 

battery usage is efficient,
has vcard viewer
has ical viewer
photo viewer has transitions.
user interface feels like osx (tiger?)

---

### Post by rpkehoe on 2008-01-11
> **airtonix said:**
> 
i've replaced mine with rockbox, only thing todo now is to get the rockbox dev team making a vcard viewer and ical viewer.


Rockbox is not out yet for the nano 3g.  Once it is, I would be willing to give it a try.

---

### Post by ntetreau on 2008-01-11
...and you do not want to use rhythmbox, amarok, gtkpod or others?

---

### Post by rpkehoe on 2008-01-11
I have already bricked one nano using gtkpod.  Until .6 is in the repos and I don't have to compile (which I have already done but I am not using), I have decided to be safe and stick to itunes.   It comes down to the new database in the 3g, and I am erring on the side of caution.

---

### Post by flaggh on 2008-01-12
> **airtonix said:**
> curious: you guys doing this becuase you like the user interface of appleOS on ipod? or you need the extras like vcard, ical and snazzy photo transitions?

i've replaced mine with rockbox, only thing todo now is to get the rockbox dev team making a vcard viewer and ical viewer.

wont need anything to do with apple apart from the ipod itself then.

ps: rockbox can zoom into jpeg images, whereas the appleOS cant.

as far as a i can see, only thing the appleOs has going for it is : 

battery usage is efficient,
has vcard viewer
has ical viewer
photo viewer has transitions.
user interface feels like osx (tiger?)

At one point I actually did, with much enthusiasm, install rockbox after reading all about it.  Loved the fact that I could just drag and drop files onto the ipod.  At first I found the user interface a little complicated, but was willing to overlook this fact since it made syncing everything so much easier.  The main problem I had was my ipod (photo) kept on freezing on me.  I had to reset it frequently and the battery life was horrible. 

I'm very impressed with what the rockbox devs have done, and I think I gave it a very fair chance, but until its a little less buggy I'd like to stick with the stock OS.  Plus, with my older ipod, I don't anticipate them doing much work to improve the port to it.

As for gtkpod, amarok, banshee, etc, I've tried these and find that they handle the metadata differently from itunes causing the artists and songtitles to be mislabeled on a good portion of my music.

What I've been doing, since I have an XP work laptop, is I set my music directory up on my ubuntu box as a samba share, mount it on my XP work laptop, set that directory as my itunes music folder, and then sync it from there.  This works great except for the fact that it can be really slow, but I don't sync that frequently for it to matter much.

---

### Post by phillywize on 2008-01-14
> **airtonix said:**
> curious: you guys doing this becuase you like the user interface of appleOS on ipod? or you need the extras like vcard, ical and snazzy photo transitions?

i've replaced mine with rockbox, only thing todo now is to get the rockbox dev team making a vcard viewer and ical viewer.

wont need anything to do with apple apart from the ipod itself then.

ps: rockbox can zoom into jpeg images, whereas the appleOS cant.

as far as a i can see, only thing the appleOs has going for it is : 

battery usage is efficient,
has vcard viewer
has ical viewer
photo viewer has transitions.
user interface feels like osx (tiger?)

Battery usage is a big issue for me.
Also, I use my 5.5G for video, which, as I understand it, is not smoothly or natively supported by Rockbox (though if I'm wrong, I'm wrong).  Overall, I like the way iTunes works, and I like the way my iPod's native OS works.  Also, I have some itunes downloads that won't work under Rockbox--though this wouldn't be a deal breaker.  Finally, I really don't like Amarok, Banshee, gtkpod, etc. -- I don't like how they manage my collection...at all.

And while I'm thinking about it:  most of my collection is in aac, and I'd like to stick with it, if only because of momentum.  Not about to flip over to ogg, though I have nothing against it.  The iTunes AAC encoder is pretty much the best consumer-level aac encoder out there, and moreover, FAAC-encoded AAC's have all kinds of compatibility issues...namely, the aac files that it produces don't have a  quicktime envelope, and so aren't compatible with itunes or ipod (or something like that -- either way, faac aac's don't work in itunes)

I'm just plain happier with the closed-source itunes and ipod os.

---

### Post by it_self on 2008-01-26
Hey, a bit late, but the idea just dawned on me a couple of days ago. Here's my situation:
I was dual booting XP and Ubuntu (7.10 now), but had internet issues. XP couldn't handle the usb 2.0 pcmcia card I put it, and therefore could not get on the net with the wifi card I was using. It would always overheat and die. Ubuntu could handle it, but couldn't sync with my iPod touch, nor activate it making it impossible for me to use youtube and other features. 
Well, after some finagling, I managed to get XP corporate installed as a guest OS using VMWare's Workstation. I'm just using the 30 trial to set it up, and then the player should be able to manage everything from there. I haven't had any issues with windows to see the iPod. Aside from my old laptop taking a beating while processing a few things (it got up to 90 degree centigrade once), everything working like a charm and I'll be deleting that XP partition pretty soon. Not sad in the least to see it go.
Wonderful post, thanks for the info!

---

### Post by rpkehoe on 2008-01-26
Hmmm, I wonder is there is better support in VMWare workstation for Ipods.  If that is the case, I would suspect you might have trouble once you start using VMWare player or Server.  I can't speak for everyone, but I think we have all been using Server since it is free.

I would suggest trying to boot your XP image in player before your workstation trial runs out.  Let us know how it goes.

---

### Post by phillywize on 2008-02-03
So here's my sad story:  that 5.5G I mentioned earlier, the one I had working with Win2k in VB...well, I went to get my drivers license renewed AND LEFT THE THING AT THE STATE OFFICE!  AGH!  I'M SUCH A MORON!

Anyhow, replaced it with a shiny new 6G...of course this is my cascade of misfortune:  as detailed above, I was using 7.3.x.y in Windows 2000 because that's the last version of iTunes compatible with Win2k (I can grouse a bit about that, but understandable since it IS almost 10 years old).  Well, the 6G's don't roll with 7.3...they require 7.4+.

After 7.4, iTunes doesn't work in Win2k.

And as I've said a few times here, can't get an iPod to sync under Win XP in VB or VM Server.

So there it is.  I'm out of this game until VM or VB or whoever comes up with a fix.

In the meantime, I'm using Amarok to syn natively under linux.  It's just not the same.  You need a degree in computer science (which I do not have) to get it to work right.  For cryin' out loud, I had to compile a library and manually link it to get my 6G to work under Amarok.  That's no way to carry on with a glorified mp3 player.  But I guess we're all going through the same kind of absurdity with trying to get iPods to sync on a virtual windows machine.

Damned if you do, damned if you don't...

I'm not going to dual boot windows just for my iPod though.  At least not yet.  Too much trouble.

---

### Post by rpkehoe on 2008-02-03
Sorry to hear about that, nothing like giving a few hundred more dollars to the DMV.  Hopefully we will have more luck under VMWare 2, but for now I have found my solution.  I have an old box on XP that I am VNC'nig into.  Seems really silly to use a computer just for itunes, but that is where I am at right now.

---

### Post by phillywize on 2008-02-04
> **rpkehoe said:**
> Sorry to hear about that, nothing like giving a few hundred more dollars to the DMV.  Hopefully we will have more luck under VMWare 2, but for now I have found my solution.  I have an old box on XP that I am VNC'nig into.  Seems really silly to use a computer just for itunes, but that is where I am at right now.

Yeah, I'm pretty much a sucker here. Is there any redeeming value to making a person's day by giving them an easy opportunity for petty dishonesty? On the one hand, I'd be pretty psyched to pick up an ipod for free; on the other, I'd like to think I'd turn it in.  But hello...this is reality we live in.  And come to think of it, I got my first ipod free, although I came by it honestly...one of those white 4G's from right around when they went from merely popular to legendary.  So what goes around comes around.  Can't get too upset about it.

Anyhow, I am going to haul out my old laptop, which is running XP natively, put vnc server on it, toss somewhere convenient, and do the same as you.  I really can't stand another day of Amarok.  I don't know what all the fuss is about -- it's probably good if you want to put some mp3's and a podcast or two on your mp3 player and only occasionally update it, but for me, with the way I'm accustomed to using my ipod, too many things don't quite work right, or don't work at all.  To wit:  video, photos, podcasts, synchronization, and (gasp) fairplay are all a problem with Amarok.  I could live without the drm support, since it's mostly one-off impulse purchases from the itunes store, but the rest is important to me.  Amarok isn't a disaster with podcasts, but it is clunky, and I follow dozens of podcasts and video podcasts (news junky).  But enough.

I'll just keep my fingers crossed along with everyone else on this thread for a solution from VM, VB, or the Flying Spaghetti Monster.

---

### Post by phillywize on 2008-02-04
> **rpkehoe said:**
> Hmmm, I wonder is there is better support in VMWare workstation for Ipods.  If that is the case, I would suspect you might have trouble once you start using VMWare player or Server.  I can't speak for everyone, but I think we have all been using Server since it is free.

I would suggest trying to boot your XP image in player before your workstation trial runs out.  Let us know how it goes.

While I'm at it...I have been VMWare using server (in addition to VBox).  Tried the new beta version of server that's out -- the one that's all browser-based -- and went screaming back to 1.0.4.  That browser interface is a bear.  Hopefully the production version will be more refined.  As I recall, I didn't have any luck syncing under it, either.

This workstation thing is intriguing though. I think there are many who haven't had any luck with it, however.  Over on the VMWare forums, a band of iPod/iPhone users are pretty much in open revolt over VMWare's ongoing failure to release a fix.  The scuttlebutt is that the company has a fix internally, but that the fix hasn't wended its way through the system.  Posters have been getting nasty about the whole thing.  Not sure what to make of it.

So it goes.

---

### Post by rpkehoe on 2008-02-05
Could you post a link over the VMWare forum you are talking about?  I would like to keep an eye on that discussion as well.

---

### Post by sinX80 on 2008-02-05
[http://communities.vmware.com/message/688148#688148](http://communities.vmware.com/message/688148#688148)

---

### Post by phillywize on 2008-02-05
> **sinX80 said:**
> [http://communities.vmware.com/message/688148#688148](http://communities.vmware.com/message/688148#688148)

Yeah, that's the open rebellion I'd mentioned.  :mad:  Anyhow, hopefully good news will come from that thread first.

---

### Post by phillywize on 2008-02-10
Here's a poll for idly venting frustration:

[http://ubuntuforums.org/showthread.php?t=692963](http://ubuntuforums.org/showthread.php?t=692963)

---

### Post by Steve Zenone on 2008-02-15
After many hour of testing, and eventually coming across this thread, I still *haven't* succeeded. As of this posting I'm have the following:
[LIST]
[*]Ubuntu 7.10
[*]VMWare Server 1.0.4 build-56528
[*]iPhone (1.1.13)
[/LIST]
Within VMware:
[LIST]
[*]XP container with all of the latest patches
[*]iTunes 7.6
[/LIST]
The most success I've had is after I do the following:
[LIST=1]
[*]Cable up iPhone to USB port -- Cancel out of camera import dialog box
[*]Doing a `lsusb` shows the phone there. Ok, not a step, but a confirmation of sorts.
[*]Startup VMware - turn on XP guest. While it boots XP...
[*]In VM, go to VM | REMOVABLE DEVICES | USB DEVICES and make sure "Apple Inc. (port 1)" is checked
[*](Warning: Windows Talk) Log into XP
[*]Go to the control panel, administrative tools, and launch the services app
[*]Click on the "Apple Mobile Device" service. Hmmm..no options to start | stop | restart
[*]So, back in VM, go to uncheck "Apple Inc. Iphone (port 1)"
[*]Now recheck "Apple Inc. Iphone (port 1)". Windows will detect the new hardware
[*]Back in Windows, go to services again and click on "Apple Mobile Device" again. Restart the service.
[*]Awesome - iphone detected. Windows pulls up a window asking to import photos.
[*]AHHH - blue screen! haha, so typical!!!!!
[/LIST]
So, I still haven't figured this out yet. I've gone through the steps uninstalling Quicktime, Apple Software Update, and Apple Mobile Device Support ... and then reinstalling iTunes (which installs everything).

---

### Post by phillywize on 2008-02-16
> **Steve Zenone said:**
> After many hour of testing, and eventually coming across this thread, I still *haven't* succeeded. As of this posting I'm have the following:
[LIST]
[*]Ubuntu 7.10
[*]VMWare Server 1.0.4 build-56528
[*]iPhone (1.1.13)
[/LIST]
Within VMware:
[LIST]
[*]XP container with all of the latest patches
[*]iTunes 7.6
[/LIST]
The most success I've had is after I do the following:
[LIST=1]
[*]Cable up iPhone to USB port -- Cancel out of camera import dialog box
[*]Doing a `lsusb` shows the phone there. Ok, not a step, but a confirmation of sorts.
[*]Startup VMware - turn on XP guest. While it boots XP...
[*]In VM, go to VM | REMOVABLE DEVICES | USB DEVICES and make sure "Apple Inc. (port 1)" is checked
[*](Warning: Windows Talk) Log into XP
[*]Go to the control panel, administrative tools, and launch the services app
[*]Click on the "Apple Mobile Device" service. Hmmm..no options to start | stop | restart
[*]So, back in VM, go to uncheck "Apple Inc. Iphone (port 1)"
[*]Now recheck "Apple Inc. Iphone (port 1)". Windows will detect the new hardware
[*]Back in Windows, go to services again and click on "Apple Mobile Device" again. Restart the service.
[*]Awesome - iphone detected. Windows pulls up a window asking to import photos.
[*]AHHH - blue screen! haha, so typical!!!!!
[/LIST]
So, I still haven't figured this out yet. I've gone through the steps uninstalling Quicktime, Apple Software Update, and Apple Mobile Device Support ... and then reinstalling iTunes (which installs everything).

I feel your pain.  Welcome to the club.  I think mostly people are watching the VMWare forum link listed above, since no one can seem to get their iWhatever to work at all.  I think you're the first person in this threat with an iPhone, although the VMWare thread above is iPhone specific.  I'm operating on the hope/assumption that whatever fixes the iPhone issue will also fix the iPod classic/5.5G/other issues that everyone's having (I have a classic).  

If you run across anything, let us know!

---

### Post by phillywize on 2008-02-20
One of the more insightful comments I've seen about this issue here:

[http://communities.vmware.com/thread/91715;jsessionid=2CAD490D905CFDDC71FE4FEF394F2D09?tstart=0&start=135](http://communities.vmware.com/thread/91715;jsessionid=2CAD490D905CFDDC71FE4FEF394F2D09?tstart=0&start=135)

I'd heard about the kernel issue before, but this is a little more enlightening.

---

### Post by rpkehoe on 2008-02-23
> **phillywize said:**
> 
I'd heard about the kernel issue before, but this is a little more enlightening.

Based on that thread, it sounds like VMware has to do enough work in order to fix this that they probably have no intention of releasing it in a patch on 1.x.  I would expect to see this fixed in Server 2 GA though.

---

### Post by rpkehoe on 2008-02-23
Has anyone tried to get this working under parallels or xen?

---

### Post by phillywize on 2008-02-24
> **rpkehoe said:**
> Has anyone tried to get this working under parallels or xen?

Tried Parallels -- can't remember the version (fairly recent), but no luck.  Similar issues.  Which lends credence to the idea is really rooted in linux and not the virtualization software.

---

### Post by phillywize on 2008-03-18
Well, it looks like there's an iPhone fix in VMWare Workstation 6.0.3...no word yet on server.

[http://communities.vmware.com/message/890202](http://communities.vmware.com/message/890202)

[Edit]
Well, installed VMWare Server 1.0.5, which was released this week, and it doesn't work with my iPod classic (6G)...yet.  Things break, freeze, crash, and don't respond in what appear to be completely new ways.  Is this progress?

---

### Post by nuzeb on 2008-04-07
I just successfully synced my iPod Classic with iTunes 7.6.2 under Win XP Home in vmware server 2 beta 2 (Host: Ubuntu Hardy Beta - Kernel 2.6.24.15, but should work for minor versions too). I had nothing special to do. Just installed vmware server (some issues there with little workarounds mentioned in release notes - eg. activate USB 2.0 support).
Everything works very well except a little speed loss in comparison to a real hardware usb 2.0.

---

### Post by vcarbon on 2008-04-09
I have to admit I didnt read all the postings, but I wanted to let you know that I sync my ipod with a XP system running vmware. I was using the 6.5 beta under fiesty. Dont remember having any problems. once your booted into you guest XP system, plug in you ipod and it should mount on the desktop. then you have to tell vmware to take control of you ipod in the devices menu. you will get an unsafe mount error but I just ignore that. once vmware has control my ipod just shows up in itunes and I do a manual manage my library but that should make any difference. check you setting in vmware before you boot to make sure you have the usb 2.0 enabled...if you not using workstation download the beta its free and they give you a serial number. this will allow you to change some settings in you virtual machine they you may not have tried if your using vmplayer. but the same goes for the player where you have to take control of the ipod in the device menu of the tool bar

good luck

---

### Post by vcarbon on 2008-04-09
now do it and Virtual box and tell me the procedure because Im going to pull out my hair trying to get the usb to work!

BTW virtual box seems to run much faster for me although the unity mode was having some issues

---

### Post by phillywize on 2008-04-11
> **nuzeb said:**
> I just successfully synced my iPod Classic with iTunes 7.6.2 under Win XP Home in vmware server 2 beta 2 (Host: Ubuntu Hardy Beta - Kernel 2.6.24.15, but should work for minor versions too). I had nothing special to do. Just installed vmware server (some issues there with little workarounds mentioned in release notes - eg. activate USB 2.0 support).
Everything works very well except a little speed loss in comparison to a real hardware usb 2.0.

Huh.  Interesting.  Does your success have anything to do with Hardy Heron/2.6.24.15?  I'm running Gutsy/2.6.22-14, with no luck, albeit using vmware server 1.0.5.

I had a beta of vmware server 2 installed a while back, and lordy -- I thought it was a mess.  The interface was so bad that it was nearly unusable.

Hopefully it's been, or will be, improved before we get to the release.

---

### Post by phillywize on 2008-04-13
> **nuzeb said:**
> I just successfully synced my iPod Classic with iTunes 7.6.2 under Win XP Home in vmware server 2 beta 2 (Host: Ubuntu Hardy Beta - Kernel 2.6.24.15, but should work for minor versions too). I had nothing special to do. Just installed vmware server (some issues there with little workarounds mentioned in release notes - eg. activate USB 2.0 support).
Everything works very well except a little speed loss in comparison to a real hardware usb 2.0.

Welp, Nuzeb, laurels for the victor.  Preliminarily, this is working with my iPod classic on gutsy.  Thanks for the tip.  I'll post more details once I've had time to try to break it, and otherwise see if mine eyes deceive me.  One thing I had to do was rebuild my virtual XP machine, since bringing my VMware server v. 1 machine over to v. 2 beta wasn't entirely successful, and in fact, died on the operating table. Also, the new XP install had to be service packed before it would work -- otherwise no USB 2.0, and no syncing (not even at 1.1 speeds).

And the UI on beta 2 isn't as bad as it was, though I miss the client.

____
Update:  Slower, but it works.  Still a little cranky.  Thanks!

---

### Post by nuzeb on 2008-04-13
> **phillywize said:**
> Huh.  Interesting.  Does your success have anything to do with Hardy Heron/2.6.24.15?  I'm running Gutsy/2.6.22-14, with no luck, albeit using vmware server 1.0.5.

I had a beta of vmware server 2 installed a while back, and lordy -- I thought it was a mess.  The interface was so bad that it was nearly unusable.

Hopefully it's been, or will be, improved before we get to the release.

 I don't know how much Hardy has to do with this but  I don't think any iPod would work with vmware server 1.0.5 because it is lacking USB 2.0 support.

You are right. The web Interface is not the best solution and i liked the client better. But it works quit well  (since beta 2).

---

### Post by phillywize on 2008-04-13
> **nuzeb said:**
> I don't know how much Hardy has to do with this but  I don't think any iPod would work with vmware server 1.0.5 because it is lacking USB 2.0 support.

You are right. The web Interface is not the best solution and i liked the client better. But it works quit well  (since beta 2).


Yeah, iPods will fall back to 1.1, which is how I was doing it with my 5.5G and VirtualBox on Win2k.  There's something about the interplay of the iPod USB implementation, the recent linux kernels, and virtualization that has been a problem generally.  So.

Here's what I did in some kind of (hopefully) reproduceable (sp?) detail:

1.  Uninstalled VMWare server 1.0.5  (I would backup anything you want off of your old virtual machine(s) before you do this, since the conversion over to server 2 beta 2 was not smooth -- at least for me.  YMMV. I found that installing 2 beta 2 over 1.0.5 wasn't fully successful.  Again, YMMV.  Plus, you run into licensing issues if you have your old VM around, I think.

2.  Set up your VM and reinstall Windows on it; service pack it.  Install iTunes, etc.  Shut it down.  (service packing it is important, since the original XP didn't have USB 2.0 support, and you only get it with the service pack.)  Oh yes, don't forget to add a USB port to your VM.

3.  Enable USB 2.0 by adding the following line to your vmx file (or in the advanced configuration options in the web UI:
```

ehci.present = TRUE
```

(This is in the beta 2 release notes, [here]("http://www.vmware.com/products/beta/vmware_server/releasenotes_vmserver2.html").)

4. I also followed the instructions [here]("http://communities.vmware.com/message/826169"), though I'm not sure it's absolutely necessary.  Essentially, it tells you how to make your virtual machine automatically grab control of a particular USB device; here, your iPod.  It also has a link to instructions for a linux  USB workaround that I set up so long ago in troubleshooting my iPod woes that I can't remember what it did or if it's important; I think it might be, so follow that link and check it out.

5.  In terms of getting your ipod to sync with itunes in the VM, I have had the best luck connecting the iPod to my physical machine, letting ubuntu recognize it, and then booting the VM and letting it wrest control of the Ipod from linux.  This results in an unsafe removal warning, and probably isn't the greatest thing in the world to do, so if anyone has a better way of doing it...  (one hunch, I think it's probably not too dangerous if you don't DO anything with the iPod in linux...I wouldn't be writing a bunch stuff to it in linux, and then let the VM interrupt it...sounds bad.)

Finally, in order to make VMware take control of the ipod, you have to boot the VM from inside the web UI, and use the pulldown USB menu to give the VM control of the ipod (i.e., get the X next to it).

Obviously this is all just anecdotal; please feel free to comment and improve upon what I have here.  Thanks Nuzeb!

One final note:  I have seen more than one story about iPhones/iPods getting bricked when people try to update their firmware in a VM.  If you're brave or if I'm wrong, go for it.  I, for one, am too afraid to try it.  And besides, my Win XP laptop from grad school needs a reason to go on living.

---

### Post by phillywize on 2008-04-13
Not that it's exactly on point, but I've noticed that VMware server 2 beta 2 tends to kill compiz when in full screen mode.  Ugh.  But it's easy enough to open a shell and issue:

```
compiz &
```

Still though.

---

### Post by dca on 2008-04-23
This post did the trick (VMware Server 1.0.5) for me, however, still have to format the iPod to use...  Let you know if after the format it still works...
 
[http://ubuntuforums.org/showthread.php?t=588225](http://ubuntuforums.org/showthread.php?t=588225)

---

### Post by mattalexx on 2009-04-24
Did anyone get this working in Jaunty yet?

---

### Post by TMavro on 2009-10-06
I am successfully running iTunes 8.2.1.6 on Windows XP SP3 through Ubuntu Jaunty with VMWare 6.5.2. I'm using this setup to sync my iPod Touch. 

There's only three minor annoyances, other than these it runs flawlessly. 1. I can not update firmware this way. 2. Connecting the iPod sometimes requires me to disconnect and reconnect it in both ubuntu and vmware. 3. Albums seem to have a tendency to be uploaded twice for no reasons at all, which means I have to manually remove the extra songs. 

Other than that it runs perfectly and it all worked completely out of the box. There were no extra hassle with configuration or voodoo spells involved. 

I hope this was helpful!

---

### Post by pauldsmyth on 2009-12-05
Don't know how many people have tried this but I just installed a Windows 7 guest in VMware Workstation 7, installed iTunes and synced my Ipod Nano 5th Gen including software update. I had to disconnect and reconnect once to start with, after that it was totally flawless.

---

