---
title: "Lucid Lynx very buggy"
date: 2010-05-05
forum: Testimonials &amp; Experiences
---

### Post by j3zmund on 2010-05-05
Am I the only one who finds the new release to be very, very buggy? I've been using Ubuntu for years (heavily since 8.04LTS), and it's never been this annoying.

My first attempt at installation of 10.04LTS was the 64bit version for my Dell Vostro 1000, which has a 64bit AMD processor. I had some strange issues, and decided that I would install the 32bit version since I only have 2GB of RAM, and I'm not really getting any advantage from the 64bit capabilities.

Last night I completed the 32 bit install, and I am finding more bizarre errors than with the 64 bit version.

For example, the Ubuntu Software Center, which I used last night to add Compiz Settings Manager, The GIMP, and Planner now refuses to launch. I know I could work-around this by using apt-get, but this is one of the features that the techie-bloggers are touting as awesome. And, to be honest, when it works, it is pretty awesome.

Also, several other programs and utilities refuse to launch. The Main Menu Editor, Update Manager, and the Compiz Settings Manager (all of which worked last night) refuse to launch.  I've rebooted, thinking maybe sleeping all night caused some problems. I haven't tried every utility to see if this is a system wide issue, because things like Firefox launch just fine.

Very strange, and very sad. My Karmic Koala desktop works flawlessly (64 bit), and I'm glad that I have not upgraded just yet. I'm seriously considering re-installing Karmic on my laptop, because I just don't want to chase down this many bugs. I've got work to do.

None of the bloggers out there seem to have these issues, they are too busy falling all over themselves to write about the music store and gwibber. Anyone else having lots of strange issues?

---

### Post by Elfy on 2010-05-05
moved to testimonials

---

### Post by WinterRain on 2010-05-05
> **j3zmund said:**
> Am I the only one who finds the new release to be very, very buggy?

Probably not, but myself and many other people use it with no issues. Just look at all the threads in this section and you will see there are many people enjoying it. Try it again after 10.04.1 is released. Also, please report bugs so things may get fixed faster.

---

### Post by arsenic23 on 2010-05-05
I'm a little curious about what is causing your problem.  Have you tried running those program from the terminal to see what errors are holding you up?

I'd like to know what they are myself.

---

### Post by antenna on 2010-05-05
Sounds a bit like what happened to my system yesterday.  For some reason several of my applications stopped working, all I would get in the terminal is Segmentation Fault.  I tried a few more and realised all the ones that weren't working were python apps (sonata, update-manager, etc),  I reinstalled just python and that didn't help so I marked for reinstallation nearly every package containing the word 'python' in the name and it seemed to fix my problem.  I have no idea what caused the problem in the first place being as I hadn't installed anything or updated recently and everything had been working perfectly since install a few weeks ago.  

Anyway, your situation is probably unrelated but I don't think these problems are widespread.. more likely an unusual error or file corruption somehow rather than a problem with the release I guess.  

I would be interested in what is causing your problems though.

---

### Post by twright on 2010-05-05
> **j3zmund said:**
> Am I the only one who finds the new release to be very, very buggy? I've been using Ubuntu for years (heavily since 8.04LTS), and it's never been this annoying.

My first attempt at installation of 10.04LTS was the 64bit version for my Dell Vostro 1000, which has a 64bit AMD processor. I had some strange issues, and decided that I would install the 32bit version since I only have 2GB of RAM, and I'm not really getting any advantage from the 64bit capabilities.

Last night I completed the 32 bit install, and I am finding more bizarre errors than with the 64 bit version.

For example, the Ubuntu Software Center, which I used last night to add Compiz Settings Manager, The GIMP, and Planner now refuses to launch. I know I could work-around this by using apt-get, but this is one of the features that the techie-bloggers are touting as awesome. And, to be honest, when it works, it is pretty awesome.

Also, several other programs and utilities refuse to launch. The Main Menu Editor, Update Manager, and the Compiz Settings Manager (all of which worked last night) refuse to launch.  I've rebooted, thinking maybe sleeping all night caused some problems. I haven't tried every utility to see if this is a system wide issue, because things like Firefox launch just fine.

Very strange, and very sad. My Karmic Koala desktop works flawlessly (64 bit), and I'm glad that I have not upgraded just yet. I'm seriously considering re-installing Karmic on my laptop, because I just don't want to chase down this many bugs. I've got work to do.

None of the bloggers out there seem to have these issues, they are too busy falling all over themselves to write about the music store and gwibber. Anyone else having lots of strange issues?
Some of these issues could potentially be hardware relatedly - I second the suggestion of posting the output of attempting to launch them in terminal.

---

### Post by j3zmund on 2010-05-05
> **twright said:**
> Some of these issues could potentially be hardware relatedly - I second the suggestion of posting the output of attempting to launch them in terminal.

Since this laptop worked very well with 9.10, I have a hard time believing it to be a hardware problem (and running LiveCD confirms that I can use the programs that have stopped).

I would be happy to run the Ubuntu Software Center (for starters) from the command line, *but I'm having trouble finding (currently looking the online Ubuntu documentation) where the binary lives and what it is called. * **Never mind that line, found it, now just trying to get it to run.**

When I issue the command *exec software-center* the terminal window closes, and I don't get any output. I'm guessing I need to redirect error output to a file.

I attempted to use 2> to redirect error output to a file, but it just gives me a Permission Denied message (even if I sudo and try to put the file in my home directory).

I'm not a CLI expert, so if anyone could post a hint, I'd be grateful. I'd rather go back to having a fully functional system on 10.04 than going back to 9.10.

---

### Post by antenna on 2010-05-05
it's software-center

(edit: Hm aren't Canonical UK based.. what's with the spelling.)

---

### Post by j3zmund on 2010-05-05
> **antenna said:**
> it's software-center

(edit: Hm aren't Canonical UK based.. what's with the spelling.)

Huh? "Hm"? What is that? I may have some bad grammar above, but most of my spelling appears to be ok. I'm not sure what you're asking.

Trying to run the software-center from the CLI, but the terminal window just closes. As I added to my post above, I am having trouble getting the error output into a file.

Sorry to be a CLI newb, but that was a big part of the appeal for modern Ubuntu. Anyone have a tip for me? I'm currently looking up other options to get some output to share and find the source of the problem (no pun intended).

---

### Post by twright on 2010-05-05
> **antenna said:**
> it's software-center

(edit: Hm aren't Canonical UK based.. what's with the spelling.)

The name in the interface varies based on local but coders of the world seem to have standardized on US English.

---

### Post by twright on 2010-05-05
> **j3zmund said:**
> Huh? "Hm"? What is that? I may have some bad grammar above, but most of my spelling appears to be ok. I'm not sure what you're asking.

Trying to run the software-center from the CLI, but the terminal window just closes. As I added to my post above, I am having trouble getting the error output into a file.

Sorry to be a CLI newb, but that was a big part of the appeal for modern Ubuntu. Anyone have a tip for me? I'm currently looking up other options to get some output to share and find the source of the problem (no pun intended).

That is OK - these days the terminal is mainly for diagnostics and hackers (in the traditional sense). Are you only typing software-center (and nothing else)?

---

### Post by j3zmund on 2010-05-05
I was using the following command (and then added sudo, just in case) in Terminal:
*exec software-center*
*sudo exec software-center*

I just found the tool called "ubuntu-bug" and entered the following commmand:
*ubuntu-bug software-center*

Here is the output:
[I]Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 18, in <module>
    import gobject, gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
AttributeError: 'module' object has no attribute 'CAPI'
[/I]

As someone mentioned previously in this thread, python seems to be an issue. I'm going to look up 'CAPI' and see what that is. I'm not finding an answer that easily.

Update:
I forced a reinstall of python using apt-get. 

The Output from ubuntu-bug is the same. 

Could something in apport-gtk could be the issue? Debugging that output is definitely over my head. I have to get back to work, but I will check this thread later if anyone would like to give me a hint or help in the right direction.

Thanks in advance!

---

### Post by j3zmund on 2010-05-05
> **forestpiskie said:**
> moved to testimonials

This section is explicitly not for bug-reporting/support issues. Was my original post not specific enough?

It has turned into a troubleshooting issue. I went to report a bug, but they say to go the forums. Now I'm stuck in a non-support forum. 

Where should I turn?

---

### Post by twright on 2010-05-05
> **j3zmund said:**
> This section is explicitly not for bug-reporting/support issues. Was my original post not specific enough?

It has turned into a troubleshooting issue. I went to report a bug, but they say to go the forums. Now I'm stuck in a non-support forum. 

Where should I turn?

You were in the right forum - it is OK, we can still help you here.

> **j3zmund said:**
> I was using the following command (and then added sudo, just in case) in Terminal:
*exec software-center*
*sudo exec software-center*

I just found the tool called "ubuntu-bug" and entered the following commmand:
*ubuntu-bug software-center*

Here is the output:
[I]Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 18, in <module>
    import gobject, gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
AttributeError: 'module' object has no attribute 'CAPI'
[/I]

As someone mentioned previously in this thread, python seems to be an issue. I'm going to look up 'CAPI' and see what that is. I'm not finding an answer that easily.

Update:
I forced a reinstall of python using apt-get. 

The Output from ubuntu-bug is the same. 

Could something in apport-gtk could be the issue? Debugging that output is definitely over my head. I have to get back to work, but I will check this thread later if anyone would like to give me a hint or help in the right direction.

Thanks in advance!

You should get rid of the exec and just type software-center. Something definitely seems broken - did you do any updates before this? You might want to run your computer's BIOS's tests to see if this is a hard drive related data corruption issue.

---

### Post by j3zmund on 2010-05-05
As instructed, I entered simple "software-center" into the terminal. Here is the output (different that reported before using ubuntu-bug and exec):

> Traceback (most recent call last):
  File "/usr/bin/software-center", line 29, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
AttributeError: 'module' object has no attribute 'CAPI'


As far as updates go, I am sure I didn't use the Update Manager (which I told not to launch at startup, since I prefer to apt-get update && apt-get upgrade myself). I may have run the apt-get update last night before going to bed. If I could launch the Computer Janitor, I would go back to a fresh setup, but that won't launch either.


Updated:
I ran computer-janitor from the command line, and I thought I asked it to removed the cruft, but I'm not sure that it did anything (even though I did pick the options to remove all packages that were not considered original). I rebooted, but have the same issue with programs not launching. My BIOS says the drive is fine. I'm running TestDisk 6.11 from a Parted Magic live CD (posting this from my iMac in the meantime).


I'll be back, and report what I find.

Thanks again!

---

### Post by Shakz on 2010-05-05
Yep...My laptop is just now running 32bit Lucid. I could have stood to wait a bit longer but figured what the heck. It was running 64bit Lucid and like you said...damn buggy. Especially the flash. Yes I know blah blah not ubuntus fault...whatever..it didnt work right. 32bit Lucid seems OK for now. Fixed my boot screen and I am golden. Not many complaints bout the 32bit but I dont know where folks are getting this "Solid as a rock" stuff. I whole heartedly disagree. 

My desktop got rolled back last weekend to Karmic 64bit.....it was freezing up and all sorts of stuff I mean ALL sorts of problems. Buttons stopped working, Applications would not launch, it would sporadically puke on itself and the mouse would stop working...while the rest of the stuff kept running fine. Gnome do wouldnt pop up, some weird window would come up with gnome do some times and go away other. I dont use my desktop much but I let my nephew jam my laptop last weekend so I was forced to use it. I put up with all that crap for about 2 hrs and 4 reboots before I said **** on this and rolled it back. 

In short...no your not alone.

---

### Post by j3zmund on 2010-05-05
> **Shakz said:**
> Yep...My laptop is just now running 32bit Lucid. I could have stood to wait a bit longer but figured what the heck. It was running 64bit Lucid and like you said...damn buggy. Especially the flash. Yes I know blah blah not ubuntus fault...whatever..it didnt work right. 32bit Lucid seems OK for now. Fixed my boot screen and I am golden. Not many complaints bout the 32bit but I dont know where folks are getting this "Solid as a rock" stuff. I whole heartedly disagree. 

My desktop got rolled back last weekend to Karmic 64bit.....it was freezing up and all sorts of stuff I mean ALL sorts of problems. Buttons stopped working, Applications would not launch, it would sporadically puke on itself and the mouse would stop working...while the rest of the stuff kept running fine. Gnome do wouldnt pop up, some weird window would come up with gnome do some times and go away other. I dont use my desktop much but I let my nephew jam my laptop last weekend so I was forced to use it. I put up with all that crap for about 2 hrs and 4 reboots before I said **** on this and rolled it back. 

In short...no your not alone.

I would honestly like to find the culprit. I started with 64bit, and it was the Flash annoyance that drove me to install the 32 bit. Flash works great, but some other things broke.

I did install a few things from the Software Center, and one thing that is not from the SC (Dropbox). The list of utilities that won't launch is more-than-a-few items (including gdebi, which prevents me from installing other downloaded stuff). I actually have 2 test machines that are upgraded to 10.04. One was a Beta, then an RC, then upgraded to the final, and it appears to be fine. The other is a test server that I just upgraded from 9.10, and it also appears to be running fine.

Only my laptop seems to be the trouble-child, and it is the only clean install of the bunch.

Thankfully, I didn't upgrade my quad-core workstation just yet. Perhaps I'll wait for 10.04.1 as someone suggested earlier in this thread.

I am quick to dismiss the "it's your hardware" argument, because when I run from the LiveCD, everything is fine, software launches, etc. Maybe Dropbox's deb package is stepping on the feet of critical files? Or maybe something from the Software Center isn't working as intended. Or maybe my harddrive is corrupted (but so far, my utilities tell me this isn't true, including the harddisk notification built into 10.04.

As much fun as I have tracking down issues like this (I do IT support for a living, so I really do enjoy it), I'm likely to wipe it if I don't make progress this evening. Maybe Flash isn't that important, and I could live with the 64 bit version after all.

---

### Post by j3zmund on 2010-05-05
Test Disk 6.11 reports that my drive and my partitions are ok.

Computer Janitor won't fix it, so I must assume I did something stupid with the Software Center and/or Dropbox installation.

I do appreciate the time you've taken to try to help me out, but I am going to download a new ISO and start over with the laptop.

If the fresh installation goes badly, I will be back. Of course, this time, I won't install anything outside of the Software Center for a few days and see how it goes before trying to add extra software (maybe then if something goes wrong it will be easier to discover).

For now, so long and thanks for all the fish.

---

### Post by j3zmund on 2010-05-05
Deleted old partitions and reinstalled 32bit 10.04 from a freshly downloaded and verified ISO.

Old issues have disappeared, so that's good news. 

A new issue has appeared, however. Like I said before, I'm running a Dell Vostro 1000, which is a laptop.

When I removed the power adapter with a freshly charged battery, things work fine. When I plug it back in before the battery gets low enough to throw up warnings, I get a warning. Even if I click on "Cancel" the computer hibernates, despite the fact that there is still a 50% charge left in it. Interesting. This did not occur previously. Previously (even though other things didn't work correctly), the power management worked flawlessly.

I've changed the Power Management settings, hoping this will not happen in the future, but I wonder aloud if there is something I can do to let this installation know that I'm on a laptop, and that it needs to not freak out about plugging in the power adapter.

Should I go an open a new thread in the Laptop section of General Help to ask this question?

---

### Post by j3zmund on 2010-05-05
ACPID and kernel updates provided by Update Manager fixed the power issue.

I'm going to close this thread and mark it as SOLVED, but that is a bit misleading, since it was a complete wipe & reinstall that fixed it.

Once again, thanks to those who tried to help me.

*Updated to fix a typo*

---

### Post by retro89 on 2010-05-05
My desktop and laptop suffers an issue when shutting down it takes me to the login screen.
When I try to mount usb devices its says not authorized.
My sound card quit working under 10.04 on my desktop. It dont seem polished and has many bugs to be fixed. But on the other hand my atheros wifi works out of the box. Hopefully 10.04.1 will fix many issues that people are having.

---

### Post by j3zmund on 2010-05-06
> **retro89 said:**
> My desktop and laptop suffers an issue when shutting down it takes me to the login screen.
When I try to mount usb devices its says not authorized.
My sound card quit working under 10.04 on my desktop. It dont seem polished and has many bugs to be fixed. But on the other hand my atheros wifi works out of the box. Hopefully 10.04.1 will fix many issues that people are having.

Since my reinstall of a freshly downloaded ISO, and one round of updates, I've had fairly smooth sailing. My laptop did lock this morning after sleeping all night, but my iMac does that at least once a week, so I don't really mind. I'm sure if people have a clear way to report bugs, they will get fixed.

I do take issue with the way bug reporting works. It should be very easy, but if you search for bug reporting, they tell you to go to the forums. I'm sure they don't want repeat reports about known issues, but some folks may never find what they need, and others may have new bugs that never get reported.

Perhaps a bug reporting tool that will tell people "we've received this report before, we are working on a solution" or something similar would be helpful. Bugs are a fact of life on every platform, I certainly wouldn't expect a brand-spanking new release to be perfect (software is made by people, after all).

---

### Post by mbuller10 on 2010-05-13
I had lots of sound skipping so I'm rolling back, its just to early to start using a brand new release, they're always buggy

---

### Post by WinterRain on 2010-05-13
> **mbuller10 said:**
> I had lots of sound skipping so I'm rolling back, its just to early to start using a brand new release, they're always buggy

Check back after 10.04.1 comes out. 

It's only too early to start using a brand new release if you are one of the unlucky few. For most people, it's not a problem.

---

### Post by Ms_Angel_D on 2010-05-13
j3zmund, thanks for your feedback.

I'm going to close this thread, as this is not the support section of the forums, if you need support please utilize the proper sections and begin a new thread.

Thank you all for participating.

---

