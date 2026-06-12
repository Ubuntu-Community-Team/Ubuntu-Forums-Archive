---
title: "[SOLVED] Update speed: XP vs. Gutsy"
date: 2008-07-17
forum: Windows
---

### Post by bilijoe on 2008-07-17
I'm not sure if this is where I should be with this, but I'm hoping someone can satisfy my curiosity.

Some time ago, I did a fresh XP install for a friend.  After finishing with the install CD, and the Drivers and Software CD, I went to the Windows Update site, and ran the scan.  The site recommended some huge number of updates, 160 seems to stick in my mind.  His machine wasn't new, and neither were his installation disks, so it seemed like a reasonable number, and we told the system to go ahead and install them.  ALMOST THREE HOURS!  Good God!  By then, we had sopped up so many martinis we had no idea what to do next--so we went to sleep on the floor.

A while back, I did a fresh install of Ubuntu 7.10 for a friend.  The CD I had wasn't exactly new either, so when the update manager popped up and recommended 220 updates, I wasn't too surprised.  I clicked on install, and suggested we make a pitcher of martinis (I like martinis).  We did, but when we got back to his den (5 minutes? 10? Maybe 15?)  Ubuntu had finished installing all 220 updates.  And there was no message telling us that we needed to reboot!  Wow!  I'd been using Ubuntu for some time by then, and was already impressed, and a dedicated fan and self-appointed ambassador.  Well, we couldn't let a perfectly good pitcher of martinis go to waste, so we spent several hours surfing the internet, and adding a few things to his new install.  He was blown away (had been a Windows user, ya see).  I spent that night on his floor.

So, my question is...  What is so different about Windows and Ubuntu (or their update engines) that makes one take hours to do roughly the same task the other does in only minutes?  I know Ubuntu has a far superior design (I've heard that, in the strict sense, Windows has no design at all), but Holy Moses!  Almost three hours, compared to less than 20 minutes!  What's wrong with this picture?  I'm a retired programmer of forensic software utilities.  My programs launched from DOS, and then took over virtually all the administrative functions of whatever OS had created the file system(s) found on the disk under investigation--Windows (9x through NT), OS2, Mac OS, Unix, Linux, CP/M (any of you remember that one?), etc.--I know what operating systems do (well, a significant part of what they do), and I can't, for the life of me, get my head around 3 hours vs 10 or 15 minutes.:confused:  Does anyone know what's going on here?  What explains this nearly order of magnitude difference in the time it takes these programs to install roughly the same number of updates (Windows actually installed only about 2/3rds as many updates as Ubuntu did).

This is just curiosity speaking.  I'm not looking for ammunition to bash Windows with.  Windows comes out of the box with an ample supply of that.  (Sorry, I guess that was a little bash-like itself.)  I'll get along just fine, if I never figure this out, but my curiosity is certainly piqued, and would like to be satisfied.  So, if any of you out there knows the straight scoop on this, please, let me know.

---

### Post by dnairb on 2008-07-17
IIRC Windows will create a restore point before installing each update, which increases the time required.

Also, Ubuntu will upgrade individual files (e.g. libraries), rather than whole applications.

---

### Post by pmlxuser on 2008-07-17
windows would like you to pay more for you to use it
->CD cost, office cost, Antivirus cost$
->connection fee
->time
->Electricity
->EVRYTHING

Ubuntu is free, it tries to make things as free as possible :)

---

### Post by lisati on 2008-07-17
Ubuntu has an advantage: you can cancel the download of the updates and come back to them later if you need the bandwidth for your connection. I'm not aware of a similar option with Windows.

---

### Post by pmlxuser on 2008-07-17
windows would like you to pay more for you to use it
->CD cost, office cost, Antivirus cost$
->connection fee
->time
->Electricity
->EVRYTHING

Ubuntu is free, it tries to make things as free as possible :)

SORRY I CLICKED TWICE

---

### Post by peterbrewer on 2008-07-17
Could be related to the size of updates, Linux tends to have the architecture of lots of small programs which doing specific tasks very well, Windows on the other hand seems to bundle lots of things into a single piece of software.  Therefore the Ubuntu updates may have been lots of small updates, where as the Windows updates were lots of major updates.

---

### Post by ilrudie on 2008-07-17
Could also be that M$ doesn't have enough bandwidth to pass out all the update files windows machines all over the world are trying to get.  This could be related to needing larger files for updates as mentioned above, more windows users or just being too cheep to get the bandwidth your paying customers need.  Maybe all of the above.

---

### Post by Jim! on 2008-07-17
It's likely that the updates for Ubuntu were smaller in file size then the Windows updates, so even though there were more they downloaded and installed quicker. Although I have to add that when I was dual-booting UBuntu and XP my downloads were averaging 60kb/s faster in Ubuntu compared to XP, I suspect that Ubuntu got along with my modem better then Windows did;)

EDIT: Nice little add-ins there BTW, "I spent that night on his floor." Awesome!:D

---

### Post by CrazyArcher on 2008-07-17
> **Jim! said:**
> Although I have to add that when I was dual-booting UBuntu and XP my downloads were averaging 60kb/s faster in Ubuntu compared to XP, I suspect that Ubuntu got along with my modem better then Windows did;)

It has a lot to do with the load on update servers. Think about half of the world downloading updates from MS servers and a much smaller fraction of people downloading them from Ubuntu repos.

---

### Post by Newuser1111 on 2008-07-21
5/10 Minutes? 
I got 14 Hours on Ubuntu 7.04(That was at 80kb/s). But it really only took a few days because of stopping it sometimes to shutdown the computer.
But I don't really think that's long.

On Windows,
I really don't know. Except that it was 52 updates.

---

### Post by bilijoe on 2008-07-21
> **Newuser1111 said:**
> 5/10 Minutes? 
I got 14 Hours on Ubuntu 7.04(That was at 80kb/s). But it really only took a few days because of stopping it sometimes to shutdown the computer.
But I don't really think that's long.

On Windows,
I really don't know. Except that it was 52 updates. I'm sorry, do I understand you to be saying that it took ***14 hours ***to download and install the initial set of upgrades, following a fresh install?  Are you on a dial-up, or a high speed connection.  If you're on dial-up, then I guess that might be acceptable.  If you're on a high speed connection, then I have to believe you have a hardware, line, or connection problem of some kind:confused:.  I've just never heard of anyone experiencing download/update times anything like that, even with well over 200 updates to process.  Everyone I know does have a high speed Internet connection though, so I don't know what's reasonable on dial-up.

---

### Post by Newuser1111 on 2008-07-21
> **bilijoe said:**
> I'm sorry, do I understand you to be saying that it took ***14 hours ***to download and install the initial set of upgrades, following a fresh install?  Are you on a dial-up, or a high speed connection.  If you're on dial-up, then I guess that might be acceptable.  If you're on a high speed connection, then I have to believe you have a hardware, line, or connection problem of some kind:confused:.  I've just never heard of anyone experiencing download/update times anything like that, even with well over 200 updates to process.  Everyone I know does have a high speed Internet connection though, so I don't know what's reasonable on dial-up.I have "FastAccess DSL", I guess that's highspeed. It isn't dial-up though.

Here's how the updates are currently going,
[IMG]http://playstationportablestuff.googlepages.com/UpdatesScreenshot-Downloadingpackage.png[/IMG]

---

### Post by darrelljon on 2008-07-21
Isn't it because Windows considers essential security updates to include upgrading whole applications like Explorer, Media Player and Messenger whereas Ubuntu considers essential security updates to only include essential security updates?

---

### Post by SunnyRabbiera on 2008-07-21
XP has had a history of crap like this, taking long and needing to restart over the tiniest update...

---

### Post by bilijoe on 2008-07-21
> **Newuser1111 said:**
> I have "FastAccess DSL", I guess that's highspeed. It isn't dial-up though.

Here's how the updates are currently going,
[IMG]http://playstationportablestuff.googlepages.com/UpdatesScreenshot-Downloadingpackage.png[/IMG] DSL is not as fast as cable, but it's still in the high speed access category, whereas dial-up is not.  Your download rate shows 96.7, which won't set any records, but is respectable.  The progress bar seems to show about 40% complete, and estimates 5 minutes, 14 seconds remaining.  Even if we assume that these figures are off by 100%, that still calculates out to just under 15 minutes, which makes perfect sense.  Where did you get a figure of 14 _**Hours**_?  Your numbers just don't add up.

---

### Post by Newuser1111 on 2008-07-21
> **bilijoe said:**
> DSL is not as fast as cable, but it's still in the high speed access category, whereas dial-up is not.  Your download rate shows 96.7, which won't set any records, but is respectable.  The progress bar seems to show about 40% complete, and estimates 5 minutes, 14 seconds remaining.  Even if we assume that these figures are off by 100%, that still calculates out to just under 15 minutes, which makes perfect sense.  Where did you get a figure of 14 _**Hours**_?  Your numbers just don't add up.After installing Ubuntu and it had over 200 updates.

---

### Post by bilijoe on 2008-07-22
> **][SIZE=1]                     Originally Posted by **bilijoe**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5428757#post5428757")[/SIZE]                 
                 *[SIZE=1]DSL is not as fast as cable, but it's still in the high speed access category, whereas dial-up is not. Your download rate shows 96.7, which won't set any records, but is respectable. The progress bar seems to show about 40% complete, and estimates 5 minutes, 14 seconds remaining. Even if we assume that these figures are off by 100%, that still calculates out to just under 15 minutes, which makes perfect sense. Where did you get a figure of 14 _**Hours**_?  Your numbers just don't add up.[/SIZE]* [SIZE=1]
[/SIZE][/quote]
[quote=Newuser1111 said:**
> After installing Ubuntu and it had over 200 updates. I see you were installing 8.04.  I can't imagine there would be a significant difference, but my most recent install was 7.10, which had 220 updates, after the initial install from CD.  The updates downloaded and installed in just under 20 minutes.  

I did notice, when the update manager first started, after it determined that there were 220 updates, it posted an*** estimated*** total time of something like 15 hours, 20 minutes.  I think this must have been calculated based on the assumption that the user had a dial-up connection.  When the downloads actually started however, and the software was able to obtain ***actual*** transfer speeds, it began to recalculate, and the estimated time to completion went lower, and lower, until after about one minute of real time statistics to draw upon, the update manager posted a relatively accurate time to completion of 25 minutes and some odd seconds, which was close to the actual time it took (still a little high, but close).  

Are you sure you aren't getting your 14 hour figure from that initial estimate?  Did you just leave it to do its thing, and come back in 14 hours, or did you check periodically to see how things were going.  

I plan on doing an 8.04.1 install later tonight, or tomorrow.  I'll have to pay close attention to how many residual updates there are, and how long it actually takes.  You've got me real curious here.  I just can't imagine it taking anywhere near 14 hours do deal with the post-install updates--any updates for that matter.  

If anyone reading this has had an experience anything like this, where the download/install of any number of updates took hours and hours, would you please write in and relate your experience.  Like I said, this has me real curious.

---

### Post by Newuser1111 on 2008-07-22
> **bilijoe said:**
> I see you were installing 8.04.  I can't imagine there would be a significant difference, but my most recent install was 7.10, which had 220 updates, after the initial install from CD.  The updates downloaded and installed in just under 20 minutes.  

I did notice, when the update manager first started, after it determined that there were 220 updates, it posted an*** estimated*** total time of something like 15 hours, 20 minutes.  I think this must have been calculated based on the assumption that the user had a dial-up connection.  When the downloads actually started however, and the software was able to obtain ***actual*** transfer speeds, it began to recalculate, and the estimated time to completion went lower, and lower, until after about one minute of real time statistics to draw upon, the update manager posted a relatively accurate time to completion of 25 minutes and some odd seconds, which was close to the actual time it took (still a little high, but close).  

Are you sure you aren't getting your 14 hour figure from that initial estimate?  Did you just leave it to do its thing, and come back in 14 hours, or did you check periodically to see how things were going.  

I plan on doing an 8.04.1 install later tonight, or tomorrow.  I'll have to pay close attention to how many residual updates there are, and how long it actually takes.  You've got me real curious here.  I just can't imagine it taking anywhere near 14 hours do deal with the post-install updates--any updates for that matter.  

If anyone reading this has had an experience anything like this, where the download/install of any number of updates took hours and hours, would you please write in and relate your experience.  Like I said, this has me real curious.I don't know what it actually was, as I posted,
because of the computer being off often it took days to download all of the updates.

---

### Post by bilijoe on 2008-07-22
> **Newuser1111 said:**
> I don't know what it actually was, as I posted,
because of the computer being off often it took days to download all of the updates. I don't know what to tell you, except that your experience with this is not normal.  

How is your system running?  If you are having any system type problems (as opposed to applications having their own problems), things like having the system stall (become unresponsive for a time), or run noticeably slower at some times than others, trailers, or ghosts behind windows when you move them, etc., it might be that you didn't get a clean install.  Not that that's likely, but it *is possible*, and it is the only explanation I can think of that might explain the incredibly long time it took to download and install those updates.

How did you do the install?  Was it an upgrade, or a fresh install?  And did you really mean 7.04?  That would be a rather old version.  I'd think you'd want at least 7.10, maybe even 8.04.1.  If it was a fresh install, did you download the .iso file, and then burn a CD from it?  If you did, did you run the MD5 checksum test on the .iso file, and did you also verify that the CD was an accurate copy of the .iso?  Instructions for verifying the .iso file can be found [COLOR=Red][here]("https://help.ubuntu.com/community/BurningIsoHowto")[/COLOR], while instructions for verifying the CD can be found [COLOR=Red][here,]("https://help.ubuntu.com/community/HowToMD5SUM/")[/COLOR] under "MD5SUM on CD" (or you can boot from the CD and select "Check CD for defects" from the opening menu.  

Because of the myriad of "bugs" that can be caused by only a single bit being mis-transmitted, or copied incorrectly, I strongly recommend taking both of these steps, every time you download any version of Ubuntu.  One bad bit, in a download or copy operation can lead to the kind of impaired performance that causes many of the nasty rumors about Linux being unstable, or erratic, or otherwise inferior to other operating systems.  The fact is, it is NOT inferior.  Different, yes.  Right for everybody, no.  But inferior?  Erratic?  Unstable??  If Linux is anything, it is stable.  

In any case, if any of the above applies to your installation procedure, PLEASE re-download the .iso file, perform the MD5SUM check on it, burn it to a CD, and perform one of the two CD validation tests on it.  Then do a fresh re-install, from the now certified CD.  I'll bet you'll find the 200+ updates download and install in less than a half hour.  

At 14 hours, or days and days, there almost *has* to be something wrong in your system, and I really don't want you to end up being one of those users who has a bad experience with Linux, and ends up believing all the untrue horror stories about it.  Fact is, Ubuntu Linux (IMHO) is the best operating system available today, and through its community of dedicated users, and the user forums, it is far and away the best supported software product of any kind I have ever had the pleasure of using.  The forums alone make Ubuntu worth the price:lolflag:.  

So please, for your sake and ours (the Ubuntu user community), make absolutely certain you are not running a corrupted copy.  Transmission and copying errors may be rare, here in the 21st century, but they do happen.  Out of roughly 25 downloads of Ubuntu system .iso files, I have encountered 2 downloads that failed the MD5 test and had to be re-downloaded, and one burn-to-CD that failed the CD error check, and had to be re-burned.  

The result of doing all this checking and re-checking however, has been that I have *never* had a problematic install, or installed a system that exhibited any unusual behavior (such as taking 14 hours to download and install its initial updates).  [COLOR=Red]BTW, ***always*** download and install ***all*** the updates, before actually running or using the system[/COLOR].  Failure to do so can also result in buggy installations which only serve to frustrate the user, and perpetuate the nasty and untrue rumors about Linux being anything less than an *excellent* choice of operating systems for many, many everyday PC users (as well as the hard-core Geeks it is so often associated with).  

I hope this didn't come off as a tirade, I just want to see you, and everybody else who tries it, have an excellent experience with Linux (especially Ubuntu--because it's *the best-*IMHO), so they will "pass the word" to others, and help grow our user base.

Cheers,

---

### Post by Newuser1111 on 2008-07-22
But I don't see very many problems.
Just that WiFi sometimes has problems and 
after several hours(Rarely, but can be minutes) it will show an error that has squares instead of text then Ubuntu will stop working.
> fresh installThat one,

All the Ubuntu cds that I can find in my desk are, 
"Ubuntu 7.10", "Ubuntu 8.04 Desktop i386", "7.04 Alt", "Ubuntu 7.04","7.10".

So I have the 8.04.

---

### Post by bilijoe on 2008-07-22
> **Newuser1111 said:**
> But I don't see very many problems.
Just that WiFi sometimes has problems and 
[COLOR=Red] after several hours(Rarely, but can be minutes) it will show an error that has squares instead of text then Ubuntu will stop working.[/COLOR] This, my friend, is indicative of a [COLOR=Red]very serious problem[/COLOR]!:shock:  Before you lose any irreplaceable data, I **strongly suggest** that you follow the directions in my previous post, and create yourself a ***certified Live / Install CD***, and use it to re-install your system.  Linux, especially Ubuntu **_*does not stop working--ever!*_**  For Linux to hang, there MUST be corrupted code somewhere in your installation.  There can be no doubt about it!  You have a corrupted install.  Please fix it before it causes you to lose data.  Also, as soon as the install from the CD has completed, and **before you run or use the [new] system**, run "Update Manager" and install** _ALL_** the updates, no matter how many there are.  Trust me, if you follow my instructions in the earlier post, and do the MD5 check on the .iso file, and either of the two integrity checks on the CD, it will NOT take 14 hours to download and install the initial updates--more like a half an hour.  Good luck.  If you have any questions, you can post them here, or send me a private message through the forum system.  I'll probably see a post first, but I check both pretty often.

---

### Post by bilijoe on 2008-07-22
BTW, I wouldn't trust any of those CDs you already have.  It's not that hard, and doesn't take that long to download AND CHECK a new .iso file, and to burn AND CHECK a CD.  Then you'll know you're playing with a fresh deck.

---

### Post by Newuser1111 on 2008-07-22
Also,

That problem has been happening ever since I tried VirtualBox.(Which I removed)

---

### Post by bilijoe on 2008-07-23
> **Newuser1111 said:**
> Also,

That problem has been happening ever since I tried VirtualBox.(Which I removed) That may have just triggered something.  Whatever the case, at this point, I'd bail out and do a certified clean reinstall.  You've obviously got a serious problem somewhere in your installation, and it isn't going to fix itself.  Really, it's not so bad.  If I had a nickel for every time I had to do a Blast and Build (that's what we called a complete reformat and reinstall) on a windows installation, I could retire.  (Wait a minute; I am retired.  Oh well.)  And, a BnB on XP took the better part of a day.  You'll probably only ever have to do this once, and even that's rare, on a Linux installation, and it should only take a few hours.  Just bite the bullet, and do it.  it'll be good experience.  If you still have problems, you've got bad hardware somewhere.  You might want to look at your log files, before you hose the current installation, though; just for yucks.

---

### Post by Newuser1111 on 2008-07-23
> **bilijoe said:**
> You'll probably only ever have to do this once, But it's already happened several times, (Before I got this Compaq Presario F700 laptop, which was when I had an Acer Aspire 3000)

> You might want to look at your log filesWhere?

---

### Post by bilijoe on 2008-07-23
> **Newuser1111 said:**
> But it's already happened several times, (Before I got this Compaq Presario F700 laptop, which was when I had an Acer Aspire 3000)

Where? You may have been working off a bad install disk all this time.  I can't see any other way you'd get several bad installs in a row.  We need to get you one good one though, so you don't lose faith.  Ubuntu Linux really is a fantastically good operating system.  I've seen it work so elegantly on so many different machines, it's hard to believe you're having so much trouble.

Most of the log files are in /var/log.  There's a ton of them.  I don't know which would be most important to look at, but if you "cd /var/log" and then run "ls -l" you'll be able to see which ones are the largest (perhaps suggesting a lot of activity, which may mean a lot of error reports), and which ones have been written to most recently (that won't necessarily tell you a lot, as a lot of the log files update every time you boot, or log in).  You may not get any useful information from the log files, but if you reinstall, you won't get any, 'cause they'll be gone.  

I probably won't check the forums again tonight--maybe once.  I'm going to start a new install of 8.04.1, and go to bed.  It's late here (for me, anyway).  If you do an install as I suggested in the earlier post, I really can't see how you could NOT come out with a smoothly running system,, unless your hardware is haunted, or something.  Good luck.  Let me know what happens.  I'll start checking the forums again tomorrow afternoon.  I hope to see a post from you saying "Everything's working perfectly!"  I've got my fingers crossed for you.:popcorn:

---

### Post by Newuser1111 on 2008-07-23
Now to look for the instructions on getting the WiFi to work.

Was there supposed to be only 30 updates?

---

### Post by bilijoe on 2008-07-23
> **Newuser1111 said:**
> Now to look for the instructions on getting the WiFi to work.

Was there supposed to be only 30 updates? I did a fresh 8.04.1 install last night, from a disk I made a couple of weeks age.  I don't remember the exact number, but it seems I got a list of about 35 updates, so 30 is probably correct for you.  The update manager is pretty good about getting you all the right stuff.  I was kind of surprised by the low number, but that could be a good sign, implying that the release has gotten pretty stable, and doesn't need much in the way of fixing and fiddling.  

BTW, I think FireFox 3 is still more than just a little buggy.  I had quite a bit of trouble with it last night.  I know many people have downgraded back to version 2.?? in their 8.04 installations.  I think that would be a good idea.  I'm going to do it.  I don't think it's particularly tricky.  I know I've seen at least one "How-to" post on it.  

I hope everything goes smoothly for you, from now on.  I'm not much of an expert on very many topics, but feel free to contact me any time, if you run into trouble.  I likely won't be able to answer your question, but I've become pretty good at finding answers within tie forums (and GOOGLE, don't overlook them as a resource).  

There is a reasonably useful feature attached to the "Start a New Thread" process, but there's a trick you have to know, or its worthless.  On the top line, there's a drop-down list for indicating which variant of  Ubuntu your post relates to.  Then there's the text entry line where you put the title.  Put some thought into the title.  The more specific and informative the title, the better will be the responses you get.  Also, it goes to this next item.  The last thing on that top line, is a button to "Check If This Has Been Posted Before".  This search feature *can* turn up a gold mine of information, but you MUST hover over it, to trigger a drop down list, and un-check everything that's checked in that list.  If you fail to do that, you might as well be asking Microsoft for help with your Linux installation.  With all the check boxes clear, click the button, and, if you are lucky, you might find that the answer is already there--that you don't need to make the post.  

There are several advantages to doing this.  One, it improves the quality and performance of the forums, because it avoids loading them down with redundant posts.  Two, it can save you the time of having to post, and wait for a reply (and sometimes sort through irrelevant posts).  And, three, the posts, and their associated threads that this search turns up, often include information on aspects of the subject you wouldn't have thought of, or additional, related information that can prove very useful.  

Before they "upgraded" the forum engine, a few months ago, this search was much more useful, but I think that is largely due to the inappropriate defaults in that drop-down list.  The items checked by default result in a search that's inappropriately restricted.  And I don't know if the search function in the new forums engine can access the tremendous base of previous posts that were made under the old system.  When the change was made, I got the impression that the maker of the forum software had released a "necessary" upgrade that was not appropriately rearward- compatible with the then current system.  

Anyway, good luck with your current install.  I hope you come to love Ubuntu as much as I do.  I've been preaching the word to any Windows user who will listen, and have made a few converts.  If you run into trouble, and can't get a timely resolution, send me a private message through the forums, and I'll try to help.

Cheers,

---

### Post by bilijoe on 2008-07-23
My apologies to all, for having run this thread *way* off topic:oops:.  I think it was for a good cause, but I will be making an effort to stay on topic, from now on.  I think the thread may have run its course anyway.  

I do think it's important to stay on topic in these forums, and again, I apologize for having failed to do so.:redface:

---

