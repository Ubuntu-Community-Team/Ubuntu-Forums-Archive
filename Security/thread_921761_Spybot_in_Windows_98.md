---
title: "Spybot in Windows 98"
date: 2008-09-16
forum: Security
---

### Post by Man_Beach on 2008-09-16
My wife needs to use Windows and Internet Explorer because some of the sites that she uses for work don't work properly (or sometimes at all) with Firefox or OpenOffice. So I have a dual boot system with a rather old but still perfectly adequate for our needs Windows 98 so that she can use IE/Excel when necessary.
I occasionally scan using f-prot for viruses and every month or so use Spybot to check for other Windows nasties - but the last time I used Spybot it took absolutely _AGES_ to do a scan - and I only have a 5gb partition for Windows, too (about 3 used).
From Googling, I suspect that Spybot support for Windows 98 is dying out. Does anyone have any suggestions for alternatives? I'm reluctant to go for the option and expense of a more recent version of Windows while what I've got still works.

---

### Post by Thelasko on 2008-09-16
> I suspect that Spybot support for Windows 98 is dying out.
I suspect spyware for Windows 98 is likely dying out as well.  An old version of spybot might protect you from the old spyware.  As there is very little new spyware for Win 98 you should be fine.

I don't have any statistics to back this up.  It's merely a theory.

---

### Post by snkiz on 2008-09-16
clamav is capable of scaning windows partitions from ubuntu. not to sure how it fares with mal/spyware but check the repos there may be something else. the advantage of doing scans this way is since windows isn't running you can delete the bad files easily and they wont self replicate.

---

### Post by Man_Beach on 2008-09-17
I'm happy with f-prot for the virus side of things, so there's no real need to try clamav. It's the malware/spyware things I really think I ought to check occasionally.

But having said that, I've only ever seen one virus on a computer (back in the 1980's) and only seen malware and spyware on friends' computers, which their children use and who visit all sorts of questionable sites.

As my wife only goes to a couple of known company sites with Windows, maybe I'm worrying too much?

---

### Post by Thelasko on 2008-09-17
> As my wife only goes to a couple of known company sites with Windows, maybe I'm worrying too much?
I don't think your worrying too much.  The fundamental problem is that everyone has stopped supporting Windows 98.

The way I see it you have two options:
1. Upgrade to XP
2. Take your chances with 98

Honestly, I don't think there are any **new** viruses for Windows 98 because the user base is so small.  However, Windows 98 is a very insecure operating system to begin with (which is why everyone switched).

If you're going to keep using it, let the wife do her work with it, but nothing else.

---

### Post by cariboo on 2008-09-17
If that computer is still running win98, it may not be capable of running xp. The best thing to do is to keep it behind a router with a builtin fire wall, and make sure nobody  else uses the computer, but your wife.

Jim

---

### Post by insane_alien on 2008-09-18
could you not get to the sites with a linux partition and ies4linux(or what ever its called).

even spoofing the useragent string has worked for me to gain access to 'ie only' sites.

---

### Post by ronnielsen1 on 2008-09-18
> Windows 98 is a very insecure operating system to begin with (which is why everyone switched).
That and alot of software wouldn't work any more

---

### Post by Man_Beach on 2008-09-18
> **cariboo907 said:**
> If that computer is still running win98, it may not be capable of running xp. The best thing to do is to keep it behind a router with a builtin fire wall, and make sure nobody  else uses the computer, but your wife.

Jim

Of course it's capable of running XP - but why should I bother spending out on a copy of it when my legal copy of 98 still works fine for my wife's limited needs of IE and Excel? Aren't we getting away from my original question here - I'm just looking for an alternative to the extremely slow running Spybot with Windows 98. [And I am running behind a NATS router, plus a firewall as well.]

---

### Post by Therion on 2008-09-18
You might want to consider [A-Squared Free](http://www.emsisoft.com/en/software/free/).

---

### Post by Man_Beach on 2008-09-19
Thank you Therion. I'll give it a try.

---

### Post by benny bronx on 2008-09-19
I believe Superantispyware is compatible with win98.  There is a free on-demand version, and I have used it to clean many infected computers.

---

### Post by airtonix on 2008-09-22
why dont you run windows98 inside virtualbox?

---

### Post by Man_Beach on 2008-09-22
> **airtonix said:**
> why dont you run windows98 inside virtualbox?

From searching the forums, I don't think that virtualbox would provide any protection against spyware. I'd still need to check using Spybot, or something similar.

---

### Post by Thelasko on 2008-09-22
> **Man_Beach said:**
> From searching the forums, I don't think that virtualbox would provide any protection against spyware. I'd still need to check using Spybot, or something similar.
The advantage of VirtualBox is that you can have a backup copy of Windows 98 on your hard drive.  If you discover it's compromised (you still need Spybot or something similar) you simply delete it and use the backup.

Basically, it saves you the four hours (in my experience) it takes to reinstall Windows.

---

### Post by sailorcire on 2008-09-22
I love Virtual Box so of course I agree with that option your fears are not ill-founded though for wanting protection for Win 98 ten years later. you might want to try Avast or AVG they have free editions and i can't think of them not working on 98...but you might want to download them to double check though

---

### Post by Thelasko on 2008-09-22
> **sailorcire said:**
> you might want to try Avast or AVG they have free editions and i can't think of them not working on 98...but you might want to download them to double check though
AVG isn't what it used to be.  It's become bloated and slow. (it also won't run on Win 98 )  If you're going to run a free anti-virus run Avast! if you're going to pay get NOD32. (both run on 98 )  Clamwin is supposed to run on Windows 98 but I don't know how well it deals with spyware.

---

### Post by sailorcire on 2008-09-22
> **Thelasko said:**
> AVG isn't what it used to be.  It's become bloated and slow. (it also won't run on Win 98 )  If you're going to run a free anti-virus run Avast! if you're going to pay get NOD32. (both run on 98 )  Clamwin is supposed to run on Windows 98 but I don't know how well it deals with spyware.

only bad thing about Clamwin is it isn't actively scanning so if you were to get phished you'd be taken all over and not know until you ran another scan and by then it might be to late and i don't think it does spyware...

---

### Post by Thelasko on 2008-09-22
> **sailorcire said:**
> only bad thing about Clamwin is it isn't actively scanning so if you were to get phished you'd be taken all over and not know until you ran another scan and by then it might be to late and i don't think it does spyware...

That's not the only thing bad about Clamwin.  But it's better than nothing.  Besides, the OP doesn't have real time scanning at the moment anyway.  My top choice is still Avast!

---

### Post by sailorcire on 2008-09-22
> **Thelasko said:**
> That's not the only thing bad about Clamwin.  But it's better than nothing.  Besides, the OP doesn't have real time scanning at the moment anyway.  My top choice is still Avast!
Indeed, i thought that that Spybot had real time...maybe I"m confusing it with Spy Sweep

---

