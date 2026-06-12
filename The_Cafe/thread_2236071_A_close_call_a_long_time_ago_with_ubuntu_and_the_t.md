---
title: "A close call a long time ago with ubuntu and the terminal"
date: 2014-07-24
forum: The Cafe
---

### Post by waterlubber on 2014-07-24
A long, long time ago, I was on a forum and say someone telling me to sudo rm recursive /.
I was bored and forgot to type sudo.
I am thankful that I did. XD
If only I knew his name, that's quite mean telling someone to wipe there hard disk. Now there is a pleasant warning.

---

### Post by coffeecat on 2014-07-24
More than mean. If the intent was malicious, that is one thing that can lead to an instant ban here.

[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

If you see anything similar, please report it so that the staff can deal with it.

---

### Post by waterlubber on 2014-07-24
It was on askubuntu. Unfortunatly, I had to go before I could get there un. I really really hate this guy because he probably caused plenty of curious users dismay. D: You should add a filter for hese commands, if so, they have the words DO NOT RUN imprinted upon them and auto-send to staff.

---

### Post by deadflowr on 2014-07-24
> **waterlubber said:**
> It was on askubuntu. Unfortunatly, I had to go before I could get there un. I really really hate this guy because he probably caused plenty of curious users dismay. D: You should add a filter for hese commands, if so, they have the words DO NOT RUN imprinted upon them and auto-send to staff.

The forum staff is quite small.
We would not be able to do basic moderations if every command instruction had to be reviewed.
However, if you come across suspicious commands such as the one you pointed out, report it using the report post button and then the staff will take the time to review it and take whatever action is needed.

---

### Post by coffeecat on 2014-07-24
Did you read the announcement I linked to?

We are not going to filter that or any command, because it could interfere with constructive and helpful advice posted here. People need to be educated about potentially destructive commands, whether used maliciously or by accident - hence the announcement. But we also rely on people reporting suspicious stuff so that the staff can take appropriate action. You are relatively new here, so you may not know that experienced members here are good at reporting stuff they are uneasy with. The staff are grateful to such members - without them it would be much more difficult to keep this forum a place the majority can find congenial.

---

### Post by Bucky Ball on 2014-07-24
> **coffeecat said:**
> ... experienced members here are good at reporting stuff they are uneasy with. The staff are grateful to such members - without them it would be much more difficult to keep this forum a place the majority can find congenial.

I second that largely. Without them it would be a dog's breakfast, a free-for-all, and mostly unmanageable. ;)

---

### Post by Warren Hill on 2014-07-24
The only advice I can give is never run a command someone tells you to without verifying it from another source.

coffeecat is correct the site would grind to a halt if every post had to be moderated before it was posted and because commands which are harmful in one circumstance may be good in another it would not be possible to set up automatic filtering.

There are plenty of people here who if they gave me instructions to do something I would follow without double checking.  But, certainly not if I didn't recognise the screen name and know they had a reputation for giving good advice.

That said the majority of people on this site are really good. You get the occasional idiot anywhere.

If you do spot anything that's malicious however report it with the Report post button at the bottom left of each post or in [Forum Feedback & Help]("http://ubuntuforums.org/forumdisplay.php?f=48").  The moderators can remove posts and I'm sure they are happy to ban a user who persists in dangerous posts.[URL="http://ubuntuforums.org/forumdisplay.php?f=48"]
[/URL]

---

### Post by sudodus on 2014-07-24
> **coffeecat said:**
> Did you read the announcement I linked to?

[COLOR=#ff0000]We are not going to filter that or any command, because it could interfere with constructive and helpful advice posted here[/COLOR]. People need to be educated about potentially destructive commands, whether used maliciously or by accident - hence the announcement. But we also rely on people reporting suspicious stuff so that the staff can take appropriate action. You are relatively new here, so you may not know that experienced members here are good at reporting stuff they are uneasy with. The staff are grateful to such members - without them it would be much more difficult to keep this forum a place the majority can find congenial.

> **Warren Hill said:**
> The only advice I can give is never run a command someone tells you to without verifying it from another source.

[COLOR=#ff0000]coffeecat is correct the site would grind to a halt if every post had to be moderated before it was posted[/COLOR] and because commands which are harmful in one circumstance may be good in another it would not be possible to set up automatic filtering.

There are plenty of people here who if they gave me instructions to do something I would follow without double checking.  But, certainly not if I didn't recognise the screen name and know they had a reputation for giving good advice.

That said the majority of people on this site are really good. You get the occasional idiot anywhere.

If you do spot anything that's malicious however report it with the Report post button at the bottom left of each post or in [Forum Feedback & Help]("http://ubuntuforums.org/forumdisplay.php?f=48").  The moderators can remove posts and I'm sure they are happy to ban a user who persists in dangerous posts.[URL="http://ubuntuforums.org/forumdisplay.php?f=48"]
[/URL]

+2

I agree with the above posts, but I have a couple of comments.

Certain obscene words are filtered and replaced with asterisks. The very worst commands, like removing all files from root would certainly also be possible to filter in the same way if we really want to.

But there is no way to filter all potentially dangerous commands. Instead we must ***encourage each other to backup everything that we don't want to lose ***because things happen related to software (including malicious commands) as well as hardware (including the power grid and theft).

---

### Post by grahammechanical on 2014-07-24
Warnings do not always work. Think of those people who install Ubuntu by selecting Use the Entire Disk and are then surprised that Ubuntu is installed and Microsoft Windows is no longer on the hard drive.

---

### Post by mooreted on 2014-07-24
The problem with Windows and OSX is they like to obscure all the yucky geeky stuff from users so they don't have to deal with it, but people don't learn how operating systems work anymore. Even Linux people have a tendency to copy and past commands from the Internet to fix a problem without really understanding what they are doing. People really need to learn how the command line works or they are susceptible to this sort of thing. So, don't ever use a command unless you know what it does first.

---

### Post by sudodus on 2014-07-25
> **grahammechanical said:**
> Warnings do not always work. Think of those people who install Ubuntu by selecting Use the Entire Disk and are then surprised that Ubuntu is installed and Microsoft Windows is no longer on the hard drive.

This happens.

But right now there is also a bug, so that people who select 'Installing alongside ...' or 'Reinstall ...' will actually use the entire disk. Maybe it is caused by some problem with identifying Windows, maybe some problem when there is already dual boot, linux and Windows, I'm not sure, but there is a lot of evidence that this is happening. So again,*** please encourage people to have a current backup*** of their system or at least the files they don't want to lose. See the initial warning in this link
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]
UEFI Installing - Tips[/URL]

and the bug report itself

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by /ADM on 2014-07-25
I would say the blame rests on the users.  If they just blindly go and type in those commands, it's their fault for not first researching what they are doing.  It takes 5 minutes on a search engine to figure this stuff out.

These people would not do this for half of the things in life (you wouldn't try to drive an 18-wheeler when you only know how to ride a bike) but people are happy to type in these kinds of commands without researching, without backing up and without even knowing what the hell they are doing.

CKI issue.

---

### Post by mooreted on 2014-07-25
Wiping the Windows partition automatically is a feature not a bug. :)

Joking aside: that's a nasty little bug. I hadn't heard of that one before.



> **sudodus said:**
> This happens.

But right now there is also a bug, so that people who select 'Installing alongside ...' or 'Reinstall ...' will actually use the entire disk. Maybe it is caused by some problem with identifying Windows, maybe some problem when there is already dual boot, linux and Windows, I'm not sure, but there is a lot of evidence that this is happening. So again,*** please encourage people to have a current backup*** of their system or at least the files they don't want to lose. See the initial warning in this link
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]
UEFI Installing - Tips[/URL]

and the bug report itself

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by Warren Hill on 2014-07-25
> **mooreted said:**
> Wiping the Windows partition automatically is a feature not a bug. :)

Joking aside: that's a nasty little bug. I hadn't heard of that one before.

The problem is partially terminology Windows  users often talk about the C: drive or the D: drive when they only have one drive but two partitions.  To a Linux user drives are drives not partitions.

Many Windows users think they have told the installer to use the whole D: drive not the whole drive that carries the D: partition, (and also the C: partition).

---

### Post by Bucky Ball on 2014-07-25
> **Warren Hill said:**
> 

Many Windows users think they have told the installer to use the whole D: drive not the whole drive that carries the D: partition, (and also the C: partition).

A new user posted a thread due to this very confusion just recently. Where's Windows? etc.

---

### Post by /ADM on 2014-07-26
> **Warren Hill said:**
> The problem is partially terminology Windows  users often talk about the C: drive or the D: drive when they only have one drive but two partitions.  To a Linux user drives are drives not partitions.

Many Windows users think they have told the installer to use the whole D: drive not the whole drive that carries the D: partition, (and also the C: partition).

I think the terminology is fine.  The very first time I installed Linux (looong ago) I knew exactly what `use entire disk` meant.  I do not see how you can get confused between disks and partitions.  I think if a user does not understand this concept, then they probably should not be installing an OS by themselves.

---

### Post by coldcritter64 on 2014-07-26
Dangerous commands tend to get jumped on quickly here, still take care what you copy/paste.

It should also be noted that copy/pasting directly from a website to the terminal (irresepective of how benign/safe the command is) is in itself a dangerous act. 

A thread, IIRC it was in this cafe, in the last year or so showed me that. It showed how a website can hide code alongside "safe" code that copying/pasting directly to a terminal can activate automatically, especially if the code contains a line return at the end of it, causing potential chaos for the user.

ALWAYS copy/paste code from a website to a text editor FIRST. Check the code for any extra "surprises". Then if the code is OK copy/paste from the editor to the terminal. In other words, inspect all code carefully before pasting to a terminal.

---

### Post by sudodus on 2014-07-26
> **coldcritter64 said:**
> Dangerous commands tend to get jumped on quickly here, still take care what you copy/paste.

It should also be noted that copy/pasting directly from a website to the terminal (irresepective of how benign/safe the command is) is in itself a dangerous act. 

A thread, IIRC it was in this cafe, in the last year or so showed me that. It showed how a website can hide code alongside "safe" code that copying/pasting directly to a terminal can activate automatically, especially if the code contains a line return at the end of it, causing potential chaos for the user.

ALWAYS copy/paste code from a website to a text editor FIRST. Check the code for any extra "surprises". Then if the code is OK copy/paste from the editor to the terminal. In other words, inspect all code carefully before pasting to a terminal.

Thanks for this warning :-)

I had never thought of this problem with 'hidden code'. But I do copy via a text editor sometimes to get rid of formatting, that I see.

---

### Post by coldcritter64 on 2014-07-26
> **sudodus said:**
> Thanks for this warning :-)

I had never thought of this problem with 'hidden code'. But I do copy via a text editor sometimes to get rid of formatting, that I see.
You're welcome :)

It was a long while back that I saw the thread here in the cafe so am posting from memory. The post linked to a website that demonstrated the technique in a relatively safe/educational way. However once someone runs a root (sudo) command in a terminal any following sudo command within the sudo timeout period carrying the hidden payload could run automatically and very destructively... OUCH :evil:. 

I now check all commands with gedit when following online tutorials.

If anyone here knows of or has a subscription to the thread I refer to, it would be good to link it here as a general terminal usage warning in the same context as the OPs warning/comments.

---

### Post by MartyBuntu on 2014-07-26
> **sudodus said:**
> So again,*** please encourage people to have a current backup*** of their system or at least the files they don't want to lose.

It's alarming how many people I know in my life that have absolutely NO backup whatsoever.

---

### Post by Warren Hill on 2014-07-28
> **MartyBuntu said:**
> It's alarming how many people I know in my life that have absolutely NO backup whatsoever.

True, there are two sorts of computer users.

Those who keep proper backups

and 

Those that will lose data.

---

### Post by vasa1 on 2014-07-28
> **sudodus said:**
> ...

and the bug report itself

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Quite a dangerous bug! The dev (?) who has taken on the bug seems to be focused on Windows 8 if one goes by [comment 57]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/57") although it appears to affect Win 7 as well.

---

