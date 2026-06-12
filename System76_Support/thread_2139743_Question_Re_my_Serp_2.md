---
title: "Question Re my Serp 2"
date: 2013-04-27
forum: System76 Support
---

### Post by hkarl629 on 2013-04-27
Purchased my Serval/Serp 2 on June 25, 2007, order # 4764.  It has been doing well ever since. Am getting up the courage to upgrade to Ubuntu 13.04 from 12.10.  Have heeded advice from System 76 to wait awhile for the bugs to go away and the server traffic to lessen before taking the plunge. (at 83, I don't rush into things)

My question for System 76 personnel - How do I determine if this computer is a 32 bit or a 64 bit machine. That's a question I need an answer for so that I choose the correct version of Ubuntu for this computer.

Web site has really changed and looks very nice.


Thanks in advance.  
H Karl Juelch

---

### Post by MoebusNet on 2013-04-28
I'm just another satisfied System76 owner, but from what I can find your serp2 is quite capable of running the 64-bit version:

[http://ubuntuforums.org/showthread.php?t=748755](http://ubuntuforums.org/showthread.php?t=748755)

Note that he is running Ubuntu 64 Bit 7.10 (Gutsy Gibbon).

I think the general rule of thumb now is that if your CPU is capable of running 64-bit, that is the preferred version.

EDIT: To find your current version of Ubuntu:

[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

I am under the impression that if you are going to do a distribution-update rather than a clean install, you need to stay with the same version (32-bit or 64-bit) that you currently use. If you do a clean install, use whatever works. As always back up any data you want to keep.

---

### Post by hkarl629 on 2013-04-29
MoebusNet,

Thank you for your response.  Using the links you provided I was able to see that my Serp 2 is running the 64 bit version of Ubuntu 12.10  So I will go for the 64 bit v. of 13.04.  I just couldn't remember what versiion I had installed.  I've put it in writing now. The upgrade will be tomorrows job.  Serp 2 and System 76 haven't failed me yet and I don't expect that to happen tomorrow.

Again, Thank you.

H Karl

---

### Post by hkarl629 on 2013-05-01
Serp 2, Intel Core 2 CPU T5600, 1.83 GHz, 2 Gb  memory,  117 Gb HD

Thought I was ready to do the upgrade via the internet, but was not successful.  Here is what happened and didn't happen:

Started the upgrade process; when it got to the "Calculating the changes", up came the message, "not enough free disk space".

Says, "needs 1,711 m of free disk space on disk '/'  Please free at least an additional 227 m of disk space on '/' . Empty trash and remove temporary packages of former installations using 'sudo apt-get clean'

How do I get to those temporary packages to remove them?  I came across several temporary packages/files and they could not be deleted or moved to Trash. Stymied.

IF I  can get stuff into Trash, I have no problem emptying the Trash.

Also, how can I Increase the space available on '/' ?  As the new versions of Ubuntu come along they are getting larger and I anticipate the need for even more space in the future.

As a novice in the field I need some detailed help to guide me through my delimma.  I thank you in anticipation of the help someone will provide

Sincerely,

H

---

### Post by isantop on 2013-05-02
Just run this command to clear out old copies of downloaded packages:

```
sudo apt-get clean
```

You'll want to type this into the terminal application, followed by enter. 

If you've never run this command before, then the system will have a copy of every version of every package you've ever installed stored locally. It fills up the disk fast, and this is one of the surefire ways to free up space on a system.

---

### Post by hkarl629 on 2013-05-02
Serp 2, Intel Core 2 CPU T5600, 1.83 GHz, 2 Gb memory, 117 Gb HD  (Plenty of space on the HD, but not enough on the '/' or root section.  That appears to be the cause of my problem. I think.

ISANTOP,
Essentially, I did exactly what you suggested.  Used the 'sudo apt-get clean' command and nothing appreared to indicate anything happened as a result of using the command.  I've copied a former message which spells out what the computer is telling me (below).
I'm stuck.  Tried to emphasize in the text below (using BOLD)

Thought I was ready to do the upgrade via the internet, but was not successful. Here is what happened and didn't happen:

Started the upgrade process; when it got to the "Calculating the changes", up came the message, "not enough free disk space".

[B]Says, "[COLOR="#0000CD"]needs 1,711 m of free disk space on disk '/' Please free at least an additional 227 m of disk space on '/' . Empty trash and remove temporary packages of former installations using 'sudo apt-get clean[/COLOR]'

How do I get to those temporary packages to remove them? I came across several temporary packages/files and they could not be deleted or moved to Trash. Stymied.[/B]

IF I can get stuff into Trash, I have no problem emptying the Trash.

**Also, how can I Increase the space available on '/' ? As the new versions of Ubuntu come along they are getting larger and I anticipate the need for even more space in the future.**

As a novice in the field I need some detailed help to guide me through my delimma. I thank you in anticipation of the help someone will provide

Sincerely,

hkarl629

---

### Post by isantop on 2013-05-03
I would back up your files and perform a fresh installation via the CD by erasing your current installation. This will set the disk up with a single partition and avoid this problem in the future (i.e. the only way you would be able to get it would be if your entire disk was full).

---

### Post by hkarl629 on 2013-05-03
Still struggling to solve my problem.

Serp 2, Intel Core 2 CPU T5600, 1.83 GHz, 2 Gb memory, 117 Gb HD (Plenty of space on the HD, but not enough on the '/' or root section. That appears to be the cause of my problem. I think.

I'm really at a loss with this problem.  I do have a disk with Ubuntu 12.10 on it. I need to know just how to erase/delete the current version of 12.10 with all the temp files you say are there so that I can reinstall version 12.10 and then hopefully have the room to move up to 13.04.

I attached an external drive and off-loaded files I want to preserve. Had to do it by opening the file, doing a "Save As" to the external drive.  Thought I could do a drag and drop - but it didn't work.

I need details necessary to do the job.  Help.

hkarl529

---

### Post by hkarl629 on 2013-05-05
Good news folks/friends,
Here was the problem:  Wanted to upgrade to Ubuntu 13.04 - had Ubuntu 12.10 installed.
Serp 2, Intel Core 2 CPU T5600, 1.83 GHz, 2 Gb memory, 117 Gb HD (Plenty of space on the HD, but not enough on the '/' or root section. That WAS the cause of my problem. 

So, took the disk (v. 12.10) from "Ubuntu User" to which I subscribe,  Checked that when computer was started it would look at the cd/dvd player first to boot up. (It was set to do that) Put the disk in the cd/dvd, shut the computer off. Turned it back on and started it up from the disk.  Told it to install 64 bit v. of Ubuntu 12.10.  It proceeded to wipe out the old version, clean everything up, and reinstalled v. 12.10.

Now I was good to go for the upgrade to v. 13.04. I did this from the Ubuntu web site with no problems.

I've taken my Serval/Serp 2 from Feisty Fawn 7.04 in June of 2007 to "Raucus Ringtail' (whatever) 13.04 in May of 2013. Says something good about this System 76 computer.

Thanks for bearing with me.

hkarl629

---

