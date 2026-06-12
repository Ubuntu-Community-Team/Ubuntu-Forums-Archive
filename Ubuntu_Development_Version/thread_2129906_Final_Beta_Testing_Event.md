---
title: "Final Beta Testing Event"
date: 2013-03-27
forum: Ubuntu Development Version
---

### Post by balloons on 2013-03-27
I wanted to cross-post this message here, because well, you all are invited! And I'd appreciate your feedback on the idea. Feel free to post here, the mailing list, or ping me if your interested in helping. Let's have a great image testing event next week!

------------------------------
[https://lists.ubuntu.com/archives/ubuntu-quality/2013-March/003388.html](https://lists.ubuntu.com/archives/ubuntu-quality/2013-March/003388.html)
------------------------------------------

I was hoping to get some feedback from everyone about us hosting an 
iso-testing event for the final beta images next week. I wanted to run 
the event a bit like we did the cadence testing livestream in the past 
(so so sad about the resulting quality of the upload :-() and encourage 
new users to get involved. I see the following needs:

Remake the isotest video on youtube (TOO LONG, and quality is not so nice :-()
Touch up (if needed) the isotest walkthrough on the wiki
Reach out to flavors, loco's, planet, greater community to encourage them to participate
People willing to join the hangout!

Who all would like to help on this? Any feedback or ideas on what you'd 
like to see? How does the following schedule look:

Tuesday April 2nd:
All day:
     people in #ubuntu-quality ready to answer questions
     people doing iso tests :-)
0800 UTC - 1200 UTC
     volunteers in #ubuntu-quality executing testcases and helping 
answer questions
     1000 UTC:
         g+ hangout with some community folks, doing testing
         live demos of doing an iso test -- including examples of doing 
more exotic tests like netboot, server, non-english, etc
1800 UTC - 2200 UTC
     volunteers in #ubuntu-quality executing testcases and helping 
answer questions
       2000 UTC:
     g+ hangout with some community folks, doing testing
     live demos of doing an iso test -- including examples of doing more 
exotic tests like netboot, server, non-english, etc

The idea is to get some folks who can make a specific timeslot commit to 
showing up so we can share that as a "good time" to be on IRC and get 
help. Of course, the whole day will be dedicated to image testing, so 
showing up anytime still works.

What does everyone think? Anyone willing to volunteer for a time slot? 
Anyone willing to help with the other needs listed above?

Let me know!

Thanks everyone

---

### Post by ventrical on 2013-03-27
In Canada, April 2nd comes after Easter Monday which is  a Holiday for some buisness aspects. (I have buisness income to prepare usually).  So it is not really a good date for me  , however, I will defintely drop in  if I can find a couple extra hours.

Regards,
Ventrical

---

### Post by balloons on 2013-03-28
Ventrical, so should we push it back a day to Weds? Anyone else see Easter conflicts? Definitely want to make sure everyone's schedule is free :-)

---

### Post by ventrical on 2013-03-28
> **guitara said:**
> Ventrical, so should we push it back a day to Weds? Anyone else see Easter conflicts? Definitely want to make sure everyone's schedule is free :-)


Wednesday is better for me. (April 3rd). Monday is a bank holiday (in Canada) so Tuesday will be busy. But don't change it just for me ! :)

---

### Post by balloons on 2013-03-29
After your feedback, the official date and time for this will be:

Tuesday April 2nd:
All day:
       people in #ubuntu-quality ready to answer questions
       people doing iso tests :-)
1800 UTC - 2200 UTC
    volunteers in #ubuntu-quality executing testcases and helping answer questions
      2000 UTC:
         g+ hangout with some community folks, doing testing
         live demos of doing an iso test -- including examples of doing
         more exotic tests like netboot, server, non-english, etc

We simply dropped the first time block.. Sorry, it's also Tuesday ventrical :-)

---

### Post by ventrical on 2013-03-29
> **guitara said:**
> After your feedback, the official date and time for this will be:

Tuesday April 2nd:
All day:
       people in #ubuntu-quality ready to answer questions
       people doing iso tests :-)
1800 UTC - 2200 UTC
    volunteers in #ubuntu-quality executing testcases and helping answer questions
      2000 UTC:
         g+ hangout with some community folks, doing testing
         live demos of doing an iso test -- including examples of doing
         more exotic tests like netboot, server, non-english, etc

We simply dropped the first time block.. Sorry, it's also Tuesday ventrical :-)

 Not a problem Nick.  I think I can squeeze in one .iso test .. even as old as I am ;)

---

### Post by ventrical on 2013-03-29
@guitara


 I zsynced the daily i386 iso yesterday and it is now working excpetionally well using standard install. Choosing F6 <nomodeset> seems to force raring to choose llvmpipe, but, up until now, it was difficult to get a standard install without using <nomodeset>.  I hope all of this bodes well for Tuesday's tests! :)

Regards,
Ventrical

---

### Post by ronacc on 2013-04-01
when will the daily current .iso freeze to the beta for testing ? I'll zsync after that so that I'm testing the right one , or will the "beta" .iso be somewhere else .

---

### Post by ManamiVixen on 2013-04-01
Ubuntu 13.04 hits beta on April 4th. It should be located on the cdimage site.

---

### Post by ronacc on 2013-04-01
> **ManamiVixen said:**
> Ubuntu 13.04 hits beta on April 4th. It should be located on the cdimage site.

I was refering to the .iso for the testing event , which is on april 2 .

---

### Post by ventrical on 2013-04-01
Here are the results you get today if you had zsynced the iso a couple of days ago.

```

dale@dale-desktop:~/Desktop$ zsync -i ./raring-desktop-i386.iso http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync
#################### 100.0% 229.1 kBps DONE     

reading seed file ./raring-desktop-i386.iso: ***********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read ./raring-desktop-i386.iso. Target 100.0% complete.      **************
reading seed file raring-desktop-i386.iso: *************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read raring-desktop-i386.iso. Target 100.0% complete.      **************
verifying download...checksum matches OK
used 830472192 local, fetched 0
dale@dale-desktop:~/Desktop$ 

```

so .. freeze!

---

### Post by ronacc on 2013-04-01
I zsync'd about 2 hrs ago .  Unfortunately the .iso ( amd64 ) will boot and run fine but wont install on my box , it hangs on the 2'nd screen  , both from a usb stick and from a dvd . I've had trouble with ubiquity all the way through raring . I think partman gets confused with all the drive's ( 6 ) , partitions  ( 11 not counting swaps )  and installs  7 including 1 windows 8 .

---

### Post by balloons on 2013-04-01
I asked the release folks earlier about where the images were/are.. Given the easter holiday, the builds haven't been posted yet. I've been assured we'll see them tomorrow for the event. Your right though ventrical, just zsync the daily and whatever new build comes out tomorrow will likely be VERY similar. I don't imagine much is going in today.

---

### Post by ventrical on 2013-04-01
@guitara

 Can you leave us some quick-links to the event so we can get right at it when it starts up?

Thanks.

---

### Post by ventrical on 2013-04-01
Actually it is live right now.

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/41090/testcases/1303/results](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/41090/testcases/1303/results)

---

### Post by ventrical on 2013-04-01
The raring-desktop-i386.iso is very clean on the usage test.

Anyone know of a better place to dump my hardware infor other than at the qa tracker details dialog box?

---

### Post by balloons on 2013-04-02
> **ventrical said:**
> @guitara

 Can you leave us some quick-links to the event so we can get right at it when it starts up?

Thanks.

ubuntuonair.com :-) There's a spanish event happening at 1800 UTC as well, with the english version happening as announced at 2000 UTC :-)

The milestone is now on the tracker, and the images should be up.

On the hardware question, I hope we'll have a better place for you to put that info soon (fingers crossed).. We had plans to utilize a hardware database for testing for a little while now. The team who is helping us is getting closer to having something ready for us to use. I imagine next cycle our results will be able to pair up with this database.

---

### Post by jerrylamos on 2013-04-02
Just installed amd64 .iso on this Acer Aspire One D255 Intel 64 bit.
Generally running just fine driving a 20" external 1600x900 monitor and running off a USB SSD.  Wireless keyboard and mouse.  1.6 gHz dual processors, 1G memory.
I'd say ubuntu generally running like it is intended to note I'm not a unity fan.

Couple persistent bugs I have launchpad bugs written on:

The live and first boot install runs the 1600x900 counterclockwise, sideways display.  Quite a crick in the neck and mouse coordination problem.  There is no "normal" orientation choice, only counterclockwise and clockwise rotation selections.  Solutions, first do 1024x768, change to normal orientatation, then apply.  Then carefully choose 1600x900 hopefully the normal choice will stay after the second apply.....
BTW, raring i386 no problem.  Only occurs on raring amd64.

On boot, hidden wireless network disconnects.  Select network which says it is out of range.  It is not.  Manually select the network, after a while discovers it already has the encryption key, and after some time connects.  Manual intervention required on every boot.  It's a network manager bug.  Pangolin runs fine same pc and network.  Android boots up in seconds connecting automatically same network.  Chromebook boots in seconds, same network, only have to enter the browser password.
This is a very long standing bug.  I conclude raring network manager as a policy is not connecting to the hidden network.  Pangolin, Android, Chromebook boot right up no problem, same network.

I'll keep udating and will try another install in a few days.

---

### Post by balloons on 2013-04-02
> **jerrylamos said:**
> Just installed amd64 .iso on this Acer Aspire One D255 Intel 64 bit.
Generally running just fine driving a 20" external 1600x900 monitor and running off a USB SSD.  Wireless keyboard and mouse.  1.6 gHz dual processors, 1G memory.
I'd say ubuntu generally running like it is intended to note I'm not a unity fan.

Couple persistent bugs I have launchpad bugs written on:

The live and first boot install runs the 1600x900 counterclockwise, sideways display.  Quite a crick in the neck and mouse coordination problem.  There is no "normal" orientation choice, only counterclockwise and clockwise rotation selections.  Solutions, first do 1024x768, change to normal orientatation, then apply.  Then carefully choose 1600x900 hopefully the normal choice will stay after the second apply.....
BTW, raring i386 no problem.  Only occurs on raring amd64.

On boot, hidden wireless network disconnects.  Select network which says it is out of range.  It is not.  Manually select the network, after a while discovers it already has the encryption key, and after some time connects.  Manual intervention required on every boot.  It's a network manager bug.  Pangolin runs fine same pc and network.  Android boots up in seconds connecting automatically same network.  Chromebook boots in seconds, same network, only have to enter the browser password.
This is a very long standing bug.  I conclude raring network manager as a policy is not connecting to the hidden network.  Pangolin, Android, Chromebook boot right up no problem, same network.

I'll keep udating and will try another install in a few days.

Thanks Jerry! If there is ever a bug you have that isn't getting attention, or you think I could help confirm let me know. Anything reported via the isotracker I try and follow-up on if possible, but I miss some :-) I'm especially curious on the amd64 only bug you mentioned -- what's the number? (arch specific bugs are always interesting!)

---

### Post by jerrylamos on 2013-04-03
> **guitara said:**
> Thanks Jerry! If there is ever a bug you have that isn't getting attention, or you think I could help confirm let me know. Anything reported via the isotracker I try and follow-up on if possible, but I miss some :-) I'm especially curious on the amd64 only bug you mentioned -- what's the number? (arch specific bugs are always interesting!)Launchpad bug #1160521 describes 1600x900 not having normal choice in both live raring and in the install, only counterclockwise and clockwise.  Systems settings displays because the default is mirror screens, so I need to un-select mirror, turn off the laptop display, and try to select the external monitor.  I've never had a screen that big ($90 sale).  So raring gets a 900x1600 resolution with the text going up and down, pretty hard for me to read.  The bug describes how to get a normal rotation 1600x900.  BTW, screen response and videos are just fine for 1.6 gHz 64 bit dual processors with raring.  In past I've tried isotracker a few times over the years, I didn't see any action on anything I entered.

---

### Post by cariboo on 2013-04-03
@jerrylamos , could your problem possibly be a setting on the monitor itself, on my BenQ 22" there is an onscreen menu setting to rotate the the view.

---

### Post by jerrylamos on 2013-04-03
raring i386 live & install has normal rotation for 1600x900.

raring amd64 has counterclockwise rotation for 1600x900 with no choice for normal.  So I get normal rotation as suggested in the bug.

?

---

### Post by jerrylamos on 2013-04-03
on Acer 5253 notebook, (has a 1280x1024 external monitor, no problem with rotation)

raring amd64 just installed and booted, got a crash.

Selected to report the crash. "The problem cannot be reported, it is not an ubuntu package. Please remove third party packages".

Continued to boot, saw a crash report in /var/crash, 
_usr_bin_compiz.1000.crash 
selected it, got the same reply "The problem cannot....not an ubuntu package.....please remove..."

Did ubuntu-bug compiz to create a launchpad bug.

Attached the crash report.

Interesting that "compiz" iis not an ubuntu package, and I'm supposed to remove it?

Launchpad Bug #1164157 

Not a showstopper, didn't even have to reboot, still running.

---

