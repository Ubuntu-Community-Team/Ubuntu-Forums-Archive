---
title: "Alpha 1 Officially Released"
date: 2012-06-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cariboo on 2012-06-07
I just received this email.

> 
"There either is or is not, that’s the way things are." 
- Charles Dickens, Great Expectations


The 12.10 (Quantal Quetzal) Alpha 1 milestone image set "is" 
now released. 

Pre-releases of Quantal Quetzal are *not* encouraged for anyone 
needing a stable system or anyone who is not comfortable running 
into occasional, even frequent breakage.  They are, however, 
recommended for Ubuntu developers and those who want to help in 
testing, reporting, and fixing bugs as we work towards getting 
this release ready.    

Alpha 1 is the first in a series of milestone images that will be
released throughout the Quantal development cycle, in addition to
our daily development images.  The Alpha images are known to be 
reasonably free of showstopper CD build or installer bugs, while 
representing a very recent snapshot of Quantal.  You can download 
them here:

   [http://cdimage.ubuntu.com/releases/quantal/alpha-1/](http://cdimage.ubuntu.com/releases/quantal/alpha-1/)
   (Ubuntu Desktop, Server, ARM)

Additional images are also available at:

   [http://cloud-images.ubuntu.com/releases/quantal/alpha-1/](http://cloud-images.ubuntu.com/releases/quantal/alpha-1/)
   (Ubuntu Server Cloud)
   [http://cdimage.ubuntu.com/kubuntu/releases/quantal/alpha-1/](http://cdimage.ubuntu.com/kubuntu/releases/quantal/alpha-1/)
   (Kubuntu)
   [http://cdimage.ubuntu.com/edubuntu/releases/quantal/alpha-1/](http://cdimage.ubuntu.com/edubuntu/releases/quantal/alpha-1/)
   (Edubuntu)
   [http://cdimage.ubuntu.com/lubuntu/releases/quantal/alpha-1/](http://cdimage.ubuntu.com/lubuntu/releases/quantal/alpha-1/)
   (Lubuntu)

Alpha 1 includes a number of software updates that are ready for wider
testing.  This is quite an early set of images, so you should expect
some bugs.  For a more detailed description of the changes in the Alpha
1 release and the known bugs (which can save you the effort of reporting
a duplicate bug, or help you find proven workarounds), please see:

  [http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/)

If you're interested in following the changes as we further develop
Quantal, we suggest that you subscribe initially to the
ubuntu-devel-announce list. This is a low-traffic list (a few posts a
week) carrying announcements of approved specifications, policy changes,
alpha releases, and other interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)


Kate Stewart, on behalf of the Ubuntu release team


---

### Post by QIII on 2012-06-07
Woo hoo!

Time to get back to this and stop goofing off, I guess...

---

### Post by MG&amp;TL on 2012-06-07
Yay! Especially nice to see firefox coming along.

---

### Post by unibroker on 2012-06-07
I downloaded and made a live DVD of Alpha-1 last night.  I want to upgrade my Precise with Quantal, even at this early stage.  Can I do that from either the DVD or the downloaded iso from which I burned the DVD?

---

### Post by cariboo on 2012-06-07
> **unibroker said:**
> I downloaded and made a live DVD of Alpha-1 last night.  I want to upgrade my Precise with Quantal, even at this early stage.  Can I do that from either the DVD or the downloaded iso from which I burned the DVD?

Depending on your experience level, you can upgrade using your DVD, even though there isn't an option in the install menu. Choose **Something else** from the partitioning menu, and use the partitions, but don't format them.

Be aware that this may render your system unusable, so make sure you have good usable backups before doing anything.

---

### Post by cariboo on 2012-06-07
I just finished an installation, it went remarkably well, aside from a couple of personal mistakes, the install completed with zero problems.

Don't talk on the phone while entering your password, and make sure you set the correct disk order in the bios after you disable booting from USB. :)

---

### Post by unibroker on 2012-06-07
> **cariboo907 said:**
> I just finished an installation, it went remarkably well, aside from a couple of personal mistakes, the install completed with zero problems.

Don't talk on the phone while entering your password, and make sure you set the correct disk order in the bios after you disable booting from USB. :)
Thanks for the response.  I just got to know of Ubuntu in November and decided to dual boot 11.10 I believe (the one before Precise) with my Win XP.  Then I read somewhere that Precise which was in development had a real quick boot time.  I did an update and upgrade from the command line and even though there were some rough edges it got better and better with every Update.  For that reason and even though I'm still learning I want to see what I can do to assist with testing.

BTW, in your first message you mentioned about selecting **Something Else**.  I assume that is under the Install Ubuntu button as Try Ubuntu just takes you to the Desktop.  There is also Install Ubuntu 12.10 icon on the Desktop when you arrive there from Try Ubuntu.  

Thanks again.

---

### Post by cariboo on 2012-06-07
> **unibroker said:**
> Thanks for the response.  I just got to know of Ubuntu in November and decided to dual boot 11.10 I believe (the one before Precise) with my Win XP.  Then I read somewhere that Precise which was in development had a real quick boot time.  I did an update and upgrade from the command line and even though there were some rough edges it got better and better with every Update.  For that reason and even though I'm still learning I want to see what I can do to assist with testing.

BTW, in your first message you mentioned about selecting **Something Else**.  I assume that is under the Install Ubuntu button as Try Ubuntu just takes you to the Desktop.  There is also Install Ubuntu 12.10 icon on the Desktop when you arrive there from Try Ubuntu.  

Thanks again.

Welcome, we can always use more testers. The preferred method of running a development version, is to create an extra partition and install it on that. There have been times when a development version is unusable, so you should always have a stable running version installed, so that you have something to fall back on  if things break, and allow you to chroot your development version partition in order to fix the problem.

For example with the problem I had with the wrong password, booting into recovery mode wouldn't allow me to change the password due to the disk order problem I mentioned. I booted into my stable install of Precise, and chrooted the / partition, and was able to change my password successfully.

If you do decide to run a development version, don't be shy about asking questions if you run into any problems.

---

### Post by jerrylamos on 2012-06-07
2 bugs so far (besides Nautilus crapping out frequently as usual)

1. "Try Ubuntu " fails on this 3.3 GHz ATI Radeon xpress 200 unless at boot menu push F6 and add
nomodeset
to the boot line.  Shades of modeset problems since Intrepid.  No clue why "startup disk" would have to do "modeset" since a "safe boot" would be best.  My opinion.  Did work O.K. on netbook and widescreen notebook.

2. Widescreen notebook can't set external monitor screen resolution, or turn off laptop monitor see bug #1007588.  System Settings, Displays fails on Apply.  Sebastian's working on it and may be making some headway.

As an aside, another partition running Pangolin with Quantal's kernel Display works fine.

Jerry

---

### Post by sammiev on 2012-06-07
Found a few bugs so far as well but all were reported a few times over. So far so good, I see the updates starting to come in. Time to play.

---

### Post by ronacc on 2012-06-07
whatever was blocking me from installing the dailys is still there with alpha-1 .I'm getting the same thing in the installer debug log every time .
```
(ubiquity:3713): Pango-WARNING **: error opening config file '/root/.pangorc': Permission denied

nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
Error opening file for reading: Permission denied
update_release_notes_label()
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.

(ubiquity:3713): Gdk-CRITICAL **: gdk_error_trap_pop_internal: assertion `trap != NULL' failed
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs is disabled since running on read-only media
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

```

---

### Post by sammiev on 2012-06-07
> **ronacc said:**
> whatever was blocking me from installing the dailys is still there with alpha-1 .I'm getting the same thing in the installer debug log every time .
```
(ubiquity:3713): Pango-WARNING **: error opening config file '/root/.pangorc': Permission denied

nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
Error opening file for reading: Permission denied
update_release_notes_label()
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.

(ubiquity:3713): Gdk-CRITICAL **: gdk_error_trap_pop_internal: assertion `trap != NULL' failed
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Home directory /home/ubuntu not ours.
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs is disabled since running on read-only media
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

```

The only way I got going was to use one of these [ISO]("http://iso.qa.ubuntu.com/qatracker/milestones/221/builds").

---

### Post by kevpan815 on 2012-06-07
My install of 12.10 Alpha 1 was a success as well despite my disappointment that it looks like WUBI does not work yet. I was still able to create a Dual Boot with Windows XP by resizing the Windows Partition and then adding a second UBUNTU partition by booting to the 32 Bit Desktop DVD (Oversized CD File) instead of trying to run the Disk inside of Windows XP.

---

### Post by ronacc on 2012-06-08
> **sammiev said:**
> The only way I got going was to use one of these [ISO]("http://iso.qa.ubuntu.com/qatracker/milestones/221/builds").

I tried the alternate but it craps out just after the partitioner starts detecting my drives . there is something about quantal that don't like my hardware , I can install precise ok ( I've done it a couple of times since the problem started just to check ) and I was able to install the very first daily live ok but no joy since then . There seems to be more than one problem , the early daily's were crashing at the same place as the alternate now does but the current lives don't even get that far , they die just after you select if you want to download updates while installing .

---

### Post by jerrylamos on 2012-06-08
?  I may not be looking hard enough, but on my wide screen notebook with both Quantal and Precise (test with Quantal's kernel) I can hardly tell the difference....

Well, there are a couple Quantal  "bugs" like Nautilus crapping out and on Quantal the external screen is stuck on 1024x768 (launchpad bug being worked on).

What changes/improvements/features should I be looking for?  I usually do internet searches for news and articles, copy internet articles to Libre with graphics & print, internet email, of course installs & updates, bug fix evaluations, test installs, (all partitioning by gparted.  Not about to let ubiquity trash my multiboot partitions with Windoze 7, archive, precise, lynx) ...

Not getting very far with "proprietary drivers" install not successful?

Anyway, bring it on...

Jerry

---

### Post by MG&amp;TL on 2012-06-08
> **jerrylamos said:**
> ?  I may not be looking hard enough, but on my wide screen notebook with both Quantal and Precise (test with Quantal's kernel) I can hardly tell the difference....


[http://www.omgubuntu.co.uk/2012/06/ubuntu-12-10-alpha-released](http://www.omgubuntu.co.uk/2012/06/ubuntu-12-10-alpha-released)

"Now before anyone gets too excited I will temper enthusiasm: there  aren’t a wealth of forward-facing changes for you to see. Like most  Alpha releases of Ubuntu the changes are, at this stage, inward facing  and in their initial stages."

---

### Post by balloons on 2012-06-08
> **ronacc said:**
> I tried the alternate but it craps out just after the partitioner starts detecting my drives . there is something about quantal that don't like my hardware , I can install precise ok ( I've done it a couple of times since the problem started just to check ) and I was able to install the very first daily live ok but no joy since then . There seems to be more than one problem , the early daily's were crashing at the same place as the alternate now does but the current lives don't even get that far , they die just after you select if you want to download updates while installing .

Glad your out testing out the dailies! What's the bug number for this? I'm curious what kind of hardware you've got that is causing things to not work with so much stubborness :-)

---

### Post by ronacc on 2012-06-08
> **guitara said:**
> Glad your out testing out the dailies! What's the bug number for this? I'm curious what kind of hardware you've got that is causing things to not work with so much stubborness :-)

bug # is 1009180

what is the cmd to make a list of your HDW and I'll post that . basicly Im amd64x2 4600+ and nvidia 7600gs and 4gb ram .

edit: the "live session" works fine it's just the install that won't work .

---

### Post by ronacc on 2012-06-08
reading through the bug report the partman log looks really suspicious , like its going into an infinite loop .

---

### Post by Curtis6767 on 2012-06-08
I'm running 12.10 in VBox.

I have 85 updates in the queue but I'm getting a warning about a partial install so I'm waiting for this to get cleared up before actually downloading.

I've read that I shouldn't do partial updates, but I don't think this is going to change until the second issue is resolved.

Posted via 12.10 Apha 1

I'm getting these two warnings:

---

### Post by MG&amp;TL on 2012-06-08
> **Curtis6767 said:**
> I'm running 12.10 in VBox.

I have 85 updates in the queue but I'm getting a warning about a partial install so I'm waiting for this to get cleared up before actually downloading.

I've read that I shouldn't do partial updates, but I don't think this is going to change until the second issue is resolved.

Posted via 12.10 Apha 1

I'm getting these two warnings:

Run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

they usually seem to fix themselves. Not sure why UM can't do that. Although if it says "will REMOVE x, y, z", obviously don't do it.

---

### Post by Curtis6767 on 2012-06-08
Those commands got me this:

---

### Post by unibroker on 2012-06-08
> **MG&TL said:**
> Run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

they usually seem to fix themselves. Not sure why UM can't do that. Although if it says "will REMOVE x, y, z", obviously don't do it.

That is what I ran when I went from 11.04 to 12.04.  Although the OS had some rough edges at the time it cleared up with Updates.  Not sure at what stage of development I was at when I did this as I had just dual booted with WinXP.  I have a 3rd world internet connection so not really looking forward using the above code this time around.

---

### Post by sammiev on 2012-06-08
> **Curtis6767 said:**
> Those commands got me this:

You will need to edit your source list and change the few lines in error from quantal to precise. You can also put a "#" sign in front of those lines or just wait for them to work from the source. You have choices. :)

---

### Post by MG&amp;TL on 2012-06-08
> **sammiev said:**
> You will need to edit your source list and change the few lines in error from quantal to precise. You can also put a "#" sign in front of those lines or just wait for them to work from the source. You have choices. :)

Or just ignore them...they don't do much. :)

---

### Post by Curtis6767 on 2012-06-08
First, I don't have those in my sources list so nothing to edit.

Second, if I ignore them, then can I just go ahead and download what's in my queue even though that will be a partial download? I don't care if it's best to wait and download them next week

Otherwise, 12.10 seems to purring right along.

---

### Post by MG&amp;TL on 2012-06-08
> **Curtis6767 said:**
> 
Second, if I ignore them, then can I just go ahead and download what's in my queue even though that will be a partial download? I don't care if it's best to wait and download them next week


extras.ubuntu.com doesn't exist yet for Quantal. Therefore ignoring the error will have no effect. :)

---

### Post by Curtis6767 on 2012-06-08
> **MG&TL said:**
> extras.ubuntu.com doesn't exist yet for Quantal. Therefore ignoring the error will have no effect. :)

Okay, thanks

---

### Post by cariboo on 2012-06-08
@Curtis6767, if you are getting an error the the repository isn't available, then you do have it in your /etc/apt/sources.list. You can either disable the **extras** repository using software sources either in the software centre, or synaptic, or change it to Precise, in order to stop the error. See the screenshot. You can also disable it from the command line using your favourite text editor:

```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#deb http://extras.ubuntu.com/ubuntu precise main
deb http://ca.archive.ubuntu.com/ubuntu/ quantal-proposed restricted main multi$
# deb-src http://extras.ubuntu.com/ubuntu quantal main
```

---

### Post by Curtis6767 on 2012-06-08
> **cariboo907 said:**
> @Curtis6767, if you are getting an error the the repository isn't available, then you do have it in your /etc/apt/sources.list. You can either disable the **extras** repository using software sources either in the software centre, or synaptic, or change it to Precise, in order to stop the error. See the screenshot. You can also disable it from the command line using your favourite text editor:

Found it and then went to Other Software tab and set it up to mimic image. This took care of it.

Thanks

---

### Post by jerrylamos on 2012-06-08
> **MG&TL said:**
> Run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

they usually seem to fix themselves. Not sure why UM can't do that. Although if it says "will REMOVE x, y, z", obviously don't do it.

Actually, I do "sudo aptitude update && sudo aptitude safe-upgrade" unless I notice something is not getting installed that should be, like a new kernel, then I'll hazard a dist-upgrade.

"partial upgrades" have screwed many many installs.  I crank up synaptic, set repositories where I like them example check "partners", turn update manager as far off as possible, reload.

From then on I use the sudo commands daily.

Jerry

---

### Post by unibroker on 2012-06-09
> **jerrylamos said:**
> 2 bugs so far (besides Nautilus crapping out frequently as usual)

1. "Try Ubuntu " fails on this 3.3 GHz ATI Radeon xpress 200 unless at boot menu push F6 and add
nomodeset
to the boot line.  Shades of modeset problems since Intrepid.  No clue why "startup disk" would have to do "modeset" since a "safe boot" would be best.  My opinion.  Did work O.K. on netbook and widescreen notebook.

2. Widescreen notebook can't set external monitor screen resolution, or turn off laptop monitor see bug #1007588.  System Settings, Displays fails on Apply.  Sebastian's working on it and may be making some headway.

As an aside, another partition running Pangolin with Quantal's kernel Display works fine.

Jerry
I downloaded the kernel 3.4 onto my precise partition.  Found only 2 display settings neither of which expanded the scrunched view on my widescreen.  It probably has something to do with my nvidia graphics driver.  I didn't even have time to send the two requested 3.4 tests as the eyestrain was intense.  I quickly uninstalled the kernel.

---

### Post by jerrylamos on 2012-06-10
> **unibroker said:**
> I downloaded the kernel 3.4 onto my precise partition.  Found only 2 display settings neither of which expanded the scrunched view on my widescreen.  It probably has something to do with my nvidia graphics driver.  I didn't even have time to send the two requested 3.4 tests as the eyestrain was intense.  I quickly uninstalled the kernel.

Having fits with my widescreen 1366x768 Acer Aspire 5253 notebook with external 1280x1024 monitor.  Settings displays "apply" seg faults every time, so I'm stuck with 1024x768.  And max bright (ouch) every boot on the wide screen.

Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310] so it's not just nvidia.

Ref. my bug #1007588 including back traces, strace, apport, ...  I think they've got the info.  Fix would depend on their time/indspiration.  "Does this bug affect you?"

On my Compaq tower ATI radeon xpress 200 the Quantal Alpha Startup disk  won't unless nomodeset is specified.  Once installed runs O.K. 1440x900.

Jerry

---

### Post by ronacc on 2012-06-10
this is starting to look like edgy eft for me and that was so bad it drove me away from ubuntu for awhile. I haven't been able to install a daily after the very first , I have an updated from precise install that is still hanging on by its toenails ( running the xorg edggers driver (nvidia)) . the internet is dog slow , sound is terrible , nautilus keeps the ball spinning 30 or more seconds after a dir is opened and generally poor performance .

---

### Post by jerrylamos on 2012-06-10
> **ronacc said:**
> this is starting to look like edgy eft for me and that was so bad it drove me away from ubuntu for awhile. I haven't been able to install a daily after the very first , I have an updated from precise install that is still hanging on by its toenails ( running the xorg edggers driver (nvidia)) . the internet is dog slow , sound is terrible , nautilus keeps the ball spinning 30 or more seconds after a dir is opened and generally poor performance .

Guess that's why there are a bunch of testers - some good results, some bad, some indifferent.  6 June i386.iso actually did work on USB flash memory from quantal startup disk creator, installed O.K. on netbook, widescreen notebook, and tower.  Bugs: 
1. Nautilus crashes everywhere, 
2. widescreen notebook with external monitor is stuck on 1024x768 Display Settings seg faults,  Ugly.  Strange, tower's 1440x900 no problem.
 
***** Edit - now stuck on 1280x1024 my wife in bathing suit on Australian beach is really stretched out.  Systems Settings doesn't work.  Now the wide screen 1366x768 or whatever is right but systems settings don't.  Something about an FGLRX driver? 

3. tower the startup disk had to do nomodeset on the linux boot line.

For what I do, quantal's about the same as precise.  As requested in this forum I have a 3.4.0-4 quantal kernel installed on one of the precise and runs just like precise so far. 

quantal does not run on my nice responsive IBM Thinkpad T40 because of no pae flag.  I run precise lubuntu on it, and for speed slitaz runs fast in memory but rough on features.  Will try upgrading the precise lubuntu to quantal to see what happens.

**** Edit - actually, precise lubuntu install with non-pae kernel can be upgraded to quantal so I did.  The kernel stays back at precise but everything else seems to be at quantal.  

Jerry

---

### Post by unibroker on 2012-06-10
> **jerrylamos said:**
> Guess that's why there are a bunch of testers - some good results, some bad, some indifferent.  6 June i386.iso actually did work on USB flash memory from quantal startup disk creator, installed O.K. on netbook, widescreen notebook, and tower.  Bugs: 
1. Nautilus crashes everywhere, 
2. widescreen notebook with external monitor is stuck on 1024x768 Display Settings seg faults,  Ugly.  Strange, tower's 1440x900 no problem. 
3. tower the startup disk had to do nomodeset on the linux boot line.

For what I do, quantal's about the same as precise.  As requested in this forum I have a 3.4.0-4 quantal kernel installed on one of the precise and runs just like precise so far. 

quantal does not run on my nice responsive IBM Thinkpad T40 because of no pae flag.  I run precise lubuntu on it, and for speed slitaz runs fast in memory but rough on features.  Will try upgrading the precise lubuntu to quantal to see what happens.

Jerry
That's why I was surprised at the headache-inducing screen when I installed the kernel 3.4 on Precise.  When I ran Quantal Alpha-1 from a live DVD it produced none of this.  I'm just glad the instructions for installing the kernel had an effective uninstall procedure just below.

---

