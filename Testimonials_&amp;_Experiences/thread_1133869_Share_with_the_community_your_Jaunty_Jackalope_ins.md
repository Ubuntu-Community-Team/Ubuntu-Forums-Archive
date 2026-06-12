---
title: "Share with the community your Jaunty Jackalope install/upgrade experience"
date: 2009-04-23
forum: Testimonials &amp; Experiences
---

### Post by frodon on 2009-04-23
The purpose of this thread is to share your experience installing/upgrading Jaunty Jackalope.

Did it worked flawlessly ? 
Did you got problems ? 
Did you manage to solve them ? 
if yes how ?
...
...
.

Feel free to post your experience here and think to explain how you solved the problems you got, it might help other users in your case.

Thank you for contributing :KS

---

### Post by sports fan Matt on 2009-04-23
Upgraded through Update manager..painless as always:)

---

### Post by Xir on 2009-04-23
Upgraded two VMs through do-release-update. Both with same hardware on them and the only difference being one was a LAMP box and the other was not. The one that was not worked flawlessly. The LAMP box failed to boot. Downloaded the server install CD and created a new VM in VMware Server. Began the install. Shortly after selecting my country and selecting "Begin the Install" the system sits there doing nothing.

I reinstalled using 8.10 and am trying the do-release-upgrade path again.

---

### Post by kshane on 2009-04-23
I use the ATI X-1650Pro, for which there is no driver at this time.  I upgraded using the upgrade manager.  My system boots but slows to a crawl and I am unable to use my mouse (can't click on anything).  Have to hit "reset"...

Again, PO'd at ATI for their slowness in releasing new drivers.

Kevin

---

### Post by phillies on 2009-04-23
Update not available, neither via update-manager nor via command line (apt-get dist-upgrade)
ran apt-get update maybe 20 times the last 30 minutes on my PC, nothing.
I started my notebook there the update manager but not the command line found the upgrade.
InCRAPid won't let me go... :(

---

### Post by veribaka on 2009-04-23
I think you need to open the update manager in order to update to another distro.

---

### Post by unoodles on 2009-04-23
Clean install. I have an Intel965, so I was affected by the issues in the release notes.
I solved this problem by installing 2.6.30rc2 kernel from [http://kernel.ubuntu.com/~kernel-ppa/](http://kernel.ubuntu.com/~kernel-ppa/)
Also installed intel drivers from the Debian Sid repo.

Ultra Special thanks to this thread. [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
I reccommend all Intel users chech it out if they are having issues.

---

### Post by oldrocker99 on 2009-04-23
I'm currently upgrading from the automatic upgrader at 50K/sec :(. I had tried 9.04 before but I had MAJOR problems with the ATI fglrx drivers and resinstalled Intrepid. There ***IS*** a new version, 9.04 of the ATI drivers, and they *say* that it supports Jaunty...we'll see in a few hours.

:guitar:


7 hours later: The 9.04 drivers didn't work at all, so I installed the 9.1 drivers, which at least gives me a login screen and a desktop. No OpenGL (yet), but that 9.01 driver is on ATI's site.

3 days later: Nothing but problems with the fglrx drivers, no OpenGL, and (sigh) a return to stable ol' 8.10. 9.04 maybe later...

---

### Post by obocho on 2009-04-23
fresh install: no problem, everything worked just fine...
I can even say that [so far] Jaunty is the best release I have ever installed!

have fun!!! :)

---

### Post by Xir on 2009-04-23
After reinstalling and performing the do-release-upgrade again, again the VM will not boot. I guess I'm done working with the upgrade today, back to 8.10 for me until I have time to troubleshoot it.

---

### Post by dubref on 2009-04-23
Not good so far:

8.04 to 8.10 was flawless, but 8.10 to 9.04 bunch of errors appear:

Errors were encountered while processing:
 linux-image-2.6.28-4-generic
 linux-headers-2.6.28-4-generic
 linux-headers-generic
 linux-restricted-modules-2.6.28-4-generic
 linux-image-generic
 linux-restricted-modules-generic
 nvidia-common

Well, looks like the best option will be to do a clean reinstall...

---

### Post by Metralha on 2009-04-23
Hi. I did a clean install, and after some tests ubuntu 9.04 keeps crashing...Can anyone do the following test?

1º Open several programs and windows.
2º Press repeatable windows+tab and make it spin for a while..

And then it just log's me off..

Message log:
Apr 23 16:37:44 metralha-laptop bonobo-activation-server (metralha-3624): could not associate with desktop session: Failed to connect to socket /tmp/dbus-jfTwjhnCvs: Connection refused
Apr 23 16:37:45 metralha-laptop kernel: [ 104.324654] [drm] Setting GART location based on new memory map
Apr 23 16:37:45 metralha-laptop kernel: [ 104.326971] [drm] Loading R500 Microcode
Apr 23 16:37:45 metralha-laptop kernel: [ 104.327035] [drm] Num pipes: 1
Apr 23 16:37:45 metralha-laptop kernel: [ 104.327053] [drm] writeback test succeeded in 2 usecs
Apr 23 16:37:57 metralha-laptop pulseaudio[3877]: pid.c: Stale PID file, overwriting.


Bah...does this happens to anyone?

Thanks!

---

### Post by satishputcha on 2009-04-23
I did a clean install on my Thinkpad Z60M. THis machine was struggling to connect to my Wi-fi from Windows but from Jaunty the wireless has begun working. Also, the whole experience was quite pleasant.

Till date, starting from Gutsy Gibbon, I have only done clean installs and the experience only keeps getting better!!

---

### Post by phillies on 2009-04-23
> **veribaka said:**
> I think you need to open the update manager in order to update to another distro.

As I said, update manager didn't work then and still doesn't work now. Even "do-release-upgrade" says "no new release found". Unfortunately, a fresh install is not an option, would take days to get everything up and running again

---

### Post by ArcticD00d on 2009-04-23
A mostly painless upgrade.... had to reset Compiz settings to my liking, set pulseaudio to default to 6 channels, and then downgrade amarok2 back to amarok1.4(so much better, imho). So far everything else is working just fine. Boots quicker, too!

---

### Post by Salpiche on 2009-04-23
Wrong spot!

---

### Post by Garrovick on 2009-04-23
Did a clean fresh install without a hitch.  Smooth as glass. :popcorn:

---

### Post by raymondh on 2009-04-23
Still on RC (fresh install) and deliberating whether to do a network upgrade to final or do another fresh install.  Previous network upgrade from 8.10 to 9.04 beta to 9.04 RC came with problems hence the fresh install preference.

So far, so good.  I just hate not having the old ctrl-alt-backspace combo key.  Still, a better version than 8.10, IMHO.

---

### Post by geekity2 on 2009-04-23
I did upgrade, which seemed to go ok, except for few minor glitches I haven't solved yet. Namely, the graphics seem all weird for drop down menus when I activate the compiz desktop cube, and if I try switching desktops via the 3D cube, the whole system freezes. Also, my Cairo dockbar has disappeared, so I'm wondering whether the two aren't related.

---

### Post by autra on 2009-04-23
@Phillies: This may be a stupid question but did you allow it ? (System -> Administration -> Software Sources -> Updates and in release upgrade, set show new distribution releases to "normal releases")

I'm also interested in feedbacks from people having the X1600 ATI card, because I had an error message saying that there is no support for fglrx in 9.04, and I need it for 3D acceleration. Is there anybody in the same case ?

---

### Post by Eric B on 2009-04-23
I just installed 8.10 this week because something was seriously wrong with my 8.04 install. I went to upgrade today, and it is done "Getting New Packages." However, it will not move on to the next step.

It was a compiz python upgrade issue. I am removing it and trying again.

---

### Post by hiec on 2009-04-23
> **raymondhenson said:**
> 
So far, so good.  I just hate not having the old ctrl-alt-backspace combo key.  Still, a better version than 8.10, IMHO.
You can reenable that combo key. I think the command was called "dontzap". I read about it in the Jaunty blueprints.

EDIT:
Okay, you have to edit your xorg.conf file to restore the old behaviour. See [here]("https://wiki.ubuntu.com/X/Config/DontZap?action=show&redirect=DontZap")

I still think there's also a shell command to do that...

---

### Post by The Funkbomb on 2009-04-23
The Upgrade was a nailbiter but everything came out alright.

Now, when I try to update again, it tells me it needs to do a partial upgrade.  When I try to do it, it says "Error Authenticating some packages"

These are the packages:

libdb4.6-java
libdb4.6-java-gcj
liblucene2-java

---

### Post by Smirre on 2009-04-23
For some reason, when I try to update through update manager, it just stops responding and I have to force quit. :/

Edit: have to add that I did the same procedure before xmas with 8.04 -> 8.10 and then everything went smooth.

---

### Post by autra on 2009-04-23
I found my answer :
[http://ubuntuforums.org/showthread.php?t=1133844&page=2](http://ubuntuforums.org/showthread.php?t=1133844&page=2)

Well it seems that many people who have more than 3 years old ATI graphic card won't be able to upgrade...

@Smirre: the servers must be overloaded for now, try later, tomorrow...

---

### Post by Smirre on 2009-04-23
Must be, I can't do a thing to upgrade.  Oh well, no hurry.  I have the day off work tomorrow, so plenty of time then to mess around with stuff.

---

### Post by 4wd22r on 2009-04-23
I too am interested in feed back from people with the X series ATI cards, I have an X1300 on my laptop and recieved that message when I went to upgrade. I need 3D acceleration on this computer, so I'm wondering if I should just stay with 8.10 for time being, any luck from anyone? THANKS!

---

### Post by Grimmwolf on 2009-04-23
Tried the update, now I can boot, see the loading bar fill up and see a garbled screen next. Resetting the xorg conf did not do anything. Other repair option did not help either, I might have to reinstall a fresh system... (pita). (64bit Ubuntu, 4870 ATI)

EDIT: I removed the ATI driver with apt-get remove --purge xorg-driver-fglrx from the root console (recovery mode) and I was able to boot into my system. :) (without compiz for now...)

---

### Post by autra on 2009-04-23
@4wd22r : your card is not supported by the new version of fglrx, which is needed to ubuntu 9.04.
Here is the complete list of the ATI drivers which are not supported any more : [http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)

HOWEVER, if you use open source drivers (if they work for you), you shouldn't have any trouble...

---

### Post by 4wd22r on 2009-04-23
> **autra said:**
> @4wd22r : your card is not supported by the new version of fglrx, which is needed to ubuntu 9.04.
Here is the complete list of the ATI drivers which are not supported any more : [http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)

HOWEVER, if you use open source drivers (if they work for you), you shouldn't have any trouble...

Hey thanks autra! I must research the open source drivers now :D

---

### Post by autra on 2009-04-23
How to install open source ATI driver

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

;-)

---

### Post by LexLuthor08 on 2009-04-23
What I find funny is how the **same old bugs** just survive every new release.
Good thing I have a whole folder of txt files with workarounds that I have to apply for each new install.

Bad thing in every new release they arbitrarily change filenames and stuff so that the workarounds don't work anymore.

-after all, an ubuntu install as usual.

---

### Post by 4wd22r on 2009-04-23
> **autra said:**
> How to install open source ATI driver

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

;-)

XD thanks again! My hat tips to you sir :D

---

### Post by notmatt on 2009-04-23
It went pretty well for me and I upgraded yesterday.  I've had to sort flash out, but so far a reinstall of that with firefox closed has sorted it.  Best and most painless upgrade yet.

---

### Post by ninjapirate89 on 2009-04-23
So far so good for me!

---

### Post by hurstdaj on 2009-04-23
I didn't see an option on the update manager, but does anything need to be done to upgrade from 9.04 RC?

---

### Post by JK3mp on 2009-04-23
Well thus far i havn't upgraded yet. Downloading it now so i'll update here in a bit. But im psyched! Havn't heard much downside to it.

---

### Post by celthunder on 2009-04-23
My upgrade went smoothly, no problems for physical machine or virtual machines that i upgraded.

---

### Post by jo4hnc on 2009-04-23
So far, slow as molasses in January. Download speeds have been at a dial up speed (16-50kBs), guess the servers are getting slammed. 5 hours and counting with 300 files to go.

---

### Post by x-na on 2009-04-23
I've been waiting 20+ minutes for update-manager to show me the release notes, no luck yet.

Me thinks some organizations should get more bandwidth...

Edit: For some reason a friend of mine can update his box from the very same server. I'm still waiting for the release notes :D. 

Edit 2: After leaving update-manager to run over night, it finally had retrieved release notes. Downloading packages about 100 KB/sec.

Edit 3: Server upgrade went without problems yesterday.

---

### Post by Amazona aestiva on 2009-04-23
Well, I need some sort of help I geuss and you may want to know about this:

I've tried a fresh install of i386 and amd64 version too.

Both seems to have a serious bug with Adobe flash player. If I go on youtube my whole system will freeze after 6-7 minutes and I have to reset. I have md5sum checked the images on computer and ran defect check on boot. I have also tried to use the flash player I can download from adobe's webpage but it fails too.

This is a pretty big problem to me andI do not think I will be the only one.

I've been using Ubuntu since Edgy and have quite a lot of experience so I do not think I have done something wrong.

Is there any way I could give you more information?
What sould I do now? Report a bug? Where?   Solutions? :)

Thanks

EDIT: made a thread because this will get lost here soon [http://ubuntuforums.org/showthread.php?p=7128455#post7128455]("http://ubuntuforums.org/showthread.php?p=7128455#post7128455")

---

### Post by drjonze on 2009-04-23
I've been running jaunty since the beta. I've done both upgrades and installs and had no issues at all. I just did another install an hour ago. Worked flawlessly.

I love 9.04. I was reluctant to leave 8.10 as it was solid as a rock but I'm glad I did. The only version I had issues with was 8.04. I had to stop running it after a while, it kept freezing up my machine. I tried to fix the problem but never could (after hours and hours of research and work). I think it just came down to some of my hardware not playing well with Hardy. Not really anyone's fault or not really a problem with Hardy or my hardware, that's just how it goes sometimes. The fact that Ubuntu works with as much hardware as it does considering it gets almost zero support from manufacturers is astounding to me.

---

### Post by TBerk on 2009-04-23
Well, I've been running 9.04 beta for some time now; it 'fixed' somethings right off the bat vs 8.10; My RealTek st2860 based wifi card for one, and broke some other things; SB AUdigy2 sound for example.

Along the way I was pretty active with Synaptic Package manager and getting updates, hardly 48 hours went by that I hadn't checked for changes. Nothing really broke, but once this week my local index file got corrupt and I had to use apt-get to rebuild it/them.

As of this AM it is 23Apr09 and I find the [http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352) **Jaunty Jackalope Testing and Discussion** (CLOSED), well, Closed. That was my 1st Big Clue that today was release day. 

My second Big Clue was Synaptic PM didn't seem to finish getting a renew, so there I was the terminal using apt-get..... "well, they are downloading, just slowly..."

Going back to the Jaunty Testing forum I finally say the banner that said "It's released!, go get a copy!". 

Having revealed my lack of Calender skills online I feel much better about not remembering what Today was. 

So, as of right now I have a Whole Bunch of updates running in the background (sorry Servers) and will append post with 'How Did it Go?'.


TBerk

---

### Post by drjonze on 2009-04-23
> **Amazona aestiva said:**
> Well, I need some sort of help I geuss and you may want to know about this:

I've tried a fresh install of i386 and amd64 version too.

Both seems to have a serious bug with Adobe flash player. If I go on youtube my whole system will freeze after 6-7 minutes and I have to reset. I have md5sum checked the images on computer and ran defect check on boot. I have also tried to use the flash player I can download from adobe's webpage but it fails too.

This is a pretty big problem to me andI do not think I will be the one.

I've been using Ubuntu since Edgy and have quite a lot of experience so I do not think I have done something wrong.

Is there any way I could give you more information?
What sould I do now? Report a bug? Where?   Solutions? :)

Thanks

Are you getting an error "npviewer.bin crashed with SIGSEGV?". This is a bug, {Bug 178038} I had this problem. I installed the Flash 10 beta: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) (its at the bottom of the page) I haven't had the issue since.

---

### Post by Amazona aestiva on 2009-04-23
> **drjonze said:**
> Are you getting an error "npviewer.bin crashed with SIGSEGV?". This is a bug, {Bug 178038} I had this problem. I installed the Flash 10 beta: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) (its at the bottom of the page) I haven't had the issue since.

I do not see any error messages it simply freeze and do not respond anymore :(

Anyway I'll have a look at it, thanks.

EDIT:
Your link leads to a 64bit version, but I experience the proble on 32bit too

---

### Post by drjonze on 2009-04-23
> **Amazona aestiva said:**
> I do not see any error messages it simply freeze and do not respond anymore :(

Anyway I'll have a look at it, thanks.

EDIT:
Your link leads to a 64bit version, but I experience the proble on 32bit too

Ah, I didn't see that, sorry. The bug I mentioned was specifically for 64-bit systems. Best of luck!

---

### Post by rage9 on 2009-04-23
Installed the Jaunty Beta last week, didn't have the latest alsa drivers so I had to fix my sound (like always).  Todays update to full went perfect.

[edit]  Actually it did screw up my sound - again.  How this isn't fixed I don't know.

---

### Post by Ice Rick on 2009-04-23
Well, today, as soon as I woke up, I tried to upgrade from 8.10 to 9.04 through update Manager. Didn't work. Was slow as hell and eventually just sent an error and shut down. Fortunately, the very helpful people here at forums recommended me the torrent download (which I did not know about) and I am using that to download the alternate CD ISO. Hopefully that'll work just fine.

---

### Post by 4wd22r on 2009-04-23
Ironed out the problems with my ATI card on the laptop, my desktop is STILL showing 2 hours to go downloading the files, just started downloading the upgrade on the laptop, hopefully all goes well, I've been plagued with graphics card issues for a while, I'm crossing my fingers that it was related to the ATI driver....hopefully the opensource one will be nicer :D

---

### Post by cullinane on 2009-04-23
Updated from the beta- absolutely no issues whatsoever. 
Really delighted with Jaunty so far, I wasn't able to make Hardy my main OS because of ongoing flickering issues with video and distorted sound, but Jaunty is near-perfect. The open source ATI driver is far better than the previous one I tried last year, too- I won't be moving to the restricted one for fear of messing my configuration. 
Two thumbs up for Jaunty so far- Think I'm ready to leave Windows behind forever (apart from the odd Photoshop job).
:)

---

### Post by jsnelli2 on 2009-04-23
[QUOTE=oldrocker99;7126541]I'm currently upgrading from the automatic upgrader at 50K/sec :(. I had tried 9.04 before but I had MAJOR problems with the ATI fglrx drivers and resinstalled Intrepid. There ***IS*** a new version, 9.04 of the ATI drivers, and they *say* that it supports Jaunty...we'll see in a few hours.

I tried 9.04 once the Release Candidate was put out.  I too had severe problems with the drivers for my ATI card.  I was completely unable to boot the machine.  I downloaded the iso and did a fresh install this morning with absolutely no problems with the graphics drivers.  In fact compiz is running more smoothly than I have ever seen before.

As I am installing necessary drivers I have ran into a single problem though.  When trying to install Adobe Flash either manually or automatically through Firefox I receive an error saying that I am running another synaptic process (which I am not).  Any ideas to help would be great.

Edit:  I ended up installing Adobe through the terminal.  It sat there for a while but I believe my problems all came from it being update day and having a large load on the servers.

Jaunty is amazing and I can say without a doubt the best distribution of Ubuntu so far and DEFINITELY the most painless clean install I have done to date.

---

### Post by autra on 2009-04-23
> **hurstdaj said:**
> I didn't see an option on the update manager, but does anything need to be done to upgrade from 9.04 RC?

As 9.04 is not a LTS release, you'll have to indicate to the Update Manager that you want it...

Follow (if u're a gnome user): 
"System -> Administration -> Software Sources", put your passwd and then click on Updates. 
Release upgrade, "show new distribution" change to "normal releases" and you're done.

Then open your update manager, you should see "new dist available" and a button "upgrade" 

:guitar:

---

### Post by maravingian on 2009-04-23
So far so good with upgrade.  Only slight hiccup is that totem/ rhythmbox music player is playing the sound from CD`s, playlists, or Youtube videos double speed. Any ideas how to slow the bitrate down?

Cheers for any help :P

---

### Post by NinjaBunny on 2009-04-23
Unable to download.  I've been trying to upgrade for over eight hours but the servers are so clogged that I can't make much headway.  After repeated attempts, it's now hung at 651 files out of 1,456 to be retrieved.

---

### Post by Luther11 on 2009-04-23
When I first tried to upgrade this morning, I got disconnected after downloading about 200 files. After that, the update manager would freeze whenever I click the upgrade button.

I tried downloading the alternate CD by torrent and upgrading from that. It gives a dialog asking if I want to go online to get the latest updates. If I say yes, the upgrade tool freezes PLUS I have to reboot to free up the update manager. If I say no, it tries to remove all the software I've installed from synaptic. This isn't really acceptable if I can't even connect to the server to reinstall everything.

So it looks like upgrading is impossible right now. Even if I do a clean install, I don't know if the update manager won't keep freezing.

Using amd64.

EDIT: I guessed the removed packages were due to version numbers conflicting with the new packages, so I decided to risk the upgrade. It's done now and seems to be working ok.

---

### Post by ray17374 on 2009-04-23
Worked flawlessly.

---

### Post by caro on 2009-04-23
I upgraded to the release candidate last week with no problems at all.  Best upgrade yet for me.  The boot time is much shorter and the login screen is much improved.  Of course I had to adjust some of my compiz settings.

My only problem is that now hyperlinks in Thunderbird don't launch my browser (Firefox).

---

### Post by DKnight on 2009-04-23
I updgraded from xubuntu 8.10 to 9.04 (using the updater, process took 1 hour). Pretty good so far, a couple of problems with sound though; suddenly the tray sound icon is gone, alsamixer doesn't seem to respond and the multimedia keys on my keyboard don't work either. I think it's Amarok 2 fault.

---

### Post by remin8 on 2009-04-23
Is anyone else having trouble with the repos?  I know this should be expected, but I haven't seen any clammoring on the forums so I was wondering if it was just me...?

Thanks,
Jay

---

### Post by volneilo on 2009-04-23
Downloaded ISO and tried in an USB stick (Unetbootin). Everything went well, ***except*** by Compiz... I'm one of the non-lucky Intel i845 card owners. I skipped Intrepid because of this, and Jaunty still didn't make me happy on this point. So, I'm sticking to Hardy and hoping someone have a light on this to bring Compiz to life again.
Yes, I do care to desktop effects THIS much... ;)

---

### Post by jo4hnc on 2009-04-23
Success! What was slow as molasses to download turned out to be smooth as butter. 7 hours to download and 35 minutes to complete the install. The upgrade resolved a few minor glitches, the memory loss problem at bootup, an internal drive that was being recognized as removable is now fine and the nvidia screen resolution problem I had. Now its on to making sure that all of the repositories are up to date.

Thanks Ubuntu Jaunty team!

---

### Post by 4wd22r on 2009-04-23
> **remin8 said:**
> Is anyone else having trouble with the repos?  I know this should be expected, but I haven't seen any clammoring on the forums so I was wondering if it was just me...?

Thanks,
Jay

:\ well I've been downloading for about 3 hours or so......between 0 and 60 kB/s slooooooow  I'm assuming its on the repo server side.

---

### Post by taygan on 2009-04-23
> **4wd22r said:**
> :\ well I've been downloading for about 3 hours or so......between 0 and 60 kB/s slooooooow  I'm assuming its on the repo server side.

The torrents are speedy, and you can use the "Alternate Install" CD to upgrade (no live session, but it can do clean installs too - the old clunky way).  Note: clean installs are *much* easier with the "Desktop" CD.

Official torrents here: (look at the bottom of the page)

[http://releases.ubuntu.com/releases/9.04/](http://releases.ubuntu.com/releases/9.04/)

---

### Post by jemlinus on 2009-04-23
Please use torrents guys.  I got full speed using torrents.

---

### Post by dougalkerr on 2009-04-23
I have already posted a thread about my experience but, here it is again...
I am still new to Linux but, after buying a new laptop and installing Ubuntu 8.10 64 bit and upgrading as and when available I had a lovely almost fully functional system with Cyberlink PowerDVD not running through Wine properly being the only thing that was letting my experience down as I can't watch any commercial DVDs. Small price to pay for something that is otherwise very nice to look at and use, with Compiz fully operational adding to the good experience.
So, now for the down side. Updates were available tonight with the offer of upgrading to Jaunty. I proceeded (no fear) and the files were downloaded. The system just seemed to sit there after the files were downloaded with no signs of installs taking place after half an hour. So I rebooted. The updates notification icon was showing and I proceeded with a warning that a partial upgrade was a choice. I continued and the system finished downloading one further file out of the 782 files if I remember correctly. So there was a message displayed before I could conti nue saying it was "imperative to run liloconfig and execute cd /sbin/lilo after liliconfig" or lilo wouldn't work.
If memory serves me well Lilo is a boot menu similar to Grub - yes?
So, I click the forward button (only other option is to cancel).
The upgrade to Jaunty continues and the system reboot is required.
Well Grub shows the boot list as before - I choose my last Ubuntu configuration and the Ubuntu splash screen shows with the animated bar and after about 20 seconds or so I get the following displayed;

Boot from (hd0,5) ext3 4c3133d3-2953-47fb-b4b8-4076a6bf3f07
Starting up ...
Loading please wait ...
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the root device?)
 -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4c3133d3-2953-47fb-b4b8-4076a6bf3f07 does not exist. Dropping to a shell!

BustBox v1.10.2 (Ubuntu 1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

So, I type in liloconfig as I believe this may be wanted as described when Jaunty was to be installed but all the time in the back of my mind I am thinking that there is something wrong with the file system missing root. Anyways, system returned;

/bin/sh: liloconfig: not found.
(initramfs)

I type cd sbin/lilo "again not expecting much and I was right. System returned:)

Couldn't cd to sbin/lilo.

I typed ls and sure enough the folders are not there and neither is liloconfig (not even a lilo folder). Result of ls is;

dev var scripts lib64 lib etc sys tmp root init usr bin conf sbin proc

Looks like I will have to download and burn an install cd using 'Windows'!!!!!!!! - yuck. Doesn't matter how much I dislike Windows I seem to keep coming back to it as always being there for occasions like this. Boy am I glad I kept it as a dual boot option. I am sincerely wanting a purely Linux experience but, my faith is being stretched. The recovery options available on Grub will do nothing either so for me it seems I have lost my Ubuntu install.
How can I prevent such a catastrophic failure of an Operating System install losing my present system. It I did not have Windows on here just now I would have to reinstall Ubuntu to be able to get onto the Internet again and type out my experience to you guys and look for help and advice.
So, bottom line? Is Jaunty safe to use or not. Do I bother with trying to burn a cd and try again. I can imagine like a lot of people I always want the most up-to-date system running. How do I prevent having to reinstall the whole system again if problems like this occur. I am willing to listen and learn...

---

### Post by satx on 2009-04-23
> **Xir said:**
> After reinstalling and performing the do-release-upgrade again, again the VM will not boot. I guess I'm done working with the upgrade today, back to 8.10 for me until I have time to troubleshoot it.
DI you recompile the VM for the new kernel using: 

sudo vmware-config.pl

I have to do this after each major release upgrade.

---

### Post by fishyf on 2009-04-23
I booted an eee 1000 from the live USB and am typing this, so the Wireless works nicely, booted relatively quickly.
Audio Playback is fine, but the microphone doesn't work.
The SD card works.

Trackpad works very well.

Webcam works fine (tested with cheese)

I liked the remix version but quickly went back to Ubuntu classic for a more familiar ubuntu look.

From my perspective, it's perfect apart from the microphone problem.

---

### Post by theducks on 2009-04-23
Used Update Manager. After hours, failed with errors.  Restarted (very slow to respond) and finished the 20 files I still needed.
Then I got to watch the time remaining jump around worse than a Yo-Yo for over an hour :P 
Reboot time:  Black screen "_ (blinking)"  (kernel 2.6.28-11-generic) :(

Tried again in recovery mode  "_"  :(

Tried older kernel 2.6.27-14-generic  :popcorn:
Fired off Synaptic and Kernel 2.6.28 does not even show 
on the list.  :confused:

Toshiba Satellite 1135

---

### Post by saboya on 2009-04-23
My upgrade experience:

I'm an owner of a Lenovo Thinkpad R61 with Intel GM965 Graphics and Core 2 Duo T8100 CPÛ. I installed Ubuntu on it because I thought it would be the best option for a Linux distro since Laptops are quite tricky to fiddle with sometimes. I use Gentoo in my dekstop.

First of all, the mirrors were really slow... But that's fine, considering the amount of people trying to do the same thing as I am.

I tried to find the release notes / changes from Intrepid, but I couldn't find nothing interesting besides boot time improvements, Gnome 2.26 and a new GUI for Brasero or something.

I had some custom conf files that were overwritten by the upgrade, which Ubuntu prompted me to do so. I also find that acceptable but it would be nice to have a merge utility so I have more options instead of "yours or mine". So far, so good.

But then, when I finally finished my upgrade and restarted my PC, I see that Compiz is not working. Fiddling around, I found out that my card is blacklisted in /usr/bin/compiz. That took me to a Google search which revealed that 9.04 pretty much borked every PC with an Intel GPU out there, because of DRI2/UXA stuff. Some useful topics and bug reports revealed a possible fix which requires you to live on the edge with unsupported kernel, vga driver and more, only to provide a functionality that I took for granted when I upgraded which could be avoided simply by providing a changelog that said: 

"Hey people that use Intel graphics, if you upgrade you're going to have lots of problems, and 965 users will not be able to use Compiz!".

I find that unnacceptable for a distribution like Ubuntu that should be as user-friendly as possible. I had no problem solving the issues above, but I'm aware that I'm not part of the majority of the users. And I installed Ubuntu EXACTLY for the reason that I wasn't willing to have this kind of issue, I just wanted things to work. Comparing this upgrade to using Gentoo, I find that I have no real benefit in using Ubuntu. I don't understand how can anyone release something in this state in a distro like this.

I'll be waiting for an official solution for this, if any.

---

### Post by MikeInParadise on 2009-04-23
First as others have mentioned I had trouble doing the upgrade, really really slow and then stopped at 510 out of 1019 files. I had to restart it twice to get it to finish.  Took about 9 hours from the start.

After the upgrade downloaded the upgrade proceeded just fine.

I have a D945GLCF2 330 Atom running a Mythbuntu Media Center mixed in with a Windows Homer Server and Several Windows Media Center.  I have been thinking of converting the media centers over to Mythbuntu but I still have some video out issues and some TV Card issues.

Anyways I had applied the intel patch to video driver for the D945GCLF2 so that the SVideo out would work. After the installed the SVideo Out Sync is off but I checked the xorg.conf file and the changes that had been made are still there. 9.04 did comment out some of the keyboard commmands.

Also I had to make some changes to the shutdown order on so that the Shares to the Windows Home Server in fstab would not hang the system on shutting down and these are gone and it is now hanging up on shut down so I will have to dig up those commands.

I had Nautilus installed as my preferred file manager and that has disappeared as well.

But all the Media functions within  MythBuntu seem to be fine.  I can access all the Videos, Music, Images off the Windows home server.

Now I have to go get the SVideo Fixed and the Shutdown of the Windows Shares to work properly.

This is just my first pass listing the obvious problems but so far an ok for the update, not perfect.

This machine is triple bootable into either mythbuntu, Windows 7 or OSX 10.5 operating systems but I am still booting it into mythbuntu and will continute to (as long as I can fix the SVideo out)so that is good!

Even better as I would never have considered running an update on one of my windows machines but would have done a cold install.

Time will tell!

---

### Post by franzrogar on 2009-04-23
Install - worked but had few things to fix, nothing serious though

==x86_64==

These were the problems:

PROBLEM 01 - Alternate CD base install failed: insert CD (but I didn't removed it).

SOLUTION 01 - Go to a terminal (Ctrl+Alt+F2). Hit "Return" to activate it.
Type:
```
cd /target
rm cdrom
ln -s media/cdrom0 cdrom
```

Go back to Install screen (Ctrl+Alt+F1) and Press "Continue" so it reloads installation disc.


PROBLEM 02 - I own an Intel X3100 GMA... which is blacklisted for Compiz and driver still uses old EXA mode.

SOLUTION 02 - I "create" an base xorg.conf (default one was empty) typing this in a terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And added, in the new xorg.conf file, using:
```
sudo gedit /etc/X11/xorg.conf
```
, at Section "Device" the following lines:
```
        Option          "MigrationHeuristic" "greedy"
        Option          "AccelMethod" "UXA"

```

And removed checks for Compiz as follow:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Restarted and done. I loosed a bit of FPS (about 5%) but it's 100% stable (just some problems with Blender 2.48a).

---

### Post by hagantic42 on 2009-04-23
Ok, so, I cannot upgrade. The internet is working, I'm posting from the pc  but as of right now I cannot get the update manager to upgrade. It just freezes. I attempted sudo apt-get update then sudo apt-get upgrade and neither of these seemed to work PLEASE HELP! It could be that the servers are clogged but it should not be causing the entire update manager to to crash and make me force quit it.

---

### Post by TBerk on 2009-04-23
> **jemlinus said:**
> Please use torrents guys.  I got full speed using torrents.

(This is the follow up to my initial post.) 

I used Synaptic Package Manager this morning (PST) and it was slow to refresh the package list as well as slow to download. 

After rebooting without trouble I swapped my NVidia AGP based card (w/ Analog Output) for an NVidia PCI card (w/ Digital Output). Both cards are GeForce 5200 cards. No config was necessary to swap cards, I only mention it because it was uneventful.

Looking over my installed packages it seemed I had Java ver 5, so I looked to update it to ver 6. Downloading the bin file from Sun was faster but very manual, using SPM to 1st install v6 then remove v5 was much easier, if slower due to the current Ubuntu Servers state of activity.

As to the quoted post above I am currently downloading via torrent the 9.04 iso so I can burn an up to date Install disk, but I'm also seeding it (seems the right thing to do).

(Not super fast right now, but I'm using a 'G' based wifi connection.)


So, to recap; I had set up a dual-boot WinXP/Ubuntu 9.04 BETA (with Studio laid over the top) which I kept up to date on the regular via Synaptic PM, and the resultant Upgrade to Released 9.04 today has been problem free.


TBerk

---

### Post by not a pipe on 2009-04-23
meh, halfway through the upgrade it decides the power is low and shuts down the computer (it was ******* plugged in). 

so now ubuntu doesn't work (mouse and keyboard don't work)

**** this

---

### Post by kfrancart on 2009-04-23
The download was slow for the upgrade. To be expected with a new release.

Was dropped into terminal mode after upgrade - didn't like my video driver.
It's an nVidia, should have known better. Got it working before in 8.10 but those drivers don't seem to work any more. I've lost the 3d & all visual effects. I've tried to reinstall the different nVidia drivers with no luck.

If anyone has had any luck with nVidia and 9.04, I'd appreciate any pointers. - FIXED - please note: It wasn't the drivers!

Downloaded the distro off torrent. Backed up data files. Reinstalled after deleting the upgraded partition. Everything is working! 
I believe the issue was using a different distro of Ubuntu 8.10 - I was using Ubuntu Studio. Don't know if it had anything to do with the above issues. Still had to use SuperGrub to fix the boot mechanism. My system has two hard drives and Ubuntu has the second drive which is only recognized as root (hd2,4). Don't care since it is working beautifully! Now I'll go test everything else :)

---

### Post by stemagic on 2009-04-23
H/W IBM/Lenovo T60 laptop
Backed up data from stable 8.10 I've been running for a few months.
Downloaded and created live 9.04 CD - Argonne Natl labs seems the speediest.
Created a bootable 4 G Maxtor USB stick and process went thru fine (previously formatted as ext3). Yet to fire USB stick up.
Installed flawlessly on HDD from live CD.
Install included resizing NTFS partition and creating and formatting new ext3 partition (and swap). Worked great.
Booted up. works like a champ! Love the look, the speed. Glad I did it.
wireless up in seconds; Included ATI driver allows extra visual effects with wobbly windows. No more proprietary ATI driver!
Ran update manager; 8 MB of firefox related files are the only updates, ran fine. 
Checked to see of audio ecorder works; it does not work with built in mic.

STEmagic

---

### Post by joplass on 2009-04-23
Mine is going through the update manage but the download is stuck at 8 of 1231 for the last 2 hours or so.  Is it supposed to do this?  I will let it hang on there until tomorrow morning. :(

---

### Post by pw_f100_220 on 2009-04-23
Fresh install on T61...all but Flash.
Youtube works...but screw youtube.  I want Hulu.com.  It worked great in Intrepid

I did experience the poor performance with onboard Intel graphic chip...but somehow that went away after a couple restarts for other updates...

HULU IS MY TV SINCE I DON'T HAVE CABLE...I JUST NEED TO WATCH THE OFFICE

---

### Post by Shrikaant on 2009-04-23
DELL Inspiron 1525 with Intel Graphics

I find it VERY SLOW. 50seconds to get the login screen, and after entering the password, 30 seconds to get working desktop.

:(

---

### Post by AlphaMack on 2009-04-23
> **saboya said:**
> My upgrade experience:

I'm an owner of a Lenovo Thinkpad R61 with Intel GM965 Graphics and Core 2 Duo T8100 CPÛ. I installed Ubuntu on it because I thought it would be the best option for a Linux distro since Laptops are quite tricky to fiddle with sometimes. I use Gentoo in my dekstop.

-snip-


As another owner of a R61i with the same GM965 chip I can tell you that Compiz works without a hitch so as long as you specify this in your xorg under devices:

```

Option  "MigrationHeuristic"    "greedy"

```

This cut down the system and CPU loads quite a bit, but not as much as I want (compared to Hardy).

ath5k is complete garbage; I replaced it with the madwifi driver provided.  NetworkManager was also swapped out for Wicd (remember ath0 instead of wlan0 while keeping the wext setting).

So far so good.

Also you may want to look into [this](http://fsrc.wordpress.com/2009/04/11/conexant-cx20549-venice-sound-input-working/) to get your internal mic working.

---

### Post by pw_f100_220 on 2009-04-23
WOOOOOOO!!  flashplugin-nonfree!!
only problem was flash...swfdec was in the way!  Would've been a flawless install if only I had known!

I spent way too long trying to get that to work

---

### Post by pw_f100_220 on 2009-04-23
and startup and login seem to be blazin to me!  not as fast as Intrepid it seems...but I was mostly using Fluxbox...I plan on enjoying Gnome for a little while before I go back and see how Flux runs over Jaunty

---

### Post by thebrokenbox on 2009-04-23
Well I did a clean install of Jaunty, and it's pretty nice. I've been working with Linux Mint 6 for over a month and thought with the release of 9.04 I'd give Ubunutu a shot. The only trouble I'm having is that it is running much slower then anticipated and my cpu is incredibly high for running just firefox. I guess I'll have to post a thread to see if I could get some help with that, other then that I love it so far.

---

### Post by Keithhed on 2009-04-23
was running the RC for the last week.  did fresh install a couple hours ago and its like riding a bike. get drivers and set up programs that i use. no major issues.  :guitar:

---

### Post by jazzman65 on 2009-04-23
I did a fresh install, mainly because something happened with my previous installation of Intrepid that caused it to continuously loop through the login screen.  Fortunately, I keep everything important backed up and I usually like to do a fresh install.

Anyway, the installation was flawless and other than resetting the notification method, I don't believe I've had any real problems.  So far, I'm quite impressed, as I usually am with each version.  It just keeps getting better and better.  Great job again!

---

### Post by 4wd22r on 2009-04-23
> **pw_f100_220 said:**
> Fresh install on T61...all but Flash.
Youtube works...but screw youtube.  I want Hulu.com.  It worked great in Intrepid

I did experience the poor performance with onboard Intel graphic chip...but somehow that went away after a couple restarts for other updates...

HULU IS MY TV SINCE I DON'T HAVE CABLE...I JUST NEED TO WATCH THE OFFICE

try watchtvsitcoms.com :D

on try number 3 now, only 100 or so files left to go....YAY!

---

### Post by alphadelta14 on 2009-04-23
tried to do a synaptic install
FAIL
stopped at 730 files downloaded and said couldn't connect to the archives. i know that the internet was working well, as i was able to google search if anyone had this problem. i don't remember the file names exactly. i tried twice (thankfully i don't have to restart all of the downloads). and all of my third party software is disabled until installation finished. i have internet, and thats it for now as i don't want to mess with anything else until my sluggish installation works.

---

### Post by ActiveFrost on 2009-04-23
Ok, so - I needed to "clean up" my system and instead of keeping 8.10, I upgraded my sys to Jaunty ( Update Manager -> Upgrade ).
Downloading files took about 30 minutes and installation went smoothly - haven't seen any errors/bugs so far .. I'll say it's pretty nice ( faster booting, updating, downloading .. ) :guitar:

---

### Post by subtorn on 2009-04-23
Finally found a link that didn't take 6 hours to DL, got it in under 20 minutes.  Mounted the iso and installed without any problems.  After using 9.04 beta for the past 3 days, I was a little disappointed that the mouse jog wheel didn't switch screens in the full release like it did in the beta.

Small detail since both the beta and full release work with my AR5007EG without needing the ndiswrapper.  Intrepid and Hardy wouldn't recognise it, so JJ is a much better fit for me.

I give it 3 :guitar::guitar::guitar: and a :cool:

---

### Post by drjonze on 2009-04-23
Two installs done!(jaunty 64-bit) The only issue was extremely slow downloads of packages, updates, etc which was to be expected and was not as bad as I thought. My installs went smoothly, I have it down to a fine art now.

---

### Post by lroux on 2009-04-24
Using the Update Manager, and it keeps "sticking" in the Getting New Packages step.  

Been at 661 of 1762 for an hour.  Time to kill it.  Last time it stuck at around 150.  Wired Cable connection, so it isn't a network drop out. 

II wonder if the servers may be swamped and when it gets slow response the Update Manager is just going into perpetual sleep mode or something?

---

### Post by Teatro on 2009-04-24
> **ActiveFrost said:**
> Ok, so - I needed to "clean up" my system and instead of keeping 8.10, I upgraded my sys to Jaunty ( Update Manager -> Upgrade ).
Downloading files took about 30 minutes and installation went smoothly - haven't seen any errors/bugs so far .. I'll say it's pretty nice ( faster booting, updating, downloading .. ) :guitar:

30 minutes!  Mine threatened 2 and half days before I cancelled it! God hates me.

---

### Post by ericy on 2009-04-24
I tried jaunty out first with live-usb stick, but it failed to boot up. Found a work-around from a thread here and it worked. 

The X environment worked the first time, which was a relief because it was a blank screen back in 8.10's initial run.  

I thought that should be it, so I went ahead and ran the install program, but it crashed after it showed an "Error 5" pop-up window. I tried a new install again and same result. I checked data integrity and it's fine. I then did a reboot and started the whole process again, and this time it installed successfully.

My machine:
ECS 780GM-A(south bridge: SB700), AMD 64 x2 brisbane 2.3G

live-usb stick boot problem:
(Stuck at splash screen for a few minutes, then this:)

modprobe:FATAL: Could not load /lib/modules/2.26.28-11-generic/modules.dep: No such file or directory

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu6) built-in shell (ash)
....


-----------
live-usb stick boot work-around: Unplug the stick during the splash screen, wait a second or two, then plug it back in.

----

My next step is to try to install fglrx. I tried two times today, but apparently the server was too busy ....

---

### Post by wd5gnr on 2009-04-24
Upgrade was almost painless. Kubuntu AMD64 A few notes:

1) I started the upgrade to find that the default servers were dying. So I interrupted the download and changed to mirrors.kernel.org in sources -- much faster but also never could get the update to fully start from the GUI again, so I used apt-get distro-upgrade or whatever. I had a few "blow ups" where I had to do apt-get -f install to get it all cranked over.

2) For some reason my BIOS remaps my boot drive so that the grub stuff never gets updated right. I know this and just go manually touch the menu.list file after any kernel update.

3) When I booted, my raid10 array was dead! (holds /home and a few other things). The update tried to make a device called /dev/md_d0 and put one of the disks on it. So I diddled with mdadm.conf and finally got the array back up with 2 of 3 disks. The one it tried to mount was marked bad. So I had to re-add that disk (it is recovering now -- dropping a disk on a raid array is recoverable.. that's the point).

4) Had to rebuild NVIDIA and XFI drivers and reinstall Virtualbox drivers. All worked fine! Yay!

5) I am getting some odd startup messages I have not seen before but won't investigate them tonight.

6) Lost my main desktop KDE settings! Not sure why. Had to build a new panel. No biggie.

7) I have some temp sensors on a hiding panel on my second monitor. I about flipped when I saw 100 degrees! Apparently the Plasma widget now uses F instead of C and there doesn't seem to be a way to change it. 100F is OK but when you are using to seeing C... 100C would NOT BE OK. ;-)

Overall not bad, but not for the faint of heart either. On the other hand, most people probably don't have funky hard drives, RAID arrays, etc. etc.

---

### Post by lisati on 2009-04-24
I originally installed the release candidate on my older laptop, no major hassles apart from something (probably carelessness on my part) borking the sound on Youtube and a couple of other flash-based web sites. Just finished an upgrade after a fresh install on same laptop - it took a couple of hours (I must get round to putting in some more ram, as soon as my budget permits), and I still need to check that everything is the way I want. 

On my other laptop, an upgrade from the 64-bit version of 8.10 via update manager went flawlessly and took around an hour.

On my COMPAQ desktop an install from the release candidate 32-bit CD went flawlessly: the only hassle is setting the video mode properly, the progress bar sends my monitor into a tiz, reporting "signal out of range", and fixed by setting "nosplash" in grub's menu.lst - I'm currently waiting on a 64-bit server disk from Cannonical, intended for use with this machine.

My fourth machine, sadly, doesn't seem to like Ubuntu (the machine's too old, specs too low), but there are alternatives.

EDIT: Any chance of a multi-choice poll for those of us with multiple machines? Anyone up to it?

---

### Post by halovivek on 2009-04-24
I tried to upgrade two times while testing and the system got crashed.
But when i do the fresh install of jaunty in direct it went fine and doing good.

---

### Post by Yucko on 2009-04-24
I did a clean install, but so far found the things mentioned below not working:

- themes

It just says "Starting <application>" on taskbar .. but after a few seconds it disappears without even opening the themes windows.

On the other hand, the problem that when closing my laptop and the screen not coming back on when opening it has been fixed :D

---

### Post by Messyhair42 on 2009-04-24
downloaded the ISO through torrent, much faster than i was getting from HTML. have yet to upgrade b/c i want to install it on my 1TB drive which means getting rid of windows and then formatting the HD i currently have 8.10 on. i've been worried about how i'm going to do this but feeling better now, should be able to do it on Saturday if i get all my docuements backed up.

---

### Post by sports fan Matt on 2009-04-24
Since I cant sleep, im trying again using best server since I killed EXT3..Im preparing to go 8.04 (disk i have) >8.10 using "select best server"

---

### Post by Svensk023 on 2009-04-24
I have been with Ubuntu since 7.10 and this is the first time I was able to install Ubuntu on both my desktop and laptop and have **everything** work right out of the box. 8.10 was a nightmare in terms of my drivers for wirless and ATI video.

I'm utterly overjoyed

---

### Post by sflicht on 2009-04-24
I'm running an AMD64 Thinkpad. 
I upgraded from Intrepid via the update manager. The download hung at one point,
causing the updater to quit, but when I tried again it succeeded, picking up where it left off.

The installation went smoothly, although there were some disturbing looking messages in the terminal during the installation. Upon restart, the only thing broken was the NVIDIA drivers. This is not that surprising to me, as this has been broken every time I installed a distro on this machine. (The builtin Hardware Drivers feature on the System->Administration menu has never detected any drivers, used or unused, for me.) I eventually managed to reinstall the latest version of the drivers from the NVIDIA website, and now things seem to be working fine.

---

### Post by jikuty on 2009-04-24
Almost a seamless installation on my T61 Thinkpad. Downloaded the alternate installation CD through torrent (download took about 30 minutes, so was much faster than the official ubuntu servers). Installation took about an hour total including getting any necessary updates. Interestingly, even though I told the installer not to use the network at all, it still went through and downloaded a few packages/updates before actually installing all the packages from the disc.  

The only problem I experienced was when I foolishly decided to keep the original grub menu.lst when installing (I was given the choice of keeping the original menu.lst or using an updated file). So, when I rebooted, 9.04 was working, but with the wrong kernel (2.6.27-9 instead of 2.6.28-11 as intended). All i had to do to fix this was to manually modify my menu.lst in order to change the 2.6.27 references to 2.6.28 ones. 

After that, bootup was smooth (and fast!) and everything worked fine. So far, I'm very satisfied with 9.04, especially the slick new notification system. Great job devs!

---

### Post by simpleC11 on 2009-04-24
Nevermind.....

---

### Post by tomsa on 2009-04-24
I did a clean install only to find out that my headphone jack does not work.  This is a major headache for me as I use my laptop for many things as a professional musician.  I wanted to try upgrading because skype was breaking my wireless connectivity in intrepid.  However, I should have checked the headphone jack for sound output with the live CD- in hindsight, I only checked the speakers.  Needless to say, it's a good thing that I dual boot windows for these situations, even if I don't like using it.  At least I can call my wife on that side of the computer when I'm out of the country.  There is a related bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755)

And I've asked the mods to move this thread from the Jaunty testing and discussion section to a an open forum:

[http://ubuntuforums.org/showthread.php?t=1131661](http://ubuntuforums.org/showthread.php?t=1131661)

If any of you know a solution to this, I would really appreciate it.  This is the first release where I haven't had trouble with wifi or 3D graphics, which I was really excited about- and I was genuinely impressed with the look of the "dust" theme and the boot time. So you can imagine how annoyed I am that my headphone jack doesn't work.  That one thing, because of my work needs, move this release (in my mind) from awesome to lame.  Meh.

---

### Post by saboya on 2009-04-24
> **AlphaMack said:**
> As another owner of a R61i with the same GM965 chip I can tell you that Compiz works without a hitch so as long as you specify this in your xorg under devices:

```

Option  "MigrationHeuristic"    "greedy"

```This cut down the system and CPU loads quite a bit, but not as much as I want (compared to Hardy).

ath5k is complete garbage; I replaced it with the madwifi driver provided.  NetworkManager was also swapped out for Wicd (remember ath0 instead of wlan0 while keeping the wext setting).

So far so good.

Also you may want to look into [this]("http://fsrc.wordpress.com/2009/04/11/conexant-cx20549-venice-sound-input-working/") to get your internal mic working.
Your solution is not a real solution. Actually I had no problems making it work using this method:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

My real complaint lies on the absence of documentation. That alone would have kept me away from Jaunty and keep my Intrepid Ibex install, which worked fine. And no matter which method is used to "solve" the problem, it's not something an end user should be doing, that's why I installed Ubuntu in the first place. If the only thing I get from Ubuntu is a larger user base to help me solve my problems, I might as well stick to other supposably non-user-friendly distro, like Gentoo, which I use in my desktop.

---

### Post by radovic on 2009-04-24
I am running tripple system on my box. XP runs OK, CentOS runs OK, I have tried to install Jaunty 32bit, burned two CD-s, tried with both, and I could not make it to work. I wanted for Ubuntu to be my master OS (controller of GRUB etc), so i tried to install lit the last. I do not know what the problem is, first disc gave me I/O error on 51% of installation, so I burned another one using slowest possible speed (4x), went better, but no luck. First, on 83% it hangs while updating mirror, so I turned my modem off, it continued to 88%, blacked the screen and started live CD in try mode without restart, just after all that installing, loaded in live mode, instead of asking me to reboot. I have no clue what went wrong, so I will download the cd image again, checksum it and burn it on yet another cd, and try again later today.
Any ideas???

---

### Post by pbpersson on 2009-04-24
I just installed Jaunty on a test machine - fresh install - and had the same exact problem with DHCP that I reported in [this thread]("http://ubuntuforums.org/showthread.php?t=1113783") a few weeks ago.

However, I fixed that, noted how I fixed it in that thread, and now I am continuing with my testing.

So far so good, but the repos are very slow.  Oh, and I am seeding the CD for everyone from the Hardy machine in my lights-out server room.....that could also be part of my problem, I keep forgetting about that little detail.  ;)

---

### Post by syntheticflag on 2009-04-24
So far so good on the download, but the servers are horribly busy.  I'm about an hour into the upgrade from Intrepid Ibex (8.10) and the predicted time is all over the place, from 1 hour 15 minutes all the way up to 3 days!  Looks like it's about 33% in the last hour, don't think I'll have fingernails by the time it's all over...

---

### Post by kbish on 2009-04-24
Upgrades: 6->7->8->9.04
Laptop: HP Compaq 6710s 

My upgrade went smoothly,, I have only two small problem:
1) some time lost network
2) Status monitor show CPU ~50%

---

### Post by Razmear on 2009-04-24
Finally completed my upgrade, YaY!

First tip, go to Admin / Software Sources
On the Ubuntu tab click on Download from, select Other then hit the Select Best Server button. 
This will ping a few hundred different servers and hook you up with the fastest one. I was getting 14kb/s downloads before this, then hooked up with a fast server and got 700 kb/s afterwards. Life got lots better. 

After upgrade SWFDEC decided it wanted to be the master flash player in Firefox, so I had to go into package manager and kill it off, now Adobe 10 is back and flash is happy too. 

Haven't tested all the other apps yet, but VLC is alive and well. 

I'll edit this post if I find any other glitches and solutions for them. 

Have fun.
eb

---

### Post by Silver Doe on 2009-04-24
Can't run LiveCD because my LCD monitor is just 1024x768 and it picks up more than that.
So i can't even START upgrade!

---

### Post by Teufel on 2009-04-24
Update took about an hour to get done. After the first reboot I got the "Ubuntu is running in low-graphics-mode" and all my compiz is gone. I can't reinstall or reactivate it either, it's just gone.
Also, my multimedia keys (Mute, Volup, Voldown) don't do anything anymore.
I see the little notification on the top right but it doesn't actually do anything

---

### Post by scarf on 2009-04-24
> **Razmear said:**
> Finally completed my upgrade, YaY!

First tip, go to Admin / Software Sources
On the Ubuntu tab click on Download from, select Other then hit the Select Best Server button. 
This will ping a few hundred different servers and hook you up with the fastest one. I was getting 14kb/s downloads before this, then hooked up with a fast server and got 700 kb/s afterwards. Life got lots better. 


thanks so much for that tip!  i went from 22 hours remaining to already installing. :P  will report back on the upgrade later.

---

### Post by asdir on 2009-04-24
Upgraded with little problems.

My sound was incredibly low, even when I set volume to the highest level. To fix that, I had to change the sound system.

Moreover, it was and still is a bit annoying that alt+tab+shift does not give me the last window any more.

Apart from that, things seem to be fine.

edit: and tracker seems to be buggy, it stopped indexing after hugging the cpu for half an hour and made me reboot.

---

### Post by AlphaMack on 2009-04-24
> **saboya said:**
> Your solution is not a real solution.

[Might want to tell that to the devs.](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

> 
Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf. 


It worked for me with the usual warning of YMMV.

That said, it still doesn't excuse the fact that this regression was allowed to slip through into the final release.

---

### Post by oudeis on 2009-04-24
> **radovic said:**
> I do not know what the problem is, first disc gave me I/O error on 51% of installation, so I burned another one using slowest possible speed (4x), went better, but no luck.

Seems to be a known problem with 2.6.6.20 kernel..but make nosense on Ubuntu 9.04.
BTW I had the same problem and there's no way to find a workaround by now. I wasn't able to make a clean installation only using the newly released CD iso of 9.04 (Ubuntu and KUbuntu).

> Input/Output error during read on /dev/sda
:(

---

### Post by zeroseven0183 on 2009-04-24
Stunningly fast!

No blood, no sweat, no tears!

---

### Post by _sleeper on 2009-04-24
i had quite a messy upgrade from hardy. my xorg crashed after using the nvidia drivers and now i'm on cl only. another thing is that grub didn't update menu.lst, so when i boot it gives me the "8.04" option. strange thing is that it boots normally on jaunty!

---

### Post by markpwilms on 2009-04-24
I'm running Kubuntu 8.10, and it is flawless!  I'm a little nervous upgrading.  Is it really worth it?

---

### Post by blackSP on 2009-04-24
Running on an Asus F8P laptop with Radeon 2400, 2 gb ram, no problems with 8.10.

After the upgrade none of my windows have borders or a windows bar. Can't resize them, move them.

Video output sucks. No sound.

Boot time now about 100 seconds.

So I will wipe the damn thing tonight and start from scratch :mad:

---

### Post by DaveySpeedstar on 2009-04-24
I've been running Hardy as I had kernel compatibility problems with Intrepid.

I updated through the update manager, and although slow, the speed did pick up in the early hours of this morning - I guess the servers were very busy last night, 

I had issues with viewing videos on YouTube, but I went into Synaptic, searched 'Flash', and re-installed all marked results.  This has sorted out YouTube, but some other Flash based sites are still not working properly.

In the whole scheme of things this is hardly a major problem, and Jaunty looks really good so far.

---

### Post by scarf on 2009-04-24
ok i'm putting in my vote for "Upgrade - worked but had few things to fix, nothing serious though" on this old Sony pcg-tr3a laptop.

those few things, so far:

0. download was really slow. after cancelling and performing "select best server" the upgrade went much faster. maybe "select best server" could be automated for upgrades?
1. i use xscreensaver, so had to reinstall that
2. i don't use all that evolution* stuff, so had to re-remove that. probably a lot of other stuff got re-installed too that i had previously removed (ubuntu-desktop dependent i suppose), i will slowly remove that over time as i notice it.
3. i don't care for the new yellow color for the system monitor's network statistics.
4. adobe flash got installed?  "WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies that you have accepted the terms of that license."
i never was prompted about the license, nor did i agree to it.  will be removing this.  how about supporting gnash?
5. sansa e280 mp3 player doesn't seem to be getting mounted. i can see it is detected in dmesg, though.  [found a bug report and workaround for this](https://bugs.launchpad.net/ubuntu/+bug/345916), which did work in my case.

i have an encrypted hdd, so that is always a concern when upgrading, but no problems with that.  rt2860 wifi card still working [s]great[/s] ([not really](http://ubuntuforums.org/showthread.php?p=7136315#post7136315)).  sound and video appear OK, played back a divx file fine.

all in all i am very pleased. thanks!!

---

### Post by Menschenfresser on 2009-04-24
Fresh install here (I had originally installed the 32 bit version of hardy instead of the 64bit one), no problems with any hardware.

---

### Post by ^_Pepe_^ on 2009-04-24
Hi!

These are my results.

1. Medion Akoya Mini E1210. Clean install. Absolutely no problem. Everything working out of the box. Thunderbird gave me a problem with IMAP google account configuration, but I could fix with an addon.

2. My home server (P4, ACME Motherboard, old ATI GPU, lots of HDDs). From 8.10, just clicked to 9.04 and everything worked ok. Fantastic.

3. HTPC. (Homemade PC: Asus M2N, AMD Be2350x2, 7950GT passive, DVB PCI card, and Logitech DiNovo bluetooth keyboard). I couln't resolve the keyboard issue in 8.10 [edit]([https://bugs.launchpad.net/ubuntu/+bug/205991](https://bugs.launchpad.net/ubuntu/+bug/205991)), and I was told that in 9.04 will work, but no luck. Though in normal boot, the keyboard can connect normally, after a suspension (most normal in a HTPC), keyboard is dead, and only works re-plugging the USB dongle.

I only hate that this laptop (my company one) has to have compulsory Windows ;-)

Best regards,
^_Pepe_^

---

### Post by warped0ne on 2009-04-24
I've upgraded 1 laptop from the RC (ext3), performed a fresh install on an EeePC 901 (ext4), and 1 virtualbox installation (ext4).  All were seamless and all finished with no hitches.  In fact, the EeePC rebooted so fast that I didn't have time to pull out the SD card and had to restart again.

---

### Post by Scarletgecko on 2009-04-24
Upgrading from 8.10 to 9.04.  Upgrade will not start.  Update manager loads 2 of 2, upgrade window appears, press upgrade button, nothing happens.

Any suggestions?

-p

---

### Post by frodon on 2009-04-24
Wait a week that ubuntu servers are less loaded. The first week after the release is always full of "server not responding" kind of errors with update-manager.
If you can't wait download the CD via bittorrent and update with the CD.
Too much people love ubuntu :)

---

### Post by Lunx on 2009-04-24
Installed from liveCD, changed over to ext4 and everything worked flawlessly. Can certainly notice differences compared with my old 8.10 installation, sound has improved (more volume than previously) and screen resolution seems better (subpixel rendering works better now and fonts look a lot clearer and sharper). Very happy with it so far.

---

### Post by Lisimelis on 2009-04-24
Updated yesterday and everything worked fine. Still no compiz though :(

damn the s3 chip!

9.04 seems faster and lighter. Nothing troubling to report and i hope it stays that way!

---

### Post by fprintf on 2009-04-24
First time ever that update manager has worked flawlessly (5th upgrade) as it usually mucks something up and I need to reinstall from an alternate install CD. This is on an older IBM T-30 laptop with 1GB RAM. That is the good news.

The bad news is that Conky has disappeared behind my desktop background and can only be enabled by calling it from a command line. More importantly, my flawlessly working Sleep, which I messed with various config files to get working (and have no idea how to replicate or restore) is now not working. 

p.s. Congrats to the developers on a relatively smooth upgrade. The boot speed is fast enough I might not even need sleep mode.

---

### Post by john stiles on 2009-04-24
Don't upgrade to jaunty, reinstall. Faster and easier!

eeepc 1000 upgrade did not install the new kernel, but started and ran but very slowly.

So I downloaded the unr .img file and imagewriter tool and made up a bootable key. Installed flawlessly and kept home drive settings and installs. Fantastic, thankyou to the people and teams involved.

---

### Post by dawynn on 2009-04-24
I've upgraded a couple computers to Jaunty now.  Upgrade Manager was not perfect, had to use aptitude.  But once all updates applied, both computers worked as before.  (Note: One was Ubuntu, the other was Crunchbang)  Because of the age of the computers, I delete all bluetooth and compiz.  So, not affected by any compiz issues.

On the good side, my nVidia card works just fine.  No issues there.  Much better than 8.10.

---

### Post by HAL5000 on 2009-04-24
The upgrade went flawlessly, but due to driver limitations i  whish I hadn't. 

Using an ATI X1650 only the open source driver which is too limited for me.

Looking for a painless downgrade...

---

### Post by kufio on 2009-04-24
After installing 9.04 I cannot boot into kernel 2.6.28-11 the system just freezes before loading, have to use 2.6.27 instead.

---

### Post by Sef on 2009-04-24
Install 64-bit ubuntu was flawless.  Also used ext4, which is proving to be much faster than ext3.

---

### Post by PGHammer on 2009-04-24
I installed Kubuntu Jaunty 64 via Wubi (Vista Ultimate 64-bit host), replacing my Kubuntu Jaunty 64-bit RC (I used the driveless Wubi method, detailed in the "Faster Way to Wubi" thread).  My HD3450 (256MB PCIe) works best using the FGLRX drivers, and my X-Fi XtremeGamer works using the Creative Linux drivers.  Utterly pain-free.[http://www.mozilla.org/projects/firefox/3.0.9/firstrun/](http://www.mozilla.org/projects/firefox/3.0.9/firstrun/)

---

### Post by autra on 2009-04-24
I have a X1600 ATI card.
So the main problem is that I cannot use the fglrx driver for upgrading. I therefore installed the open source one, which turns out to be 2x faster that fglrx for glxgears. At the beginning, direct rendering was not activated. Then after restarting my laptop, it turns out to be activated and the result I have now for glxgears is 10x time faster than with fglrx !!
However, compiz is really really slow... Well, not everything : the cube is perfect, but everything else is very slow, and it was working very well with 8.10...

Apart of this compiz issue (which I don't mind honestly), everything is better than perfect.

---

### Post by Staesys on 2009-04-24
After waiting a long time for the network upgrade to work, I downloaded the alternate ISO and upgraded from that. On reboot was informed my X server config file was corrupted. Set it for default and restarted. On reboot and login I had a 800x600 screen. After enabling restricted (proprietary) sources I was able to install the nvidia 180 driver and reboot. After reboot I was able to set the display to 1280x800 like normal. WIFI strength seems to be a little lower than in 8.10 and the light is still orange all the time (HP Pavilion dv6000 laptop). Also the internal mic's still don't work, although the external mic jack does.

---

### Post by meho_r on 2009-04-24
Install, Jaunty 64bit. Worked like a charm. I couldn't help myself, installed ext4 which is, as it seems, almost twice as fast as ext3. Everything is faster, not only boot time. Congrats, devs, this is probably the best Ubuntu edition yet :D

---

### Post by rooster78383 on 2009-04-24
Surprisingly easy process. Had to go from 8.04 to 8.10 to 9.04, and I took the typical desktop user route of Update manager. No immediate issues identified after nearly 24 hours except:

* Had to adjust Flash player in Firefox to get sound to work from within the browser. Sound worked fine otherwise.

* Desktop effects no longer work. Will tackle that later. I've seen posts flagging that one.

I have four machines running Ubuntu - three desktops and a laptop. I'll try a clean install on one of the desktops and upgrades for the others.

So far very good!

---

### Post by BB88 on 2009-04-24
**Did it work flawlessly?** Everything except troublesome RTL8187 driver.
**Did you get problems?** Only RTL8187 Wireless Driver.
**Did you manage to solve them?** Yes.
**If yes, how?** I installed Ndiswrapper and installed the WIN98 drivers from my motherboards website. I then disabled NetworkManager Applet and connected manually via the terminal. I then added the connection commands to /etc/rc.local. This resolved the low connection signal and dropping under heavy packet usage.

I really like the new Boot Screen and Login Screen, great work on the new release!

---

### Post by dougalkerr on 2009-04-24
Have now installed Jaunty completely on my new Dell laptop. No Windows dual boot, fingers crossed for future computing.
Still can't run dvds though even after installing the ubuntu-restricted-extras vlc

So more head scratchin and searchin till I find something that will play my DVDs.

---

### Post by LoganS on 2009-04-24
Upgraded from 8.10 by way of package manager. Did update then upgrade. Once or twice had to reboot during download.  Can not get 9.04 to run.  Had to get online using my installation DVD for 8.10.  I suspect the problem is corruption in GRUB files but am not sure.  Have tried to reload GRUB files several times after hitting escape button and being presented with menu.

Thanks

---

### Post by Therion on 2009-04-24
> **dougalkerr said:**
> So more head scratchin and searchin till I find something that will play my DVDs.
Install **libdvdcss2** from Synaptic if you're referring to factory/encrypted DVD's.

---

### Post by iliev on 2009-04-24
I just installed it on Asus U6V (Bamboo). All installed, but at first try things did not work properly, I could not even start X. I restarted in safe mode and asked it to repair itself. After that most things worked fine, except for the sound, which required some further tuning, as explained at:

 [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by sammiam on 2009-04-24
:confused:  I allowed my system to perform the upgrade automatically, there was a brief popup of something that failed, but the system continued.. I checked back at 3am and the upgrade was stuck at the stopping of the powernowd daemon.  LUCKILY I had dd'd my root fs and was able to restore back.  looks like Jaunty Jackalope upgrade has a ways to go...

My system:  HP Pavilion dv7-1267c Entertainment Notebook
            2.20 GHz AMD Turion X2 RM-74 Dual-core Mobile
            4GB memory
            ATI Radeon HD 3200 Graphics RS780M
            Atheros AR928X wireless network adapter (pci-exporess)

---

### Post by Almighty on 2009-04-24
I love the progress Canonical is making. The install is as smooth as silk. 

I believe it took me less than 20 minutes to install.

---

### Post by glynn on 2009-04-24
Did a clean install with 8.10 on a stock standard Toshiba Satellite A50 - After it completed, the update manager offered 9.04 (I hadn't realised that it was ready) and I allowed this - it took quite a long time to download - speeds did vary from normal to extremely sloooow.  However, there was only one noticeable issue after the upgrade was finished and this was with the video display - it occasionally showed a garbled screen, but refreshed itself and has displayed properly since the computer rebooted.  The wireless connection was much easier and better than with 8.04 and 8.10.  The whole process was very smooth.  At the moment, I would say that this is the easiest version of Ububtu I have used.  Keep in mind that I have only just finished installing this OS this evening.

---

### Post by Scarletgecko on 2009-04-24
> **frodon said:**
> Wait a week that ubuntu servers are less loaded. The first week after the release is always full of "server not responding" kind of errors with update-manager.
If you can't wait download the CD via bittorrent and update with the CD.
Too much people love ubuntu :)

How do I force the upgrade with the CD rather than the clean install?

---

### Post by kellner on 2009-04-24
This is the first upgrade that worked flawlessly. Great! 

I did the upgrade on a PC with two screens, both of which were correctly detected, and it's become really easy to configure such a setup without manually editing xorg.conf.

---

### Post by frodon on 2009-04-24
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

The method you are looking for is upgrading through the alternate CD.

---

### Post by amudman on 2009-04-24
I'm not a whiz on the terminal.But the real sign of good computer program for me is when I can bumble along on an install and at the end it works. Remember that: the sign of greatness is when pumpkins like me get it working!

Here is what I did. I started an internet update--- very slow. I started a torrent download---- very fast (<1.5 hr) but I guess I didn't get the right file to update (???) as it wanted to install and I didn't want to loose my old data so I stayed with the internet. Went to bed. Checked progress during night and (darn it) the install had stopped while it awaited my response to some question. (hint, don't ask me-- I don't have a clue what I am really doing-- I just want to upgrade). In the morning all worked well except my virtualbox which I had just got working ( and am super pleased with how well MediaMonkey works on the guest winxp on a t23 laptop). Using all the skills at my disposal, I did a re-install of VirtualBox and MediaMonkey is now playing some great music as I hope I help others.

 It just works and it works in spite of my lack of knowledge. I just installed the 9.04 update. I have not fully explored the update to see how things worked, but so far great.

 You, who have knowledge and experience, remember folks like me when you write those great tutorals, step by step instructions, and how to's. I am amazed how well some of them help me get my projects working.

Thank All of you who sure have my respect,admiration and envy at you skills.

---

### Post by scyntl on 2009-04-24
install --> upgrade

For various reasons I deleted my ext3 partition and tried a fresh install from the studio CD, twice. Both times my laptop hung after a few minutes in the new environment, couldn't run update etc. So I reinstalled the old 8.10 and updated/upgraded from update manager from there.  So far clear sailing!

---

### Post by Flyingjester on 2009-04-24
upgraded to 9.04 works flawlessly, didn't even have to fumble around getting my wireless to work. Awesomeness in a can.

---

### Post by bartoi on 2009-04-24
just upgraded through update manager from intrepid.  install went smooth, reboot then showed up a graphical problem (looks like an old zx spectrum crash) looking out my intrepid disk and will stick with that for the moment, at the moment i cant even log into my box because of this issue

---

### Post by nixie21 on 2009-04-24
Upgraded through upgrade manager, everything went fine...I just needed to re-install flash..

---

### Post by the_monster on 2009-04-24
Finally finished the upgrade about 1 hour ago.

Everything went smoothly. Except I had to replace the default libsane-pixma.so file with the custom one that works with my Canon MX700.

I am gonna get some sleep now and then do some more testing later. 9.04 is very fast.
:P

---

### Post by ckoz on 2009-04-24
Seem to be having the same issue others are having where update manager can't seem to find the update. Already checked Software Sources->Updates->Release Upgrade: Normal Releases, but still no luck

Also tried alt+f3 "update-manager -d" no go...
:confused:

Currently 8.10, Kernel 2.6.27-11

---

### Post by Raptor Ramjet on 2009-04-24
Once again the upgrade killed my xserver which now won't start due to problems with the Nvidia driver.  Sadly I'm too bored with the whole thing to even try fixing it today.

Even when Xorg does work it *still* doesn't drive my monitor at the correct resolution which it has failed to do since "automagic" detection was added (it all worked perfectly under Dapper when I could force it to use a particular resolution in xorg.conf).  And when I do raise a bug all I'm ever told is "it'll be fixed in the next version".  Pah.

All in all it's been another disappointing Linux experience for me.

---

### Post by bryan.m.obrien on 2009-04-24
I performed the dist-upgrade method from 8.10 -> 9.04.
Immediately hit the problem where /dev/pts wasn't mounted at bootup.

Now, I can't sign on to gdm...popping over to a virtual terminal (ctrl+alt+f1) and signing on - shows that I don't have permissions to /dev/null.  

chmod /dev/null 0666 gets me by this....but at the next reboot, same thing.

Edited /etc/rc.local and added
chmod 0666 /dev/null
(before exit 0)
..
reboot
..
still no love...still /dev/null has 0600 perms.

None of these are showstoppers and I believe most of them are due to the fact that I was using insserv.

I'd still like to know why /etc/rc.local isn't being read at bootup.

Am also seeing /etc/init.d/rc: 390: /etc/rc2.d/S20skeleton: Permission denied

---

### Post by sanderella on 2009-04-24
Upgraded easily. Only one problem, B43 fwcutter didn't install properly, but I am fed up with this pesky wireless card anyway, and don't intend to do anything about it, works nicely on wired. :)

---

### Post by kopus on 2009-04-24
New install.

Two major problems and one small bug.

Problems
Compiz is slow when Resizing/restoring/maximising/opening windows. I'm using the fglrx proprietary driver with a Sony Vaio FW (ATI Radeon HD 3400 Series).
The brightness control (FN+F5/F6) does not work (kernel patch missing maybe). 

When shutting down ubuntu it hangs, after the hole process of shutting down is done (I think). When it should go off it sticks to the blank screen.

Going back to 8.10 until the compiz/ati problem is fixed.

---

### Post by Luther11 on 2009-04-24
> **hagantic42 said:**
> Ok, so, I cannot upgrade. The internet is working, I'm posting from the pc  but as of right now I cannot get the update manager to upgrade. It just freezes. I attempted sudo apt-get update then sudo apt-get upgrade and neither of these seemed to work PLEASE HELP! It could be that the servers are clogged but it should not be causing the entire update manager to to crash and make me force quit it.

Same problem I had. Here's what I did. I'm writing from memory, so some button names may be off.

1. Download the alternate CD by torrent.
2. Either mount the iso file (Sorry, I don't know the command.) or burn it to a CD and re-insert the disc.
3. When the box comes up, click Run Upgrade.
4. It will ask if you want to go online for the latest updates. Click No. If you say Yes, it will crash and you'll have to reboot before trying again.
5. It will warn that it will remove some packages. I don't know why, probably because of version conflicts. Just go ahead with the upgrade.
6. After installing, it will ask if you want to remove some obsolete packages. I think it's safe to say yes, since you'll probably just have to update them again when you reinstall your software.
7. After the upgrade is done, you can finish it by using Update Manager.

HTH

---

### Post by yellabelly on 2009-04-24
Upgrade went well with no problems reported on both 64 bit desktop and a 32 bit Dell laptop.
The only issue I have found is with my vpn on both machines.
The connection through the network manager (vpnc) is successful but then I can no longer resolve internet name lookups, Skype disconnects. Internal lookups are fine.

UPDATE
Fixed by the tick box in vpn ipv4 routes section "Use this connection only for resources on its network"

---

### Post by Evil Dax on 2009-04-24
Did a clean new x64 install (with ext4) on my Acer Aspire notebook.
All works smoothly, booting from grub to login only 27seconds.

Only thing that does not work out-of-the box (and still) is the Intel WiFi link 5100 wireless card. :-(   

Seems to be some trouble with the iwlagn, not wanting to accept security...

At this moment my filserver is upgrading from Intrepid

Jaunty is working very smoothly!
:popcorn:

---

### Post by Johnr123 on 2009-04-24
The upgrade worked flawlessly, though very slow to download but that's my fault for doing it on the first day.

All my tweaks and settings were preserved. Totally impressed with Ubuntu to date. This is my first upgrade -- but not my last :-)

---

### Post by Johnr123 on 2009-04-24
> **kshane said:**
> I use the ATI X-1650Pro, for which there is no driver at this time.  I upgraded using the upgrade manager.  My system boots but slows to a crawl and I am unable to use my mouse (can't click on anything).  Have to hit "reset"...

Again, PO'd at ATI for their slowness in releasing new drivers.

Kevin


Kevin,

I also have an ATI x1650 Pro (mine is AGP by the way), and I have found the default driver that Ubuntu assigns to the card works well. I have had poor experience using the proprietary driver that comes up in the "Hardware Driver" tool search. Thought I'd mention that in case you haven't tried using the default driver that Ubuntu uses for that card.

Best of luck,
John

---

### Post by ArgusVision on 2009-04-24
Overall a great install. One big caveat... Video.

Installed on Acer Aspire 4520

[COLOR="Lime"]Wireless[/COLOR] - (Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)) Works right out of the box with the ath5k driver.

My CDMA phone even works as a modem with no config needed.:)

[COLOR="Lime"]Sound[/COLOR] - flawless 

[COLOR="Red"]Video[/COLOR] - (Nvidia GeForce 7000m) So far, it's a bump in the road. Right now I'm stuck at 800x600.
In 8.04 (Hardy) I was able to get EnvyNG from the universe repo, install and configure, then everything worked. For some reason I cannot find EnvyNG in the universe repo for Jaunty. (Another user told me they found it just fine)
I've checked my /etc/apt/sources.list, and reloaded Synaptic, but no luck.

[COLOR="Lime"]Applications[/COLOR] - So far, so good. Haven't loaded all the codecs yet, but all of the "out of the box" apps work great.

Unfortunately, I've not been able to experience ext4, since I installed using wubi.(Have to use "that other OS" for work") It appears to only have an ext3 option right now. Hopefully, that Ha be updated so I can see if it affects the boot speed for me as much as it has been reported.

Overall, very pleased. Will be more pleased when I get a better resolution.
------------------------------------------------------------------------------------------------------------------------
Update: Just rebooted a little while ago, and apparently Jockey ("Hardware Drivers") Just updated and included the Nvidia 173.##.## Driver I needed. Now screen res is perfect, and I'm one happy camper.

---

### Post by ivan-frankfurt on 2009-04-24
Upgrade from Kubuntu 8.04

Relatively smooth, but two problems I am still working to solve:

1) the nvidia driver
it just wont' work. The error in Xorg.0.log is not very clear
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
However, if I start a console and then type startx, then the real problem is shown:
the nvidia driver is version 180, but the nvidia kernel module is version 168.
I had always installed from restricted-drivers, not directly from the nvidia website, so not sure what the problem is.
nvidia-kernel-common and nvidia-glx-180 are already the latest version according to apt-get
Right now I am using the vesa driver, so no 2nd monitor.

2) No menu bar in KDE. I have to start all apps from a console for now.

Aside from this, some minor errors on packages such as irda-utils.

I think next time I'll go for a clean install

----
EDIT:
After a few hours I realized that the update was hopeless. 
I did a clean install, it worked with no problems. I am glad I had separate partitions.
A colleague of mine did a 8.10 -> 9.04 install on comparable hardware and had no problems.

---

### Post by AndreiMe on 2009-04-24
i also upgraded it, as i always do. but for the first time since 7.04 this didn't work. i grew confident that nothing bad will happen and it did. very bad. couldn't get nvidia drivers to work, the headers were all messed up, and after a reboot when i didn't do anything the display didn't even bother to start. i tried until 4 hours ago to get my info and projects back. and i almost gave up until i took an older xorg.conf and merged some data from there in the new one. i managed just to copy my files on a windows partition. for me, this sucked very bad. i don't care what people are going to say about backup if you want to give people the chance to upgrade rather that clean install at least make it work. and for what i see it didn't work, not just for me but for many people. now 9.04 isn't all that fancy. i still can't get most of my programs installed. yesterday i was very close to give it a rest for a few months but just managed. hopefully it will start improving for i don't know how long i can spend a day or two just trying to get back my projects and files and so on.

---

### Post by domus-dei on 2009-04-24
Hi all,

almost everything went flawlessly. I had issues with 8.10 and two monitors. I played around with the gnome as well as the nvidea settings to no avail. I gave up and waited for 9.04 \\:D/
I tried the live-CD with a connected old Sony (Multiscan 300sf, 19" at Dell Latitude D830). Everything fine. I did an dist-upgrade, rebooted and played around with the settings again. There wasn't a second screen at all.
Workaround: I booted the live-CD again and copied the whole /etc/X11 to my upgraded system's /etc (after a backup of course). I restarted X and problem solved!

Even vmware runs after a simple vmware-config.pl!

I like it, thx alot!

dd

---

### Post by myfriendzebbie on 2009-04-24
Compaq F500 laptop - AMD Sempron nVidia video.

Did the upgrade from 8.10 with studio package installed.  it was slow going...i let it download overnight.  A few minor issues - conky, compiz need to be reconfigured.  When the update finished it actually flashed me an error that said something to the effect that the update failed.  Appeared to be a video issue.  After closing that screen it gave me another that said update was finished.  

Wireless, video, sound all working perfectly.  Still early but haven't found any major issues.  Which is nice because the upgrade from 8.04 to 8.10 went badly.

Very happy this time around.

---

### Post by TheLocust830 on 2009-04-24
Upgrade thru packet manager went flawlessly (although download was very slow for obvious reasons, the rest just tore thru in about a half hour) on my amd64 desktop.
All my settings and files remained intact, the sound is definitely improved over 8.10, where it always seemed too quiet, and it seems like the video in sites like hulu and youtube improved also. 
I have yet to mess with a lot of things, but everything I tried has worked so far, and quicker, especially boot time.

Great Job! =D>

---

### Post by transformation on 2009-04-24
Hi, i just tried to upgrade from intrepid to 9.04 but ran into a major problem. This is the error I get:


[I]Boot from (hd0,0) ext 3 565fef....(a whole bunch of numbers)
Starting up ...
Loading please wait...
Gave up waiting for root device .Common problems:
   - boot args(cat /proc/cmdline)
	-check root delay= (did the system wait long enough?)
	-check root= (did the system wait for the right device?)
   - missing modules (cat /proc/modules; ls/dev)
ALEART! /dev/disk/by-uuid/565fef...(a whole bunch of numbers) 	does not exist.Dropping to a shell!

Busybox v1.10.2 (ubuntu 1:..)....
Enter 'help' for a list of commands..

(initramfs)_[/I]


Please help..Thanks in advance

---

### Post by willPower on 2009-04-24
This new release looks great guys, keep up the good work!

As far as the actual upgrade, I have xubuntu running on 3 machines in my house. One plays a dedicated server role on an eMachines T3104 (i386 version), I have it on my Lenovo U110 laptop w/ x3100 rev 3 graphics (also running i386), and my AMD64 desktop system with nVidia 8800GTS. On all machines I used the alternate install CD which I downloaded early yesterday before the rush.

It installed flawlessly on my desktop system.

My laptop had a problem with a package during the initial upgrade (can't remember which one, but it seemed too irrelevant to cause the upgrade to fail), causing an error and subsequent failure, but it came back online following a reboot. Running the update manager once again brought up an option to run a partial upgrade; this did not fix the problem, so I ran sudo apt-get dist-upgrade from the command line and it resolved the issue.

The "dedicated server" in my living room had a fatal problem which I was also able to resolve. For some reason initrd was trying to do an NFS boot, so it was failing when attempting to load the root filesystem. I had to change the BOOT=nfs option in /etc/initramfs-tools/initramfs.conf to BOOT=local, comment out the BOOT=nfs line in /etc/initramfs-tools/modules, and finally run sudo update-initramfs -u. The server came back online with no problems after that. Hopefully this wasn't something that the Ubuntu installation disc organizer(s) accidentally left in place! :eek:

---

### Post by leamanc on 2009-04-24
Hello,

I have a Dell Inspiron 1720 with an Nvidia graphics card.  (Sorry, I'm at work and can't recall exactly what it is.  I know it has 256 MB of VRAM.)  Everything has worked flawlessly since 7.10.  dist-upgrade to 8.04 on release day was flawless.  I dist-upgraded 8.04 to 8.10 about a week before official release.  Again, flawless.

About a month ago, I decided to dist-upgrade to the latest nightly of 9.04.  It seemed to go OK, but after re-booting I could not launch an X session.  It would boot straight to a command prompt.  I tried a few things with xorg.conf, doing startx manually, etc.  No love.  Fortunately, the wl drivers still worked, and I backed up my 45 gigs of data over 802.11n over the network (an overnight process for sure!).  I then re-installed 8.10 from scratch and brought my data back over.

I really want to get 9.04, but would like to avoid another clean install if I can.  Anybody got similar hardware with some advice?

Cheers and TIA,
Leaman

---

### Post by jamessnell on 2009-04-24
That poll is missing an option for what happened to me. "Mostly worked flawlessly, but one major problem".

After upgrading from 8.10, my machine rebooted and everything looked normal until gdm got going - then I couldn't interact with my machine and the screen had weird stuff on it (one time very little, another time a vague sense of boxes/windows).. 

I logged in through ssh and decided the issue was probably that I was using ATI drivers and that perhaps I needed to re-run the installer for the drivers.

I found that the ATI 9.2 driver wouldn't immediately install for 9.10, so I checked to see if there was a newer version, there was.

[You can get it here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-4-x86.x86_64.run")

I just downloaded that newer driver, set the file as executable and ran the installer. It appeared to install properly. I rebooted and everything was working just as I'd expect!

My video card is an ATI Radeon HD 2600 (Mac Pro).. So it would have been nice if the upgrade utility had caught that issue, but hey, there's something for 9.10 to do.

---

### Post by LowSky on 2009-04-24
worked like a gem,

but then again I've been using 9.04 for months now

---

### Post by jamessnell on 2009-04-24
@leamanc: Sounds like you need to deal with your video driver. There are many ways of approaching that..

One thing is to identify what video driver is being used in your xorg.conf file. If it says "nvidia" then you're using a propritary driver and you should go download and run the latest one ([here]("http://www.nvidia.com/Download/index.aspx?lang=en-us")). If you're still not sure what card you have, use the command "lspci" or "lspci -v" to figure that out.

If your xorg.conf says a different driver, such as "nv", "vesa" or something, then I guess you can try to re-run the video config tool bundled in Ubuntu. For that, try running the command "dpkg-reconfigure xorg".

Hope that helps somewhat.. I suppose it could be something else, but my issue was solved by the ATI equivalant of downloading a new driver and running the installer.

Note that you may have to set the executable flag on the driver you download, just remember you do that by running "chmod +x <filename>". Then you can run the installer by invoking by running "./<filename>".

---

### Post by nealaustin on 2009-04-24
Yes I had just upgraded to Nvidia 8.10 a couple of days ago  and it automatically upgraded to Nvidia 8.44 with the Jackalope upgrade. After fixing my Flash problem (posted) everything seems to be working flawlessly. THE JACKALOPE ROCKS !

---

### Post by se user on 2009-04-24
just insalled 9.04 works great and the volume keys on my M$ keyboard work now thanks ubuntu dev's:popcorn:

---

### Post by RazVayne on 2009-04-24
This thing is one the "juice",it has to be.Installed perfectly in 10 minutes and shaved 10s on by boot time...on a 5 years old computer with the specs of a modern netbook.
Make love to me Jaunty,please!

---

### Post by teamkiller87 on 2009-04-24
Like it's been discussed before, apparently the magical "Ctrl+Alt+Backspace" combination is gone, which makes me weep uncontrollably. Anyone know what file I need to edit to fix it? 

Cheers

---

### Post by jamessnell on 2009-04-24
Ohh, I've also run in to the flash issue that it seems many people are having. I found this post here that seemed to really nicely explain a few good options: [here]("http://blog.ibeentoubuntu.com/2009/04/upgrade-to-ubuntu-904-jaunty-and-flash.html")..

Though I found I couldn't precisely follow what they suggested.. I completely removed the nonfree package, then I had it reinstall the "flashplugin-installer" package.. That resolved my flash issue just fine (or so it seems for now).

---

### Post by x-na on 2009-04-24
> **x-na said:**
> 
Edit 2: After leaving update-manager to run over night, it finally had retrieved release notes. Downloading packages about 100 KB/sec.

Edit 3: Server upgrade went without problems yesterday.

All-in-all took about 3 hours to get all the packages for my desktop comp. Nothing has been broken, tho.

On the server side, cacti-spine doesn't work for some reason.

---

### Post by tylerjoh on 2009-04-24
fsck was unable to bring up mdadm/raid1 partitions after the upgrade reboot and dropped me into single user :(

I was able to fix by hand, but this is kind of unsettling.

This thread [http://ubuntuforums.org/showthread.php?t=1134706](http://ubuntuforums.org/showthread.php?t=1134706) has a decent discussion of issue

---

### Post by jamessnell on 2009-04-24
@teamkiller87: That's freaky that ctrl+alt+backspace is gone, do you suppose it could have just been remapped to something else? Cause yeah, I still find that comes very much in handy at regular intervals.. Damn..

---

### Post by teamkiller87 on 2009-04-24
> **jamessnell said:**
> @teamkiller87: That's freaky that ctrl+alt+backspace is gone, do you suppose it could have just been remapped to something else? Cause yeah, I still find that comes very much in handy at regular intervals.. Damn..

After looking into it a little deeper indeed it has been remapped. The new combination is a grotesquely counterintuitive RightAlt+PrtScr+k. I haven't found a way to change it back just yet but I'll die trying!!

LE:

Looks like I didn't die trying cause I found the fix. :D
[http://kubuntuforums.net/forums/index.php?topic=3100383.0](http://kubuntuforums.net/forums/index.php?topic=3100383.0)

---

### Post by blueyelabs on 2009-04-24
The Install worked perfectly through update manager from Intrepid. Several issues arose having now rebooted, however:
1) I received a message telling me that frequency scaling is unsupported on my processors. This is silly because it worked first time in Intrepid.
2) My compiz settings seem to have been disappeared and now I'm going to have to reset them.
3) My dictionary has been reset to en_US from real English (en_GB) which is just a pain.
4) I haven't found any more problems, and I hope I don't. I can, with confidence, say that insofar as much as I have used Jaunty, Intrepid has been my favourite Ubuntu ever.

If I have to re-set all the compiz and dictionary settings on all seven or so users I shall be most displeased.

---

### Post by merlinof2 on 2009-04-24
No Joy.  Burned Alternate CD with Verify.  Seemed to work well.  First machine Sony Viao VGN-TX650P which is running 8.10  flawlessly.  Tried upgrade with CD, started then received pop up stating "Error Authenticating some packages"  and lists ClamAV, Cups, Evolution, multiple Gnome entries, and multiple others.  Ends at that point.
Tried up grading with Update Manager as it said new distro available,  starts, progresses for a while, then exactly same error and result.  :confused:
Any help?

---

### Post by Mars73 on 2009-04-24
I voted for update, but I meant install (was bit too quick).
I've been using Ubuntu since 6.06 and with every new version I've installed it fresh and it never failed me.
With <7.10 my belkin usb network adapter didn't work out of the box but with some tweaking got it working everytime.
From >8.04 it is working out of the box and also with this release.
Mounted my home partition in fstab and everything was fine, I really recommend making a separate home part as it so easy to do a new install and mount it. Getting thunderbird up and running was never this easy.
Right now I'm compiling ffmpeg, x264, xvid, avidemux etc and no problems yet.
Not getting into ext4 yet, but as soon as the issues are ironed out, ext4 it will be.
Excellent release, thanks guys!

(X64 installation from USB stick)

---

### Post by boulderwalker on 2009-04-24
The upgrade to jaunty went well. The only minor problem is Computer Janitor hangs at "post-cleanup."

---

### Post by AlphaMack on 2009-04-24
> **teamkiller87 said:**
> Like it's been discussed before, apparently the magical "Ctrl+Alt+Backspace" combination is gone, which makes me weep uncontrollably. Anyone know what file I need to edit to fix it? 

Cheers

Install dontzap then run

```

sudo dontzap --disable

```

---

### Post by jalder on 2009-04-24
I'll add my two cents too. I love Ubuntu, but every time I do an upgrade something seems to go wrong with my software raid (mdadm). Here is a list of the things I ran into upgrading from 8.10 to 9.04.

Raid:
One of my raid devices didn't mount at boot, so the first reboot after the upgrade dropped me to a repair shell. Not a huge deal, but its kind of discouraging after you just did an upgrade. Turns out it was a problem with the device not being in my mdadm.conf. Apparently it didn't need to be in 8.10. For more info see my post:

[http://ubuntuforums.org/showthread.php?p=7135383&posted=1#post7135383]("http://ubuntuforums.org/showthread.php?p=7135383&posted=1#post7135383")

This was fixable, but I would consider it a more major problem. I was in limbo for a while trying to figure out if ~700 Gb of data just got nuked.

Video Drivers:
I have an Nvidia card that was working without problem in 8.10 with the drivers from the Ubuntu repo (ie not Nvidia binary drivers). After upgrading my video bombed. After clicking a lot of dialogs telling me GDM was failing, it would eventually load X in low res mode. I ended up switching the the new Nouveau Nvidia drivers and making a new xorg.conf. Everything is fine now.

The Pidgin popups were annoying, but easily fixed

I also had a common problem with the Tracker failing every other minute saying the index was corrupt:

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560")

All in all its been a bit bumpy. Each time I upgrade I have some issues (especially with software raid), but this time around it seemed a little worse than the upgrade to 8.10. I would consider myself an average to advanced user, so I can deal with these issues. But if Ubuntu is going to be the 'easy to use linux' or a Windows replacement I would think a beginner or novice would be discouraged by these hurdles.

I still think Ubuntu is the best distro around, but I need to put on my thinking cap every 6 months when a release comes out and get ready to deal with some problems. I suppose that is the price of being an early adopter.

---

### Post by ben2talk on 2009-04-24
After downloading around 375 packages my internet cut - and ubuntu offered to continue, and after installing a lot of jaunty software it said a reboot was required.

I reboot to get the kernel options - selecting the older of the two available kernels I can get to a recovery console, but the keyboard is not working at this point (both the original and a spare usb keyboard work at the boot screen, and won't select 'repair' options at the screen, and I cannot hit 'enter' to try to continue booting. Mouse is also dead.

I am also unable to connect to internet until AFTER I get to a desktop and sign in using a browser.

Any ideas?

---

### Post by Ceratog on 2009-04-24
Just recently updated from 8.10 to 9.04 on a 64bit laptop with nvidia graphics. I used the update manager. I'm getting a ridiculous amount of segmentation faults and X11 scrambling/crashes. 

I've used/administered Linux since '98 and have never had this much trouble with an upgrade. It's going to be a long day........

---

### Post by whoey on 2009-04-24
Upgrade from hardy 8.10

**Flash** broken, went into synaptic, removed all the flash entries, added only the adobe one as per a forum thread on the topic, reboot, flash works.

**Filezilla** got uninstalled during the upgrade by the wizard. Add/remove kicks up an error about the program only working for i386 or smth... synaptic reinstalled it just fine.

**Amarok** lastfm scrobble broken, seems to be a known issue with the plugin, not the actual software. Had to manually rebuild my library.

**Firefox** crashes/greyscreens ALOT especially when switching tabs/ or to other running tasks.

Seems like my system more or less works ok. I think it's actually a bit more sluggish/less responsive than it was with 8.10 I just upgraded this machine and it was a clean 8.10 install a few months ago. It's an Intel quad 9300 with 3gb ram, Nvidia gf9600gt. I was not unhappy with 8.10

---

### Post by tomdkat on 2009-04-24
My upgrade is still in progress.  My biggest problem is video from X.  I get the Ubuntu splash screen ok but when X starts, I get colored garbage on the screen. I've started a thread in the installation & upgrade forum on this already.

At this point, I'm at a total loss.  This has by far been the worst Ubuntu experience I have ever had.

EDIT:  Oh yeah, I started an upgrade from 8.10 (64-bit).

Peace...

---

### Post by jamessnell on 2009-04-24
@teamkiller87: Counterintuitive indeed. Useless to me too, as my keyboard doesn't have a printscreen key. What the frak?

---

### Post by Topsiho on 2009-04-24
Downloaded the Ubuntu Netbook Remix .img version, to put it on my acer aspire  one netbook. Put the .img file on a 2GB UBS-stick, using the command line method, as the other, graphical method was far to complicated for me :) , and had it checked for errors: one file was found to have errors.
Checked the md5sum of the .img file and this was correct.
So I decided to go on with installing on the netbook, which went great.

I am using the UNR Jaunty on this acer aspire one right now :), wireless.

Topsiho

---

### Post by hanzgroove on 2009-04-24
The server edition upgrade went smoothly. So far no noticeable problems.

---

### Post by cubeist on 2009-04-24
I have done three fresh installs (64 bit, ext4) on an old laptop, a semi-old laptop and a desktop.

Everything was flawless.  Very impressed and a big thanks for all the hard work! :)

---

### Post by NWAdawg on 2009-04-24
Did a fresh install on my HP zv6000 laptop. Everything went great. Had to install b43fwcutter to get wireless to work, this was no big deal. Infact this was one of the lease painful installs. Great work Ubuntu-team

---

### Post by jamessnell on 2009-04-24
> **tomdkat said:**
> My upgrade is still in progress.  My biggest problem is video from X.  I get the Ubuntu splash screen ok but when X starts, I get colored garbage on the screen. I've started a thread in the installation & upgrade forum on this already.

At this point, I'm at a total loss.  This has by far been the worst Ubuntu experience I have ever had.

EDIT:  Oh yeah, I started an upgrade from 8.10 (64-bit).

Peace...

I had video uglyness too.. Was annoying, but easily fixed in my case by downloading the latest [ATI drivers]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and installing them at the terminal.

---

### Post by Aevorn on 2009-04-24
Upgraded through Update Manager. Slow, but no problem at all ... until I rebooted an extra time and now can't find/mount my primary HDD.

---

### Post by buchan on 2009-04-24
RAID does not seem to work as the / partition.

Tried to create (in about a dozen different ways) partitions/Arrays for my root filesystem using RAID 1 and it always comes up as "degraded".

During the setup /proc/mdstat looks normal but once the system is rebooted it only shows one degraded array (I had created two during the setup)???

/etc/mdadm/mdadm.conf shows the two arrays but the partitions don't even seem to be there in the /dev dir???

I am lost, and I have been working with software RAID for years??

Any help??

---

### Post by aniruddha on 2009-04-24
Fresh install of Jaunty 64bit. Installation noticebaly smoother then Hardy or Intrepid. 

When I first boot up after install there is a slight problem with the Nvidia drivers (hardware drivers tell me "no propeitary drivers in use"). Shudders. Palms clench, cold sweat breaks out. Take deep breath, reboot. 

HALLELUJAH!!!

No worries. All drivers are go. Jaunty persuades me to take a spin with exaile (We are not amused, amarok2). Great stuff. And a perceptible performance increase when it comes to bootup/shutdown. All that is left to do is check out how Civ4 works. 

Awesome stuff.

---

### Post by ecsdrive on 2009-04-24
Upgrade from 8.10 (amd64) on a Dell D830 (intel graphics), everything went smooth but I don't have compiz :confused:
I found this [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html) but I'm holding my breath for now

---

### Post by yohshii on 2009-04-24
Upgraded through package manager (8.10 -> 9.4 64 bit) on reboot X was broken (not really surprised with my ATI card).  Downloaded the Catalyst 9.4 driver with my windows installation ( believe it was here [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English) )and installed that through root shell (selected Recovery Mode from Grub > Drop into root shell), and after a reboot everything came right up.

---

### Post by slasher3x on 2009-04-24
I decided to go towards the fresh install install route.  So far so good since changing to 9.04 with no major issues to report.

---

### Post by camokat on 2009-04-24
After the update when I connect my Lenovo T61 to external monitor and enable my monitor, the clock seems to stop updating:
[IMG]http://farm4.static.flickr.com/3401/3471668552_af6010254a_o.png[/IMG]

As you can see on the top the current time shows as 1:04, in reality it's 2:15.

Besides this small issue this is the best Ubuntu release yet! Great job!

---

### Post by sloppyc on 2009-04-24
So far, no good.  I have two machines, I'll separate my experiences:

1. AMD Athlon 2000+ machine with 512MB RAM, GeForce440MX.
Drops to Busybox shell when I try to boot from CD.  I had this problem with 8.10 on this machine as well.  I was able to upgrade the 8.04 to 8.10, but unable to boot 8.10; Busybox again.  So when the LiveCD dropped to the Busybox, I just quit.  8.04's running great anyway.

2. Pentium 4 2.66 (@2.75GHz), 1GB RAM, GeForce6200.
Attempted upgrade from 8.10.  Seemed to be working okay, but taking forever.  I started at 4PM, and it still claimed to have an hour to go at around 10 or 11PM.  This was not a big deal as I was able to watch my movies on another machine in the house while it installed... problem came when this box dropped its network connection.  No more movies for me if I can no longer connect to the machine that's storing them.
So, I cancelled. Restarted.  Ubuntu is now unbootable.  No biggie, Windows is still the primary OS for this machine (and only this machine), I'll just reformat my Ubuntu partition and install it clean, I thought.  Installation was smooth, maybe even a little nicer and faster than before.  Rebooted, liked the new login screen.  
Too bad I can't do anything once logged in.  I get a blank, white screen.  I've tried the failsafe boot to fix X Server, etc.  No change.
On the plus side, it did notice that I have Vista, openSUSE and Fedora installed and added them to GRUB.  The downside of that is that the order of my hard drives changes all the time for some reason (I solved this before by using UUIDs instead of /dev/sdxn in my fstab) and I think that's what's prevented me from actually being able to boot into them from Ubuntu's GRUB (it's okay though, anticipating such a situation I'd given each distribution its own /boot partition, so I can still easily get to them).

Haven't really done much troubleshooting, so I won't cast my vote just yet.:?

---

### Post by tomdkat on 2009-04-24
> **tomdkat said:**
> My upgrade is still in progress.  My biggest problem is video from X.  I get the Ubuntu splash screen ok but when X starts, I get colored garbage on the screen. I've started a thread in the installation & upgrade forum on this already.

At this point, I'm at a total loss.  This has by far been the worst Ubuntu experience I have ever had.
Well, I got my video problem resolved.  I ended up having to re-install the xserver-xorg package and then things started working for me.

Peace...

---

### Post by wildsnail on 2009-04-24
Used Update Manager to upgrade from 8.10. All seemed to go smoothly but I had no sound.

I downloaded the iso (amd64) and tried a fresh install but still no joy with my Audigy 4. I worked my way through the Sound Troubleshooting guide which is linked elsewhere in the forum but I still couldn't get any sound even though my hardware and drivers appeared to be fine.

Oh well, I'm back on 8.10 for now until I can find a proper solution.

---

### Post by or1onas on 2009-04-24
Absolute chaos.
Nothing works. Everything's broken.

No force options work.

Going for reinstallation

Worst upgrade experience in my 7+ years of Linux use

---

### Post by wsonar on 2009-04-24
Beta went good and updated before release to full version 

have not been able to update my intrepid box as servers have been to full

---

### Post by tomhorsley on 2009-04-24
I installed i386 from the text mode alternate CD. All went well, I logged into the GUI, was on my way down the menus to launch synaptic when, boom! My screen went blank and monitor went into power saver mode. Nothing would get the screen to come back on. I couldn't Ctrl-Alt-F2 into a vterm or anything.

Fortunately, I want to run this thing without the GUI anyway, so I booted another OS, mounted the filesystem where I just installed jaunty, and removed the gdm entry from the /etc/rc2.d directory.

At that point I was able to boot into text mode fine, and everything seems to work. Pointed DISPLAY to another system, and ran synaptic over there to get the ssh server installed, once I had that, didn't need to use the local console at all.

There is an ATI card of some kind in this system, not sure exact model. I think I've seen some folks report similar problems with xorg radeon driver in the fedora 11 beta as well, so I definitely suspect the radeon driver.

---

### Post by tneva82 on 2009-04-24
Thanks a lot 9.04 :( Tried to update it, ended up with computer that won't boot. 8.10 installation cd still refuses to co-operate. ATM downloading 9.04 installation cd hoping the bug has been fixed so I could start the reinstallation and install it clean from there hoping against hope I won't lose files in home folder when I do that.

Crap. Should not have upgraded. Especially when working with thesis program. Delay I could have done without.

---

### Post by weisel on 2009-04-24
Everything went fine for me haven't had the first problem.

---

### Post by Grendel336 on 2009-04-24
I am getting a message that the download and install process will take 4 days and 18 hours. :confused:  Say What?????

Is this just a glitch, or could that be real?

---

### Post by knuckx on 2009-04-24
Updated via Update-Manager. Seems to have worked but I was told it had failed due to "b43-fwcutter" not being upgraded. Missed clean-up stage and rebooted. Reinstalled the b43 wifi card driver, and set compiz back up. Works fine.

EDIT: Upon shutdown major graphical corruption appears on display. Video card is ATI Radeon Xpress 200M, Dell branded. Works fine otherwise.

---

### Post by Wandering Wombat on 2009-04-24
All in all pretty flawless upgrade from Intrepid, took a while to do the net updates though, which I guess is expected. 

Loving Jaunty so far, haven't come across any major problems just minor niggles here and there. 

Cheers :P

---

### Post by kellner on 2009-04-24
Bummer - after being so enthuiastic about the flawless upgrade on my desktop, I dared upgrading the notebook, too (Lenovo 60), foolishly: intel graphics issues seem to have broken down X completely. I found no way of fixing this, even through downgrading xorg-xserver-video-intel to 2.4.

---

### Post by trundlenut on 2009-04-24
slow to download but it was nice and smooth to update.  Only niggle was that I had the wrong kernel version as default in grub.  A quick edit to menu.lst and it's all sorted.

All in all it seems to look and perform a bit better.

---

### Post by Tilos on 2009-04-24
Grabbed the alternate ISO from the official torrent. Upgraded. Now my system reboots 10 seconds or so after the desktop is shown. 

Quickly shutting down gdm doesn't help. Recovery mode that fixes X doesn't help. Recovery mode with networking does work and doesn't reboot. The last line in syslog before rebooting is always:

[88.996107] mtrr: no MTRR for e0000000, 40000000 found

Any ideas?

---

### Post by zeldin on 2009-04-24
Upgrade from Intrepid:

After the upgrade, I didn't have any networking.  Turns out that ifup was
erroring out because it was trying to create /var/run/network/ifstate,
but the directory /var/run/network didn't exist.  /var/run is a ram disk,
so this directory needs to be created at each boot.

In the end, I had to add this line to the beginning of /etc/init.d/networking:

[ -d /var/run/network ] || mkdir /var/run/network



Weird.

---

### Post by RossendaleIT on 2009-04-24
Upgrade went splendidly, no problems other than had to tweak the Debian Lenny grub loader on my other partition. Flawless except it didn't pick Lenny up, never mind, not a problem. :)

---

### Post by nuir on 2009-04-24
I upgraded from intrepid. Worked almost perfectly, I only had a dependency problem which I solved forcing the version of the library needed. And it seems tracker is a little buggy, it crashed after the upgrade and gave me a message about my index being corrupted. Right now it's reindexing all my files again.

Besides these two issues, it has been a very clean process.

---

### Post by sygnate on 2009-04-24
I tried doing an upgrade from 8.10 to 9.04 but the server took forever to upgrade. Once it finished, it turned out that it was only a Partial Upgrade.

It was no biggie though becuase I had downloaded the iso and burned it to a disc. I cleaned out the original install and repartitioned my drives from "/", "/home" mount partitions to "/boot", "/", "/usr", "/tmp", and left the "/home" partition intact.

After install, ubuntu started up and I was on the desktop in under 30 seconds. (Windows fails to load now because of it, but at least my Jaunty is working ^_^)

---

### Post by teh603 on 2009-04-24
Worked OK on my Acer Aspire One, except for the right card reader. Still waiting on a workaround.

---

### Post by RossendaleIT on 2009-04-24
Also (forgot to mention) it worked first time with no problems with the crappy Atheros wifi card in my HP G7000. No need to mess about with madwifi etc.

---

### Post by iang1 on 2009-04-24
I was running Ubuntu 8.10 Intrepid and it told me there was an upgrade to 9.xx Jaunty something or other so I thought great! do it! The install/upgrade seemed to go fine until it came to the auto restart at which point the whole thing just froze at a blank screen with nothing visible and no disk action to indicate anything was happening.  I now have a machine that seems to be loading OK up to the point at which one would expect the desktop to show itself and at that point all I get is a blank/black screen and therefore no way to see what has happened.  I don't know if an error message may be showing or if it has just simply frozen at that point or even if the whole thing has worked perfectly.  Any ideas anyone? before I reinstall v8.10 or throw the whole thing in the bin!!

---

### Post by ram zu on 2009-04-24
I've finished the fresh install (early version 8.04).

Everything went fine.

The only thing that is wrong is after grub there is a line that does not appear in early versions

"[1.068296]ACPI: Expecting a [Reference] package element, found type 0"

Didn't change anything in BIOS so I don't see the reason for this.

---

### Post by GuiGuy on 2009-04-24
For me it's been a disaster, especially when I reflect on the 8.04 to 8.10 upgrade which went well.

The upgrade left me with a black screen and no cursor. 

A subsequent clean install borked trying to "[scan mirrors]("http://ubuntuforums.org/showthread.php?t=1136017")" - I mean, if I am installing from a CD why does the installer want to scan mirrors?

I'm going to wait and hour or so to see if there are useful suggestions on getting a clean install running. Other than that, back to 8.10, I think. 

I thank the silicon gods for Acronis True Image.

---

### Post by crispeto on 2009-04-24
I upgraded my wife's wubi jaunty beta install to the official release and it works great. Next upgraded my son's asus eee 901 and it went perfectly and lastly my asus 1000he and I couldn't be happier. Everything works great.

---

### Post by majikshoe on 2009-04-24
For me, I was looking to upgrade two PC's and have had two failures, one not so bad, but the other is almost a write off.

My laptop was running Hardy 32 bit, and was going to upgrade to Intrepid and then to Jaunty.  Intrepid upgrade went fine.  When I went to upgrade to Jaunty, I got the "Hey you are using fglrx and probably don't want to upgrade" message.  Fail, yes, but I'm running Intrepid happily and will have to wait for driver support for the X1400 mobility card I have in here.

My desktop running Intrepid 64 bit is another story.  Started the upgrade and after downloading all the packages, popup boxes began appearing saying I already had some of the packages installed.  OK, no problems, so I clicked through a good 20-odd "already installed" type messages throughout the upgrade.  Then a Grub menu appeared saying "Hey, do you want to blow away your grub.lst", which I accepted the default "No" since I had modified it previosuly.

Anyway, following the installation I got an error saying that not all packages could be installed and the upgrade had failed. It did not ask me to reboot. Synaptic shows around 60-odd "broken" packages and when trying to reinstall them, Synapse wants to uninstall a whole stack of other things - some of which look quite important.  Also, Nautilus does not start and I cannot access any of my mount points.  So I tried a restart, and now X will not come up and I have to boot into a terminal. Lucky I can get to that - no network or anything but my Windows disk is mounted at least.

So now I'm tarring up my /home and backing it up to my Windows mount before blowing away the whole lot and reinstalling from scratch.  During the fresh install I'll make sure to create a /home partition, so if this happens again I wont have to go through this messing around - just fresh install and minimal data loss.

---

### Post by bngguy on 2009-04-24
The Upgrade process went very smooth and my system has been working well,
the one thing i would like to suggest to people who have not yet upgraded is to first find the best mirror server, this could be done by :

***System --> Administration --> Software Sources*** then select ***Other*** from the ***Download from:*** menu item.

I started the process very late in the night abt 12:55AM and i had to download 1100 MB of data which took about 90 minutes on my DSL connection, then it took about 30 minutes to unpack and install the packages, clean up all the left over stuff, so it was roughly 2hrs for the entire upgrade process.

One thing i would like to know from other users who did a clean install, is if they used ext4 filesystem and do they see any speed differences.

---

### Post by IronOxide on 2009-04-24
Just upgraded from Intrepid, haven't found anything not working yet! Here's to hoping!

---

### Post by elvijs on 2009-04-24
Am I the only one to lose Evolution-Calendar functionality? I cannot add appointments and the tasks/memos section is doing funny things as well.

---

### Post by psidre.felix on 2009-04-24
> **frodon said:**
> The purpose of this thread is to share your experience installing/upgrading Jaunty Jackalope.

Did it worked flawlessly ? 
Did you got problems ? 
Did you manage to solve them ? 
if yes how ?
...
...
.

Feel free to post your experience here and think to explain how you solved the problems you got, it might help other users in your case.

Thank you for contributing :KS

I will update this (hopefully) as my upgrade process continues, I wanted to share what I've experienced while it's fresh though.
I have never upgraded a Linux distribution in my life, always kept one version or re-installed from media so, this is all very new to me. Bear with my n00bomantiks please.

System Environment before upgrade:

*OS Distribution: Xubuntu 8.10 x86 :KS (LOVE IT BTW)
*CPU:  1.8GHz AMD
*MEM:  2GiB DDR
*Disk: 80GB ; Filesystems: / , /home , /var , /tmp , swap

X Server 11.0 (1.5.2-1.12):

*NVidia Driver: 96.43.06
*Display: DELL Trinitron P1110
*GPU: GeForce4 MX 440

___________________________________________________________

1st issue: (error as displayed during upgrade)

Could not install 'netbase'

The upgrade will continue but the 'netbase' package may be in a not working state. Please consider submitting a bug report about it.

unable to install '/etc/services.dpkg-new' as '/etc/services': Operation not permitted
___________________________________________________________

I did notice that my display resolution was reset to the monitors optimal settings during the upgrade process, which was quite comforting to me, as I have had extensive difficulty with this particular graphics card, i.e. getting the proper drivers and having to manually edit my xorg.conf file several times before the x server would take the file without automatically applying it's own 'defaults'.

The terminal emulator that displays the processes running during the upgrade showed continual errors about 'missing' something to do with packages, I am about to reboot now and have a rather good feeling that my system is not going to come back up, so let's see what happens.

(I'm new to the bug reporting, so I don't know where to gather the best information for submitting an official bug report about the netbase and other issues, so any feedback on taking steps with that would be helpful and welcomed)

Wish I could remember the other issue that came up, I was unable to record the message. Maybe someone can also point me to an upgrade/update log that is kept?

Also - The initial download of the upgrade was unusually slow, ranging from 15-90kb/s for the majority of the time it took to download, which was about 5 hours. So to those who are about to upgrade, be sure you have selected the best mirror/source for your distribution especially if you are working in a time-critical environment, and/or prepare for a long ride.
______________________________________________
*update*
Ok it's worse, which is just as I expected. When I tried to reboot from the desktop, system tells me there is no session manager active. Did sudo reboot from terminal.

Was unable to escape the boot splash for quite some time, so I missed quite a few system messages. Everything I saw was [OK] - When the system finished booting, there was no session manager still, so it defaulted to fail safe, which of course there is no window manager to be found either, so it takes me to an emulator. I tried doing apt-get xfce4 which returns after a list of installed packages this line: E: Sub-process /usr/bin/dpkg returned an error code (1) . I dunno what that means but I'm not going to mess with this much more. I'm going to download a fresh 9.04 install and try that once. If I have a single issue though, I'm regressing back to 8.10 which works very well for me.

Worth a shot anyhow, thankfully I'm nowhere near a production environment! :)

---

### Post by windfix on 2009-04-24
Jaunty upgraded via Update Manager, went smoothly until reboot.  Black screen with only a mouse pointer.  My local Linux guru can not make it recognize my home partition which is on a separate NTFS partition (so I can share data with dual boot XP). It will read the NTFS partition, but will not use the /home directory as such.

---

### Post by nuras on 2009-04-24
I am trying to upgrade my 8.10 - 9.04 through update-manager and its crawling - it feels as if I am on dial up (btw I have a 2Mbps ADSL). I kicked it off last night and after ~15 hours only half of the packages are downloaded. 

I also get intermittent messages asking me to insert an iso dated 20090420. OF course I dont haev it and so i just cancel that pop up and then it goes back to crawling.

I have no idea whats happening and any help is much appreciated. Is there an iso for upgrading - I went through the web site but cant seem to find anything. 

PS : I am still a novice so apologies if I missed something obvious.

Thanks a ton in advance.

---

### Post by Dartr on 2009-04-24
Upgrade over 2Mbps line is stuck at "fetching file 509 of 1325" after over 2.5 hours from the start.

The progress bar looks to be at about 10%.

Stop and try again later?

---

### Post by waldrepdebater on 2009-04-24
Upgrading through update manager was going to take 4+ hours on my connection, so I torrented the alternate upgrade .iso, mounted it and upgraded.  Everything worked flawlessly, I was amazed!  My boot time has been cut in half, the system responds quicker and new notification eye candy is just icing on the cake.  This is my best experience with an Ubuntu version to date!

---

### Post by Pumalite on 2009-04-24
Upgraded one of my Intrepids amd64. It worked flawlessly.

---

### Post by fatbotgw on 2009-04-24
The only problem I had was with Grub.  After I upgraded and then installed the nVidia drivers, I rebooted.  At that point I got a "Grub Error 11" and couldn't boot into Ubuntu.  Turns out my menu.lst was missing a root location.

BAD:```
title Ubuntu 9.04, kernel 2.6.28-11-generic
root 
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=1b498d49-fcd0-4c54-bf0e-caa557b8802d ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet
```

GOOD:```
title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=1b498d49-fcd0-4c54-bf0e-caa557b8802d ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet
```

As you can see from the second line in each, they are different.  Don't know why it happened, but it did.

Otherwise, the upgrade(x64) went fine.  Downloading the files took all of last night, but that's to be expected with how hammered the servers were last night.  Also, I'm running the nVidia 180.44 drivers and Compiz is working fine with my 8800GTS (320MB) and dual 20" monitors.:guitar:

---

### Post by sloppyc on 2009-04-24
I tried to reinstall from the regular CD, thinking maybe I screwed something up last night when I installed after sharing a few bottles of wine with my wife.

Nope.  Did it sober, still useless.  I can login, I see my background for a moment (/home is shared between Ubuntu and a couple other distributions), then it all goes white.  Nothing I can do.

I've tried a "*dpkg-reconfigure xserver-xorg*" to no avail.  My xorg.conf is pretty sparse, my monitor and graphics card don't appear in there at all.  Strange.

I may have to skip this version.  That's okay though, I'll just pretend it doesn't exist.  Jackalopes aren't real, anyway.

---

### Post by fletchoid on 2009-04-24
Ran automatic upgrade.  Booted into newest kernel just fine.  Tried to play a video.  Was choppy and no sound. Installed fglrx driver for ATI 4870 from GUI.  seemed to work, but no sound in videos.  Tried to boot into lower number kernel and no such luck.  Total disaster.  Can't boot into ANY kernel.  Ran recovery mode in all kernels.  Tried to fix Xorg from all recovery modes.  Just get a totally broken display and locked up.  Would really like to rescue my instal.  I will be VERY hesitant to upgrade in the future, and will NOT recommend to my less experienced friends to try Ubuntu because of this disaster.  Help would be appreciated.  I am now stuck in.... shudder.... Windoze..... shudder.... only 1 desktop... no rotating sphere.... help!! Viruses are attacking me.....  I have the urge to instal a malware infested toolbar..... help!!

---

### Post by loyal one on 2009-04-24
I was not ableto install the upgrade to 9.04 -- from 8.10 -- because I am using the proprietary ATI/AMD FGLRX video driver, and 9.04 does not support the driver. What''s up with that??? It seems that I will have to install a fresh copy and install my preferences one at a time. That may not be so bad; my past experiences with Ubuntu upgrades have been sketchy at best.

Loyal01

---

### Post by enigmatic28 on 2009-04-24
Hi all,

i have installed kubuntu 9.04 yesterday and everything was working properly, until i installed XBMC and it was not working properly, so i search the forums for similar problem and found that it was a driver issue with ATI.

i followed the link hey have given there for the latest ATI driver and i have installed it, then the another problem has occurred and i do not know how to properly fix it...

the problem was after i rebooted my laptop, it won't display the desktop properly, this happens on the part where the splash screen would show.

so here is what i have done so far but with no luck in the recovery mode (or something like that)
1. chosen the option to repair broken packages --- nothing happened
2. chosen to login to terminal with networking and tried the following commands that i have found in the forums and rebooted every time to see if it works but still with no luck:
 sudo apt-get install xorg-driver-fglrx
 dpkg-reconfigure xserver-xorg

what i would like to do now is to reinstall the default graphics driver that kubuntu have installed for my laptop so that i can use it again properly.

as mush as possible, i don't want to reformat my laptop again.

i'm currently using the live-cd just to be able to post here...

any help will be much appreciated...

thanks...

---

### Post by larryboythedog on 2009-04-24
This tip changed my life! Went from 35 to 400= k!!!! Thank you so much! (now if I'd read it 8 HOURS ago...!!!)


> **bngguy said:**
> The Upgrade process went very smooth and my system has been working well,
the one thing i would like to suggest to people who have not yet upgraded is to first find the best mirror server, this could be done by :

***System --> Administration --> Software Sources*** then select ***Other*** from the ***Download from:*** menu item.

I started the process very late in the night abt 12:55AM and i had to download 1100 MB of data which took about 90 minutes on my DSL connection, then it took about 30 minutes to unpack and install the packages, clean up all the left over stuff, so it was roughly 2hrs for the entire upgrade process.

One thing i would like to know from other users who did a clean install, is if they used ext4 filesystem and do they see any speed differences.

---

### Post by MeanStreak on 2009-04-24
Ran the upgrade process. Upgrade completed, rebooted machine - graphics are scrambled and cannot view the login screen. I now cannot login or use my computer. I can only view this as a critical failure. I am typing this on a friend's PC. :confused:

UPDATE: It's working now. I booted into Recovery Mode, selected the command line option and ran the following command:
```
apt-get remove xorg-driver-fglrx
```

Rebooted as normal and can now login. Phew.

---

### Post by R@inm@n on 2009-04-24
I had one hell of a job trying to upgrade to 8.10 from 8.4, in the end I gave up and just wiped the HDD, installed JJ from a DVD and here I am.
Love the latest release, it works great.

R.

---

### Post by fletchoid on 2009-04-24
Thanks Grimmwolf:  I used apt-get remove --purge xorg-driver-fglrx to get back into my system.  Now, though, I can't use any fancy graphics effects.  I could run anything in 8.10;  3 rotating speres with videos playing on several surfaces, which you could look through the back of, etc.  Now, with the "upgrade" my graphics suck, and if I try to use the ATI drivers, my system crashes and won't boot.

---

### Post by Redsunz on 2009-04-24
> **autra said:**
> @4wd22r : your card is not supported by the new version of fglrx, which is needed to ubuntu 9.04.
Here is the complete list of the ATI drivers which are not supported any more : [http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)

HOWEVER, if you use open source drivers (if they work for you), you shouldn't have any trouble...

Even the new cards don't seem to work I have a 4870 X2 and when I tried to use the restricted drivers via the Sytem menu and terminal install Ubuntu crashes on boot up I see the progress bar then the next screen is a blurred mess.
I like my games so I may go back to 8.10 or XP

---

### Post by javyn999 on 2009-04-24
I just got into Linux a few weeks ago, and Intrepid was giving me nightmare driver issues with Nvidia.  I figured installing Jaunty would just be a continuation of all these probs, but no, everything works flawlessly!

---

### Post by MechaMechanism on 2009-04-24
The install was fine except for the bandwidth issue.  The servers were so overloaded that in synaptic the packages were listed as local/obsolete, but this returned to normal once I reloaded the package list.  Aside from that I am enjoying the 9.04 release quite a bit.

---

### Post by Aearenda on 2009-04-24
I've installed it 4 times, all fresh:
Acer Aspire One - good, see [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
Dell Inspiron 530N - perfect
Dell GL240 - perfect
HP TC1100 Tablet - good, had to copy xorg.conf from Intrepid to get tablet to work, and updated the wireless drivers from madwifi.

Really rather boring, it's too easy!

---

### Post by jf1991999 on 2009-04-25
I upgraded Intrepid to Jaunty fully expecting to have a number of major issues to resolve over the weekend as was my experience when upgrading from 8.04 to 8.10.  

The upgrade went flawlessly from beginning to end.  Everything appears to be working perfectly.  

Frankly I don't see a lot of difference between 8.10 and jaunty.  Boot time is not noticeable faster ( I always thought the boot time was very quick anyway and less than a quarter of the time taken for Vista on my dual boot system) and the look hasn't changed much at all apart from the login screen and the notifications.  

Maybe things are a little snappier, but again speed was never an issue for me.

I am using an HP Pavilion dv6700t and life is good. :)

---

### Post by blackfalcon03 on 2009-04-25
Hi Friends,

I am facing a big trouble in Upgarding from 8.10 to 9.04.:(

It started of as a normal upgrade using the upgrade manager. Even though I faced some trouble downloading the packages because of loss of internet connection, I was able to continue from where I left out, when I tried the upgrade again.
Once the packages are downloaded it started installing the packages one by one. Everything was going fine until the PC shutdown itself for no reason. I was really confused:confused: what happened as i did not really see it happening.

Now when I boot the PC, it loads the GRUB Loader. I was surprised to see only the 8.10 version entries in the GRUB menu list. However when I selected the latest entry i got the 9.04 splash screen and the login screen also resembled the 9.04 login. Once i entered my credentials, it took me to a blank screen- No icons, No taskbar, nothing....

I am able to start the terminal window with the shortcut key i had set earlier while using the 8.10 version. And using the terminal I can start browsers and applications required. However I could not get the internet connection also(I connect from a Wireless router). I am sure that the upgrade did not succeed before the PC went down, but not sure on how to repair my system with 9.04 in complete working condition.

Could you please help me...........:cry:

For your information I faced a similar problem while upgrading from 8.04 to 8.10. During that period I got some commands that could redo the upgrade step by step through the terminal from the forums. The upgrade still had minor problems but i was able to fix it in due course.

---

### Post by lovswr on 2009-04-25
Well after I read the little caveat about ATI hardware, I disabled my on board ATI adapter & installed a old nVdia 8600GS I had laying around.  Hit the upgrade button & 3 (painless) hours later & here I am :)

I have been trying to 'upgrade' with Fedora for like 3 years with no success.

---

### Post by Xavier Oddmon on 2009-04-25
I, so far, have mixed feelings about Jaunty. I will start by saying i'm quite impressed by its speed. I have now have a 21 second boot time, less than half the boot time I had in intrepid.

I'm using the ext4 filesystem, and this has happened twice now:

the first time, I was going through my contact photos, which i had just recently copied to the hard disk. After loading perhaps 15 of them, eog closed, my theme and icons turned to solid colors, and I couldn't open programs. Rebooting brought me to a root level terminal telling me to fsck manually. Fixed all problems (and there were lots). This was yesterday.

Fifteen minutes ago, I was deleting some text files off of my desktop, when a window came up telling me that it was a read-only file system. My theme disappeared again as well. When I rebooted, I got grub error 2. Using the live CD, I couldn't mount /dev/sda5 (my ubuntu partition), but an fsck from there fixed it. I haven't had any apparent data loss, but this will certainly get old fast if it continues. 

The install was a clean install, formatting my previous ext3 filesystem and replacing it with an ext4 filesystem. I'm using 9.04, 64 bit.

Although, there are some nice pluses. My mouse and touchpad don't have drastically different sensitivities. My xbox controller works fine, my webcam sort of works (inverted colors, really dark, but more than before.), sound works, nvidia graphics card works after manually installing nvidia-glx-180. 

I didn't vote in the poll. I wouldn't say that there are errors i haven't fixed, since it's working fine at the moment. But I also would most certainly not call these issues minor.

---

### Post by madman_lxl on 2009-04-25
So far so not good. Seems the 2.6.28 kernel has things missing like older patch's for 945 motherboards that have been removed FOR NO BLOODY REASON. Come on are linux dev's of late taking up Microsoft's mantra of not caring about older hardware?

---

### Post by wsonar on 2009-04-25
I was running the beta at work on ext3 I got the RC downloaded tonight 

download took about 30min 

install was pretty quick choose the ext4 Can definitely  can tell a speed improvement very quik and snappy

everything else flaless wireless keyboard mouse and wireless usb all recognised automaticly 

pluged in passport drive played a mp3 automaticly asked to install apropriate codec

after codec was installed mp3's and avi's  and all other media seem's to play no problem

Quick and easy install with the essentialls working!!

---

### Post by berlinbrown on 2009-04-25
Yea, the previous version of Ubuntu upgrade worked flawlessly.  This one has had a couple of major issues that have prevented me from doing anything.

I did the upgrade route and I had some disk issues early on.  On start-up, the file check would run and stop at 65% and then kick me to the command line in read only mode.

I believe the disk issue was cause because of Jaunty not liking something with my filesystem.  I ran fsck and did the repair on the filesytem inodes that had the problem and Ubuntu was able to start.

On the first couple of reboot, the GDM (Gnome Display Manager failed to start).  For some reason, now I get a different issue.  When I reboot now, I get a blank screen.  Also, my keyboard does not respond to input.
-----

I am guessing X windows was reconfigured or is messed up somehow.  I normally use the nvidia configurations and that GUI tool would configure X and the card for me.  How do I upgrade downward?

-----

It isn't a big deal, I have been using Ubuntu for years but I can't say that so far it was a perfect experience.

---

### Post by mingtien on 2009-04-25
I did a fresh install on another partition (run with Jaunty for a month, if everything works, use the Intrepid partition to play with other distributions).  Partly in case of problems, more because there was so much 'cruft' that had accumulated on the drive that a fresh start was not a bad idea (hmm.. too bad you can't do that with your house!).

First amazing thing: my EVDO dongle was autodetected and connected automatically.  Joy of joys!  Before I had a script placated various modules and ran wvdial -- so this is great!  Even better -- applications now sense that I am online (before Firefox would always start in offline mode -- a bit tedious.

I like notifications -- very elegant!

Google Earth is a non starter until someone releases an ATI driver (please please!), which is a bit of a pain, as I use it for work (settling for Maps for the time being).

Weather finally working, which is very useful (I know, small thing, but in such a hot country and going into monsoon season, it's useful).

Oh one glitch -- I wanted to resize the Windows partition to install, but parted could not read the partition...  ...so I finally got rid of it (I haven't booted Windows in months anyway, and Wine seems to be maturing nicely).

Overall verdict: I'm very impressed.  Looking forward to the ATI drivers :)

---

### Post by BoringOldFart on 2009-04-25
I think you guys have lost the plot. Why? I'll try to convince you politely.

This is the upgrade poll for Jaunty. The upgrade to Hardy Heron 8.04 poll is closed.

Why does this matter?

Hardy Heron is an LTS server release. Ubuntu has made its name partially through the promise of easy administration, long term support, and clear release and upgrade paths.

I have been running Ubuntu for many years (since Warty Warthog in fact) and Linux longer than that. 

Last year around this time of year I built a server.

6.06 LTS was pretty ancient and would not support the hardware.

8.04 was going to be released a month later. I couldn't wait so I went for 7.10 in the knowledge I'd have to go to 8.04 one day. I was not prepared to spring straight onto a very early 8.04. So I ran 7.10 for a year or so.

I looked earlier at moving to 8.04, but you guys had a huge and long open bug where the upgrade crashed on kernel release 15 ([http://brainsik.theory.org/.:./2008/ubuntu-710-gutsy-804-hardy-upgrade-freeze](http://brainsik.theory.org/.:./2008/ubuntu-710-gutsy-804-hardy-upgrade-freeze)) Did not inspire confidence so I thought I'd wait for everything to be stable.


7.10 end of life is announced. [http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)

Now I finally decide to go get the latest updates for the 7.10 packages and upgrade: just one week after end of life: guess what? They've moved 7.10. How nuts is that? Something  that is in production about a year and you can't get patches any more using the standard tooling. I can understand you say it is end of life but don't you realise that you've prevented the average user from upgrading using the standard tooling? First thing you have to do is patch 7.10 to the latest patches before doing a distro upgrade. Then the next step, you have to upgrade via the distro upgrader for 8.04 .... which lives in the 7.10 packages. That also breaks because the repositories have been moved. And it doesn't break cleanly. It falls in a heap. The user is then forced into looking at /etc files using vi and updating package sources. Next time it runs, the distro upgrade insists on doing a partial upgrade even after editing the /etc/sources.list file to the old-releases URL. Why not upgrade the update manager to simply say that this release chain is end of life when you update to the last supported release in this chain and then ensure that the distro upgrade button really really always does work so people have confidence in it? Why do you have to move the URL at all? Why not have a specific host URL for package sources in the first place per release chain that never ever changes and host it using virtual servers or whatever on the physical machines? Then you can move that URL to another physical machine if you are getting short of space or whatever, without breaking the upgrade path. I see on poll that only around 20% of people upgrade without problems. If M$ did this there'd be absolute outrage. So why do you guys think this is acceptable? The distro upgrade from the last supported release of one distro to the next supported distro should be holy for you, certainly if that's your unique selling point (stable release train).

OK next experience: I finally get 8.04 packages downloaded and complete the partial upgrade. Takes around an hour from a local mirror.

What's the damage?

TWiki upgrade failed (guess that was my fault as I screwed down the permissions)

Asterisk failed to start. Config running fine on 7.10 fails on 8.04. Looks like the timing initerface in the kernel has changed 7.10 didn't need ztdummy. Apparently 8.04 does. So I compile asterisk direct from sources. Works first time without changing my config. Annoying and pretty inexcusable but it's working now.

Postfix fails. Config running fine on 7.10 fails on 8.04. After many hours searching I'm not sure of the exact cause. It was failing to connect to sasl socket. I guess this was to do with a chroot problem. Anyway I compiled, installed  and manually configured from source based on this howto [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04) This took lots of messing around with obscure debugging of saslauthd. Why is configuring a simple mail server still so difficult after 20 years? I thought I'd be done with using gcc on sendmail and postfix sources by now.

The machine freezes on suspend/restore. Only solution is to keep the power button pressed for 4 seconds.

There are numerous other small things I think I'll have to detect and discover in the coming days. So We're talking well over 12 man hours to do what should be an easy task on a single server. Remember, I didn't want to upgrade. I just want security and bug fixes and stability packaged in a LTS server OS. It is your release chain that forced me to upgrade.

The upgrade from 7.10 to 8.04 has been a disaster as far as I'm concerned.

I think I'll be looking for a new server distro. One that really is stable, one that just does security and bug fixes only, and has proper long term support (with potentially some hardware support additions in case the old hardware breaks). Seems to me Ubuntu has decided the desktop is priority and Windows Server is not a competitor. Well just remember where you came from guys. Linux servers were how you got into these companies in the first place. Personally, I think Windows XP/ Office 2000 feature set was fine for the majority of corporate users. Many corporations are still running this stuff in production for tens of thousands of users. It's good enough. Both MS and Linux seem to have gone feature crazy for stuff that 95% of normal users don't care about at all. My iMac running OSX is the machine that is most pleasing for me to work with at the moment. Super fast, stable, and it just does what I want without having to go to a terminal prompt, or reboot a new patch every day.

HP 3000 MPE. Now that's what I call proper long term support.

---

### Post by GuiGuy on 2009-04-25
Updated the home entertainment center's mythbuntu this afternoon (AU). 

No problems, everything seems good.

Much better than my office desktop, which has been an absolute disaster (leers left, looking at Win7) :(

---

### Post by Ticketoride on 2009-04-25
> **blackSP said:**
> After the upgrade none of my windows have borders or a windows bar. Can't resize them, move them. So I will wipe the damn thing tonight and start from scratch :mad:
Couldn't find a Way to fix that either, then the Keyboard got lost and couldn't be gotten back.

> **saboya said:**
> My real complaint lies on the absence of documentation. That alone would have kept me away from Jaunty and keep my Intrepid Ibex install, which worked fine. And no matter which method is used to "solve" the problem, it's not something an end user should be doing, that's why I installed Ubuntu in the first place. If the only thing I get from Ubuntu is a larger user base to help me solve my problems, I might as well stick to other supposably non-user-friendly distro, like Gentoo, which I use in my desktop.
Ubuntu certainly is making public Waves. Ma 'n Pa Computer Store around the Corner already had a Dozen Machines brought in today after 9.04 installs, more than they had all Year. Over half were Grub Errors.

---

### Post by quotidion on 2009-04-25
I installed the i386 desktop ISO of Jaunty over an old Ubuntu install, replacing it entirely.  There is also WinXP on a different HD. I kept getting "Firefox is already running" whenever I tried to start it.

When you try to start Firefox and you get this error it can mean a couple different things. One of the most common is that Firefox cannot find or write to your Firefox profile.

Apparently Jaunty looks for your Windows profile and, quite reasonably, tries to share that if it exits.  This is what my install tried to do, but it didn't work well for me.

When setting up my partitions, I told the installer to mount my Windows NTFS partition as /media/windows and a shared VFAT partition as /media/shared.  The VFAT partition exists so that older versions of Ubuntu could share files (read & write) with Windows. 

However, my NTFS volume got mounted as /windows.

Meanwhile my Ubuntu Firefox profiles.ini file, which tells Firefox where to look for my profile, was saying to look in /media/inferno. This is almost the way that I'd asked it to be set up: "inferno" is the actual partition name of my NTFS partition, that I asked to be mounted as /media/windows.

My VFAT partition did get mounted as /media/shared, as requested, not that that helped.

Instead of changing the way the NTFS volume got mounted, I changed the profiles.ini file to point to the /windows mount, instead of the /media/windows mount that I'd originally tried for, or the  /media/inferno mount that Firefox apparently was told to expect.

I'm not sure why things didn't get mounted the way I requested. Maybe Ubuntu would have mounted my NTFS as /windows by default and my specifying where to mount it just messed things up.  If so, it could have been more clear about what it wanted to do.

GRUB correctly listed Windows a boot option, but not the default one as I had before. (This is a shared machine.) Perhaps this is because I was overwriting my old Ubuntu setup instead of upgrading it. If the installer tries to keep the same default, it should take a look at my boot options before erasing the old install. Or, perhaps, ask for my preference for a default boot.

After years of playing with Debian and Ubuntu I know how and where to change what the default boot option is, but I would guess that people completely new to Ubuntu might be frustrated at that.

Otherwise, running pretty smoothly.

---

### Post by tolachi on 2009-04-25
> **berlinbrown said:**
> 

On the first couple of reboot, the GDM (Gnome Display Manager failed to start).  For some reason, now I get a different issue.  When I reboot now, I get a blank screen.  Also, my keyboard does not respond to input.
-----

I am guessing X windows was reconfigured or is messed up somehow.  I normally use the nvidia configurations and that GUI tool would configure X and the card for me.  How do I upgrade downward?



I am having the same problem with a blank screen and no keyboard response.  I've tried copying over with the original xorg.conf file and generating a new one, but no luck.

---

### Post by shayguitarra on 2009-04-25
Well, I had some problems as detailed here [http://ubuntuforums.org/showthread.php?t=1135033](http://ubuntuforums.org/showthread.php?t=1135033). But now everything is running smoothly even if on kernel 2.6.24-22. Could someone just let me know if this actually counts as having the system running properly. I'm assuming that this kernel is just a slightly older release candidate.

It feels very stable except knetwork manager seems to have disappeared and I have to connect to the internet via terminal. And I'm running my nvidia 9500GT with the open source driver, which is fine as I don't really play games.

If I could make one suggestion. Given the number of problems (bordering on anger in some instances) that people seem to be having it would be an idea if it were made clearer that the official release may actually cause problems. I think a lot of people simply get caught up in the release frenzy and expect a completely unproblematic expansion and improvement of their previous OS. I know the download page lists regressions and issues but perhaps a message (like the banner message for reporting bugs) would save everyone, users and devs, a lot of aggravation. Someone on another thread suggested that anyone unprepared for some problems should maybe wait a month or so before upgrading. :)

---

### Post by ursus262 on 2009-04-25
My Kubuntu upgrade went perfectly, and I'm delighted with the result.  Since I had only recently upgraded from Hardy Heron to Intrepid Ibex, my install was pretty fresh anyway.  A lot of the problems on here, I would guess, is down to broken dependencies and missing libraries.

I find that in my experience, the best approach is to:

[LIST=1]
Back up your Home folder onto another drive;
download the ISO and burn it to a CD
Connect your pc or laptop directly to your modem/switch using ethernet;
Install the latest version from the CD you just burned and let drivers be found from the repositories; and
finally, restore your home folder.[/LIST]

I find this works for me most of the time.

Hope this helps

---

### Post by paapereira on 2009-04-25
I upgraded my 64bit Ubuntu 8.10 HP dv5-1020ep laptop using the alternate cd. All went well except for the **sound**.

After **[following this instructions]("http://ubuntuforums.org/showthread.php?t=789578")** I have sound if I use headphones, but there's no sound coming out of the columns.

This is an issue with the new kernel I think, because if I reboot into a previous kernel the sound works.

Also, when checking for new updates, I have to do a Partial Upgrade in order to continue. This partial upgrade isn't working. When it says how many packages will be updated and I click Update Now it exits...

If anyone has tips on how to make my columns work please post something :)

Thanks a lot!

---

### Post by roaldz on 2009-04-25
I got a problem with my mousepad after installing 9.04. Solution:

```
sudu modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

create file as root with favorite text editor:

```
sudo nano /etc/modprobe.d/options
```
paste this:
```
options psmouse proto=imps
```

This works for my Elantech touchpad

Roald

---

### Post by Bruce S on 2009-04-25
> **shayguitarra said:**
> Well, I had some problems as detailed here [http://ubuntuforums.org/showthread.php?t=1135033](http://ubuntuforums.org/showthread.php?t=1135033). But now everything is running smoothly even if on kernel 2.6.24-22. Could someone just let me know if this actually counts as having the system running properly. I'm assuming that this kernel is just a slightly older release candidate.

It feels very stable except knetwork manager seems to have disappeared and I have to connect to the internet via terminal. And I'm running my nvidia 9500GT with the open source driver, which is fine as I don't really play games.

If I could make one suggestion. Given the number of problems (bordering on anger in some instances) that people seem to be having it would be an idea if it were made clearer that the official release may actually cause problems. I think a lot of people simply get caught up in the release frenzy and expect a completely unproblematic expansion and improvement of their previous OS. I know the download page lists regressions and issues but perhaps a message (like the banner message for reporting bugs) would save everyone, users and devs, a lot of aggravation. Someone on another thread suggested that anyone unprepared for some problems should maybe wait a month or so before upgrading. :)

Phew- after reading that and other posts I will take your advice and wait for a month or so.

 Thanks for warning me .:shock:

---

### Post by N2PTF on 2009-04-25
Took over a couple of days to update through the update manager, but other than that it appears that everything went well on my Dell 530N. Suspend/Hibernate even works:)

---

### Post by atomizer on 2009-04-25
did an upgrade and wireless was gone again, and knetworkmanager wont start at startup.

tried several methods, but couldnt get my wireless to connect to encrypted networks.

Gonna try a fresh install when i have an empty cdrom, because other users say their atheros ar5007 works out of the box.(and I want to switch to ext4 in a easy way)

---

### Post by nzmoose on 2009-04-25
clean install of jaunty server - by and large amazingly awesome.
having some sound issues though :confused:

---

### Post by Aristide on 2009-04-25
(Kubuntu) - First I tried the online update. That downloaded everything but then simply stopped so I had no way to go from there.
Next, I used the Alternate CD, which worked fine.
Trouble started after the next reboot :
- lost all audio (my Intel soundchip not recognized anymore) ;
- about 30 packages "held back" at each update/upgrade session.
I'll spend the next few hours looking for a way to solve this. Burnt the Desktop Installer iso during lunchtime so when I get tired of forum browsing and troubleshooting, I'll resort to a fresh install instead, as I used to do with previous editions. Maybe switch to EXT4 in the process.

---

### Post by prkos on 2009-04-25
I went for the upgrade and the process was slow because some files were slow to get, but it went ok except no compiz. 

I had problems with nvidia driver, then with deinstalling it, in the end I managed to clear the system and installed it manually and now it's all working, including compiz. 

Although the problems I encountered weren't easy to solve (I had expert help) I'm glad to be on the new version :)

---

### Post by juelze on 2009-04-25
My biggest problem, was when I went to use the update manager it basically stalled at downloading the update tool (there were 2 files to download). Frustrated, I clicked cancel and then it started working.  Weird.  Anyway, I left it on overnight as I was getting dial-up speeds when downloading, but now everything is great.  I have an ATI 9800 pro and it seems to run A LOT better in Jaunty then it did in Intrepid.

---

### Post by redb on 2009-04-25
I had purchased my wife a new HP Compaq CQ60 which is not a top of the line laptop.  I installed 8.10 after quite a bit of difficulty with the proprietary OS that came with it.  8.10 was not so good either due to my knowledge.  I did a clean install of 9.04 and every thing works perfect, no problems, I am very happy.  My wife is very happy, she is no longer threatening to throw her laptop into the driveway on a daily basis or do mean things to me when I'm sleeping.  

Now if I could just do an install on my hp zd8000 (ATI graphics) life would be good.  

Cheers for the developers!  You have made my beautiful wife extremely happy, which keeps everyone in the house happy!

Mike

---

### Post by Jose Catre-Vandis on 2009-04-25
All went well with a fresh install of Xubuntu 9.04. Check my sig for more details.

---

### Post by Ericyzfr1 on 2009-04-25
The install process went without any problem, everything works just fine.

---

### Post by codya517 on 2009-04-25
Install went fine until restart. At restart, apparently the GUI won't load. I'm in recovery mode right now with a CML+Network.

Basically the Ubuntu loading bar goes as usual and then the screen gets scrambled and I have to manually power down my computer.

I am using an ATI Radeon 4650 card that ran absolutely fine until this.

If i have to reinstall 8.10 I will...i just need to grab a file off of my comp first and put it onto a usb flash drive through the cml.

---

### Post by nsramkishen on 2009-04-25
I tried to install Jaunty using Wubi. I selected the D drive, which I had used for Intrepid (I had uninstalled Intrepid). The drive has 15GB (sufficient for Jaunty). During installation, something like the message "creating virtual disks" was shown and I was waiting for aeons before cancelling it. I found that pagefile.sys was created in the C drive for this installation. The C drive only has 3.5GB of free space. So, I changed the system setting to create pagefile.sys in the E drive. Even after this, Wubi tried to use the C drive and at one point, all the space was taken up by the installer, yet Jaunty was not installed. Now I want to recover the 3.5GB eaten by Wubi. Can someone show me the way? There are no traces of Wubi in the C drive.

(In hindsight, I think I should not have tried Jaunty. I should have waited for a month or so. Hmm...)

--Brooding Ram

---

### Post by autra on 2009-04-25
> **codya517 said:**
> Install went fine until restart. At restart, apparently the GUI won't load. I'm in recovery mode right now with a CML+Network.

Basically the Ubuntu loading bar goes as usual and then the screen gets scrambled and I have to manually power down my computer.

I am using an ATI Radeon 4650 card that ran absolutely fine until this.

If i have to reinstall 8.10 I will...i just need to grab a file off of my comp first and put it onto a usb flash drive through the cml.

Do you use fglrx drivers (proprietary drivers from ati) ? Did you check if your card haven't be moved to the legacy software support ?
If so, fglrx won't work with ubuntu 9.04 (ati's fault, not ubuntu).
Intead, use the open source drivers, and everything should be fine (but compiz may not work very well). I had the same problem as you, with a radeon X1600.

---

### Post by Devi 710 on 2009-04-25
I did a fresh install. Everything went fine except when I went to add the proprietary drivers for my Nvidia 6200 card under "Hardware Drivers", it timed out. I rebooted and found that is did in fact install.

I had the same issue with the Live CD. And from what I read in the bug reports, it was still happening in the RC candidate.

Otherwise, 9.04 is awesome. I didn't update since 7.10 because I felt the last two versions weren't worth it. But 9.04 is :)

---

### Post by vijaym on 2009-04-25
Upgraded using the alternate cd
worked well mostly

Problem areas

Wifi recognition
screen resolution

Figured out that upgrading without an internet link was slow and caused some problems esp wifi set up
Used envyng to sort out my screen resolution

Machine 
HP dv6611ie
AMD laptop with nvidia card
Broadcom wireless

---

### Post by spacedoubtman on 2009-04-25
I don't think an ubuntu dist upgrade has ever worked properly for me - in future I will just re-install fresh.

Few things.
* As usual it takes ages so I leave it but when I come back there is some question on the screen and need to click ok.
* I got some errors installing memtest.
* It kept asking me if I want to run lilo but I don't care - in fact it looks like my system is using grub anyway
* When asking about lilo it shows this in the console - I run ubuntu on my widescreen tv with large fonts so the console drops past the bottom of the screen and at first I couldn't move the box up. Eventually I found that by enabling compiz and setting some settings this could be done.
* Now the killer and where I'm at - Its all installed but on reboot it says it fsck cant find /dev/md0. I've remove this from /etc/fstab and rebooted and now I get into X but what about my raid disk. Do I have to assemble manually, have I lost all my data - looks like there goes my Saturday afternoon.

---

### Post by myk.dinis on 2009-04-25
Everything went smoothly, except...

KTorrent and AmaroK no longer act the same...

Any ideas how I can remedy the situation?

Thanks!

Myk

---

### Post by Crank-N-Jam on 2009-04-25
Just wanted to say that I've upgraded two machines.  

First being my laptop, a Dell Inspiron 2200.  Upgrade was flawless.  First time too.  Usually I have to fuss around with my wireless.

Second was my main PC.  This one never goes smoothly.  Always have to mess with my audio (M-Audio Delta 1010LT) and video (onboard nvidia 7100, usually the dual monitors that cause some issues).  This time, the only two things that didn't work was Amarok 2 (had to install phonon-backend-xine and it's fine now) and flash, which I installed via Adobe's website with no issues.

So hands down the best upgrade process to date.  Many kudos for all the hard work!!!!!

Jason

---

### Post by pickarooney on 2009-04-25
I resisted the urge to click on the Upgrade to 9.04 button on my dekstop and instead threw my laptop to the Jackalopes, as much to see just what basic element of the system the upgrade would royally **** up this time. Previously it's been the usual supsects (no graphical interface, no soundm no network connection) but this time there's a new fubar - xfce and gnome zere apparently not found and so I have instead a simple xterm window in lieu of a desktop environment. 

Once again, sterling work from Canonical in making a flawless upgrade procedure - screw the bejesus out of the existing system and thereby force a clean install.

Now, if only I had a blank CD!

Unless someone has an idea of how to rescue a hosed system using only an xterm window?

---

### Post by hipogrito on 2009-04-25
Hello,

I have been using Ubuntu for the past 2 years. No big problems in updates except for this one, where I could not get to the login page. I could see the loading bar at the beginning, then a lot of pages from black to grey, flickering, but no login page at the end.

I have an Intel graphics card and I tried to follow some of the advices here for that, but they did not work... so, finally I found my solution...

[http://news.softpedia.com/news/Install-Nvidia-and-ATI-video-drivers-on-Ubuntu-Edgy-44388.shtml](http://news.softpedia.com/news/Install-Nvidia-and-ATI-video-drivers-on-Ubuntu-Edgy-44388.shtml)

Following more or less that, packages names are a little different today, now I can log in!

Regards,
Hipo

---

### Post by Qwertyfog on 2009-04-25
Wubi instal > bunch of problems > not solved

1 Got original 9.04 iso from website, burned it.

2 If i try to install an english version:

[IMG]http://img15.imageshack.us/img15/2570/uberror.gif[/IMG]

(my windows is weird, it's half russian. It says that there is an arror, an where to find log. I didn't dug it out though).

3 Okay, lest boot. But no, when selecting any item in main boot menu (by pressing enter), everything freezes for few seconds and nothing happens.

And yes, i'v tryed istalling using wubi and .iso - it's the same.

---

### Post by Anzan on 2009-04-25
I've just upgraded an old Thinkpad R40 to 9.04. Everything works.

---

### Post by ascandaroli on 2009-04-25
For some reason I still don't have a clue after running the upgrade from 8.10 to 9.04 ubuntu seems to be loading things doubled or even tripled.

When I log into my gnome session I receive many errors due to ubuntu launching multiple instances of many applications.

To depict a bit below is a ps command result:
[INDENT][FONT=Courier New]username@hostname:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:01 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   12 ?        00:00:00 kstop/0
   13 ?        00:00:00 kstop/1
   14 ?        00:00:00 kintegrityd/0
   15 ?        00:00:00 kintegrityd/1
   16 ?        00:00:00 kblockd/0
   17 ?        00:00:00 kblockd/1
   18 ?        00:00:00 kacpid
   19 ?        00:00:00 kacpi_notify
   20 ?        00:00:00 cqueue
   21 ?        00:00:00 ata/0
   22 ?        00:00:00 ata/1
   23 ?        00:00:00 ata_aux
   24 ?        00:00:00 ksuspend_usbd
   25 ?        00:00:00 khubd
   26 ?        00:00:00 kseriod
   27 ?        00:00:00 kmmcd
   28 ?        00:00:00 btaddconn
   29 ?        00:00:00 btdelconn
   30 ?        00:00:00 pdflush
   31 ?        00:00:00 pdflush
   32 ?        00:00:00 kswapd0
   33 ?        00:00:00 aio/0
   34 ?        00:00:00 aio/1
   35 ?        00:00:00 ecryptfs-kthrea
   38 ?        00:00:00 scsi_eh_0
   39 ?        00:00:00 scsi_eh_1
   40 ?        00:00:00 scsi_eh_2
   41 ?        00:00:00 scsi_eh_3
   42 ?        00:00:00 scsi_eh_4
   43 ?        00:00:00 scsi_eh_5
   44 ?        00:00:00 kstriped
   45 ?        00:00:00 kmpathd/0
   46 ?        00:00:00 kmpathd/1
   47 ?        00:00:00 kmpath_handlerd
   48 ?        00:00:00 ksnapd
   49 ?        00:00:00 kondemand/0
   50 ?        00:00:00 kondemand/1
   51 ?        00:00:00 krfcommd
  416 ?        00:00:00 khpsbpkt
  593 ?        00:00:00 knodemgrd_0
  804 ?        00:00:00 kjournald
  952 ?        00:00:00 udevd
 2080 ?        00:00:00 mount.ntfs-3g
 2084 ?        00:00:00 mount.ntfs-3g
 2088 ?        00:00:00 mount.ntfs-3g
 2364 tty4     00:00:00 getty
 2365 tty5     00:00:00 getty
 2368 tty2     00:00:00 getty
 2371 tty3     00:00:00 getty
 2372 tty6     00:00:00 getty
 2445 ?        00:00:00 acpid
 2460 ?        00:00:00 vino-server
 2461 pts/0    00:00:00 ps
 2494 ?        00:00:00 syslogd
 2517 ?        00:00:00 dd
 2519 ?        00:00:00 klogd
 2542 ?        00:00:00 dbus-daemon
 2566 ?        00:00:00 sshd
 2594 ?        00:00:00 postgres
 2597 ?        00:00:00 postgres
 2598 ?        00:00:00 postgres
 2599 ?        00:00:00 postgres
 2600 ?        00:00:00 postgres
 2780 ?        00:00:00 hddtemp
 2814 ?        00:00:00 nmbd
 2818 ?        00:00:00 smbd
 2839 ?        00:00:00 smbd
 2840 ?        00:00:00 winbindd
 2863 ?        00:00:00 winbindd
 2888 ?        00:00:00 hald
 2891 ?        00:00:00 console-kit-dae
 2954 ?        00:00:00 hald-runner
 2983 ?        00:00:00 hald-addon-usb-
 2985 ?        00:00:00 hald-addon-inpu
 3032 ?        00:00:01 hald-addon-stor
 3034 ?        00:00:00 hald-addon-stor
 3052 ?        00:00:00 hald-addon-cpuf
 3053 ?        00:00:00 bluetoothd
 3054 ?        00:00:00 hald-addon-acpi
 3089 ?        00:00:00 gdm
 3128 ?        00:00:00 NetworkManager
 3146 ?        00:00:00 wpa_supplicant
 3148 ?        00:00:00 nm-system-setti
 3152 ?        00:00:00 avahi-daemon
 3153 ?        00:00:00 avahi-daemon
 3176 ?        00:00:00 cupsd
 3221 ?        00:00:00 system-tools-ba
 3290 ?        00:00:00 atd
 3318 ?        00:00:00 cron
 3387 ?        00:00:00 apache2
 3405 ?        00:00:00 dhclient
 3413 ?        00:00:00 jsvc
 3414 ?        00:00:00 jsvc
 3416 ?        00:00:03 jsvc
 3429 ?        00:00:00 gdm
 3434 ?        00:00:00 apache2
 3435 ?        00:00:00 apache2
 3436 ?        00:00:00 apache2
 3437 ?        00:00:00 apache2
 3438 ?        00:00:00 apache2
 3665 ?        00:00:00 timidity
 3670 tty1     00:00:00 login
 3890 ?        00:00:00 ntpd
 4028 ?        00:00:00 evolution-data-
 9548 tty7     00:02:58 Xorg
 9761 tty1     00:00:00 bash
10161 ?        00:00:00 gnome-keyring-d
10173 ?        00:00:55 x-session-manag
10233 ?        00:00:00 ssh-agent
10236 ?        00:00:00 dbus-launch
10237 ?        00:01:20 dbus-daemon
10242 ?        00:00:00 pulseaudio
10243 ?        00:00:00 gconf-helper
10245 ?        00:00:43 gconfd-2
10256 ?        00:00:00 seahorse-agent
10259 ?        00:00:03 gvfsd
10265 ?        00:00:00 gvfs-fuse-daemo
10272 ?        00:00:20 gnome-settings-
10280 ?        00:00:38 compiz.real
10281 ?        00:00:23 gnome-panel
10283 ?        00:00:01 nautilus
10285 ?        00:00:00 bonobo-activati
10286 ?        00:00:06 trackerd
10288 ?        00:00:19 skype
10289 ?        00:00:45 firefox
10293 ?        00:00:10 pidgin
10294 ?        00:00:31 skype
10296 ?        00:00:15 python
10298 ?        00:00:07 tracker-indexer
10300 ?        00:00:01 vino-server
10301 ?        00:00:03 bluetooth-apple
10308 ?        00:00:04 tracker-applet
10309 ?        00:00:02 launchy
10314 ?        00:00:02 launchy
10321 ?        00:00:00 gvfs-hal-volume
10322 ?        00:00:05 launchy
10324 ?        00:00:00 trashapplet
10333 ?        00:00:02 launchy
10335 ?        00:00:05 nm-applet
10337 ?        00:00:00 gvfs-gphoto2-vo
10339 ?        00:00:04 update-notifier
10341 ?        00:00:00 gvfsd-trash
10344 ?        00:00:04 evolution-alarm
10348 ?        00:00:05 notify-osd
10355 ?        00:00:00 cpufreq-applet
10357 ?        00:00:07 gnome-power-man
10361 ?        00:00:08 multiload-apple
10364 ?        00:00:07 fast-user-switc
10379 ?        00:00:00 mixer_applet2
10388 ?        00:00:22 indicator-apple
10403 ?        00:00:00 evolution-excha
10438 ?        00:00:00 evolution-data-
10526 ?        00:00:00 gvfsd-burn
10613 ?        00:00:00 sh
10614 ?        00:00:00 compiz-decorato
10616 ?        00:00:00 gtk-window-deco
10904 ?        00:00:15 gnome-screensav
12381 ?        00:00:00 SystemToolsBack
17585 ?        00:00:05 gnome-terminal
17597 ?        00:00:00 gnome-pty-helpe
17598 pts/0    00:00:00 bash
[/FONT][/INDENT]Many processes above are repeating and making my system extremely load full.

You can see that there are multiple instances of launchy, skype, apache, migration, kstop, smbd, kintegrityd, etc...

Does anyone know why is this happening?

Any hint on how I could get this solved?

---

### Post by pickarooney on 2009-04-25
FWIW I was able to resolve my issue in about 10 minutes, but only because I knew where to look for advice and because I had a second machine handy to search for a solution with. The problem in question is a recognised bug and it just completely baffles me how anyone can release an OS in the knowledge that it's not going to start up properly...

---

### Post by kahping on 2009-04-25
My DVD writer's disappeared :-(

Other than that everything else seems ok. No ideas at all where to start with this :-/

---

### Post by Spiritous on 2009-04-25
Pretty Balanced... Some people have problems, some don't... Normally its all bugged bugged, but really, good job Canonical!!

---

### Post by Elviswind on 2009-04-25
Only thing I had to do was re-enter my network settings . . . my wired connection was set back to DHCP.

Also, I had to manually reinstall my NVIDIA drivers from a terminal session when I rebooted from Hardy . . . but that wasn't a surprise, I have to do that everytime there's an update to the Linux kernel.

---

### Post by rasca7 on 2009-04-25
Hi, I can't install Jaunty... I'm trying to install it from the alternate CD onto my Macbook 1,1 , but my keyboard doesn't seem to work. I've posted more on this here:
[http://ubuntuforums.org/showthread.php?t=1137001](http://ubuntuforums.org/showthread.php?t=1137001)
Thanks

---

### Post by ngsupb on 2009-04-25
I am happy now

Upgraded, somehow I crashed my video drivers. Reinstall custom kernel. reinstalled nvidia. Reisntall kernel again, because I missed some options.

It rocks now :guitar:

Except of  segfault bug in libc-2.9.so( think it will be fixed soon )

everything other is fine.

P.S.

Instead of promised reducing boot time. it is booting longer now about 1 min instead of 45 sec on 8.10 :S

[http://autoya.info/volkswagen_saveiro_announce_photos_engine_sell/](http://autoya.info/volkswagen_saveiro_announce_photos_engine_sell/)

---

### Post by Pipette Monkey on 2009-04-25
I updated through the update manager and have had nothing but troubles.  The time from login prompt to desktop is notably slower.  Everything seems generally slower.  Tracker has been throwing out all sorts of errors about corrupt indexes.  Worst of all, I have had the computer freeze three times so far, without having a single freeze since building the computer.

---

### Post by MickSulley on 2009-04-25
Just updated my desktop running 64 bit.  It all seemed to go OK, opened up Evo mail, looked OK, opened Firefox and it failed with no network, checked mail again and no network (it is wired).  

Tried to restart, got to the new logon screen, looked OK, but after my username and password I just got a black screen with the mouse pointer, could not do anything at all.  Tried again a couple of times and got the same problem.  Then I booted into recovery, tried the package and file options, didn't seem to find anything, then continued to normal boot and it was fine.  I have restarted a couple of times since and it all seems fine now, just wish I knew what was wrong and how I fixed it!

Now I need to decide if I upgrade my laptop, also 64 bit Intrepid. I think I will leave it a day or two....

---

### Post by Anzan on 2009-04-25
> **Anzan said:**
> I've just upgraded an old Thinkpad R40 to 9.04. Everything works.

Update: Suspend/resume doesn't work.

---

### Post by ngsupb on 2009-04-25
I would advise for users who think about upgrade/not upgrade. Better do not upgrade it atm:D Wait a few weeks until it is more stable. I haven't noticed big difference between 8.10/9.04 just some bugs that took me a few days to back everything to normal :D
It is linux :D

---

### Post by AlanInVancouverBC on 2009-04-25
Surprisingly fast download on Friday morning (pacific coast time). Easy burn from 8.04 software to installation disk. Very fast installation. Very easy and clear directions during installation. 

And above all, everything worked!!! "Right out of the box!"

Even the internet connection, which along with the display problems I had with 8.10, killed my experience with Ibex.

Congratulations to all involved. Sorry I could not name you all....

I've been with Linux/Ubuntu for about 9 months solidly, and 4 months clean of Windows. How could I ever go back???

---

### Post by ninjabob7 on 2009-04-25
I was rather disappointed. I was hoping this would be the first upgrade where I didn't have to fix anything afterwards.
I rebooted and found, as I sort of expected, that my NVIDIA drivers were broken *again.* Then I realized my network drivers were broken (which doesn't usually happen). After I finally found the module for my card, I saw that it was blacklisted and fixed that.
I uninstalled nvidia-glx-173 and reinstalled, which did nothing. I discovered envyng and installed that, which led me to discover that my boot menu didn't get upgraded and I was still running the old kernel.
After fixing my menu (not sure how I did it), envyng fixed my NVIDIA driver painlessly - I was impressed by that. Now everything appears to be working. *cross fingers*

---

### Post by deb_untu on 2009-04-25
> **obocho said:**
> fresh install: no problem, everything worked just fine...
I can even say that [so far] Jaunty is the best release I have ever installed!

have fun!!! :)

Have same thing to say.I have P4,intel 845GLLY motherboard;
Installed with alternate install CD.

---

### Post by Cam42 on 2009-04-25
Tried to update from Xubuntu Intrepid, by popping in the 9.04 disk, but that didn't work, did a clean install on a system with 384MB of RAM and a 1.1 GHz athlon processor. worked perfectly!

---

### Post by tneva82 on 2009-04-25
Installed it now from cd clean. Of course lost all the files :( Other than that went well but god what happened? It's noticably slower! Firefox is lagging. And my coding project went from ~450 FPS to ~320 FPS! 25% performance drop? WTF? And network speed suffers also which causes some serious lag.

Damn!

---

### Post by jigal on 2009-04-25
:guitar:
Decided to do an upgrade, though the system is upgraded since 7.10, so perhaps next time I'll do a clean install....

The issues I have saw are:
1. Jerky download - had to restart the update manager to continue 
   downloading - occasionally it got stuck.
2. Download completed in 2-3 days (I installed a lot of stuff, including
   KDE+Gnome...).
3. Upgrade occasionally asked me questions, which means that the rest 
   of the update didn't go.
4. And finally, probably for the last item installed, it said that 
   configuration has failed - and that the system is unstable.
   I ran update again - it mentioned the failed component (some stupid 
   game I never actually used) - and updated flawlessly.
   But this time - it was just a component update - not an ubuntu upgrade.
   which means that the upgrade has finished - though I didn't see/hear
   the bells & whistles... :confused:
5. Decided to restart - saw the changed graphics... - restart went ok,
   though once KDE started, it decide to switch to a lower resolution.
   And then, 2-3 minutes after logging in, it switched automatically to
   the higher resolution (XGA I think - 1280x1024).

All in all - keep up the excellent work - I am an ubuntu addict for more than 3 years... on my private pc & laptop, I never run windows at all.
Unfortunately, I need another pc & home, mostly for the wife (she refuses to switch to open-office), and games for the kids..

---

### Post by arashiko28 on 2009-04-25
After a 10 min installation, works like a charm
I have 64-bit, had some minor compatibilty issues, all solved except the aMSN issues with 64-bit.

---

### Post by LE CHARBON on 2009-04-25
Upgrade worked without a hitch. Though Tracker acted up. Found a fix on the forum to delete a couple of files and it solved the problem. This is so far the best upgrade for me.:KS

---

### Post by hzrunner on 2009-04-25
This is how far I get after the update:

Boot from (hd0,0) aa3a and more number..
Starting up ...

After 10 minutes or so the screen goes blank, that it, no more action.

Help please.

Okay, I manage to get things going again somewhat, but I still need help.

By pressing "Esc" during booting, I got to several startup options: The one that worked was the one with Kernel 2.6.27-11 generic (recovery) (..28-11 did not seem to work). When I got to the next selection screen, picking the "resume" option got me back to the now new Ubunto window.

I have to do this now every time I start the computer, which is obviously not really the idea, I guess.
Is there a way around this (I am fairly new to Ubuntu, so anyone who has any ideas, please keep it simple).

Thanks much in advance.

---

### Post by Philk on 2009-04-25
My attempt at upgrade stuttered to a stop with some recurring form of "repositories need updating" - couldn't break that.  My install from disk went very well.  One problem with the automatic re-partitioning for tri-booting (8.10, 9.04, WinXP Pro): the partition for 9.04 was so small (despite a 150GB drive with over 80GB free) that I had to use gparted-Live to shrink my 8.10 and enlarge 9.04 before I could install any extra software and updates!

I'm impressed with the x64 version, but I won't be staying on it for now.

I use BOINC to run SETI modules and the times I am seeing to run modules runs over twice as long.  The Astropulse tasks that take just over 100 hours on my 8.10 setup, say they will need over 200 hours apiece in my 9.04 setup.

I also very much like Google Earth.  I have an ATI-based PowerColor X1950Pro video card that needs the 3d acceleration driver to run GE.  I have that in 8.10; AMD is not supporting my card in the new kernel.

I don't think either of those problems is of Ubuntu's making, but I will pass on using Jaunty for the present.

---

### Post by evolx10 on 2009-04-25
Updated through Update-manager, took a while, but managed to install showing errors throughout, and gave me a gnome desktop -minus the panels, and var other little problems. i have not had problems like this since that other OS. Im impatient and im rdy to try a clean install of 9 and loose my data.

---

### Post by undfined on 2009-04-25
I did a fresh install on my Dell Inspiron 1420n and managed to get through my workday (usual printing, document viewing, web-surfing, intranet, etc all worked as they should).  Amarok didn't work (no sound) out of the box but adding libxine1-ffmpeg and the kdemultimedia packages fixed that.

I've been trying to upgrade my 64 bit "server" for the last 24 hours but the download is taking far too long so I'm just going to do a fresh install there.  Then my home office machine is next.

I love the New Wave theme and login screen, and there is a noticable speed improvement.  I'm likin' it.

---

### Post by hyperzahranism on 2009-04-25
Dear Memebers 

Regarding Upgrading to Jaunty -- i upgraded my 8.10 with update manager
& it went smoothly - but lately my NVIDIA is not working properly & 3rd party is turned off & i can't turn on now

altough i tried many ways to fix this problem but i couldn't

This was one of my trial to solve my problem 
[https://launchpad.net/ubuntu/jaunty/+source/nvidia-graphics-drivers-180/180.44-0ubuntu1](https://launchpad.net/ubuntu/jaunty/+source/nvidia-graphics-drivers-180/180.44-0ubuntu1)

the libGL is not created yet & i'm not familiar with terminal altough i tried but yet the problem still existing

& i don't know what miss i've done in the Terminal :-s

---

### Post by ubuntunewb75 on 2009-04-25
First Ubuntu install since 7.10 that I have kept.  Used Wubi from a Vista install.  Wubi rocks.  9.04 64bit rocks.  Clean, better memory usage.  Flash works.  Java works.  Nvidia works.  I haven't even needed to add an xkill icon to the panel yet.  It's done in  minutes what takes me a couple of hours to a day on a clean arch install (so far still one of my favorite distros).  Mmmmm...Ubuntu...

---

### Post by dobhar on 2009-04-25
Install went great...just had to setup the Broadcom Wireless driver...Nice!!!!! :KS

---

### Post by Messyhair42 on 2009-04-25
install went perfect, now i have to decide what to do with my other HDD w/8.10 on it. in the process of migrating documents and downloading programs. the one thing i havent been able to find however is how to change the setting while navigating folders of how to get folders to open with a single click instead of a double click, anybody?

---

### Post by cfchagas on 2009-04-25
Upgrading through Update Manager, but the installation is stopped for 24 hours at "Running post-installation trigger man-db". The last line on the terminal window below that message shows "Processing triggers for man-db ...". The machine seems to run well otherwise and I am able to share files normally over the network.
 
What do I do?

---

### Post by tzenes on 2009-04-25
I have a little story which I thought I'd share with the class.

So I decided to try and use the new distribution upgrade program, see how it works out.  So I ssh into my server, 
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
It gets as far as holding the hardware abstract layer and my ssh client dies.

Ok, that was fairly stupid of me.  So, I leave it over night and in the morning I go a head and drive over to where my server is located. Over the night the power went out and I have to restart my server when I get there.  Nothing works.  So, quick drive back to burn an extra update cd.  Except it won't recognize my cd drive...  Now sufficiently worried I get ready to do a fresh install, but before that I figure: "heck, let's try -f install"

Works like a charm.  Things finish installing themselves, the system starts to come back together.  Only one problem:

```
dependency problems prevent configuration of ubuntu-standard: 
ubuntu-standard depends on at; however:
```

Ok, let's try reinstalling at.

```
dpkg: error processing at (--configure): subprocess post-installation script returned error exit status 1
```

I finally trace it down to the init.d script for atd.  Aparently atd start is failing. More over I notice a really strange error message:

```
bash: /dev/null: Permission denied 
```

Bingo.

```
sudo rm /dev/null
sudo mknod -m 0666 /dev/null c 1 3
```

Now at reinstalls fine, as does ubuntu-standard.

Joy.

Except now I'm afraid to restart my box... oh well, here is hoping.

---

### Post by dislocated on 2009-04-25
New install, went just great. In fact, Ubuntu just keeps getting easier for me.

I'm using a Dell Inspiron 6400 with and ATI graphics card in it. Both the graphics card and the wireless worked without a hitch!

Many many thanks to all the people who put so much hard work into this release!

Also, I think that the poll at the top of this thread is perhaps a bit misleading since most people who install without problems will not be looking in this section of the forums and therefore not post their success.

Happy GNU/Linux-ing!

---

### Post by louieb on 2009-04-25
Worst upgrade since Edgy. 
Can't drag panels to new location.
Alt F2 does not bring up run dialog.
Title Bar missing on all windows - no min - max - restore buttons.
window preferences in control center mia 
Glipper disappeared.
Gkrellm disappeared too.
No telling what else just finished the upgrade abut 30 minutes ago. 

At least X and wireless network works. 

Going to play with it a bit to see if I can get it going but if not. 
Thank God I took a backup before staring the upgrade. 

IBM T30 laptop 2.2gHz , 1GB ram.

---

### Post by NathanDS101 on 2009-04-25
It froze on cleaning up had to force turn off and whenn i tried to boot ubuntu again had a problem so i uninstalled it so ya but know i have 9.04 so am happy :)

---

### Post by NathanDS101 on 2009-04-25
> **louieb said:**
> Worst upgrade since Edgy. 
Can't drag panels to new location.
Alt F2 does not bring up run dialog.
Title Bar missing on all windows - no min - max - restore buttons.
window preferences in control center mia 
Glipper disappeared.
Gkrellm disappeared too.
No telling what else just finished the upgrade abut 30 minutes ago. 

At least X and wireless network works. 

Going to play with it a bit to see if I can get it going but if not. 
Thank God I took a backup before staring the upgrade. 

IBM T30 laptop 2.2gHz , 1GB ram.

wow seriously thank god i didnt have those problems but that really suks...

---

### Post by mbeltagy on 2009-04-25
Upgrade went very smoothly. Thought when I restarted I got a much lower screen resolution that I had before on intripid. I could not go beyond 1440x900.. 

I used envyng to downgrade my nvidia graphics driver to 177, instead of the default 180, I rebooted and things are now just fine.

---

### Post by reivax89 on 2009-04-25
This was my worst upgrade : after rebooting, the computer was freezing when launching X.
I was thinking it was a mode issue since Xorg has now to find all available resolutions itself.
Finally it was an interaction with fglrx driver which I did not require since I have an intel video card.
[FONT=Courier New]aptitude purge xorg-driver-fglrx[/FONT] 
and all was working fine ! :)

---

### Post by ubuntunewb75 on 2009-04-25
This Ubuntu install turned me into a Newt!

---

### Post by jsonder on 2009-04-25
Trying to install using the final release live cd at our computer club has been a bust, in that 3/4ths of the computers shut down with a checksum error message.  

The live cd is 699 meg.  I'm suspicious that pre-spacing and such may be taking just enough room that the checksum isn't completely written to the cd when I burned it.  I tried burning with 2 machines and used both k3b and brasero for burning, but still got the checksum failure and arrested boot of the cd.

And, I've had no problems at home.  Go figure.

---

### Post by groovomata on 2009-04-25
I just did an install and it worked flawlessly, wireless, video drivers. I'm just now re-installing my favourite programs. 
Dell Inspiron 6400 laptop with an Nvidia 9300 video card.
Perfect.
Erik.

---

### Post by von Stalhein on 2009-04-25
That upgrade went fine - I told it to hang on to most of the configurations I'd set up in Ibex.

It was certainly easier than the last upgrade, where I borked the GRUB menu and it took ages to get it sorted again.

---

### Post by devlin7 on 2009-04-25
"**Did it worked flawlessly ?**"

The installer worked flawless

"**Did you got problems ?**"

I had problems with the changes made. disabling of crtl-alt-backspace... 
"because people were accidentally hitting it" seriously? I think these few should just learn from their mistakes or be doomed to kill their X server until they do.

Wanting to kill who had the great idea to make the system ask me for my password EVERY FREAKING TIME I want to connect to my secured wireless network. Even Windows isn't that annoying.

"**Did you manage to solve them ?**"

Yes, even thought I was considering just going back to UNR 8.04 which worked out of the box for me and wasn't annoying as hell. I figured I'd see if I could cure the problems.

"**if yes how ?**"

1. CTRL-ALT-Backspace not fixed yet... They need to correct the instrructions on re-enabling it. *It is going to screw with some noobs that are following the Official Ubuntu book(s) that mention this key  combo.*


2. As for the "Shutdown" problem it was easy. You'll see there are two a big one all the way on the right and a small one beside the user's name. The little one does what the large one should. I removed the large one from the panel and moved the user name w/ little button to the far right. All is better in my world....


3. Wireless conformation every time connecting to secure network - Yes, thanks to "Dave" of Dave's Tech Blog [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

To be honest, if I was a noob knowing nothing about Ubuntu, and how to search for fixes I would run back to Windows and tell of how annoying Ubuntu Netbook Remix 9.04 is. Luckly I've been with Ubuntu/Kubuntu since 5.10 and got loads of help mostly here on the forum as well as other places.

---

### Post by Noel96 on 2009-04-25
On one computer the installation of Jaunty was flawless. This was because no restricted drivers were involved.

On a second computer that needed a NVIDIA graphics driver, I had to use synaptic package manager to load the driver. It turned out that a file was needed from the installation CD. The usual process of activating restricted drivers could not pick this up.

Overall, though, a great OS!

---

### Post by kerryhall on 2009-04-25
Upgraded to 9.04

On boot, dropped to busybox.

Got the following errors:

*No block devices found
*Gave up waiting for root device
*Alert! Can't find /dev/mapper/nvidia_cajdbccj2

---

### Post by larryboythedog on 2009-04-25
Upgrade went flawlessly on my  old dell 600m, even during a thunderstorm with 2 dropped internet connections. All the fetched packages had been cached. "Latest,greatest,uptodate-est"

---

### Post by dragondrop on 2009-04-25
Updated to 9.04 from 8.10 and the proprietary nvidia driver broke again, same as earlier versions.Thought they'd fixed this issue by now. It gave me a bundle of error messages about xorg already running, cannot find monitor :0. Impressively, the GUI managed to start (800x600) so I was able to troubleshoot. It claimed that no nvidia driver was installed. Tried to install/configure manually with no luck. Had to make a clean installation. Now......if I just can get Elisa working again....

---

### Post by Feelin_froggy8877 on 2009-04-25
Attempted with the update manager...Everything seemed good to go, until I rebooted. There was some kind of problem with the gnome panel. Would not display the menu and just could'nt do anything with it all together. tried adding a panel and that just made things worse. Rebooted after that and it would boot to the desktop but kinda went into a freeze state. Possibly had something to do with the way I customized the panel...not really sure. Uninstalled from within windows, downloaded the new iso and did a clean install...Everything is going great now...(knock on wood)

---

### Post by GerryDG on 2009-04-25
Going back to 8.10. 
 
 Spent 2 days trying to get 9.04 working with ATI drivers.
 
 OpenGL is slugish, can't set proper resolution, hangs, can't logout, etc.
 
 Tried Ubuntu32, Ubuntu64 and Kubuntu.
 
 Disappointed.

---

### Post by Feelin_froggy8877 on 2009-04-25
Attempted with the update manager...Everything seemed good to go, (even though it actually took everybit of 15 hours on cable) until I rebooted. There was some kind of problem with the gnome panel. Would not display the menu and just could'nt do anything with it all together. tried adding a panel and that just made things worse. Rebooted after that and it would boot to the desktop but kinda went into a freeze state. Possibly had something to do with the way I customized the panel...not really sure. Uninstalled from within windows, downloaded the new iso and did a clean install...Everything is going great now...(knock on wood)


Sorry for the double post.

---

### Post by addiebk on 2009-04-25
Fresh install-- everything works perfectly.

The only disappointment was Amarok 2...  I'll probably use Banshee until Amarok gets all of its features back.

---

### Post by Tanker Bob on 2009-04-25
Upgraded from Intrepid to Jaunty. I'd played with the betas and RC in a virtual machine so didn't expect any issues. My system specs are in the sig below.

I used Update Manager last night and the download took about 2 hours, the install about another 25 minutes. When it was done, I rebooted and the system came back with no problems. It preserved my entire setup, including my RAID1 configuration, the proprietary NVidia drivers, lmsensors and the sensors applet, my Epson scanner (which required fixing in Intrepid), and my custom screen and compiz-fusion settings. Except for the new version additions, I wouldn't have known that I upgraded - perfectly smooth.

When I tried to run VMWare Workstation the first time after upgrade, a graphic tool popped up, compiled and activated the VMWare kernel modules. After that, Workstation worked perfectly. I didn't have to intervene at all. I did have to reboot to solve a slowdown in file access after the VMWare compilation, but everything worked perfectly after a restart.

The only real issue was having to reinstall Flash for Firefox after the upgrade. That proved trivial.

I documented my upgrade experience in more detail [here](http://reformedmusings.wordpress.com/2009/04/25/upgrading-from-ubuntu-810-intrepid-to-904-jaunty/). This has been the smoothest upgrade experience I've ever had on any operating system. Great job by the Ubuntu team! =D>=D>=D>

---

### Post by DustyMP on 2009-04-25
Upgraded both a notebook and desktop today from Intrepid. Only had an issue with a wireless presenter no longer working but wrapped a Windows driver and have it back. When I attempted the upgrade yesterday the download speeds were ridiculously slow but I think it may just have been all the traffic from everyone trying to upgrade at the same time.

---

### Post by Merovius on 2009-04-25
Upgraded with an alternate install CD. Update manager is acting a little weird with partial updates crashing without finishing. Figure time will fix that. GRAMPS genealogy program had to be updated to a newer version also.

Other then that, it has gone almost perfectly. Noticeably faster also.

BRAVO! \\:D/

---

### Post by cutterjohn on 2009-04-25
Distribution Upgrade through Update Manager hung after downloading all packages requiring a cancel, then rerun at which point it worked OK. Easiest Ubuntu upgrade for me yet, so distro upgrade through the GUI is slowly but surely progressing.

[EDIT]
Upgraded from 8.10 x86-64 with Catalyst 9.4 drivers already installed.  MSI GT725-074US (P8600/4GB DDR2 800/4850 512MB GDDR3/WD black 320GB/1680x1050).

(Upgrade was WAY WAY WAY better than 8.10 initial install which required all sorts of blast from the past fun, alternate install CD, manual text configuration file tinkering, building drivers(cats), just to get X11 up.  (Having to bootstrap gcc and then build X11 was worse, but that was a LONG time ago and it worked in 4MB...))
[/EDIT]

---

### Post by DaveAU on 2009-04-25
Upgraded today with much fear.  I started using Ubuntu with Fiesty, and had catastrophic upgrade problems moving to Gutsy and Hardy.  Because of that I did a clean install for Intrepid and only had to spend a day or so tweaking things.

The upgrade went pretty much flawlessly.  I had to change some settings to get my trackball to work - but that was due to Jaunty fixing a bug that my old setup was working around - and a package or two have introduced bugs, but very pleased with the result.

The last couple of upgrades I did were disappointing.  Watching a fair few people give up on Ubuntu because of the initramfs/busybox issue(s) that's been around since the Dapper days was even more disappointing (although it looks like it's getting more attention now).  Between those two things I was worried that Ubuntu might be collapsing under the weight of the new users, which made me a little reluctant to try to help out.

I'm all optimistic again now, so I'm planning on carving out a nice new partition so I can help test Karmic when it gets going.

---

### Post by Owlyn on 2009-04-25
My experience was not all that good.  I have a 64 bit version of Intrepid on my Dell Inspiron 530 that is working well.  I installed the 64 bit version of Jaunty on another partition on the same PC and it was just slow opening windows and resizing windows.  I suspect it is the quality of the proprietary ATI driver, but that is just a guess.  I decided to install 32 bit Jaunty over it to see if that would make a difference, but the results were the same.  Opening and dragging windows is slow.  This seems counter to many other people's experience.  All of my installs were fresh installs.  The nice thing is that I still have a working version of Intrepid on the PC that I am happy with.  Note, I've used all versions of Ubuntu since Gutsy and never had any problems I couldnt' work out, so I'm puzzled by this.  I will probably tinker with it a little more, but probably some future update will fix the problem.  There were other problems too, but not the usual ones.  For example, I had no problem getting Flash to work on both 64bit and the 32bit installs.  VLC Player, for example, performs very poorly on Jaunty when in PVR mode to watch TV.  And there were other odd things and few freezes that required me to unplug my computer to restart it.  Usually I wait a few months before installing a new release, and I guess I should have done that in this case.  But, I still love Ubuntu!

---

### Post by robtg on 2009-04-25
Clean install.  I left Ubuntu after displayconfig-gtk was removed from the distribution; at that time and since then, Ubuntu can't detect my screen resolution properly.  I thought I'd give Jaunty a try but still no luck; my laptop is hopelessly stuck on 800x600.  So, I've gone back to Pardus.   Why displayconfig-gtk was removed from the distribution I'll never ever know.:confused:

---

### Post by mitchellcipriano on 2009-04-25
My experience was good. I had a couple of minor problems, one with racker and another with a libdb-java package. All is fixed now. The upgrade fixed my suspend issue. Overall I am very pleased.

---

### Post by inxygnuu on 2009-04-25
Wonderful!:KS Everything worked better than expected, and was flawless!

---

### Post by sieve on 2009-04-25
System: Thinkpad t43.  ATI Mobility Raedon X300 graphics card

*Did it worked flawlessly ? Yes.  Used Update manager.  Took a few hours.
*Did you got problems ? None yet.  
*Did you manage to solve them ? N/A
*if yes how ? N/A

I originally started the update on Thursday but immediately had the message that my ATI fglrx graphics card drivers would not work with 9.04.  So I aborted the upgrade.


I was initially reluctant to go away from the ATI drivers because my screen used to lock up in 8.10 until I installed the ATI driver.  After installing the ATI drivers - no more problems.  But I did some reading and found that the open source drivers had been improved for 9.04.


To test the theory, I burned a bootable 9.04 CD and used that a bit and had no issues.

So I uninstalled the ATI driver and went with the open source driver.  Then did the upgrade.  So far so good.

---

### Post by Kakteed on 2009-04-25
So far, it's been a really mixed bag. I like the new notifications, and I like that I can now use compiz - it never worked for me in Intrepid (nor did desktop effects), but it works beautifully with Jaunty. It's amusing, actually, since I have an ATI Radeon X1650, so you'd think that I would have had the opposite experience.

I did have some big problems initially, but they were almost all caused by my own stupidity; some fooling around with xorg.conf and menu.lst fixed all of the big issues.

My problem now is that there are random programs that won't start, or that consistently misbehave. I'm sure that most of it is stuff that I've done, but it's really pretty frustrating. The two that are the most frustrating are Pidgin and Amarok - Pigin won't start at all, and Amarok will only start once I've killed one of the processes (it opens two processes?). I tried running Pidgin through terminal and got this: "(pidgin:24465): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed", so at least I have something to go on. Oh, and I also can't open some of the things under "system/preferences" - sound, for example, doesn't open.

It's really frustrating that almost everything is requiring some tweaking, though. I've already spent a day and a half trying to make things work, and I predict that it'll take me another week or two to get *everything* working.

I should learn my lesson about immediately upgrading, but I can never resist the temptation.

---

### Post by danian88 on 2009-04-25
It was awful!  I just tried upgrading from Ubuntu 8.10 amd64 and my computer froze during the process of installing the upgrade. :(  The computer would stop working at the login screen every time I did a reboot.

I had all my important stuff backed up, though, so I ended up doing a clean install...  Overall, it's been great and I'm glad I did it! :D

---

### Post by reswob on 2009-04-25
Wow, was this upgrade bad.

I've used Ubuntu since 7.04 and I haven't had any problems upgrading since.

But this upgrade from 8.04 to 9.04 went horribly.  I've posted elsewhere, but not yet gotten a solution for why nautilus doesn't work.  One casualty already is all my email is gone.  I thought I backed it up, but I didn't.


Wow.  Wow.  BAD.

---

### Post by pjhudson on 2009-04-25
unfortunately my linux experiment has ended for now as a result of attempting to upgrade to 9.04 from 8.10. :( The upgrade just didn't work, I could never get it to successfully boot and now I don't trust Jaunty enough to do a clean install while wanting to keep my windows partition.

I'm using a fairly new Toshiba laptop with windows vista installed and a dual-boot into ubuntu which worked alright, apart from annoying wireless driver problems that crept up every once in a while...  all in all, ubuntu version 8.04 was a decent experience if not educating, at least, and I enjoyed the different features of ubuntu :P ...  but the novelty of using a free os has worn off and I've realized that linux just won't work for me as a "#1" os because of the following:

1- It's too time consuming and difficult to install some applications (although linux has made strides in recent years)-  while I enjoy typing in code to a certain extent, I really just don't have the patience or time to screw around with it all that much. 

2- When a driver breaks or crashes, it requires an enormous amount of forum searching and code executing to get it working again, not a fun experience and it just doesn't interest me.

3- There seems to be a real lack of support for applications that I use daily or frequently-- such as itunes and the itunes store where I buy all of my music, photoshop/ illustrator (gimp is cool and free is awesome, but not in the same class as photoshop), not to mention the funky/ buggy "wannabe" versions of apps such as google earth, real player, skype, which make me feel like I'm using something in safe mode compared to the windows versions.

4-  Trying to get the bluetooth to connect to my mobile phone and use it as a modem proved too complicated and way over my head-- (it was extremely easy in vista and I use it all the time when I'm away from a wireless connection)
Anyhow, I'll probably try Ubuntu again in 6 months or so, but to be honest, it's not yet a truly viable option for your average windows user who really does want to get out of windows.

---

### Post by zaiboot on 2009-04-26
I have not been able to load the live CD, in my desktop, but in my laptop works fine. Only the touch pad does not work.

Thank you and keep the good work.

=D>=D>=D>

---

### Post by farhill on 2009-04-26
Fairly smooth for me, amd64 Toshiba L305D-S5874 with KDE (although not originally kubuntu) 

X crashed somewhere late in the upgrade process but a dpkg --configure -a in the console seems to have taken care of things. The text mode console suddenly appearing would have been a major issue for a newbie.

Needed to re-add the network manager applet, as documented in the release notes

---

### Post by eatloaf on 2009-04-26
Complete failure.

First, I tried to upgrade.  I came back a few hours later to a blank desktop.  Rebooted to a failed start, fschk failed on my drobo ( /dev/sdg ), bad superblock or something.  There is nothing wrong with the drive. Launching 9.04 from the CD mounts and accesses the drive correctly.

Second, tried a clean install.  After the reboot I came back to a terminal screen of a stack dump. Rebooted and Gnome launched, except trying to run any application sends me back to the login screen.

Disappointed, going back to 8.10 indefinitely.

---

### Post by ram4nd on 2009-04-26
My ati xpress 200 mobile is 10 times slower.

---

### Post by WE0H on 2009-04-26
9.04 works like crap after running for a hour or so. Kept logging off by itself and wouldn't accept the correct username & password. Now I am doing a fresh 8.10 install. Have to check back in a month to see if 9.04 is fixed.

Mike

---

### Post by noushii on 2009-04-26
Upgraded from 8.10

This upgrade is a nightmare, many many bugs to fix and no time to beta test for you guys -.-

---

### Post by telmac on 2009-04-26
cannot burn properly on vista need help, tried transferring thru flashdrive, would not mount .iso optical drive on my ubuntu 8.10 machine will not respond to blank discs.

---

### Post by Another Monkey on 2009-04-26
Have few issues with the Jaunty upgrade (two systems) - bad enough to make seriously consider reverting to 8.10.

[LIST=1]
[*]compiz support dropped without warning during upgrade - OK, my bad, I should have checked the Release Notes, but Update Manager doesn't seem to let you view them (or I am so blind I didn't see the button)
[*]Samba no longer fully functional - cannot browse Windows network
[*]Lost usplash screens - fixed by upping video memory in BIOS from 1mb to 8mb (no idea why that should be required).
[*]Had a request during upgrade to run "liloconfig(8 )" - tryig to figure out how to do this as "liloconfig" throws up a warning message and then exits.  I'm not even sure what "lilo" is.
[/LIST]

Item 2 is the major show stopper for me.  I can find loads of references to the problem in the release candidate and it seems it is still there in the final version.  I can use "smb://blah-de-blah/" in the address bar of Nautilus and that works, it's just trying to browse or access the workgroup/domain that fails.  This affects both boxes I upgraded and, as such, I'm leaving everything else on 8.10 until I figure out what the answer is.

At the moment my opinion of Jaunty is less than favourable.

---

### Post by butnmashr on 2009-04-26
I installed Intrepid in December on my old ex-state POS Dell with a rambus set, 2GHz P4, nVidia GeForce 4, and a hard drive out of my even older HP, which previously had been running WinME, "running" being a very kind word for this computer. From that first reboot I knew that Ubuntu was the most awesome.

And this upgrade was in the same vein of awesome. No sound problems. No boot problems. I'm playing Counterstrike quite fluidly, which, honestly, is where i come to my conclusions... No regressions I've encountered yet. I kept ext3, maybe that's why my experience was much more positive than alot of the others... I also kept my original config file... Or maybe it's because this computer's too old and crappy to be affected heavily. I don't know. Yet. Learning more every day...

I love Ubuntu. I can't wait to contribute more to this.

Sorry for stretching the point...

---

### Post by NotTheMessiah on 2009-04-26
Clean installations on netbook(wind U100  -ext4) and my old laptop(ext3). Zero issues so far - a lot of nice little touches in jaunty. it seems faster/snappier and more polished. Liking it a lot :)

---

### Post by IainPurdie on 2009-04-26
Updated through Update Manager from Intrepid 8.10. Took about 40 hours - I guess because the entire world was trying to do the same thing!

Had to manually re-enable and update several of my Software Sources afterwards

Performance seems worse than in 8.10 and I *think* it's graphics-related. I run an Acer Travelmate 2410 with an Intel 900 chip and I've notices Intel graphics seem to be an issue. When running some apps (WINE, System/Preferences/Display for example) I get corruption of the bottom 1/3 to 1/2 of the screen as they load. Fine once up, though.

Using MPlayer in fullscreen, when I go down the screen to point at the controls, the entire windows flickers so I can see the desktop background momentarily.

Flipping desktops, opening windows etc - anything involving a large graphics change - makes MP3s or streamed audio skip. This didn't happen under 8.10 or 8.04.

System/Admin/System Testing fails to load - I've seen this mentioned elsewhere as well

And there's no utility I can spot for controlling the new pop-up notifications. I believe this was present in the beta and RC but seems to have vanished in the release version!

---

### Post by jigsaws on 2009-04-26
It was first Ubuntu upgrade without any problems to solve. Everything is working ok. Maybe one small thing - I have now smaller fonts in Lotus Notes 8.5.

---

### Post by bjfs on 2009-04-26
Here's my experience, took a couple of hours.

The box: Fujitsu Siemens Computer Amilo Si 1520

It has strong integration with Windows Vista so I picked the dual-boot option with Wubi.

Here are my extended notes on the whole process (no timestamps, heh):

> 
0. Backed up old files with tbz2, the /etc and my home directory, uninstalled 8.10 (with 10Gb disk space)

1. Installed 9.04 by Wubi (with 15Gb disk space this time)

2. Boot by Windows Boot Loader, to not complicate things I have disabled quiet and splash options in GRUB interface...

3. Installed ChatZilla, you know, IRC never dies.

4. System reminded me of i18n, installation successful. Used IME (whatever that is). Relogged.

5. Looks like keyboard support is b0rked, shift with number keys appears... shifted (imagine that). Fighting with SCIM (whatever that is). Ok, Gnome defaults to Italian layout for no apparent reason. Now some apps work right, some not. Geez, complicated stuff.

6. Make a break with keyboard, at least I can type alphanumeric chars right.

7. Install Ubuntu Studio stuff. Had to resize Synaptic window to see the search icon. Ok, let us install ubuntustudio desktop. No screenshot, not supported by Canonical. Supported by community. Yeah, right. Looks like we will boot again with actually working RT kernel.

8. Boot anew...

9. Okay, so there are only RT kernel headers by default. At least the keyboard works right this time. Didn't modify GRUB options at this time (so we have splash and quiet). Whoah, amazing login screen. The default Ubuntu Studio login sound is even creepier than the one provided with Ubuntu, Let's turn it off ;P

10. And turn off the logout sound too. Maximum volume makes my ears unhappy.

11. Let's install linux-image-rt (no screenshot with that on Synaptic again, how sad) , maybe my box will not explode !

12. Boot anew... (Synaptic tells me to do so)

13. Okay, RT is not the default kernel so let's pick it up. Nothing blows up this time.

14. Let's start Gnome Terminal. Changing colors to retro-hackish green on black.
Little CLI Kung-Fu:
bjfs@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009 i686 GNU/Linux

15. Okay, so it works. Will play with MIDI later on...

Time to self-sign as an Ubuntero ;-P

16. But before that happens I have to install some extra non-community stuff. First, the Kadu. IM client from Poland. They have version for Jaunty Jackalope already. Following the installation instructions. Since Kadu (like most K's) use Qt then we download that Trolltech stuff.

17. Meanwhile can't connect with Google. But DMOZ works. Can't remember why I wanted to do this so let's try Google again. Works this time.

18. Now I know, I have to reclaim my password to Ubuntu Forums and won't use reminder again (used reminder after registering, good memory bad). We are using KeePass for this.

Last time I did this was with some weird .NET "emulatation" (or whatever that is) by so-called mono.
But let's see if there's some sort of KeePass in the reps...

bjfs@ubuntu:~$ aptitude search keepass
p   keepassx                        - Cross Platform Password Manager

Hmm...

19, Let's add another row and column in virtual desktop. Man this feature is missed on Windows.

20. Going back to KeePassX. Looks like I can't browse C:\Documents and Settings\ and I have no idea how to fix it (maybe something wiped out my entire personal data ? oh well).

21. Let's forget about that, using password reminder ;-P



So apart from fighting with the alien NTFS  everything appears to work fine. At least not worse than on Interpid Ibex.

---

### Post by Tristan_F on 2009-04-26
As usual upgrade with adept corrupted my Xserver. I had a conflict between xserver-xorg-core and xserver-xorg-video4. I was not able to do anything except boot with revoery mode. 

I finally decided to make a fresh install which works.

I have a sony VAIO FW21-E with a Radeon HD 3400 card.

---

### Post by jerha202 on 2009-04-26
My setup:
Windows XP, Intel Pentium 4 2.4GHz, 1.5GB RAM
Hard disks: Seagate Barracuda 7200.10 250GB, Seagade Barracuda 7200.7 80GB
DVD/CD: Lite-On DVDRW LH-20A1P
Graphics: ATI Radeon HD 2600 Series; screen resolution 1680x1050
Sound: C-Media Wave Device

[LIST=1]
[*]Booted up the kubuntu-9.04 cd and chose "Try kubuntu without any change to your computer". After the progress bar completed, I got a kubuntu background screen, a mouse cursor and an icon that looked like a hard disk, then the computer froze.
[*]Started the kubuntu wubi installer from within Windows. Installer crashed because I changed installation language from Swedish to English.
[*]Tried wubi again with Swedish and completed installation. After reboot and the completion of the progress bar, the screen turned black and the computer froze.
[*]Booted up the ubuntu-9.04 cd and chose "Try ubuntu without any change to your computer". Again, after the progress bar, the screen turned black and the computer froze.
[*]Booted up the ubuntu cd again and chose "Install ubuntu". After the progress bar, I got an ubuntu background screen and a mouse cursor, then the computer froze.
[*]Started the ubuntu wubi installer from Windows (using default language). After installation and reboot, I came as far as an ubuntu background screen and a small window with a progress bar "Checking installation". At 28%, the computer froze.
[*]Tried all the other boot menu options of the wubi installation, but in all cases, the computer froze at some occasion during startup.
[*]Finally, I tried booting up both the ubuntu and the kubuntu cd in a Microsoft Virtual PC 2007. After choosing any boot option, a long list of error messages was printed to the screen, and then the virtual computer froze.
[/LIST]

---

### Post by alicemoon on 2009-04-26
Just did 2 upgrades - both went well and have not experienced any problems so I am very pleased

---

### Post by corsairgt on 2009-04-26
I've installed v9.04 on a 16 GB USB flash drive. However, I could not save anything (updates, configuration or new software) on the drive after reboot or shutdown.

Does anyone know why?

---

### Post by sbcontt on 2009-04-26
I followed general procedure of upgrade, but still the updater tried to update third party programs such as mplayer & failed to get repositories :( . I had copied all the messages, but ...copy & paste always fails in ubuntu so I lost it.

---

### Post by Convert on 2009-04-26
> **ivan-frankfurt said:**
> Upgrade from Kubuntu 8.04

Relatively smooth, but two problems I am still working to solve:

2) No menu bar in KDE. I have to start all apps from a console for now.

Sorry but I would not call having to run apps from the console to be a "relatively smooth" upgrade.  To a typical Windows user, this kind of problem would be a show stopper and would turn them off from Linux.

---

### Post by mgscano on 2009-04-26
> **frodon said:**
> The purpose of this thread is to share your experience installing/upgrading Jaunty Jackalope.[...]

Well, I got a bunch of Ubuntu VMs:
1) the gnome desktop version upgraded flawlessy and smooth as velvet;

2) all the others are LAMP server versions. Same result for do-release-upgrade: no new release found.

I will investigate the forums to see if there's something do-able :-)

bye

---

### Post by RedStickHam on 2009-04-26
Yesterday, April 25, 2009, I used Synaptic to upgrade from Ubuntu 8.10 to 9.04.  It took around 4 hours due to slow download times, probably due to overworked servers. 

My system:
Homebuilt Asus motherboard
AMD Sempron 2300 1.583ghz CPU
1.5 GB RAM
On board sound, VIA-8235 chipset
On board NIC, also VIA chipset
NVIDIA GeFORCE FX-5500 128mb video
Acer Flatscreen monitor

One problem I had was getting the proprietary NVidia driver version 173 to load.  I tried a tip I found for a previous version of Ubuntu, and downloaded the EnvyNG tool for loading Nvidia and ATI drivers and after rebooting, it worked.

Another problem, which I've already asked about in another posting, is when I checked for updates, I was told I could only get a partial update and was told this would be done if I took that option:

Remove libd4.5-java
install libass1
install libd4.6-java
install libd4.6-java
install libd4.6-java-gcj
install libdca0
install liblrdf0
install libmodplug0c2
upgrade liblucene2-java

When I did that, update manager closed and nothing happened.  Not sure what is causing this.  I posted another thread about it and hope to find out soon what to do.

Other than that, so far it appears to be running smooth.  I like the fact the upgrade kept all of my old settings, including using the Firefox and Thunderbird profiles from the WindowsXP side of my dual boot system.

Ubuntu 9.04 boots up quicker and seems to run better than 8.10, which is nice.  If other problems come up, I'll post about them.

RedStickHam

---

### Post by drbuggs on 2009-04-26
After ugrade from 8.10 to 9.04 My computer absolutely refuses to pull an IP adress by DHCp, tried setting static ip-adress but guess old network amnager bug is there still so no good, then tried disbaling profile in apparmor, no good.

Also as the computer has no Ip adress Gnome never finishes with loggin so network manager is not available. / Could wait a few hours i guess and see if gnome logs in, but did not finish in 8 hours)

Gonna try uninstalling network amanger next:(:(

***_Update :_***

"sudo dpkg --configure -a" fixed gnome

***_Update 2_***

Disabling, rebooting, then Endabling Network on Motherboard in Bios fixed network.

---

### Post by Claus7 on 2009-04-26
Dear ubuntu developers and ubuntu users,

first of all I would like to congratulate the former on their effort to produce the "newest member of our alliterative menagerie" fully operational and functional, as they refer to every new version in the fringe. 

Judging from the poll results up to now, I can see than in general the migration from previous versions or the installation from scratch was not as easy as it could have been. The new machines have a profound advantage, whereas the old machines either suffer from new shortcomings or the old seem to remain.

Just to make myself clearer. My intention is not to show the good aspects of the new version. Not for any other reason, yet my intention is to point to the negative aspects, according to my humble experience, so as doing that way to point to the direction of their solution. As a result I think obvious that: this is my personal point of view, thus completely subjective.

Ubuntu is clear that is taking a more "windowish" style. It wants to become more appealing to users that they are not so accustomed(familiar) to the terminal and continue to be the most friendly choice of an os that is based on linux engine. Having said that the graphical environment is one that many os would jealous (e.g. compiz, volume control preferences e.t.c.). The choices have increased so much and the complexity is so high, that sometimes is difficult to be able to find the way to adjust the os to ones needs (alsa or pulse anyone?).

My opinion is that some tools that they were working decently, should not be abandoned. For example the configuration of the graphical environment is not working any more. So either the graphics driver will work out of the box or it will require a tremendous effort in order for someone to have good results. 

Maybe I'm wrong, yet no matter how simplified linux might become, the philosophy behind it will remain the one it was, is and I think it will be: unix/linux. I cannot imagine linux without terminal. Configuring my system from graphical environments, I feel that I'm loosing part of my "power" without being able to control my system as I used to do. In addition to all these I feel a little bit out of date, watching things that they were working, now not to work any more. 

I could write even more things. I think that my point is clear enough. Ubuntu keep changing, without forgetting your old users though.

Forgive me if I'm a little bit off subject, yet this was the "taste" I got from the new version. Without a doubt, I think that these things will be fixed in the versions to come and I also think that these problems arised because Ubuntu, with this version wanted to take a huge step forward. I have the impression that this version is one that got a lot of attention, even without being a LTS one.   

Just a small reference to the issues I found difficult in the newest version:
-ipv6 caused a lot of headaches. Even though the latest protocol in its category, yet it seems that it hasn't succeeded fully the ipv4 one
-nvidia settings was once again a difficult process for one to configure if one has not one of the latest graphics cards
-pulse and alsa at the same time was too complicated
-flashplayer, even one click away, didn't seem to work as expected

Having said that, it is nice that we have more support on hardware devices than before, newest version of libraries that enable people to do even more things and an ubuntu community that will be there, when the need comes.

My kindest regards to anyone,
Claus7

---

### Post by GrumpyBob on 2009-04-26
Four upgrades from 8.10:
IBM Thinkpad R52 - flawless upgrade
Sony Vaio TX5XN - flawless upgrade
Two desktop PCs of various vintages and modifications - both upgraded flawlessly

I used the usual route of distribution upgrade following the prompt from Update Manager.  I could only vote once in the poll!

Robert

---

### Post by mckelly46 on 2009-04-26
Install went great on four machines - an old P4 desktop, an Acer 8104 laptop, an Toshiba Celeron laptop and a MSI Wind. Only two issues so far.

[LIST=1]
[*]Gramps needs desperately to be upgraded to version 1.1 so we can see all the forms on a netbook (I use a MSI Wind). Right now if we fill in data, we can't see the "Save" button and so we can't save data.

[*]Virtual Machine (installed on the Acer 8104) is great but it doesn't see the USB ports.
[/LIST]


BTW, nice job on the netbook interface.

Cheers,

---

### Post by oldHat on 2009-04-26
Upgrade failed.  

Installer got stuck on "ca-certificates" and gave up.  Rollback left things somewhere between Intrepid and Jaunty, pretty much crippled.  Networking was totally fubar.  

Glad I had put /home on a separate filesystem.  I simply wiped my root partition then did a fresh install from CD.  Fast, simple, easy, no issues.  It even found my "spare" root partition and configured it in grub for me.  Now, I'm reinstalling the stuff that wasn't installed from the CD.  

My only criticism is that I found the partition editor confusing to use, even though I have done several installs and upgrades in the past.  No mishaps, but still not particularly intuitive.

Boot-up to the login screen takes 30 seconds, not too shabby, but then it takes another 30 seconds to login.  The ATI driver installed by the hardware drivers menu seems to perform (based on glxgears) about the same as the latest Catalyst driver from the ATI site.

Xine codecs doesn't seem to work properly with Compiz enabled (libxine1-ffmpeg?).  I can't be sure that is a new problem because I haven't used Compiz in the past.

---

### Post by bgs100 on 2009-04-26
Whoops
I meant to pick "Install - worked but had few things to fix, nothing serious though "
Put accidentally picked "Upgrade - worked but had few things to fix, nothing serious though "
I did a fresh install, as it's usually cleaner.
My only problem was not expecting Subpixel smoothing (and turning it off) and was fixing the refresh rate which was at 50 for some reason

---

### Post by chandra on 2009-04-26
The upgrade from Kubuntu Intrepid to Kubuntu Jaunty on an AMD 64 Gigabyte GA-MA78GM-S2H mobo went off flawlessly. I was even prompted that a new release was available so that I could initiate it.

Some teething problems with KDE 4.2 on Intrepid were ironed out with KDE 4.2.2 in Jaunty.

The upgrade script was smart enough to detect my local repo run by my ISP and simply changed the lines with intrepid to jaunty while disabling third-party repos in my /etc/apt/sources.list file.

I only needed to re-activate the virtualbox and medibuntu repos and all was set.

This is the most flawless upgrade ever since I started using Kubuntu with Hoary.

Kudos to the K/Ubuntu team.

---

### Post by simpleC11 on 2009-04-26
So I took my chance upgrading...and it worked flawlessly!...and I still have everything. It's a bit slow, but I'm sure that won't last!

It's actually working better than 8.10. It actually notices that I have a button to turn on wireless when I press it. I had to use a USB with 8.10.

---

### Post by schloss on 2009-04-26
Very few issues with my upgrade. In fact I found that a few things that didn't work (but should have) under Intrepid, i.e. the menu editor, are fixed so they work (again). Intrepid wouldn't recognize my bluetooth, though, and Jaunty still won't (on a Thinkpad T41). Maybe it's a problem with my drivers, though I do recall seeing a discussion of this being one of the issues with Intrepid that was going to get fixed in Jaunty.

Also things seem a bit more sluggish under Jaunty than under Intrepid. I know my machine's going on 5 years old, and maybe it's just time for me to add some RAM, but I was able to use extra compositing effects under Intrepid and things were still pretty snappy (and snazzy). Now I have compositing set to normal and things tend to hesitate. A lot.

---

### Post by manusharma on 2009-04-26
I am definitely having some issues with the upgrade from 8.10.  Most notable is that Evolution is no longer functional, which is a real drag.  I haven't been able to find a fix yet, so I won't post any details here. 

An additional comment on the upgrade process is that one should be able to upgrade from one LTS to another LTS (e.g. 8.04 to 9.04) directly.  Otherwise it feels like one got suckered down a deadend of sorts.  

Other than that, it seems to be working.  Thanks to the development team for their continued effort.

---

### Post by Rulls on 2009-04-26
Pretty rough go with 9.04 so far.  Most ragged experience of installation and use of the last four Ubuntu/Kubuntu releases (normally things go quite smoothly).

Installer operation was without incident (though I'm disappointed in new design of the disk partitioner interface) until restart of the system after completion of the system setup.  System froze during post-install shutdown; had to brute force a shutdown.  Now, the system won't shut down normally.

Also, multiple problems with multimedia.  I've followed the instructions for enabling restricted formats and DVD playback.  DVD seems to be working fine, but still working through audio CD recognition/playback and Flash Player audio problems within Firefox.

One large step backwards in my own experience with (K)Ubuntu.  Will work through the problems, but it makes it hard for me to promote Ubuntu to my Windows user colleagues as I would normally be inclined to do.

---

### Post by C.S.Cameron on 2009-04-26
Th last time I tried an upgrade, I recall, was with Feisty. I swore I would never try one again and have since used seperate home partitions along with fresh installs.
As things have been improving with Ubuntu at a tremendous rate I decided to try again with Jaunty.
First I upgraded a thumbdrive that was running 8.10. This was surprisingly quick and worked flawlessly. Next was my daughters computer with D201GLY2 motherboard. This has a dreaded SIS662 graphics controller. I ended up with a new xorg.conf so I had to replace driver "sis" under device. otherwise no problem.
My son's computer computer took a bit longer as it still had 8.04 on it. I upgraded it first to 8.10 which took a while, then to 9.04 which again went quickly and without problems.
Now that I have confidence I am about to upgrade my laptop, then when I am absolutely sure it is foolproof I will do my wife's.

---

### Post by GregDT on 2009-04-26
Upgraded from 8.10 with the nvidia drivers and an Nvidia 8600GT
After a few minutes the screen locks and requires a reboot.
This also happened to my 8.10 upgrade. Disabled the nvidia drivers with no improvement. Turned of compiz and screen effects with no improvement.
Went back to 8.04 which works flawlessly.

---

### Post by Chesh on 2009-04-26
I've had some bad luck with Jaunty. I first tried an update, but it ended up hanging and I ended up doing a fresh install. The actual install process is faster and the boot times are excellent, Im just running into a lot of odd little quirks that are really annoying. 

Jockey crashes when I attempt to install the restricted drivers, no fix yet.
Aptitude will randomly seg fault, fixed by removing cache files.
Pidgin crashes randomly.
System often hangs on reboot.
Disk checking fails and has to be performed manually.
Fonts on Sun stuff OO, Virtualbox are way too big for whatever reason.

So baisically a lot of strange trivial tiny bugs that are just enough to make life annoying.

---

### Post by Sprut1 on 2009-04-26
I voted upgrade but should have been:
"Install - worked but had few things to fix, nothing serious though"

First of all, when installing I had to use an external monitor because the resolution was to big for my laptop so I couldn't see what was going on. Then when I first booted to fresh Ubuntu the screen resolution was to high so I had my old xorg.conf ready (this has been an problem for me in every release, because the monitor isn't detected correctly). I had to enable proprietary drivers to get wireless working.

Now the only thing that isn't working is getting sound output on my jack-connection, which has never worked either way.

---

### Post by loteq on 2009-04-26
Hi,

I upgraded from intrepid, and had only one issue at first. The upgrade program  said that it could not upgrade the kernel package. After rebooting, I had to manually remove nvidia modules, play around a little with synaptic to reinstall the new kernel, and modify menu.lst manually to finally be able to boot in the new kernel. Then reinstall nvidia. It was a little scary, but not that bad.

Now I have a more insidious issue:

Whenever any gnome program seems to open a modal dialog (right-click on the panel->properties, or just opening a file browser in any program). The invoking program freezes for 30s-1min more or less, until the dialog shows up. This is a showstopper of course unless i find a solution. I have been looking around on the forums but have not been able to find a solution. 

Help/guidance would be greatly appreciated!

:)

---

### Post by jsonder on 2009-04-26
> **jsonder said:**
> Trying to install using the final release live cd at our computer club has been a bust, in that 3/4ths of the computers shut down with a checksum error message.  

The live cd is 699 meg.  I'm suspicious that pre-spacing and such may be taking just enough room that the checksum isn't completely written to the cd when I burned it.  I tried burning with 2 machines and used both k3b and brasero for burning, but still got the checksum failure and arrested boot of the cd.

And, I've had no problems at home.  Go figure.

Solution to the strange checksum problem:

The computer club techs had installed dvd readers as the primary optical drive and the cd read/write units were on the secondary (slave) connector.

Unplugging the dvd and giving the cd read/write unit the end connection got me installing.  While that is going on (800 megahertz P3 computer) I've reversed the cd and dvd drives on the 2nd recalcitrant computer and the installation cd worked fine.

So simple!:lolflag:

---

### Post by kevinbsmith on 2009-04-26
I was a happy 8.04 user (have been happy with Ubuntu for several years). This week, upgraded to 8.10 and now 9.04. I'm still reading forums and bug lists, but at the moment I have three problems, each of which would have kept me from upgrading if I had known about them in advance:

- Mouse cursor responsiveness is very poor (jumpy)
- Wifi no longer works (Atheros)
- Sound no longer works (maybe ALSA/pulseaudio conflict?)

I really wish I had stayed with 8.04 longer. I'm optimistic that I might be able to get the sound working again. But from what I'm reading so far, the responsiveness issue may require a kernel upgrade, and none of the wifi howto's seem to apply. I might have to revert to 8.04 until 9.10 comes out.

---

### Post by ckoz on 2009-04-26
today I went and tried again to see if there was any change, and now the upgrade showed up in update manager! I didn't change anything, so what was wrong is still a mystery. Got update, installed no problem at all, looks good!

Only odd thing now is when I run update manager is states "System is up to date" but there's a greyed out "Brasero" in the list (????)

---

### Post by ckoz on 2009-04-26
just found brasero answer...linked here in case anyone else has same issue
[http://ubuntuforums.org/showpost.php?p=7009023&postcount=4](http://ubuntuforums.org/showpost.php?p=7009023&postcount=4)
Major verison jump makes update manager a little nervous....

---

### Post by bzarnsy on 2009-04-26
everything went very smoothly. no problems at all. 
Dell Dimension 2350
1.7G Celeron
1G Ram
845G integrated graphics

---

### Post by V-600 on 2009-04-26
I've just installed the netbook remix on an aspire one (512MB memory, 8GB SSD). The instructions to create the bootable USB stick worked perfectly, as did the live session itself. UNR installed with no problems.

The are a few problems that I know are already well known. I am now looking into how to get my SDHC card with all my data on it visible to ubuntu. Something about booting the computer with the card in place, but this failed first time I tried it. I will have a play around with it though.

I am also looking about whether it is necessary to disable swap to save SSD usage, or change the swappiness value.

Aside from this, everything has gone smoothly and seems to be working correctly.

Of note though is that nautilus seems much slower than thunar which it replaced from linpus lite.

---

### Post by Shriner on 2009-04-26
I had only 2 problems, had to modify .conkyrc as the window was always top now..no biggie. Additionally, it looks raised from the desktop now...I can either live with it or try adjusting more....

Other appeared to be, prob was with BOINC though, see my thread: [http://ubuntuforums.org/showthread.php?t=1137783](http://ubuntuforums.org/showthread.php?t=1137783)

Only other thing that I've noticed is that BOINC is telling me there is a new version available for my machine, but it's not in the repositories yet, so I'll wait.

---

### Post by jakwriter on 2009-04-26
Considering I went XP, 6.06, 8.04, 8.01, 9.04, or something along that line, all in one day AND the essentials all work, I must once again proclaim the superiority of the open source philosophy.  Call me biased, but I love Ubuntu.

---

### Post by Viranh on 2009-04-26
I've done a clean install 4 times. I checked my disk and found no errors, but shortly after booting up the first time, apt encounters a "segmentation fault" error, and then other programs start to do the same. Additionally, my wireless card stops transmitting every few minutes. Disconnecting and reconnecting helps, but I can't use a system where this must be done about every 2-5 minutes. I will be downgrading to Intrepid ASAP. Everything worked for me in Intrepid! I rarely have problems with this machine. Aghh.. Jaunty has been terrible for me, and that makes me really sad. I saw a pretty significant speed increase with it.

---

### Post by Messyhair42 on 2009-04-26
the install went alright, but i'm finding more and more things as i gather my old programs back that either annoy me or are glitchy. i've had quite a few lock ups when certain programs are running and i can't get wine programs to start up on boot ala system>preferences>start up programs.

---

### Post by PacSci on 2009-04-26
Probably the hardest part of the upgrade was waiting for the servers to unmelt. The upgrade worked fine, and incidentally, right after the upgrade I switched to Xfce full time.

I was freaking out a bit after the upgrade, because I was trying to rip some CDs. The CD didn't appear in Sound Juicer, so I thought that Jaunty had broken the drive. I tried mounting it manually, but it didn't work. Then I realized that I couldn't mount it because it was a music CD, and that it wasn't showing up because I had the wrong drive selected. ;)

Also, I was having problems with my Python setup in the 2.5 to 2.6. That took a bit of time to reconfigure, but I'm glad that Ubuntu finally has 2.6, and I was honestly expecting it to be worse.

---

### Post by joker77 on 2009-04-26
Downloading: 
Torrent. worked well. However the estimated time was exceeded about 5x (estimated 3.5 hrs, took maybe 15 hours). 

Burning to CD:
This has been recently reported on this forum... I was also affected. The iso (699 MB) was not accepted by 8.10's brasero for a cd, saying it was too large. Was about to trash the iso, but then I found the post reporting a similar experience. As one of the members had suggested, I went to Windows Vista and burned the CD (DVD not required) with no problems (I did set the speed to 10X). This worked fine for the installation. (Post installation, I tried to find that thread to thank and report, but am unable) :(

Actual installation:
Went smoothly. I think faster than the previous 2 distros. I stayed with ext3 (based on advice in this forum)

Post installation
I had the problem of rhythmbox asking for more plugins/codecs to be installed even after I had allowed the gstreamer plugins. It's working now, but I get the pop up almost every time I start playing something on it, which I have to cancel. (This also has been reported earlier). I'm sure it will be fixed in subsequent updates.
Regarding the faster start... I have yet to try it :)
Skype: not able to transmit. But am receiving well. Tried adjusting the speakers etc. 
Everything else working well...
I haven't tried on Jaunty, but I guess nothing new is to be expected regarding syncing with windows mobile.

---

### Post by jsroth on 2009-04-26
As described [in this thread](http://ubuntuforums.org/showthread.php?t=1138779) I got a quite big problem with upgrading to Jaunty. I'm using Ubuntu since Gutsy and with every upgrade some problems occured ... this is quite annoying.

---

### Post by windom on 2009-04-26
Technically the upgrade from Intrepid went flawlessly. When the first reboot took place, X finally went black. The upgrade **totally** hosed compiz. After disabling compiz everything works fine but I miss compiz. I have a laptop with an Intel 945 chipset. None of the work-arounds I found have restored compiz. <sigh>

-w-

Compaq C571NR


<note 27APR2009> I finally stumbled unto the fact that the blur plugin causes my screen to go black when using compiz. I deactived the plugin and now life is good.

---

### Post by Smiley Coyote on 2009-04-26
I had Ubuntu Studio the other day and when I went to update, I ended up with a system that wouldn't even boot.  So, I accessed my files with my 8.10 CD to back them up and try again and found that some of it I was not even allowed to even read, as if it wasn't sure I was who I said I was; after all, my system was set to only login with the use of a password.

I backed up what I could.  Thank God nothing important was unavailable but a warning of this sort would have been nice instead of being actively encouraged that doing it this way would negate the need for backing up anything.  I spent hours poring over what had been said and I suspect that there are folks you are going to hear from out there with similar experiences that just can't get online to even divulge it.

Eventually, I reinstalled 8.10 on a whole new, clean partition, using the whole drive and tried again but when updated the same thing happened: on the boot just the word BUG showing with hundred of digits showing in columns and rows and no option to continue further or debug or anything, i.e. no way to boot.

I have 8.10 now for a third time and I am going to wait for 9.05 at least before I enter that nightmare again.

For noobs this is huge; my system had been tweaked through the pain that comes with trial and error for someone brand new to Linux.  It is going to take days to get my system back to where it was, if that is even possible.

I repeat: backup your files before trying to upgrade with Update Manager!

---

### Post by alex.mobigo on 2009-04-26
Yesterday i decided it was time to upgrade from ubuntu 8.10 to 9.04, here is what i have experienced so far.

Hardware: Notebook core2 duo 1.8, 2 Gb Ram, 40 Gb HD, Intel 945 video(Intel 945GM Chipset), broadcom B43 wifi, SD card reader, DVD R/W. Dual boot Ubuntu/Windows XP (it came with Vista).

I made a fresh install from 8.04 to 8.10 to solve minor issues related to sound card and dual head monitor that i could not make it work in 8.04. Everything worked fine manually installing wifi and sound following forums instructions. Dual head monitor was configured automatically, so nothing to worry about until i upgraded.

I had my notebook hand crafted to best performance i could and never had experienced any crash, well i never pushed it really hard to see or expect any. So i was happy.

I had Mysql and PostgreSQL (Both latest version running).
I had evolution running and configured and working.
Gnome as the desktop.

I made some screen shots to help compare memory usage and Cpu usage for both version, and help decide if it "worth upgrading" . The shots were taken with System Monitor and Update Manger running.

[SIZE=2]**I made this steps:**[/SIZE]

   1. update all the software in 8.10
   2. started upgrading

During the upgrade, i had some warning complaining about video ":0.0", something about missing default configuration for video :0.0 ( did not take note of the complete message ), but it carried on.
Ubuntu nicelly point out the MySQL config would be overwritten and asked me i it could or not, and also showed me the diff (i could decide), and also about the apparmor config it was about to change. I had MySQL and PostgreSQL in a separate partition.
For the B43, it asked me to download and install the firmware, but crashed in the middle, and the ethernet connection was broken, from there i knew it had not installed and at the end, warned me that it completed with errors and i could end with an Unstable install. Now i started the get worried. I rebooted and it came with the nice login, and i was expecting a crash, and there i was with my dual head monitor working as expected.

[SIZE=2]**Things that did not worked:**[/SIZE]
a) B43 Wifi driver
b) bonobo-activation-server (complained about a socket connection error, missing file)
c) Video Decrease of performance
d) System testing

[SIZE=2]**What i did to solve:**[/SIZE]
a) B43 Wifi Driver:
> sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh for the B43 and activated the driver in System->Administration->Hardware Driver, it crashed. Even so it activated the B43 driver, now i have Wifi and eth0 connection established. 

b) The error seems related to video driver or the B43 driver. Need to look further. Someone with advanced linux experience could point out why this error is or was occurring.

c) The video slow performance eat 35% cpu (see the attached file), making it very slow, read this thread: 
[http://ubuntuforums.org/showthread.php?t=1067967&page=3](http://ubuntuforums.org/showthread.php?t=1067967&page=3)
[http://ubuntuforums.org/showthread.php?t=1130582&page=10](http://ubuntuforums.org/showthread.php?t=1130582&page=10)
I edited the xconf and added Accelmethod and MigrationHeuristic:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_intel_greedy&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_intel_greedy&num=1)
> Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"    "EXA"
    Option        "MigrationHeuristic"    "greedy"
EndSectionNow i have improved performance, or at least  back to normal. I hope this driver fix will be available soon, otherwise you dont get Compiz working. I am using dual head with more than 2048 virtual pixel size, so i cant get compiz working with this configuration anyway, never mind.

d) Nothing to do yet. [https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/357470](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/357470)

[SIZE=2][COLOR=Red]Things that still need "**investigation"**:[/COLOR][/SIZE]
Evolution takes [COLOR=Red]**30 seconds**[/COLOR] to edit **Preferences**.
FireFox takes similar times to open the default Gnome Dialog box (the one to Browse files).
They seem to wait for some condition that is not working properly.


Lets see if the next available updates for the 9.04 can help this.
I found that 9.04 has a better performance, but i have not done any benchmark, it is just feeling...

I hope this help people to decide for the upgrade, and perhaps, help solve this minor issues.

Cheers

---

### Post by jd1975 on 2009-04-26
Started apt-get and went to sleep three nights ago.  Finished things up in the morning, appeared to be smooth, but got to black screen where it should have prompted me to log in, and it just stayed there.  Restarted a couple times, left the screen open while I took a shower and got dressed, and still a black screen with a moving mouse pointer, but no log in prompt.    

I probably have an ATI card that needs some sort of driver that I might be able to find and install with three cups of coffee and fifty Google searches, but I was hoping it would just work.  I've rolled back to Intrepid until I delude myself into thinking I have time to try again.

I love Ubuntu (the price is right!), but I do wish installation and upgrade didn't feel like committing to a week-long role in a William S. Burroughs sort of scenario involving hazy encounters with stimulants and weird bugs.

---

### Post by OttifantSir on 2009-04-26
I did an upgrade from 8.10 to 9.04. When I restarted, I got a warped image on my monitor, and did a reboot. Still the same, several times. Changed monitor, still the same several times. Got a message about USB (add-on card) and device not accepting address 4 on port 3. Removed the USB card and rebooted. Warped image on new (older) monitor. Removed an ATi card and rebooted. Did a filesystem check from the recovery menu, rebooted, got GRUB error 17. Tried to do e2fsck, got a message saying it wasn't a valid ext2 partition (/dev/sda1). Did fsck -yfv which was the only thing that did anything. Unfortunately, it did a whole lot of damage; it wiped my installation. /home, /swap, three FULL 1TB disks set in LVM, NFS are at risk as I now do a fresh install of 9.04. This is the first time I have a really bad experience with in-distro-upgrade, but it is a REALLY bad experience. 

On another note: Why does an in-distro-upgrade force me to remove accessibility I don't use, Evolution which I don't use, Ekiga which I don't use, games which I don't use, F-Spot, GiMP, XSane, Transmission and a whole host of other things I don't use? Why can't upgrade be done without re-installing applications I have removed prior to upgrade? (That's usually my gripe about upgrades)

---

### Post by uniontroublemaker on 2009-04-26
[http://ubuntuforums.org/showthread.php?t=1130582&referrerid=277529](http://ubuntuforums.org/showthread.php?t=1130582&referrerid=277529) worked on 2-yr old Dell laptop to solve integrated Intel graphics video driver problem

---

### Post by Imaginary on 2009-04-26
Upgraded an AMD64 system from Intrepid to Jaunty using Update Manager.  The new version of gnome-session broke my GNOME/Openbox login, a problem that took me about half an hour to track down to a no-longer-supported option being called from openbox-gnome-session and fix.

On the other hand, Flash now works a dream, getting rid of skipping problems and failure to load problems that I've wasted hours and hours trying to fix with no lock.  And PulseAudio seems to be infinitely less broken.

On balance, a serious victory.  None of the troubles I ran into going from Hardy to Intrepid.

---

### Post by Randy3011 on 2009-04-26
Did the online upgrade. Made sure that I had all the updates for 8.10 installed first. Did a full image backup with standalone Acronis Disk Manager. Took about 1hr20min to complete everything, yesterday. So far the only things I have noticed is I had to re-install Flash plugin even though it said it was there and my original screen resolution is not a choice anymore (my setting was in the middle - 1280x1024 is okay but these are old eyes, 1024x768 looses too much real estate). I do have two partitions set up - one for the system and a separate /home partition. 

So far, so good.

Smoothest upgrade I have ever done!! Great job!!.

Regards,
Randy3011

---

### Post by siepo on 2009-04-26
Updated laptop and desktop with do-release-upgrade. No problems whatever in spite of both having a Intel 945G chipset (didn't try 3d acceleration though).

---

### Post by Tails9 on 2009-04-26
> **Feelin_froggy8877 said:**
> There was some kind of problem with the gnome panel. Would not display the menu and just could'nt do anything with it all together. tried adding a panel and that just made things worse. Rebooted after that and it would boot to the desktop but kinda went into a freeze state.

I'm having the same problem. The panels don't respond to anything. No panel applets are loaded. The panels remain gray. Alt-f2 works, but the dialog box remains gray. It responds to input though.

Tried switching to vesa instead of nvidia but it didnt help...

---

### Post by relaxedcrazyman on 2009-04-26
omg, when i tried to upgrade through the update manager it was hellish. it kept crashing and i was getting super slow dowload speeds. it took over 15 hours to finally finish the download, and when it started installing and such, it kept crashing and i had to keep starting the install over and over. so finally i said **** it and did a clean install over it.

---

### Post by mrdancemachine on 2009-04-26
Well i upgraded from 8.04 -8.10 and the final release. Now i am not able to move my window around and i checked compiz and nada.. here is what i got. 

tony@tony-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

tony@tony-desktop:~$ compiz
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0
tony@tony-desktop:~$ compiz


When i kill compiz and got to System and Pref, i select the Windows Manger and i get this error--> "Cannot start the preferences application for your window manager"  Window manager "unknown" has not registered a configuration tool. 

So what can i do here and i already have removed and reinstalled Compiz. Even checked of my video card was in the blacklist and tried those steps. It has worked before in the 8.04 and 8.10.

---

### Post by nelsonhogg on 2009-04-26
I am guessing my problem is with my ATI Radeon x1400 video card. In any case, after becoming an ubuntu devotee several years ago, this it the first time my upgrade/install is so thorougly screwed up that I cannot boot or login. Back to 8.10? I'm most disappointed.

---

### Post by Shpongle on 2009-04-26
update went smoothly, but performance seems to have diminished from intripid,

---

### Post by Ozitraveller on 2009-04-26
I always use the alternative when I do a clean install, I have a low spec system. The problem I had, and I had the same problem when testing the beta, was that the install failed in "Select and Install Software". The progress bar stopped at 6%, however the download continued to file 770/864.

I got around the problem by doing a command-line install and then installed the ubuntu-desktop.

;(

---

### Post by zaivala on 2009-04-26
I couldn't even get it to install -- WUBI would not run, started sending a slough of error messages, and I had to delete two Python programs in my Windows Program Manager to get my system back.  I tried it both by downloading WUBI from wubi-installer.org AND by downloading Ubuntu from Ubuntu.com and running the ISO using Daemon Tools.  I started a topic under Absolute Beginners, "WUBI, WUBI, WUBI Do Ya Hate Me?" -- no responses.

---

### Post by Linux000 on 2009-04-26
Horrible upgrade experience. The computer shut down when the upgrade started to install packages, ruined the computer, had to restart from scratch.

---

### Post by glantela on 2009-04-26
Overall, i think my upgrade went well.  Just a couple minor things- Computer Janitor hangs my computer and system testing doesnt seem to work... Anyone else have this problem?

---

### Post by shark1997 on 2009-04-26
Upgrade was FLAWLESS!!!

Just really slow...

Took 14 hours to finish

Best release ever!:P

---

### Post by elewis on 2009-04-26
Upgrading from Intrepid which worked flawlessly to Jaunty on an HP Pavilion machine was a disaster. It did something to the boot script requiring one to have to type "control D" to boot the machine. All the while numerous error messages (loading this module failed, loading that module failed) scrolled by on startup. Once Jaunty was finally up, I found that Sun VirtualBox would no longer run. Other apps seemed OK. Attempting a clean install caused the computer to flash thousands of error messages. Each begins with a number (started with 1, I shut it down 8-10 hours later at 6000 or so followed by a colon, followed by 6 other numbers. I gave up and installed another Linux OS which I now have running well.
My concern is that I am a long time (10 years plus) user and supporter of Linux. Jaunty is simply not the Linux experience you would hand anyone upgrading from Microsoft or something else. I hate to see Linux get a bad name from one poor release.
I use Ubuntu 8.04 which is unquestionably the best computer product I have seen on a Dell Laptop. I have had similar outstanding success with Intrepid where I have installed it on numerous machines in two businesses I run. It is unfortunate that Jaunty is such a disaster. I trust 9.10 will be better! Fortunately, all data backed up prior to upgrade - no data loss!
Jaunty at least needs a clean install option resembling that of Fedora.

---

### Post by bobcomer on 2009-04-26
Install of both x86 and x64 left me with no sound.  None of the suggested fixes on the forum have made any difference at all except installing OSS, but I couldn't get anything but osstest to play anything.

Sound worked in 8.10.

---

### Post by DavidTangye on 2009-04-26
So far 2/3 upgraders did not report a flawless upgrade. That is not a good statistic, and needs serious attention. I was in the happy 1/3 for the first machine. I have 4 more to go, and all are different (motherboards etc, PCs, laptops). I hope I can add more to the "flawless upgrade" report.

---

### Post by DavidTangye on 2009-04-26
> **OttifantSir said:**
> On another note: Why does an in-distro-upgrade force me to remove accessibility I don't use, Evolution which I don't use, Ekiga which I don't use, games which I don't use, F-Spot, GiMP, XSane, Transmission and a whole host of other things I don't use? Why can't upgrade be done without re-installing applications I have removed prior to upgrade? (That's usually my gripe about upgrades)I am also curious about this. I assume that removing those packages would have also removed the meta package 'ubuntu-desktop'. I would have thought that an upgrade would not re-install 'ubuntu-desktop' and thus its dependent packages. You might raise this as a bug/enhancement request.

---

### Post by LonelyAppleHater on 2009-04-26
I'm extremely happy upgrading from 8.10 to 9.04.  Had to restart the update manager a couple of times to keep it downloading the files, but it finally got done.  

Everything pretty much worked without a hitch except for two things.  Playing flash fullscreen was choppy.  Also, it was asking me to remove some packages, which was fine, except for the fact that it wanted to remove Vuze.  So, I kept everything just to be extra safe. But these are extremely minor issues.  No showstoppers on my end!  Great job, Ubuntu Team!

---

### Post by laffinet on 2009-04-26
My upgrade worked without any problems. However out of curiousity I did a fresh install on a separate partition and the system there was much faster (boot especially, but once loaded as well). So in the end I did a fresh install anyway and got rid of the upgraded one.

---

### Post by krolls on 2009-04-26
i dont have any problem so far.. as i upgraded my 9.04 using upgrade manager in 8.10..

but not sure coz i just finished last night..

but the first thing i went tho 9.04 is 'animation setting'.. 
couldnt change i think...!

---

### Post by undfined on 2009-04-27
My laptop installation went so well I was surprised to run into problems upgrading my 2 desktops.  The downloads kept stalling on both my i386 and 64 bit machines.

I ended up burning CDs and installing fresh, without issue.  But it was a couple of days worth of struggling with the upgrades that I expected to go off without a hitch.  

My biggest issues (so far) have been in getting simple Last.fm and other media streams to work.  And Amarok is a nightmare - I'm ok with admitting I need to get used to the new interace, but basic libraries are missing, mp3s aren't playng out of the box, I can't add network folders to my library, etc.  And Rhythmbox keeps sending me duplicate songs in Last.fm streams.

Luckily I kinda know what I'm doing and a few searches have worked out some kinks (aside from the media problems).  But again, it's more fuel for the people saying "Ubuntu isn't ready for prime-time, yet."  Which isn't true but a roadblock nonetheless.

Other than that, I'm wired up with a 64bit "server" keeping my mp3s, files (my wife's and mine), printer, web server, ssh server, and our picture folders on 9.04 without any major hiccups, aside from the upgrade issues.

My i386 desktop and laptop have never looked or worked better.  Typical office work (email, google calendar, scanning, printing, google finance, intranet, flash websites, etc) is going on without any problems.  I haven't yet gotten my blackberry synced, nor started heavily into my backlog of photos that need to be loaded, edited in Gimp, and moved to our file server.  Same with scanning (a USB stick on our Brother MFC 6490 does the trick in the meantime.


I have yet to get Jack and some multi-track audio recording going on but should start down that road in the next month.  And I have yet to load Virtualbox for a Windows XP install (still need Office 2003 for some work files that Open Office can't handle yet).

Anyways, I'm still impressed with the newest version and am looking forward to the fall update. :)

---

### Post by gadabyte on 2009-04-27
did a fresh install, xubuntu amd64.  everything worked flawlessly until i rebooted, at which point i lost all sound.  i tried 2 re-installs, with the same result every time - perfection until reboot.

tried some of the tricks i learned while trying to get my (then new) card working on an existing install of intrepid, to no avail.  i've no time to wrestle with it right now, so i went back to intrepid.  sound works again.

i'll probably have another go at it at some point this week, or i might just wait for someone better than me to figure it out :-D

for the record, my sound card is a m-audio revolution 7.1

---

### Post by angie4107 on 2009-04-27
I did a clean install... and am a newbie to Linux/Ubuntu/etc..... so of course there were a few things I'm still learning and had to fix.. but honestly it was ALL my fault ha ha ha.. other than getting Java to work properly ( I had installed actually 2 versions -- with help from the forums--KUDOS to all!!! -- VERY HELPFUL--- got it fixed really quick.. and well I still have one more issue that I wasn't expecting.. can't sync my phone yet still.. but honestly I'd even switch phones ..it's totally worth it if I can't get it to work... 


Ubuntu ROCKS:guitar:!!!!!

---

### Post by pkolesni on 2009-04-27
Installation from Live CD - Notebook HP nc6000:

- in LiveCD version Atheros WiFi (Atheros AR5212) works with hidden SSID & WPA/WPA2, but in HDD installation Atheros WiFi don't work with hidden SSID (I used to have the same problem with 7.04, but in 7.10&8.x everything work fine). The only difference I've found in logs is
/var/log/wpa_supplicant.log
---- Worked (LiveCD) ---
Trying to associate with 00:14:bf:ef:81:87 (SSID='myHome' freq=2437 MHz)
CTRL-EVENT-SCAN-RESULTS 
Associated with 00:14:bf:ef:81:87
WPA: Key negotiation completed with 00:14:bf:ef:81:87 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:14:bf:ef:81:87 completed (auth) [id=0 id_str=]

---- Failed (HDD Instalation) ---
Trying to associate with SSID 'myHome'
Failed to set operating mode
CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (auth) [id=-1 id_str=]
CTRL-EVENT-SCAN-RESULTS 
----


PS: I think that gparted will be usefull not only in LiveCD ;)

Thanks,

Pavel

---

### Post by Acreo Aeneas on 2009-04-27
I did a fresh install of UNR 9.04 onto my AA1 netbook on Saturday and have been using it almost flawlessly since then (just the SD card reader issue - waiting on it to get resolved).

At the moment, I've decided to install 9.04 Desktop on the AA1 instead of keeping the UNR as I want to see my wallpaper and have a "normal" desktop experience rather than the UNR experience.

After Desktop is installed, I'll be throwing my video files, Starcraft, WINE, and VLC MP back on their along with some FF3.x add-ons.  :)

I'm hoping the resource usage of Desktop is the same as UNR.

[I]For reference: My AA1 model is the AOA150-1049 (Oynx Black).  It's the 8.9" first generation model not the current D150-xxxx 10.1" second generation.

[/I]Overall, I'm liking it a lot better than 8.10 on the desktop/server next to me.  WiFi works after resuming from suspend, so that's a big plus.  

My only concern now is if any windows will appear out-of-bounds on my netbook's screen (1024 x 768 resolution).  I had already encountered one window like that on UNR (logon properties).

I'll probably throw Ubuntu 9.04 SE onto the desktop/server next to me this coming weekend.

---

### Post by tsaowang on 2009-04-27
Downloaded the distro on DVD.
Backed up all my files.
Install went just flawlessly and faster than with Intrepid.
Boot is just astonishing now !!! It's so fast...

WIFI Network recognized and configured in 1 sec.
Nvidia display 100% OK with no problem.

Great job from the Ubuntu community. This Jaunty Jackalope is just PERFECT.


I will never go back to Windows again

---

### Post by zenbachry on 2009-04-27
Got 2 answers to that poll, but on the main PC is the one I answered with. Flawless install.

On main PC, downloaded the amd64 version, burned it disc and fresh install replacing 8.10 with new filesystem. So, I guess it should have been upgrade *shrugs* oh wells.

On brothers PC, I downloaded the i386 version, put it on my flash drive, and it failed to boot. So, I had to install. Installed with new filesystem, and it had a little bit of trouble starting up.  I don't exactly remember what I did, but it works flawlessy now.

I'm lovin' it too!

Oh, It took forever to get the drivers for my Wireless card and my video drivers (5 hours!) I just wrote it off as I'm doing it on release day and everyone is using the same server.

---

### Post by jmomandia on 2009-04-27
Got this message:

Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda5 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


Kubuntu upgrade (same hard drive) went without a hitch, though.

Thanks!

---

### Post by ppm on 2009-04-27
Upgraded from 8.10.

NVidia driver (the restriced one) failed to load probably due to kernel upgrade, which was expected from a previous experience.

These issues are minor for an experienced user or at least he knows where to look for a problem and possible fix it by doing some serious googling. However, for new users I reckon issues like these are unacceptable; you only get a flickering screen when X fails to start... :(

---

### Post by blackSP on 2009-04-27
> **blackSP said:**
> Running on an Asus F8P laptop with Radeon 2400, 2 gb ram, no problems with 8.10.

After the upgrade none of my windows have borders or a windows bar. Can't resize them, move them.

Video output sucks. No sound.

Boot time now about 100 seconds.

So I will wipe the damn thing tonight and start from scratch :mad:


Well, installing from scratch was no guarantee for success. After activating the fglrx driver my video went black with only some pixalation on top of the screen.

Damn, 2nd try, staying away from the fglrx hardware driver for the time being!

BTW, I still have the dreaded ACPI reference not found error during boot! Had it after the upgrade as well as the clean install. Never had it with 8.10!

---

### Post by rlogan on 2009-04-27
Hi all

Heres the results for 4 machines, 1 upgrade and 3 fresh installs with the Jaunty Beta.

First the fresh installs :-

1) P4 3.2Ghz 2.5Gb RAM, ATI Radeon 256Mb, 2 x 80Gb PATA HD, ASUS P4 motherboards, LCD Monitor with 1280x1024 resolution. All worked perfectly, not one issue.

2) Celeron E2140 2Gb RAM, GA NVidia GeForce 9500GT, 2 x 80Gb PATA HD, 1 x 500Gb SATA HD, Gigabyte M/B. Two issues the first being incorrect screen resolution. Previously hard worked on Feisty, Gutsy, Hardy and Intrepid, but after a manual config back on Feisty. Had to do manual config of x-org to get 1440x900 resolution.. But on examination of manual for GFX card it does not list 1440x900 resolution but that is what monitor uses. The card was capable of higher resolutions but hey it works beautifully now. The second is not resolved but Firefox chews memory until it halts the machine on only one website that I have found ([www.nrl.com](www.nrl.com)) which I have posted seperately. This one is work in progress but not critical as I can use Opera to view this page if absolutely necessary, will come back to it.

3) Celeron 1.2Ghz 384Mb RAM, Matrox Mystique 4Mb, 1x 8Gb PATA HD, 1 x 20Gb PATA HD, HP Motherboard ( A machine built from recovered machines for my 5 yr old daughter). This machine had no problems at all, all working nicely, admittedly a little sluggish but she is happy with it and thats all that matters to me !

Now onto the upgrade machine, this one is my wifes notebook which is an Aspire 4135 with 2Gb RAM and 80Gb HD, integrated GFX. The upgrade was done post release and worked perfectly, not one issue. It was a little sluggish on Intrepid (but still much much quicker than Vista) now it is so quick it is brilliant.

All in all what a great release, all machines run much much quicker and boot much quicker. 

Message to Canonical, please keep up the improvement from Intrepid to Jaunty with Karmic, plus can we have a face-lift for the desktop.

Cheers all 

Richard

---

### Post by Sprax on 2009-04-27
Upgrade broke completely. Got a bunch of error messages and it stopped. Was unable to reboot.

Install worked flawlessly however. Although I'm now having some configuration issues unrelated to installation.

---

### Post by Ubuntist on 2009-04-27
I tried to upgrade from 8.10 on a Dell Dimension 8300.

Three error messages appeared along the way, the first that python 2.6 could not be installed, the second that openoffice.org-emailmerge could not be installed, and finally that the upgrade was being aborted and a script would run to try to return the system to a usable state.

So I'm still running 8.10.

The first couple of times I upgraded, things went pretty well.  Last time (upgrading to 8.10) I had some problems, and this time it's failed completely.  Not a good trend.

---

### Post by zefiriss01 on 2009-04-27
download xubuntu 9.04
install ok, but trouble with my Aquos tv, so install with safe mode, than edit xorg.conf for all day to make it work.
but i'm satisfied with the result.

---

### Post by Hena Gaijin on 2009-04-27
Tried to dual boot 9.04, XP english, and XP japanese. (guess that would make it a tri boot eh?

Install worked fine but it wants to boot to Ubuntu by default.  Haven't found a way to boot to the japanese version by dfault.

Can't seem to burn DVD movies that I can watch on my DVD player.  Can't watch any flash vids on the internet. i.e. YouTube.  I can play DVD movies no problem though.  Tried to install flashplayer for linux but it would error.
Surfing the web is fine until I tried to visit the Ubuntu forums for info.  Can't use the search box or input text anywhere.  Weird.

Going back to Ibex till I can find out what the problem(s)is/are.

I'm a new user so no rush.

---

### Post by strange_cathect on 2009-04-27
1) After upgrade, firefox crashes 100 percent of the time when trying to play youtube. I still can't resolve this one.

2) Tracker index got corrupted. Had to delete all the contents of tracker folder and re-index.

---

### Post by Dearhell on 2009-04-27
I don't know about the previous polls but this is by far the most Ubuntu problematic version I've ever tried.

---

### Post by paapereira on 2009-04-27
> **RedStickHam said:**
> 
Another problem, which I've already asked about in another posting, is when I checked for updates, I was told I could only get a partial update and was told this would be done if I took that option:

Remove libd4.5-java
install libass1
install libd4.6-java
install libd4.6-java
install libd4.6-java-gcj
install libdca0
install liblrdf0
install libmodplug0c2
upgrade liblucene2-java

When I did that, update manager closed and nothing happened.  Not sure what is causing this.  I posted another thread about it and hope to find out soon what to do.
RedStickHam

Use Synaptic to mark this packages to update. Apply and you're good to go :) :guitar:

---

### Post by ap90033 on 2009-04-27
> **Redsunz said:**
> Even the new cards don't seem to work I have a 4870 X2 and when I tried to use the restricted drivers via the Sytem menu and terminal install Ubuntu crashes on boot up I see the progress bar then the next screen is a blurred mess.
I like my games so I may go back to 8.10 or XP
 
SAME PROBLEM HERE I have a 4870X2 and all i hear is follow the directions (I did duh) I have tried the manual method and it doenst seem to work. Any ideas? Anyone with a Current Radeon (like my 4870X2) that has this working and can help a guy out? Please???

---

### Post by therblack on 2009-04-27
I'm using a T60.  Following the upgrade, I find that the suspend/resume is flacky (requires a reboot roughly one time in ten)

Also, evolution/exchange didn't work and I had to mess with it to make it so.  Even know, it seems to crash a lot and the calendar doesn't always show my appointments

---

### Post by KeesM on 2009-04-27
Upgrade worked (nearly) flawlessly, apart from a minor glitch in the download of new packages on my laptop: hung on the last package, but a restart solved the issue.

Thanks! :) Looks great, both on my desktop and on my laptop. Only missing a more thematic wallpaper, like the Ibex artwork I used in 8.10; but I assume something similar for this one will pop up sooner or later.

---

### Post by ap90033 on 2009-04-27
Any ideas? :)

---

### Post by SyL on 2009-04-27
Worked smoothly, as usual.
Only had to re-install NForce driver for my sound card (Mother board Asus A7N8X).

---

### Post by ap90033 on 2009-04-27
Good for you. Wish it worked for me... A locked up computer doesnt do much for me.

---

### Post by SentientFluid on 2009-04-27
Install went well and reboot was fine.  Had issues with Java but ran update-alternatives and had to manually edit some links to point to java 6.0.13 folders now everything seems to be working fine.

---

### Post by ThomasJ02 on 2009-04-27
Things I've had to do so far to get Jaunty running:

1) Needed to download and compile latest mdadm, since the mdadm included in Jaunty segfaulted when assembling an array (and the latest isn't available via synaptic)

2) Needed to install 2.6.29, since 2.6.28 included in Jaunty led to soft CPU lockups when deleting files from ext4 (and the latest isn't available via synaptic)

3) Needed to downgrade to nVidia 173, since 180.44 included in Jaunty is known to be unstable  (and, in any case, 180.51 is not available via synaptic)

---

### Post by vexorian on 2009-04-27
I upgraded from hardy to jaunty (this jump is not recommended)

Anyway, there were some kde-related dependency issues, I'd recommend to uninstall kde before doing a hardy-> jaunty upgrade, you can always install it later (I installed kde after installing ubuntu)

Then the real problem was that nvidia yet again had issues, if you get a problem like mine, I was able to solve it so I am posting what I did:
* My problem was that although the restricted driver was loading and xorg didn't crash or anything, there was no glx(3d acceleration). In the xorg log it said something like
"module version mismatch"

It seemed like it was loading a glx module different to the one it was supposed to load (the installed driver was nvidia 173, but it was trying to load 96 which was uninstalled...

After some snooping I noticed this:
/usr/lib/xorg/modules/libglx.so : A link to a wrong module version
/usr/lib/xorg/modules/extensions/libglx.so : A link to the right one.

My hunch was that the one in /modules was a ghost and that the one in /modules/extensions was not getting loaded because xorg gave priority to the one in /modules

What I did was to remove /usr/lib/xorg/modules/libglx.so , but I'd recommend you to just do this (provided you do confirm there is a 'good' one in /extensions:

```

sudo mv /usr/lib/xorg/modules/libglx.so /usr/lib/xorg/modules/libglx.so.bad

```
After restarting it could work, if it still doesn't work then it was something else, if the situation is worse now (xorg now crashes) then restore the file:

```

sudo mv /usr/lib/xorg/modules/libglx.so.bad /usr/lib/xorg/modules/libglx.so

```

---

### Post by CCER on 2009-04-27
I just upgraded from 8.10 to 9.04, through the Update Manager. After rebooting and the loading bar, the screen remains black. I'm downloading the ISO and I'll reinstall, hoping I can get my files back.

---

### Post by jerrylamos on 2009-04-27
video graphics - 

IBM ThinkCentre with i845 intel integrated graphics, finally working more or less with 2.6.30-rc3 kernel on top of jaunty. Still sluggish compared to Hardy, however there's a lot of polish on ubuntu since then and don't want to return.  

Thinkpad R31 with i830 intel integrated graphics jaunty gradually corrupts fonts.  More and more letters turn into ink splats.  It's a bit better with 2.6.30-rc3 however I do resort to intrepid when I have something to do.

ATI on Compaq Presario 3.3 gHz some video benchmarks stink.  Flash full screen runs O.K. on YouTube etc.  so I can put up with lousy fps (frames per second) on other tests.  

ATI on IBM Thinkpad T40 1.5 gHz pentium running O.K. I think.....

All the above run just fine with XP.  I have no intention of buying Windows 7, 8, 9, 10, ...

Jerry

---

### Post by hockman5 on 2009-04-27
Upgraded from Feisty to Jaunty. No video. Scrambled screen. HAve been booting into recovery mode, text only trying to get the display to work with no luck. Seems as all the packages are there
just can't get them working right. I have an ATI Radeon HD2400 Pro PCI card and am still searching for solutions. This is day 2 and I am wishing I didn't upgrade since there are no big changes.....

---

### Post by blitzer on 2009-04-27
Upgraded through upgrade manager.  Let upgrade manager pick the best repository for me then selected upgrade.  Upgrade went smoothly so **I tried a game which had no sound ?**  **Screen saver kicks in the background while playing a game, thinks the system is idle ?**  **Seems the laptop runs hotter then before -fans hardly run ?**

The most puzzling is a family member has the exact same system as I do. When I upgraded that system it **failed on the wireless part ?**  The only thing that was different **was the repository.**

---

### Post by dLeon on 2009-04-27
- Done a clean install of Xubuntu.
- A bit surprised to some new features.
- May say work flawlessly in my system. Except a minor problem, that Xfce Desktop wallpaper image list work really weird now. It bog down the system like hell. Seems this new Xfce try to figure out what kind of images we listed up front than just do that when the image it self being called as before in Xfce Intrepid. Still figuring the work around.

After (can say) testing the final release of Jaunty for sometimes:
I can confirm that I am one of happy people that get everything out of the box. All my hardwares detected and works flawlessly.
Don't have any serious problems with any my chosen softwares. As a matter a fact, I practically didn't need to set anything in softwares area. And everything fast.

Thank you Ubuntu developers + contributors for your hard works.

---

### Post by Niniel on 2009-04-27
I upgraded 2 machines. One worked without a hitch - my desktop - and one looked like it had a problem - notebook - but that went away by itself.

The issue I seemed to have with my HP Pavilion notebook is that I have my /home partition on an SD card that is in a USB adapter (by Transcend). On the first reboot after the upgrade I was unable to log into the installation because the system was unable to mount that adapter/card. I then restarted the computer and used the previous kernel from 8.10. That worked flawlessly. But the next time I forgot to pick the old kernel and it still worked, so now I've deleted the old kernel and everything is ok.

Update: When I started the laptop yesterday, I got that error again, and the system can't find my /home partition.

---

### Post by David Valentine on 2009-04-27
Upgrading from 8.10 (Ultimate Edition) AMD64 to 9.04 AMD64 was the smoothest upgrade experience I've had yet.  So far, not a single issue, even though I accepted the maintainers' versions of the various config files.  Amazing.  Kudos to the developers.

---

### Post by aharding3rd on 2009-04-27
Upgrade through update manager on Sony Vaio- K23.  Flawless.  I was pleasantly surprised as I usually end up having to do a clean install to get those results.  Everything works- 

Thanks Ubuntu Team....


AOH 3rd

---

### Post by neigun on 2009-04-27
:)

No problems with the upgrade- data intact (back up made just in case though in XP, I hasten to add ;-) but I've nearly ditched it). 

Since the upgrade I now have the desktop themed sounds which were never present in 8.10.

I would warn newbs, like myself, to be cautious with the Janitor. As an experiment I removed the Deb install of GoogleEarth, which Janitor stated was unsupported and no longer in the package archives, and it did exactly that! I assume Medibuntu is not classed as an archive or is an unofficial archive, which according to Janitor was no longer supported. If you want to remove previous editions of the kernel, etc though it is ideal, but I would exercise caution and maybe just use Synaptic. So far nothing else has materialised which needs my attention in Janitor so I can't comment further.

TTFN 

Neil

---

### Post by cbconway on 2009-04-27
After a slow (all night) download, the upgrade from intrepid went smoothly. The only glitch is that I get no audio when viewing online videos in Firefox. Downloaded videos run fine. I'm fairly new to Ubuntu, so it might take me some time to figure out the problem.

---

### Post by myxiplx on 2009-04-27
Absolute nightmare, the graphics support is horrendous.  I had a perfectly working 8.10 system that had started with 7.04, upgraded to 7.10, 8.04 and 8.10.  Every one has worked fine.

With 9.04 though it was a different story.  The upgrade appeared ok, but then on reboot I couldn't log on.  Every time I tried to log on, the system crashed straight back to the logon screen.  After a fair bit of time messing around I managed to move my .config folder and log on.  Thank god I had a couple of old testing accounts on here that worked!

Well, after that I started looking for the cause, and found that it was Compiz.  It appears that any attempt to change the appearance settings causes this problem every time.

Way to go Canonical, ship a system that can brick itself just by enabling the fancy graphics that have been shown all over as one of the benefits of Linux compared to Vista.

Well, after that I figured I'd try the proprietary drivers, and wasn't that fun.  After rebooting to a screen of complete garbage I realised I could have a problem on my hands.  Fortunately we have a second (windows!) computer in the house, and I was able to use that to find the command to disable those drivers.

So way to go #2 - ship a system that can also brick itself by enabling the proprietary drivers.

Now I know I'm stuck with the open source drivers, and I know I can't enable Compiz.  That's a bit of a step backwards from 8.10, but I can live with it... until I try to get my dual screens working again.

I eventually find that if I go through the dialog in just the right order, I can get it working at 1280x1024 on each screen, but no matter what I try, I can't get the second one working at the proper 1440x900 resolution.  Any attempt to do that leaves me with two blank monitors (but fortunately I'm so used to graphics problems in 9.04 now this is only a minor inconvenience now).

And then today I realise that the hardware cursor corruption bug is back now I'm on the open source driver, great.

So in summary:
- The upgrade left my system unusable
- The hardware driver installation left my system unusable
- ATI's new drivers to support 9.04 aren't available for my hardware
- Attempting to use dual screen mode renders my system unusable
- Enabling Compiz renders my system unusable
- I can't use my two monitors at the proper resolution
- I get corruption all over the screen on the mouse cursor

A pretty damn awful upgrade experience to be honest, one that's left me wishing I could go back to 8.10, and wondering whether I'm going to be able to use new Ubuntu releases in the future.

Hell, at this point I'm wondering whether to switch to OpenSolaris, at least with ZFS I can roll back system upgrades.

---

### Post by Lektorvis on 2009-04-27
Wow a though upgrade. :confused:
I was careless and distracted during my first upgrade attemt. 
I interrupted the upgrade-proces before the download began. 
On the next attempt there were no Upgrade shown in the Update-Manager, I tried anaway, but apparently I didn't really upgrade but only updated. 
The result of my "upgrade" was a black  graphic screen showing Busybox.

I figured out how to solve the mess without having to do a new clean install. [http://ubuntuforums.org/showthread.php?t=1138397&referrerid=294234]("http://ubuntuforums.org/showthread.php?t=1138397&referrerid=294234")

Next time I will save a list of my installed package and run a clean install instead of an upgrade.
[http://ubuntuforums.org/showthread.php?t=169062]("http://ubuntuforums.org/showthread.php?t=169062")

AnyWay 9.04 seems to run all rigth on my Dell laptop :P

---

### Post by ap90033 on 2009-04-27
Nice well I see I am not the only guy with issues. :)

---

### Post by fofenk on 2009-04-27
i tried to update from alternate install cd, then i encountered some sort of error and update cancelled.
then i had a clean install from same cd. it started well, but after sometime (maybe after i've altered network settings to static ip from dhcp) it started to freeze and stopped responding my mouse clicks (thanks god i've set a keyboard shortcut to terminal before hand). i tried to undo what i've done but nothing changed.
then i thought that the cd i use had problems, so i've downloaded kubuntu desktop cd, and re-installed. i had exactly the same problems.
any ideas?

---

### Post by blackkat on 2009-04-27
I tried doing an upgrade from 8.10 to 9.04 it worked but I could not use Compiz without system crashing. So I did a clean install of 9.04 and I had better results.

---

### Post by MikeBrown on 2009-04-27
I tried to upgrade on the day of release and faced a few difficulties that I'm sure many of you can guess...

To start off, by the time I was actually at a place where I could download the new install disc, it was already about 1pm my time, so Ubuntu.com was having some bandwidth problems (as expected) with everyone and their mother jumping at the chance to get the new flavor of Ubuntu NOW!

I finally got to the mirrors/download page and opted for the torrent, as I figured that it would be faster than downloading straight from Ubuntu.com itself and would also help out some fellow linux users having the same problems as I had. 

I select the torrent, it opens in Transmission and downloads in about 30 mins. I burn it to a blank dvd (it was the only type of disc I had that was empty, I usually hate wasting the space) and prepare to upgrade. 

I go through the install process a few steps only to realize that I grabbed the "alternate" (text/minimal GUI) install disc. As I am used to using the regular install and don't want to accidentally overwrite my other boot on my harddrive, I cancel and reboot back into the previous install. Luckily I wasn't too far into it, and nothing was harmed. 

I go back to Ubuntu.com and try to get the .iso link I really wanted (making absolutely positive that I got the GUI interface install disc) and started the download. 

When it was all said and done I finally had Jaunty downloaded burnt and installed at about 3-4pm. It took that long mainly because the page to grab the download kept timing out or not appearing at all...

After it was installed, my conky, thunderbird, pidgin, and other plugins/settings were transferred very quickly, I just had to go through the hurdle of getting the install disc to start downloading. 


I only had trouble getting the download to start, otherwise it was a very quick and painless process. 

I like the new notification system! Plus I did notice faster boot time on my computer (see sig for specs). I did not however try the new file system compression. Anyone that has care to weigh in on the pros and cons of the new compression?

---

### Post by Freaky_Llama on 2009-04-27
This Evolution and Exchange issue is a show stopper for me. It is broke, and using both the OWA plugin, as well as the new MAPI plugin do not connect at all. Previously on 8.10 it worked fine.

---

### Post by newintolinux on 2009-04-27
After trying to installing/uninstalling Ubuntu 9.04 for several times (on two different laptops), because of problems with the resolution settings of the videocard, i installed Kubuntu 9.04 and the videocard works perfect.

The problems with the videocard i could not solve.

Does anyone can help or point me out in the right direction for solving the problem with the resolution?.

One of the laptops i use is a ASUS G1S

---

### Post by aextance on 2009-04-27
Oddly, on my Thinkpad Jaunty worked fine for a couple of hours, then just as I needed to do some work on it the Trackpoint crashed. 

Managed to fix it with some tinkering in the xorg.conf file, and workaround with keyboard shortcuts until then, but it's been a bit of an annoying start to this week's freelancing assignment.

---

### Post by vexorian on 2009-04-27
> Absolute nightmare, the graphics support is horrendous. I had a perfectly working 8.10 system that had started with 7.04, upgraded to 7.10, 8.04 and 8.10. Every one has worked fine.It was about time you had problems with an upgrade.

Problems with upgrade are a norm, so your previous experiences were just luck.

I decided next time I will always just back up my documents and do a fresh install. Redownloading all packages I haver ever installed is basically the same as the dist-upgrade process, only that without breakage...

---

### Post by ibang1 on 2009-04-27
Hello.

This is my first post and the first install and everything went smooth.  The only problem I have is my Microsoft blue tooth mouse does not work.

I could never make 8.10 work on my Sony laptop due to some graphic problems.  I have to say 9.04 worked out great!

:)

---

### Post by Cowpoke on 2009-04-27
I went from 8.10 to 9.04 over the weekend.  8.10 was working very well, the upgrade to 8.10 was flawless.  9.04, not so; my computer boots, but I get no sign-in prompt; I have retried a few times; I am stuck looking at the mouse pointer in the center of my screen; it moves (which is very nice); but there are no menus, context menus...  there is nothing!

Is there a way to boot into a 'safe-mode'?

Ride on...
Cowpoke

---

### Post by ranch hand on 2009-04-27
When the boot first starts (goes from bios to boot) hit escape to see your menu.  Choose recovery mode.

---

### Post by ranch hand on 2009-04-27
I did a clean install of both 32 and 64 so I could reformat to ext4.  No problem at all.  Seems to love my box.

I still use Hardy as my primary OS but I have dropped Intrepid and replaced it completely with Jaunty for my 2nd choice.

The improvements seem to be small but the overal effect is very, very nice.  I will be very comfortable, if this type of improvement continues to switch my primary to the next LTS.

+1

---

### Post by TheropodWatcher on 2009-04-27
9.0.4 was a bad idea from my point of view.
Problem one: upgraded existing long-running system. Immediately, saves took so long the screen greyed out, but completed. I was planning on buying a new computer with more memory next day so didn't worry much about it (512M in old system, which was due to become a backup)

Problem two: installed on new machine, as dual boot with Vista (so I could actually see what it was like, since system came with it). Could not not change default home page on Firefox. Worse, could not download anything other than from Canonical archive without error to affect that "/tmp/somenumber" hasn't enough space. Delete files or save to another location" but no way to change save target! Even doing so in Firefox preferences failed - would not accept change. Couldn't load anything other than from archive.:confused:

Problem three: re-installed 8.10 over 9.0.4. System hung (I blame 9.0.4) Retried 8.10 installation after killing machine, only way to break hang. Installed perfectly, but Vista totally gone (not all bad, that). Now running just fine, no more problems, with 8.10. I'll be staying with that until forums assure me that Jaunty Jakalope is working much better (Jerking Jackass was what I started calling it). Have never run into this much trouble with an Ubuntu upgrade.

Note: I did make recovery disks of the Vista "you may make one set only". Just the attitude difference between that approach and Ubuntu's will keep me running Linux rather than Windows for some time.

Now I've reported in, will go see how others have fared.
 Regards,
 Brad

---

### Post by kiprit on 2009-04-27
I made an upgrade from 8.10 to 9.04 . The upgrade itself was flawless. Everything went smoothly... (even i had a pleasant surprise: with 8.10 I had struggled really hard to have digikam 0.10 work on gnome, and had failed. With jaunty it came default... yip yip!)

But after the upgrade I am running through a very strange problem. Certain actions take a veeery long time. For example it takes about one minute to have awn manager started. On the other hand, much heavier -ram / processor consuming programs start at the speed of light... I mean, while waiting for gnome panel properties to open, I can open firefox - thunderbird - ooo writer, digikam and gimp... one after the other; none of them suffers from any slowness. 

I keep checking system monitor, nothing seems awkward. So far I am hoping to be saved by a future upgrade... because I am not seeing anything wrong.

---

### Post by stonis on 2009-04-27
There was some problems during update. Slapd complained that it failed to configure and when I pressed to report a bug it crashed.
KDE 4 was huge disappointment from the begining. Moving to 4.2.2 is no different. There are some many things wrong I do not know even where to start. For example:
o) everything become transparent, so it is no longer possible to see the window that has focus. However, all transparency and all desktop effects are turned off
o) both dolphin and konqueror become so slow, that are no longer usable

---

### Post by Mr_bleu on 2009-04-27
Upgraded via synaptic.  Waited for install to finish and tried running Eternal Lands.  Saw an error message mentioning "fence" or something.  Tried running cvs version of Eternal Lands.  Another fence error.  I tried various work arounds posted in another thread.  Downloaded another kernel.  wasted a day trying to get Jaunty to work w/ Eternal Lands.  Broke out the 8.10 cd and did a fresh install.  Downloaded the needed files to play EL.  Downloaded the cvs files.  Compiled the game and it works.  No intel graphics errors.  No Jaunty for me until the drivers for mesa or intel are fixed.

---

### Post by Wintersdark on 2009-04-27
Was running 8.10 Intrepid; upgraded to 9.04 Jaunty via Update Manager.  Everything appeared to run smoothly, until reboot.

After reboot, the system starts up, I get the Ubuntu logo, until the "* Reading files needed to boot" point, at which point I get an error message regarding reading from /dev/sda (my hard drive; the only drive in the system).  The hard drive is partitioned into two partitions - an ext3 boot partition and a resierfs partition functioning as a network shared drive.  Obviously, Ubuntu can read it or it wouldn't go so far in the boot process.  Not sure what's going on there.

This happens with either available kernel version and in regular and recovery mode.

I'm not bothering to mess with it, though, and am currently making a livecd usb stick (no cd drives on my Ubuntu box) to format ext4 and try a clean install.  

We'll see how the clean install goes :)

I should have known better, though.  OS upgrades are a finicky beast at the best of times.

---

### Post by sloppyc on 2009-04-27
> **sloppyc said:**
> I tried to reinstall from the regular CD, thinking maybe I screwed something up last night when I installed after sharing a few bottles of wine with my wife.

Nope.  Did it sober, still useless.  I can login, I see my background for a moment (/home is shared between Ubuntu and a couple other distributions), then it all goes white.  Nothing I can do.

I've tried a "*dpkg-reconfigure xserver-xorg*" to no avail.  My xorg.conf is pretty sparse, my monitor and graphics card don't appear in there at all.  Strange.

I may have to skip this version.  That's okay though, I'll just pretend it doesn't exist.  Jackalopes aren't real, anyway.

Okay!  Seems my main problems with the 9.04 were all my fault, and not that of the installer!

I had a permissions issue with my /home folder (I've got one /home partition that is shared amongst two other distributions that I'm playing around with).  User and Group IDs didn't all match up.  I fixed that, it's not something the typical user would run into, nor is it a problem with Ubuntu.  It would, however, be nice if during installation, linux distros would recognize each other as being installed, and do a simple check for UIDs.

Which brings me to my list of bugs in 9.04's installer:
Didn't detect user accounts to import from.  8.10 did.  I thought it'd be particularly easy for 9.04, since now I'm sharing a /home partition with openSUSE and Fedora.

Partitioner had problems noticing any other OS installations.  Not a problem for me as I choose the "manual" option, but for the person that chooses "auto," it may be.

But it was quick, and there were probably fewer clicks to get the job done (particularly with the timezone screen).

All's running nicely, haven't run into any problems yet.

---

### Post by enigmatic28 on 2009-04-27
Hi all,

I currently installed kubuntu 9.04 on my laptop, i know that my GPU (ATI X200M) is already under ATI's legacy GPU..

is there a way to make XBMC and MythTV to work in my laptop?

XBMC and MythTV are the only one left on my to-do list to properly use my system.

one thing that i know is to fix this is to downgrade back to Intrepid but i don't want to do so since my system feels much stable with Jaunty vs Intrepid.

this is the only issue that i have encountered after a fresh installation of Jaunty on my laptop..

thanks...

---

### Post by jimdhall2 on 2009-04-27
I upgraded my desktop 8.10 to 9.04 with no problems.  However trying an online upgrade to my server yielded the following errors:

Errors were encountered while processing:
 console-setup
 kbd
 ubuntu-minimal
 pm-utils
 hal
 gnome-mount

Could not install the upgrades 

The upgrade is now aborted. Your system could be in an unusable 
state. A recovery will run now (dpkg --configure -a). 

Please report this bug against the 'update-manager' package and 
include the files in /var/log/dist-upgrade/ in the bug report. 
E:Sub-process /usr/bin/dpkg returned an error code (1) 

Setting up console-setup (1.28ubuntu8) ...
 * Setting up console font and keymap...                                        



and it just hangs at this point.  I can log in from the console or using ssh from my desktop unit with no problems.  Any suggestions as to how I can fix these errors would be appreciated!

---

### Post by spinwood on 2009-04-27
Dedicated convert unable to do an upgrade.  :(

As seen in:

[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=767064&highlight=Failed+to+add+the+CD+There+was+a+error+adding+the+CD%2C+the+upgrade+will+abort.+Please+report+this+as+a+bug+if+this+is+a+valid+Ubuntu+CD.+The+error+message+was%3A+%27Unable+to+locate+any+package+files%2C+perhaps+this+is+-a+Ubuntu+Disc+OR+the+wrong+architecture%3F%27
[/COLOR]

---

### Post by Gaballufix on 2009-04-27
The update went pretty well.  It took a while to download all the packages, but the Installation went quickly.  While running 9.04, I noticed it wasn't as responsive as 8.10 had been on the same system.  

I had it completely freeze twice. Once while my wife was working on our checkbook and once while I was adjusting the display settings.  In both cases, the screen froze in such a way as the mouse was responsive and nothing else was.  I don't know if it has anything to do with the fact that I'm working with a Wubi install, or that I've got an ATI chipset (which I heard can have problems.)

For the time being, I'm back on Intrepid, but eagerly awaiting the updates that will make me able to upgrade.  I really liked what I saw before it froze.  Also, I'm still a bit new to Ubuntu- if I missed something, any advice would be welcome.

---

### Post by jejones3141 on 2009-04-28
I'm upgrading my wife's computer from 8.10 to 9.04, and it's stuck at the end of the "Getting new packages" stage. It claims to be downloading the last of the packages it says it needs, but no net activity is going on.

---

### Post by hyperzahranism on 2009-04-28
i installed the jaunty again but now i hve a bigger problem

No hardware detected at all 

i feel that jaunty is little pit heavier & it takes time when asking for simple action 


but talking honestly the graphics & the resolution is much much better than ever

---

### Post by Messyhair42 on 2009-04-28
I've been tweaking things that were a bit glitchy at first after the install, but nearly everything is back to what Intrepid was like. Jaunty itself i think is an improvement. the one thing i have yet to do is try virtualazation of some manner in order to get photoshop to work.

---

### Post by developer on 2009-04-28
I've just upgraded to UBUNTU 9.04 from UBUNTU 8.10 but I've got many problem such as the destop effect doesn't work...!!!
I'm thinking of reinstall everything from the beginning

---

### Post by Blara on 2009-04-28
Fresh install of Jaunty and I got some problems:

USB 2.0 won't work, this may be due to me having plugged in a USB 1.1 PCI card without realizing it (I tried it out a few weeks ago and never got around to unplugging it)
no FGLRX for my ATI card due to ATI dropping development of it, so I've decided to revert back to 8.04 and wait for a 3D enabled open source driver instead, and that will feel very nice :)

---

### Post by Merkaba_ZA on 2009-04-28
I had absolutely no errors with my clean install of Jaunty except for a few of the icons in the notification area getting a bit jumbled about but that got sorted out in a few minutes.  Overall it installed smoothly and within 90 minutes my system was completely set up and customised.

A friend of mine also installed it and its an entirely different story for him with constant crashes every 10 minutes.  Needless to say its turned him off Jaunty completely.  Not sure what the root cause is other than a general hardware problem.

---

### Post by pa7two on 2009-04-28
Upgraded from UBUNTU 8.10 to v9.04. Toshiba laptop, Intel videocard, dual boot UBUNTU & WinXP. Downloaded new packages via the Update manager. 
Problems occured in Brasero burner tool, Java and Flash. Removed swfdec flash related items and (re-)installed Shockwave Flash 1.0 r22. But unfortunately Flash really crappy still in Firefox. 
I wait with two other PCs until these Flash and video driver problems are resolved.

---

### Post by fibo112358 on 2009-04-28
I upgraded to 9.04 through the update manager, and I lost my system. I seem to have lost xwindows (startx doesn't work at command line) or something, so I am now in the process of pulling my files off my external hd with Ubuntu installed on it. I would like to emphasize that this was a system I had enough trust in to make it my main os. It had my dissertation and a lot of very important research papers on it, which luckily I am able to recover. I will be switching to another distro because I can't afford the risk, and will be much more weary of "upgrades" in the future. I thought I was learning much about Linux through Ubuntu, but I am completely helpless here.

My question is, why would the developers of Ubuntu send out an upgrade that would render the desktop/graphics of a system inoperable? A few threads I have read seem to point to the graphics card driver, but this is something I don't know how to fix and don't really have the time to learn about. I would be patient and wait for updates and fixes, but does this really help when I can't even bring up the desktop?  

I thought an upgrade left what you had in place and made your system better. I was expecting a new updated machine, completely trusting the automated updates from Synaptic and update manager. When it asked me if I would like to upgrade, I ok'd it and did this to my own machine. I don't know why they would make this version available through a seemingly innocuous update when it is not ready for release yet. Hopefully these problems make their way through this community forum to the developers who need to hear about them.

---

### Post by lisati on 2009-04-28
> **zaivala said:**
> I couldn't even get it to install -- WUBI would not run, started sending a slough of error messages, and I had to delete two Python programs in my Windows Program Manager to get my system back.  I tried it both by downloading WUBI from wubi-installer.org AND by downloading Ubuntu from Ubuntu.com and running the ISO using Daemon Tools.  I started a topic under Absolute Beginners, "WUBI, WUBI, WUBI Do Ya Hate Me?" -- no responses.

[https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

---

### Post by cjshelley on 2009-04-28
Upgraded from Intrepid - I only have sound in OSS, with an error upon opening Amarok that says ALC888 Analog doesn't work, going back to default or something. Flash doesn't work anymore, either. I've spent an hour looking at the forums and these problems have been addressed, but not solved. Furthermore, the beep upon shut down/restart is obnoxious, however it's supposed to signify to me that there's a problem.... what's the problem!? Something else I noticed is that I had to enable the FGLRX driver to change the appearance of GnomeDo, something I didn't have to do with Hardy OR Intrepid. I keep FGLRX deactivated because it has never worked properly.

---

### Post by skotos on 2009-04-28
First time since 7.10, that upgrade did not start arguing with me for somewhat reason: as in the good old 6.x/7.x days!

Almost completely unattended! So cool!

I experimented some minor issues with

[LIST]
[*]the new Nvidia 180 driver that did not like the previous xorg.conf (that I am still updating with the many dual monitors configurations I have been successfully using for years)
[*]Amarok that was not able to play podcasts after the first stop ([http://ubuntuforums.org/showthread.php?t=1138252](http://ubuntuforums.org/showthread.php?t=1138252))
[*]the undraggable gnome-panel ([http://ubuntuforums.org/showthread.php?t=1139434](http://ubuntuforums.org/showthread.php?t=1139434))
[*]audio/video reproduction ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578))
[/LIST]
***It would be incredibly nice if the sound system started working just out of the box as at the old 6.x/7.x days...** It is simply really annoying to always face the same screen and audio problems you had when running Linux in the early 90's!*
No Windoze users will ever switch definitely to GNU/Linux if this nightmare goes on for long.
(This recurrent Ubuntu audio nightmare reminds me I felt the urge to have a forums stable account because of this. I had been successfully running Ubuntu since 6.06 and I had got no need but to read a few posts to solve my problems: then 7.10 and 8.04 came and the multimedia stress with them; consequently, the need to discuss the problems and the possible solutions within the community)

Indeed, it was great when I realized that - for the first time - my notebook **Bluetooth** and **multi-types card reader** devices had been automatically discovered and configured.

Last but not least!

[LIST]
[*]**Amarok** has been upgraded to version** 2**
[*]**OpenOffice** to version **3**!
[/LIST]
(I had been in fact evaluating alternatives to start natively running these _long awaited_ stable apps in a way or another)

To conclude my report: _the overall impression is positive and makes me feel more optimistic about the future updates_. Though I think consistency is still a goal to achieve, Jaunty seems to be far better than the previous 8.x distros! Thanks a lot, Ubuntu team!:)

---

### Post by pgdave on 2009-04-28
Upgraded from Intrepid. I have a ATI2600 video card. I half expected trouble, and got it in spades. As usual, the graphics didn't work after upgrade. Rebooted in recovery mode, and ran xfix. Previously this worked, and give me un-accelerated graphics  - now it doesn't. System now completely f*****d, no method of booting it even. I see some weird graphics at the top of the monitor, and that's it. Sigh... this message brought to you by courtesy of Microsoft...

Come on guys, even if you can't run ATI cards at full rate, at least test the upgrade on a PC with an ATI card. They're hardly rare, are they?

---

### Post by skotos on 2009-04-28
> **pgdave said:**
> Upgraded from Intrepid. I have a ATI2600 video card. I half expected trouble, and got it in spades. As usual, the graphics didn't work after upgrade. Rebooted in recovery mode, and ran xfix. Previously this worked, and give me un-accelerated graphics  - now it doesn't. System now completely f*****d, no method of booting it even. I see some weird graphics at the top of the monitor, and that's it. Sigh... this message brought to you by courtesy of Microsoft...

Come on guys, even if you can't run ATI cards at full rate, at least test the upgrade on a PC with an ATI card. They're hardly rare, are they?
I would suggest you the following[php]sudo dpkg-reconfigure -phigh xserver-xorg[/php]Then, if the X Window system boots up, I would try out my always beloved EnvyNG: it has always solved my Nvidia problems and it works for ATI cards, too.

---

### Post by pa7two on 2009-04-28
> **skotos said:**
> I would suggest you the following[php]sudo dpkg-reconfigure -phigh xserver-xorg[/php]Then, if the X Window system boots up, I would try out my always beloved EnvyNG: it has always solved my Nvidia problems and it works for ATI cards, too.

This was the Driver info I was looking for! Thanks!

---

### Post by johnvoisey on 2009-04-28
Upgrading eleonex webbook.

The webbook has been a bit of a rollercoaster experience, it came preloaded with hardy, self-destructed inside a week and sat idle for ages as I had no factory reinstall until I got an intrepid boot usb drive from elonex last month. Things went well until last week I auto-upgraded gnome-network manager and kissed goodnight to my usb g3 modem and the wader tool designed for the usb stick modems failed to find it.....

With no way back (I cound not see any instructions on how to undo an auto update) I wondered if jaunty was a way forward. The upgrade has gone ok BUT the xorg screen is well wierd, the web book guru alan bell found out why (bug in the via chrome config). I have many years experience in using linux, but I've never used ubuntu and unlike slackware, arch and fedora i can't EASILY find a wiki explaining how I can grab the video driver source so I can reconfigure it and rebuild it with alan's patch.

I'll spend another day or two trying to hunt down a "where to start tinkering with your ubuntu system" forum or wiki but after that I think it'll be back to some other distro ....

---

### Post by rbkhanna on 2009-04-28
Just installed the system. Seems to be working fine. How do I configure my wireless network on it. The network was working fine with the previous version Kubuntu 8.1. On scan I get eth1 as connected to the network but it does not appear on my task bar or work with my browsers. HELP!!!

a novice

---

### Post by muhannadfa on 2009-04-28
installing fresh jaunty on Toshiba satellite notebook, intel pentium 915g,

proplem is, connot connect internet > connot solve problem
any help here

---

### Post by David Robertson on 2009-04-28
Brilliant

I now experience a 30 second boot from Grub ESC to Desktop. (it's a quarter of the time under 8.10). Applications load in seconds (OpenOffice takes a bit longer the first time, but that is understandable and it's not that long). Suspend / Hibernation fail, but power management works and with a 30 second boot doesn't matter. My notebook is now exceptionally cold.

Last time I experienced this was 18 years ago under Windows For WorkGroups 3.11 under very heavy tuning.

Wireless authentication now just works from desktop start - thanks
Stupid wireless card (that use to require ndiswrapper muck around or kernel patch) now just work under B43 - thanks

9.04 is heaps better than 8.10 that was heaps better than 8.04 that was heaps better than 7.10 ... 

Thanks

---

### Post by automaton26 on 2009-04-28
I did a fresh install of Kubuntu AMD64 onto a Dell Studio XPS 435MT, to dual boot with Vista x64.

1) During installation, I got a warning about "Error informing the kernel about modifications to partition /dev/sda5 -- Device or resource busy" but I just ignored it and carried on. All that happened was that my drive mappings for /windows (ntfs) and /data (ntfs) weren't created, but you can just mount/unmount them directly from Dolphin anyway.

2) Also thought that sound wasn't working, but found that I just had to use the mixer to max out all the volume levels, then it was fine.

3) Proprietary ATI Catalyst driver installed without problems. Firefox + Flash worked immediately - yes !

4) I use a static IP so, as with Intrepid previously, it was easier to remove NetworkManager and install wicd instead (and it's in the repositories too).

5) Disappointed to find that mplayer is still a really old version though, without the "scaletempo" audio filter.

6) Disappointed to find that wine is still a really old version too - can more resources be put into getting the repositories up-to-date ?

But now I'm generally jaunty.  :biggrin:

Big thanks to all involved - now I'll wait until the next LTS release.

---

### Post by mkaz on 2009-04-28
Had 8.04 running perfectly. Upgraded first to 8.10 and then immediately to 9.04. Those are the issues I encountered, some solved some not:

1. After upgrading the system did not boot any more. root could not mount any more. Searching the forums brought up a solution by adding rootdelay=90 to the grub.conf file.
System now was booting up.

2. The system booted but was very sluggish. Hard disk activity LED was ON constantly. Then a tracker window pop up declaring the index is corrupt. Reindex does not work and neither does cancel. Searched the forum and this was happening on other systems as well. Solution was to stop the tracker processes and then delete the tracker cache and files. 
Log out and log in again, tracker issue solved.

3. Hard disk still constantly on and system still sluggish. Googled for the issue and installed iotop in order to find the culprit.
iotop showed that gconfd-2 was accessing the disk constantly. The forum recommends deleting the configuration by deleting the ~/.gconf directory.
Rebooted and checked with iotop. gconfd-2 had calmed down.

4. But - the HD Led is still on and now beagled took over first place in iotop.
Uninstalled beagle and rebooted.
With both gconfd-2 normal and beagle gone, iotop seems kind of normal. No process is taking first place constantly.

5. HD still constantly on and initial boot phase is very long, displaying a few error messages and the continuing.
My hunch is that both issues are related and caused by HD or HD channel.
Searching the forums shows others are experiencing similar issues. I'm shutting down the system in order to explore HD connections.
Turns out that HD was connected fine but my 2 CD/DVD IDE drives were connected to the secondary (instead of primary) IDE. This is valid, but since a few others found out that an empty primary IDE and a used secondary could cause issues in Ubuntu, I'm changing the setting and connect both drives to the primary.
Boot up and voila - boot is fast and without a glitch and after Ubuntu is up, HD LED is off. Led goes on only if there is HD activity, as it should.

This upgrade to 9.04 was far from smooth, lot's of issues and still not all solved. Quite a difference when compared to the extremely smooth upgrade to 8.04 that I did a year ago. Maybe I should have waited a month more.
At work we have a few more Ubuntu machines, I'll wait with the upgrade until I see a more stable and bug free 9.04.

Michael

---

### Post by phubai on 2009-04-28
I'm very pleased overall with jaunty with the unfortunately notable exception of graphics. I had a reasonable graphics experience in 8.10 by using proprietary ATI driver, as a choice, and I no longer have that option. Unfortunately, for me, it's a deal-breaker and I'm moving back to Mint 6.0 until such time as I'm able to restore graphics in Ubuntu. I don't understand why the ability to utilize proprietary graphics (at least for the older FireGL Mobility T2 cards) was removed? I mean I understand the 9.04 is the latest/greatest from ATI for linux, but it won't work with my card, so I should have a choice. The proprietary driver available in 8.10 worked very well for me. What happened to that one? Shouldn't it still be in the repos? Is it a compatibility issue?

---

### Post by macpointman on 2009-04-28
My ATI machine upgraded just fine.  I am not sure what the major differences are.

It seems like ATI has ironed out most of its Linux issues.  Upgrade worked fine for me on my PC.  Just had to reactivate and reconfigure compiz after rebooting.  My personal installation is within Windows and works like a charm.  I am not sure what the difference is from doing a clean install or an upgrade.

Now I am having issues with Nvidia on My mothers machine. All I get when trying to activate the NVIDIA drivers is the old Black screen of death. or the computer freezes up.  My mothers is single installation no other operating systems.  All other drives have been disconnected.  I would like to get all the bells and whistles going for my mom though she doesnt need them getting the NVIDIA drivers will definitely make things look better and operate a bit smoother from an aesthetic standpoint.

I cant wait for the next LTS version though 9.04 seems much better than 8.10 even after an upgrade.  I still have much to learn about Linux.  LTS versions seem to work much better.
  
MacPointMan

---

### Post by Tuxoid on 2009-04-28
It worked better than any other upgrade of Ubuntu I've done on my laptop to date. I heard that those with intel video chipsets would have some issues with performance, and while my native games are running much faster than they did in intrepid, my wine games are running at half the speed they would on intrepid. Even a game as old as starcraft is running at a speed unsuitable for playing.

Besides the slowdown in wine games, Jaunty is running fairly well for me.

---

### Post by egwest on 2009-04-28
upgraded, nearly everything works good, but my Atheros AR242x wireless no longer works, I cannot even get up going.
I think as soon as I get over the urge to rip out the OS by hand, I am going to re-install 8.10.

---

### Post by euphemus on 2009-04-28
It took forever for "Hardly" to settle, then
"Increpit" was such a let down - but finally got there...
Now the "Jaundiced Jackass" (Its me feeling jaded and Jadiced!) or JJ for short - so far it has been a breeze - updated well - installed no trouble - only thing is a small problem with KDE ap notifications (windows need to be resized to view them - bug reps already in) and Transmission cannot be set to "unlimited" download/upload speed (someone will do it).

Otherwise... Just Jaunty! (Jaunty sound sooo Afrikaans!)   :P

---

### Post by euphemus on 2009-04-28
> **muhannadfa said:**
> installing fresh jaunty on Toshiba satellite notebook, intel pentium 915g,

proplem is, connot connect internet > connot solve problem
any help here

I had that problem after upgrade - full boot and it went away. Maybe the obvious - maybe not helpful?!?!

---

### Post by LeakyInkPen on 2009-04-28
I have never had much success with performin upgrades, so I had a fresh copy on a usb drive just in case things got bannanas.  Things went... impressively well.  There were some issues to iron out of course, but that was after the install.  

#1- 9.04 failed to see the new kernel and was booting up with the old splash screens.  A quick reconfigure of menu.lst solved that to where it is now running perfectly

#2- The upgrade also blew out my 3rd party software sources list (eg. wine, medibuntu, etc.), I guess if I had thought for half a second I would have been expecting that, but if thinking for myself was my strong suit then I would be off using some other distro

#3- Well, the thing about #3 is that... well, there is no number 3.  

This has been the easiest switch to a new release I have had in 3.5 years.  So far everything is rock stable, there doesn't seem to be much in the way of significant changes (besides boot time), but that is the best "feature" so far.  I am not having to relearn how to ride the bicycle, it just feels like the bicycle got more efficient. Good job guys, can't wait for the Koala!

cpu- Core 2 duo/E8400
motherboard- Gigabit EP45-UD3P
graphics- EVGA 9500GT
4gb ram

---

### Post by euphemus on 2009-04-28
"Good job guys, can't wait for the Koala!"

I hope they call it "KILLER!":P

---

### Post by apostate on 2009-04-28
So,

Jaunty might be the best OS I've ever used, seriously. 

Except....there's always an *except* with Ubuntu anymore, sadly. I don't know if this is a Compiz issue, a Driver issue, or what but I have two glaring issues. I am using the 64-bit addition, as I have 6 G of memory now, and it has quirks. However, issue #2 below was a problem on 32-bit too.

1. Firefox. When scrolling, the text of the page going by doesn't redraw properly. Even on this very page. Peoples' Ubuntu beans are drawn right through their names, or text is garbled/missing.

2. Java apps + Compiz + Nvidia 180 driver = FATAL CRASH

If I open Netbeans and SQL Explorer at the same time, the desktop will get graphical corruption, become unresponsive, and within seconds go to it's knees and lock hard. I am thinking of putting in a bug report as soon as I know where. I am thinking NVIDIA, but as another poster cogently pointed out, using the 173 driver isn't even as stable as it was in Intrepid, so some of the burden has to be shouldered by Ubuntu I fear.

I may have to go with the 32-bit edition with the 173 driver, and sacrifice 2 gigs of RAM. I can't live the sketchiness of this 64-bit distro. I keep thinking, any day now 64-bit OSes will come into their own. It's the latest thing, after all.  Nope. Not yet.

** EDIT **

I have just enabled this repository: [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

Halleluja! Halleluja! Hallllaaaaaa - luja!!!! It works. Multiple Java apps, smooth-scrolling, 3D accelarted lightning-fast-sexiness. Someone at Canonical, give this man a job.

---

### Post by Skeorx13 on 2009-04-28
Well I have two systems I tried to install jaunty on. One was an upgrade from intrepid. Worked pretty much flawlessly but when I rebooted the first time I got the tracker error loop that wouldn't go away. Booted it up the other day and it never came back. Azureus, however, still won't open. Just shuts down right away. I'm pretty sure it is still the same java issue that it had before. I haven't had time to putz around with it though to see if I can get it working. nvidia driver 180 is loaded and working. I still have to get some time to see if my 1080p files will run with vdpau and the new mplayer. This is pretty much the sole reason for me upgrading.

My other system wasn't so lucky. I have a raid0 with xp on it and another drive with a non-booting ntfs partition. I tried to install jaunty on the empty space on the single drive but the ntfs was at the beginning and grub has a stick up it's butt apparently about being first in line. Had to move the ntfs partition to the back of the drive, copy the new ext4 partition to the front, delete the old ext4 partition, and reinstall grub. That didn't work so I deleted the ext4 partition and reinstalled again. Worked this time but I still have to configure dmraid so I can actually boot to the OS of my choice without going into the bios each time. Haven't had a chance to configure my dual monitors yet either.

I really like the new graphic and layout of the login screen though.

---

### Post by egwest on 2009-04-28
> **egwest said:**
> upgraded, nearly everything works good, but my Atheros AR242x wireless no longer works, I cannot even get up going.
I think as soon as I get over the urge to rip out the OS by hand, I am going to re-install 8.10.

Got my wifi working on my Toshiba A205-S5843!! After some serious Google searching I came across this site:

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

I followed it and now my AR242x card is detected and working at full speed!

Sooo...guess I will stick with Jaunty after all.:P

---

### Post by egwest on 2009-04-28
> **muhannadfa said:**
> installing fresh jaunty on Toshiba satellite notebook, intel pentium 915g,

proplem is, connot connect internet > connot solve problem
any help here

I was having the same problem on my Toshiba I found this site and followed the directions here and got my wifi working:

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

---

### Post by dragos_iliescu_2005 on 2009-04-28
Install ok on HP Compaq 6715b the testing Ubuntu 9.04. Solve the sound problem after by upgrade alsa.
Upgrade failed on desktop - no ati driver. The big problem.

---

### Post by jstalnak on 2009-04-28
Upgraded system unusable -- boots to gnome desktop, but the video is hosed (I can tell that it's displaying the wallpaper I have set by the colors that I see) and the keyboard/mouse become unresponsive. I have to manually power down with power button.  Nothing seems to work to fix the issue. dpkg-reconfigure -phigh xserver does not work.  Using an older xorg.conf with fglrx drivers doesn't work. Using an explicit reference to the ati driver in the xorg.conf file doesn't work. Right now, my desktop is, frankly, useless. I'm typing this on my laptop, which, thankfully, has not been updated to 9.  Though I've been a Linux user for years, and an ubuntu user for two years, I don't know what to do now, as everthing else I've tried has failed.

---

### Post by sweetnsourbkr on 2009-04-28
Two computers, both failed.

First, an Acer Aspire One netbook (A110) with the SSD.  The LiveUSB key media check registered 1 faulty file, but during the live desktop, the keyboard wouldn't work.  The upgrade path using the Update Manager ends in errors after about 5 hours of operations--which require supervision because of repeating dialogs.

Second, a desktop system will not boot the LiveCD.  It ends with a 'modules.dep' missing error, and a limited command prompt.  I can't give more details because I don't know what the problem is, and to list all the hardware here would be difficult since I'm at work.

Deal breaker on Jaunty, as Intrepid was practically flawless.  Seems like the Jaunty release was rushed, and not properly tested. :(

---

### Post by hockman5 on 2009-04-28
> **jstalnak said:**
> Upgraded system unusable -- boots to gnome desktop, but the video is hosed (I can tell that it's displaying the wallpaper I have set by the colors that I see) and the keyboard/mouse become unresponsive. I have to manually power down with power button.  Nothing seems to work to fix the issue. dpkg-reconfigure -phigh xserver does not work.  Using an older xorg.conf with fglrx drivers doesn't work. Using an explicit reference to the ati driver in the xorg.conf file doesn't work. Right now, my desktop is, frankly, useless. I'm typing this on my laptop, which, thankfully, has not been updated to 9.  Though I've been a Linux user for years, and an ubuntu user for two years, I don't know what to do now, as everthing else I've tried has failed.
Same here, and when I went to go backward to 8.10, I reinstalled and got the dreaded grub error 2. Had to run fixmbr in windows and am stuck with that for now. I am tired of messing with this after 4 days and give up for now.

---

### Post by AlanPo on 2009-04-28
> **LeakyInkPen said:**
> I have never had much success with performin upgrades, so I had a fresh copy on a usb drive just in case things got bannanas.  Things went... impressively well.  There were some issues to iron out of course, but that was after the install.  
#1- 9.04 failed to see the new kernel and was booting up with the old splash screens.  A quick reconfigure of menu.lst solved that to where it is now running perfectly
#2- The upgrade also blew out my 3rd party software sources list (eg. wine, medibuntu, etc.), I guess if I had thought for half a second I would have been expecting that, but if thinking for myself was my strong suit then I would be off using some other distro
#3- Well, the thing about #3 is that... well, there is no number 3.  


I can add few things I am not able to resolve after upgrade:
1. filename with russian characters causes disk check and asking for ROOT password to do manual disk check. Never had one in ubuntu, so not able to boot at all. And why just not correct the error? file was in /Documents folder.

2. Installing russian language support is not possible because after that you can choose menu language only russian (in system/administration/language support). And musteriously menus un gnome are english, but open office and vuze is completely russian.

---

### Post by andycarroll on 2009-04-28
I have just upgraded to jaunty jackalope.

I would like to thank the whole community.
im sure a huge amount of time and effort is used providing such an excellent commodity to so many people you have never met and who will never repay the favor.

I am very grateful and a little touched.

excellent work!
also thanks to everybody who asks the questions so i don't have to.

---

### Post by JohnPta on 2009-04-28
I have a problem with upgrading to 9.04. The Upgrade manager is telling me it can not find the cdrom with 7.04 However why is the software looking for that cd while I am running Release 8.04 With the Kernel Linux 2.6.24-24-generic? I did upgrade last year from 7.04 to 8.04 without any problem. 

I get the same error message when I try to upgrade to 8.10 as intermediate to get to 9.04. Further more I have the same problem with my notebook computer running 8.10 there the software can also NOT find the Cdrom when I try to upgrade to 9.04.

---

### Post by pgdave on 2009-04-28
> **skotos said:**
> I would suggest you the following[php]sudo dpkg-reconfigure -phigh xserver-xorg[/php]Then, if the X Window system boots up, I would try out my always beloved EnvyNG: it has always solved my Nvidia problems and it works for ATI cards, too.
Thanks for the suggestion, but it had no effect at all.

---

### Post by paapereira on 2009-04-28
Add some troubles in my desktop machine. There were several errors during the upgrade and after rebooting no joy...

Found a solution here in the Forums.

I have a [blog post]("http://lofspot.net/blog/2009/4/27/upgrading-to-ubuntu-904-jaunty-jackalope-on-the-desktop.html") about this. Feel free to check it out.

But basically it was very easy to resolve the problems and I have everything in the right place.

Nice work!! :)

---

### Post by paapereira on 2009-04-28
> **jimdhall2 said:**
> I upgraded my desktop 8.10 to 9.04 with no problems.  However trying an online upgrade to my server yielded the following errors:

Errors were encountered while processing:
 console-setup
 kbd
 ubuntu-minimal
 pm-utils
 hal
 gnome-mount

Could not install the upgrades 

The upgrade is now aborted. Your system could be in an unusable 
state. A recovery will run now (dpkg --configure -a). 

Please report this bug against the 'update-manager' package and 
include the files in /var/log/dist-upgrade/ in the bug report. 
E:Sub-process /usr/bin/dpkg returned an error code (1) 

Setting up console-setup (1.28ubuntu8) ...
 * Setting up console font and keymap...                                        



and it just hangs at this point.  I can log in from the console or using ssh from my desktop unit with no problems.  Any suggestions as to how I can fix these errors would be appreciated!

I also had [problems upgrading]("http://lofspot.net/blog/2009/4/27/upgrading-to-ubuntu-904-jaunty-jackalope-on-the-desktop.html"). 

Try [this]("http://ubuntuforums.org/showthread.php?t=1136740").

---

### Post by elektronaut on 2009-04-28
> **JohnPta said:**
> I have a problem with upgrading to 9.04. The Upgrade manager is telling me it can not find the cdrom with 7.04 However why is the software looking for that cd while I am running Release 8.04 With the Kernel Linux 2.6.24-24-generic? I did upgrade last year from 7.04 to 8.04 without any problem. 

I get the same error message when I try to upgrade to 8.10 as intermediate to get to 9.04. Further more I have the same problem with my notebook computer running 8.10 there the software can also NOT find the Cdrom when I try to upgrade to 9.04.

Sounds like you should check your /etc/apt/sources.list. The CD-ROM is most likely mentioned there and should be deleted or commented out.

---

### Post by joecool0998 on 2009-04-28
upgraded using update manager no probs and i have an ATI card (Radeon express 220m) as well.
great!

joe:lolflag:

---

### Post by RDouglasC on 2009-04-28
I have been using Ubuntu for a few years and have never been able to upgrade. (always had to install from the CD). So I copied a VM and tried it again... success, tried a second and third VM and both of those worked. On to the Desktops... feeling brave with 3 successes... both of my desktops worked as well. I have one minor problem that I can't seem to fix. I use Spambayes which works with 9.04 and Python 2.6 but fails when you train messages... not a major problem.

---

### Post by RDV on 2009-04-28
As I only use my SPDIF connection for audio, I had disabled pulseaudio under Ubuntu 8.10 (pulseaudio does not play well with AC3 Passthough). 

Using ALSA only I could switch back and forth between a PCM audio source to an AC3/DTS source using passthough with no problems.

Since upgrading to Jaunty (again disabling pulseaudio) anytime I play a PCM audio source AC3 passthough will not work. If I restart the ALSA server AC3 passthough will work again. A PCM audio source always plays without issue.

To say the least this is frustrating. So far I have not seen anyone else with this problem.

The actual upgrade to Jaunty did work well on three computers including an eeePC 701 4G. The issue described above is my only major issue.

---

### Post by reedness on 2009-04-28
The login screen looks a lot better, it boots up very quickly.  It has a new theme that I really like too.  It's great.  At this point, there's only 2 issues.  Most important one being that I used to be able to use Pidgin to connect to my work's Jabber account.  Now, it accepts the certificate, and says I'm connected, but I'm not.  I can't see anyone and they can't see me.

Also, wireless in Kubuntu is teh fail.

---

### Post by ubnoobie on 2009-04-28
hit by the sigmatel audio problem on 9.04 -- went back to 8.10.

---

### Post by JSeglem on 2009-04-28
Generally the install was pretty user friendly. It was first Ubuntu install. I've been using opensuse for about a year. I have both running on my Lenovo laptop. I let the install process do the partition. "Update Manager" keeps popping up but the message is that I don't have enough disk space. I guess the partition is not quite right. I have an 80GB hard drive and it looks like it split about 60/20. I'm not sure how to best resolve that and not disrupt my opensuse.

---

### Post by rmartinus on 2009-04-28
Fresh install for me. The only problem I had so far was VPN connection error message, saying that "there were no valid VPN secrets". Adding refuse-eap string and setting it to Yes in gconf solved this problem. I think this option should be available as a checkbox in the VPN GUI.
Other than that, this release seems to be really stable and I can really notice the speedy bootup & login time.

---

### Post by cooldudeman01 on 2009-04-28
My sound is completely jacked, it's got static/distortion playing behind everything I try and play back.  Really annoying, and really loud.  I haven't been able to fix it now for about a week.  Running on a Dell D620 Dual boot with Windoze.  Sound works in windoze and it worked in 8.10, but not the upgraded Ubuntu.  I tried reinstalling Alsa and Pulseaudio and about 200 other suggestions from searching the net.  I don't see anyone else having any problem like I'm seeing, so I might try reinstalling Ubuntu from CD... gah...

---

### Post by esalnoj on 2009-04-28
Jseglem:

If your partition editor works in Opensuse, try splitting off a blank portion of your 80GB. 

Then install 9.04 and use "largest continuous free space" option.

-Esalnoj

---

### Post by bmartin on 2009-04-28
I did a fresh install on two desktops (a new one I built myself and a 4-yr-old eMachines). All hardware works for both of them; one has an ATI video card, and the other an NVIDIA chipset. The NVIDIA chipset works great OOTB. The ATI card (which is now considered legacy, even though it's only about 2 years old) performed so poorly that I ordered a new NVIDIA card from newegg.com. In the meantime, I messed around with the PC, trying to get the video to stop running at 5 FPS and managed to brick the install. After a reinstall, I modified my xorg.conf like so
```
Section "Device"
	Identifier	"Configured Video Device"
        Option		"AccelMethod" "XAA"
EndSection
```
and, like magic, there was a huge boost in performance.

I will never buy a computer with an ATI chipset again, ever.

---

### Post by domeng on 2009-04-28
Tried upgrading via Ubuntu alternative disc but it keeps on connecting to the net. I checked on my data, everything is backed up and no hassle doing a reinstall so I cancelled the update and did a clean install from normal desktop image.

As usual, problems with the b43 firmware and nvidia driver but something I could not fix easily.

---

### Post by undfined on 2009-04-29
I upgraded my 2 desktops.  1 is a plain-jane i386 install.  No fancy hardware - the install went as smooth as I could ask for.  Right on.

My 64 bit server has been a bit of a struggle.  Partly because of my ignorance and partly because of some strange issues:

1.) I decided to try using the nVidia SATA RAID on my motherboard for mirroring.  I was able to install normally after activating the RAID.  Then I re-installed through the normal dektop ISO image (I now know this is a no-no).  I noticed RAID wasn't working so I ended up following a HOWTO, adjusted grub to reboot from the raid pair and hoped I could rebuild the second drive.  As I now know, this doesn't work.  But it seems to me it could - since all I needed was a utility to tell the hardware the second drive is new and needs to be rebuilt.  I ended up futzing with it for a couple hours before moving on burning an alternate installation CD.

2.) I want to use XDMCP, since it's native, to log into the 64 bit machine.  Since it only servers files and openssh I simply want to plug it into the wall and have a 802.11g USB stick attach the machine to the network.  After the Alternate CD install it took some futzing with the "Authorizations" application (under Syetem...Administration) to get the machine to log in to the wireless network prior to a user login.  I think that's a feature I struggled with before as well.  But once that was done I was able to log in remotely - but got this weird session: the top panel's letters were upside down.  Terminal sessions were upside down.  The trash can was upside down.  It was funny, but not workable.  And in hindsight I think it was probably because of the nVidia video driver (180, I believe).   In my tired, upside down haze I reinstalled with the alternate CD.

So today I'm back up and running, finally got my files moved over to the RAID mirror, and am ready to start serving.  In fact this writing is from an XDMCP session over ethernet* - although I'm afraid to load the nVidia drivers, which kinda sucks because I can't see a lot of the administration windows in an 800x600 when hooked up to the monitor.

1 issue I have is I can't figure out is how to administer users in the GUI over XDMCP - I can't unlock the panel.  I'll do a search later - but I would think it nice if the account I setup in the install process would have the right to manage all facets of the system, even remotely - after entering in the proper credentials, of course.

Anyways, I'm 90% there.  Still need to get some file flow and media streaming happening but all in all my 3 machines (laptop is still forcing me to do work instead of tinkering) are doing what they need to.  Nice!

*manual static IP addressing over ethernet still requiers a workaround, and since I'm brain dumping I'll mention it instead linking back to the solution:: disable Auto eth0 from logging in automatically, create new Wired Connection 1 by copying MAC address from Auto eth0, and set IP addressing appropriately.  Use the enter key after typing in each address (IP, netmask, and gateway - otherwise they disappear).

---

### Post by Gooorn on 2009-04-29
Hi.

I just upgraded first of my upgrade pending laptops and it worked flawlessly. It's Aces AspireOne, first edition 9" with Ubuntu 8.10 without any funny repos and without Netbook Remix (I did not like it much).

There was only one regression and it's WLAN activity led which just begun to function with one of the latest 8.10 upgrades but now it's gone again.
Don't get me wrong, I don't care for it nor I'm considering this as a bad thing. I just want to mention it.

Thank you all for such a great work on Jaunty. For me it's a best looking Ubuntu ever. The rest of the features I need to test more.

Sinisa Perovic

---

### Post by randogauci on 2009-04-29
Hi all,
Did a clean install of 9.04 remix on EEE-PC 1002HA and everything is working except for very low sound from speakers!!!!
I have tried all the settings in the sound applet but no difference. At present I have it set on auto and I can hear sound through earphones ok!
Regards to allhttp://ubuntuforums.org/images/smilies/confused.gif

---

### Post by Timpotten on 2009-04-29
On updating from 8.10 to 9.04 the following warning appeared:

**Third party sources disabled**

Some third party entries in your sources.list were disabled. 
You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.


I have not yet found out which packages were disabled - could this be a bit more informative?

**Tracker failed**, and the only way to fix it seems to be - first to stop the warnings,[(*,) use:

System> Admin >System Monitor and **kill any Tracker process**

(Maybe this endless loop should be broken by killing the process rather than hogging the display with uninterruptible warnings?)

Finally search Ubuntu to see how to remove Tracker permanently until someone finds a fix.

My main work-tool Open Office was a complete mess of missing (thesaurus) or dysfunctional (formatting) components: I had to open 

System> Admin > Synaptic

and actually **"completely remove" every installed OpenOffice component,** delete the profile manually and then reload 
**(the "reinstall" had made no difference)**

Although I was strongly advised to install from an OO download, the instructions for this this were console commands and not very clear. Fortunately the Synaptic/Ubuntu installation worked

**Disappointing** to have waste a day fixing an ìmproved' system that previously worked - maybe continuous innovation would be more stable than new releases? 

Although I will probably stick with Ubuntu for now (it is a great platform - especially since I have to use XP as well)  but I think I will probably not upgrade it again once I get it stable, since any improvement is rather minor (I have not noticed any practical advantage yet, and even it seem a bit slower than 8.10, so it probably has lots of junk to be weeded out -when I have the time) 

Linux is free of monetary cost, but the time investment simply is not worth the disruption and frustration of the wasted day each half year fiddling with change for change sake. The main body of the Ubuntu distro already works just fine.

Hope this helps others!

---

### Post by ullaspa on 2009-04-29
Hi,
Fresh install over a previous Intrepid that was working very well. Now on Jaunty with EXT4 and the experience has been terrible. This is on a Dell Vostro 1510.

First, the keyboard and the touchpad refuse to get detected from a cold boot. One has to carefully press the capslock or a random key just when the boot-up screen starts to have them detected. Apparently Vostro's touchpad is internally a PS-2. But, it still worked flawlessly on Intrepid.

Second, random system freezes with no recovery. Everything gets frozen and even the REISUB trick fails as the keyboard is also inactive. Have to hold the power button to switch-off and boot again. Suspected it to be the desktop effects and turned it off. No luck, still.

Third, the typing caret gets shifted at random. Result is text getting typed where it was not intended, somewhere in between a paragraph. I had to do about 5-6 corrections to get this message typed out and typically about 20 times on OpenOffice page.

Probably the worst Ubuntu experience I have had. Seriously thinking of moving back to Intrepid till patches are released. But moving again is too painful!

Regards,
Ulhas

---

### Post by ranch hand on 2009-04-29
I love this thread.  I check the poll every day.

I can't believe that folks upgrade instead of doing a clean install with a backed  up /home.  It is so much faster and easier.

Juanty is also built for the ext4 format and upgrading is going to be wierd.  I installed both the 32 and the 64 editions.  I tried the 32 on ext3.  It works burt not like it does on ext4.

My primary OS is still Hardy and will be untill 10.04 (The next LST).  I like both Intrepid and I think that Jaunty is a real step up too.  Hardy is nice, stable and LST.

Jaunty has, already become my second (or play) OS.

I keep hearing about "having to upgrade Ubuntu every 6 months".  Why?  The interim releases are nice but I(ntrepid will reach its end of support with 10.04 and Hardy will still have a year left.  I figure to upgrade sometime in May or June next year.

Untill then I will play with these fine OSs like Intrepid and Jaunty.  I will work with Hardy.  When I upgrade I will do a clean install and then transfer what I need to from Hardy or where ever I have it stored.

---

### Post by VictorR on 2009-04-29
After frustrating experience with upgrading to Intrepid 6 months ago, I was very cautious about upgrading to Jaunty. So I burned a live-CD and tried it first. What I got was a black screen and a message about crashed Nautilus. Fortunately Firefox worked well and I has access to the Internet. The solution I found was to disable Brasero module with this command:
```
sudo chmod a-r /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so
```
After fixing Nautilus the rest worked just fine, Jaunty even found and downloaded a driver for my NVidia 4 MX440 card and enabled visual effects.
So I upgraded 8.10 to 9.04 using alternate CD and got perfectly working system with all my custom settings saved.
So far only GIMP does not want to start from Gnome panel (?), although it is not broken and works fine from terminal.

Big thanks to all developers for their great job!

---

### Post by juise- on 2009-04-29
Had a quite a bit of problems upgrading from hardy to jaunty but finally got it working, I wrote my survival story here: [http://ubuntuforums.org/showthread.php?t=1142401]("http://ubuntuforums.org/showthread.php?t=1142401")

---

### Post by stonis on 2009-04-29
Upgraded laptop. The horror. KDE was upgraded to 4. According to forums it should not upgrade. Now it looks so horrible and and is so slow.
Is there any way to switch to KDE 3.5?
I assume the only one other option is to install Gnome.

---

### Post by union two levers on 2009-04-29
first time trying to upgrade rather than a clean install,mainly cos i dual boot with windows xp and i didn't understand how to get rid of 8.10 and install 9.04 in its place. The upgrade was dead easy, worryingly so in fact. only prob so far seems that sane scanner utility wont work my canon mp610 scanner whereas 9.04 running as a live cd did allow the scanner to work...will have to look into that problem, also now my belkin N1 wireless usb adapter works...yippee

---

### Post by dmm1983 on 2009-04-29
i actually was running kubuntu 9.04 back in the beta stage.
Then where i attend decieded to mirror the reps.

my laptop runs very well. using ext4.

---

### Post by dmm1983 on 2009-04-29
i actually was running kubuntu 9.04 back in the beta stage.
Then where i attend decieded to mirror the reps.

my laptop runs very well. using ext4.

---

### Post by jarrah-95 on 2009-04-29
i did a clean install of junty and only had a few minor problems:
my falut:
       i downloaded the wrong disk to upgrade from disk hence i did a clean install
actual problems:
   couldent connect to my 3g modem 
[http://ubuntuforums.org/showthread.php?t=1135073](http://ubuntuforums.org/showthread.php?t=1135073)
[http://ubuntuforums.org/showthread.php?t=1136712](http://ubuntuforums.org/showthread.php?t=1136712)
but i managed to fix them by downloading the files for wvdial in a windows machine (wish i dident need to)
but now its all working perfictaly (way better than 8.10)
i downloaded it in half an hour using free download manager

---

### Post by Chuckels550 on 2009-04-29
I upgraded from Mythbuntu 8.10 AMD64 to 9.04 AMD64.  As usual, it did not go flawlessly.  I lost my wireless connection along with the wireless network interface and trying to fix it has created more problems.  I fixed the wireless problem by doing a full install and then installing wicd. 

The /etc/modprobe.conf file now prevents the modprobe command from working because the file is not a list of modules to make active, but options for some device.  The audio is no longer working, but I haven't had a chance to troubleshoot that.  When I configured the Nvidia restricted driver to output 1080i as I have it in 8.10, after the reboot the machine locked up faster that I can read the dmesg output, which means I will probably do another clean install and then try to figure out why the nvidia drivers aren't working properly.  What a mess!

---

### Post by kosen on 2009-04-29
I'm using an Atom-based netbook with Ubuntu and a desktop PC with Kubuntu. Both have integrated Intel graphics. I had to roll back to 2.4 Intel drivers after upgrading to Jaunty on both. Aside from that, I haven't noticed any problems yet.

---

### Post by OzOle on 2009-04-29
Did a fresh install of Ubuntu 9.04 on HP 2133 Mini-Note (netbook). I installed the proprietary Broadcom STA wireless driver as suggested. I was also using that in Ubuntu 8.10 where it worked flawlessly. 

When installation was finished I rebooted and great, it worked and after entering pw I was on the Net again.  :popcorn:

BUT..... after a while without doing anything, suddenly the wireless connection was lost and no matter what I tried to get it to reconnect, absolutely no joy   :confused:

After a new reboot I was again on the Net, great :popcorn:

But after another while the connection was again lost   :confused:

What is going on?
I don't really feel like having to reboot every time the wireless connection goes down.
Perhaps I should have stayed with 8.10 for a while and let somebody else have these problems and fixes being made.  :(

Oh, well, otherwise I think everything else looks great.  :guitar:

---

### Post by zool2005 on 2009-04-29
I did a clean install to test out EXT4 support and I wanted to try the 64-bit edition (finally!).
The install was fine with no problems to fix and the system feels really responsive and boots in 26 seconds according to bootchart.
I must admit I have quite a simple ("compatible") system so I rarely have any problems even with the upgrades.

System specs :

AMD Athlon X2 5600+
2GB RAM
2 x 120 GB SATA HDD (Jaunty / Win XP)
Ethernet LAN connection with Static IP
USB Mouse/Keyboard
Scanner : Canon LiDE 60
Printer : HP5500

That said, I'll wait a little before trying it out on my Aspire One until more people have posted their experiences.

---

### Post by ubuntumaybe on 2009-04-29
Hi,

I downloaded the regular live cd edition then I found out that I needed the alternative cd. After a search I finally located it then found the faulty instructions on this page,
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading).

Under 'Upgrading Using the Alternate CD/DVD'

sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0

gksu "sh /cdrom/cdromupgrade"

This line should be gksu "sh /media/cdrom0/cdromupgrade".

Once this was corrected it run and performed all the updates. 

It removed some packages I had installed, including modifying my menu entries. My compiz icon is gone.

It boots quicker which is a big plus.

---

### Post by -jay- on 2009-04-29
mine was great just can no longer suspend or shutdown i have to shutdown from my towers power button i check my bios but have no idea what i need to disable or enable

---

### Post by lannatwin on 2009-04-29
It was hell.  Did afresh install on two machines.  Never could get them to talk to each other (samba) correctly.  Tried everything I could find on the forums.  struggled with it for two days, I'm reinstalling 8.10 as I write this. :(

---

### Post by FirstByté on 2009-04-29
> **tolachi said:**
> I am having the same problem with a blank screen and no keyboard response.  I've tried copying over with the original xorg.conf file and generating a new one, but no luck.

This obviously would [/might] have been solved along the thread. I'm posting this here 'cause I was too lazy to read through it all.

First, a commendable effort done by the Ubuntu team! I'm forever indebted to thee. Buying those tee-shirts @ the [Canonical Ubuntu Shop]("http://shop.ubuntu.com/") is just not enough.

**PROBLEM CASE:**

I had a smooth upgrade to Ubuntu 9.04 Junty a couple days ago (after release) from 8.10 Intrepid. Though it took 8hrs<--Did it overnight :P.

All seem well except for my lost 'Visual Effect' capability. 
This I tried to rectify by Installing 'xorg-driver-fglrx' from the Synaptic Package Manager.

I couldn't carry this out initially, since I made an [online] upgrade. It kept asking for the CD so I had to download and burn the iso.

Everything went well till the next time I had a reboot and.... a ugly blank/black screen swept my beautiful new log-on screen away.

my lspci | grep VGA returns

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: 
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

to fix my debut graphics problem, I shelled to RECOVERY MODE at grub and straight way to **root** to straight way remove the poison I installed earlier

This alone was unable to norm the venom

```

sudo dpkg-reconfigure xserver-org
```

This fixed the whole snag.
```

sudo apt-get remove --purge xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg

```

Above all, Ubuntu distros seem to be leaning gradually towards a much graphical appeal like the bug-nut Vista and related. Thumbs up guys!


**UNRESOLVED ISSUES:**
I ran Ubuntu 8.04 (Hardy) and 8.10 (Intrepid) on my previous hp laptop and the remote works out of the box.

But ever since I switched to a lovelier Dell, REMOTE feature seems to have died. It didn't work with Intrepid on my Dell Studio.
I thought quietly that this would be fixed by the new Ubuntu 9.04 Jaunty, However, this has not been resolved.


**Specs:**
Distro: Ubuntu 9.04 Jaunty
Movement: Upgrade from Ubuntu 8.10 Intrepid
Machine: Dell Studio 14 [Intel T6400, 32bit]
Video Card: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by prinze on 2009-04-29
Fresh Install on I386 worked flawlessly no issues at all now exploring the OS installedd for the first time happy to be out of Windows...

---

### Post by henwyn on 2009-04-29
I had more problems than normal going through testing with Jaunty. I started with Alpha 3, which installed but wouldn't boot. I then upgraded an installation that had started with Kubuntu Dapper Drake to Alpha 4 and have continually upgraded it to the current one that I am posting from. 

Problems in testing were primarily video and audio and are currently working fine. Pulse audio had problems right up to release and anyone interested might want to check out the testing Pulse Audio thread for some insight into how hard they were working on these issues and why we are using pulse audio now. [http://ubuntuforums.org/showthread.php?t=1084919](http://ubuntuforums.org/showthread.php?t=1084919)

There were also some problems with individual programs, specifically Firefox and Amarok for me. The problems with Amarok seem to have been caused by an add-on which downloaded album covers from Amazon and may have done some other stuff, but it made sound start and stop and vary in speed and it's gone. The Firefox problems (program and sometimes the screen freezing) were probably caused by one of the add-ons on it, too. They have all been recently upgraded as well and the problems seem to be gone. 

Yesterday, I upgraded my other Intrepid installation on this computer (Gnome) with no problems. Props to the folks who have been working so hard to get this out. Diagnosing and fixing problems on all sorts of hardware and widely varying software installations is a hell of a job and they not only do it well but manage to keep their temper in the face of pressure and demands from all sides, which is more than I could do. Hats off.

---

### Post by ETChipotle on 2009-04-29
Installed Jaunty on old Asus A7N8X, one of the early revisions that doesn't have an option to boot from USB devices.  Was able to use the wired internet out of the box, and was notified that my wireless card had drivers available for it.  When I clicked to install the Broadcom 43XX wireless drivers, they installed without error, but because the card doesn't have the antenna on it, and doesn't support WPA2 I haven't tested it out.

:)

---

### Post by emarkay on 2009-04-29
Yhis is mindboggling - this far into Ubuntu and it has totally screwed the pooch on one of my machines - something was slupped thru that affected my ATI/AMD HD2600 craphics card - that worked fine before in the prior release.  

I spent many hours on this last night, and finally removed all teh native drivers and installed the Catalyst one from the AMD site - still no good.

There's a lot of talk, but no answers.


Let's get all the Jaunty 9.04 ATI HD 2 series card data on one post to get this solved:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by Samilong on 2009-04-29
I've been on a regular six-month upgrade path since Version 5.10. Normally, the install goes smoothly. 

Then, with 8.10, the upgrade hated my graphics card, an nvidia MX4, and I lost all 3D capabilities (which prevented me playing most of the games I liked - Sauerbrauten, FooBillard, and others). This is still unresolved...

With 9.04, my problem is Mice! I upgraded, and over the next few days added a few updates. Monday evening, I switched the computer off. Tuesday, I switched it back on, and had no mouse. I unplugged it, plugged it back in - ah, the wonder of USB! - and it returned; however, shortly thereafter, the cursor began to drift of it's own free will. The direction of drift varies with each reboot, as does the length of time before drift starts. 

I need to get to the bottom of this, though, as it is driving me mad, and making the computer unusable... ](*,)


***Ha! Wouldn't you just know it. My problem with the mice turned out to be unrelated to the upgrade - it was just a knackered mouse. Replaced it, and it worked fine... until I tried to use streaming video/audio websites (see page 64)




Computer: Handmade AMD Athlon 3200+/1Gb Ram/500Gb HDD
Upgrade: 8.10 > 9.04

---

### Post by TobbeR on 2009-04-29
Tried to upgrade but in the middle of it I lost my mouse and keyboard !!!
Had to power down with a useless box. Downloaded the ISO and made a fresh install, I have my /home on a separate partition, and everything seem to work for now. I have had some bad upgrade experience during my years with Ubuntu but this was really to much.
T

---

### Post by TobbeR on 2009-04-29
... and another thing, GLXGEARS show 200 fps against 1200 fps for 8.10.
Don't mind that, I'm no gamer, but something is broken .
T

---

### Post by btunell on 2009-04-29
Upgrade seemed to go well on my home system, but the system halted after boot, with a message stating the drive couldn't be found. 

Haven't had a chance to follow up with it yet.

---

### Post by OdinHammer on 2009-04-29
I had no problem going a clean install on virtual box machine, i cant wait to do a clean install on my actual laptop an acer 5680.

---

### Post by mgmiller on 2009-04-29
I really wanted to report a flawless upgrade, but my sound didn't work.  I had to open sound preferences and disable and enable a few of the optional switches.  Finally, by moving my front audio slider up from 50% to 100%, I got my sound back.  In fact, I now get sound events for button presses and other system sounds that have been missing since 7.04.  Other than that, it changed my desktop cube back to a desktop wall, but that's not really problem.  A quick trip to simple-ccsm fixed it.

I see it still has the samba browsing bug.  I always try setting the /etc/samba.smb.conf back to the package maintainers version to see if it works right, but it never does.  I have to edit the line that says:
  ```
; name resolve order = lmhosts host wins bcast
```

so it says:
   ```
name resolve order = lmhosts wins bcast host
```

Then samba works quickly and smoothly.

As you can see, I have upgraded my system a lot and this is about as smooth as it gets, but not flawless......yet.

---

### Post by peaeye1 on 2009-04-29
As a beginner this is likely a simple problem, but after successful install, on reboot I get the following:

MP BIOS BUG 8254 Timer not connected to IO-APIC

Boot Args (cat/proc/cmdline)
Check root delay=(did the system wait long enough?)
Check root=(Did system wait for right device?)
Missing Modules (cat/proc/modules;ls/dev)
ALERT! /dev/disk/by-uuid/ddf9259a-a162-4db4-bc01-4e81e95cfb2c does not exist

I do find ref to the drive and its companion drive - Have tried ain.7xxx ain.7xxx=no_probe but falls back to command line.  Basically same with Server or desktop.  This is being installed on a Dell 1550/1000 server P3 dual processor, 1G memory, Dual SCSI 16G drives. I disabled floppy and CD drive works fine.  I have installed 8.04 on a Gateway 550 previously with no problems.  Don't have a clue as to the problem.

---

### Post by TFrog on 2009-04-29
After holding off on Intrepid Ibex (Kubuntu), I went ahead and attempted installation on my Compaq Presario R4125US laptop.  First I attempted the AMD64 version.  After only an hour or so on my laptop it had continual crashes.  Couldn't even run Gimp on it not to mention the new updater had a tendency to lock the system to the point of having to resort to a hard reset (power off using the power button then restart it).  This didn't include the powermanager not working which it did NOT work in either version.  Next up, I attempted the i386 version.  There I was able to run it for about a day till I started looking at the plasmoids that monitor the system and started crashing.  This is where I noticed the fans running constantly at high speed on the laptop.  One plasmoid confirmed that my CPU was running flat out at 2200Mhz which is the high end for it.  It would not cycle down via ACPI.  The i386 version also started experiencing crashes as well.  I've since stepped back to Hardy Heron.  I certainly hope they get KDE and the other issues fixed by 9.10.  I loved what I saw but am unable to run it on this laptop due to the issues with ACPI power management.  I especially loved the plasmoids for weather and monitoring your network connections.

---

### Post by Dexhu on 2009-04-29
I had many Problems Upgrading to Jaunty Jackalope!
I got several Errors and did posting to Launchpad
now I can NOT KDE4 to install!
how can I redo the Upgrade and get it fully installed?
I still want to keep my previous settings and software kept!

ERROR MSG: Not all updates can be installed!
Can't install 'kubuntu-kde4-desktop'

---

### Post by ardensdrunk on 2009-04-29
upgrade worked flawlessly

i was honestly kinda scared that it would mess up my compiz settings or my dock bar or any of the other various personalized things i had done, but it went perfect

took about 30-45 mins from time i started the upgrade (via update manager) until it rebooted to my desktop

everything works as expected

---

### Post by flugh on 2009-04-29
I wish I could give a big thumbs-up and "no problemo" install report, but sadly, this isn't the case.

I run a Dell XPS M1710. 8.10 installed, everything worked flawlessly out of the box (enabled restricted drivers to get the nvidia drivers).

A fresh 9.04 yielded much hair-pulling. No detection of the nvidia card. No sound. And my AT&T USBConnect 811 modem continually resets (utmsmon didn't work either, but since I was running both as root and as sudo-enabled user, have to assume it's a modem driver problem).

The modem was a deal-breaker for me. The other issues could be resolved with a fair amount of monkeying about (although I liked the ho-hum, out-of-the-box method from 8.10 ;) ).

It LOOKED great, and seemed to boot a good bit quicker than I'm used to, but, alas, I'll be reinstalling 8.10 this evening and waiting on 9.10.

---

### Post by TobbeR on 2009-04-29
Third post, and I gave up. To sluggish as my internal graphics card (Intel) is not supported. Reinstalled 8.10 and had a hard time getting my sound back but now everything works again. Glxgears back to 1200 fps and the nice eye candy looks good.
T

---

### Post by Brad Heathman on 2009-04-29
I have unresolved problems with MediaWiki and NetBeans since the upgrade.

---

### Post by lisati on 2009-04-29
Not my first post on this thred.....this is kinda like an update. Success (or otherwise) for me seems to be at least partly related to which machine I use.

My experiences include a big "thumbs up" (Ubuntu Sudio 64-bit, haven't used it much so far, so not many chances to notice problems) through a couple of failry minor annoyances (drum sounds repeating or taking longer than usuall to quit on one machine, seems to happen on 8.10 as well, hangning on shutdown/restart on another machine, seems to be related to the WiFi card) to a big "What the.....?" (a pile of error messages) trying to install via Wubi on the machine I currently have Ubuntu Studio on. (bug report duly filed at launchpad)

---

### Post by thenewmexican on 2009-04-29
Install. Horrible.

Always get ata1: softreset  (device not ready).

Then. The boot drops to a shell. In which I have no idea what to do.

So. As of 04/29/2009. Could not accomplish a full install.

Tried an install of openSUSE11.1 on same hardware. Zero problems.
So. This is clearly an Ubuntu issue.

---

### Post by Vrekk on 2009-04-29
Personally i wasnt able to do the upgrade with the manager, the program would get an error with downloading one of the updates.
I was finally able to upgrade by download the alterative install disc and mouting it. After that some of my programs stoped working right and the tracker wont index my files.

---

### Post by dfour on 2009-04-29
Extremely fast and easy install on both my desktop and laptop. Best release I've seen so far.

However, it did refuse to give me an install screen until I disconnected my second monitor.

---

### Post by deboh on 2009-04-29
[B]''No valid Mirror found
    While scanning your repository no mirror entry for the update information was found. This can happen if you run a internal mirror or if the mirror information is out of date.
    Do you want to rewrite 'sources.list file' anyway? If you choose 'yes' it will update all 'intrepid' to 'jaunty' entries. If you select 'no' the update will cancel.[/B]
   
 
the above was what i got while trying to upgrade from 8.10 to 9.04 via a mirror deb upgrade as provided for me from my community linux based internet provided using the friefunk software in order for me to have a faster upgrade, and so i clicked ''YES'' and restarted my update manager, everything seem to go on fine but eventually when i expected things to work out i got a sort of system check and realized that my graphics card was being tampered with, long story short, i do not know if i have successfully upgraded because my graphics quality has been reverted to default and now i see nothing when ubuntu starts up except the orange-brown background that comes up after the splash screen, i dual booth xp and ubuntu and the graphics card seem to be fine when i boothed into Xp but it wont show me a thing wheni booth into ubuntu. i have no idea what this is or what i should do. i need help.

---

### Post by doas777 on 2009-04-29
I seriously love Jaunty. I've found 4 things thus far, that have never worked correctly for me (despite many attempts to address them), that now magically do. they include:

[LIST=1]
[*]Atheros wifi magically works for the first time ever, OOB.
[*]Nvidia Twinview works correctly with simple nvidia-settings changes.
[*]the integrated VNC server now can use passwords to force login (previously failed whenever a passwd was applied).
[*]laptop boots up without stalls on usb detection, and non-x resolutions work by default as well.
[/LIST]
I had given up on ever getting some of these fixed. I must say, the boot speed improvement is incredible, and the install was verrrrrrrrrry smooth. the only weird thing i've noticed is that for some reason the numberpad on my media box is not being detected, after login (but works fine at login). if i connect via vnc, the numberpad on the host fails as well.

good work folks!

---

### Post by kelt65 on 2009-04-29
My workstation is in a quite complicated environment, NIS and AD (via a commercial product), automounter ... everything went flawlessly.

---

### Post by northwestuntu on 2009-04-29
freezing randomly after fresh install.  had to back to 8.10.  wasted 2 days trying to get 9.04 to work.  guess i'll wait a couple months for whatever is causing the freezing to be worked out.

---

### Post by jamillikan on 2009-04-29
I upgraded from Intrepid to Jaunty.  It downloaded 1974 total files and began the installation process and terminated with the message "system unstable" and did a dpkg reconfigure -a thereafter.

I rebooted and was still, thankfully, in Intrepid and all was well.  I checked synaptic package manager's repositories and they had changed to jaunty.

I did a "mark all upgrades," and apply.  The first time there were several errors.  I still did not reboot.  I ran it two more times until all the apparent issues were resolved and it finished installing the upgrades from the repositories just fine.

I checked to ensure there were no package errors and closed synaptic.  Then, I ran an update.  It said I was up to date.  Then, and only then, I rebooted and I was in Jaunty just fine.  

It's important, I think, to remain calm and thoughtful throughout the process.  I'm really enjoying the improvements in Jaunty and I'm glad that's over.  

Just as an aside, before I even began the upgrade, I used Acronis True Image and imaged my system (and verified the image) before starting, so that was also of comfort because had it failed, who cares?  I would've just restored the image made beforehand.

Everything is functioning as it should:  VMWare Workstation 6.5, samba shares are mounting properly (thank God), and every application I was using previously is working flawlessly.  I also use Terminal Server Client, and I was able to tunnel into my office Windows XP computer just fine.  All's good here.  

Kudos to Mr. Shuttleworth and his professionals for the aesthetics and stability.  It's been the easiest upgrade so far...and I started with Edgy.

FTR, Ubuntu is truly a wonderful Linux distro...and I've tried Fedora, Xandros, Mandriva, SUSE, SLED and PCLinuxOS (I think that's what it was called), and Ubuntu remains my favorite by a long distance.  Your mileage may vary.

Enjoy!

Joe

---

### Post by dbclinton on 2009-04-29
Just installed JJ on my Compaq Evo laptop and it looks good. One sticky point though: perhaps because I didn't have net access during the install Synaptic was acting very strangely until I clicked on "Reload" and then, after full package info was finally downloaded, everything was fine. 
Is there any way to avoid that? I can only imagine how a newbie might react.
Great work,
David

---

### Post by Timokl on 2009-04-29
I did a net upgrade which worked pretty well although not quite flawless. I encountered the following problems:

1) The upgrade had a problem with Skype. So I temporarily de-installed the package.

2) The upgrade did not manage to install all new packages. I forgot the reason because it happened right before I had to leave home for a couple of days. Jaunty booted, but some programms like Tracker complained that something is missing. After I went back home, I opened a terminal and finished the upgrade manually:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install 
sudo dpkg --configure -a   
sudo apt-get autoremove

```

After that, everything worked. Two annoying things that were broken in Intrepid were fixed: F-Stop now imported photos from my Canon EOS 400D directly, and I had Wifi internet access with my Broadcom Wifi card.

My first impression is, that Jaunty is the best Ubuntu available. Thanks to all developers and Canonical for making it happen.

Timo

---

### Post by slumbergod on 2009-04-29
I found performing a clean install of Jaunty to require more fiddling than did Intrepid last time around.

Firstly, I ended up installing it twice because I went to remove network-manager in favour of wicd, which I already had the deb for. Unfortunately, the deb hadn't been updated for python 2.6 so it failed. As I only have wireless in this apartment I had no connection at all and couldn't reinstall the network-manager. Lesson learned, and no problem second time around.

The second issue I had was with the audio on my Acer Aspire laptop. It was really quiet like it was a year ago before the hardware was catered for with backports. In the end, this was solved by getting rid of that pulse audio devil. Now my sound is the correct volume.

The biggest issues I have found to be applications so not the fault of Ubuntu at all. VLC had reverted back to no embedded video (so I had to use a PPA with a testing version), and similar situations with a few other apps.

Boot time is marginally faster but almost unnoticable really - not that it bothers me cos my laptop is on 24/7 most of the time. 

Xfce4.6 is really excellent. I had it in Intrepid but now it is built-in so is smoother and more integrated.

---

### Post by archer6 on 2009-04-30
> **Garrovick said:**
> Did a clean fresh install without a hitch.  Smooth as glass. :popcorn:
On a laptop or desktop? Specs Please...

---

### Post by Gausian on 2009-04-30
I did a clean install.  This is the first time ive installed and had 100% functioning hardware from the start.

in previous releases ive had to configure the touchpad after install, but it worked ootb this time.

Really happy with this release overall.

---

### Post by PaulM1985 on 2009-04-30
Keyboard and mouse no longer work following upgrade. See thread:

[http://ubuntuforums.org/showthread.php?t=1143078](http://ubuntuforums.org/showthread.php?t=1143078)

Any ideas would be brilliant since I really need my computer back.

Paul

---

### Post by dhopley on 2009-04-30
Coming from 8.04 with clean install which was very slick and quick , howvever due to problems with my integrated Intel videocard I've had to shut off desktop effects and automatic screensaver logging to achieve an acceptable on line experience and revert the Intel driver to the 8.10 version . I'm still just about to stay with it but looking back the Intel integrated videocard problems seem to be coming cumulative , still who knows whether the next release will concentrate a bit on this matter .

INTEL CELERON 2.4GHz - 0.5GB RAM - 82865G Integrated Graphics Controller (rev 02)- 80GB HDD - Ubuntu 9.04 32bit

---

### Post by pmenefee on 2009-04-30
Upgrade on a Dell laptop at work.  This install is to a USB hard drive.  The download on a wired network was so slow that I simply left it going all weekend.  The expected time notice at one time said 3 days.

But on Monday morning the download was complete and I had one on screen question to answer, and then the install was complete with no problems.  I was really surprised.

---

### Post by worksofcraft on 2009-04-30
Have been running ubuntu 8.04 for a while on dual boot system. Windows XP on the IDE drive (hda) and Linux on SATA drive (sda).

I replaced the sda with a brand new drive (so as not to risk losing anything) then installed Ubuntu 9.04.

On completion Grub loader simply crashes with error 15.

So I installed Ubuntu 8.04 with exactly the same set of partitions

Everything works just fine :)

I'll post a new thread about grub loader issues. Evidently there is a problem in 9.04 that was not there in 8.04

---

### Post by SteveHillier on 2009-04-30
Install worked a dream.   
Very quick.
I like what I have seen so far.
Well done the development team, testers and everyone involved.

---

### Post by skotos on 2009-04-30
> **phubai said:**
> I'm very pleased overall with jaunty with the unfortunately notable exception of graphics. I had a reasonable graphics experience in 8.10 by using proprietary ATI driver, as a choice, and I no longer have that option. Unfortunately, for me, it's a deal-breaker and I'm moving back to Mint 6.0 until such time as I'm able to restore graphics in Ubuntu. I don't understand why the ability to utilize proprietary graphics (at least for the older FireGL Mobility T2 cards) was removed? I mean I understand the 9.04 is the latest/greatest from ATI for linux, but it won't work with my card, so I should have a choice. The proprietary driver available in 8.10 worked very well for me. What happened to that one? Shouldn't it still be in the repos? Is it a compatibility issue?Have you tried EnvyNG? It is now in the standard repos: it will look for your drivers by itself.

---

### Post by w0ipl on 2009-04-30
The install (I put in a new HD to make it easy) was not as happy as I would have liked. I got the 64 Bit version of 9.04 and was looking forward to trying the ext4 file format. The installer has zero provision for doing that.

I have the Update manager set to "Only notify about updates" but it takes off and does downloads as I work on other items. I really HATE that.

I tried some of the "fixes" (from this forum) to get rid of the 60 second delay on shutdown and NONE of the menu items in those "fixes" exist in the 64 bit version (at least that I can find).

The initial version of Thunderbird would do a header only get of E-mails that were larger than the 50K default (blocking) size. After the last update it now downloads oversize E-mails without asking. I went in to the Preferences and can not find the default blocking size any more.

I was on 8.04 and upgraded to 8.10 about a month ago. 8.04 used one process for shutdown and 8.10 used another. 9.04 changed back to what 8.04 used but added that stupid 60 second delay. I'm about ready to go back to 8.04 and wait until(?) 9.04 "evolves" into something usable. :(

---

### Post by j.daniel on 2009-04-30
**Hi,**

Fresh install, wanted to make an old Win 2k a dual boot machine. I basically had two problems with the install:

1: The live CD failed when starting Ubuntu. I believe that it could not mount the CD rom drive after I chose which way I wanted to start Ubuntu and left me with a busybox prompt and... well nothing else.

I solved it by trying a lot of different things mentioned in these forums and in the end I got ubuntu to boot if I chose either noacpi or nolacpi option (F6 button on the start screen).

The computer is an old dual processor design with built in RAID (four IDE connectors). Booting without "quitet" and "splash" I saw in the log that it said that it was trying to mount the root file system. Then it just froze, no errors nothing and kicked me out into busybox. The CD rom is configured as master on the second IDE bus so I guess that somehow it did not find it.

I tried to disable the built in RAID controller, but no change. The machine booted faster without it though (no BIOS check/startup of the controller) so I left it off.

Strangely enough I got it to start when choosing either noacpi or nolacpi. I have looked in Wikipedia regarding that and that has to do with the sync between the processors on the motherboard (as I said, it is a dual processor machine). So.. go figure. It booted though so I'm happy.

2: Second problem was when I got to the partitioning. I wanted as I said a dual boot machine, however when I got to the partitioner, I was presented with only two main options: format the whole thing or Manual. Further in the manual stage I could just edit or delete partitions, not resize them.

Tried the 8.04 LTS installer as well and same game. After much trial and error I downloaded the GParted live CD and voilalá: it had a small exlamation mark on the partition and the information said that there were problems with the NTFS partition. It even said to run windows and do a chkdsk /f on the drive!

After some reboots (chkdsk needs that) I checked in GParted that all was fine and without doing anything further I restarted the 9.04 installer. All of a sudden I had a lot more options in the partitioning setup and I could proceed from there and set up my dual boot system.

**Improvement suggestions**

The main thing I could think of improving is most obviously that the partitioner in the installer should do something like GParted (guess that the partitioner is using much the same code?) - tell the user that there is a problem with the partition and that cannot do anything else than to reformat the whole thing or suggest running chkdsk /f. As it is right now - if I was a new linux convertee, I would most likely have given up.

Another options would to modify the live CD launcher to catch when you're kicked out into busybox and give the user a few choises: 1 - launch busybox as happens now or 2 - try starting with a few different choices, perhaps even ask the user about his/her system so an intelligent guess could be made about which flags would most likely be required. Heck even have a loop trying all combos until it boots! Would take time, but it would increase the chances of the computer booting at least.

It is better to say that there is a problem and trying to solve it than to dump a potential linux convertee at the command line.

Anyway, my $0.02
/ Daniel

---

### Post by ranch hand on 2009-04-30
You should be able to resize partitions under the "edit" option.  Just change the size in the "partition size" box.

---

### Post by j.daniel on 2009-04-30
> **ranch hand said:**
> You should be able to resize partitions under the "edit" option.  Just change the size in the "partition size" box.

There was no such box in the edit screen: Just a file system selection, a format check box and a mount point text field.

As I said, it had all to do with that the system could not handle a NTFS file system with defects. When I got that fixed with windows it all worked fine. My gripe with the installer's partitioner was that it did not tell me that there was a problem with the partition whatsoever.

/ Daniel

---

### Post by AgedP on 2009-04-30
I have just completed installation/upgrade to 9.04 for the second time but with the same problem each time!
I have to use pppoeconf to connect to my ISP.  This works OK and I have been able to install Nvidia, codecs and other software. Browser is upgraded and works fine. Done it heaps of times.
But after restarting computer I do not have automatic connection to broadband.  And when I try to connect using 'pon dsl-provider' the connection is immediately disconnected.
Here is the output of plog
 
elassed@elassed-ubuntu:~$ plog
Apr 30 23:41:17 elassed-ubuntu pppd[4482]: PPP session is 45531
Apr 30 23:41:17 elassed-ubuntu pppd[4482]: Connected to 00:01:63:1c:ac:38 via interface eth0
Apr 30 23:41:17 elassed-ubuntu pppd[4482]: Using interface ppp2
Apr 30 23:41:17 elassed-ubuntu pppd[4482]: Connect: ppp2 <--> eth0
Apr 30 23:41:18 elassed-ubuntu pppd[3903]: Connection terminated.
Apr 30 23:41:18 elassed-ubuntu pppd[4482]: Remote message: DefaultSimultaneousUse of 1 exceeded
Apr 30 23:41:18 elassed-ubuntu pppd[4482]: PAP authentication failed
Apr 30 23:41:18 elassed-ubuntu pppd[3903]: Modem hangup
Apr 30 23:41:24 elassed-ubuntu pppd[4482]: Connection terminated.
Apr 30 23:41:24 elassed-ubuntu pppd[4482]: Modem hangup

I am using the amd64 version of jaunty on an AMD64 4400+ and  I installed Nvidia 7300GL graphics card.

I have installed Ubuntu and other distro's many times but never had this problem before.   I am hoping someone will be able to suggest an edit to a configuration file.  Don't think I can face another installation.

---

### Post by Mac181 on 2009-04-30
Upgrading seems to have worked fine. Everything that was working still works. Everything that was broken is still broken. I'd call it a wash. :)

---

### Post by kwilliam on 2009-04-30
As in my past experiences, the upgrade tool hung after downloading the very last package, but after killing and restarting it, it went without a hitch.

Unlike past upgrades, this one was literally flawless. Nothing broke at all except for 3 khotkeys shortcuts, which is khotkeys fault since it changed how shortcuts are handled. Sound, X... ALL my packages were upgradeable? That's amazing, usually it's months before my favorite obscure package is available, but no, the only packages removed for the upgrade were some old libraries.

Best of all, the upgrade did more than I ever hoped for! All the graphical glitches with running Firefox in KDE4 are GONE! The KDE3 knetworkmanager is replaced with a slick plasmoid applet! Amarok 2 finally plays sound for me! And it looks like Gnome apps look even better with the new style. I'm in user heaven - it "just worked". (As a geek, I'm slightly disappointed I don't get to spend a week fixing it.)

---

### Post by DannyRux on 2009-04-30
8.10 Worked flawlessly on both my laptop and my desktop.

I upgraded to 9.04 on my desktop and have some interesting problems.

(Let me add I am pretty new to Linux, but none of my machines have ANY other operating system.)

I can no longer navigate my "places".  I'll click on "places" then "computer".  A window tile will show up that says "Opening Computer", will work for a bit, and disappear. 

I thought about updating gnome, which did not work.  

Also, when I go to the update manager I get a critical error that reads: "Not all updates can be installed", and suggests I run a partial upgrade.

I attempt a partial upgrade and it tells me 1 package is to be removed, and 2 will be installed.  

Remove - libdb4.5-java
Install - libdb4.6-java
Install - libdb4.6-java-gcj
Upgrade - liblucene2-java

I click start upgrade, and window disappears and nothing happens.

I still navigate my computer via the terminal, but with these errors happening I can imagine my distro was not installed properly.  Should I just reinstall my distro?  Or even go back to Intrepid Ibex?

---

### Post by ferrian1 on 2009-04-30
I tried to upgrade through the update manager - started out fine, but stalled near the end of the process - machine froze completely.  I now can't boot - get to the log in screen and that works but then I'm stuck on a blank orange screen.
 
Any suggestions on how I can fix the update?  Obviously I can back everything up and do a fresh install but I'd like to avoid that.

---

### Post by DannyRux on 2009-04-30
It also appears my desktop is not functional.  I attempted to drag a Netbeans icon to the desktop and when I let go of the mouse it just disappears.

---

### Post by Auslegung on 2009-04-30
I've been with Ubuntu since 7.10 and have very much enjoyed my experience.  However, Jaunty UNR has pissed me off so bad that I actually logged on to this stupid forum to post this.  I was told Pulse worked like a dream in Jaunty, and Skype is probably the number one reason I upgraded, and of course it still doesn't work.  Not only that, it's worse than it was for me in 8.10.  Now, Rhythmbox skips like I'm playing a CD while mountain biking down Kilimanjaro.

Also, many of my settings were lost, and so were many of my downloaded programs.  I made a backup of my package.selections just in case, and now I can't even dpkg it correctly (that's probably my ignorance, though).  I hate the UNR gui and promptly removed it, but some settings on the mouse and keyboard, which aren't immediately noticeable, were frustrating and had to be changed.  I can't seem to get compiz to work right, and it lost all my settings.  My computer is lagging as though it's using 95% of my memory, but running top in a terminal shows me I'm using less than half.  

All-in-all, the absolute worst upgrade or install for me, and I've had more than a few.  If I hadn't wiped my 8.10, I would DEFINITELY be returning to it.  Stupid me for believing 95% of the net who said Jaunty is the holy grail of Ubuntu.

---

### Post by Cincinnatux on 2009-04-30
I'm still a Linux n00b - After being a Windows user since 1990, I didn't try Linux until Ubuntu Feisty.  By the time I transitioned to Gutsy, I stopped using Windows and haven't looked back.  But the experience has been rocky, and I'd like to say here that I'd much rather have a painless upgrade experience every six months than an ambitious upgrade every six months.  I'm tempted to stick to the LTS releases, though that seems excessively conservative.  

Every six months, I've upgraded to the latest Ubuntu release, and each time I lose functionality that I then have to troubleshoot to restore or give up.  In earlier upgrades, the broken bits were fairly major - broken proprietary video drivers, broken Java functionality, etc.  With Intrepid and Jaunty, the broken bits have been the games I like to play (I lost OpenFracas with Intrepid and Dominion with Jaunty).  But Jaunty has left a few additional hiccoughs along the way - my Thunderbird functionality has been maimed (I had to disable all my add-ons just to get it to work, and now it only recognizes 4 new messages on the server at a time so I have to keep telling it to check again to get the rest) and all of my applications need at least double the time to load up before I can use them.  Intimidatingly, every time I have to enter my password, my system hangs for a few seconds while it thinks about it (sometimes enough for my screen to go grey).  But it still works.

I haven't minded too much because it gives structure to my self-study of Linux, and I'm gradually learning how to play with the OS.  But I'd really like Ubuntu to be able to go toe-to-toe with either Windows or OSX and the regularity with which I lose basic functionality would be unacceptable to anyone who just wants their computer to work.  Windows and OSX, for the most part, just work.  Sure, Windows in a pain in the butt and it gives annoying error messages and often does not do what the user tells it to do, but I cannot remember the last time a regular update caused me to lose video function or Java function or multimedia functionality or rendered games unplayable.  It should take *major* changes to cause problems of this magnitude.  And, yet, as a user I don't perceive major improvements each six months.  I just perceive major losses of function.

Obviously, I need to stop using the latest release of Ubuntu.  But maybe Canonical needs to market the latest release as "for Linux geeks only" and have a separate release for folks who just want things to work and who are willing to be a little lighter on the potential feature set.  Kind of like the way Debian identifies its various unstable and stable releases so it is more clear to users what the risk-to-benefit ratio is.  I'm sticking with Ubuntu specifically because Ubuntu seems most likely to be able to achieve mainstream adoption.  I just wish its efforts were more toward an intuitive, painless experience for n00bs.  CLI is powerful and all, but unlikely to ever be mainstream.  Every time I use CLI to do something, I find myself thinking "there's no way I'd be able to convince casual computer users to do this.  The learning curve is too steep.  Folks expect a more intuitive interface and shallower learning curves."  And yet, even with GUI-intensive Ubuntu, there are times when the CLI is the only effective way to fix problems (and those problems remain common).

Sorry to be so long-winded.  I just wanted to explain why I feel that Canonical is taking Ubuntu in unhelpful directions if their goal is to broaden market share.  Maybe I'm wrong, but these are the things most of my friends point to as reasons why they are uninterested in trying Linux, and *they* are that market share I'm talking about.

---

### Post by Sudofreak on 2009-04-30
I downloaded the latest version of Ubuntu (9.04 -Jaunty) as soon as it became available, and installed on my Dell desktop (XPS 410 with E4300 core 2 duo processor, 4GB RAM, Nvidia GeForce 7300 video card) as soon as I could.  I have 2 other OS installed on this computer (windows xp on the first partition, 2nd NTFS partition for windows on the 2nd partition,
a swap partition on the 3rd partition, LinuxMint on the 5th [1st logical drive in the extended partition].  Ubuntu, obviously, went on the 6th partition (HD0,5).  All went well until I went to reboot.  Much to my chagrin, the grub bootloader failed to recognise my windows installation,
and instead listed Linux Mint as the installation on the first partition (Hd0,0).  The grub menu offered 10 different boot scenerios for the Mint distribution (see attached file listing)
  
[COLOR="Blue"]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e14f5144-ceb2-4f73-93cb-8f007f631cc0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e14f5144-ceb2-4f73-93cb-8f007f631cc0

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e14f5144-ceb2-4f73-93cb-8f007f631cc0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e14f5144-ceb2-4f73-93cb-8f007f631cc0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e14f5144-ceb2-4f73-93cb-8f007f631cc0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e14f5144-ceb2-4f73-93cb-8f007f631cc0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e14f5144-ceb2-4f73-93cb-8f007f631cc0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Linux Mint 6, kernel 2.6.27-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Linux Mint 6, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Linux Mint 6, kernel 2.6.27-7-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Linux Mint 6, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint 6, kernel 2.6.27-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint 6, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint 6, kernel 2.6.27-7-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint 6, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot
[/COLOR]

                     
Of course, I got by this problem by editing the menu.lst file in the grub directory.  Part of the fun of running Linux is troubleshooting and correcting problems (providing you have enough time and don't mind pulling out a little hair).  

Has anyone else encounted a problem like this?  (I would gladly remove my windows installation if I could find a good driver for my Canon Pixma MP980 - which is an excellent printer

---

### Post by marsrover on 2009-04-30
well i have a big problem the os thinks me screen is 4:3 when it's wide screen so i can't do full resulution without black bars at the side HELP

---

### Post by MaskedMarauder on 2009-04-30
I upgraded from 8.10 >>-> 9.04.

Everything seemed to go fine, but when I rebooted it couldn't find the system partition.  When I checked for it I found that the partition had been tagged as swap partition and everything on it was lost.  I had backups, but still....!!

The machine is an IBM T42 Thinkpad.  I have a Windows partition (1), Compaq diagnostics (2), a small linux ext2 (3, about for /boot directory), a swap partition (4) with the rest for ext3 (7).

I've been running ubuntu on the laptop since about 6, and done upgrades without any serious problems until now.  I didn't see any special error messages and have no idea why it clobbered my working partition.

---

### Post by Guilden_NL on 2009-04-30
I have 6 systems to upgrade.  System #1 went perfectly, not one single hitch and it took less than 45 minutes from clicking the Upgrade button to being fully up on Jaunty.

Config for this 'puter:
MSI K8N Neo4 Platinum SLI
AMD64 Athlon 3800+ x2
GSkill 4 x 1GB DDR PC3200
SATA: WD 74GB 10,000RPM; 2x WD 80GB 7,200RPM
eVGA GeForce 7800 GT 256MB
Enermax 600W ATX Power Supply ATX
ThermalTake VA8000 Tower Case
LiteOn DVD Burner IDE
Asus DVD-ROM IDE

---

### Post by MountainX on 2009-04-30
I cannot install Jaunty and I would appreciate some help. 
Here is my thread: [http://ubuntuforums.org/showthread.php?t=1144086](http://ubuntuforums.org/showthread.php?t=1144086)

---

### Post by 47_MasoN_47 on 2009-04-30
So far I've updated my primary desktop at home, my primary desktop at work, and my primary laptop.  I still have 2 laptops, a server, and a secondary desktop to upgrade at home, but both of the upgrades I've done so far have been painless.  The laptop I upgraded originally had 7.04, went to 7.10, 8.04, 8.10, now 9.04 using the upgrade manager and I haven't had any problems at all.

---

### Post by Slick.N on 2009-04-30
Clean install this time, after doing an upgrade for Hardy & Intrepid.

I'm a happy bunny - it all went fine AND I can hibernate for the first time since leaving Windows [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by noahhomsky on 2009-04-30
For some reasons I'm use Ubuntu Server in production and have some BIG troubles.

Physical server upgrade/install:
- Auto installed dmraid - really BAD and crappy thing. After install/upgrade server just wan't boot. When I physically disconnected all my software raid10 disks and purge this package server boot successfully. On server with Adaptec 5805 (real RAID) I have same behavior. It's very bad for upgrading headless servers.
- [This post about mdadm.]("http://blog.creonfx.com/linux/mdadm-raid-failed-after-upgrade-from-ubuntu-810-to-904") No comments.

Virtualised servers (in vmWare ESX cluster):
- Little headache - NFS3/NFS4 mounts in fstab not mounts on boot. But mounts successfully with "mount -a". I post [bug to Launchpad]("https://bugs.launchpad.net/bugs/367675") but it's still "Undecided".
- And again - tons of not needed packages with minimal install (acpid for example).

Resume - bad work. I use Ubuntu in production from Hardy Heron. But now I thinking about change distro.

---

### Post by arkiedan on 2009-04-30
I moved from Windows XP to Ubuntu 8.10 exclusively when it came out. I clean installed it and it's been fantastic. I upgraded to 9.04 this afternoon and I can't find a problem. Everything, I mean everything, is rock solid. I was a little worried about my Virtualbox'Win XP install but it too was fine (by the way....I only use it because my genealogy program, Legacy, needs Windows! My last contact with Microsoft!) 

By the way....I'm a 71 year old coot who hates change but I love this move to Linux and, particularly, to Ubuntu!

arkiedan

---

### Post by Dwood15 on 2009-04-30
I Upgraded from the last version of Ubuntu and.... It won't start... it just says the "Starting Ubuntu" line and I never get anything else out of it.

Well, I was able to get the loading screen to come up by going into safe mode and then 'start normally' however the loading screen only came up for a few seconds, went away and my screen just wouldn't go any further.

---

### Post by johnny2m on 2009-04-30
I did a fresh install of Jaunty a couple of days ago.  I wiped my / partition (previously a Hardy install) and reformatted as ext4.  Left my /home partition alone, ext3.

A few tweaks required as might be expected, a couple of virtual machines no longer want to start in VirtualBox (conversely an virtual install of Debian which never worked before has sprung to life!), but I haven't had a chance to look at this in any detail.

The only real problem I have is with my graphics driver.  With Hardy, I installed the proprietary driver for my card (Radeon HD3450) and after fiddling with the aticonfig file got it to display across my two monitors.  But now I have a problem.  With the propretary ATI/AMD FGLRX driver installed, my system starts really slowly after logging in.  Opening Display settings can freeze the machine.  Also conky appears on my desktop in front of my windows.  A couple of videos I've tried to watch have been choppy and blocky.  Basically it rendered my PC unusable.

Using the open source drivers instead, everything is very snappy, I have none of the above problems, BUT, it won't let me have any visual effects:(  I just get an error "Desktop effects could not be enabled".  I'm not too bothered about most effects, but I do miss my compiz desktop cube!

Apart from that I haven't had much chance to poke around.  Boot up time is around 15% faster, not really noticed a difference once logged in.

---

### Post by c-shadow on 2009-04-30
Fresh install, amd64, nvidia 7600GS. nvidia proprietary drivers with two separate screens.
Xorg crashes almost every time when switching users. Since my wife and I switch a lot during the day, it's unusable for me (at least for now), returned to intrepid.
Everything else seems to be working fine.

---

### Post by johnny2m on 2009-04-30
Oh, it also takes me longer to shutdown as I keep going to System, then pause for a few seconds, then remember the button's been moved!  And my PC produces a very loud beep when it does shutdown.  But now I'm just being picky!

---

### Post by AlanPo on 2009-04-30
Only thing that is not working in Jaunty is language support other than english.  If you install some other, after remove part of it (with system/administration/language support)  you have interrupted boot process with message that locale do not exist.  
Also adding support causes all gnome in that language.  It's not appropriate. I have to write in russian, but why I have to have all menus in russian? Global mess with languages here.

---

### Post by ap90033 on 2009-04-30
ATI Drivers and Jaunty = garbled mess with a 4870X2...

---

### Post by rmartinus on 2009-04-30
I can't get the desktop effects working (compiz) as my laptop graphic card is "Intel 4500MHD Graphics Accelerator". I guess that is expected and I'm hoping they can fix it through update soon.
I can however use this guide ([http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)) to enable it on my laptop by running this command:
>  mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

---

### Post by mkquist on 2009-04-30
Fresh install of Jaunty Jackal.  Just keeps getting better with each release.  Quick and painless.  Back to business in less than an afternoon.

AMD64x2 5600+
Nvidia 8800GT 
Abit AN78GS
4 GB PC8500 1066MHZ
(left it ext3 for now)

Thanks for the good stuff! :)

---

### Post by Samilong on 2009-04-30
Damnation! Just when I thought it was all going so smoothly...

Whenever I try to view streaming video/audio on a website (BBC, CNN, Youtube, or whatever) Firefox crashes and burns.

Trying to decide whether it's a fault with Firefox (3.0.10) or Ubuntu, I used the Epiphany browser. It crashed and burned too... guess something has gone astray somewhere, but where I'm not sure. I suspect gstreamer, but uninstalling and re-installing it will be a pig of a job... ](*,)

---

### Post by tabinin on 2009-04-30
This was the best upgrade ever!  I have tried upgrading since I first installed 6.XX and it mucked up my system every time.  I voted "flawless" on the poll since all I had to do was reinstall Picasa. 
This is really exciting!  
In the past, I had custom partitions, mostly since I wanted to make sure my personal files were safe in case I needed to reinstall.  The last time I let the installer choose (and everything was on one partition).  I was a little nervous this time since I might have to pull out my backup drives and really find out if I had everything there, but in the end all was well.

Desktop
GIGABYTE GA-M55plus-S3G AM2 NVIDIA GeForce 6100 ATX AMD Motherboard
AMD Athlon 64 3500+ Orleans 2.2GHz Socket AM2
CORSAIR XMS2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800
nVidia GeForce 7100 GS

Yipee!

---

### Post by Guilden_NL on 2009-04-30
System #2 out of 6, first upgrade was flawless on a desktop and I posted that config here yesterday.  This upgrade took 34 minutes from clicking the Upgrade button to fully running on Jaunty.  

System #2 is an HP HDX18 with a bunch of goodies like BluRay etc.  Will have to download my config from HP and will come back to edit this post with the details.  HP is a big supporter of Linux, so no surprises here!

This is my wife's laptop and her friend was here watching me do it.  She is now going to buy an HP laptop which will be running Ubuntu as her primary OS.  My wife is thrilled with Jaunty - no major changes and I got rid of an annoying delay a month ago due to a bug in Intrepid, Jaunty either didn't change my config or the bug is fixed.  Here are the details on how to correct the annoying clocking problem: [http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell]("http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell")

Two thumbs up in agreement that this looks like a good release.

Config:
&#8226; Intel(R) Core(TM)2 Quad Processor QX9300 (2.53Hz)
&#8226; 8GB DDR3 System Memory (2 Dimm)
&#8226; 640GB 7200RPM SATA Dual Hard Drive (320GB x 2) with HP ProtectSmart Hard Drive Protection
&#8226; 1GB Nvidia GeForce GT 130M
&#8226; 18.4" diagonal High Definition HP Ultra BrightView Infinity Display (1920x1080p)
&#8226; Blu-Ray +/-R/RW with SuperMulti

---

### Post by Nittalope on 2009-04-30
Updated from 8.10 and, beside some problems with the spanish site from which I downloaded worked fine.
Nice experience.
Had some problem with graphics (Acer Travelmate 290 with Intel chipset), but thanks to the [forums]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") now almost everything works fine (some problems with NBA site and youtube video...sigh).
Probably will come back to 8.10, to upgrade in some future (but not sure... I'll just work out some other solutions and if won't work...), but 9.04 seems really promising... maybe on my next laptop!

---

### Post by danebramaged on 2009-04-30
** Problem:  Partial upgrade does not work in Jaunty**.  (1 package is going to be removed. 3 new packages are going to be installed. 1 package is going to be upgraded.) It wants to remove libdb4.5-java and, install libdb4.6-java, install libdb4.6-java-gcj, install liblrdf0 and Upgrade liblucene2-java.  I then click on "Start Upgrade" and I get nothing.  The window disappears and that is all.

**Problem**:  Click on Applications, System Tools, Root Terminal.  Type in the correct password. Password screen fades away as per usual.  Then nothing happens.  Root terminal won't load even though a standard terminal works just fine.

**Problem**:  Compiz 3d deformation setting defaults to Cube.  There is no cube setting in compiz.  Only cylinder and spherical.  Cannot make cube go away, only the grey background dissapears.

**Problem**:  NVIDIA X Server Settings are set to auto for resolution and refresh.  Changed settings from 1600 x 1200 to 1280 x 1024 @ 85 Hz.  However, every time I reset my computer, the settings have reverted back to "auto"

**Problem**:  Tracker has corrupt cache.  Deleted tracker cache and re-indexed everything.  Add 1 hour to the 9 hours it took to download at approx. 256 kbps from mirror.anl.gov.

I am upgrading from 8.10 TO 9.04 on an AMD Sempron 3100+ with an nforce 250 Gigabyte mobo with a Gig of ram, an NVIDIA 7600 GS 8x AGP card, Nokia 445Xi monitor and two 320 Gig Seagate SATA drives.

My main reason for upgrading was going to be putting ext4 on these two Seagate drives.  Now I read that I should probably hold off until the NEXT release and not even use ext4.  And this comes from the blog of the guy who was responsible for the project.

Jaunty Crapalope is quickly becoming a roaring pain in the neck.  At the point at which I have to fall back to 8.10 and then restore all of my data, I will be taking a long hard look at everything from PClinux to OpenSuse.

This particular debacle reminds me of KDE 4.0, which is why I am still running GNOME, thank you veddy much.

And it's too bad really.  After Hardy and Intrepid, I was really looking forward to 9.04.  

If there is a distro out there that detects my linksys card as sweetly as Ubuntu did, I would like hear back from people on that issue because, it is a very BIG deciding factor for me personally.

To all the people on this forum:  THANK YOU for helping me.  I greatly appreciate it.  Your responses have always been accurate in the past.  I do not forsee any immediate solutions however, when it comes to my remaining problems; root terminal - compiz - X server.

...but as the old saying goes, "Buy the ticket, Take the Ride"  ~ Hunter S. Thompson

---

### Post by 37fleetwood on 2009-05-01
did the upgrade and it went ok. boot and shutdown are slower. the only gripes are, I have a difficult Canon Scanner/Printer that I finally got working in 8.10 and now the scanner part doesn't work in xsane any more (it does however work in Gimp), and I don't like that the tool box seems to want to stay on top all the time in Gimp and I can't figure out how to get it to behave. overall it wasn't bad. I'm figuring the bugs will be worked out as we go along. I guess that is the view from an ex-Windows user.
overall, I haven't seen anything it does different or better so I'm wondering why upgrade at all? my advice, don't bother until there are significant changes made, the risk of problems outweigh the benefits.

---

### Post by mikechant on 2009-05-01
Desktop: 
Dell 530, 2Gb RAM, E4500 Core2Duo 2.2Ghz processer.
Did a fresh install of 9.04 (normal desktop edition) to triple boot with Ubuntu 7.10 and Vista (not used but maintained!).

Installed into preallocated single 20Gb root partition (will use seperate /home from 7.10 install). Installed in about 10-15mins with no issues at all. 
Enabled Nvidia driver and installed Flash plugin - all desktop effects work great, all multimedia video/sound OK (after Totem installed good/bad/ugly codecs).
Multiple video/sound apps playing nicely together, sound quality fine - looks like pulseaudio is usable without tweaking now!
HP 880c printer and Cannon 620(?) Scanner installed automatically and working fine. 
Internet connection (Cable via wired connection to Netgear router) set up automatically OK.
Boot time (grub-->logon prompt) reduced from 30s to 20s (with ext3 - possibly more gains to be made with ext4).
Generally snappier and better looking, no faults found so far.

Netbook:
eeePC 1000 (40Gb SSD model with Xandros).
Tested netbook remix from 2Gb SD card - slow boot (due to SD card speed probably), but generally works OK. Wireless is a real high point - connection strength 95%+ and rock solid with throughput at the maximum speed of the cable modem, as opposed to using the same eeePC with Xandros with gives about 50-70% connection strength, slightly flaky and throughput medium/poor.
Special keys working.
Webcam *not* working with Cheese but haven't tried anything else yet (not really bothered about Webcam but I will try to get it working). Battery life seems similar to Xandros, but power info is much more comprehensive.
I will attempt a proper install on the eeePC in a few days, initially dual boot but I think Xandros is going to get blown away fairly soon.

---

### Post by e1luca on 2009-05-01
Laptop:
Vaio VGN-FW21E

Wow!!! I did fresh install from Fedora10. I'm so glad I did. 
Everything works out of the box. 
- The ATI proprietary drivers wich I was so affraid of - just went to System>Administration>Hardware Drivers and I was set (I have Radeon 3470 card).
- wifi: out of the box
- sound: out of the box
- webcam: out of the box
I have a complete system working without touching the terminal. Great job Ubuntu!
  
Minor problems:
- still no fn keys (brightness). It's an old problem, I know there are some workarounds I fiddle with this later.

---

### Post by mjezell on 2009-05-01
Used distro upgrade on my desktop with only one small problem.  Nvida video card with driver seemed to cause the xorg.conf to use some generic setting.  Used the Nvida graphics config program to correct the settings but it would not save it to xorg.cofig file.  Copied and paste to editor and replaced original xorg.config file.  Everything working great sofar on the desktop.

Just purchased a Asus 1000ha that came with windloss (no choice).  Wiped the drive and installed remix9.04.  What a great install.  Not one problem and only took about 15 mins (not including loading the image to the thumb drive, but that was painless too).  Love Ubuntu on the netbook but would not even think of using it with windloss.  This has been the best install/upgrade release since I started with v4.10.

---

### Post by albertbijzitter on 2009-05-01
Upgraded using distro upgade.
Only Google earth isn't working as it used to. I had a few crashes. Hope to get that fixed.
I havent encountered any other problems so far.

I was little bit scared about the Nvidia stuff but had no problems. 
A few weird Graphics in Blender from 8.10 are solved in 9.04.

---

### Post by dbram32 on 2009-05-01
One upgrade/install on a pc went smoothly. It also has fixed an intermittent drop of my Linksys USB Wireless (WUSB54G). So all is good there! The only issue seems to be the screen size will not quite fit...I lose 1/2 inch on the right side and resize- but it snaps back...???

The laptop upgrade went smoothly also - it is a dual boot and took care of a partition issue I caused the first go round. However, the use of the upgrade is not quite happy yet - I cannot use my Logitech Marble Mouse nor can I use the Sharp AR M550N office printer. Both of these worked in 8.04, so I am hopeful they will both work again soon.

Nice look, nice feel - now if I can convince the wife!

---

### Post by oldrocker99 on 2009-05-01
On my Toshiba laptop, I tried the upgrade, hoping the denial of fglrx drivers wouldn't affect my system. Wrong.

Back to 8.10, and I'll stay there for the time being.

:guitar:

---

### Post by utnubuuser on 2009-05-01
Jaunty Jackal-ope installed easily, no problems - My hardware has liked all releases except 7.10.
I had a problem with the liveCD and endless instances of nautilus trying to open unsuccessfully, but the installer worked ok anyway.

---

### Post by scintilla on 2009-05-01
Upgraded from 8.10 on AMD64.  

Download stopped a few times but I could restart from where it left off ... ok.
Have had serious screen problems: 
- browsing "places / home" shows an enormous window & then freezes the system
- playing aisleriot solitaire regularly crashes X, can reboot using magic keys
- various odd behaviour (dots all over the place etc)
have now disabled compiz custom effects, will try disabling Nvidia non-free driver next

Networking on KVM broken - bridge shows up extra MACs and Windows under KVM can't get a DHCP IP address .. still working on this

On the other hand - boot is faster; SW raid still works fine for me

---

### Post by anishman on 2009-05-01
The ATI x1300 card in my Intel based Pavillion dv6000ca laptop is fine. No issues here. Upgrade was flawless, but I can,t say the same for my AMD X2 based HP desktop.  Random lockups happen every few minutes.   I almost thinking its a AMD processor issue.

---

### Post by Draekaar on 2009-05-01
Hi

I just instaled my 9.04 kubuntu, but there have been a few issues i couldn't figure out right away, but with some help from more linux savvy friends, i solved most of them.

Now, my only problem is the sound output.  I've tried a few of the things I've read in these forums to no avail, and my friend giving some advice didn't work either, but I don't know how to make anything run sounds.

Basically, upon boot, all the system sounds work fine, then i open firefox and youtube will run the video but not audio for vids...  instead it gives a staticy mess.  Same thing happens when i try to run an mp3 through vlc or amarok.  Just static.  And then my system sounds went, so kopete and quassel just give static for notifications.

The only other thing i think i should mention is my computer gives me an error message that i keep forgetting to write down, basically says my nvidia audio device won't work and that it was defaulting to pulseaudio.

I'm getting really close t ogiving up and just switching back to vista.  at least i never had any issues with it.

Advice would be readily appreciated :D

~Draekaar

---

### Post by yeowzuhx3 on 2009-05-01
I installed Jaunty Studio on a Asus P5B Deluxe board w/ Core 2 processor. I am experiencing frequent freeze ups especially while running audio programs. I didn't think Linux locked up like 98. I've tried giving it time to do whatever process supposedly that was taking place for up to 3 hours. I had this computer built for speed w/ 4GBs ram and 2TBs data storage (ext3) and the OS running on a 10,000rpm 150GB hard disc but I'm experiencing SP2 speeds. What gives?

---

### Post by ian1457 on 2009-05-01
to be blunt - disgusted with the whole upgrade experience - when will they release one that just works - this is sinking to an MSW level!!

---

### Post by jemlinus on 2009-05-01
This 9.04 reminds me of the memory when I try to install MS Vista for the first time.

---

### Post by cyrulution on 2009-05-01
The upgrade to Jaunty went well, but now my system crashes at least once per half hour. The screen freezes and the only escape is a hard reset.

---

### Post by ronparent on 2009-05-01
I did a clean install on a computer I had not previoulsly been able to get 8.10 to run on (kernel freeze after ~20min). What I have now is a mixed bag. Because of a no longer supported ATI card I'm operating on the default graphic. Not a desireable situation since I'm running two monitor (no spanning) and the card cannot be set to display wide aspect for my principal 22 inch monitor.

Other Comments:

1)If you have a fakeraid setup, it is not automatically found during install. You would have to install and run dmraid in a live cd terminal to see and partition a raid drive. I had to install it again after the system 1st booted (I forgot to chroot). Fortunately since I wasn't installing to a raid, the remainder of the install went fine.
2) Grub didn't install properly and there was no menu, only a grub prompt, on boot. I had to locate it, set it as root, and run setup on it, Everything was fine thereafter.
3) Grub didn't find my windows XP install on the raid. I had to sudo gedit to add it to the menu.lst. 
4) Otherwise all of the partitions on the raid were found (duplicated since it was a raid1) and automatically displayed properly after installing dmraid! In 8.10 I had to separately add them to fstab manually to mount them. 
5) I almost forgot, I had to F6 to no-apic and no-lpic, as well as F4 to load in safe graphic mode to bootyhr live cd.

Other than the fact that the graphics display sucks, and that the user has to be a bit knowledgeable to install to a system with a fakeraid, everything went smoothly. Now I have to reflect on how I'm going th approach an install on my other three computers and a usb stick.

---

### Post by raven on 2009-05-01
It is a clean install

system:
mobo gigabytes P35C-DS3R
Intel Core2 Quad CPU    Q6600  @ 2.40GHz
Ram 4GHz
video PCI Express GeForce 8600 GT
Ethernet controller RTL8111/8168B PCI Express Gigabit 

 3 little issues:
1-video resolution max was 1024x768 with nVidia drivers
solution, copied xorg.conf from Hardy to jaunty and it worked with no modifications now 1280x1024@85
_solved_

2-some applets did not work (sensor-applet and gkrellm) could not get HD temps,
in Hardy they all worked with no fidling.
_in progress_
update this one is solved, every time I add a HD I need to reinstall hddtemp, in Hardy it was dynamic

3-tracker indexing most of the time is corrput need to reindex
or it will not find anything that I have to reindex, so tracker is not working at all
_no solution found at this moment_

system is up to date

over all a good experience, fast to install
had to install jaunty twice, first log after insall could load home
delete installation and reinstalled it, all went ok except for the 3 issues above...

---

### Post by RickSGM on 2009-05-01
I have an almost new Dell Inspiron 1525 that I had installed 8.04 on with Wubi.  I upgraded to 8.10, then on to Jaunty.  No problem whatosver with it.  

On my older E Machines, I tried upgrading (Ubuntu is on the 2nd hard drive), and it didn't take, but a clean install worked beautifully.  Before, I had issues with sound, flash, and java.  On the new Jaunty install, everyting worked perfect.  I couldn't ask for any better than that on an old 64 bit machine.

---

### Post by EmilyRose on 2009-05-01
I upgraded a couple days after release came out, and most everything worked great. There was an issue with the tracker, but fixed it easily. My only other issue is add/remove not listing third party apps, but other than that everything works just great, and mostly it seems a good bit faster than 8.10!! :D

ETA: I'm on a gazp5 from System76 :D

---

### Post by winfree on 2009-05-01
I have 2 computers, 
.One flawless upgrade - with NVidia card, 
.the other upgrade no so good - with ATI RV350 (Thanks to Grimmwolf's comments : apt-get remove --purge xorg-driver-fglrx). I use this computer in family room with a 42" Philips TV/LCD. It blinked (screen goes DARK and comes back) at me already 4 times ???, it never did this before. Can't change to another workspace (4) either with wireless mouse or keyboard !!

No Compiz.

---

### Post by ranch hand on 2009-05-01
My box loves it,  I can run in 64 or 32 mode and both work great.  Install was slick, I like the updated install as it seems a little quicker and easier.

I did completely screw grub but that had to do with what I was doing and had nothing to do with Jaunty.  I actually have 4 9.04 installations.

I installed Stoner Edition 1.0.  What a nice little varient.

---

### Post by yogo on 2009-05-01
I did two installs yesterday, one on a Gateway laptop and the other a Dell Desktop.  Both installs worked great. The Gateway needed some tweaks to get wireless going, works out the box on Dell laptops.

As for the desktop, everything worked for wireless out the box.  Both were installed from a persistent USB. I did end up with some problems with the Gateway, had to use Wicd to get wireless working and these changes were made to the USB drive used to install, so it had Wicd on it and no network manager. After about three failures trying to install it I figured that that was the problem and I redid the USB 9.04 again and installed. Then downloaded the deb package of Wicd and removed network manager and got wifi going quickly on the Gateway but a little tricky.

---

### Post by lannatwin on 2009-05-01
Ahh, back on 8.10.  where everything just plain works.  I love this OS. :)

---

### Post by charlesdean2002 on 2009-05-01
> **Xir said:**
> After reinstalling and performing the do-release-upgrade again, again the VM will not boot. I guess I'm done working with the upgrade today, back to 8.10 for me until I have time to troubleshoot it.
Tell me how to go back to 8.01 without losing  what I have built. I upgraded to 9.04 and now I do not have a desktop. it starts up and shuts down the only thing you can't see it a desktop. right now I am online with a live cd of 8.04..

---

### Post by flyingsliverfin on 2009-05-01
had(ve) a very serious problem

X is FAILING

otherwise very good and smooth

( see my thread [http://ubuntuforums.org/showthread.php?t=1145713](http://ubuntuforums.org/showthread.php?t=1145713)  )

---

### Post by neo.patrix on 2009-05-02
hi everyone, 

I live in outcast universe with Ubuntu 8.10, FGLRX 8.5.43 (whatever pain in...), CompizFusion and  RADEON X1300. So far most blogs or threads I have read conclude don't try it because probably 3 year old Dell Inspiron 6400 with X1300 is considered "too old" for any kind of support from the "AMD/ATI" (boo boo). 

Only conclusion is never , ever buy ATI, and its support for Windows
is hardly better, I had to uninstall ATI Catalyst Gui Configuration
because it always kept crashing.

---

### Post by aikiwolfie on 2009-05-02
Once I did a fresh installation of 8.10 everything went fine. But having to do a fresh install of the previous version defeats the point of an upgrade. It also means I've not been able to take advantage of the new ext4 file system.

For some reason every copy of the install CDs I downloaded i386, x86_64 and alternate got corrupted. But the disk check utility said they were fine. It was the installer that claimed there was an issue. This might be a problem with my desktop PC. Some other things aren't working properly with that.

I also flashed the BIOS of my laptop (the PC I've upgraded) which complicates things a little. I'm using the latest BIOS for the M1330n (A15) using Dells procedure for flashing a BIOS in Linux. Which is always a scary process for me.

A few things are happening that didn't happen before. The CD drive stalls when trying to eject a disk (both software and by pushing the button methods) and sometimes the screen goes all weird with vertical lines and then bleaches out white when trying to reboot. LinDVD also tends to crash now. It never did this before. VLC refuses to play any commercial DVDs. I've done the whole Medibuntu thing and it still doesn't work.

I've heard of these problems before from other users. But never had them myself. I'm in two minds about trying the Dell 9.04 iso.

I was particularly pleased to see the awnwindow-manager-dock-bar-thingy maturing nicely in 9.04. That seems to be super stable now and well integrated into Ubuntu. The new notification system is almost invisible in terms of it's impact on daily use.

Some of the icons in the notification area behave a little differently. Like the Pidgin icon for example. But that change isn't detrimental to the way I use the system. And the notification area seems to be more stable. Meaning it's not jumping around the top panel from one boot to the next.

The new version of GoogleEarth installed from Medibuntu works flawlessly. Previously when I tried to install this on my own it required root privileges to just run the application. Now it installs properly.

I know the Medibuntu repositories aren't strictly part of the official release. But it's not just the official release that matters from a users point of view. All the stuff in the community that surrounds the official release also matters. Without projects like Medibuntu, Ubuntu would be little more than an OS for e-mail, word processing, spreadsheets and some web browsing.

I do wish however Canonical would finally get the message and build three partitions by default. /home, / and swap. This advice is handed out to newbies in every other thread here on Ubuntu Forums. Why aren't Canonical paying attention? Maybe this is something they can work on for 9.10.

So to round up. I have an OS that is in many respects more stable and feels more solid than before. It definitely boots faster even though I was unable to us ext4. But it currently does less than it did before and some older applications don't work properly.

I've criticised Microsoft in the past for delivering similar results with it's OSs. So it's only fair that I should say this isn't good enough for Linux. It's not good enough for Ubuntu and I expect better from Canonical.

Canonicals' saving graces are, their OS is free and fixes to problems and bugs won't be held back until "patch Tuesday" or SP1 or 2 or 3 or even 5 years from now until the next OS is released.

I do however think that Canonical should return to the mantra of "do less, but do it better".

---

### Post by Stupojohn on 2009-05-02
Fresh install.

Booting much quicker than 8.04 which is what I upgraded from.
Initially had sound only in amarok.  I tried to fix it and now I don't have sound at all!  Not all my buttons are showing up in the top and bottom panels either.

Small problems that shouldn't take too long to fix.

---

### Post by BigSilly on 2009-05-02
Fresh install. All good and no issues to report.

:guitar:

---

### Post by aikiwolfie on 2009-05-02
> **charlesdean2002 said:**
> Tell me how to go back to 8.01 without losing  what I have built. I upgraded to 9.04 and now I do not have a desktop. it starts up and shuts down the only thing you can't see it a desktop. right now I am online with a live cd of 8.04..

Do you have dual graphics cards? The new X server since 8.10 doesn't choose a default. You need to tell it which one your display is connected to.

There's a thread on this very issues kicking around somewhere on Ubuntu Forums.

---

### Post by archer6 on 2009-05-02
> **frodon said:**
> The purpose of this thread is to share your experience installing/upgrading Jaunty Jackalope.

Did it worked flawlessly ? 
Did you got problems ? 
Did you manage to solve them ? 
if yes how ?
...

I have a suggestion:

Many people are sharing their experience and problems, but not telling us what kind of computer they have installed it on. Therefore no help can be offered. 

Perhaps the title of this thread could be amended to reflect this issue.

Cheers...

---

### Post by Guilden_NL on 2009-05-02
New update: system #2 - HP HDX 18 worked perfectly for two days.  Made one change to get the sound system working (I am hard of hearing, so didn't notice that sound wasn't working on the out of box upgrade). Now it hangs on shutdown and reboot.  I have left it for hours and nothing happens.  Any normal key combination ends of acting like a terminal session or busybox session with garbage characters.  When I Alt-CTRL-DEL, it will reboot, but with the message - md: Stopping all MD devices.

I backed out the sound change and no difference.  I put it back in.

Nothing in the logs to provide a clue as to what it is.  I have spent several hours today scouring the Net and it looks very much like a bug that floated in and out of kernels in 2004 & 2005.

Wife was big fan of Ubuntu, but now is booting into Vista.  I'll keep checking, but have a feeling that a device bug crept back into the kernel.

---

### Post by nathang1392 on 2009-05-02
i hit some buttons. it handled itself. i wasn't even sure it upgraded until i looked in system monitor, thats how easy it was.

---

### Post by haraldmilz on 2009-05-03
Thinkpad T61 6458-CTO

Upgraded from 8.04 to 8.10 and finally to 9.04

The bad:

Fingerprint stopped working. Bug has been submitted. No solution to it yet.
VMWare Workstation stopped working. Here the solution: [http://ubuntuforums.org/showthread.php?t=1040351](http://ubuntuforums.org/showthread.php?t=1040351)

My NVidia Card wasn't working, 640x480 :S - Uninstalled all envy components, apt-get autoremove, apt-get autoclean - reinstalled envy-qt, reinstalled nvidia drivers... all good now. Curious, when on Separate X-Screens, applications launched on :1 open on :0... bug reported, no fix yet.

The Trackpoint middle-mouse-button stopped scrolling :S Solution: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T61)

thinkwiki, great site guys :)

When gksudo is called, it just takes a few seconds to show up.. try launching Synaptics Package Manager... no idea why.

The Root Terminal. New color, nice, but it doesn't work. hmmmm Bug has been reported, no solution yet.



The good:

- Hibernation now works!
- I got sleep to work on Gutsy, still working on Jaunty.
- The WLAN LED now works! It also blinks on WLAN activity. Nice to have.
- Is my battery lasting longer or am I being just too positive?? :)

Regards,

Harald

---

### Post by mfearby on 2009-05-03
My network upgrade (after rsyncing my /home partition and doing a clonezilla backup of my root partition) worked well. It told me of changes made to a couple of Apache configuration files, which I reinstated afterwards, and it busted Java so I had to go fetch Sun JDK again and use --jdkhome to keep NetBeans happy, but apart from that, not a problem.

Once thing that's bugging me though is that new indicator applet. I've told it not to startup and also removed it from the tray, but I'm still getting a rather annoying little popup with each incoming IM in Pidgin and with each track change in Rhythmbox (which I use when playing actual CDs). I'd like to be able to turn off both of these notifications, but for now, I'll just remove it and hope it doesn't come back at next login (but I'd like to know which process to kill so I don't have to log out and in again).

---

### Post by mfearby on 2009-05-03
Having just said all's fine and dandy, I went to edit a Calc spreadsheet and all of a sudden all four cores of my Q6600 CPU went to 100%. Ran top and saw four wvWare processes eating up all the CPU time. Turns out this is a library for converting MS Word documents (why it would load when I'm editing an OOo Calc spreadsheet is beyond me) so I had to kill -9 them to recover (though my hard disk is still recovering from the near heart-attack). Checking "top" again and I can see that "tracker-indexer" and "tracker-extract" are now making nuisances of themselves. I've always hated Beagle/Indexy type things. Must turn that rubbish off!

---

### Post by akoskm on 2009-05-03
It was a fresh install on MSI M670X. Additional boot parameters were: *noapic nomce nosmp* unless wont boo't. And no splash screen, even if the video driver installed.
Everything works (sound, video, hardware ...).
Good job.

---

### Post by stanca on 2009-05-03
Upgraded since alpha6 stage,better%better,no serious issues.:guitar:

---

### Post by LoREZ on 2009-05-03
Hoping against hope, I did a fresh install of Jaunty for my Medusa of a system.  Okay, for years I've had trouble installing any linux distro, usually because of the configuration of my system.  I have several drives of mixed bus (SATA, IDE)  and this always causes problems.  Hardy wouldn't even boot on my machine, and all subsequent versions were unbootable as dual-boot machines.  The trick, it turns out, is to pull my SATA plugs, install to my taste, plug SATA back in, then reboot.  Everything works.

But then I find out, inexplicably, that Jaunty doesn't warn you that your DVDs won't work without doing some keyboard jockeying (adding sources, downloading extra libs).  They really should tell you that when you try to play content, like they usually do when you don't have required software, instead of leaving you with cryptic error messages.

But other than that all my problems have to do with individual programs, not Jaunty.  Jaunty is the best Ubuntu release yet.

---

### Post by Jerry41 on 2009-05-03
My machine is an HP Pavilion a1243w "Media Center PC" with AMD Athlon 64 cpu and ATI RS480 (Radeon Xpress 200G series) integrated video. 
I have been using UBUNTU since 6.10 with decent to good results. on 8.10, after I got the ATI drivers installed, the video was *almost* as good as it had been under XP. 
I am not a demanding user as far as video goes - no gaming, don't look at much "U-tube" & such. That said, my video on 9.04 is the absolute **WORST** I have endured since Windows for Workgroups 3.11.
I gave up and removed Google Earth (it has never worked very well, but not at all on 9.04), and any picture with decent resolution takes minutes to paint on the screen. I brought my RAM up to 1 GB and should be able to use 256K of that for video, but for some reason, it will not recognize more than 64K. (No selection available in BIOS). The 64K worked reasonably well with the ATI drivers, and was even passable with the Native drivers, but with 9.04 it is just painful.
This is a GIANT step backward for me. 
In general, I love UBUNTU, but I am now looking for a distro that will work with MY hardware.

---

### Post by fillintheblanks on 2009-05-04
fresh install of EXT4

runs like a wet dream.. couldn't be happier :)

---

### Post by zaivala on 2009-05-04
I just installed Hardy Heron again, and updated it, first to Intrepid and then to Jaunty.  Everything works fine... except my sound... I haven't really run it through its paces yet to be certain that everything works, but the sound doesn't just yet.

---

### Post by aikiwolfie on 2009-05-04
In my previous post I managed to get 9.04 working on my laptop by doing a fresh install of 8.10 and then doing an on-line upgrade. Not the best way to go about things. But it worked.

Installing the 64-bit version on my desktop has been even worse. I have an SLI setup so the standard Live CD just doesn't want to know. Clearly Canonical doesn't have a solution to this problem. So I'm using the alternative iso image.

The sticking point seems to be Grub. It just doesn't seem to get installed or doesn't understand the ext4 file system. But the installer claims everything installed fine and reboots the system.

I've been up all night. This is the third or fourth or fith time trying to get this working. It's looking like I'll need to do a fresh install of 8.04 and then do an on-line upgrade. This of course means I can't take advantage of ext4.

This is the worst Ubuntu installation experience I've had since Ubuntu first appeared. Canonical has taken a major step back with 9.04 in terms of ease of installation.

All these issues make me feel like Ubuntu is lagging behind Windows. After all there's no point in having a desktop that can match or even surpass Windows XP/Vista/7 if you can get the damn thing installed!

---

### Post by kneewax on 2009-05-04
Did a completely painless upgrade from Intrepid x64 to Jaunty x64 on release day.  Really really impressed, Jaunty knocks the socks off previous versions feels very stable and has a 'smoothness' about it which is hard to define, but feels great to use.

Cracking release guys, thanks.

---

### Post by frodon on 2009-05-04
> **aikiwolfie said:**
> I
The sticking point seems to be Grub. It just doesn't seem to get installed or doesn't understand the ext4 file system. But the installer claims everything installed fine and reboots the system.

I've been up all night. This is the third or fourth or fith time trying to get this working. It's looking like I'll need to do a fresh install of 8.04 and then do an on-line upgrade. This of course means I can't take advantage of ext4.More information there:
[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

It is recommended to stick with ext3 for now. Ext4 is new and is known create some troubles with jaunty so if you are not willing to spent time fixing ext4 known issues then just stick with the rock solid ext3 filesystem.

---

### Post by pa7two on 2009-05-04
Upgraded 3rd home PC, a pretty new HP Compag. Upgraded from v8.10 to v9.04. 
All went fine, even the Nvidia drivers were automatically installed. No Java / Flash issues in Firefox after removal of the swf-dec packages from the Synaptic Package Manager *before* the upgrade.  
With regards to this particular PC, happy as a bee can be! :)

---

### Post by ranch hand on 2009-05-04
Thanks for the link Frodon.  I will read the thread.

I find the stuff interesting because I have 4 (2x32 and 2x64) installations of Jaunty and a varient.  Have had no problems at all with any of them.  Smooth, fast and slick.

All of mine are clean installs.  Ubuntu just seems to like my box.

---

### Post by aikiwolfie on 2009-05-04
> **frodon said:**
> More information there:
[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

It is recommended to stick with ext3 for now. Ext4 is new and is known create some troubles with jaunty so if you are not willing to spent time fixing ext4 known issues then just stick with the rock solid ext3 filesystem.

Thanks. I finally just opted for ext3. Install went fine. Since I'm using an SLI setup I still had to install the nvidia drivers manually and configure the xorg.conf file. But I remembered how to do that from 8.10. So it's all coming together now.

All is calm again and Ubuntu is awesome again. :p

---

### Post by LuxAeterna on 2009-05-04
Hi,

upgraded from 8.10 to 9.04 on two computers: My Dell M1330 XPS (32-bit) and my desktop PC (64-bit). Both upgraded flawlessly by Update Manager.

However, I needed to re-configure VMWare on my 64-bit machine to make it work again, and Compiz Fusion does not work on my Dell yet. It's fine on my desktop machine.

---

### Post by aikiwolfie on 2009-05-04
My advice is give up on VMware and use VirtualBox.

---

### Post by fcastillo on 2009-05-04
I love this new version of Ubuntu, it works like a charmed, except for one thing, the wireless network keeps disconnecting. I don't know if it's a drivers problem, or the network manager, kernel, conflict with other application, I don't know, but every 5 to 10 minutes the network disconnects, and I have to disable networking and re-enable it, sometimes that doesn't even work, and I have to restart my laptop.
I have windows also installed and it doesn't give me any problems at all, so I know it's not my card.

---

### Post by dnairb on 2009-05-04
Installed Jaunty afresh on my self-build (worked flawlessly with Hardy Heron) - install was a breeze (much quicker than with previous releases of Ubuntu). No issues at all - everything works as it should. Jaunty also boots faster than Hardy did.

---

### Post by gfox42 on 2009-05-04
I've used Linux for 10 yrs on my desktop machine. This upgrade made a decision for me: I'm installing Windows on this machine. There are so many things wrong -- in particular, the machine locks up a lot -- that I don't want to figure out how to fix them. I'd prefer to stay with Linux, but I don't want to spend the next month fixing software. Since the IT department downstairs supports MS, they'll fix my software problems. I wish I could say "but it will be with worse software," but I'm no longer convinced that's true.

---

### Post by kneewax on 2009-05-04
> **fcastillo said:**
> the wireless network keeps disconnecting. I don't know if it's a drivers problem, or the network manager, kernel, conflict with other application, I don't know, but every 5 to 10 minutes the network disconnects, and I have to disable networking and re-enable it, sometimes that doesn't even work, and I have to restart my laptop.
I have windows also installed and it doesn't give me any problems at all, so I know it's not my card.

Stupid question, but it may be relevant -  do you run Skype?   If so try shutting it down and removing it from Start up, I found that Skype regularly killed my wifi connection both in Hardy, Intrepid and this week when I gave it one last go, in Jaunty both 32bit andd 64bit - this seems to be an undocumented but I have found the same problem on two very different machines.

Anyway might not apply to you, but worth a go if you are running it. :)

---

### Post by Wiebelhaus on 2009-05-04
No issues on my home pc's what so ever , My tech bench machine had a monitor detection issue , which was fixed in the past with displayconfig-gtk which has been removed for no logical reason.

---

### Post by kneewax on 2009-05-04
> **gfox42 said:**
> I've used Linux for 10 yrs on my desktop machine. This upgrade made a decision for me: I'm installing Windows on this machine. There are so many things wrong -- in particular, the machine locks up a lot -- that I don't want to figure out how to fix them. I'd prefer to stay with Linux, but I don't want to spend the next month fixing software. Since the IT department downstairs supports MS, they'll fix my software problems. I wish I could say "but it will be with worse software," but I'm no longer convinced that's true.

Sorry to hear that, especially when most folk (not just here, but non-linux critics too) seem to be quite impressed with Jaunty.  I hope Windoze works for you, but chances are you'll soon remember why you stopped using it.  I run both (My wife is wedded to XP), and have far fewer problems with my Linux box.  I also have far more support than I could get from any IT dept, in terms of this forum.  Not that I have too much call to use it these days.

Still we all have to make the decisions that make most sense given our needs, so have fun back in Microsoftland I hope it works out for you.... :)

---

### Post by rrashkin on 2009-05-04
I did a fresh install from the Live CD.  No problems.  I have an Everex gPC2 with VIA graphics.  I haven't noticed any particular improvement in performance, but then I didn't think it was particularly poor on 8.10, either.

---

### Post by gazer22 on 2009-05-04
Upgrade attempt failed - grub and nvidia issues upon reboot that I couldn't solve.

Fresh install went cleanly, but the sound issues are horrible.  (snd-hda-intel & alsa/pulseaudio).

Firefox likes to randomly die too - haven't figured that one out yet either.

---

### Post by skotos on 2009-05-04
Day by day, I am getting more and more upset with the pulseaudio alsa system base: nice, great idea and concept with too many flaws in its deployment. It is discouraging to see we are all looking for ways to definitely solve the same issues... Humm.. Wouldn't it be nice to have a sort of pulseaudio-check-and-rebuild-from-scratch-package? A sort of pulseaudio doctor to thouroughly diagnose the system and propose a new/revamped configuration?

---

### Post by Zunino on 2009-05-04
Hello.

I have written a couple of posts about my initial experiences with Jaunty. You may read them at [http://blog.zunino.eti.br/]("http://blog.zunino.eti.br/").

Cheers.

---

### Post by del_diablo on 2009-05-05
I have 3 things to say:
*Curse Ralink for not making proper drivers
*Curse ATI for not having a proper grapic driver ready for the current xorg version
*Curse Fujitsu Simens for having a crappy BIOS on the computer(can't regulate a certain fan from there)

Beyond that its flawless :P

---

### Post by Nuked on 2009-05-05
All is working fairly, well.. just need to get this scanner working (Epson Perfection 1200 Photo) and some minor fine-tuning to my personal likings... but otherwise, all is well!  :)

---

### Post by Gert-Jan on 2009-05-05
First time I installed Ubuntu and very happy with it.
Just a problem concerning a wireless card I'm trying to install (system doesn't boot properly with the card, if you're an expert; pls check [http://ubuntuforums.org/showthread.php?t=1145217](http://ubuntuforums.org/showthread.php?t=1145217) =P~) but I'm pretty confident that it will be sorted...

---

### Post by Freckletoe on 2009-05-05
Opposed to some people who upgraded from Intrepid, Jaunty actually *fixed* a problem I had:

-I couldn't play any 3D FPS games (Cube 2, Nexuiz) in 8.10 probably because of my graphics card (maybe, I don't know.) but in Jaunty they work fine now.

Love the new notifications system!

---

### Post by whayong on 2009-05-06
Can't get proper screen resolution.  Ever since 7.10, Ubuntu has been screwing up detecting my Intel 82815 graphics card but have managed to do a few workarounds.  With 9.04, I can't even do any workarounds.  Bottom line, most unusable Ubuntu I've used since 6.10.

---

### Post by ok_dr on 2009-05-06
On the poll I voted for a flawless upgrade but now I notice Compiz is not working and I can't enable any visual effects, it says my video card is blacklisted, while it was running just fine with Intrepid. 
Nothing else, apart from the very low audio and audio capture which troubled me with 8.10 also.

---

### Post by happyenduser on 2009-05-06
[FONT=Trebuchet MS][B][SIZE=3]upgrade issues, 
all went well except for two things:[/SIZE]
[/B]
[I][B][SIZE=4][SIZE=3]1) loss of readable fonts in some apps (mostly KDE).
this was fixed by[/SIZE]:[/SIZE][/B][/I][/FONT] 
[LIST]
[*][FONT=Trebuchet MS]*Appearance Settings > Fonts > select* '**Best Shapes**' instead of 'Subpixel smoothing (LCDs)'
[/FONT]
[/LIST]
[FONT=Trebuchet MS][SIZE=3]***2) Amarok would not play MP3s.***[/SIZE][/FONT][FONT=Trebuchet MS]
[/FONT][INDENT][FONT=Trebuchet MS]thought it was a sound-card issue (Integrated INTEL HD), 
however, in my case it turned out i just needed to install some packages:
[/FONT] [/INDENT][INDENT][FONT=Trebuchet MS]**libxine1-ffmpeg package **
```
sudo apt-get install libxine1-ffmpeg
```**kubuntu-restricted-extras package**
```
sudo apt-get install kubuntu-restricted-extras
```amarok sauce:
[http://amarok.kde.org/wiki/MP3_on_Kubuntu](http://amarok.kde.org/wiki/MP3_on_Kubuntu)[/FONT]   
[/INDENT]

---

### Post by JoeKachurowski on 2009-05-06
As a raw newbee, I'm not sure I'm even qualified to begin to describe my  frustrations. I'm expecting things to be in places they aren't, and haven't the language the developers, volunteer's all, want the problems explained in.  Having a look at the various forums just confuses me more!  I have an Acer Aspire One, and from what I've read, I should be installing the OS on an SD card to prevent premature wear on my 8gb SSD.  Ubiquity crashed every time at every configuration I could figure out, right at creating Grub and associated files trying to install to an SD card. The clean up scripts didn't run, of course, so even if I had figured out a way to create the required grub and files, I still wouldn't have had a working system.   This seems to be an issue for 8.04, 8.10, as well as 9.04 (I tried loading them all).  Until I find somebody that has managed to install to an SD card on an AA1, I'm just muddling through, for example, trying to determine how to properly install ClamAV, and figure out why OO seems to be different in Ubunto from Windows (Can't get a spell check to work for love nor hors of time thrown at it!).:confused:

---

### Post by element_G on 2009-05-06
I first installed jaunty at alpha 6 because my kubuntu 8.10 had dependency problems preventing kde-dev packages and compiz from being installed. However I am back on 8.10 because sound has never behaved for me in jaunty. The last update I did last week broke pulseaudio for me since I use the digital out on my card and this disappeared. Not to mention the sound crackling issues that seem to be program specific ( it's better now, still present in VLC). 

That being said after some googling it looks like an upgrade to alsa 1.0.19 and pulse 0.9.15 should remedy my sound woes.

I understood these issues being in alpha and betas and even RC, but still present in release?? I know the issues were not directly ubuntu's fault (i think it was a kernel and pulseaudio thing) but to have them present at release is disappointing.

Jaunty was not without advantages though, aside from sound everything is working nicely, and there is a noticeable decrease in my boot time, looking forward to 9.04.1.

On a side note, I have jaunty on 2 laptops and everything is working nicely.

---

### Post by cguy on 2009-05-06
Yes!!
I just upgraded from 8.10 to 9.04. Absolutely beautiful! No problems whatsoever.

The only thing that didn't work (that I know of right now) was VirtualBox which just needed a reinstallation of the current version.

The only thing I need to check tomorrow is the sound system (it's 3:24 AM now :> )

The upgrading process actually lasted as advertised: 52-54 mins. It a bit much isn't it? How much would've lasted a clean installation? 20 mins?




OK, here's a thing that annoys me: Amarok was upgraded to v2 and I lost my database. I'm gonna give this cr*p a spin and most likely go back to 1.4. Too bad that scanning 50GB of music takes aaaaages.



This concludes my upgrading experience. Perfect!!!
(the journey of upgrading was all the way from 8.04 to 9.04)


Addendum: I hope the boot times would improve, even after an upgrade. :(
It still takes 57 seconds from GRUB to GDM. Any quick tips?

---

### Post by Murasaki903 on 2009-05-06
My upgrade from 8.10 was flawless. It took three hours to download but it was definitely worth it. :)

---

### Post by Keithhed on 2009-05-06
32 bit is flawless for me! I was running 64 bit for a time, but I was affected by too many of the buggy issues.  And I lacked the desire and patience to sort out the problems, so I nuked it last week and 32 bit is great :)  very satisfied with the release!

---

### Post by sammorxman on 2009-05-07
**Installation totally borked **
Unreadable after the splash screen is done.
No sign in screen, graphics is squashed to a 5/8" ribbon at top of screen witn a row of fuzzy Ubuntu logos beneath that along with non uniform green dashes under that. **I need to re-upgrade so I do not lose data ** but cd version (so far) hasn't shown me a way to upgrade or fix rather than doing a clean install
HELP !!!   8.10 ran flawlessly and vista sucks[/B]
:confused: --- Sam   [email]sammorxman@yahoo.com[/email]

---

### Post by Zer0Nin3r on 2009-05-07
Did a fresh install on the Toshiba U405 laptop (64-bit Alternative CD; Encrypted LVM) and no problems.  WiFi works out of the box.  Wasn't the case with 8.10.

Performed upgrade on Desktop and no problems.  Only minor things I've noticed is that suspend is still broken and the WiFi bars always show 13% across the board and never changes.  I am using the nVidia drivers I wonder if that is preventing the suspend.

Suspend does work flawlessly on the laptop.

---

### Post by cguy on 2009-05-07
I decided to do a fresh install and get a decent boot time.
35 seconds from GRUB to usable desktop.

(before: 55 seconds from GRUB to GDM and 30 more from GDM to usable desktop)

Nice, eh? :D

---

### Post by derwood5555 on 2009-05-08
Just wanted to add my congratulations and thanks to the Ubuntu devs for an excellent experience.

I upgraded from 8.10 to 9.04.  The upgrade took about 35-40 minutes on my system that I use for XBMC.

There were only two minor upgrade issues.

1 - GDM no longer signs me in automatically.  I'll google around and figure out how to fix that one.

2 - Pulseaudio was installed during the upgrade even though I had removed it while on 8.10.  XBMC and Pulseaudio don't play well together.  I've already removed both pulseaudio and libpulse. 

I then updated my sources for XBMC, and 15 minutes later, I had the latest XBMC release working perfectly, including VDPAU with the Nvidia drivers.

Thanks again to all involved with Ubuntu development.  I quit using Linux about 8 years ago because back then, upgrading from one distro version to another meant a complete reinstall.  I switched from Linux to FreeBSD because they already had a method in place for upgrading from one version to another in a more or less seamless fashion.  Ubuntu has closed that gap in a big way.

---

### Post by scarf on 2009-05-08
more problems :\

- [gnokii isn't working anymore](http://ubuntuforums.org/showthread.php?t=1150403)

- [can't adjust laptop brightness anymore](http://ubuntuforums.org/showthread.php?t=1147760)

- still, i can't find a way to verify a burned audio cd after write.

---

### Post by phoenix116 on 2009-05-08
did a fresh install on ext4 with a ext3 home partition of 8.10

worked very well for some days, then I got a grub error 2

fixed it with a live disk and fsck, which reported quite a few problems with files that share the same block or so

then i had to manually install grub and write a menuconf file,

this was some 3 days ago, now varius apps like synaptic, gnome-terminal etc are crashing and giving a "segfault"(referring to dmesg).

I hope I'll find a fix for this, but I think I'll have to reinstall(3rd time then....)

---

### Post by brntoki on 2009-05-08
Fresh install for me.  I've gotten the Jaunty-Freeze version, as have apparently many others.  It's not that there are many problems.  There's just one... which renders the machine unusable :(

---

### Post by ububaba on 2009-05-08
> **kshane said:**
> I use the ATI X-1650Pro, for which there is no driver at this time.  I upgraded using the upgrade manager.  My system boots but slows to a crawl and I am unable to use my mouse (can't click on anything).  Have to hit "reset"...

Again, PO'd at ATI for their slowness in releasing new drivers.

Kevin

A problem has come up with both keyboard and mouse, both 
freeze after the login. The cursor has been working perfectly 
earlier today and even in other OS. I tried with a USB cursor 
that too behaves in exactly the same manner. I have **reinstalled 9.04 **
several times. But no help.

Any suggestions on how to solve this? Thanks.

---

### Post by CalvinK on 2009-05-08
> **brntoki said:**
> Fresh install for me.  I've gotten the Jaunty-Freeze version, as have apparently many others.  It's not that there are many problems.  There's just one... which renders the machine unusable :(
I upgraded my Toshiba Satellite A200, two weeks ago.  I had a problem during installation. My system froze and I had to hardware restart. However, I was pleasantly surprised to find a procedure to fix it repairing the broken packages without further ado. I still have problem with the bluetooth part and pulseaudio. Nothing new since Intrepid Ibex.:o

---

### Post by wbee on 2009-05-08
Hello,

I did a fresh install of 9.4,32,i386 and XP over 8.10 and XP.

Using  gpartion and then the manual install,setting up a dual boot with XP,selecting the "4" option instead of the "3",and using a Linux swap,the install was flawless and fast.

-----------

+ The proprietary drivers process for Nvidia drivers was much better. I won't rehash all the confusion video drivers can cause,but these were flawless.

+ Using the "4" format instead of the "3" format caused no problems at all. I'm not sure it boots any faster,but as I understand the release notes,the point is it will be faster when half your drive capacity is used. We'll see.

+ Pigeon and Gimp continue to well impress me.

+ JJ and tvtime work a little better than in 8,10. However,one reason I kept a small XP partition is to use my TV card there. Now that is at least fifty percent me,as I have not yet poured though the documentation  required to set up MythTV to function as a recorder with time shifting and remote control function.

-  The volume was muted by default,which might confuse a first time user.

- On the initial boot after removing the live CD,and on the first boot after that,when I opened Firefox,I got a screen telling me Firefox was already opened. Then,I had two Firefox tabs at the bottom.I tapped on to the desktop and closed the other.

? instead of a plus or minus because I don't understand Pulse Audio well enough to comment in depth about it.

The setting in "sounds" and "volume" and "volume preferences" differ from the defaults in 8.10.

Every once in a while,I get pops in my speakers and checking the system monitor,even while Pulse is sleeping,it is using five percent of my CPU.

On the Pulse documentation site,there is a chart,that shows it is similar to a cardio vascular system. I suppose I have always thought of sound systems as nervous systems. I do not doubt that for someone using Linux to set up a recording and mixing studio, once the learning curve is scaled,that is works well.

For my purposes,listening to streaming FM or CDs,listening to the audio portion of TV,or listening to a different audio while watching television,it is overkill.

**All in all,JJ is a fine operating system. My hat is off to the developers and testers for a leap forward from II.

Except for the TV function mentioned above,I use this as my main operating system.

--------------

W

**Edit** 

+The computer janitor is a good function. This evening,I downloaded a screen configuration tool that also brought down another forty packages. When I uninstalled it, in favor of a different one,it left behind the other files. Computer janitor took those right out.

---

### Post by banduan on 2009-05-08
I first started using Ubuntu during Ibex.
It was brilliant and I loved it. I really liked the way installs worked.
Unfortunately, Jaunty has been a bad experience.

Speakers stopped working and I had to use the headphone for sound.
Then the broadcomm wireless suddenly stopped working after an update- which I thought had nothing to do with wireless- sometime around the 6th May.

Did a fresh install, used the problems as an excuse to switch to 64bit, but am still experiencing the same problems.

Clean install of Ibex now refuses to work so I very much regret upgrading!

---

### Post by el.norman on 2009-05-08
[LEFT]I didn't like it, X broke and i have problem with my graphic card, intel 945 GM, still using hardy heron.:eek:[/LEFT]

---

### Post by Bios Element on 2009-05-08
> **el.norman said:**
> [LEFT]I didn't like it, X broke and i have problem with my graphic card, intel 945 GM, still using hardy heron.:eek:[/LEFT]

Read the release notes...You might find something useful there. As will just about everyone with an intel card.

---

### Post by satellite360 on 2009-05-09
64-bit upgrade from 8.10.

Sound was broken:
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
but easily fixed by appending
options snd-hda-intel model=ref
to /etc/modprobe.d/alsa-base.conf

Reverted to Amarok 1.4 as 2.0 just doesn't cut it yet.

---

### Post by tibbar_eht on 2009-05-09
I upgraded fro 8.10 and now I get constant static after I log in for about 10 mins then nothing.  I have gone through all the volume Control inputs and the ALSA Mixer with no joy.  I get the drum beats when the login screen first comes up.  This is perplexing me.

---

### Post by klc5555 on 2009-05-09
"Upgraded" Mythbuntu 7.10 to 9.04. Which is to say backed up MySQL database (mythconverg), and critical files, did a clean install of 9.04 to the system drive of my PVR machine, and then restored my backed up MySQL database to the new installation and mounted the various storage drives that contain the recordings.

Nearly flawless: hardware detection is much better than in 7.10 --required no tweaking. Several flawed drivers from the 2.6.22 series kernels in 7.10 are now finally fixed in the 2.6.28 series.

Small problems: 1) since all-scsi drive designation has been the norm since 8.04, the automatic Grub configuration routine absolutely cannot link to the correct drive in mixed SATA/IDE systems. The first reboot always aborts with a Grub Error 2, necessitating a boot from the CD and a manual running of sudo grub to manually find grub's boot files and link it to the correct drive. 
2) In 7.10 I relied on xmodmap to run at x startup to map special keys. Finding xmodmap disabled in 9.04, it took considerable time to figure out that "input hotplugging" in x was the culprit, and more importantly, how to shut it off to restore xmodmap to functioning status.
3) The newer mythbackend/MySQL pair is somewhat fussier about starting up correctly and connecting than under 7.10. Mythbackend does not start correctly after a warm restart, and I find I need to ssh in to the machine to sudo mythbackend -d to get it going. It does start on a cold boot. It sometimes requires two or three (or more) attempts to connect slave backends to the 9.04 master after the master starts up before the connection is successful.
4) Mythbuntu 9.04's automatic drive partitioning scheme (big partition for /var/lib, little dinky partition for everything else) is OK for single-drive systems, but makes no sense for a multiple-drive system. This necessitates using gparted or the equivalent after installation to arrange the system drive in a more rational fashion.

But on the whole, the transition to 9.04 has been completely satisfactory. I'm quite happy with it, and no longer expect to have to backlevel to 7.10, as happened when I last attempted to upgrade to 8.04.

---

### Post by aikiwolfie on 2009-05-09
I'm think of going back to Hardy. I'm just starting to notice too many problems. It doesn't shutdown properly and the monitor won't come back on after being put to sleep. Even when it's just the monitor going to sleep.

9.04 still has too many bugs and issues that need working out. I still don't have DVDs working.

Interestingly the 32-bit version on my laptop seems to be a lot more stable. It has fewer issues.

---

### Post by joeray on 2009-05-09
First time dual partition Root & Home install-had to establish single ownership on home folder to remember sessions-used nautilus scripts package instead of cli

---

### Post by dnairb on 2009-05-09
I have just installed Jaunty on a second-hand Dell Laitude D600, which took all of 30 minutes!
Works very well. Wireless works as it should with the b43-fwcutter thingy installed.

---

### Post by castlefox on 2009-05-09
I upgraded from 8.10 to 9.04 

The problems I am having is that no video will play, even .ogg files.
I prolly is not an upgrade issue but not having the extra desktop effects with my intergraded Intel card is annoying

I have not found any good fixes for either of them.

---

### Post by pme 72 on 2009-05-09
Upgraded from 8.10. Ibex was working perfectly for me except for an intermittent keyboard sensitivity issue. The problem was reported to have been fixed in Jaunty. The upgrade was quick and painless. The keyboard sensitivity issues are gone. About all I had to do was make a quick trip over to the 64 bit forum to get instructions for installing Adobe Flash Player. 

Great update, thank you team Ubuntu!

---

### Post by Falcon1002 on 2009-05-09
I upgraded to 9.04 The upgrade went great! Except my video card is not supported real well. Oh well, I will wait on 8.10 until it is. Thanks for a Great Distro people!!! :D

---

### Post by baconman on 2009-05-10
I had Kubuntu 8.04 with lots of Ubuntu (Gnome) and other stuff mixed in so in order to get a clean system I decided to do a fresh install rather than an upgrade. Everything went fine until the installer ran grub-install, where it failed with a "Could not execute grub-install /dev/sda0. This is a fatal error". In the end I had to first install 8.04, then do an upgrade to 9.04. Now everything works very smoothly.

---

### Post by jwilentz on 2009-05-10
Absolutely terrible!!!! I'm a huge Xubuntu fan, but I have to say this is really a pre-alpha adventure rather than an operating system. With good practices I backed up all data to a remote server before embarking, so nothing lost.  Issues were that upgrade failed about 2/3 of the way through: couldn't get ACPI, no mouse recognition, no sound, no boot after upgrade.  Was able to access my system by the fact that the old kernels were still on the system, so using ESC I could choose the 8.10 kernel and boot away.  I thought this all might have been caused by some glitsch during the upgrase process, so I did a fresh install using the alternate i386 CD.  This had exactly the same result, although the initial reboot after install went fine, after performing the obligate update manager updates post-install, the nail was sunk deeply in the coffin, sealing the fate of 9.04 for me.  No boot, failure to see mouse, ACPI failure and finally the unix equivalent of the WIN blue screen of death --- the little drum majorette twirling her forward slash baton across the screen endlessly!!!

Look, I know that the Ubuntu team does not have the resources of a MS, but why not have listed this as nightly build rather than a "normal" upgrade?  Many of us use Xubuntu on older machines that will not run modern versions of Win, in my case a very elegant little Toshiba 3110t on which I've written scientific papers, book chapters, etc. and am reluctant to scrap.  My suggestion would be to accumulate as many "old machine" users as possible and doing a "stress test" of the proposed new release on that group in a more stringent way than in the general user population.  Once you get near 95% success, then call it OSC (owners strongly cautioned - may contain code that will freeze or burn your machine and possibly blow up the earth JKJK).  With the numbers reported so far in this poll it sounds as though you are very very far away from that sort of near universal success that I would think of as competitive with MS.  I'm going back to 8.04 as I write this.

Regards,

jw

---

### Post by jwilentz on 2009-05-10
> **phillies said:**
> As I said, update manager didn't work then and still doesn't work now. Even "do-release-upgrade" says "no new release found". Unfortunately, a fresh install is not an option, would take days to get everything up and running again

In Update Manager, look under Settings for the dropdown, where you can choose between"Normal Releases" or "Long-term Support Releases Only."  If you ***REALLY*** want to upgrade (and I use that term loosely) to jaunty, then choose "Normal Upgrades."  I would counsel you against this upgrade.  Look at the poll at the beginning of this thrread and you will see that only 19% of users found the upgrade to go flawlessly and ~ 20% said that the upgradr succeeded but they had to solve a number of issues with the system afterwards.  Especially if you have an older machine I would stick with Hardy or Intrepid.

---

### Post by ranch hand on 2009-05-10
The only things that has really bothered me are the timer at reboot/shutdown and the Jackalope artwork.

The timer can be fixed by going to Switch User, right click -> preferences -> uncheck Show confirm dialogs for logout, restart and shutdown.

Living here in the native land of Jackalopes I am aware that they DO NOT have deer antlers but have Antilope horns (antlers and horns are not the same thing).  Antilope horns are not very similar to deer antlers.

This is the kind of problem I am having to deal with under Jaunty.  It is exhausting and extremely frustrating to install.

---

### Post by jcats on 2009-05-10
Just did the upgrade from the update manager on a HP Pavilion dv9808nr laptop. This by far was the faster and best install/upgrade I've done. From clicking the upgrade button to reboot took just under 1 hour. (Upgraded from 8.04)
Everything I had installed before is still working correctly.
The great thing is how much faster everything works.
Definitely worth the upgrade.

jcats

---

### Post by Billy Pilgrim on 2009-05-10
I was running Hardy, and upgraded to Jaunty, and the upgrade to new distribution went very smooth.

However, when it upgraded my KDE 3.X to 4.X I lost my KDE pwmanager (Password Manager). I still have my encrypted file with my passwords, but I can't seem to find the updated version of KDE pwmanager.  Without the application, I can't access my encrypted password file, (which is giving me an anxiety attack, right now).

I typed "pwmanager" into the KPackageKit and it brought up "kde-pwmanager 1.2.4 Oubuntu4 (i386)", but had no focus on the "apply" button.

Reading through the description it said:

Package Name:
kde-pwmanager
Group:
Admin tools
Details:
With PwManager you can easily manage your passwords. PwManager saves your passwords blowfish-encrypted in one file, so you have to remember only one master-password instead of all. Instead of the master-password you can use a chipcard, so you don't have to remember a password to access the list. PwManager has a KWallet emulation layer, **_available on systems with KDE-3.2._**
Homepage: [http://passwordmanager.sourceforge.net/](http://passwordmanager.sourceforge.net/)
Size:
344.9 KiB

Does this mean that there is no version for Jaunty? Is there a way to access my ".pwm" file with any other password Manager?

I've tried looking for help in these forums, and on the Web with Google, but I'm not getting anywhere.

Does anyone have any ideas?  I would really appreciate any help.

---

### Post by ranch hand on 2009-05-10
Another good reason to use Gnome.  Sorry, I like and think choice is great, I know folks love KDE, I am just not KDE compatible.

---

### Post by supermorph on 2009-05-11
i have trialed a few versions of ubuntu, startign from v7 , i got sent the 8.04 series and 9.04 series on disk, (thanks cannonical, proved quite handy)

i then proceeded to make my own custom disc, so i didnt have to reinstall my gear if things went down,  i also kept ubiquity on as i am making a custom iso for xda-developers with thier tools for wm pda phones, so if something doesnt work i can just install to another partition without any upgrades or updates,

i found it quite simple, i had at one point with 9.04 that kde and gnome somehow inter-twined and somehow kde's control panel started on gnome, and vise versa, i figured i done it with all my messing about. i just reinstalled from my custom disk (which was made of jaunty alpha, then beta)

ive stuck with gnome, much easier and cleaner, no offence to kde people
it just felt to me, more productive less (fix this, click that etc)

i wish there was a way to put propper UUID's on ntfs partitions
this way i could have a VERY tidy and EXACT grub menu list.

other than that, this is actually good,
one snag i find with my having a hdtv, the login
when i installed the ubuntustudio themes and the like, it works well
but the text size cannot be changed for where u type your username/password,  if that was in the gdm login control panel this would be great, but i expected this as its not really designed for lcd monitor as its primary function, (samsung 32" le8rbd32) its a hdtv first, freeview second, and hdmi other (games/pc) third.

but still, great stuff.

---

### Post by grashdur on 2009-05-11
I reinstalled with JJ on both computers, and am very happy with this version overall. Jaunty Jack solved 3 critical problems for me: 
- I'm now able to save files over the network with OpenOffice
- I can now install Ubuntu normally onto the hard drive of my main computer, instead of resorting to Wubi (via Win XP)
- My Microtek 4800 scanner works (previously I had to do a workaround by reverting to an earlier sane driver)

I had one big problem while installing on my desktop computer: After installing the special screen driver for my nvidia monitor, I booted up each time into a blank screen. I solved this by booting into recovery mode, selecting "try to solve graphics problems" and then resuming normal bootup. I then found that the driver version 73 worked for me, though it's not quite as good as the latest version was for me in Hardy Heron.

---

### Post by weese on 2009-05-11
I was originally running eebuntu on my eee 1000ha. When I tried to "upgrade", my system came up to the login screen and kept popping up a message that said "login failed". I was NOT able to get rid of the message and log in. I could not fix it via the rescue boot option. Then I downloaded Netbook Remix to a usb and did a fresh install over the eebuntu. That seems to be working well so far.

---

### Post by brotherlen on 2009-05-11
Installed on a new T400 Lenovo. No problems as of yet, haven't played with however the ATI driver is giving an issue, so I reinstalled and just use the generic driver for it. Other than that, so far so good.

---

### Post by sagasha on 2009-05-11
I have used many other Linux Distro's but 9.04 64bit has given me all the features I wanted. I have been able to install 64 bit flash, 64 bit Java, 64 bit Anti-Virus, Multi-Media and more. I couldn't be happier.

---

### Post by skotos on 2009-05-12
Avoiding any amarok installation under Ubuntu makes it work incredibly fine and Jaunty smoothly discovered a few more hidden devices in my multimedia laptop.

Currently, I think that - the same can be said for grub 2 as well - installing amarok 2 in Ubuntu (not Kubuntu) should be discouraged by the repositories.

Since there is a wrong relationship between kde/amarok 2 and gnome, amarok 2 should not be availaible to Ubuntu users (are you one of the desperate pulse audio users?)

Selecting an app in the official repositories makes you feel free to install and run it with no issue, but this is not the case.

To me, these two apps have been released for production though they are still in their early alpha stage. I do both like them and I am eagerly waiting for further changes and updates, but I do not want to ruin a perfectly running laptop with them... 

I hope that in the future similar issues will not rise any more or - at least - might be anticipated by some warnings since they are not related to a single user configuration, but to a specific and commonly run application.

---

### Post by Simon-v on 2009-05-12
Upgraded cleanly, working flawlessly, with the exception of the missing ATI video driver, but, then again, i wasn't really using it for anything for a very long time... :)

---

### Post by texpat on 2009-05-14
Update manager made this a completely painless experience.

Funny that new installations should have a nearly equal rate of "no problems", "some problems", "serious problems".

---

### Post by peacen1k on 2009-05-14
This is my first attempt at running u8untu although I've had live cd's knocking around since 7.10.

I would say that looking at the stats on this poll a clean install is the way to go with future options.

I would also have appreciated a little more warning regarding the partitioning process at start-up and perhaps some good information on partitioning tools that run from live CD.

Actually I'm very happy with the way my system runs at this point... although I am extremely tired from chasing around forums looking up information on mtp, skype and partitioning.

All told I think there should 8e 8etter info availa8le on known incompata8ilities...... with gnomad2, skype, etc. if u8untu is going to 8e a successful alternative to windows for the average to moderately enthusiastic home user.

Also it's taken nearly a week of constant work and I still don't have the same functionality that i would get straight out of the 8ox with windows.

---

### Post by bmartin on 2009-05-14
> **texpat said:**
> Funny that new installations should have a nearly equal rate of "no problems", "some problems", "serious problems".
Well, figure that about 1/3 of users have a laptop with an ATI chipset, or a desktop with an ATI card and don't know how to install a new one. That would explain the case of the "serious problems". After upgrade, Ubuntu was virtually unusable on a fairly-new PC of mine, since fglrx for "legacy" chipsets is NLA. Setting the AccelMode in xorg.conf, which shouldn't have to be done anymore, helped... but the ultimate solution was to go on newegg.com and buy an NVIDIA card.

On my laptop, which has a Radeon 200M, I reinstalled Intrepid. On another desktop, I had no problems (NVIDIA chipset built-in). No more ATI crap for me. I'd say the three computers each met one of the three voting options listed above. The open-source radeon driver is not very good, at least not for my Radeon 200M or Radeon X1050 (the one I replaced).

Hardware detection was better than ever before, boot performance and overall performance have made great improvements, and the default desktop is looking a lot better.

---

### Post by ap90033 on 2009-05-14
You would think in this Economic Climate that ATI would be aware of what a pain their drivers are and would do everything they could to be AT LEAST as good as NVIDIA!
 
Do they not like selling video cards? 
 
FYI ATI I Spent $400 on a STUPID 4870X2 and still cant get it working right in Linux. :(

---

### Post by elektronaut on 2009-05-14
I did a fresh install from the alternate CD on my laptop which previously had 8.04 installed. This was the first time I had trouble since 5.04.

The software installation phase wouldn't finish, always bitching that some package (vinagre*.deb) would be corrupted. I checked the CD integrity in this laptop's drive and also in another drive, both times no complaints. Trying to go on with the installation from the last succesfully finished step was not possible, as the installation program kept on asking for the installation CD although it was already inserted - no other option than 'Continue' was given... So I had to redo the installation from the beginning. Trying to omit formatting the partitions again resulted in some bootstrap warning. OK, so I did it all again completely...

Surprisingly now it worked, everything went flawlessly in the end. Strange. Costed me a whole day (including the time spent on searching the net for possible failure reasons and ways to get around) where it should have been 2-3 hours.

---

### Post by skygazer on 2009-05-14
Generally i prefer to stay behind the curve and avoid common pitfalls, but something bit me today and i decided to try out Jaunty 64 bit. I setup a dual boot Hardy Jaunty installation. Partitioned hardy's drive and made a 80 GB partition for jaunty + 3 GB swap.. Installation went smooth. Hardware drivers installed in a few attempts. Installaed 48 MB update files which was done in few minutes. Havent encountered any bugs as of now.. All hardware works perfectly as it did with the new laptop when i bought it last year.
Improvements i observed are as below
1. Vista UDF format is supported and cdroms mounted perfectly outofthebox
2. Supported USB device outofbox unlike Hardy which needed tweaking of fstab file

wwill post more as and when i discover new things about the Jaunty X64

---

### Post by allstar1971 on 2009-05-14
Install was seemless and easy.

The only issue I have is the printing icon under system-admin is having issues.

Everytime I click on it, the printer configuration box crashes and won't show up. So I can't make any changes.

I have an amd-64 system with 2mb of memory.

Nvidia 96 video driver and compiz installed.

---

### Post by lotharjade on 2009-05-14
My upgrade experience has been somewhat unpleasant.  Why?  Video drivers.  :(

Before the upgrade I had upgraded to the Nvidia-180 driver and it worked fine (heck, even better than the old one (I loved it actually)).  Anyhoo, the upgrade worked except it wouldn't let me upgrade the driver.  It recognizes that the 180 driver is the one I need and is there, but when I click 'Activate', nothing happens.  I read the bugs and everywhere I could for a fix and tried a number of fixes, but I couldn't get anything to work.  

Then 2-3 weeks ago I posted a bug to launch pad and waited.  Not a word.  It doesn't seem like the Nvidia-180 video area gets much of a look at since not only my bug sits there with no notice, but a lot of other do as well.

Well, I finally got fed up last night ](*,) , and decided to ditch the Nvidia-180 driver and purge the evil from my system.   :mad:  I reinstalled the Nvidia-173 driver, and surprisingly it is working better than it was before.

I guess I just have to wait till they get the Nouveau drivers going, but upon looking on the status at their website it specifically mentions problems with my video card (Nvidia 8200).  Ugh...  :-?

:|  So, I am not overly impressed, but since I have had similar problems on the last two upgrades I am not overly shocked.  I guess I have drew the short straw with my video card, and getting stuck with a non-active driver bug system.

Other than that, I have seen a little improvement with Jaunty, but it seems to me everything mostly looks the same as the older version.

---

### Post by InkyDinky on 2009-05-14
So far these are the things that I've had issues with / am unhappy with:
1) conky broken.  I'm not using desktop effects so no issues there was working fine in 8.10.  It is running upon startup but it doesn't display anything on my desktop.
2) vino-server cpu hog. I vnc into my box from school and my pc is running hot due to this. Time to find a new vnc server
3) tomboy broken sorta.  I get the tomboy applet error warning where it asks if I want to delete the applet. I don't understand seeing as how tomboy starts up and pops open with the search screen.
4)log out prevention. I keep getting stuck when I try to shutdown with an "unknown application" not responding or some crap like that.  Ever since 8.10 I've been unhappy with the shutdown procedure.  I need to take some time to make it dumber, the way it used to be.

---

### Post by indigodog on 2009-05-15
Fresh Live CD install on a lowend recent Clevo laptop that's been running since Gutsy with Update Manager used exclusively for upgrades because regressions made fresh installs problematic.  

Perfect out of the box!  Except for the auto-partition UI bot slider thingy, which couldn't get a plain share with Win XP sized properly. Possibly a result of old Grub boot stuff not properly wiped.  No problem doing it manually.
Notifications is a welcome improvement over fixed-position applets.
Boot is as brisk as!
Clearlook skin is very much cleaner and crisper. 
Very welcome polishing of the basics.

Kudos to everybody.

---

### Post by Marcus_øland-Christensen on 2009-05-15
my install went okay, hehe, first time, i deleted everything to install ubuntu, and it didnt start after that haha. but i Got it working again so thats awesome, now im just figuring out all the small stuff.

---

### Post by x12796 on 2009-05-15
I did the upgrade from 8.10 to the Beta 9.04 and it worked flawlessly with fewer conflicts (as in none) than upgrading from 7.10 to 8.04 or from 8.04 to 8.10.  Later I did a clean install of 9.04 in order to rearrange my partition structure and 9.04's install was by far the easier Ubuntu install that I've done.  This sentiment was echoes to my by friends of mine who just upgraded to 9.04.

---

### Post by element_G on 2009-05-15
posting again with my 2cents on installing xubuntu 9.04 on a dell studio hybrid.

just got this box a couple days ago and im very pleased with running ubuntu on it. I am using this as a htpc attached to a 32" tv. (almost) everything works out of the box! The only snag was my wireless n adapter (dlink dwa130) which i got to work with ndiswrapper and the xp driver. Bluetooth is great, I easily paired my logitech dinovo mini. No problems playing hd content off of my home server. 

very impressed =D>

---

### Post by chouse626 on 2009-05-16
When it first loaded up I was excited and fell instantly in love.  I will never use Windows again unless through work or Virtual Machine.  My computer functions so much better.  Once I get used to the commands and functionality I'm sure I'll have many many more good things to say.

---

### Post by rishabh_destiny on 2009-05-16
I thought updates was a problem. I updated. And it downloaded 47 MB of updates. But the problem is that, it's not updating. All the stuff is downloaded but still, the update manager keep asking for updates. When I click install updates, the window just vanishes and nothing happens

---

### Post by joeray on 2009-05-16
I have a jaunty fresh full install. I have a vista dual boot setup. Win Explorer slowed down to a crawl for me with the suggested fixes ranging from "I don't know how to fix the problem" to a full os reinstall, All not acceptable. Jaunty worked fine out of the box with the only major hangup being my intel 945 Chipset (which by reading posts in the forums is something that will be fixed shortly). What I like about Ubuntu is the sheer speed of everything compared to vista. Also, this Jaunty requires about 30% less memory to run on my machine.
It's as if my pc now has 2gb ram instead of 1.5gb.
This is a great os for a basic user (docs writing, internet auction sites third party software use, pics and media basic use {cd & dvd burning}. The ease of finding software through the various available sources couldn't be easier. It looks good to the eye also. 
If anyone who has any minor complaints think that they can find a hassle free os think again. It ain't gonna happen because of all the different configurations on all the different machines out in the cyber world.


Compaq Presario RZ537AA-ABA SR5010NX
Intel Integrated 945 Chipset, 1.5GB Ram
Intel(R) Celeron(R) D CPU 3.46GHz
Jaunty 9.04 2.6.28-11 Generic Kernel
Gnome 2.26.1
Just know ubuntu is fine for about 90% of us who use a computer.):P):P

---

### Post by Chiapo on 2009-05-16
I downloaded the Ubuntu Netbook Remix 10.01 (karmic koala) IMG using {vomit} Windoze, because I haven't been able to get online using UNR 9.04 with my AAO.
Used Ubuntu ImageWriter to install karmic to USB flash drive... (I used flashnul to install Jaunty, which worked wonderfully!)
The USB key boots to the Ubuntu install screen, I select English language, then the splash screen comes up for a short time, then it drops to BusyBox initramfs prompt.
I don't know what to do after that! So I re-wrote the IMG to USB a few times with identical results.
I tried using wubi in {puke} Windoze, but received an error due to insufficient disk space!
I swear it's a vast conspiracy by m$ to keep this little netbook locked to Weendose...
If I could get online with Ubuntu, I would use old DOS FDISK.COM to wipe the hdd & do a clean install of Ubuntu Netbook Remix, but so far this dream remains just that, a dream...
I guess I'll try using flashnul to write the IMG to USB.

---

### Post by shawnyboi on 2009-05-16
Just installed the Jaunty Netbook Remix on an Acer Aspire One with XP preinstalled.  I installed from a USB flash drive, and had absolutely no problems with the install. The installer resized the XP partition to my desired size and did everything from there. :p

All drivers are working out of the box, with no configuration. Speed is excellent with stock 1GB RAM and Intel Atom CPU, but I'll probably upgrade the RAM to 2GB.

I had the netbook for less than 30 minutes before realizing I just can't do without Linux, even on a netbook. I went to download Kubuntu since I run that on everything else, and came upon the NBR and am VERY impressed with how polished and well supported it is. 

Good job guys, very very good job!! ):P

---

### Post by ugm6hr on 2009-05-18
9.04 NBR on an 8GB Dell Mini 9.

Easy. Flawless (so far).

---

### Post by cmnorton on 2009-05-18
I have been installing Ubuntu since 6.10 on four different platforms, three of which have been laptops. This 9.04 install has been by far one of the most pleasant experiences of any installation, Ubuntu, Red Hat, or CentOS. 

The hardware was a System 76 Gazelle Ultra that was purchased with the prior release. I had to re-establish restricted drivers for a modem and the System 76 drivers without a problem.

NetworkManager comes up almost immediately and does not take up to thirty seconds to connect.

---

### Post by arcane14 on 2009-05-18
Had Intrepid on my Toshiba Satellite L305-S5907, but went with a fresh install for Jaunty, converting to the ext4 file system. Went flawlessly, gets heavy use, no complaints so far.

---

### Post by tolito-cr on 2009-05-18
In general the upgrade went pretty smooth from Intrepid to Jaunty, but I've noticed that a few things I have not been able to use properly:

-Pidgin: when I backspace the screen (the whole screen!) goes black for a sec (like blinking). Also when Pidgin is running and there is music, sometimes the sound makes a really awkward noise...

-Xsane: Starting Xsane has been a difficult task, as every time I run it, the preview window is blank (or at least not looking right)... it takes like 4 attempts before it works...

Another thing that hasn't been upgraded is the driver for the Intel Media Accelerator x3100 so, I cannot use the Compiz Settings Manager, nor Google Earth...

Being a newbie to Ubuntu, and having only enjoyed it working properly in my new laptop for like 4 months, I sometimes regret having upgraded... but hopefully things will be mended...

Any thoughts???

e.

---

### Post by khamil8686 on 2009-05-18
9.04 works fine except 2 problems. one major and the second im not sure of the severity. the first one is on boot i get modprobe: FATAL:could not load /lib/modules/2.6.8-11-generic/modules.dep and the modules.dep along with 2 softreset failed messages, the os boots fine after displaying the fatal and 2 softresets, i would think a fatal would stop booting, but hey, im not complaining :) just worried that that might be related to my serious problem. i need suspend to work, i frequently come and go from my desktop and dont want to wait 30sec every time for it to boot and load the os, sometimes im just checking my email. i turn it off at night for those of you who are very green :) i can suspend fine just once, then when i resume, gnome-power-manager puts a plug icon in my system tray that says unable to get data... and im unable to suspend. i click the plug icon and it says hibernate or suspend and i click suspend, then it tells me that the action is forbidden. so i have a dual boot intrepid ibex and jaunty jackalope, ibex is my main one and jackalope is a little project i tinker with from time to time now. i do like how the dust theme is packaged with the os. and i like the splash screen more. havent really found out many differences between the two except those 2

---

### Post by redhand8888 on 2009-05-18
Im in the many problems category

My wireless card(Intel wifi link 5100) drops whenever I use bittorrent

It takes forever to boot, this just started happening

My graphics card(nvidia 9800mgts)  is recognized some times but not others

The weird part is that it worked like a champ at first, booting in less than 40 seconds, staying connected  to wireless

---

### Post by kapok on 2009-05-18
I had a great Intrepid install, fully updated. As soon as I upgraded to Jaunty, my computer would not start up. I had to do some data recovery with a live cd, and I'm back on Intrepid.

---

### Post by ktmom on 2009-05-19
Flawless upgrade.  Although I did replace my ATI X300 card for a NVIDIA GeForce 8600 GT before the upgrade.

---

### Post by AFarris01 on 2009-05-19
Flawless upgrades to jaunty from intrepid on 4 completely different computers.  No complaints!

Gets better every time... can't wait till 9.10!:popcorn:

---

### Post by frodon on 2009-05-20
Flawless upgrade here too, i just pushed the button waited 40 minutes (i have good internet connection) all was just working as it was used too.
I just needed to upgrade virtualbox kernel module as after every kernel update.

It has been running for 4 days now and seems really stable.

---

### Post by xebian on 2009-05-20
Upgraded straight to jaunty from hardy.):P

---

### Post by ranch hand on 2009-05-20
xebian,
OS::9.10 KK::Konky Kangaroo - NO - Kinky Kitty

---

### Post by Vegabondsx on 2009-05-22
Wireless broke on two of my laptops, but after running update with either another card or ethernet it was back up and running. :/

---

### Post by wristbandsnow on 2009-05-22
Hi dear, LAMP box failed to boot. Downloaded the server install CD and created a new VM in VMware Server. If doing this and problem is not solved. Then you are ignore it. Thanks

---

### Post by lbthrice on 2009-05-22
The babby is formed w/out defect.
I noticed some rumors bouncing around that upgrades can be tricky on machines with both kubuntu and ubuntu desktop environments installed...but I saw no negative effects.
On a probably unrelated note: I do observe some strange random theme-switching in gnome but I would characterize that as a feature; pleasant surprise to break up the monotony of success.
=D>THANK YOU DEVELOPERS FOR YOUR HARD WORK.  
do it for the moo

---

### Post by edyeeh on 2009-05-22
When I upgraded from update manager, there was trouble mounting the drives so I couldn't even complete the boot up process. I think it was because I started from the update-manager (which I couldn't finish because of my connection) then continued updating using the terminal.

But after some searching help on the net, I found a fix and now its running smoothly.


New Gnome desktop, new artwork, Gnome-Brave, faster boot. A worth it upgrade. :D

using Xubuntu and Ubuntu

---

### Post by x33a on 2009-05-22
well i had problems burning the jaunty iso to a CD. both my dvd writer and combo drive failed during the burning process. then, i burned it using my sister's laptop.

when i checked the live cd for errors using the disc inbuilt checker, it showed 1 error. but, i still proceeded with the install and it installed perfectly.

---

### Post by DimGothic on 2009-05-24
It went all perfecly, just that little issue with the hanging on shutdown/reboot but it's solved now :D

So far, one of the best releases imo.

---

### Post by growled on 2009-05-25
Did a fresh install of Kubuntu here and everything worked flawlessly.

---

### Post by bobnutfield on 2009-05-25
I used to do only fresh installs, but since Hardy I have upgraded and experienced minor difficulties, usually only on my Toshiba laptop.  Desktop and Acer Aspire One went flawlessly.  Still minor difficulties with the Toshiba, mainly to do with the wireless connection.  It connects to my WPA-PSK network just fine, but after about five minutes of being connected, it disconnects for no apparent reason.  This problem is consistent, and logs reveal nothing.  This laptop is my main workhorse, so I have to track this problem down and fix it.

The "good" changes are faster boot times and a generally better desktop experience.  But the wireless problem is a deal breaker on this laptop if I can't fix it.  Never had such a problem with Intrepid.

---

### Post by jezjones on 2009-05-25
New laptop, new install.

Mostly good, but no backlit keyboard or compiz (since no driver for the nVidia card.. only the standard nVidia driver).
[CORRECTION] - Backlit keyboard working fine, but has to be turned on with the Fn key and the right arrow (with a funny icon on it that might just be a lit up key)

Managed to get my vodafone 3g working due to this site....

[https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/)

Its Vodafone's own R&D, most of their sales people don't even know it exists.

Sound - working
Webcam (builtin) working in Ekiga but not skype (no skype problem).
Mic (builtin) working.
Wifi - working.
HDMI out - not checked but not optimistic due to graphics driver.

So, mostly good but a few niggles. 
The 3g support has moved on SO FAR in the last couple of years and was the only thing that really meant i had to have an install of something else.
Now, if we could just get 3ds Max working in Wine....

Good work developer people!

---

### Post by fridaythe14th on 2009-05-25
I always had problem upgrading before, but this time I only have minor complaints.

Vuze keeps crashing for some reason and the update manager did the only time I tried it (became unresponsive so I had to kill it and apt-get upgrade). Other than that I've been using it for two weeks with no problems now.

Oh, and I had to disable compiz because I use VNC. I don't care about desktop effects anyway but that should prolly be fixed.

It's running faster than ever now and boots much faster too. I did change to AMD64 kernel though, so I'm not sure if that's the reason.

---

### Post by brunoscunha on 2009-05-25
Fresh install went fine, but can't connect to certain wireless routers and a week ago vpnc stoped working (I need vpnc badly)

---

### Post by abhilash82 on 2009-05-28
I upgraded to Jauty Jackalope last weekend it was a breeze..
But I still have some minor issues with my compiz not working with existing drivers.

---

### Post by AICollector on 2009-05-28
When I upgraded, something went wrong; the system got slower and slower and slower...had to reinstall, I don't know if it's gonna happen this time.

---

### Post by brookie on 2009-05-28
upgrade worked but i cold nt use my MS wireless usb mouse or keyboard
i reinstalled intrepid on a new larger hdd anyway
inspiron 600m is getting old but it still works great with intrepid
:)

---

### Post by safetycritical on 2009-05-28
Can't get wireless internet to stop disconnecting and connecting every few minutes. It's stopping me from using Ubuntu more frequently. I've tried loads of things but nothing worked. Tried to remove IPv6 but that got rid of my wireless altogether !!! .. :-)
:confused:

---

### Post by rovingmutt on 2009-05-29
I installed it on a dell d600 laptop, only had 1 problem so far, the wireless did not work, so i found alot of good info on the forum and installed fwcutter with synaptic and it has worked very good, i have not checked everything yet but so far so good, love my ubuntu.

---

### Post by Saxie on 2009-05-30
Well my laptop is an old Sony Pcg-GR390.  Pentium 3 with 512mb of ram, and a 100gb hard drive.   There were absolutely no issues to speak of.  I dual boot currently.  

Couple of minor things, with the partitions and such.  What file system to use etc.  Drivers were also a non issue, had a Microsoft Wireless card that took a little tinkering.  

All in all, great, for just starting with Ubuntu/Linux.

---

### Post by Rofko on 2009-05-30
A lot of people on here seem to have had the same issues as me:

One: Wireless disconnects: [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

Two: Graphics problems: [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

Both have been an absolute nightware, especially given that both worked perfectly in 8.10. 

The worst uprage experience I have had since I started wuth Ubuntu - A LONG TOME AGO.

---

### Post by lordyosch on 2009-05-31
Upgrade went smoothly except sound was at first not there, then very quiet.

A quick google and a tweak of alsamixer later all is well.

One miniscule moan though, I prefer the old splash screen! (trivial eh?)


Jay

---

### Post by Tanker Bob on 2009-05-31
Second bite at the apple. I wrote a while back that I had no serious issues with upgrading from 8.10 using the package updater. Very cool.

I just put a new motherboard/CPU and 8 GB of RAM in my box, so installed 9.04 x86_64 from scratch. No problems at all this time - not even minor ones. I set up software RAID1 this round using the alternate installation disk and mdadm. Flawless. All my data on the separate /home partition survived intact through multiple install iterations (had some hard drive issues with the RAID unrelated to Ubuntu), even retaining my highly-customized desktop configuration. Outstanding!

Jaunty seems to be the best distribution yet. Thanks, development team!

---

### Post by gordintoronto on 2009-05-31
I did a fresh install, then copied my data files over from the previous hard drive.  Almost everything works.  However, when I try to use the microphone attached to my VIA 8235, the volume is very low and there is a huge amount of static.  It was not a problem when I ran 7.10.

This comes really close to being a deal breaker.

---

### Post by kutjara on 2009-06-01
Installed 9.04 Desktop on my HP 2133 MiniNote last night using the standard ISO.

The experience was about the most painless I've experienced with any Linux distro so far. Everything worked out of the box (even the Broadcom wireless card after Ubuntu recognized it and installed the restricted driver).

The only issue I had was the known one where screen resolution goes haywire after the Broadcom driver installs. A simple edit of Xorg Config to add the proper resolution fixed that in a hurry.

The MiniNote came preloaded with Vista, which made it slow to the point of being unusable. I didn't install Ubuntu at first because of the dire warnings I read about its incompatibility with the MiniNote. Instead, I tried Puppy, Mepis and Sidux. All of them had problems either with the OpenChrome graphics driver or the Broadcom wireless card. Hours of fixing produced only partial results, so I took the plunge to see if Ubuntu would succeed where the others had failed.

And it did, beautifully. I strongly recommend 9.04 for this netbook.

---

### Post by alastair-e on 2009-06-01
Originally had [this bug]("https://bugs.launchpad.net/ubuntu/+bug/365881/"), but I solved it by just unplugging my USB SD Card Reader. 9.04 has been the best version so far. 8.04 & 8.10 were pretty iffy with me.

---

### Post by cjv8888 on 2009-06-07
I did a fresh install of Jaunty of the / partition over Hardy.
A few quirky things happened which I did not have the patience to solve so I re-installed Hardy again.

1. Every time I clicked on Places/Home Folder I got vlc coming out blinking wildly.  This went away only by removing vlc.
2. Other machines cannot ssh into the system.  Open ssh server is installed.
The machine can ssh into other machines but refused connection to itself no matter what I tried to do in the Firestarter.
3. Cairo dock lost all the themes and applets did not show up and also lost the 3D aspects.

There may be other things but I rushed to reinstall Hardy so I could get all the updates and packages back while I had time.

---

### Post by jpmaglutac on 2009-06-10
On Desktop: Upgraded through Update Manager. Noticed that it seemed to flow much faster now, and I love the new interface! For some reason flash applications on Firefox don't have any sound :(

On Laptop: Installed Ubuntu Netbook Remix on Acer Aspire One. Worked like a charm ;) Honestly feels better than my desktop :D

---

### Post by jenkinbr on 2009-06-12
Fresh install.

Voted "Install - worked but had few things to fix, nothing serious though", but in reality, I have issues with the sound (link in sig) that I've been unable to resolve.

Also, had a major issue when adding a user to the system: the user was added, but the /et/group file was blanked (didn't realize till after a reboot :(), which cause me to reinstall.

Other than that, works great.

---

### Post by majamba on 2009-06-12
The upgrade worked almost perfectly except i had to set up the wireless on my macbook

---

### Post by relen on 2009-06-12
I have an original Acer Aspire One with HD, which on purchase was running Linpus. Although I had unlocked that, activated XFCE and added quite a number of apps, the process was difficult and not everything I wanted worked properly (Adobe Air for example was very erratic). Having read about different distros aimed at the netbook community I decided to try Ubuntu for the first time, namely UNR 9.04. 

On June 10 (I note this to perhaps indicate what versions of various elements I would have been using) I decided to wipe the machine and start from scratch; successfully downloaded the image and put it on a USB stick which booted successfully first time. I gave the machine a 1GB swap partition and made the rest "/" and ext4 (I since gather there are some potential issues with this, so perhaps ext3 would have been better, or even ext2?). 

Installation proceeded with no problems and on reboot ran the environment successfully. I started by downloading Skype from skype.com, which would not install because of dependencies that apt could find reference to but couldn't install. After a bit of to-ing and fro-ing I got all the bits installed but I could not get Skype audio to work in any sense (no input, output or ringing). Trying other audio apps I could get no audio.

At some point in my setting of preferences and tweaking the machine locked up, and on reboot the graphic environment would not come up and I ended up in an unresponsive "low graphics" mode. I reinstalled, again from scratch and again successfully. 

This time I first of all went to the updater and let it find new updates, of which there were many, and I left it to update. At some point during the course of installing the updates after downloading them it locked up, leaving the machine unresponsive and with the Caps Lock light flashing (a kernel panic I gather?). I rebooted and the system came up fine, so I went to the updater again and let it find the updates. This time I watched over it during the update process, occasionally moving the cursor to confirm it was still alive, and this time it completed successfully. I have not experienced the lockup problem since. 

In addition I noticed that the update had installed a more recent ALSA package. Later research indicates that this latest version fixes most, if not all, of the problems with the sound capability in the AAO. This time I got Synaptic to locate and install Skype which it did successfully with its dependencies. Although I had to change the Skype audio settings from the defaults, once done Skype worked in audio and video.

I installed the recommended fix for the WiFi LED and this operated as advertised (LED flickers during activity instead of being permanently off). On the subject of WiFi, I notice that the AAO now connects much more quickly to my wireless nodes (WPA2) than previously. As the fan appeared to be changing speed according to the temperature of the unit, and no problems were observed, I did *not* install the fan mod. 

One reason for the move to Ubuntu had been problems with Adobe Air, and I downloaded this from the Adobe site, having first installed the flash 10 player, also from the Adobe site. Both installed normally with no issues. I installed Tweetdeck and Seismic Desktop, both of which had given problems under Linpus/XFCE. The former took ages to download but both installed normally and both worked, although in the case of Seesmic the app initially came up with blank black windows, but on quitting it and re-launching, it worked fine an has done subsequently. Running either of these apps full-screen (Tweetdeck is great for single accounts, Seesmic for multiple) makes the AAO into an awesome Tweetmachine. During this process, Air called for an update from 1.5 to 1.51 and this also proceeded with no issues. 

I identified an issue with the netbook-launcher screen in that adding items to the Favorites menu did not work: instead the icons were added to the Other menu. [I have documented a work-around here]("http://ubuntuforums.org/showthread.php?p=7443503#post7443503").

For some reason the keychain is asking for a password on every boot. Looking into it. 

Apart from the fairly minor hiccups noted above, the operation and functionality of the installation has been excellent and far more effective and useful than the original Linpus/Fedora 8 installation on the AAO. I am already in a position where I am using the machine to actually do things rather than spending all my efforts making it work. Congrats to all involved.

---

### Post by xXchibidudeXx on 2009-06-12
Well, I came from Mandriva. I have some old computer from my family (2.4ghz single core, 512mb ram) so windows wasnt the best option in the means of speed and all. So went to mandriva because it worked incredibly well... But new technolgies came out so I decided to try ubuntu's new version and it works great! I had to change the xorg file because it was slow with my intel card...

I installed my root and swap on my 60gig drive and my home on the 80gig drive. Unlike mandriva multiple drives at once works flawlessly.

The only I don't like and hasn't improved is graphics and the inablity enable compiz on my card. But everything else was incredible especially with ext4 and uxa.

Also, all the software runs more stable than mandriva and the boot times are cut in half.

---

### Post by ranch hand on 2009-06-12
xXchibidudeXx
As you can see in my sig, I am not adverse to other OSs (except MS).  Mandriva is my second choice for people that ask.

I think you will like Ubuntu quite well.  I love it.

I think you will find it a lot less of a pain to get apps and update.

I hope you are using Ubuntu rather than Kubuntu but that is because I am not a fan of KDE or the package manager that it rides in on.  If you are using Kubuntu I suggest you install Synaptic, it works great in Kubuntu as does update manager.

---

### Post by Kryptick on 2009-06-12
Sad to say after the most recent update as of yesterday my eth0 dropped out and I couldn't be arsed rectifying the problem for longer than an hr so I've dropped back to 8.10

Have had a myriad of issues with Jaunty and I can't say that I've been very impressed with it at all

videos playing like crap
issues with maya 2008
general speed of the os
boot soft reset messages and boot times close to 1min
volume controls muting on boot all the time
etc
etc

so till 8.10 dies I'll be on that

---

### Post by orethrius on 2009-06-14
> **Kryptick said:**
> Sad to say after the most recent update as of yesterday my eth0 dropped out and I couldn't be arsed rectifying the problem for longer than an hr so I've dropped back to 8.10

Sorry to hear that.  I wonder if you could post a quick **lspci | grep net** to verify your card type.  My tower has two cards - one integrated, one a National Semiconductor (I think it was) gigabit that wasn't well supported by the earlier driver.  It's considerably better now, but it had its share of glitchy performance under both XP and an early Gentoo install.

> **Kryptick said:**
> Have had a myriad of issues with Jaunty and I can't say that I've been very impressed with it at all

I agree, but I'm willing to place blame squarely where it belongs.  I understand that ATi needs to make money, but cutting off cards that were still on the market last year?  That's not cool.  If you have nVidia or Intel equipment, video issues are definitely something to discuss in open forums, as those two vendors seem to have a better development turnaround.

> **Kryptick said:**
> 
videos playing like crap
issues with maya 2008
general speed of the os


ATi issues on my rigs, though if this is different on yours it may warrant further investigation.

> **Kryptick said:**
> 
boot soft reset messages and boot times close to 1min
volume controls muting on boot all the time


These almost sound like issues with customization.  Of my Ubuntu systems, not one has booted faster than a single minute; though, in my defense, I've never tried anything outside of the standard init process.  I also had some issues with my audio muting until I checked some settings in a mixer app somewhere.  In all honesty, I wish I could remember what I did to remedy that.

> **Kryptick said:**
> so till 8.10 dies I'll be on that

Ditto that, but my laptop's dropping back to 8.04 when I get half a chance.  That way, at least fglrx can take over until the open-source ATi team develops a workable 3D driver for the Xpress 200M (and, no, I strongly detest software rendering).

---

### Post by pous on 2009-06-15
[LIST]
[*]*Install - worked but had few things to fix, nothing serious though*
[/LIST]
[I]
i'd like to explain my vote a little... i love it, being a first time linux user i'm considering ditching windows completely, but had a hard time getting multimedia to function in firefox, anyhow got it solved and havent opened windows in round a week, and counting!
[/I]

---

### Post by pous on 2009-06-15
for those having issues with multimedia on firefox here is the thread that helped me solve it after a pair of days of looking... [click here]("http://ubuntuforums.org/showthread.php?t=1180896")

---

### Post by zaivala on 2009-06-15
I've already voted, but it was on a different machine I was trying to get to dual-boot.  I now have a separate Linux machine and a separate Windoze machine... a KVM switch, a hub connecting both machines to the DSL modem and, hence, the Internet... separate speakers, and a printer that doesn't like Linux so it's only connected to the Windoze machine.

When I got the new (older) machine ready to put Linux on it, I tried some Italian thing first... then Debian Lenny... if I were a real Linux hacker I could probably have gotten either of those to work, but as I'm still really a newbie despite years of trying, I finally threw up my hands and installed Jaunty.

Not a bit of a problem, none of the problems I had with earlier attempts at installation on the other machine (as dual-boot through WUBI), everything works great that can.  (Ubuntu is not responsible for OpenOffice.org's problems, which, if they would solve them, would allow me to sell my Windoze machine, KVM switch, etc.)

Hugs,
Moss

---

### Post by RobOrr on 2009-06-15
Upgraded, and found out that my card is no longer supported for new drivers by ATI, and that Xorg has a hissy fit. Restricted me to either using Intrepid and my closed source drivers (which let me play games) or Jaunty + open source drivers, where the most graphically intensive thing that works is playing a video. This is the first time I've experienced a step backwards in compatibility with Ubuntu. Admittedly, this is to do with ATI trying to force me to buy a new graphics card, but it's the New Xorg that won't support the old drivers that Intrepid currently runs fine.

---

### Post by conradin on 2009-06-15
I am currently running Jaunty on a intel desktop board (d854epi) with promise tech Raid IDE, and the intel chip-set for everything else. Works fine, no hassles setup. I do notice a fialiure for FFMPEG to create .oog, mp3 and other file types despite the fact it can create .wav files no problem. Im not sure how FFMPEG works, whether it must be supported by the sound card drivers, I have no idea. I can play mp3 and other file types however.  I'm not certain if this is Regression, but I installed 
Jaunty on my HP Pavilion ze(series) laptop. (ATI radeon 320 M graphics card, marvel Yukon Ethernet. 
In this case, I could not bring up a GUI to save my life. Also. I was only able to bring up a single shell prompt. I tried xfix and the other restore mode type programs to no avail. Strangely ( think any how, ) I was able to get on line and receive updates.  
After trying a variety of things, I went back to Hardy Heron. Where FFMPEG & my ATI Graphics card work fine.

I also want to say the new boot up and login screens are Awesome.

---

### Post by Prium on 2009-06-16
I updated to 9.04 from 8.10 twice - once on my 32-bit lappy and the other on my 64-bit quad-core work PC. For the former I had only one unresolvable issue: network manager could not connect to my wireless network. For the latter PC the update seems to have worked flawlessly.

---

### Post by CanadianBac0n77 on 2009-06-16
Well i'm a Vista/Ubuntu user. And i recently received a free (old) Desktop, but it had no Operating system on it so i googled "free OS" and found Ubuntu! It was amazing. I installed it, (No problems) tried it out and i loved it! Now its both my ubuntu Desktop and i got it setup with a second hard drive for a Personal File server! Ubuntu is amazing!

---

### Post by kndfs3001 on 2009-06-17
I upgraded 2 computers-worked flawlessly on one, and on the other, my mouse and keyboard stopped working in the middle of the update.  Then it got to the point were I had to click OK to remove the obselete packages, and I couldn't.  However, I just moved the mouse and keyboard to other usb ports, and it worked.  Once I rebooted, the original usb ports started working again.  This was just a fluke, and otherwise, the update went great.

---

### Post by techfanboy81 on 2009-06-20
I have installed and I'm exploring and learning to see if something has to be fixed, but so far it works ok for me.

---

### Post by dgeezer on 2009-06-20
I've installed Ubuntu several times now on my laptop (Dell Vostro 1400). I have never been able to get the Nvidia drivers to work. I'mm always stuck at not being able to enable appearance effects. I've tried the repository drivers and  the manual install from the Nvidia site. I've re-installed 9.04 from scratch at least 3 times now. 

I really want this to work but I may just give up.

---

### Post by Astound on 2009-06-20
Just voted and should actually have voted worked flawlessly, but because I chose a custom partitioning option, had some issues, initially with ext4 and later sound, which has since been worked out.

Overall a great choice for anyone new to Linux IMHO :KS

During install I chose to use ext4 filesystem, since it was offered and new, but only discovered afterwards the issues regarding freezes when deleting Video files (Large ones).

Searched the forums and found that this was known issue and most pointed out that the Kernel 2.6.30 fixed the issues on ext4 file system so I installed that ;)

No lock ups after the Kernel upgrade and speed is phenomenal, around 25 seconds to boot up, snap crackle and pop then raised its ugly head, Sound :p

Turns out that there appears to be a regression on the Kernel 2.6.30 regarding Sound.

Any mp3, wav, ogg, and even movies started skipping every second or stuttering after installing that Kernel, so now what?

Did some Googling and forum searches and it seems that I could downgrade the Kernel to 2.6.29 which has solved the sound issue :lolflag:

I have been weaned on the BSD's and used Slack some time back so not new to Linux but new to Ubuntu.

As a South African, I am imensely proud of MS achievements and what a fantastic job done on Ubuntu.

All of the above were not issues as such, just pointed out these because of my initial choice of going with ext4 file system instead of ext3.

So right now, everything just works and this is my Howdy, _not_ Goodbye   ):P

Kudos to the developers on this fantastic distro.

---

### Post by Rillanon on 2009-06-20
Upgraded last week. All in all okay. Not a smooth ride but everything was within my ability to fix (or shall I say google). 

Had some trouble with grub not booting off ext4; resized a ext3 /boot and used live CD to fix grub record. 

Screwed up fonts by compiling gtk2.16; but to be fair this was my fault, i should have apt-get install build-essential first. 

Pissed off gf because i wouldn't go to bed 3am in the morning D:

everything is running smooth atm; ext4 on my WD raptor is FAST. I booted into GDM under 10 secs. 

NVidia binary + Alsa X-Fi drivers installed without a hassle. 

One issue was that my 1TB samsung hd had to be fsck.ext3 checked in order for jaunty to see it as a device. 

I miss ctrl-alt-backspace tho :(

Benefits so far: 

ALSA much much smoother now.
random errors gone mostly; I haven't noticed any legal errors from 8.10. 

Conclusion: Great job Ubuntu! Every upgrade is getting better!

---

### Post by xenosaga456 on 2009-06-20
it worked with some problems but i fixed them 
nvidia card didnt work at first in stall did an update then i whent to the restricted driver adnd hade to download the new version and worked fine oww and one great thing i was suprised at was that my Atheros 5007 worked out of the box i thought i was going to have to spend like 5 hours looking up how to fix it lol oww and my uploads work great to:lolflag:

---

### Post by pbpersson on 2009-06-20
I did the upgrade on my main desktop last night from 8.10 to 9.04.

I took the route where I kept the same home partition with all my settings, did a fresh install to the root, then with that one line command re-installed the 1,923 packages I had installed in the 8.10 version.

It works flawlessly and everything is setup just like the 8.10 version - even my desktop settings and my quicklaunch icons in the panel.

AWESOME!  :guitar:

---

### Post by Committed on 2009-06-21
I just installed 9.04 on a new IBM laptop.  Tried to install it with Wubi, but it wouldn't.  Got an access denied message.  Took out my 8.10 disk and installed that, then just upgraded to 9.04.  Working great so far.  Wanted to try it out with Wubi first before I committed to a complete install or dual boot. 

Not sure If I'm going to upgrade my main desktop yet from 8.10.  Had some trouble with the beta version although I'm sure those kinks are worked out now.  Maybe give it a go this week.

---

### Post by sdbrogan on 2009-06-22
I got the freeze problem too (on a clean install), with no solution in sight; so can't use Jaunty.

---

### Post by ssri on 2009-06-25
Initially, I tried to do perform the upgrade from the notifier on my intrepid install, which promptly warned me that Catalyst may not support my video chip (M64-S) in Jaunty.  From reading the forums, I witnessed a lot of wailing and teeth gnashing from ATI sufferers.  I began to understand why many users dubbed ATI as "A Thousand Irritations".  I tested Jaunty on my system with the livecd and came away unimpressed with the included radeon driver.  Sure, I could enable kwin compositing for a little while before X came to a screeching halt, yet another critical bug users have been complaining about in launchpad.  So, the lack of GLSL support combined with random X freezes from the radeon drivers forced me to stick with kubuntu intrepid until the oss drivers are ready for primetime.

---

### Post by goldfish2 on 2009-06-25
> **sdbrogan said:**
> I got the freeze problem too (on a clean install), with no solution in sight; so can't use Jaunty.

I assume you're refering to the same problem I got where my keyboard and mouse wouldn't work upon arriving at the login screen because of the issues with Hal.  I give it a 0/10 as it is completely unusable.

(Okay, so, not completely, I was able to log in remotely and change screens using the "sudo chvt 1" command... but that didn't help much as I had to whip the whole system to make it usable and downgrade it to 8.10 anyway)

Still no fix that I'm aware of.

---

### Post by KegHead on 2009-06-25
Hi!

It was flawless.

KegHead

---

### Post by philcamlin on 2009-06-25
no issues at all :popcorn::popcorn:

---

### Post by magh-87 on 2009-06-25
It installed flawlessly on both of my machines (laptop and desktop), however both are relatively out dated so they can't really try any of the features that newer, more powerful machines can do. 

Overall I'm fairly content. It's stable. My laptop hasn't had any crashes where Windows used to crap out on me fairly often. My friends seem to like ubuntu also.

---

### Post by pbpersson on 2009-06-26
> **pbpersson said:**
> 
I took the route where I kept the same home partition with all my settings, did a fresh install to the root, then with that one line command re-installed the 1,923 packages I had installed in the 8.10 version.


Someone asked me to post how I re-installed all my previous packages using a one line command from a saved file.

The instructions are here:
[URL="http://ubuntuforums.org/showthread.php?p=7208608#post7208608"]
http://ubuntuforums.org/showthread.php?p=7208608#post7208608[/URL]

---

### Post by jimbean on 2009-06-26
just upgraded, worked cant complain so far {for free ubuntu hehehehe}
just as good as the competition who ever that is ????
i have internet upgraded for the last 4 distros, machine still boots
i`ve never seen that ever the whole of my computer time on earth
thanks ubuntu

---

### Post by BlazeFire247 on 2009-06-28
I'm very, very new to Ubuntu (I don't mind though :D), and Jaunty is my first install. I must say it was quite amazing. It installed perfectly with no errors.

---

### Post by Blood//Stain//Child on 2009-06-28
My only real technical issue was the lack of a proprietary ATi driver. Everything else is fine.

---

### Post by jenkinbr on 2009-06-29
managed to solve my sound issue.

All is well now. :)

---

### Post by Vasator on 2009-06-29
I was able to successfully upgrade from 8.10 
I have a Vnideia Geforce 9500GT that will not run on the restricted drivers
I re-installed 9.04 and formatted my old partition
Restricted drivers still will not work.
I have gone through the forums and posted a thread but am receiving no help.

Thinking of ditching Ubuntu and installing XP 64-bit

---

### Post by ktmom on 2009-06-29
> **Vasator said:**
> I was able to successfully upgrade from 8.10 
I have a Vnideia Geforce 9500GT that will not run on the restricted drivers
I re-installed 9.04 and formatted my old partition
Restricted drivers still will not work.
I have gone through the forums and posted a thread but am receiving no help.

Thinking of ditching Ubuntu and installing XP 64-bit

Have you gone to nVidia's website and downloaded the newest driver?

---

### Post by doublemike on 2009-06-29
I did an upgrade from 8.10. Works for the most part but the ATI driver has been a real pain since my card is no longer supported by AMD/ATI. ( I've got a X1200 on my laptop )

I get a very annoying jitter/flicker when large parts of the screen are being updated. The worst is when I'm viewing a JavaScript slide show with a fade effect. The display jumps, jitters and flickers. I can downgrade my video to something really rough and don't see the problem. No problem with the "vesa" driver. My fps drops way down, but the problem goes away. Go figure.

I'm hoping I can get this puppy fixed so I'm not having to downgrade to 8.10. I've been tring different setting I'm finging but nothing seems to be fixing it.

---

### Post by Abzddon on 2009-06-29
I just recently decided to install linux to try it out, and done so along side windows. After the installation was done, I was unable to and still am  unable to install anything on linux because there isn't enough space, because for some reason during installation it didn't give it self enough space, although I have over 200gigs free!

Iv'e been searching for hours and doing things I don't even understand to increase the partition size, but it seems everyone has slighty different issues to my problem and I am still unable to fix the problem.

Even uninstalling Linux seems to be a mission on its own.

Very very very bad experience, nothing works, and a huge waste of time.

:cry:

---

### Post by rs3 on 2009-06-29
Installed to my laptop anew yesterday using the amd64 arch.  Everything has worked brilliantly.  After the usual battery of updates via update-manager, I was able to activate Compiz and run accelerated games on my Intel GMA 965.

Installing to my desktop now; I anticipate success.

---

### Post by jenkinbr on 2009-06-29
> **Vasator said:**
> I was able to successfully upgrade from 8.10 
I have a Vnideia Geforce 9500GT that will not run on the restricted drivers
I re-installed 9.04 and formatted my old partition
Restricted drivers still will not work.
I have gone through the forums and posted a thread but am receiving no help.

Thinking of ditching Ubuntu and installing XP 64-bit
A link would be nice, as well.

---

### Post by #11u-max on 2009-07-01
clean install, everything is smooth as butter except that my resolution is HORRIBLE!!! i can't stand having the stevie wonder resolution setting that i can't change. i've tried 3 or 4 different xorg.conf changes but they either did nothing or screwed it up to the point i had to use recovery mode to reset it. if ANYBODY can help me in ANY WAY, i would greatly appreciate it!

---

### Post by gordintoronto on 2009-07-01
> **#11u-max said:**
> clean install, everything is smooth as butter except that my resolution is HORRIBLE!!! i can't stand having the stevie wonder resolution setting that i can't change. i've tried 3 or 4 different xorg.conf changes but they either did nothing or screwed it up to the point i had to use recovery mode to reset it. if ANYBODY can help me in ANY WAY, i would greatly appreciate it!

What is your video card?  What is your display?  Did you install a driver from the video card manufacturer?

People want to help, but they need data.

---

### Post by robertsdf on 2009-07-01
I have been using 7.10 for a long time. It works flawlessly. I have a dualboot system still using Win98. Ubuntu 7.10 is perfect. I installed 9.04 dual boot on my new Vista computer. I only have dial up modem. I installed 9.04 on 04/23/2009. I have spent the last 2 months solving the internet issue with dialup modem. I still can not get gnome-network-admin to work but I am able to connect using wvdial and gnome-ppp. I got all my help through this forum but getting information was a challenge and took a long time. Now I can not get 9.04 to change the settings on my Samsung LCD monitor. It will only let me 800:600.  I am looking for a display solution now. Also, my old 7.10 works perfect for music internet stations like yesterdayusa but when I try to listen on 9.04 I get error message can not decipher mpeg1. I am now searching for a fix for that. I was very happy with 7.10 but 9.04 has been extremely challenging.

---

### Post by Vasator on 2009-07-02
> **jenkinbr said:**
> A link would be nice, as well.

Here ya go...
[http://ubuntuforums.org/showthread.php?t=1199055](http://ubuntuforums.org/showthread.php?t=1199055)

Since my last post there has been two responses to my post

---

### Post by Umang on 2009-07-04
After upgrading to Hardy and Intrepid, I was very disappointed with the slow speed and multiple errors/ problems (though they were small they were irritating). The Jaunty upgrade was quick, problem free and awsome!

I can feel the difference in responsiveness. Even clicking the menus feels good! :D

Umang

---

### Post by spike_naples on 2009-07-04
+1 Upgrade - worked flawlessly

---

### Post by rallen71366 on 2009-07-04
Sadly, this is the worst experience I've had with Ubuntu in over 2 years. I did a clean install over 8.10 (had to work through a few graphics issues with 8.10, but it was easy using EnvyNG). Got a nice Spaceball device to do Blender models with, but needed a newer version than apt was providing. I figured now would be a good time to upgrade to jaunty, upgrade the driver for my nVidia 6200 card, and get the latest Blender. Yay! 

BOOO! I've been fighting with the latest xorg (1.60) for the last week and a half! I'm mad enough to change distros! I've followed this [http://ubuntuforums.org/showthread.php?t=990978&page=75]("http://ubuntuforums.org/showthread.php?t=990978&page=75") thread several times with different levels of FAIL. Xorg isn't seeing the devices in my conf file, I'm stuck using the onboard VIA graphics adapter and 17" CRT instead of my nVidia 6200 and 22" LCD. 

Sorry for venting, but my frustration level is through the roof! I'm to the point that I get sick looking at my machine (AMD 64x2) and resort to using my little Acer netbook to get online!

---

### Post by Shazaam on 2009-07-07
Went over and abused my brothers broadband and downloaded Ubu 9.04 and the latest Mint. Jaunty install on a fresh ext3 partition (shared /swap with 8.04 and 8.10) was a success with zero hickups. Spent the next two days back home on my dialup installing updates :(
Boots and loads a lot faster than earlier Ubuntu versions which is impressive. Hit the usual snags installing nvidia's proprietary driver but it runs compiz/emerald fine. Why does nvidia think it is ok to put "xorg.conf.new" under / ? 
The two changes that I do NOT like are the new update manager popup and the fact that logout/shutdown has been moved. The old update popup wasn't as annoying as the new one. Gotta dig under the hood and fix it (or break it). :)

Homebrew pc- 20" HP lcd; AMD AthlonXP3200 on a Soyo Dragon board; 2gigs ram; 2 hd's (one 80gig with Windows' one 320gig with linux); a BFG GeForce 7800GS card; and a SoundBlaster Live! 4.1 Digital.

---

### Post by guitard00d on 2009-07-07
The thing about 9.04 that's driving me nuts is that the RT kernel causes the system to lock up (and I've installed it on 4 different systems, a Dell Inspiron 1200 laptop, a homebrew AMD system, a homebrew Pentium 3 system, and the Netbook Remix on an Acer Aspire One D250).

Bug #366952 on launchpad.net says that kernel with the stock 2.6.29.4 kernel compiled with the .config from Ubuntu's 2.6.28-3-rt source package doesn't exhibit this problem. But, the person that says that doesn't give any kind of specifics as to where to get this kernel source or how to use make-kpkg to do the job.

If anybody can provide me with any tips on how to obtain this other kernel package for Ubuntu, I'd appreciate it. My Acer Aspire One D250 is the brain for my keyboard rig in the band I play for. Without being able to use the realtime kernel, I have enough latency that it's a real burden to deal with. So any help at all would be hugely appreciated!

---

### Post by Liametc on 2009-07-07
just upgraded from 8.04 through 8.10 to get to 9.04. Randomly after upgrading to 8.10 so i could make the jump to 9.04, i appear to have both the kde and gnome desktop running at the same time. And since going from 8.10 to 9.04 wicd has dissapeared so i cant get on the internet and every time i try and open a program it wont load. 

has anyone else had this problem.

i cent fix anything because terminal also wont open:mad:

luckily i backed up my system so i can always revert back to hardy if i need to;)

---

### Post by StarsAndBars14 on 2009-07-11
Just upgraded from 7.10 to Jaunty today, as a matter of fact I just got done with it and I started it about six hours ago.  

First, I couldn't even begin the upgrade owing to circular dependency problems with libc6.  So I just started forcing APT/dpkg upgrades and removals until I was blue in the face.  About 10 or so different things wouldn't - initially - install on me, and scrollkeeper messed up GNOME something bad so it had to be uninstalled and reinstalled after every Python package was done with.  Even then I had to remove GNOME and reinstall it.  Had to remove Compiz packages that conflicted with each other in the install process.  

Then, after everything was set up, the real fun began. :D

I had to use a GParted CD to mount my boot partition in order to fix Grub (I dual boot with Win XP on this computer) and that didn't get done for a while.  Then, I had to mount my / partition and - since I didn't remember my root password (its been 2 years since I last used this system) chroot to create a new one.  Also had to put reboot into sudoers (not important, merely for the sake of convenience between restarts) and what not.

Xorg wouldn't work after that, owing to missing freetype/nvidia drivers.  Had to uncomment freetype from config and uninstall nvidia.  Went with the open source nv driver.  Xorg again crapped out and complained about /dev/input/wacom.  To my surprise I found neither the keyboard nor the mouse would do a thing inside GDM.  After nosing around for a while, found dbus/hal were the culprits.  Recreated default symlinks in the required runlevel order (first DBUS, then HAL.)  

After that, I got back into GNOME, downloaded a few packages again - like gnome-terminal - and I'm working fine.  Except for 2 things in order of importance:

1) HWClock can't be accessed.  Nary a twitch coming from /dev/rtc.  lsmod shows no rtc modules loaded, and something like modprobe --dry-run /lib/modules/$(uname -r)/drivers/rtc/rtc-core.ko thinks its trying to access a module separated by underscores instead of dashes.
2) AVG dazuko module isn't insmod'
One more thing: 3) I'm seeing a weird 131.6MB volume appear in "Places" that I have *ABSOLUTELY* *NO* idea about. It can't be my XP partition or system recovery.  Wth is it. 

And that, as they say, is that.

---

### Post by note32 on 2009-07-11
Work right out of the box for me:mrgreen:

---

### Post by Clorow on 2009-07-11
Pretty much everything went off without a hitch, although I had to uninstall my FGLRX graphics card driver because it was taken out of the restricted repository. :sad:

---

### Post by khamil8686 on 2009-07-11
this is an update to my previous post on this thread, i noted i had a major problem that isnt solved, i was just overlooking a major piece of information. jaunty is great for me :) working fine except bluetooth in kde i cant send files from my computer to my phone, works in gnome though :)

---

### Post by Mikekoi on 2009-07-12
Installed Flawlessly On Fujitsu Siemens Amilo Pi1505 Laptop

Installed First time on MSI7316 Mobo Homebuilt Computer but failed to identify and drive the Broadcom Wireless Card. Still working on this.

---

### Post by lavezarez on 2009-07-13
Hi,

I made a clean install of jaunty in my aging acer travelmate 290 (intel centrino, 256mb ram, 40gb hd) and I must say overall I'm very pleased with it. Pleased because it runs much faster than the XP OS that was previously in it.

my rating: Upgrade - worked but had few things to fix, nothing serious though

Coming from a Microsoft Windows world, I must say Ubuntu 9.04 is the best experience I've had as to ease of installation.  I've tried Open Suse, Mandriva, vectorlinux, even Ubuntu 8.04 LTS... but it was only with Jaunty that I managed to do what I wanted to do at home.

These were setup I have solved and are now all working:
1. Installation of Ubuntu in the laptop
2. Configuration of my broadband wireless (in the Philippines, using Sun Cellular Huawei e160 modem) - man, this was great! no need for wvdial, etc. at all! Jaunty installation painless!
3. Playing audio Windows files - from synaptic, just install the codecs
4. Integrating iPod sync - with Banshee; again easily done with synaptic package :)
5. Creating new users for the family - a breeze with System - Administration - Users and Groups
6. Sharing my internet connection via the built-in laptop's wifi; sharing it with a Win XP laptop - again, this was easy! Just had to create a new wireless connection and follow the prompts in Network Connection. Then enabled the wireless, and had it detected in my XP machine - viola! it works!
7. Installing Firefox 3.5 (shiretoko) and making Ubuntu run that instead of the old 3.12 Firefox - this was a bit tricky, had to do some research and do what a [linux user]("http://www.ubuntusolutions.org/2009/07/ubuntu-firefox-3-5-install-use-ubuntu-mozilla-security.html") advised - sudo apt-get, etc. (argh!) - but had in running in the end :)

--- and here are the things I couldn't setup just yet:
1. Using Linksys Wireless-G WPC54G ver.3 as my wifi card; had to settle for the laptop's built-in wifi
2. Ubuntu not auto-mounting my dvd/cdrom; when I insert a disk, and try to mount it manually, it says "Unable to mount location; can't mount file"

---

### Post by anung524 on 2009-07-13
I've been using Ubuntu for almost a year now, and i love the Jaunty.
I installed it on my amd athlon X2 desktop, compaq cq40 laptop, and aspire one netbook. On my desktop, everything works out of the box. No flaw whatsoever.

On my compaq almost everything works out of the box, i just got one problem with the sound driver, but now it's solved.

As for the aspire one D250, also almost everything works out of the box. But i still have this one problem. The ethernet LAN card doesn't work. I haven't found any solution for that problem on the net. By the way, I'm not using the netbook remix version on it. Its the Ubuntu Desktop version.
Well.. but i'll keep searching.. :)

Nothing can stop me from using Ubuntu..

Greetings from Indonesia. :)

---

### Post by rogueleader12345 on 2009-07-16
I had Intrepid on a 4 gig flash drive and decided after I crashed it to just go ahead and use Jaunty. I wiped the drive, got Jaunty on it fine. The only real problem I've had with it, or Intrepid, is getting my sound to work and my ATi X1900GT. I've pretty much given up hope that I'll ever have desktop effects because every driver I've tried has crashed it. I got my sound working, but still having issues with Flash. If I have a song on my desktop, I can play it and hear it fine. But if I'm trying to watch a video online, I don't get sound. Not a peep. I tried using my Firefox off of my flash drive that I use for Windows and still don't get any sound for online videos. Oh well.

---

### Post by Andras B. on 2009-07-16
Just another satisfied Ubuntu Jaunty user here ):P

I installed it on my desktop machine, installation went fine, everything works out of the box. I am very pleased with this release, I had trouble with earlier editions, but Jaunty did the trick.

Finally, a decent, user friendly Linux, that looks good, feels good, and gets the job done, and is actually usable in everyday computing. I think I will be using Ubuntu Jaunty for a long time as my primary system. :)

Cheers!

---

### Post by tmt1096 on 2009-07-16
eeePC 900HA
Installation on SD.
Had to tweak configuration for touch pad. (Touch pad jumpy).
Mute still is not working - (Mute the sound output put up loud static)

tmt1096-eeePC 900HA

---

### Post by keepitsimpleengr on 2009-07-18
Upgrade from 8.10 to 9.04 amd64 has been total disaster.

Required many hours and still 9.04 not doing as well as 8.10.

Many bugs (some marked as fixed but not available) in Launchpad.

2nd monitor essentially useless after this upgrade.

Many features do not work.

Hard to believe release would be made with so many problems.

Note: 32bit upgrade on different machine went well???

---

### Post by mesmith on 2009-07-19
The data indicating 18% with many problems after an update is a sad number.  Presumably, updating a stable 8.10 user should be the easiest of all paths.  Failure with multiple unresolved issues should be a single digit problem at best.  Sorry, too many regressions for happy 8.10 users means the update should have stayed in the oven longer.

---

### Post by Dullstar on 2009-07-22
I installed with Wubi.  Works fine.  I have not had to upgrade yet, because when I made the switch Jaunty was the current version.

---

### Post by joelgsf on 2009-07-22
I gave a big try with Jaunty AMD64 using the Live CD on a DELL Vostro 1510 notebook. There were no hard problems to solve. As I am currently using Hardy Heron 32 bits, I was surprised as how well it went, including automatic recognition of the Wi-Fi system, and even automatic recognition of my 3G Modem, which really brings me mad sometimes on Hardy (I had to use GPPP with it, but it does not go well every time). 
All in all, I found it marvelous and I am planning to switch to Jaunty soon, and really making a big switch as I plan to leave behind my XP, which is my primary boot on this machine.
The only real problem is with the Intel graphics chipset, which is beeing discussed in this thread, and I was also pleased to see today that it seems to have a workaround this problem, though not yet a final solution. I believe that now we do have something to compete with Microsoft.

---

### Post by Dullstar on 2009-07-23
Ubuntu is way better than Windows, so we can compete now, can't we?

That's right Microsoft, tremble with the terror; your monopoly is threatened by open-source free software!  You should be so embarrassed!

---

### Post by Blu Fox on 2009-07-24
First time ubuntu user here.
I'll have to say, installation was pretty painless, as well as installing flash and java to complete my internet needs. I absolutely love the fact that my wacom tablet was plug and play, I was worried that I had to do some complicated terminal stuff to get it working. 

Had some issues getting a playstation emulator to work, though. Finally got pcsx installed but I can't really configure my controller, maybe because I didn't got all the plugins yet :/

All in all, I'm happy with the switch.

---

### Post by ranch hand on 2009-07-24
> **Blu Fox said:**
> First time ubuntu user here.
I'll have to say, installation was pretty painless, as well as installing flash and java to complete my internet needs. I absolutely love the fact that my wacom tablet was plug and play, I was worried that I had to do some complicated terminal stuff to get it working. 

Had some issues getting a playstation emulator to work, though. Finally got pcsx installed but I can't really configure my controller, maybe because I didn't got all the plugins yet :/

All in all, I'm happy with the switch.
If you would be so kind, I would love to know what wacom model you have and if all features are supported.  I do not and never have had one of them but I want to.

---

### Post by Velvet_Man on 2009-07-24
I ran a distribution upgrade through Update Manager from Ubuntu Studio 8.10 to Jaunty.

The upgrade went seemlessly with only a few minor problems. For some reason Cairo Dock no longer has a theme for the WiFi connection signal strength applet. It was just showing a numeric percentage without the coloured globe icon. I just made my own icon set to replace it, so that wasn't a big deal.

I was wondering why I wasn't seeing the new notify_osd system that I read up prior to the upgrade. After some Google searching I discovered a bug report about it. Apparently without the meta package ubuntu-desktop installed, the upgrade doesn't install notify_osd. And since I use Ubuntu Studio, I have the ubuntustudio-desktop package installed, not ubuntu-desktop. So I had to install notify_osd myself through Synaptic. It works fine now, but that was a little annoying. Plus it makes me wonder what else wasn't installed that should have been.

Overall, it was a pretty good upgrade experience though.

---

### Post by mudman00 on 2009-07-24
Not a happy camper here......I am not a computer programmer. I do not know how to write software......I do not work professionally with computers. I switched from that viral code produced by M#@^S%#t because I love the Idea of Linux.....I believe in the basic philosophy, in other words.

I upgraded from 8.10 to 9.04 and have had issues ever since. I am currently running a live 8.10 CD to type this note.

I am displeased with the upgrade. I should have known better. I will be wiping the hard drive clean and reinstalling 8.10.....it appears that Jaunty was released with more than just a few bugs.

This does not do the Linux community any good what so ever. I don't care how fast it boots up or shuts down. I came to Linux looking for stability and I didn't want to do bidness with the evil empire from Washington State anymore. To say the least, this is disappointing.

I suspect that with considerable help, and time, I will be able to massage the system to get Jaunty to work.....but that is not good. Like I said....I am not a programmer. I do not know code.

Just my buck fifty

Craig Clark
Houston, Texas

---

### Post by BiggoCharley on 2009-07-24
worked great for the first few weeks, in fact the best experience I have had with Ubuntu since I started with it (5.1)-- but all of a sudden I can't bring up a terminal and the top bar on the app screens where we have the min-max-close icons (-, square max icon and x close icon) have disappeared from all my apps.  Could this be a gnome issue or an invidia issue?  When I try to bring up a terminal all i get is a rectangular white patch where the terminal should be on the screen. The programs seem to function properly otherwise,thankfully.  Except for not being table to bring up a terminal and this cosmetic issue everything else seems ok.

---

### Post by Blu Fox on 2009-07-24
> **ranch hand said:**
> If you would be so kind, I would love to know what wacom model you have and if all features are supported.  I do not and never have had one of them but I want to.

It's an old wacom graphire4 tablet. It's been roughed up over the years and still works perfectly fine, albeit it's small but it was cheap so I can't complain.

---

### Post by Tanker Bob on 2009-07-25
> **BiggoCharley said:**
> worked great for the first few weeks, in fact the best experience I have had with Ubuntu since I started with it (5.1)-- but all of a sudden I can't bring up a terminal and the top bar on the app screens where we have the min-max-close icons (-, square max icon and x close icon) have disappeared from all my apps.  Could this be a gnome issue or an invidia issue?  When I try to bring up a terminal all i get is a rectangular white patch where the terminal should be on the screen. The programs seem to function properly otherwise,thankfully.  Except for not being table to bring up a terminal and this cosmetic issue everything else seems ok.

Definitely a display issue. Unless your driver updated just before the occurrence, it's probably not the NVidia driver. Sounds like your desktop lost track of your window manager. If you're using gnome desktop without compiz-fusion, your window manager should be metacity. If you're using compiz (or enhanced effects), then you can use either metacity, emerald, or another manager for compiz. Restarting your xserver should restore the default. This used to be ctrl-alt-backspace, but that's been disabled by default in Jaunty. Best bet is to restart the computer. If you've done that already and it didn't work, then re-select your window manager from the login screen.

---

### Post by BiggoCharley on 2009-07-25
> **Tanker Bob said:**
> Definitely a display issue. Unless your driver updated just before the occurrence, it's probably not the NVidia driver. Sounds like your desktop lost track of your window manager. If you're using gnome desktop without compiz-fusion, your window manager should be metacity. If you're using compiz (or enhanced effects), then you can use either metacity, emerald, or another manager for compiz. Restarting your xserver should restore the default. This used to be ctrl-alt-backspace, but that's been disabled by default in Jaunty. Best bet is to restart the computer. If you've done that already and it didn't work, then re-select your window manager from the login screen.

I really appreciate your help on this.  
I had tried restarting -still had same problem
I tried again and was given the following options on the log-in screen:
"Last Session
1. Run xclient script
2. GNOME
3. Secure Remote Connection
Failsafe GNOME
Failsafe Terminal"

I tried #1,, 2. Failsafe GNOME, Failsafe Terminal --tried to restart the xserver from the terminal but couldn't find the right command so I scrapped this approach.  Back to square one.

---

### Post by Tanker Bob on 2009-07-25
> **BiggoCharley said:**
> I really appreciate your help on this.  
I had tried restarting -still had same problem
I tried again and was given the following options on the log-in screen:
"Last Session
1. Run xclient script
2. GNOME
3. Secure Remote Connection
Failsafe GNOME
Failsafe Terminal"

I tried #1,, 2. Failsafe GNOME, Failsafe Terminal --tried to restart the xserver from the terminal but couldn't find the right command so I scrapped this approach.  Back to square one.

What video card do you have? Are you using compiz-fusion or Visual Effects?

---

### Post by BiggoCharley on 2009-07-25
> **Tanker Bob said:**
> What video card do you have? Are you using compiz-fusion or Visual Effects?

If the graphics processor and video card are the same I have NVIDIA GeForce4 MX440 with AGPBX.
As to Compiz-fusion vs Visual effects you've lost me (which is easy to do)
I will say that what ever the 9.04 install CD has is what I've got - I have made no changes to the default installation.

---

### Post by Tanker Bob on 2009-07-25
> **BiggoCharley said:**
> If the graphics processor and video card are the same I have NVIDIA GeForce4 MX440 with AGPBX.
As to Compiz-fusion vs Visual effects you've lost me (which is easy to do)
I will say that what ever the 9.04 install CD has is what I've got - I have made no changes to the default installation.

That's a legacy GPU that probably won't run compiz or visual effects well. But it sounds like you're using the open source 'nv' driver installed by default. Please go to the /etc/X11/ folder, open xorg.conf with the text editor (just double-click it), then cut-and-paste the contents here.

---

### Post by BiggoCharley on 2009-07-25
> **Tanker Bob said:**
> That's a legacy GPU that probably won't run compiz or visual effects well. But it sounds like you're using the open source 'nv' driver installed by default. Please go to the /etc/X11/ folder, open xorg.conf with the text editor (just double-click it), then cut-and-paste the contents here.

Here are the contents of xorg.conf;

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Sat Jan 24 20:04:42 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by Tanker Bob on 2009-07-25
That indicates that you are running the proprietary NVidia driver. Interesting. The legacy cards are supported by the legacy driver. We need to make sure that the proper driver has loaded. 

This issue diverges from the purpose of this particular forum. Please start a new thread under the Multimedia & Video forum, post the same results from xorg.conf there, and send me a private message when you do. I'll join you there and try to help. Others helping with video issues will also be there to help. Thanks for your patience.

---

### Post by aikiwolfie on 2009-07-25
Or maybe a moderator could just do a thread split and pleople can get on with helping this guy? Sounds like a plan.

---

### Post by aj_the_first on 2009-07-26
Everything worked except ATI had abandoned support for my "legacy" card X1200.  admittedly 2 years old, but that is still relatively young.
So, I used the open source driver, which produced intolerable screen flickering (fixed it) and no 3D...  couldn't put up with not being able to play any games at all, so I backdated to Hardy Heron...
HUGE mistake.  Now with Hardy, It won't recognize my wireless card, Cheese won't install properly, Skype crashes the computer, my webcam doesn't work anyway, I can't get any fix to actually work because it seems that there is no longer any support for this LTS...
Anyway...  at least I have 3D accelleration right?  Grrr
I may end up switching to a different distro like Fedora or OpenSUSE...  but I LOVED Jaunty, nearly everything worked right out of the box and everything installed properly, and I could fix my problems, and it was... it was wonderful...  if it wasn't for that damn video driver.
Who is developing that thing anyway?

---

### Post by coredeal on 2009-07-27
Hi everyone,

One day a friend talked very highly of Ubuntu. So I ordered the disk but I left it in a drawer for two months because I was afraid it was going to mess with my Windows XP. Then, one day I looked at the disk and I decided I was ready to try. Boy, was that an experience. Here's what I found.
Printer : Epson C-60, recognized with no problem.
Scanner : Canon, recognized with no problem.
DVD burner : Asus and TDK, recognized with no problem.
IDE and SATA HDs (Ihave two) : recognized with no problem.
Mouse : Kensington Ball, not recognized (it needs its own software to adjust settings, but it still works fine with Ubuntu and settings under Preferences, Mouse).
Sound card and speakers : recognized with no problem.
ATI graphic card : recognized with no problem. No need to get a new driver.
Firefox and its add-ons : excellent version 3 for Ubuntu, got all my add-ons back
Access to my Yahoo e-mail account : no problem.
Pdf files : no problem.
Movies and power point presentations : no problem.
What created (somehow) a problem : downloading and installing software. It's very different from Windows as there are no executable files but two good Managers (Synaptic and Add-Remove under Applications) do the whole work automatically. You only have to ask. Getting familiar with tar.gz and repositories took some work, but there are plenty tutorials, and above all good people, in this Forum, available to guide you. Two more worries : defragmentation and system restore. The former I discovered is not needed with Ubuntu (oh, joy) and the latter can easily be achieved by following an excellent tutorial from Heliode called Howto backup and restore your system. It worked fine, with no problem for me. In 10 minutes I had burned my restore DVD, just in case I screwed up the system. Another (little) concern : files and directories. They are organized differently from Windows and you need to practice in order to become familiarized. A little practice to become better acquainted with Workspaces is also suggested. A final concern : the command line, aka the syntaxis, required to perform certain operations at the Terminal. It was less burdensome for me as my background dates back from DOS, but for those who do not know DOS I suggest that they follow the codes graciously provided by the community. After all the good points listed above, this is not a big price to pay. At this stage I had a fully operational Ubuntu-based computer.
What did I like in fact ? A lot, ladies and gentlemen : boot and shutdown speed (there is no comparison with Windows) ; operations speed ; elegance of graphics ; overall desktop presentation ; no freezes or reluctant applications ; beauty and variety of desktop backgrounds ; incredibly beautiful screensavers ; virus scanning built in the OS, no money asked ; amazing variety of free software ; automatic notification of updates ; live disk sent to you just upon request, totally free of charge. AND, a fantastic community spirit, feeling to be part of a free community as opposed to the Windows environment where no such community exists and almost every update comes with a dollar price. Going back to Windows after dwelling with Ubuntu gives you the impression of going backwards several years to an obsolete, awkward OS. I strongly encourage all newbies to give a try to Ubuntu : it will change the way they are doing computing adding a real pleasure. Be patient if everything does not work fine immediately (I don't see why, I have a 5-year old PC, even if it is a 3 GHz machine with 3 GB RAM) 
I'm sure I'm forgetting further positive aspects. The above just quickly came to my mind.
Open source : that's the future. Microsoft move on, your days are counted.

---

### Post by badman35 on 2009-07-29
Well it is horrible i upgraded my ubuntu 8.10  and i could not load it after it was done tryed everything i knew to get it to boot up and load but it would not i lost almost 3 years worth of data and files (this same machine was upgraded from ubuntu 8.04). So with all my files gone i reinstalled 8.10 and tried to get it back where my previously 8.10 was at before the upgrad but i'm still not there...so for this machine i guess i will have no other upgrade path so when 9.10 comes out i will have to ether start over or just do with out.. that's the bad news the good news is that i have 3 other systems  that have 8.04 on them and waiting for the next lts version to upgrade them... this is the first upgrade that has went bad all the other times the i upgraded it all went fine don't know what the ubuntu team has done to the upgrade side all i know is it did not work for me this time....

---

### Post by ranch hand on 2009-07-29
> **badman35 said:**
> Well it is horrible i upgraded my ubuntu 8.10  and i could not load it after it was done tryed everything i knew to get it to boot up and load but it would not i lost almost 3 years worth of data and files (this same machine was upgraded from ubuntu 8.04). So with all my files gone i reinstalled 8.10 and tried to get it back where my previously 8.10 was at before the upgrad but i'm still not there...so for this machine i guess i will have no other upgrade path so when 9.10 comes out i will have to ether start over or just do with out.. that's the bad news the good news is that i have 3 other systems  that have 8.04 on them and waiting for the next lts version to upgrade them... this is the first upgrade that has went bad all the other times the i upgraded it all went fine don't know what the ubuntu team has done to the upgrade side all i know is it did not work for me this time....
A backup of your "home" folder is your friend.

---

### Post by jenkinbr on 2009-07-29
> **ranch hand said:**
> A backup of your "home" folder is your friend.
+1 and a seperate /home partition :)

---

### Post by ranch hand on 2009-07-29
Yes

---

### Post by Blu Fox on 2009-07-31
> **jenkinbr said:**
> +1 and a seperate /home partition :)

Just tried making my own home partition and I ended up screwing up the priorities and couldn't log in. Ended up reinstalling in the end >.>. Thankfully my data wasn't lost, but I still wanna go at making a home partition again..cept with some extensive help to make sure I get it right this time

(complete ubuntu dumbass/noob) 

As for reinstall, painless as always

---

### Post by ranch hand on 2009-07-31
> **Blu Fox said:**
> Just tried making my own home partition and I ended up screwing up the priorities and couldn't log in. Ended up reinstalling in the end >.>. Thankfully my data wasn't lost, but I still wanna go at making a home partition again..cept with some extensive help to make sure I get it right this time

(complete ubuntu dumbass/noob) 

As for reinstall, painless as always
It would have been easy to do when you reinstalled.

When you come to the partitioning you just select manual and then you can set up your partitions right there.

---

### Post by Blu Fox on 2009-07-31
I didn't did it that way, I used this [website's instructions]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by ranch hand on 2009-07-31
> **Blu Fox said:**
> I didn't did it that way, I used this [website's instructions]("http://www.psychocats.net/ubuntu/separatehome")
WOW, I just glanced at the site and it gave me a headache.

It would be easier to install another time on the same drive (dual boot - Ubuntu/Ubuntu) and transfer your files with nautilus.

I do normally make my partitions before I install and then all I need to do is select manual and tell it which partitions to use and what for.  All ready formatted to the FS I want there is no need for the installer to format.

If it is your primary production OS, I would go with around 15Gb for / (root) and make the /home partition as big as you want.  Most of the OS' that I have I am just playing with and I go with 10Gb for / and 20 for /home.

We do have an OLD box running 8.10 on a 10Gb HDD /=4Gb and /home=5Gb and 1 for swap.  Have quite a bit of music on it (for its size) and it runs fine.  My son has run his box for years on 40Gb HDDs and runs the OS on the whole drive (12/38 - I think).

---

### Post by Blu Fox on 2009-07-31
If it's any consolation, I do have like 90gb unallocated space on my hard drive but I wanna keep that in case I want to install more linux distros (tempted to install xubuntu just to try it out)

And glad i'm not the only one who gets confused by those articles

---

### Post by libra1780 on 2009-07-31
I had no problems at all, neither with update from 8.10, nor with complete fresh install. Just had to use the alternative text mode installer 'caus graphics (HD3650) don't work with vesa driver.

I had, and have, still a lot of problems now, after installation. K-menu hangs, device manager hangs, the update tool crashes even firefox and konqueror crash from time to time. don't know if it's a hardware issue, maybe my old piece of a pc-like sh** is counting it's last minutes.. i never had this probs in intrepid.

p.s. at least i don't have any space probs..
root / is 40 gigs  (remember, root has /tmp too, so if you rip a blueray = 16gb on /) and as much as 450GB for /home.. all on PATA.. a miracle :)

---

### Post by COZZIEMAN on 2009-08-01
This is the first Ubuntu distro that I actually managed to get my Brother DCP-120 to work with (except the scanner).  I am a new user of unbuntu, having ditched Widows Vista Ultimate because it continually caused hardware probs with each now update. I am more than satisfied with my choice, but still have to engage with the command line which seems a little daunting at present! The only problem I encountered was that after selecting the 'Hibernate' option from the Close Down menu I could not resume Jaunty. I ended up having to re-install to end the problem. Anyone else have this problem, or have made an error in the install process??

---

### Post by slakkie on 2009-08-02
I just did an upgrade from 8.04 to 9.04. 

I knew that KDE4 was coming but I lost all my panels from 8.10 to 9.04 (which is KDE4 > KDE4). That was a huge turn off. Will really need to dive into KDE docs to see how I can make my desktop keyboard accessible again (had huge amounts of keyboard shortcuts in 3.5.x which are gone now).

I removed all .kde* files to start all over again, also I wanted to see what the default install looks like. Very disappointing to say the least. Kubuntu is really just KDE on top of a minimal Ubuntu machine, and not a fully tweaked theme like in Gnome. Which is a shame really. Haven't looked at Gnome, but knowing the liveCD from Ubuntu it looks way better then KDE. 

Some small changes to wpa_supplicant broke my wireless connection, but that was easily fixed. On 8.04 there is a -w flag which is not used (or got changed to -W, not sure) in 8.10 and up. Not really a Jaunty thing, but had to be fixed none the less during my Sunday upgrade day.

Disk space usage on Jaunty is huge, compared to 8.10 (at least 2 Gb more). I must admit, I have Gnome/Xcfe and KDE DE's installed, so that will consume some space. 

Too bad the bootchart didn't leave a valid .png file behind, but otherwise I could have shown the difference between 8.04, 8.10 and 9.04.

I will test Jaunty for a couple of days, see if KDE fits my needs (or if I can adjust to the new KDE), otherwise I will go back to 8.04 (made a backup, so should be an easy recovery). 
Maybe tweak KDE4 inside a VM so my next upgrade will be less painful ;)

-edit-
[s]The biggest issue so far is sound, it is really low on 100% and I am unable to start kmix..[/s]

---

### Post by slakkie on 2009-08-02
> **Blu Fox said:**
> If it's any consolation, I do have like 90gb unallocated space on my hard drive but I wanna keep that in case I want to install more linux distros (tempted to install xubuntu just to try it out)

And glad i'm not the only one who gets confused by those articles

aptitude install xubuntu-desktop

aptitude search tu-desktop to see which official Ubuntu desktop flavors you can use. 

See this page [http://xwinman.org/](http://xwinman.org/) for many other windowmanagers you can use on Linux.

---

### Post by ranch hand on 2009-08-02
> **Blu Fox said:**
> If it's any consolation, I do have like 90gb unallocated space on my hard drive but I wanna keep that in case I want to install more linux distros (tempted to install xubuntu just to try it out)

And glad i'm not the only one who gets confused by those articles
90Gb is plenty to have 3 more distros installed on 2 partitions apiece - /=10Gb and /home=20Gb.  Plenty of room for a good test.

---

### Post by dr_voodoo on 2009-08-04
well, this is my first crack at running a linux distro on my aging P4 3.06ghz Dell... I decided to go for Kubuntu as I prefer the look of KDE. 
I'd love to say it was flawless, but somewhere along the line Ububntu's installer decided to format not only the clean drive I had set aside for it, but also reformat the other hard drive in my PC containing my XP partition and my data partition. To say I am pissed off is an inderstatement. I don't know how this could have happened - there is no way I would have selected an option like that, and I double-checked every dialogue box before I clicked on to the next one. I have lost a lot of valuable work. To say I am angry is an understatement. Apart from that I quite like the overall look/feel.

---

### Post by Arvie on 2009-08-05
My ageing Dell Latitude X300 with Windows XP was becoming extremely slow, even after doing the usual clean-up and defragmentation stuff. Just starting the explorer took forever. I already have EEEBuntu 3.0 standard on my Asus EeePC, so the choice to replace Windows XP with Ubuntu 9.04 was an easy one. Burned the ISO on CD, ran it live to check whether the important stuff like WiFi worked and then installed. Painless execise (and yes, there is a warning that Windows XP and everything else will be wiped). Up and running in no time. Speed improvement is beyond belief. Thanks for a great distro and already looking forward to Karmic Koala!
Arvie

---

### Post by Ameneon on 2009-08-05
Been using ubuntu since 7.10 (so not that long), usually been adopting fairly quickly after release but this time took awhile longer. Anyway, started update process and went out to grab a snack, came back to an error message related to an old package freeciv-lib which couldn't be replaced. Ok, clicked it away and saw that rather than being done, the process had paused at that point.

Let the process run through, at one point another message about the same package came up but that was about it. At the end of the install process however I was expecting a cleanup process and reboot as the original update progress descriptor indicated however if such a thing took place I never saw it at least. Rather, an error message indicating that the update could not be completed and had been aborted, and that my system could be in an unstable state :o

So I checked system properties and see that it states 9.04 and while the changes appear to be minor on the visual plane, a new logon screen also shows that the update's done.

So, a smooth upgrade in and of itself but with a couple of unexpected quirks, nothing major however.

This on a homebuilt desktop with Asus P4 (IIRC) mb, AMD Athlon 6000+ x2 cpu, 2x1gb corsair "value" memory, nVidia 9800gtx and otherwise unspectacular setup with dual boot into windows xp pro (altho it is months between each time I log in there).

---

### Post by hiflyer on 2009-08-05
I have 2 very different experiences. I updated my dell D810 laptop from 8.10 to 9.04 no problems. No lockups. Works great.

I updated my HP system on amd 64. easy update. Freezes regularly (max operating time ~ 8 hours less before a hard lockup). So I am really hoping someone finds a fix to the AMD 64 problem.

---

### Post by BlueVark on 2009-08-05
Mixed reviews here also. 
Installed great on a Dell Latitude laptop that I use mostly as a client.  
Installed fine as dual boot with XP on a Dell 
Dimension Desktop, but I still have yet to get the Internet Connection Sharing to work.  I have tried about a dozen different set ups from a dozen different recommendations (including the "official" ICS Wiki)and still no luck.  It shouldn't be this hard.  I hate to think about how many hours I have (wasted) spent learning about Linux this week.

---

### Post by Dr. Moreau on 2009-08-05
I installed 9.04 Desktop i386 as a dual-boot on a separate freshly-installed recycled hard drive.  There were lots of minor disasters, but none that I can blame on the software.  I'm a noob to Linux, so I was expecting trouble, and I actually enjoyed doing the work as a learning experience.   No fatalities, the machine runs great now, four hours well spent says I.

---

### Post by Spiritof76 on 2009-08-08
I installed Jaunty into my new computer. A homebuilt system based on the in expensive D945GCLF Motherboard/processor.

  I tried to create a bootable flashdrive from the CD / but it wouldn't boot from my system. I didn't waste any time trying to work it out, and installed a CD/DVD player. booted the live CD and boot went just fine.

The installation went pretty quickly, I selected the defaults for everything. All went pretty uneventful. 

I installed Adobe flash and PDF reader , got my HP network al in one working without any hassle.  (its actually a lot easier than  in Windows) 

Took me a few minutes to get the cube thingy going with compiz but google is my friend. To my surprise I found out that [dropbox ]("https://www.getdropbox.com/referrals/NTc0ODE0NTk")has an ubuntu port.  Which allows me to move files between my different computers.

I then installed these codex things and I was able to watch movies and such. I  got afraid that I might need to run some Windows applications and breaking away from Bill Gates chains could be too much!  I installed virtual box with Windows XP. Funny how XP takes a lot more time and is more involved than Ubuntu.  The XP install went smoothly, but perhaps time has proven that its been unnecessary, I haven't found much need for XP yet.

I now have a pretty powerful and fast system based on modest hardware, I do not find myself wanting for Windows. I don't believe I have a system as good *** Windows, but a System thatwprks a lot better than Windows ever did.

I do have 2 mino critisisms on the wasy Ubuntu works, and that is the application upgrade process.  We are stuck behind in the latest versions of both Open office and Firefox. Openoffice and Firefox are not part of the operating system and it would be nice if the Synaptic Package manager could just upgrade us to the newer versions when we are ready instead of making us wait until October and having to upgrade the whole OS to get these upgrades.

All in all Ubuntu is great and I don't find myself looking back at all.

---

### Post by phuchungbhutia on 2009-08-08
I have two drives one is sata and another pata and . . I have win xp in sata and i installed ubuntu in the other today . . But i couldnt see ubuntu detect sata drive and there is no bootloader . . Plus it takes time to start up the ubuntu os . . Now i have to change boot drive priority everytime i need to change the os i want to use . .

---

### Post by hgraham on 2009-08-08
I got my first computer in 1988.  Prior to that I submitted cards to a Univac.  It was all unix then.  I was happy to go with Microsoft when they made the PC accessable with their programs (purcased or purloined as they were).  But in recent decades Microsoft has changed. How can they charge the money they do?  I live in China and for the average Chinese it is impossible to be leagal. Enough nostalga. A year or so ago, I tried many of the Unix based programs and settled on Ubuntu.  It was still too frustrating to me and I gave up.  These last few weeks I tried again and succeded.  I have now completed a complete switch-over from XP.  I only use XP now for games and that may change too.  I regret running out of problems to solve.  It has been a ball.
My current experience with Ubuntu has been nothing but pleasure although frustrating at times.  It reminded me of my old DOS 3 manual and trying to figure it out.  Ok the nostalga came in again.  My point is that when you spend a little time trying to figure out how things work, the system seems to be more your own.  It is a good feeling.  The community here is wonderful.  You all make me feel as if I belong to something.  And the bonus is that you get a first class, fast, reliable, free operating system that is better than anything you have to pay for.  I just want to say thanks to everyone involved.  I am happy there is a forum where I can say it.

Thanks to everyone 

Howard in China

---

### Post by Tanker Bob on 2009-08-08
Welcome aboard, Howard!

---

### Post by ZizzerZuz on 2009-08-08
Unknown 2.8ghz PC, upgrade was flawless.  It just works.  
 
IBM xSerries 220 dual P3 1.2's had some problems with a PCI SCSI card.  Yanked the card and it works wonderfully.  Now, to get that card to work.
 
Anyone ever get a touch screen to work with Ubuntu?

---

### Post by Hygaphunkik on 2009-08-09
I installed the UNR on an elonex webbook probably about 3 months ago. I dual booted because I needed to keep some windows stuff on for work and did not want to let go. About a month and a half ago my frustration got the better of me and I shabbed XP off did a clean install and have not touched windows since.

There were a couple of niggling problems that I had to sort out to get everything running well and I still have not figured out how to get JACK working but that is a minor worry that I do not really need, a sort of ongoing future project.

I was thinking of writing a small guide for installing UNR on the webbook but was not sure where to put it.

---

### Post by Assim on 2009-08-11
I installed Ubuntu myself and I should say it's so easy to install. Even my 11 year old sister was able to install it all by herself. :lolflag:

Ubuntu is simply the best. :KS

---

### Post by mikcarroll on 2009-08-13
Hello,
 I've been around puters my whole life, my best friend works frontend at Yahoo and has been nagging at me to try Linux again for about fifteen years. I installed a distro in the mid 90's and it was a frickin train wreck so I went back to winblows, that is until last week, I saw a video on Beryl on youtube thought it was cool (the fire got me) and said to myself, self, I've got to check that out!!
 I've always heard the Linux doesn't like some hardware so was a little hesitant, I decided on Ubuntu because My best friend suggested it for overall useage or Gentoo if running a server.
 I've got three computers, two desktops and one laptop, so I decided to turn the laptop into a dual boot after running Ubuntu off of the disk for a while(excellent option to try it out).
 I figured out the hard way that Beryl was now Compiz and it turned my screen black, I struggled with trying to fix it for about two hours by looking up the problem, finally I just said the hell with it and did a fresh install and got rid of windows.
 Now my 1st destop is in dual boot config and testing, once I figure out the bugs on the laptop I will eventually switch over all of them.
Ubuntu was easy to install, the only problems I have noticed are you have to reconfigure the sound settings and the built in webcam does not work on a Dv2000 Hp laptop.

---

### Post by von Stalhein on 2009-08-13
^^
Welcome to the addiction mate!!!
After you get past the realisation that it's terminal (no pun intended!!) it's all good :biggrin:

---

### Post by MountainX on 2009-08-13
Never got things to work.
[http://ubuntuforums.org/showthread.php?t=1156237](http://ubuntuforums.org/showthread.php?t=1156237)

---

### Post by proyectomx on 2009-08-21
Installed once it got released, and today working nicely ....

One issue I had with nvidia video card. The Nvidia website drivers did not work right, but the repositories drivers worked flawlessly.

One issue with Intel GMA950 graphic card. It worked without any correction once the system got updated.

I recently purchased a laptop with intel video card... it came with windows vista, and I didn't want to make changes to the partitions... but once I put ubuntu on it.... maaaannn I had never booted vista!! 

It boots so fast everybody keeps asking me.... is it done booting already??

Have always recommended ubuntu to people who know me... and Jaunty is no exception.

---

### Post by aljoriz on 2009-08-25
I was using pirated Windows7 when a friend of mine introduced me to ubuntu.  Initially I was aghast at migrating.  Tried the live and my webcam didn't work (a4tech) for skype.  It took me days of reading and scourging the net on how to make it work.  

Now it is working,  ubuntu + google = the best help guide any user can have.

---

### Post by aljoriz on 2009-08-25
I was using pirated Windows7 when a friend of mine introduced me to ubuntu.  Initially I was aghast at migrating.  Tried the live and my webcam didn't work (a4tech) for skype.  It took me days of reading and scourging the net on how to make it work.  

Now it is working,  ubuntu + google = the best help guide any user can have.:P

---

### Post by von Stalhein on 2009-08-26
Double dipping, I've done this on my home desktop before....

I'm pumped.

I use a laptop (Lenovo R61) for secretarial purposes for a sporting club I'm involved with, and I thought I would install Jaunty in a dual boot mode for security and as an educational opportunity for teh n00bs.

And due to the fact that that's where I'm most comfortable and usually "live" anyway.

Ubuntu FTW :-) Flawless so far and it took less time to sort a wireless connection than the hassles I had sorting Vista.

I'm doing a bit of Synaptic updating atm, hopefully no issues will arise.

I'm still pumped. Can't believe how simple it was, and how much quicker it's been so far.

---

### Post by wurx on 2009-08-29
Wicked! I've installed it through Wubi. Like the grub menu more though. Also have to add that I've plugged my cellphone in and went through the setup which popped up. No more struggling with wvdial or bash commands to get onto the net. Just BAM and you are on the net.

Thanks Guys!!!

---

### Post by arashispencer on 2009-09-12
Upgraded by clicking on the update reminder...Connection slow but working...1 error so far while downloading but since it allows me to press 'next', I continued...after done, restart was prompted by the comp and I did... But....
Unable to login anymore...

-Boot args (cat /proc/cmdline)
blah, blah
blah,blah
-missing modules (cat /proc/modules;1s/dev)
ALERT! /dev/disk/by-uuid/...... does not exist. Dropping to a shell.

Result=failed

---

### Post by community nerd on 2009-09-13
I love Ubuntu 9.04! It is the best ubuntu edition as far as i am concerned. I have tried many versions but 9.04 is great. I did have a wireless problem but i fixed it quite easily.

---

### Post by jeannacav on 2009-09-17
At first I thought I would make a BRAVO GREAT JOB thread, then I came here and saw this thread.
I think the worst of it was the speed of my dsl connection. On labor day (hoping for less traffic at the university mirror) I downloaded the iso in 6 hours.

I must say flawless.

Anything confusing already had a tutorial and people jumped right in to help with the little questions I had.

I have even been able to view some websites that have non flash videos with ease. wow.

This has been a great experience.

Oh yeah, with the exception of some photoshop psd or files bundled as photoshop EVERY file I made on my mac has a reader that jumped right in and read the file. So, I used a flash drive and moved over my most important (enormous) folder.

I put a beautiful picture on my desktop and now, I have a customized slick running computer.
Wow.

Thank you everybody who worked on this. You did a wonderful job!

jeanna

---

### Post by thenoobguru on 2009-09-17
Did it worked flawlessly ? Best Install EVAR
Did you got problems ? sorta, i think its my computer thou, whenever i'm at the end of a page and scroll with arrow keys, i get a screech from my headphones
Did you manage to solve them ? no, but i haven't tried :P
if yes how ? N/A

---

### Post by techfanboy81 on 2009-09-18
So far I have installed it nice and easy, but still needs to explore more.

---

### Post by rwatkins on 2009-09-23
Once burned...
The upgrade manager indicated that JJ was the available upgrade.  I upgraded and am now treated to a boot that ends with
"IO APIC Resources coult not be allocated
 Gave up waiting for root device, Common problems...
 ...
 ALERT! /dev/disk/by-uuid/373faafa-29e8-4ee3-89a0-0df3a09870f1 does not exist.
 Dropping to a shell!
 Busy Box v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
 Enter 'help' for a list of built-in commands"

The upgrade appears to have rewritten /proc/cmdline to
"root=UUID=373faafa-29e8-4ee3-89a0-0df3a09870f1 ro quiet splash"
which refers to a nonexistent device.

My first attempt to fix was to go back and install HH from CD but that failed miserably and I again landed at the ash command prompt.

Looking at the forums, I understand that I may have needed to make some intermediate upgrades prior to this maybe?

This looks like it will be a long week...

---

### Post by aikiwolfie on 2009-09-23
Have you tried a clean install of Jaunty?

---

### Post by arashispencer on 2009-09-23
rwatkins, i was having the same problem and since i m very new to linux,i used an approach we used to treat windows...reformat...itz disappointin actualy....

---

### Post by dcclabough on 2009-10-03
In previous releases, I have had to use the alternate disk in order to successfully install on my m2n4sli nforce 4 mb with x64 amd dual... with jaunty, however, the opposite was true.  I dl'd the alternate x64amd disk and had the freeze at 70 something % no disk mounted error (ide dvd-rw with sata hdd).  I then dl'd the live cd (also x64amd) and booted up and installed like a charm.  there were some minor fixes here and there, but i must say that ubuntu has come a long way from my first install of dapper... nvidia xserver was an easily selected driver in the system menu, my wusb54gc wireless card (necessary for connection even on my desktop - router under kitchen table by necessity) worked out of box [this was huge], and no messing with imwheel... my mouse just worked.  oh yeah, and i didn't have to manually turn off the apic and lapic controls for the live cd to even boot... great work everyone, and thanks... now if i can find a way to run civ4 (and tesV when it comes out) without having to dual boot.

---

### Post by Habboblob on 2009-10-04
Seemed flawless to install for me when installing to a internal hdd.

And update manager works very well also.

---

### Post by Nude_Lewd_Man on 2009-10-05
Complete n00b when talking about Linux (other than 5 minutes d1cking about with a friends' install....about 8 years ago) and I've installed three times.

First was the (9.04) server version, which while I got it installed and started, it was a PITA as it was 100% CLI. Wiped that and went for the desktop version instead. I'll refer to that as UNIX1.

That install went fine, seem to have got (almost) everything sorted that needed anything doing to it (which wasn't too much) and was happy - even started Folding on it...

I then remembered/realised that the only reason another box (I'll call it UNIX2) wasn't working was as I'd swapped the HDD over to use in one of my M$ boxes. It still had a 20 GB drive, so I went for it.....

Not so impressed with this install. Tried installing a few things, some work some don't... Video drivers seem to be stuck with the originals (this is a rebuilt Compaq rig, and the only things I know about it is 1GB of RAM and an AMD chip) and it is using an on-board GPU...

Can't get Skype to work on UNIX2, can't get the graphics drivers updated (or found out what they are), can't play Monopoly [[http://www.monopolycitystreets.com](http://www.monopolycitystreets.com)] and a few other things that I can't remember at the moment too.......

---

### Post by ch11cva on 2009-10-12
No problem in upgrading.it's simple.

---

### Post by dyess002 on 2009-10-12
Jaunty worked great on my dv8000 laptop no problems, But the pavilion DV7 everything worked but the headphone, the sound will not come out through the headphones and I hate that, but that was all the problem I had with that. And on the Mini HP I also put the Netbook remix on it and the sound will not work period and I hate the layout of the netbook remix just hate it, I wonder if a regular Ubuntu would work on the HP Mini?

---

### Post by igor1102828 on 2009-10-13
[COLOR="Red"]Upgraded from Ubuntu 8.10 to Jaunty via Synaptic automatic upgrade. Got several problems:[/COLOR]
1)[COLOR="Blue"] **Cannot even login**[/COLOR]: [COLOR="Red"]the system started to generate "5" [/COLOR]in the login window every couple of seconds, so, I am not able to write the password within these 2 seconds between two generated "5"-s, the result is "Wrong password". I had the same problem when I upgraded from Ubuntu 6 to Ubuntu 7; then there has appeared Ubuntu 8, which was free from this problem and I worked with it. 
How to cure this problem? I've written just in case in the /boot/grub/menu.lst 

[COLOR="DarkSlateBlue"]## ## End Default Options (I've inserted "root (hd1,0)" in 2nd line ##
title           Ubuntu 8.15, kernel 2.6.28-15-generic
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash
initrd          /boot/initrd.img-2.6.28-15-generic
savedefault
quiet
[/COLOR]
[COLOR="DarkSlateBlue"]title           Ubuntu 8.14, kernel 2.6.27-14-generic
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash
initrd          /boot/initrd.img-2.6.27-14-generic
savedefault
quiet[/COLOR]

and was forced to choose booting from second line
 ([COLOR="Orange"]**Ubuntu 8.14, kernel 2.6.27-14-generic**[/COLOR]). 
Then I see next problem

2)**[COLOR="Blue"]HPLIP Status Service fails - no system tray detected[/COLOR]**

3)Tryied to open via Mizilla Firefox some files in  [http://localhost/Forlder](http://localhost/Forlder) and got the content of the Folder, but cannot open  a file in the Folder, **[COLOR="Blue"]Apache is hanging..[/COLOR]**

Any suggestions?

---

### Post by jaycee23 on 2009-10-13
I have only recently seen the light and tried Ubuntu.

I installed Jaunty Jackalope with a great deal of trepidation but actually the whole thing was simple, smooth and quick as compared to Windoze!

Since I have had a couple of minor issues - easily sorted by reading the relevant posts.

Looking forward to 9.10 - with which I think I will do a clean install.

Overall everything works and it's been an absolute pleasure, even more so due to all the people on the forums willing to help and point you in the right direction.

20yrs ago when I was at school I wanted to be a computer programmer - long before most people knew what a computer was - ended up being a doctor! At last might get my chance to work under the hood of an OS!!
[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

### Post by Pelsia on 2009-10-14
Did a clean install on my laptop.  Spent a lot of time researching and making sure that all my devices had drivers, or could be configured once running Ubuntu.  Installation was the easiest I've ever gone through and fast.  Installing Photoshop on Windows takes longer than it did to complete the whole install!

Only major snag I ran into was getting my wireless adapter to work; the final solution was a real hack job and shouldn't have worked.  It's working fine now so won't go try and fix something that isn't broken.

Other item that is still bothering me is desktop space.  Though the resolution is set to the same as it was when I was using Windows, it just feels like I have less room.  Have a feeling that the system font size may be set too large and just needs some adjustment.

---

### Post by running_rabbit07 on 2009-10-14
> **Pelsia said:**
> Other item that is still bothering me is desktop space.  Though the resolution is set to the same as it was when I was using Windows, it just feels like I have less room.  Have a feeling that the system font size may be set too large and just needs some adjustment.

I get that feeling about the desktop icons, too. They seem much bigger than the ones in Windows.

---

### Post by Endolith on 2009-10-29
Are you going to make one of these polls for Karmic?

---

### Post by emigrant on 2009-10-29
@ [Endolith]("http://ubuntuforums.org/member.php?u=235198") why don't you open a poll ;)

---

### Post by Endolith on 2009-10-29
frodon usually does it.

[http://ubuntuforums.org/showthread.php?t=580852](http://ubuntuforums.org/showthread.php?t=580852)
[http://ubuntuforums.org/showthread.php?t=764847](http://ubuntuforums.org/showthread.php?t=764847)
[http://ubuntuforums.org/showthread.php?t=963853](http://ubuntuforums.org/showthread.php?t=963853)
[http://ubuntuforums.org/showthread.php?t=1133869](http://ubuntuforums.org/showthread.php?t=1133869)

I think the questions should be identical for each one so [we can compare]("http://www.endolith.com/wordpress/2009/06/24/ubuntu-isnt-getting-any-better/").

---

### Post by Dullstar on 2009-10-30
9.10 is out now, so we probably should unsticky this and make a 9.10 one.

---

### Post by M&amp;StL on 2009-10-30
HUH?  

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages)  404 Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I am not a programmer by any stretch. This pops after files appear ready to install. It has proven a total road block.

---

### Post by KiLaHuRtZ on 2009-11-01
By far Karmic is the BEST version/upgrade ever!  On the reverse, I believe Jaunty was the worst version/upgrade.  Jaunty caused more problems and issues for me than anything.  Karmic upgrade required absolutely no action on my part; on three systems, all different, no problems.  Not to mention, all my previous problems are non existent!  I love it!  And I love how they brought back the brown look!  Awesome job on this release Ubuntu Team!  Makes me even that much more excited for Lucid!!!

---

### Post by bmartin on 2009-11-01
> **KiLaHuRtZ said:**
> By far Karmic is the BEST version/upgrade ever!  On the reverse, I believe Jaunty was the worst version/upgrade.
I haven't "upgraded" since Feisty. I keep a separate /home partition and do a fresh install every time. I've got a simple script to create a list of the packages that I installed via Aptitude and use that to restore my packages.

Suspend doesn't work on any more on either of my computers. On my custom-built desktop, the computer shuts off instead; on my wife's desktop, you can't "wake it up". I'll have to get that fixed.

---

### Post by Endolith on 2009-11-01
> **KiLaHuRtZ said:**
> By far Karmic is the BEST version/upgrade ever!

I hope that's true.

>  On the reverse, I believe Jaunty was the worst version/upgrade.  

According to these poll threads, Intrepid was the [worst in a while]("http://www.endolith.com/wordpress/2009/06/24/ubuntu-isnt-getting-any-better/").

---

### Post by gilgalad2007 on 2009-11-04
Clean install, works right off.   All systems work fine.  (Asus EPC1000HEB netbook w/ 160GB HDD and 2GB memory).

---

### Post by solwic on 2009-11-04
> **gilgalad2007 said:**
> Clean install, works right off.   All systems work fine.  (Asus EPC1000HEB netbook w/ 160GB HDD and 2GB memory).

Clean installs usually do work right off.  :)

---

### Post by jenkinbr on 2009-11-04
No new thread?

/me waits...

---

### Post by bgangopadhyay on 2009-11-13
Upgrade from 9.04 was not successful. But fresh install was excellent.

---

### Post by ben44b on 2009-11-22
Tried to upgrade to Koala. System was in a perpetual boot; when I logged in in recovery mode, I had to type startx everytime. Then, whenever I got the screen to full-size on some web pages or Synaptic, total freeze.
I spent a week looking for answers and got none so I-reinstalled 9.04. 

I was looking forward to Koala because of the "benefits" for users with Intel-imbedded chipsets. 

Not impressed.

BG

---

### Post by Thanh-BKK on 2009-11-24
Hi.

Is this still about Jaunty? If so, here goes......

Roughly 35 clean installs, each one cleanly wiping off one Windows-install :twisted: 

This was done on anything from Celeron 600 with 256 MB of RAM and 20 GB hard drive to AMD Athlon 64 x2 5600+ with 2 GB RAM and 500 GB hard drive. ATI, Nvidia and Intel graphics, on-board, AGP and PCI-Express (even one PCI!), on-board and PCI sound and LAN etc etc etc, you name it - i did it. 

EVERY SINGLE ONE WENT WITHOUT A GLITCH.

The worst problems encountered were "no sound" (actually sound was there but i had to find it, it was a Dolby-something sound card and i had to play with the settings to make the sound worm it's way to the right connector) and a boot splash that has too high a resolution which the (15" LCD) monitor can't handle, the actual desktop is fine though. 

I even ran (just yesterday evening and just for a test!) Jaunty from the Live-CD on my boyfriend's laptop and got it online - wireless! In no time as a matter of fact - booted, found network, entered network key and was online. Now if it wasn't for his bluddy games i could install it there..... 

I know Karmic is out but i will stick to Jaunty for fresh installs - because it works and i love it. And i get more people to love it :)

Kind regards.....

Thanh

---

### Post by HeadHunter00 on 2009-11-24
It was flawless until it came to gaming, but that problem was fixable.

---

### Post by olddave1 on 2010-05-03
Nothing to see here

---

### Post by OneMixDJ on 2010-06-24
Hmmm...

I'm still running Ibex on a Thinkpad T22 with 512MB of RAM, so I'm not sure if this machine will fare well if bumped up to Jaunty. 

:popcorn:

---

### Post by philinux on 2010-06-24
Rest in peace old thread.

---

