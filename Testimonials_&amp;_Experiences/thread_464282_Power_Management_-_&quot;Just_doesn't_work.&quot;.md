---
title: "Power Management - &quot;Just doesn't work.&quot;"
date: 2007-06-04
forum: Testimonials &amp; Experiences
---

### Post by Talon2 on 2007-06-04
I'm curious if others are having any success with power management while using Fiesty.

I moved to Ubuntu with Dapper.  Suspend and resume worked reasonbly well on the systems I support.  With Fiesty not a single system I support has usable suspend, hibernate or resume.  There are additional related problems such as USB not waking from suspend.

For weeks in my spare time I've search the forums, launchpad and the net for possible solutions.  There are some reported solutions that involved uninstalling this and installing that but I haven't found time to dive into these solutions.

Does power management fully work for anyone?  For me Fiesty has been a disaster as far as power mangement goes.

---

### Post by Sunflower1970 on 2007-06-04
I had trouble with Feisty...so I downgraded back to Edgy on my laptop. Works like a charm. I'm going to keep Edgy around for a while until something is either fixed in Feisty or it's been fixed in Gutsy.

Some people were able to add a patch to the kernel? I think?  (Suspend2 I think it's called) But that meant recompiling a kernel, and I'm not that brave (or advanced in my Linux knowledge) to be able to do so at this time....

---

### Post by christhemonkey on 2007-06-04
Power Management has never worked on any ubuntu OS on any pc that i have used.

Then again, even if it did work, i wouldnt use it.
Tend to j ust leave my pcs on, and if they are not in use then they get switched off properly.

---

### Post by Bluecircle on 2007-06-04
Hibernate and suspend work perfectly for me. I guess I'm just lucky.

---

### Post by Geekkit on 2007-06-04
Power management on my tower seems to work. At 12 minutes the screen saver kicks in (but just don't use the Braid screen saver with OpenGL - it crashes the desktop). At 40 minutes the monitor shuts off. So yes, it works for me.

---

### Post by Talon2 on 2007-06-05
> **Geekkit said:**
> Power management on my tower seems to work. At 12 minutes the screen saver kicks in (but just don't use the Braid screen saver with OpenGL - it crashes the desktop). At 40 minutes the monitor shuts off. So yes, it works for me.

How about suspend and hibernate?

---

### Post by 3rdalbum on 2007-06-05
On my computer, suspend worked under Dapper, but not Hibernate. Now, on Feisty, both work.

---

### Post by Geekkit on 2007-06-05
> **Talon2 said:**
> How about suspend and hibernate?

Sorry, I haven't tried these particular options.

---

### Post by Talon2 on 2007-06-06
> **Geekkit said:**
> Sorry, I haven't tried these particular options.

If you were to try them I wouldn't give odds on them working right.

I just went to lauchpad.net and searched open Ubuntu bugs for the word "suspend".  How many hits?

977

Prior to Fiesty suspend and hibernate worked acceptably on my systems.  Something happened with Fiesty.

A while back I decided to investigate the details...possibly even come up with a patch or two to help out.  I've coded in C though I'm a little rusty and need to get more familiar with the platform.  What I found was more complicated than anything I could imagine.  It isn't obvious to me how power mangement can be maintained.

It sure looks to me like power management needs a good look and a big overhaul.

---

### Post by meng on 2007-06-06
Power management, both suspend and resume, work great for me using Feisty and a notebook from madtux. (Intel graphics card of course)

---

### Post by eustace on 2007-06-14
I have mixed feelings about power management in Feisty. On the one hand, this is the first version of Ubuntu that does suspend/hibernate on my HP laptop (with Edgy it didn't work at all). On the other hand, these features work extremely unreliably. 

1 of 3 times my laptop would just freeze on resume, and if I leave it suspended for a few hours, it would most probably not resume but perform normal boot. Also, the gnome-session would occasionally crash on resume and I have to log in again. All of this makes suspend/hibernate almost unusable for me.

That is not to say that power management is completely broken, it just doesn't support all hardware equally well. On two other laptops that I have access to, running Edgy and Feisty, the power management works pretty much OK.

---

### Post by nymphaeles on 2007-06-14
Power management doesn't work for my Dell XPS M1210.  The laptop battery depleted in about 1:45 hours (lasts about 3 to 3:30 with XP or Vista due to Power Management quickly shut down HD and screen, and reduce CPU power consumption when there is no activities.  In addition to that, APCI seems to cause my laptop to pause for a good 1-1.5 min during boot up as I posted in another thread.  Hibernation/Suspension doesn't work at all with this laptop, as I close the laptop screen, it will light up the keyboard in the dark all night long.
Power management also doesn't work for some other models I have tested including a Dell Dimension 8200 desktop, Dell Precision 530 desktop, Dell Dimension 4100, Dell Precision 610, and an IBM workstation 6443.  The monitors do go blank; however, I believe that is the feature of the monitor, not from power management.

---

### Post by erfunath on 2007-06-16
Neither suspend nor hibernate work for me. Suspend closes down well and leaves the power light flashing, but on resume the screen doesn't turn back on. My hardware returns to normal functionality (I think), but I can't see or do anything, so it's useless. Kind of frustrating for a student who takes this laptop from class to class and needs a quick boot-up. It's alright, though, because Ubuntu is SO much faster and more reliable than Windows. At least in my experience for my programs. I haven't been able to find any fixes to attempt for this problem, so if any of you have any ideas please tell me! Thanks. :)

---

### Post by Talon2 on 2007-06-17
> **erfunath said:**
> Neither suspend nor hibernate work for me. Suspend closes down well and leaves the power light flashing, but on resume the screen doesn't turn back on. My hardware returns to normal functionality (I think), but I can't see or do anything, so it's useless. Kind of frustrating for a student who takes this laptop from class to class and needs a quick boot-up. It's alright, though, because Ubuntu is SO much faster and more reliable than Windows. At least in my experience for my programs. I haven't been able to find any fixes to attempt for this problem, so if any of you have any ideas please tell me! Thanks. :)

Troubleshooting power management is difficult.  Either there is a lack of useful information or I haven't found it.

There are many many bugs in launchpad related to power management.  Some bugs do have information about some work arounds for specific situations.  Here is a url showing bugs that have the word suspend:

[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=suspend&orderby=-datecreated&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=suspend&orderby=-datecreated&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Here is a url to a bug that sounds similar to what you have:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96240](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96240)

---

### Post by OzzyFrank on 2007-06-18
They both work for me in Feisty (last time I checked!). What I've been waiting for is a Power Management app that is AT LEAST as useful as that in Windows. I mean, I never use Suspend or Hibernate, but I would like to be able to set my hard drives to power down when not in use, and perhaps to be able to set the monitor's power down there too (instead of having to go to another app). Oh, I would use Suspend and/or Hibernate if I had the option of setting it for a specified amount of inactivity, as sometimes I'll set Windows to hibernate after tasks have finished. Would love to know of an app that could do this for me in Ubuntu!

---

### Post by Xizorbg on 2007-08-29
Hello-

I had some horrible crashes after using power managament in my 64bit Ubuntu Feisty on my Asus A8V.  My system no longer boots.  It will boot the kernel but then just a black screen with the HD light on.  Last time this happened I had to reinstall Feisty.  I would like to avoid this.  Using the rescue function on my Alternate install disk does not fix it.  Any ideas?

Thanks,
X

---

### Post by ticopelp on 2007-08-29
I have Ubuntu installed on a 15" Powerbook and an old Dell... the Dell is pretty sturdy as far as coming back from suspend, but the Mac is a complete crap shoot, every time. Nothing I've tried works. I've just learned to live with it, reluctantly.

---

### Post by mostwanted on 2007-08-30
Suspend doesn't work for me when I use Compiz, but it does when I use Metacity as my window manager. Probably some weird composite-X errors.

---

### Post by transatlant1c on 2007-09-16
I'm not totally sure about this one.. But you could all try this [http://www.getdeb.net/category.php?id=11]("http://www.getdeb.net/category.php?id=11")

It's a few slots down called 'GFreqlet'. It seems to work for me.. Which is good seeing as I have a laptop like a few other people here.. What do you all think?

---

