---
title: "How much drive space does a standard ubuntu install need?"
date: 2006-03-08
forum: The Cafe
---

### Post by xequence on 2006-03-08
On my new computer I am going to have ubuntu on it dual booted with windows... But what is the space needed for an ubuntu install?

Im not talking bare minimum. I mean like to have it and have it work well, and have room to install plenty of stuff.

Whats your opinion on this? How much should my linux partition be? Windows partition?

It is a 200GB hard drive.

Im thinking:

Windows: 40GB
Linux: 20GB
Shared: 140GB

And obviously if that thing where hard drives arnt as big as they say is real, ill have to have a smaller shared partition.

Explanation of what I think: I will install more stuff on windows then linux (games and programs) as getting games to work in linux is just waaay to hard at the moment.

If you have a similar sized hard drive what is yours partitioned like?

---

### Post by Swiss on 2006-03-08
I have an 80GB HDD, I have it like so:

XP: 39GB
Linux: 39GB
Swap: 2GB (overkill, I know)

Your partitioning plan seems good to me. :)

---

### Post by ssam on 2006-03-08
assuming that you intend to keep you documents on the shared drive then 20Gb should be fine, it would be a challange to fill it by installing applications.

if you wanted to install thousands of packages including things with large data files (games, music apps with many samples etc) then you might maybe fill 20gb.

dont forget 1 or 2 gig for swap (between 1 and 2 times the size of you RAM is a good rough size)

---

### Post by jasay on 2006-03-08
And windows will probably swipe 4-12 gigs for a backup/restore partition.

---

### Post by bjweeks on 2006-03-08
[QUOTE=jasay]And windows will probably swipe 4-12 gigs for a backup/restore partition.[/QUOTE]

It doesn't use a new partition...

---

### Post by jasay on 2006-03-08
[QUOTE=bjweeks]It doesn't use a new partition...[/QUOTE]
Was on mine.  Though that was from factory, so it was probably more a Dell thing than windows.

---

### Post by xequence on 2006-03-08
> And windows will probably swipe 4-12 gigs for a backup/restore partition.

It doesent make any other partitions.

And I have server 2003 anyway, which doesent even include system restore, so it doesent matter :P

> assuming that you intend to keep you documents on the shared drive then 20Gb should be fine, it would be a challange to fill it by installing applications.

if you wanted to install thousands of packages including things with large data files (games, music apps with many samples etc) then you might maybe fill 20gb.

dont forget 1 or 2 gig for swap (between 1 and 2 times the size of you RAM is a good rough size)

Ill have all my music and videos and stuff on the shared partition.

---

### Post by Bandit on 2006-03-08
A standard Ubuntu install? Without updates and no additional software installed it should not take up more then the size of the CD, but mine end up always around 2GB. So I am totally confused why..

---

### Post by bjweeks on 2006-03-08
It is commpressed on the cd...

---

### Post by xequence on 2006-03-08
[QUOTE=Bandit]A standard Ubuntu install? Without updates and no additional software installed it should not take up more then the size of the CD, but mine end up always around 2GB. So I am totally confused why..[/QUOTE]


It is compressed on the CD and uncompressed on the hard drive.

But I am not talking about a clean install. I am planning to install programs ya know =P

---

### Post by Bandit on 2006-03-08
[QUOTE=xequence]It is compressed on the CD and uncompressed on the hard drive.[/QUOTE]
Damn, I never thought out that... I feel stupid now... :-D 
Then I'd say 2-3GB without updates or any additional software. 
My install is at 6GBs right now and I have my own kernel installed, tons of extra stuff. 32bit compatability libs for Fx 32bit 1.5.01 and few other what nots that didnt come on the CD.

---

### Post by xequence on 2006-03-08
> Damn, I never thought out that... I feel stupid now...  

Everyone has a momentary lapse of reason sometimes =P

---

### Post by aysiu on 2006-03-08
Ubuntu shouldn't take up more than 6 GB usually. Mine has a bunch of stuff and is less than 3 GB.

---

### Post by xequence on 2006-03-08
So maybe even 20GB is a bit overkill...?

---

### Post by WildTangent on 2006-03-08
[QUOTE=xequence]
And I have server 2003 anyway[/QUOTE]
BAD idea my friend...a friend of mine tried to use it as a desktop OS, it didn't work out well at all, there were many problems with program compatibility, and games don't work well. Just stick with XP.

-Wild

---

### Post by xequence on 2006-03-08
[QUOTE=WildTangent]BAD idea my friend...a friend of mine tried to use it as a desktop OS, it didn't work out well at all, there were many problems with program compatibility, and games don't work well. Just stick with XP.

-Wild[/QUOTE]

Oh, ok, I wont use it then.

Thanks for telling me :P Wouldent want to be disapointed.

I had heard it was alot more stable then XP. But then again XP is stable for me anyway.

---

### Post by Orunitia on 2006-03-08
[QUOTE=xequence]So maybe even 20GB is a bit overkill...?[/QUOTE]

Definitely. Right now my Ubuntu partition is 5GB, and I have over 2GB free. I dual boot with XP, so I have a "storage" partition I like to call it that I keep all my files on, that I keep as fat32 so both XP and Ubuntu can access it.

---

### Post by WildTangent on 2006-03-08
[QUOTE=xequence]Oh, ok, I wont use it then.

Thanks for telling me :P Wouldent want to be disapointed.

I had heard it was alot more stable then XP. But then again XP is stable for me anyway.[/QUOTE]
It is very stable for its intended purpose, but not as a workstation or desktop OS. And it's a bitch to configure it to even approach normal usability. My friend had me do it...it was hard. There are many services which must be enabled, and things that must be tweaked, registry files that must be edited, etc. Not worth the effort.

-Wild

---

