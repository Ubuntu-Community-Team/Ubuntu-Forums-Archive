---
title: "ISO Testing (Beta 2): March 26th &amp; 27th - Request for help"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-24
[B]*** UPDATED March 27th ***
[/B]As a result of everyone's contribution to testing the Beta 2 builds and thanks to their bug reports, developers managed to fix a few important bugs and release new builds (Beta 2 candidates) before the **[_[COLOR=Red]BetaRelease[/COLOR]_]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule") **deadline** (March 29th). **You can see details of what was fixed in the new builds in** [_[COLOR=Red]Guitara's[/COLOR]_]("https://launchpad.net/%7Enskaggs") [_[COLOR=Red]post[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=11798162&postcount=76") **in this same thread. It means everyone's efforts were fruitful and represented real contributions to Ubuntu quality.
For those that will make an effort to try these new builds and contribute even more: Time is short, but we still have tomorrow to test and report bugs. As usual, please post all your questions and doubts here or contact [**_[COLOR=Red]me[/COLOR]_**]("https://launchpad.net/%7EEffenberg0x0") directly via PM or e-mail if you need any help.

Thank you,
Effenberg0x0 

----------------------------------------------------------------------------------
[B]EDITED TO INCLUDE THE FINAL LINK TO THE TUTORIAL:
[/B]**_[COLOR=Red]https://wiki.ubuntu.com/U+1/iso-testing-main[/COLOR]_**

That's it guys, another "fun" no-sleep weekend LOL. Here's the U+1 Team first attempt at a complete tutorial for people that have problems and/or need guidance understanding ISO Testing, downloading the ISOs, burning and installing them. It has two approaches: **Simple Testing** (get, burn, run) and **QA-Testing** (how to use the QA ISO Tracker)

I did my best given the short time available. I hope it serves some purpose and helps someone. I'm absolutely sure it has typos, sections that could have been better written, procedures I could have mentioned (such as MD5 check). Or simply wrong stuff (hopefully not, but to tell you the truth, I'm *very* tired). But, as you know, our Wiki is open to edition. I hope others take the time to improve and fix it the way they see fit.

And more importantly: Let's use all our resources to try to get people to test.  

Regards,
Effenberg

-------------------------------------------------------------------------------------------------[B]
ORIGINAL MESSAGE[/B]

Hi everyone :)

You guys know that with Beta 2 Release by **March 29th (Thursday)**, testing of the ISO should be done by **27th (Tuesday)**. 

Many of you will go through the QA-Testing process via QA Tracker and that is great. But one of the problems we are very aware off is that the current QA Process is not properly user-friendly. Most people won't go through the QA Tracker process and Test-Cases. Hopefully this will change some day soon. But our short-term need is to get **as much people as possible** to at least try the ISO and report back.

**This release is appealing:** If ordinary users understand that not much will change from B2 to final release and that this is an opportunity to get the latest Ubuntu before everyone else, it might spread virally in blogs and online/social.

I'm working on a **"Step by Step" ISO-Testing Tutorial**. It attempts to, in the most friendly and clear way I can write, instruct ordinary users on how to get and install the ISO (and hopefully get them to try the QA process, although it won't be mandatory). 

I'll finish it by tomorrow. You can see what it looks like so far and follow it's development here: [https://wiki.ubuntu.com/U+1/iso-testing](https://wiki.ubuntu.com/U+1/iso-testing)

By Monday morning, I'll post it here and:

[LIST]
[*]Ask the staff to put it as a sticky here at Ubuntu+1.
[*]Ask everyone in my friends list, twitter, etc to give it a try or at least spread it to their contacts.
[*]Ask helpers in other forum sections if it would be possible to publicize it in those sections too. But I'm not sure if this will be doable.
[*]Ask friends at other forums to help.
[*]Add it to my signature in all forums.
[/LIST]
I'm asking for your help too. If you can try the ISO, spread the link to the sticky thread here (once it is created), post it on your blogs, twitter, etc we may be capable of increasing the number of tests significantly. At any rate, we'll generate some impact.

I'll be online at our IRC channel (**#U+1 on Freenode**) throughout Monday and Tuesday if anyone wants to talk in real time.

I really appreciate any help you can offer.

Thanks,
Effenberg

---

### Post by jerrylamos on 2012-03-24
Help??

Love it!

Installed today's Beta candidate went O.K. as far as I could see.

Restart according to the install screen, got:

initramfs

Some message about not being able to get C/H/?? values.

How do I write a launchpad bug from initramfs??

It's a dual hard drive system.  Booted onto the second hard drive with Lucid LTS, then ran update-grub and grub-install.  Lucid Grub works fine.

Booted precise pangolin Beta candidate O.K.

One hard drive is IDE, the other a SATA. Lucid Lynx, Meerkat, previous ubuntu's back to whenever assign the boot hard drive as /dev/sda.  Works perfectly.  Pangolin decides the boot hard drive is /dev/sdb and then gets confused.

From some past bug experience with Narwhal, Pangolin Grub is looking for some UUID on the wrong hard drive.  Never ever occurs to Pangolin Grub to look on the other hard drive for that UUID.

How do I write a bug for that??

Thanks much, appreciate the help.

Jerry

---

### Post by effenberg0x0 on 2012-03-24
Hi Jerry, Thank you so much for taking the time to test.

> **jerrylamos said:**
> Help??
Love it!
Installed today's Beta candidate went O.K. as far as I could see.
Restart according to the install screen, got:
initramfs
Some message about not being able to get C/H/?? values.
How do I write a launchpad bug from initramfs??


Please report it against initramfs-tools. Triagers will later tag it properly.
You have two options here:
[B]1. Report it using Apport:
[/B]```
apport-bug initramfs-tools
```[B]2. Manually fill in a Launchpad Bug Report:
[/B]- Access [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)
- Write a bug summary
- Select Package initramfs-tools

In this case, I think it would be nice if you could report it via apport and then visit the Launchpad bug page and add as much info as possible about your hardware, your setup, etc. Try to be as thorough as possible. You should also add the tag "precise" to it. 

> **jerrylamos said:**
> 
It's a dual hard drive system.  Booted onto the second hard drive with Lucid LTS, then ran update-grub and grub-install.  Lucid Grub works fine.

Booted precise pangolin Beta candidate O.K.

One hard drive is IDE, the other a SATA. Lucid Lynx, Meerkat, previous ubuntu's back to whenever assign the boot hard drive as /dev/sda.  Works perfectly.  Pangolin decides the boot hard drive is /dev/sdb and then gets confused.

From some past bug experience with Narwhal, Pangolin Grub is looking for some UUID on the wrong hard drive.  Never ever occurs to Pangolin Grub to look on the other hard drive for that UUID.

How do I write a bug for that??

Thanks much, appreciate the help.

Jerry

You have experience and know a lot about your hardware. You also have a hypothesis (UUID issue you mentioned). That can help a lot, you got what it takes to create a high quality bug report. 

Thanks,
Effenberg

---

### Post by keithpeter on 2012-03-24
Hello effenberg0x0 and all

Wiki pages look clear.

Alas, it will have to be 'simple' testing for me over the Monday/Tuesday as I have work and travelling.

What time (in UK timezone) will the beta actually exist roughly?

I can do a test install on a netbook early afternoon.

---

### Post by ronacc on 2012-03-24
is the beta candidate jerry is talking about todays daily live ? (march 24 ) .

---

### Post by jerrylamos on 2012-03-24
> **ronacc said:**
> is the beta candidate jerry is talking about todays daily live ? (march 24 ) .

Just zsync'd it today:

Mar 24 08:27 precise-desktop-i386.iso

DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux Compaq 3.2.0-20-generic-pae #32-Ubuntu SMP Thu Mar 22 02:43:40 UTC 2012 i686 i686 i386 GNU/Linux

I've then done usual install of aptitude, synaptic, samba, ...

No particular problem to try another install if there's something informative that can be done.  Install takes about a day squeezing in zsync, gparted, ... with the other things I do. 

Jerry

---

### Post by cariboo on 2012-03-24
I did a test install yesterday, as I may not have time next week to do it again. I did the the **Broken internet** and **Something else** test cases. The broken internet test case because of bug #[lpbug]963475[/lpbug] and the something else test case, as the partitioner has been broken for me for the last couple of months, and I wanted to make sure it works.

Additionally if you have run the System Testing applet, and up loaded the results you can view them using the following link:

[https://launchpad.net/people/+me/+hwdb-submissions](https://launchpad.net/people/+me/+hwdb-submissions)

In my case, I've used the applet since 2008, so I have 14 profiles in the list:

[https://launchpad.net/~cariboo907/+hwdb-submissions](https://launchpad.net/~cariboo907/+hwdb-submissions)

---

### Post by bfb on 2012-03-25
/Downloads$ zsync [http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync](http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync) 
failed on url [http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync](http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync)
could not read control file from URL [http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync](http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync)

[http://cdimage.ubuntu.com/releases/precise/beta-2/](http://cdimage.ubuntu.com/releases/precise/beta-2/)
**Not Found**

 The requested URL /releases/precise/beta-2/ was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at cdimage.ubuntu.com Port 80

I can't test if I can't downlaod....

---

### Post by effenberg0x0 on 2012-03-25
Hello,

It hasn't been published yet, just as the tutorial. If you'd like to have a look at the ISO QA Tracker, you can view the download information for each of the many Ubuntu products at [http://iso.qa.ubuntu.com/qatracker/milestones/210/builds](http://iso.qa.ubuntu.com/qatracker/milestones/210/builds). 

But, for a basic test, just choose the latest 32-Bit or 64-Bit daily build. As usual, they are posted at the cdimage website. The latest daily builds are here: [http://cdimage.ubuntu.com/daily/20120324.1/](http://cdimage.ubuntu.com/daily/20120324.1/)

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-03-25
Hi, I think I should  try to make it clearer for others that read this thread: On March 23rd we had BetaFreeze (see the release schedule [_**[COLOR=Red]here[/COLOR]**_]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule") and the definition of "Beta Freeze" [**_[COLOR=Red]here[/COLOR]_**]("https://wiki.ubuntu.com/BetaFreeze"). It means that, theoretically, we should have no more daily builds after the March 23rd one: Everyone tests it for a week or so, and it is renamed as Beta 2 on March 29th. 

The thing is, just as any Daily Build, sometimes there are some (hopefully) minor glitches that are blatant and can be fixed quickly. This is why the possibility of having one or more daily builds after BetaFreeze exists. However, it's a much more complicated process. It must pass through the Release Team for approval, etc. So (also theoretically), if they approved a new daily after BetaFreeze, it probably fixes something relevant. 

Because of that possibility, some people usually wait until 2 or 3 days after BetaFreeze to start testing. 

If you look at [http://cdimage.ubuntu.com/daily/](http://cdimage.ubuntu.com/daily/), you'll see there are three directories: 23rd, 24th and 24.1. Hopefully it will stop there and we will work with this release on 26th and 27th. 

However, some people won't be available to test 2 or 3 days before the Beta release, so they simply test the latest build that is there on Day 0 or Day 1 after BetaFreeze. Huge testers, that test many products and do many test-cases need time, so they can't wait. They assume that no big changes and fixes should be made at this point (which should be correct), and therefore it is safe to proceed with testing. 

It's a matter of personal preferences actually. IMO, giving only 4 days to testers is admitting that quality assurance is not important. So, whatever testers choose to do, they are already doing a lot. 

Regards,
Effenberg

---

### Post by ubunbu on 2012-03-25
I tried installing about a week ago both through the update method (which stalled near the end and broke my update manager) then on a DVD (which would freeze up on the various set up screens and drop the installation process)

---

### Post by keithpeter on 2012-03-25
> **effenberg0x0 said:**
> If you look at [http://cdimage.ubuntu.com/daily/](http://cdimage.ubuntu.com/daily/), you'll see there are three directories: 23rd, 24th and 24.1. Hopefully it will stop there and we will work with this release on 26th and 27th. 

Hello All

Right now, the directories above seem to have Alternate Install CDs only. Is that what you want testing? Live CD done?

---

### Post by spsf on 2012-03-25
> **keithpeter said:**
> Hello All

Right now, the directories above seem to have Alternate Install CDs only. Is that what you want testing? Live CD done?

Just change directory to:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by jerrylamos on 2012-03-25
The official announcements of downloads for aplpha beta gamma etc. may point somewhere and even a bit devious to follow, not all the images etc.

So I just zsync from the daily build for ubuntu lubuntu ... that's either the same as the "download" they call out, or even more updated than that.

Also, zsync as usual from the daily builds is less of a load on the servers.

I did that on yesterday's daily build and did a new install on one of my test pc's.

Beta2 candidate bug was, on a two hard drive one sata and one ide, install went on one, on rebooting grub selected the other and couldn't find the UUID.  Absolutely never dawned on grub to look for that UUID on the the correct hard drive.  Bug number is somewhere in this thread. 

Recovered by booting the hard drive that Beta2 hadn't installed grub, brought up Lucid LTS, update-grub and grub-install ran perfectly.  

The new daily build booted and ran except for sound which is dead.  Wrote a bug on that.

Presently getting ready to try install on this netbook.

Enjoy

Jerry

p.s.  No bugs no fun.

---

### Post by keithpeter on 2012-03-25
> **spsf said:**
> Just change directory to:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Thanks, me being thick as usual, just clocked the directory structure of the cdimage server.

I'll get the most recent one I see in that folder early on Monday and give that a go

Cheers

---

### Post by ronacc on 2012-03-25
installed todays 64bit daily , install went well , used "other " for drive selection , partitioning and grub placement . even wireless came up on the install without prodding ( not always so on some alphas ) , installed synaptic and gnome-shell , rebboted into GS all seems well .

---

### Post by grahammechanical on 2012-03-25
In downloaded from here:

[http://iso.qa.ubuntu.com/qatracker/milestones/210/builds]("http://iso.qa.ubuntu.com/qatracker/milestones/210/builds")

If you click on the ISO name, such as Ubuntu Desktop amd64 you go to this page

[http://iso.qa.ubuntu.com/qatracker/milestones/210/builds/14153/testcases]("http://iso.qa.ubuntu.com/qatracker/milestones/210/builds/14153/testcases")

It lists the test cases the QA would like run for that ISO image. They vary. If, for example, you click Live Session, you get this page

[http://iso.qa.ubuntu.com/qatracker/milestones/210/builds/14153/testcases/4/results]("http://iso.qa.ubuntu.com/qatracker/milestones/210/builds/14153/testcases/4/results")

If you click on the link to test case, you get this this page

[http://testcases.qa.ubuntu.com/Install/DesktopLiveSession]("http://testcases.qa.ubuntu.com/Install/DesktopLiveSession")

It is a step by step run through of what should (fingers crossed) happen.

This is great if you have a second machine or a printer. Not so great if, like me you have to write it out by hand.

If we have a launchpad account we can click on log in and then we can confirm the Single Sign On and that leads us to a page where we can report our results for that ISO image.

I have yet to try this myself.

Note they want a hardware profile and a url to it. To get one for your machine run this command

```
sudo lshw -html >hardwareprofile.html
```

That will generate the hardware profile and put it in the home folder.

I got my hardware profile but not done anything with it.

Regards.

P.S. After reviewing the QA reporting method I see that we cannot browse to our home folder to attach the profile file like we can on the forums when we want to attach an avatar image. Disappointing.

---

### Post by bennachie on 2012-03-25
I'm always surprised to note how few people actually participate in the ISO testing round. It's not that hard, although the wiki will be welcome, and we always seem to find some bugs that have slipped past the internal testing process. 

I've spent a fair bit of the day testing the 20120325 images. FWIW, Ubuntu exhibits an annoying "gnome-settings-daemon" crash that wasn't evident in pre-beta2 versions, while my netbook screen flickers badly every time I use the Unity launcher. That wasn't the case pre-beta2 either, and doesn't seem to affect my desktop - or Wubi - installations. Both incidents have been reported. On a brighter note, Kubuntu generally works well, with just a couple of minor cosmetic glitches and Xubuntu has been completely trouble-free for me. 

YMMV.

---

### Post by ventrical on 2012-03-25
> **bfb said:**
> /Downloads$ zsync [http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync](http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync) 
failed on url [http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync](http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync)
could not read control file from URL [http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync](http://cdimage.ubuntu.com/releases/precise/beta-2/ubuntu-12.04-beta1-dvd-amd64.iso.zsync)

[http://cdimage.ubuntu.com/releases/precise/beta-2/](http://cdimage.ubuntu.com/releases/precise/beta-2/)
**Not Found**

 The requested URL /releases/precise/beta-2/ was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at cdimage.ubuntu.com Port 80

I can't test if I can't downlaod....

I got the same thing .. but I see it is not released yet .. but the builds are.

---

### Post by ventrical on 2012-03-25
Sorry .. I'll have to wait until tommorrow ..

---

### Post by balloons on 2012-03-25
> **ventrical said:**
> I got the same thing .. but I see it is not released yet .. but the builds are.

Yes -- I'm not sure when exactly (I'm assuming by the time I'm around tomorrow morning) the builds will be completed. However, they will include unity 5.8 and the checkbox application test suite using the new -qt interface. Thanks to all of you who helped write tests for that (and there are always more tests to write, PM me if interested -- It's really EASY!). Some of that might not land until later on Monday.

Thanks to you all for helping test.

---

### Post by jerrylamos on 2012-03-25
Installed March 25 daily build on a netbook, a tower, and a notebook.  Various bugs reported on launchpad.

Various install foibles.  All installs from same USB flash.  This Acer Aspire 5253 notebook relatively clean.

This notebook is the only one of the three that sound works on.....yes, there's a bug entry for the others.

Jerry

---

### Post by ubunbu on 2012-03-26
Just installed, and on reboot got 'no partition found' which turned out to be a known bug and was fixed by reinstalling grub using boot repair... And otherwise it seems pretty buggy but it's working.

---

### Post by ventrical on 2012-03-26
> **effenberg0x0 said:**
> Hi everyone :)

You guys know that with Beta 2 Release by **March 29th (Thursday)**, testing of the ISO should be done by **27th (Tuesday)**. 

Many of you will go through the QA-Testing process via QA Tracker and that is great. But one of the problems we are very aware off is that the current QA Process is not properly user-friendly. Most people won't go through the QA Tracker process and Test-Cases. Hopefully this will change some day soon. But our short-term need is to get **as much people as possible** to at least try the ISO and report back.

**This release is appealing:** If ordinary users understand that not much will change from B2 to final release and that this is an opportunity to get the latest Ubuntu before everyone else, it might spread virally in blogs and online/social.

I'm working on a **"Step by Step" ISO-Testing Tutorial**. It attempts to, in the most friendly and clear way I can write, instruct ordinary users on how to get and install the ISO (and hopefully get them to try the QA process, although it won't be mandatory). 

I'll finish it by tomorrow. You can see what it looks like so far and follow it's development here: [https://wiki.ubuntu.com/U+1/iso-testing](https://wiki.ubuntu.com/U+1/iso-testing)

By Monday morning, I'll post it here and:

[LIST]
[*]Ask the staff to put it as a sticky here at Ubuntu+1.
[*]Ask everyone in my friends list, twitter, etc to give it a try or at least spread it to their contacts.
[*]Ask helpers in other forum sections if it would be possible to publicize it in those sections too. But I'm not sure if this will be doable.
[*]Ask friends at other forums to help.
[*]Add it to my signature in all forums.
[/LIST]
I'm asking for your help too. If you can try the ISO, spread the link to the sticky thread here (once it is created), post it on your blogs, twitter, etc we may be capable of increasing the number of tests significantly. At any rate, we'll generate some impact.

I'll be online at our IRC channel (**#U+1 on Freenode**) throughout Monday and Tuesday if anyone wants to talk in real time.

I really appreciate any help you can offer.

Thanks,
Effenberg

I was reading so fast I didn't see the part where it said you will have it finished by tommorrow. :):)  I see you removed the links and answers from the wiki ISO testing for now .. smart move.

---

### Post by ventrical on 2012-03-26
> **spsf said:**
> Just change directory to:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


 I tried everything to zsync this file: ubuntu-12.04-beta1-desktop-i386.iso from daily but it keeps telling me it can't find the control file. If I leave my beta1 out it tells me it will have to download the whole file .

 What am I doing wrong here ?

---

### Post by effenberg0x0 on 2012-03-26
Hello everyone,

My original post in this thread was updated to include the new link for the [**ISO-Testing Tutorial**]("https://wiki.ubuntu.com/U+1/iso-testing-main").

If some staff member could write a sticky thread, post it here (and, if possible, even other forum areas), it would be nice. After all, it will be a sticky just for this Monday and Tuesday, then testing is done. 

Ubuntu needs as much people as possible testing Beta 2. Let's make an effort. 

Kind regards,
Effenberg

---

### Post by effenberg0x0 on 2012-03-26
> **ventrical said:**
> I tried everything to zsync this file: ubuntu-12.04-beta1-desktop-i386.iso from daily but it keeps telling me it can't find the control file. If I leave my beta1 out it tells me it will have to download the whole file .

 What am I doing wrong here ?

Hi Ventrical :)

Wrong URL. You should see this:
```
AL-DESK01$ zsync http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso.zsync
#################### 100.0% 235.8 kBps DONE     

No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C oe
downloading from http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso:
-------------------- 0.0% 8.7 kBps         
#################### 100.0% 1936.7 kBps DONE      

verifying download...checksum matches OK
used 0 local, fetched 733262166

AL-DESK01$ ls -lha precise*.iso
-rw------- 1 ahsl ahsl 700M Mar 25 07:23 precise-desktop-amd64.iso
```

Sorry for poor formatting, this terminal uses bashish.

Regards,
Effenberg

---

### Post by ventrical on 2012-03-26
> **effenberg0x0 said:**
> Hi Ventrical :)

Wrong URL. You should see this:
```
AL-DESK01$ zsync http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso.zsync
#################### 100.0% 235.8 kBps DONE     

No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C oe
downloading from http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso:
-------------------- 0.0% 8.7 kBps         
#################### 100.0% 1936.7 kBps DONE      

verifying download...checksum matches OK
used 0 local, fetched 733262166

AL-DESK01$ ls -lha precise*.iso
-rw------- 1 ahsl ahsl 700M Mar 25 07:23 precise-desktop-amd64.iso
```Sorry for poor formatting, this terminal uses bashish.

Regards,
Effenberg


So basically you downloaded the whole ISO file (as I think I see) plus I just want the 32bit desktop version.  So how does zsync save time and bandwidth??

edit ... ok .. I didn't have the daily to begin with so I have to download the whole  file to be able to use zsync to udpate.

---

### Post by ventrical on 2012-03-26
> **effenberg0x0 said:**
> Hello everyone,

My original post in this thread was updated to include the new link for the [**ISO-Testing Tutorial**]("https://wiki.ubuntu.com/U+1/iso-testing-main").

If some staff member could write a sticky thread, post it here (and, if possible, even other forum areas), it would be nice. After all, it will be a sticky just for this Monday and Tuesday, then testing is done. 

Ubuntu needs as much people as possible testing Beta 2. Let's make an effort. 

Kind regards,
Effenberg

Nice work .. and clearly explained .

---

### Post by effenberg0x0 on 2012-03-26
> **ventrical said:**
> So basically you downloaded the whole ISO file (as I think I see) plus I just want the 32bit desktop version.  So how does zsync save time and bandwidth??

edit ... ok .. I didn't have the daily to begin with so I have to download the whole  file to be able to use zsync to udpate.

Hi Vetrical,

Yes, I recommended ZSync mainly because some people may loose their broadband connection in a 700MB download... so using ZSync they can restart where they stopped. Of course, other methods, including some browser can also do it. 

Regards,
Effenberg

---

### Post by ronacc on 2012-03-26
I zsync'd yesterday's (mar 25) daily (amd64) no problem and checked just a few minutes ago , no new files ( 0 fetched )

---

### Post by ventrical on 2012-03-26
> **effenberg0x0 said:**
> Hi Vetrical,

Yes, I recommended ZSync mainly because some people may loose their broadband connection in a 700MB download... so using ZSync they can restart where they stopped. Of course, other methods, including some browser can also do it. 

Regards,
Effenberg

Thanks effenberg :)

  I just downloaded the recent build and .... holy  banana tress !!! this thing is running off the live.iso a if it were a hard drive.. in fact it is running faster than most of my hard drives.

  Ok.. I'm off to do a hard install.

---

### Post by fjgaude on 2012-03-26
A fresh install of today's build went as it should.

Used 'other' onto an SSD with two other HDDs in Intel Z68 system. All went perfectly. No issues!

Well done, and thanks!

---

### Post by effenberg0x0 on 2012-03-26
I've been emailing friends and asking them to give us a hand, testing the ISO if they can... It looks like a lot of people contributed. But, as it seems, everybody prefers to simply download the ISO and install it, without going through the QA process.

The positive side is that I haven't received any complaint yet: Just emails saying that it worked OK.

Maybe we have trained eyes? I've seen a couple bugs. Ex:

- Alternate 64-Bit. Let it try to get an IP via DHCP in a network with no DHCP, or one in which the DHCP will not allow your MAC Address to get an IP. Keep telling it to try again. Eventually you get stuck in a purple console screen, no menu, no button, no nothing.

- Alternate 64-Bit: After the first boot, right after install, you get Jockey, Update-Notifier and "Language Support" Windows popping, almost at once. If tells me to install Brazilian Portuguese, but I don't want to (my PCs are in English, I'm used to it). It will continue popping forever. Eventually, you can accept to install language support for Brazilian Portuguese, but not select it to be the default. But if you do that, ccsm will crash at open 100% times. The debug message in logs in "unable to set locale".

- Standard / Alternate 64-Bit: G-C-C/Displays, on a dual monitor setup (with Nouveau or nvidia-current), shows a single monitor.

I mean, my list here is growing. I think people simply install, but they are not used to spotting the problems.

Regards,
Effenberg

---

### Post by grahammechanical on 2012-03-26
Not received any complaints, yet? Well, here I am :)

I have just had the most frustrating experience trying to submit a report the QA. I tested using the live CD to TRY and to INSTALL using the screen reader. But sound is muted by default! So, the accessibility option no good.

QA needs a launchpad bug report. There are almost 2,000 reports for ubiquity. Cannot use Apport because the problems on the CD. To create my own bug report launchpad first directs me to a HOw-TO page which I have to read to find the link to the Launchpad form.

So, I get my bug number but QA is rejecting my submission because I did not know that it only wants the number not the hash ( # ) that Launchpad puts in front of the number.

And you said that we must have fun!

ISO testing is no substitute for alcohol when it comes to having fun. 

Regards.

---

### Post by effenberg0x0 on 2012-03-26
> **grahammechanical said:**
> 
And you said that we must have fun!

ISO testing is no substitute for alcohol when it comes to having fun. 

Regards.

Definitely not lol :)
Ok, I lied, It's no fun muahaha :)

Now seriously: This is a punctual effort for this LTS. The community around the Ubuntu+1 sub-forum has always been much more targeted at daily updates, testing packages, not ISOs (which is a lot smarter).

You know my opinion about ISO testing, I think we talked about that on iRC: It shouldn't exist. We should be able to automatically keep track of what effectively changed from daily to daily, what was fixed, what was not fixed, what was changed, what could be affected by that change (better communication to developers), etc. Why would we need to test everything over and over and over and over and over and over and over and over and over? We *should* simply stress-test areas indicated by developers, areas we know have been broke, areas we know have been changed/fixed. 

The current process is like asking as much people as possible, hundreds of people, to donate their time to drive your car around for half an hour and take notes of everything weird they feel in the car. However, we drive our car everyday and we *should* know what's broken and ask the mechanic (developer) to fix it. If he doesn't fix it, it's broken. There's no magic. No need to test it again until someone changes it. 

And then it gets fun. Package-oriented testing, as opposed to ISO-Oriented testing, means trying out unreleased packages, with new or fixed features, and actually using the Development Release heavily. Any similarity to what we have been doing here for some cycles? :)

However, until we (or anyone else) manages to implement a better process into QA, we will continue to ask people to test an entire ISO install, even though each of us can pinpoint where many of the not-fixed bugs are without ISO Testing. That's what Ubuntu+1 always did. We take Ubuntu+1 for a ride everyday. It frequently is used as our main machine OS. We know what's broken. We should receive information on what to test.

So, as much as I heartily support this process for our current sprint, and have dedicated many hours to it, you can rest assured that I am not gonna support in the QQ cycle. IMO it's brutal and not a smart method. But it's what we have today and QQ is just around the corner so... no much time to change anything now.

Regards,
Effenberg

---

### Post by grahammechanical on 2012-03-26
I agree.

I am burning some ISO images right now. I have worked out my test program. Live sessions for the 6 Ubuntu types both amd64 and i386. Followed by manual installs.

I am going to sign off my QA report with Compliments of U+1 Testing team.

By joining in we get some credit and maybe a voice as well. I have also learnt lessons that I can share through the U+1 wiki.

Regards.

---

### Post by dFlyer on 2012-03-26
Install of build 20120325 amd64 yesterday over i386. Attempted to install from live cd desktop failed. Was instructed to format / and and froze at removing non-required files instead of formating. Rebooted off same cd and did a direct install by passing the live desktop. Again instructed to format / and install proceded without a problem. Seems there are still bugs with .xsession-errors, libreoffice (recent files) and xiphos not locating sword. No crashes to report over the last 16 hours.

---

### Post by ronacc on 2012-03-26
the only bug I noticed during the install was that even though I left "download updates" unchecked it did it anyway ,this has been around for awhile and still not fixed .

---

### Post by jerrylamos on 2012-03-26
4 installs yesterday with 20120325.  By far the cleanest was this one, Lubuntu.  Running crackling fast on this 1.5 GHZ Pentium M,

The precise pangolin's on my Acer Aspire1 netbook and Compaq Presario 3.3 GHZ had some false starts and bugs reported to launchpad. Sound does not work on either one, also reported.

Clean install of precise pangolin on Acer Aspire 5253.  Sound even worked!  Note, all installs from same USB flash (ugh slow USB with pangolin) except the lubuntu booted directly from HD.  Zoom.

No show stoppers except sound bug.  Sound works on 1 out of 4 test pc's.

Jerry

---

### Post by ventrical on 2012-03-26
Seamless install here of thismorning's build. Not even a jiggle or a wiggle.! Straight off from 'Install Ubuntu'.

Linux ventrical-P4M266A-8237 3.2.0-20-generic-pae #32-Ubuntu SMP Thu Mar 22 02:43:40 UTC 2012 i686 i686 i386 GNU/Linux
ventrical@ventrical-P4M266A-8237:~$ 

The only bug I noticed was that the 'live' install actually works faster than the harddrive.

ventrical@ventrical-P4M266A-8237:~$ uname -a
Linux ventrical-P4M266A-8237 3.2.0-20-generic-pae #32-Ubuntu SMP Thu Mar 22 02:43:40 UTC 2012 i686 i686 i386 GNU/Linux
ventrical@ventrical-P4M266A-8237:~$ lspic
No command 'lspic' found, did you mean:
 Command 'aspic' from package 'aspic' (universe)
 Command 'lspci' from package 'pciutils' (main)
 Command 'lsdic' from package 'canna-utils' (universe)
lspic: command not found
ventrical@ventrical-P4M266A-8237:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
ventrical@ventrical-P4M266A-8237:~$

---

### Post by NHclimber on 2012-03-26
> **cariboo907 said:**
> .... and the something else test case, as the partitioner has been broken for me for the last couple of months, and I wanted to make sure it works.

And does it work?

---

### Post by ventrical on 2012-03-26
> **effenberg0x0 said:**
> [B]EDITED TO INCLUDE THE FINAL LINK TO THE TUTORIAL:
_[COLOR=Red]https://wiki.ubuntu.com/U+1/iso-testing-main[/COLOR]_[/B]

That's it guys, another "fun" no-sleep weekend LOL. Here's the U+1 Team first attempt at a complete tutorial for people that have problems and/or need guidance understanding ISO Testing, downloading the ISOs, burning and installing them. It has two approaches: **Simple Testing** (get, burn, run) and **QA-Testing** (how to use the QA ISO Tracker)

I did my best given the short time available. I hope it serves some purpose and helps someone. I'm absolutely sure it has typos, sections that could have been better written, procedures I could have mentioned (such as MD5 check). Or simply wrong stuff (hopefully not, but to tell you the truth, I'm *very* tired). But, as you know, our Wiki is open to edition. I hope others take the time to improve and fix it the way they see fit.

And more importantly: Let's use all our resources to try to get people to test.  

Regards,
Effenberg

  A great job effenberg! Kudos to you and all the team. I'm pooped too. Had two lawnmowers and a rototiller to fix today .. geesh ...  but I was able to download the daily, burn it, run it and so far , so good.

 One day at a time ... !

---

### Post by NHclimber on 2012-03-26
> 
**Do I risk loosing my current install and my personal data?**

 Unless you choose to install it **over** your current version or to **update** it, that won't happen.


This statement is not accurate.  There are bugs in partman that can permanently scramble the bootloader.

---

### Post by ventrical on 2012-03-26
> **NHclimber said:**
> This statement is not accurate.  There are bugs in partman that can permanently scramble the bootloader.

could you reference  a particular bug please?

thanks


edited


Unless you choose to install it **over** your current version or to **update**  it, that is not likely, however, there are certain bugs that can  scramble the grub bootloader. There is always a risk of things going  wrong with the partition manager during beta testing and this too may  depend on hybrid hardware conflicts that is not Ubuntu Certified  (discontinued) or Ubuntu friendly.

---

### Post by Doug S on 2012-03-26
Just a comment:
 
The ISO images are significantly larger than the Beta 1 ones (at least for the server ones I use). 64 bit server now doesn't fit on a CD, I had to change to a DVD. 32 bit server now barely fits on a CD (if I have to go to DVD in future, I will have to swap the drive in the (old old) computer).
 
References:```
2012.03.01  01:51       728,018,944 precise-server-amd64-beta1-01.iso
2012.03.14  08:21       725,921,792 precise-server-amd64-beta1-02.iso
2012.03.26  09:27       [COLOR=red]746,893,312[/COLOR] precise-server-amd64-beta2-01.iso
2012.02.29  08:58       715,436,032 precise-server-i386-beta1-01.iso
2012.03.03  10:50       717,533,184 precise-server-i386-beta1-02.iso
2012.03.24  08:11       733,261,824 precise-server-i386-beta2-01.iso
2012.03.26  08:18       733,261,824 precise-server-i386-beta2-02.iso
```

---

### Post by NHclimber on 2012-03-26
> **ventrical said:**
> could you reference  a particular bug please?

[https://bugs.launchpad.net/ubuntu/precise/+source/ubiquity/+bug/690926](https://bugs.launchpad.net/ubuntu/precise/+source/ubiquity/+bug/690926)

The side-effect of ubiquity choosing '/dev/sda' -- even when there's an existing grub install -- is bad news for people who might not know better and are running fakeraid :(

> **ventrical said:**
> **There is always a risk of things going  wrong ... during beta testing**

Isn't this what I just said?

---

### Post by ventrical on 2012-03-26
> **NHclimber said:**
> [https://bugs.launchpad.net/ubuntu/precise/+source/ubiquity/+bug/690926](https://bugs.launchpad.net/ubuntu/precise/+source/ubiquity/+bug/690926)

The side-effect of ubiquity choosing '/dev/sda' -- even when there's an existing grub install -- is bad news for people who might not know better and are running fakeraid :(



Isn't this what I just said?

 That is what I edited into the wiki text. Was not this your concern?


[https://wiki.ubuntu.com/U%2B1/iso-testing-main#preview](https://wiki.ubuntu.com/U%2B1/iso-testing-main#preview)

---

### Post by NHclimber on 2012-03-26
> **ventrical said:**
> That is what I edited into the wiki text. Was not this your concern?


[https://wiki.ubuntu.com/U%2B1/iso-testing-main#preview]("https://wiki.ubuntu.com/U%2B1/iso-testing-main#preview")


Sorry -- I didn't realize that "edited" in your previous post referred to the wiki. Apologies, my bad.  (I thought "edited" referred to asking for a bug reference...)

Thanks for taking the time to update the wiki.

---

### Post by ventrical on 2012-03-26
> **NHclimber said:**
> Sorry -- I didn't realize that "edited" in your previous post referred to the wiki. Apologies, my bad.  (I thought "edited" referred to asking for a bug reference...)

Thanks for taking the time to update the wiki.

My apologies too.. I'm just wore out and should have been more clear. Thanks for pointing that out eh .

---

### Post by ventrical on 2012-03-26
> **cariboo907 said:**
> I did a test install yesterday, as I may not have time next week to do it again. I did the the **Broken internet** and **Something else** test cases. The broken internet test case because of bug #[lpbug]963475[/lpbug] and the something else test case, as the partitioner has been broken for me for the last couple of months, and I wanted to make sure it works.

Additionally if you have run the System Testing applet, and up loaded the results you can view them using the following link:

[https://launchpad.net/people/+me/+hwdb-submissions](https://launchpad.net/people/+me/+hwdb-submissions)

In my case, I've used the applet since 2008, so I have 14 profiles in the list:

[https://launchpad.net/~cariboo907/+hwdb-submissions]("https://launchpad.net/%7Ecariboo907/+hwdb-submissions")

  I just did the something-else from "Install Ubuntu" from thismornings ISO on this machine :

```

ventrical@ventrical-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] LPC Controller (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
ventrical@ventrical-desktop:~$

```

and it was seamless.

---

### Post by NHclimber on 2012-03-26
> 
**What are "Standard" and "Alternate" ISOs?**

 
[LIST]
[*]"Standard" ISOs are at **[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)** 
[*]"Alternate" ISOs are at **[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)**.  Alternate ISOs use a different installer and allow for some different  install tasks, such as installing to systems with very low ram (less  than 384MB, implementing [RAID]("https://wiki.ubuntu.com/Raid") and [LVM]("https://wiki.ubuntu.com/hhtps%3A//wiki.ubuntu.com/Lvm"), among other. 
[/LIST]


The iso descriptions and their respective links are reversed:  standard is @ daily-live and alternate is @ daily.

---

### Post by effenberg0x0 on 2012-03-26
> **NHclimber said:**
> The iso descriptions and their respective links are reversed:  standard is @ daily-live and alternate is @ daily.

Hi, I believe you may be looking at a browser (or proxy) cached version of it? They show correctly in my browser. I'll have a look at it right now.

BTW, I never really thought we would face problems with URLs. A lot of people had a hard time finding files, browsing the servers, understanding versions, alternate vs standard (desktop), etc in order to download them. I don't think the names of these servers and their folder structure help much: 

- The files aren't properly "CD images" anymore, considering one can burn/mount them to other ODD (DVD/BluRay),  internal/external HDD, external USB/FireWire/eSata/etc device, virtual machine ODD/HDD/USB,  mount to network and boot via IPX, besides burning them to a CD-ROM. Most of my contacts that tested it mentioned using USB and VMs.
- "Desktop Releases" are not targeted at Desktops only. They can be used in any hardware: Desktops, Laptops, Servers. 
- Directory structure is not clear enough, and seeing people's problems with it is strong evidence of that. 

Nonetheless, as I mentioned one of these days on IRC, when I Google for "**Download Ubuntu Precise ISO**", the first 4 hits are from cdimage.ubuntu.com. Next hits are not even at ubuntu.com domain. So, it's unquestionable this server is relevant as a first point-of-contact for many users.

When we get to any of these links, besides the files, we see some basic introductory info at the top and one single link to wiki/BurningISOHowTo. No link to a Ubuntu support source. I believe this is not enough, it calls for a better specification: 

- Rename the server (something other than cdimage.domain, maybe simply **downloads.ubuntu.com**). 
- Use redirection from old to new one to not create problems for people that have coded something that uses cdimage* or have bookmarked it.
- Rearrangement of the directory structure (a more logical tree). Its not hard to think of a more structured way of arranging the files.
- Better introductory information (as initially brought up by Graham last week), pointing at least one *.ubuntu.com source for support and more detailed info. If possible, a single Wiki page from where users could advance to all forms of support (Wiki, UbuntuForums, IRC, etc).
- Considering we are very likely to have downloads for new Ubuntu-Based devices in the future (mobile, etc), if we do nothing, this will only get more confusing. 

Regards,
Effenberg

**EDIT: **Pushed it to [https://wiki.ubuntu.com/U+1/ideas](https://wiki.ubuntu.com/U+1/ideas)

---

### Post by grahammechanical on 2012-03-26
Why do they still call the images i386 and amd64. That sure confuses those not in the know.

It is midnight in the UK. This post is coming from my first HD install of the ISO testing program. It is Xubuntu i386. The arch command says it is an i686, which is more acurate from an Intel point of view.

HD install program

Xubuntu i386  - done - no problems.
Xubuntu amd64 - done - no problems arch = X86_64
Ubuntu Studio i386 - done - no problems    low-latency pae kernel



@ventrical   I used to have a 80088 machine. A slightly more advance CPU that the 8086 but It was not the one chosen. Batch files was as close to programming as I ever came.

---

### Post by ventrical on 2012-03-26
> **grahammechanical said:**
> Why do they still call the images i386 and amd64. That sure confuses those not in the know.

It is midnight in the UK. This post is coming from my first HD install of the ISO testing program. It is Xubuntu i386. The arch command says it is an i686, which is more acurate from an Intel point of view.

HD install program

Xubuntu i386  - done - no problems.

I think it may be the programming language because if it is written in i386 assembly then it will run cooler on i686 machines because the Pentium 4s ran hotter and were out performed by the 1.7GHz Dothans.

So using the NetBurst technology at that time would really drain a laptop battery, but if they assembled in 80386, and not use 686 instruction sets then power consumption would be lower and 2.4 Ghz P4s would run better.. me thinks...

7:40pm here in Canada, Ontario..

edit.. hehe I used to actually write programs in x86 (as in 8088 programming language). I forget a lot of it now.

2.4 Mhz processors back then. I still got WordStar somwhere :)

---

### Post by NHclimber on 2012-03-26
> **effenberg0x0 said:**
> Hi, I believe you may be looking at a browser (or proxy) cached version of it? They show correctly in my browser. I'll have a look at it right now.

???

[IMG]http://ubuntuone.com/0mBLqYEjLQgHd9YOwmvrgj[/IMG]

---

### Post by effenberg0x0 on 2012-03-26
There's something wrong, I see the wiki differently...
At any rate, feel free to edit and fix it. I've had it.

---

### Post by NHclimber on 2012-03-26
> **effenberg0x0 said:**
> At any rate, feel free to edit and fix it.

Ok -- fixed. (I should have just done that from the beginning)

Thanks for putting all that effort into the wiki. Extremely useful material and an excellent foundation for future release qa as well.  Thanks again!

---

### Post by effenberg0x0 on 2012-03-26
> **NHclimber said:**
> Ok -- fixed. (I should have just done that from the beginning) 
Thanks for fixing it. I'm beginning to see that, as you use the wiki a  lot, for many files, many edits, you begin to see weird things. And the  MoinMoin syntax is maddening. 
> **NHclimber said:**
> Thanks for putting all that effort into the wiki. Extremely useful material and an excellent foundation for future release qa as well.  Thanks again!
Thanks, it was a short deadline, as usual...By 28th, it's up to Dale and Graham to use it or not, integrally or partially in the team docs. 

I was out of home, away from PCs, when you changed it. As soon as I got back, I accessed the wiki to try to understand what was going on. And now I'm 100% sure there's definitely something wrong going on. Look at the attached screenshot. It doesn't show your edit in the page history! And I'm not the one that did that last change (it was you, of course). I have tested from two desktops, 2 laptops, the results are the same. Maybe it's something with my Launchpad account... no idea at this point.

[ATTACH]214988[/ATTACH]

Regards,
Effenberg

---

### Post by cariboo on 2012-03-27
It's about half an hour later, and I see the change list correctly.

---

### Post by effenberg0x0 on 2012-03-27
> **cariboo907 said:**
> It's about half an hour later, and I see the change list correctly.

Yea, I'm not sure what's going on, why does things look different to me, tested in different PCs. I'll get some sleep urgently, maybe I'm going insane or something :)

Regards,
Effenberg

---

### Post by Doug S on 2012-03-27
> **Doug S said:**
> Just a comment:
 
The ISO images are significantly larger than the Beta 1 ones (at least for the server ones I use). 64 bit server now doesn't fit on a CD, I had to change to a DVD. 32 bit server now barely fits on a CD (if I have to go to DVD in future, I will have to swap the drive in the (old old) computer).
 
References:```
2012.03.01  01:51       728,018,944 precise-server-amd64-beta1-01.iso
2012.03.14  08:21       725,921,792 precise-server-amd64-beta1-02.iso
2012.03.26  09:27       [COLOR=red]746,893,312[/COLOR] precise-server-amd64-beta2-01.iso
2012.02.29  08:58       715,436,032 precise-server-i386-beta1-01.iso
2012.03.03  10:50       717,533,184 precise-server-i386-beta1-02.iso
2012.03.24  08:11       733,261,824 precise-server-i386-beta2-01.iso
2012.03.26  08:18       733,261,824 precise-server-i386-beta2-02.iso
```
Now I see that the ISO images are smaller than any previous ones I have downloaded.```
2012.03.26  09:27       [COLOR=red]746,893,312[/COLOR] precise-server-amd64-beta2-01.iso
2012.03.26  23:40       [COLOR=red]722,776,064[/COLOR] precise-server-amd64-beta2-02.iso
```

---

### Post by ventrical on 2012-03-27
@effenberg
But those links have been at the main testers wiki preview page all this time. Why didn't you link into them ?

[https://wiki.ubuntu.com/U%2B1/tester-wiki#preview]("https://wiki.ubuntu.com/U%2B1/tester-wiki#preview")

 No .. it's me ..  I should of made an earlier note about it.

---

### Post by ventrical on 2012-03-27
> **effenberg0x0 said:**
> There's something wrong, I see the wiki differently...
At any rate, feel free to edit and fix it. I've had it.

  Hope you get some good sleep effeneberg.

btw ..the links were always here at  testers wiki... we have to work on this duplication problem

---

### Post by ventrical on 2012-03-27
Mulitple tabs open to tester wiki, because of encrypted page , have to do a <resend>.

---

### Post by ventrical on 2012-03-27
> **effenberg0x0 said:**
> Thanks for fixing it. I'm beginning to see that, as you use the wiki a  lot, for many files, many edits, you begin to see weird things. And the  MoinMoin syntax is maddening. 

Thanks, it was a short deadline, as usual...By 28th, it's up to Dale and Graham to use it or not, integrally or partially in the team docs. 

I was out of home, away from PCs, when you changed it. As soon as I got back, I accessed the wiki to try to understand what was going on. And now I'm 100% sure there's definitely something wrong going on. Look at the attached screenshot. It doesn't show your edit in the page history! And I'm not the one that did that last change (it was you, of course). I have tested from two desktops, 2 laptops, the results are the same. Maybe it's something with my Launchpad account... no idea at this point.

[ATTACH]214988[/ATTACH]

Regards,
Effenberg

There is that funny thing with the moinmoin syntax, that if there is another user editing the page and they don't log out then , if the flag is set, moinmoin will send a warning to the new user trying to do an edit. if it is not flagged it will not send a warning, However, those pages will not refresh automatically and a resend has to be done in firefox. Not sure if this explains the anomoly. I';m still trying to get a handle on that moinmoin also :)

 You are doing a great job at organizing all of this effenberg.

---

### Post by jibel on 2012-03-27
Precise Beta 2 is scheduled next Thursday (Mar. 29th) and Beta 2 candidates are available for testing on the ISO tracker [http://iso.qa.ubuntu.com/ ]("http://iso.qa.ubuntu.com/")

Anyone can participate in ISO testing to ensure we have good test coverage. All you need is a Launchpad account to login on the tracker, a Beta 2 image available from [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com), a spare machine, a free partition or a virtual machine. At this stage, testing on hardware would be very much appreciated.
 
The procedures for testing ISO images and reporting results are explained on [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures) and test results are tracked on [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

  We are coordinating testing in #ubuntu-testing on freenode. Please, go  there often to see what others are testing or what need to be tested.
 
Thank you very much for your help and happy testing!

---

### Post by grahammechanical on 2012-03-27
A wise man once said: "As one grabbing hold of the ears of a dog is anyone passing by that is becoming furious at the quarrel that is not his."

This is not a quarrel, is it? No! Ok. Then I can ask:

Should not this be the link?

[http://iso.qa.ubuntu.com/qatracker/milestones/210/builds]("http://iso.qa.ubuntu.com/qatracker/milestones/210/builds")

I found out very early this morning that the images that I had downloaded and burned (from this very page) had been superseded and new versions were being linked to. And I could not post a report on the versions I had tested. I did not find any errors by the way.

I learned a lot while trying to share in this ISO testing sprint. It is a time for reflection, is it not?

Regards.

---

### Post by grahammechanical on 2012-03-27
Sorry. Some how I put in a duplicate post. I clicked submit and got advanced. So, I clicked submit again.

Perhaps the forum robot had a late night ISO testing also. :D

Sorry.

---

### Post by ventrical on 2012-03-27
> **grahammechanical said:**
> A wise man once said: "As one grabbing hold of the ears of a dog is anyone passing by that is becoming furious at the quarrel that is not his."

This is not a quarrel, is it? No! Ok. Then I can ask:

Should not this be the link?

[http://iso.qa.ubuntu.com/qatracker/milestones/210/builds](http://iso.qa.ubuntu.com/qatracker/milestones/210/builds)

I found out very early this morning that the images that I had downloaded and burned (from this very page) had been superseded and new versions were being linked to. And I could not post a report on the versions I had tested. I did not find any errors by the way.

I learned a lot while trying to share in this ISO testing sprint. It is a time for reflection, is it not?

Regards.

Meh ? I thinks you are right and I am going to go and grab a blanket and two pillows because I have no quarrel with no one ! :)


  Reflecting, I think it has been successful as a first run and also considering the time and that most of the volunteers are busy with other projects. The q&a sprint so far has been a class act thanks to you and our team captain, effenberg. Even if we brought attention to only just ONE bug it is all then done for the greater good of Ubuntu as a whole and for Linux for human beings, however, we may  also recognize that Canonical has to somehow pay for itself.. it has to create revenue to run these  monsterous load balancers and I can only wonder sometimes  as to how those devs pay for their usage and room and board.

Regards,

Ventrical

---

### Post by teeks99 on 2012-03-27
I'm trying to run one of the iso tests: [http://testcases.qa.ubuntu.com/Install/AlternateManual](http://testcases.qa.ubuntu.com/Install/AlternateManual)
 and I found something that I think might be a bug, but I'm not sure...and if so I wouldn't know how to file it
 when I'm near the end of the install, I am prompted with a screen that says "At the moment only the core of the system is installed...." then I'm presented with a list of things I can install...OpenSSH server, Mail server, Print server, Ubuntu desktop, or manual package selection
 this step wasn't listed in the instructions for this testcase, and it seems like it should have defaulted to "Ubuntu desktop"

I installed from a USB image (made with unetbootin) and when the unetbootin menu came up I chose "Default".  Is this the correct way to test the CD image?  Did this setup cause it to apply some other boot options that aren't usually given which could have caused the install menu to come up?

---

### Post by cariboo on 2012-03-27
Merged two threads on the same subject.

---

### Post by Doug S on 2012-03-27
> **grahammechanical said:**
> ...I found out very early this morning that the images that I had downloaded and burned (from this very page) had been superseded and new versions were being linked to. And I could not post a report on the versions I had tested. I did not find any errors by the way...

The same happended to me yesterday, however I still had the test reporting page open, so I didn't even know. There is a way to get back to the superceded pages and add or review information (I don't know if it adds value or gets looked at if superceded). Just "click" on "See removed and superceded buils too". Note however, that the filters do not work, so you will get everything. In the daily build phase, I found it overwhelming. See attached screen shots below.
 
Edit: Now I realize that the only reason I could still enter test results in a superceded case yesterday was because I had set "In Progress" for all the cases I was going to run. Today I did not do that and it was again superceded, and now I am not permitted to enter the results.

---

### Post by teeks99 on 2012-03-27
> **teeks99 said:**
> I'm trying to run one of the iso tests: [http://testcases.qa.ubuntu.com/Install/AlternateManual](http://testcases.qa.ubuntu.com/Install/AlternateManual)
 and I found something that I think might be a bug, but I'm not sure...and if so I wouldn't know how to file it
 when I'm near the end of the install, I am prompted with a screen that says "At the moment only the core of the system is installed...." then I'm presented with a list of things I can install...OpenSSH server, Mail server, Print server, Ubuntu desktop, or manual package selection
 this step wasn't listed in the instructions for this testcase, and it seems like it should have defaulted to "Ubuntu desktop"

I installed from a USB image (made with unetbootin) and when the unetbootin menu came up I chose "Default".  Is this the correct way to test the CD image?  Did this setup cause it to apply some other boot options that aren't usually given which could have caused the install menu to come up?

So I think that my problem was Unetbootin, I tried making the USB stick again with Startup Disk Creator (usb-creator-gtk) and it worked much better.

---

### Post by effenberg0x0 on 2012-03-27
> **Doug S said:**
> The same happended to me yesterday, however I still had the test reporting page open, so I didn't even know. There is a way to get back to the superceded pages and add or review information (I don't know if it adds value or gets looked at if superceded). Just "click" on "See removed and superceded buils too". Note however, that the filters do not work, so you will get everything. In the daily build phase, I found it overwhelming. See attached screen shots below.

First f all, thanks for contributing with testing Ubuntu

It's hard for us, as testers, to not have absolute certainty that the ISOs we're testing are definitive and won't by superseded in the middle of the testing process. Considering we have about 4 days to test, it definitely doesn't help. Reports of superseded releases are valid, as long as what you report is unrelated to what was updated. It should be triaged to verify. There's a lot to improve definitely...

Regards,
EFfenberg

---

### Post by balloons on 2012-03-27
just posting an update, verbatim from jibel -- this details bugs and fixes for today's images.

New builds of Precise Beta 2 are now available on the tracker. These images include the following changes:
 * set cdimage's OFFICIAL="Beta
 * [https://launchpad.net/ubuntu/+source/brltty/4.3-1ubuntu4](https://launchpad.net/ubuntu/+source/brltty/4.3-1ubuntu4) - fix for upgrades only; rebuild needed if we don't want out-of-date packages on images
 * [https://launchpad.net/ubuntu/+source/gtk+2.0/2.24.10-0ubuntu6](https://launchpad.net/ubuntu/+source/gtk+2.0/2.24.10-0ubuntu6) - fix for upgrades only; rebuild was needed to avoid out-of-date packages on images
 * [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963633](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963633) - CRITICAL,  blank screen.  has been worked around in compiz
  [https://launchpad.net/ubuntu/+source/compiz/1:0.9.7.2-0ubuntu4](https://launchpad.net/ubuntu/+source/compiz/1:0.9.7.2-0ubuntu4)
 * [https://launchpad.net/bugs/965390](https://launchpad.net/bugs/965390), dup of [https://launchpad.net/bugs/893548](https://launchpad.net/bugs/893548) [https://launchpad.net/ubuntu/+source/ubiquity/2.10.3](https://launchpad.net/ubuntu/+source/ubiquity/2.10.3)
 * [https://launchpad.net/ubuntu/+source/ubuntuone-client/2.99.91-0ubuntu2](https://launchpad.net/ubuntu/+source/ubuntuone-client/2.99.91-0ubuntu2) - security fix, remove accidental logging of user's proxy credentials
 * [https://launchpad.net/ubuntu/+source/unity/5.8.0-0ubuntu2-](https://launchpad.net/ubuntu/+source/unity/5.8.0-0ubuntu2-) cherry picked patch [https://launchpad.net/bugs/963718](https://launchpad.net/bugs/963718)
 * [https://launchpad.net/ubuntu/+source/gnome-keyring/3.2.2-2ubuntu2](https://launchpad.net/ubuntu/+source/gnome-keyring/3.2.2-2ubuntu2) (building in release, fix for Bug:964857)

---

### Post by teeks99 on 2012-03-27
Can someone explain how the beta release process works as far as which daily builds are shown on the iso.qa.ubuntu.com tracker?  

I was working along, and aparently a new build came out because everything got a line through it.  Does that mean that we need to go back and re-do all the same items we just did?  Does this happen every day?

---

### Post by cariboo on 2012-03-27
Iso images are rebuilt as needed during the iso testing period, there could be several rebuilds to fix bugs. I suggest running the same test cases, if you ran into any bugs, to see if the bugs have been fixed.

---

### Post by teeks99 on 2012-03-27
So is there anywhere that keeps track of what has been tested overall? Or which ones have errors that especially need testing?  Or is the plan just to test every ISO every day (I mean ideally I'm sure that would be best, but feasible?)

---

### Post by grahammechanical on 2012-03-27
> **teeks99 said:**
> I'm trying to run one of the iso tests: [http://testcases.qa.ubuntu.com/Install/AlternateManual](http://testcases.qa.ubuntu.com/Install/AlternateManual)
 and I found something that I think might be a bug, but I'm not sure...and if so I wouldn't know how to file it
 when I'm near the end of the install, I am prompted with a screen that says "At the moment only the core of the system is installed...." then I'm presented with a list of things I can install...OpenSSH server, Mail server, Print server, Ubuntu desktop, or manual package selection
 this step wasn't listed in the instructions for this testcase, and it seems like it should have defaulted to "Ubuntu desktop"

I installed from a USB image (made with unetbootin) and when the unetbootin menu came up I chose "Default".  Is this the correct way to test the CD image?  Did this setup cause it to apply some other boot options that aren't usually given which could have caused the install menu to come up?

What alternate ISO image were you testing? A server image?

It seems to me that the test cases are only relevant to testing the basic install process whether it is an alternate install or a live session or a standard install.

The test cases should not be be seen as step by step instructions for installing a particular version of Ubuntu, especially with the alternate installs.

You will find that the same test cases are used where necessary for the different versions. So, the test case that you were running is called dmi-001. That same test case is used for the alternate install of Ubuntu and also Xubuntu even though there is a big difference between the programs that each installs. The installer called Ubiquity is the same and that is what is being tested.

Regards.

---

### Post by cariboo on 2012-03-28
> **teeks99 said:**
> So is there anywhere that keeps track of what has been tested overall? Or which ones have errors that especially need testing?  Or is the plan just to test every ISO every day (I mean ideally I'm sure that would be best, but feasible?)

The [iso testing tracker]("http://iso.qa.ubuntu.com/qatracker/milestones/210/builds") shows what test cases have been run, and the bugs with bug numbers that have been encountered. The different builds, will lead up to the Beta 2 image that will be published on Thursday. Keep in mind, that Beta 2 is only a snapshot of the distribution as it is at that particular time, and as soon as the freeze is released more changes will be made, so the beta is only really valid on the day of release as things change leading up to the final release.

---

### Post by ronacc on 2012-03-28
cariboo907  What app are you using to upload your HDW profile ? I tried using checkbox-gtk and it seemed to send but the new profile didn't appear in my list only 2 from 4 years ago . I tried again and checkbox don't even try to send it although I can view it .

---

### Post by teeks99 on 2012-03-28
> **grahammechanical said:**
> What alternate ISO image were you testing? A server image?

It seems to me that the test cases are only relevant to testing the basic install process whether it is an alternate install or a live session or a standard install.

The test cases should not be be seen as step by step instructions for installing a particular version of Ubuntu, especially with the alternate installs.

You will find that the same test cases are used where necessary for the different versions. So, the test case that you were running is called dmi-001. That same test case is used for the alternate install of Ubuntu and also Xubuntu even though there is a big difference between the programs that each installs. The installer called Ubiquity is the same and that is what is being tested.

Regards.

It was the ubuntu-alternate-amd64, but the problem turned out to be with how unetbootin made my bootable USB.  When I used the official "Startup Disk Creator" the install progressed normally.

---

### Post by nm_geo on 2012-03-28
> **teeks99 said:**
> It was the ubuntu-alternate-amd64, but the problem turned out to be with how unetbootin made my bootable USB.  When I used the official "Startup Disk Creator" the install progressed normally.

I wondered about that teeks99.  I have been testing the Lubuntu-alternate-amd64 and have had no trouble with the encrypted full disk installation.  In fact I did one yesterday right after I noticed your report, and did another install last night after the latest respin. Anyway thanks for doing the testing you do.

---

### Post by teeks99 on 2012-03-28
> **cariboo907 said:**
> The [iso testing tracker]("http://iso.qa.ubuntu.com/qatracker/milestones/210/builds") shows what test cases have been run, and the bugs with bug numbers that have been encountered. The different builds, will lead up to the Beta 2 image that will be published on Thursday. Keep in mind, that Beta 2 is only a snapshot of the distribution as it is at that particular time, and as soon as the freeze is released more changes will be made, so the beta is only really valid on the day of release as things change leading up to the final release.

Right, but there are multiple daily builds in the run-up to beta 2 (or any other milestone).  Is there a cumulative list of these so we could look back and see if one particular iso has had failures across multiple builds...or if another has been fine?  

Since there are usually some configurations that don't get tested before everything is wiped out at the re-build time, is it possible that certian configurations are *never* getting tested?  It would be good if we could know if this was happening and possibly get focus on the few test cases that were missed.

---

### Post by cariboo on 2012-03-28
> **ronacc said:**
> cariboo907  What app are you using to upload your HDW profile ? I tried using checkbox-gtk and it seemed to send but the new profile didn't appear in my list only 2 from 4 years ago . I tried again and checkbox don't even try to send it although I can view it .

I just use System Testing (checkbox-gtk). Last week I ran it on both my Main system, and netbook, both profiles showed up with no problem encountered. Are you using the email address associated to your Launchpad account?

---

### Post by ventrical on 2012-03-28
> **ronacc said:**
> cariboo907  What app are you using to upload your HDW profile ? I tried using checkbox-gtk and it seemed to send but the new profile didn't appear in my list only 2 from 4 years ago . I tried again and checkbox don't even try to send it although I can view it .


 I get the notification that if you 'skip' a test that a report will not be included in 'Ubuntu Friendly'

  I can see the report on my PC but where are we suppossed to look?? On our launchpad accounts?

---

### Post by teeks99 on 2012-03-28
> **nm_geo said:**
> I wondered about that teeks99.  I have been testing the Lubuntu-alternate-amd64 and have had no trouble with the encrypted full disk installation.  In fact I did one yesterday right after I noticed your report, and did another install last night after the latest respin. Anyway thanks for doing the testing you do.

The problems I had with the lubuntu (and kubuntu) disk encryption were not related to the problem I had getting the USB disk created.  I ran into those after I switched to the "Startup Disk Creator".  I'm wondering if the [encrypted disk screen bug]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/966403") might be related to my graphics card.

---

### Post by cariboo on 2012-03-28
> **ventrical said:**
> I get the notification that if you 'skip' a test that a report will not be included in 'Ubuntu Friendly'

  I can see the report on my PC but where are we suppossed to look?? On our launchpad accounts?

Back on the first page of this thread, I posted the link, here it is again:

[https://launchpad.net/people/+me/+hwdb-submissions](https://launchpad.net/people/+me/+hwdb-submissions)

---

### Post by ronacc on 2012-03-28
> **cariboo907 said:**
> I just use System Testing (checkbox-gtk). Last week I ran it on both my Main system, and netbook, both profiles showed up with no problem encountered. Are you using the email address associated to your Launchpad account?

yes I can sign in and see the ones I uploaded in 2008 but the new one doesn't show up , I'm going to try completely removing and reinstalling both checkbox-gtk and FF and try again . The first time I did it it opened the report in FF and then sent it but attempts to redo it just opened a blank FF window and did nothing .

---

### Post by kansasnoob on 2012-03-28
Beware ................ RANT:

When I started iso-testing it was pretty easy to sign up and the explanations were very clear and simple. Over the past couple of dev-cycles things have become more and more complex. 

While there have been some improvements the negatives far outweigh the positives. I'm honestly considering dropping out of testing altogether at this point :(

Testing in itself has become more complex because the ubiquity devs added new features and removed old and popular features.

Obviously the number of testers has decreased, think I'm full of BS:

[http://ubuntu.5.n6.nabble.com/Testing-Precise-Pangolin-Beta2-td4662784.html](http://ubuntu.5.n6.nabble.com/Testing-Precise-Pangolin-Beta2-td4662784.html)

But rather than fix what's wrong some of us seem to think creating new additional layers of complexity to be the answer.

IMHO we need certain testers to test certain things, and we need an adequate number of those testers. But it needs to done within Ubuntu QA!

Otherwise people just end up banging their heads against the wall (or the keyboard) ](*,)

---

### Post by effenberg0x0 on 2012-03-28
> **kansasnoob said:**
> Beware ................ RANT:

When I started iso-testing it was pretty easy to sign up and the explanations were very clear and simple. Over the past couple of dev-cycles things have become more and more complex. 

While there have been some improvements the negatives far outweigh the positives. I'm honestly considering dropping out of testing altogether at this point :(

Testing in itself has become more complex because the ubiquity devs added new features and removed old and popular features.

Obviously the number of testers has decreased, think I'm full of BS:

[http://ubuntu.5.n6.nabble.com/Testing-Precise-Pangolin-Beta2-td4662784.html](http://ubuntu.5.n6.nabble.com/Testing-Precise-Pangolin-Beta2-td4662784.html)

But rather than fix what's wrong some of us seem to think creating new additional layers of complexity to be the answer.

IMHO we need certain testers to test certain things, and we need an adequate number of those testers. But it needs to done within Ubuntu QA!

Otherwise people just end up banging their heads against the wall (or the keyboard) ](*,)

Hi Kansasnoob,

The QA Weekly meeting starts at 17:00UTC. Can you join and express your opinion there? 
I personally got a little confused about this, didn't understand it:

> **kansasnoob said:**
> 
But rather than fix what's wrong some of us seem to think creating new additional layers of complexity to be the answer.

IMHO we need certain testers to test certain things, and we need an  adequate number of those testers. But it needs to done within Ubuntu QA!


**EDIT:** Actually the meeting was short and it's already over... But if you could mail or PM me, I'd really appreciate it.

Regards,
Effenberg

---

### Post by ventrical on 2012-03-28
> **kansasnoob said:**
> Beware ................ RANT:

When I started iso-testing it was pretty easy to sign up and the explanations were very clear and simple. Over the past couple of dev-cycles things have become more and more complex. 

While there have been some improvements the negatives far outweigh the positives. I'm honestly considering dropping out of testing altogether at this point :(

Testing in itself has become more complex because the ubiquity devs added new features and removed old and popular features.

Obviously the number of testers has decreased, think I'm full of BS:

[http://ubuntu.5.n6.nabble.com/Testing-Precise-Pangolin-Beta2-td4662784.html](http://ubuntu.5.n6.nabble.com/Testing-Precise-Pangolin-Beta2-td4662784.html)

But rather than fix what's wrong some of us seem to think creating new additional layers of complexity to be the answer.

IMHO we need certain testers to test certain things, and we need an adequate number of those testers. But it needs to done within Ubuntu QA!

Otherwise people just end up banging their heads against the wall (or the keyboard) ](*,)

@kansasnoob..

Thank you for writing this.  Actually .. it was a nightmare. Yesterday, after going through a barrage of a corrundum,sp> and *thinking I was actually logged on and testing in the q&a tracker I was , if fact , not testing nothing and ended up filing just one bug that now turns out to be a non-bug because that Lubuntu .ISO worked on all my other systems.. and then.. thismorning there is this e-mail telling me that I could  now log on to this link  for a one-time hook-up to the qa/tracker .. so I clicks , enters my password and it tells me wrong password. That did it for me.

  My thoughts... the Ubuntu .ISO testing process is tailored for specific tests to fit in with the new Ubuntu Friendly format (Ubuntu Authenticated no longer in progress). It makes it almost impossible for a noob or somebody not juiced into the heirerarchy to be able to test  these .ISOs. Therefore  good testing results  and reports from non members or noobs is considered nomenclature and those bug reports are not really taken seriously.

---

### Post by kansasnoob on 2012-03-28
> **effenberg0x0 said:**
> Hi Kansasnoob,

The QA Weekly meeting starts at 17:00UTC. Can you join and express your opinion there? 
I personally got a little confused about this, didn't understand it:



**EDIT:** Actually the meeting was short and it's already over... But if you could mail or PM me, I'd really appreciate it.

Regards,
Effenberg

When would I have time anyway :confused:

Look:

[ATTACH]215077[/ATTACH]

Oh goody we're discussing a silly countdown widget! Maybe we should be discussing countdown to doom!!!!!!!!

Yesterday it was reminders of another freaking IRC meeting! Meetings around testing time are about as welcome as coin slots on restroom doors!

Get real :mad:

---

### Post by effenberg0x0 on 2012-03-28
> **kansasnoob said:**
> When would I have time anyway :confused:

Look:

[ATTACH]215077[/ATTACH]

Oh goody we're discussing a silly countdown widget! Maybe we should be discussing countdown to doom!!!!!!!!

Yesterday it was reminders of another freaking IRC meeting! Meetings around testing time are about as welcome as coin slots on restroom doors!

Get real :mad:

Oh, I think I got just as angry when people were discussing the best blur method for the dash for 3 weeks. Or when my email got full of 100's of messages of people arguing if Unity was a Christian DE. I can understand you are mad.

Anyway... You are an experienced tester. What you have to say matters a lot.  Many people need guidance and QA itself is changing and needs feedback. I would really like to see that you're part of it, telling people what's wrong, what's right, where the problems are, what could be done to improve it. I understand time is always a problem for everyone. I've been sleeping 3 hours a day for a month or more and feel really tired and sick. 

When the current rush ends, would you consider taking some time to talk about these things? I can adapt to your schedule. 

Thanks,
Effenberg

---

### Post by ventrical on 2012-03-28
> **effenberg0x0 said:**
> Oh, I think I got just as angry when people were discussing the best blur method for the dash for 3 weeks. Or when my email got full of 100's of messages of people arguing if Unity was a Christian DE. I can understand you are mad.

Anyway... You are an experienced tester. What you have to say matters a lot.  Many people need guidance and QA itself is changing and needs feedback. I would really like to see that you're part of it, telling people what's wrong, what's right, where the problems are, what could be done to improve it. I understand time is always a problem for everyone. I've been sleeping 3 hours a day for a month or more and feel really tired and sick. 

When the current rush ends, would you consider taking some time to talk about these things? I can adapt to your schedule. 

Thanks,
Effenberg


Ummm.. effenberg .. was it not you warning me about 'burnout' a week or so ago ??

  Get some sleep amigo. geeesh..

---

### Post by Irihapeti on 2012-03-28
> **ventrical said:**
> Ummm.. effenberg .. was it not you warning me about 'burnout' a week or so ago ??

  Get some sleep amigo. geeesh..

+10!! -- or should it be +100???

Actually, I strongly suspect it may apply to all of us. We can kid ourselves that the work we are doing is more important than silly little things like rest and sleep and time with family, but it doesn't work that way in practice. These things have a way of catching up with us, and we don't get to choose exactly how it happens - it could be anything from a dose of the flu to a fatal accident.

And, no, I'm not making that last one up. It happened to a friend of a family member, after yet another late-night rehearsal that went on for too long.

I think I'll get away from the computer and go for a walk. Anyone like to join me? :)

---

### Post by effenberg0x0 on 2012-03-28
> **ventrical said:**
> Ummm.. effenberg .. was it not you warning me about 'burnout' a week or so ago ??

  Get some sleep amigo. geeesh..
Do as I say, not as I do :) 

> **Irihapeti said:**
> +10!! -- or should it be +100???

Actually, I strongly suspect it may apply to all of us. We can kid ourselves that the work we are doing is more important than silly little things like rest and sleep and time with family, but it doesn't work that way in practice. These things have a way of catching up with us, and we don't get to choose exactly how it happens - it could be anything from a dose of the flu to a fatal accident.

And, no, I'm not making that last one up. It happened to a friend of a family member, after yet another late-night rehearsal that went on for too long.

I think I'll get away from the computer and go for a walk. Anyone like to join me? :)
Funny coincidence, I just talked about that 3 minutes ago with Guitara! He was going for a walk too :)  Sorry about the accident you mentioned :\ I'm gonna take a break until Friday, enough Ubuntu for now.
I'll just send an email to the mailing list now, because it's important, but that's it :)

Regards,
Effenberg

---

### Post by arpanaut on 2012-03-28
> I think I'll get away from the computer and go for a walk. Anyone like to join me? :smile:That was the sentiment I was feeling yesterday, tired and frustrated with iso testing, I shut down my 'puters.
Went over to my golf club and played my first round of the season, had a great time with some friends and 
last night was one of the best night's sleep I've had in months!  I feel invigorated today.

Sometimes you just gotta step away from the keyboard and monitor to get some perspective and avoid ->](*,)

---

### Post by kansasnoob on 2012-03-28
> **effenberg0x0 said:**
> Oh, I think I got just as angry when people were discussing the best blur method for the dash for 3 weeks. Or when my email got full of 100's of messages of people arguing if Unity was a Christian DE. I can understand you are mad.

Anyway... You are an experienced tester. What you have to say matters a lot.  Many people need guidance and QA itself is changing and needs feedback. I would really like to see that you're part of it, telling people what's wrong, what's right, where the problems are, what could be done to improve it. I understand time is always a problem for everyone. I've been sleeping 3 hours a day for a month or more and feel really tired and sick. 

When the current rush ends, would you consider taking some time to talk about these things? I can adapt to your schedule. 

Thanks,
Effenberg

Right now I'm basically standing back, I already have partitions set up for upgrade testing (this will be the second round):

Ubuntu Lucid > Ubuntu Precise
Ubuntu Oneiric > Ubuntu Precise
Lubuntu Oneiric > Lubuntu Precise

And I may do a little lackadaisical iso-testing tomorrow, but not much! I'm just fried.

My personal opinion of this whole "team" thing is that 95% to 99% of any team does all the talking and the other 1% to 5% end up doing all the work, so I'm probably not the person to have on your team :redface:

Do-ers do ................... talk-ers talk, it's always been that way, always will be.

---

### Post by effenberg0x0 on 2012-03-28
> **kansasnoob said:**
> Right now I'm basically standing back, I already have partitions set up for upgrade testing (this will be the second round):

Ubuntu Lucid > Ubuntu Precise
Ubuntu Oneiric > Ubuntu Precise
Lubuntu Oneiric > Lubuntu Precise

And I may do a little lackadaisical iso-testing tomorrow, but not much! I'm just fried.

My personal opinion of this whole "team" thing is that 95% to 99% of any team does all the talking and the other 1% to 5% end up doing all the work, so I'm probably not the person to have on your team :redface:

Do-ers do ................... talk-ers talk, it's always been that way, always will be.

Ok, I'm sorry you feel that way.
Thanks anyway :)

Regards,
Effenberg

---

### Post by jerrylamos on 2012-03-28
Well, I've got 4 different types of test pc's up on ubuntu and lubuntu 12.04 Beta 2 candidate trying to do a bunch of things that people usually do (except games). Last bug was this afternoon with simple scan crash.

Generated several bugs. Some are getting fixed, some won't be. Maybe I post too much I don't know, it's whatever strikes me.  So I'm a "doer" and a "poster" but no I don't do team meetings.

Jerry

---

### Post by Irihapeti on 2012-03-28
> **effenberg0x0 said:**
> Do as I say, not as I do :) 


Funny coincidence, I just talked about that 3 minutes ago with Guitara! He was going for a walk too :)  Sorry about the accident you mentioned :\ I'm gonna take a break until Friday, enough Ubuntu for now.
I'll just send an email to the mailing list now, because it's important, but that's it :)

Regards,
Effenberg

That happened many years ago and I didn't know the person in question myself, but thanks anyway.

Both professionally and personally, I've see too many people push themselves too hard and end up paying some kind of price that was too high. Probably, those who take pride in their sense of responsibility and dedication are worst of all.

So, great idea that you recognise what's going on and are doing something about it.

Anyway, the walk was very enjoyable. Must remember to do it more often. :)

---

### Post by effenberg0x0 on 2012-03-28
> **jerrylamos said:**
> Well, I've got 4 different types of test pc's up on ubuntu and lubuntu 12.04 Beta 2 candidate trying to do a bunch of things that people usually do (except games). Last bug was this afternoon with simple scan crash.

Generated several bugs. Some are getting fixed, some won't be. Maybe I post too much I don't know, it's whatever strikes me.  So I'm a "doer" and a "poster" but no I don't do team meetings.

Jerry

Ok

Regards,
Effenberg

---

### Post by cariboo on 2012-03-28
> **Irihapeti said:**
> +10!! -- or should it be +100???

Actually, I strongly suspect it may apply to all of us. We can kid ourselves that the work we are doing is more important than silly little things like rest and sleep and time with family, but it doesn't work that way in practice. These things have a way of catching up with us, and we don't get to choose exactly how it happens - it could be anything from a dose of the flu to a fatal accident.

And, no, I'm not making that last one up. It happened to a friend of a family member, after yet another late-night rehearsal that went on for too long.

I think I'll get away from the computer and go for a walk. Anyone like to join me? :)

I just took the dog for a walk, and feel much better thanks for the suggestion. :)

---

### Post by ventrical on 2012-03-28
> **Irihapeti said:**
> +10!! -- or should it be +100???

Actually, I strongly suspect it may apply to all of us. We can kid ourselves that the work we are doing is more important than silly little things like rest and sleep and time with family, but it doesn't work that way in practice. These things have a way of catching up with us, and we don't get to choose exactly how it happens - it could be anything from a dose of the flu to a fatal accident.

And, no, I'm not making that last one up. It happened to a friend of a family member, after yet another late-night rehearsal that went on for too long.

I think I'll get away from the computer and go for a walk. Anyone like to join me? :)

  I always make sure to get my exercise in for sure ! Yesterday I had a visit at the denstists - one of those teeth cleaning things .. boy oh boy .. that just whooped me out .. but  I got a good rest after that.

  I am also retiring another PC that I have been working with , an older model ... so there will be some spring housecleaning to get done up here in Canada.

  I'll often just turn off  all my PCs .. completely .. for about 12 hours.. I got to.

 After a break there is always a renewed perspective.

thanks for reminding me to walk  :)

---

### Post by ventrical on 2012-03-28
> **effenberg0x0 said:**
> Do as I say, not as I do :) 

Regards,
Effenberg

Yes dad. :)

 hehehe

---

### Post by Irihapeti on 2012-03-29
> **cariboo907 said:**
> I just took the dog for a walk, and feel much better thanks for the suggestion. :)

And I bet the dog appreciates it, too. :)

---

### Post by ventrical on 2012-03-29
> **jerrylamos said:**
> Well, I've got 4 different types of test pc's up on ubuntu and lubuntu 12.04 Beta 2 candidate trying to do a bunch of things that people usually do (except games). Last bug was this afternoon with simple scan crash.

Generated several bugs. Some are getting fixed, some won't be. Maybe I post too much I don't know, it's whatever strikes me.  So I'm a "doer" and a "poster" but no I don't do team meetings.

Jerry

  I can appreciate that. Back in 1992,93, during my BBS years we used ot have these GTs (get togethers) or we would be online in  multiple  chats (before the internet). It was always good to hash stuff out at those meetings.  Things are different now.

---

### Post by ventrical on 2012-03-29
> **kansasnoob said:**
> Right now I'm basically standing back, I already have partitions set up for upgrade testing (this will be the second round):

Ubuntu Lucid > Ubuntu Precise
Ubuntu Oneiric > Ubuntu Precise
Lubuntu Oneiric > Lubuntu Precise

And I may do a little lackadaisical iso-testing tomorrow, but not much! I'm just fried.

My personal opinion of this whole "team" thing is that 95% to 99% of any team does all the talking and the other 1% to 5% end up doing all the work, so I'm probably not the person to have on your team :redface:

Do-ers do ................... talk-ers talk, it's always been that way, always will be.


   I have 5 towers all cracked open in front of me. Switching and swapping parts, memory whatever. I'm doing a lot of footwork about here, and I'm not belly aching about it. Joining a team and *sharing* our ideas is a lot of work .. it is the work of doers that get things done that nobody else wants to do. Yes.. the recognition might not be there like that q/a listing thing the  pumps up the hottest beta tester but a lot of that is hot air coming from a severely dysfunctional marketing machine .  The pulse of Ubuntu is here at the forums.  .  The last two days have shown that  this part of the Turing machine is , in some respects, severely strained .

So lets fix it ?

edit : I meant to say .. bah .. humbug ! :)

---

### Post by Irihapeti on 2012-03-29
So have I been doing the wrong thing, doing those tests on the QA site?

---

### Post by cariboo on 2012-03-29
> **Irihapeti said:**
> So have I been doing the wrong thing, doing those tests on the QA site?

Of course not, I've done the same as you, we do the easy stuff, and leave it up to the QA guys to compile all the data from the test cases, and hand the results off to the developers in order to get as many bugs as possible squashed.

---

### Post by ventrical on 2012-03-29
> **Irihapeti said:**
> So have I been doing the wrong thing, doing those tests on the QA site?

 I'm just...  counter- ranting ... ;)

my apologies...

---

### Post by Irihapeti on 2012-03-29
Just wondered. It wouldn't be the first time I'd thought I was doing something useful and it turned out not to be. :)

---

### Post by surja on 2012-03-29
Installed Ubuntu 12.04 on a Lenovo G570 (with Radeon and Intel switchable graphics). Most things works ok but I have a CDMA EVDO Capitel modem (Device ID 1c9e:9e00) which is not detected by this release. This modem has worked perfectly well with Ubuntu 10.10, 11.04 and 11.10. So i cannot configure it from the Network Manager.

---

### Post by ventrical on 2012-03-29
> **Irihapeti said:**
> Just wondered. It wouldn't be the first time I'd thought I was doing something useful and it turned out not to be. :)


Hopefully... HOPEFULLY ... I hope to gather the gold mine of data which exists here in the Precise Forums and also the past  beta forums like Oneiric Ocelot and Lucid and so on.  All of these comments .. all of this back and forth exchange, the sudo code work arounds and the non -official Q&A that goes on here is like a treasure chest of fine jewels.

  Iv'e started on this project with the U+1 wiki and I plan to keep working on it .. so far I've accomplished only a pittance ..   there is gold in them thar hills and I hope to dig it out !

btw .. do you belong to any teams  ??

---

### Post by Irihapeti on 2012-03-29
> **ventrical said:**
> Hopefully... HOPEFULLY ... I hope to gather the gold mine of data which exists here in the Precise Forums and also the past  beta forums like Oneiric Ocelot and Lucid and so on.  All of these comments .. all of this back and forth exchange, the sudo code work arounds and the non -official Q&A that goes on here is like a treasure chest of fine jewels.

  Iv'e started on this project with the U+1 wiki and I plan to keep working on it .. so far I've accomplished only a pittance ..   there is gold in them thar hills and I hope to dig it out !

btw .. do you belong to any teams  ??

No, I don't belong to any teams. I wondered about joining the U+1 team but figured that I didn't really fit the profile. I don't post much (don't have much to say, really) and very likely won't being doing much with QQ because I tend to stick to LTS.

---

### Post by grahammechanical on 2012-03-29
@Irihapeti

You fit the profile.

It is sensible to have a working OS that you do not mess with. For you that would be an LTS. For me, it is 11.10 at the moment then it will be 12.04 and so on.

At the present I also have 12.04 development branch on another partition. I test it as an ordinary user. I am using it right now.

If something breaks then a utility called Apport tells you about it and asks if you want to report it. If you do and if you have a Launchpad account then Apport will make it easy to report or add your comments to an existing report of that problem.

You do not have to join the U+1 team but you would be welcome. We hope to provide easy to understand information that will help an ordinary user become a serious tester. That is where I need help. I see myself as a casual but serious tester. Hopefully.

We also hope that the U+1 wiki will be a place where those who want to test can not only learn how to test but also what to test and when to test.

A person does not have to join the team to benefit from what is being put in the U+1 wiki. I do not think that any of the Ubuntu development teams see themselves as a small elite that is closed to others. That certainly is not the case with U+1 Testing team.

Regards.

---

### Post by jerrylamos on 2012-03-29
Installed 20120328 lubuntu on a thinkpad T40 and ubuntu on a atom N455 netbook.  

Went fine.  This is getting boring.  

I have 2 more installs to try, a tower and a notebook, maybe something will happen.

Jerry

---

### Post by balloons on 2012-03-29
> **jerrylamos said:**
> Installed 20120328 lubuntu on a thinkpad T40 and ubuntu on a atom N455 netbook.  

Went fine.  This is getting boring.  

I have 2 more installs to try, a tower and a notebook, maybe something will happen.

Jerry


Heh -- boring is good! We like it when things work. Final Images for beta2 are coming out today ;-)

---

### Post by jerrylamos on 2012-03-29
> **cariboo907 said:**
> I just use System Testing (checkbox-gtk). Last week I ran it on both my Main system, and netbook, both profiles showed up with no problem encountered. Are you using the email address associated to your Launchpad account?

Acer Aspire 5253 notebook.

You Tube sound O.K.

Sound applet test O.K.

checkbox-qt no sound at all.

Tru Sound applet again, still O.K.

Bug #968049

Jerry

---

### Post by Wiebelhaus on 2012-03-29
Things are going well for me, besides a few crashes with ati video drivers but ......it's ati video drivers.

---

### Post by jerrylamos on 2012-03-31
> **guitara said:**
> Heh -- boring is good! We like it when things work. Final Images for beta2 are coming out today ;-)

NOT boring on my Thinkpad R31 in contrast.  It's a triple boot with Lucid, Pangolin, and Lubuntu Pangolin A2.  It's 2005 vintage and has pae flag and will run generic-pae but lubuntu is a better fit, no compiz overhead.

Lubuntu Beta 2 CD Live install going fine until "copying files" ubiquity hung.  Wrote bug since CD live still working O.K.

Tried to reboot - oops, Ubiquity erases Grub2 files early in install, writes files back at end of install.  If install fails pc won't boot.  From a user viewpoint, that's a DUMB strategy.

Grub rescue came up, Tried all the instructions for grub rescue.  Seemed to go normally but no grub menu.  

Tried grub rescue CD.  It said it worked, but still wouldn't boot, no grub menu.

Booted Lucid CD live.  All files on the hard disk O.K. except for the partition being installed into of course.  Tried the instructions for re-installing grub.  Went normally still wouldn't boot, no grub menu.

Booted the Lubuntu Beta 2 CD Live tried to check the disk.  Screen flickered for quite a while then dropped into lubuntu live desktop so I don't know if it checked the disk or not or what it found.

Installed Lucid Lynx LTS onto one of the partitions.  THAT WORKED!  All the partitions except the install partition O.K.

Now installing samba, will copy over the network the 12.04 lubuntu Beta 2 and try booting the .iso directly from the hard drive.....

Spent  about 3 hours messing around so far.

Quite a mess.  I've installed Beta 2 four times on other pc's went as expected, not this time.

Jerry

BTW, on a late Acer Aspire 5253 notebook, every flag imaginable, 64 bit, ... with Windoze...7 on it, several times during 12.04 Alpha and Beta 1 grub2 would absolutely clobber boot totally all measures of recovery failed except installing Lucid Lynx into a spare partition or recover Windoze 7 with four full DVD's.  Ugh.  Solution: swap out hard drive let some other user complain to launchpad.  Much quicker on that notebook to swap hard drives than to try to get "precise" (?) to co-exist with Windoze...7.  For a while, I thought a USB hard drive with pangolin was the way to go until pangolin install destroyed main hard drive boot even though during install selected boot target on the USB.  Fix: unplug pangolin USB hard drive, install Lucid Lynx....

---

### Post by jerrylamos on 2012-03-31
Several tries on Thinkpad R31 to install Beta 2 with latest zsync and even apt-get update dist-upgrade.  Somewhere in copying files it gets a "broken pipe".  

In the middle of the attempts did a Lucid Lynx install clean no problems - to fix grub2 fouled up by the Beta 2's.

Drop back 20 and punt.  I'm doing upgrade of the lubuntu pangolin A which was at 3.2.0-5.  Merci beaucoup updates & new package installs.

715 updates, 2300 new packages, no problem at all (other than time for the massive update/upgrade) from 3.2.0-5 to 3.2.0-21.  Ubiquity Beta 2 install craps out after a couple minutes of copying files??  Launchpad bug #969620


Jerry

---

