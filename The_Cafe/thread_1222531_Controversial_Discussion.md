---
title: "Controversial Discussion"
date: 2009-07-25
forum: The Cafe
---

### Post by snakeman21 on 2009-07-25
So I was talking to a friend at work today who is a Windows user, and we were talking about him keeping his seventeen-year-old son off his computer.  This conversation strayed into general computer security, and he told me that he knew about how most people don't know about the hidden Admin account on Windows that is only accessible through Safe Mode.  He was confident that his computer was secure, because he put a password on it.  I told him no, his computer was NOT secure just because of a password.  (Keep in mind that we're not talking at all about network security, just physical access to the computer.)  

Any, he asked why, and I said that there were many ways to get through such passwords, such as password crackers.  He had never heard of such a thing, and asked if I could come over to his house after work and help make him more secure.  I said sure.

So I went over, and first demonstrated how someone could use Ophcrack via Slitex from a usb stick.  He was shocked when his password was cracked in seconds.  I said he could avoid this by making his password longer than 14 characters.  We did this, and I demonstrated that Ophcrack would not work on such long passwords.  He said, "So I'm safe now, right?"  I was about to tell him yes, when I remembered about running Linux from a flash drive to access the hard drive of a computer.  So I plugged in my flash drive with a persistent Jaunty installation and showed him how anyone could do that and mess with his hard drive, stealing and/or deleting crucial files.  I told him this could be prevented by setting up a bios password, which would prevent the computer from booting anything until said password was entered.  But then I thought, what if someone just opened the case and power-cycled the cmoss battery?  That would reset the password!  

I had never thought about all these things together before, and I came to the realisation that I, even though I am far from being an expert, could get into anyone's computer illegally.  Is this true?  Can anyone with a simple knowledge of computers get into my system in a matter of minutes when I'm not around?  Or is there a level of security I'm unaware of?  It really makes me uncomfortable, seeing as though anyone with a live usb or cd could instantly bypass any security measures, as long they knew how to power-cycle the battery.

Are we really this vulnerable???

---

### Post by lykwydchykyn on 2009-07-25
There is an age old understanding of computer professionals that physical access to the machine is pretty much owning the machine.  No matter what OS you use, if a knowledgeable person gets his/her hands on it, it's cracked.

The exception would be if you actually encrypted all your data, thus incurring all the performance overhead and making data recovery more difficult in the event of an emergency.

---

### Post by snakeman21 on 2009-07-25
It made me realize that if someone has physical access, *NO* computer is unhackable... Kinda scary.  I have touchy information on my system. (bank info, pay stub PDF's, personal info... not to mention my wife and I have our, ahem, "restricted" pic folder on there... maybe I'll start locking up my computer...in my gun safe that's bolted to the floor...

---

### Post by snargfish on 2009-07-25
Except using disk-encryption would make things much harder.

---

### Post by lisati on 2009-07-25
I read something a few years ago to the effect that the best security system is not so much one that is unbreakable, but one which is sufficiently difficult that by the time the intruder has worked out how to get round it, the information or service they're after is either no longer available or no longer relevant.

---

### Post by Grant A. on 2009-07-25
> **snargfish said:**
> Except using disk-encryption would make things much harder.

[img]http://imgs.xkcd.com/comics/security.png[/img]

Comic courtesy of: [xkcd]("http://www.xkcd.com/").


Even then, encrypted disks are still vulnerable to cold-boot attacks. If someone really wants your data, then there's no way to stop it.

---

### Post by snargfish on 2009-07-25
> **Grant A. said:**
> [img]http://imgs.xkcd.com/comics/security.png[/img]

Comic courtesy of: [xkcd]("http://www.xkcd.com/").


Even then, encrypted disks are still vulnerable to cold-boot attacks. If someone really wants your data, then there's no way to stop it.

Except if you set up a RYPHER code that DoD's the first sector of the disc if the password is entered incorrectly a certain number of times, or it detects illegal attempts at data entry/recovery.

---

### Post by MaxIBoy on 2009-07-25
> **snakeman21 said:**
>   But then I thought, what if someone just opened the case and power-cycled the cmoss battery?  That would reset the password!  
Some of the more-recent BIOSen use static flash and thus do not require a battery to keep their settings (although the battery is important to keep the clock accurate.) Most BIOSen have a "case open" alarm if you hook it up to a device which would detect such a thing. 

In general, it's all about buying time, and making it "too much trouble" for an intruder. The goal of a good security system is that it takes physical access *and* at least twenty minutes to crack. In other words, never let your computer out of your sight for twenty minutes or more. :)


(By the way, if the data is not encrypted, it *will* be readable. You can boot an OS from removable media or even use netboot to boot it over the LAN, or you can move the hard drive to another machine. Doesn't matter. It will be readable. However, data can be encrypted using things like TrueCrypt.)

---

### Post by snakeman21 on 2009-07-25
A "case open" alarm is pretty useless.  All you do is open the case, pull the battery, put it in backwards, pull it again, put in in the right way, close the case, and boot the computer... no case open alarm will be triggered because the computer was never started with the case open.

Edit:  I do like the idea of the static flash bios... that's a good one

---

### Post by tjwoosta on 2009-07-25
Put the computer inside a big safe with only holes for the cords to get through then lock it

---

### Post by philliptweedie on 2009-07-25
> **tjwoosta said:**
> Put the computer inside a big safe with only holes for the cords to get through then lock it

Not good enough!

[http://www.gizmodo.com.au/2009/07/power-line-exploit-logs-your-keystrokes-using-outlets-lasers/](http://www.gizmodo.com.au/2009/07/power-line-exploit-logs-your-keystrokes-using-outlets-lasers/)

---

