---
title: "Trash the display"
date: 2010-03-24
forum: The Cafe
---

### Post by tkoco on 2010-03-24
I am a long time user of Linux, in general. One item, which will anger me faster than anything else in a Linux distro, is when my nicely working system gets trashed by a supposedly good update. Such an event just happened this morning. I will eventually figure out what went wrong and fix it. But, IMHO, I should not have to spend enormous amount of time performing forensics on my system just because someone did not their homework before releasing an update.

---

### Post by red_Marvin on 2010-03-24
One way to avoid this would be to not update right away, but wait a few days and then check the forum to see if others have had problems with the update. However the enormous amount of time you spend on computer forensics is nothing compared to the time spent by thousands of developers in order to give you something completely free of charge, it is not a case of doing ones homework here.
If you want to help out and make sure that these glitches happens as seldom as possible, please, when you have identified the problem file a bug report, or add your info if it is already existent.

---

### Post by madjr on 2010-03-24
yeap this a big problem

anyone has a **fail-proof** way to backup system files before updating and restoring in case of breakage?

any program that will do this for you?

i really dont like reinstalling from scratch, because of 1 BAD update ;/

---

### Post by themarker0 on 2010-03-24
> **madjr said:**
> yeap this a big problem

anyone has a **fail-proof** way to backup system files before updating and restoring in case of breakage?

any program that will do this for you?

i really dont like reinstalling from scratch, because of 1 BAD update ;/

Buy a cloning program. Close before every update. I know people paranoid enough to do so. Works well for them. Most can create an image file, and clone to a dvd, while cloning to a backup HDD.

---

### Post by cariboo on 2010-03-24
Why buy a clone program when there are many free alternatives available. [Clonezilla]("http://www.clonezilla.org/") and [Remastersys]("http://www.geekconnection.org/remastersys/") are two just off the top of my head.

---

### Post by Wee_Guy on 2010-03-24
I use Clonezilla to create images of my drives, so if/when anything messes up majorly I can write the image back on the drive.

It is annoying though, how unreliable Ubuntu can be. If Ubuntu wants to shake off the 'geeky' connotations that surround Linux, the best way to do so would be for people to be able use a system out of the box. No farting around installing X or editing config files  to get  Y working properly, or wondering why features otherwise taken for granted (ie: Suspend) simply will not work, even after trying different solutions. I can appreciate how difficult it would be to get the majority of systems working out of the box, but the less 'geeky' type that Canonical seem to be increasingly targeting don't care for using the terminal, and if they find themselves told that they have to dig around system files just to try to fix stuff, no amount of prettiness or fastness will stop them from diving back to the safety of an operating system that they *know* will work.
I understand how the user interface is important, but small, insignificant issues like boot time and the location of window control buttons really only matter if the system actually works first, which is not always the case.

Having said that, thanks to all the developers and people on here helping fix stuff :D

---

### Post by swoll1980 on 2010-03-24
Alot of times it's caused by installing NVIDIA drivers from outside of the repositories. if this is the case it's easy to fix. What happens is the new kernel you get in the update doesn't contain the driver anymore. Installing the drivers from the repos will insure that the module gets transfered to the new kernel.

---

### Post by tkoco on 2010-03-25
Thanks everyone for the good comments. Yeah, it's an Nvidia problem. The HD is cloned so restoring won't be an issue. Only thing is that after restoring, you won't be 100% sure as to which update item did the dirty deed and won't be able to feedback good info to the developers.

---

### Post by swoll1980 on 2010-03-25
> **tkoco said:**
> Thanks everyone for the good comments. Yeah, it's an Nvidia problem. The HD is cloned so restoring won't be an issue. Only thing is that after restoring, you won't be 100% sure as to which update item did the dirty deed and won't be able to feedback good info to the developers.

Install the driver from the repos, and it won't break when you get a kernel upgrade. The kernel update is the dirty deed you speak of.

---

### Post by themarker0 on 2010-03-25
> **cariboo907 said:**
> Why buy a clone program when there are many free alternatives available. [Clonezilla]("http://www.clonezilla.org/") and [Remastersys]("http://www.geekconnection.org/remastersys/") are two just off the top of my head.

I've had little success with both sadly. And when it comes to someone else's data i can't afford to rely on something without a warranty or garrantee.

---

### Post by swoll1980 on 2010-03-25
> **themarker0 said:**
> I've had little success with both sadly. And when it comes to someone else's data i can't afford to rely on something without a warranty or garrantee.

Clonezilla is awesome sauce.

---

### Post by the yawner on 2010-03-25
Hmm... So. The limited number of developers should test out their updates on **all possible scenarios** before rolling it out to us? And by all, it would include every hardware combination, or software (i.e. drivers et al), or hardware and software. Why yes, that is very much feasible. Ubuntu should do that. Hrm...

---

### Post by Crunchy the Headcrab on 2010-03-25
> **tkoco said:**
> Thanks everyone for the good comments. Yeah, it's an Nvidia problem. The HD is cloned so restoring won't be an issue. Only thing is that after restoring, you won't be 100% sure as to which update item did the dirty deed and won't be able to feedback good info to the developers.
You don't need to rewrite the whole drive, just run the nvidia installer again and you should be good to go.  It should be the same process you used to install it in the first place.

---

### Post by swoll1980 on 2010-03-25
> **Crunchy the Headcrab said:**
> You don't need to rewrite the whole drive, just run the nvidia installer again and you should be good to go.  It should be the same process you used to install it in the first place.

I think he's scurd of the CLI.

---

### Post by Crunchy the Headcrab on 2010-03-25
Oh.  I assumed he got his driver from nvidia.com since it borked.  Last time I used drivers from there you had to install them using the cli.

---

### Post by swoll1980 on 2010-03-25
> **Crunchy the Headcrab said:**
> Oh.  I assumed he got his driver from nvidia.com since it borked.  Last time I used drivers from there you had to install them using the cli.

There's a program called envy that does it for you. or maybe he doesn't know how to ```
get
``` stuff

---

### Post by Mark Phelps on 2010-03-26
Ubuntu could easily solve such problems if it would only do ONE THING that the developers have steadfastly refused to provide in every single release -- provide an easy way to roll-back driver or other such updates.

MS has been doing this with System Restore for YEARS!

For this to work, it would need to have the capability to:
1) Automatically save off what is going to be changed -- probably to a folder
2) Apply the changes
3) If the changes don't work, or trash the display, or other such problem, provide a way to boot into a console and run a "restore" command to back out the last set of changes (basically, take all the files that were overwritten, , overwrite THEM with the copy that was saved prior to the update, and remove any new files that were added).

And a really useful extension to this would be the ability to roll-back a version update -- something sorely needed by the folks that install Betas on their system only to then find out that there is no easy way to "go back" to what they had before.

OH, and please don't preach to me about backups -- I already do that.  I'm looking for a solution for the folks that do NOT do backups.

---

