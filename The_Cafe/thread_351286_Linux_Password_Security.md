---
title: "Linux Password Security"
date: 2007-02-01
forum: The Cafe
---

### Post by natedawg on 2007-02-01
Ok so I read on digg.com today about a program called  Ophcrack. The program cracks windows passwords and can be run from a SLAX live CD. I booted the cd on my computer and waited about five min. Then behold, it displayed my windows password. I was just wondering is there anything like this to crack Linux passwords? I don't know anything about Linux password security but how secure are the root and user passwords on Ubuntu? Can the passwords be found by rainbow tables like Ophcrack? I'm not trying to crack my Linux password I just want to know about the deterrents involved and how secure Linux passwords are vs Windows.

---

### Post by raul_ on 2007-02-01
They're stored in a hash table, it's *virtually* impossible to crack a password stored in a hash table. The only way i see it done is by using brute force - try & failure

At least that's what i was told in my OS class :)

---

### Post by natedawg on 2007-02-01
> **raul_ said:**
> They're stored in a hash table, it's *virtually* impossible to crack a password stored in a hash table. The only way i see it done is by using brute force - try & failure

At least that's what i was told in my OS class :)

Thats good to know if what you say is true :) 
This is just one more reason to use Linux.

Why wouldn't Microsoft use a hash table for their passwords? Or do they use one now on Vista?

---

### Post by Brunellus on 2007-02-01
> **natedawg said:**
> Thats good to know if what you say is true :) 
This is just one more reason to use Linux.

Why wouldn't Microsoft use a hash table for their passwords? Or do they use one now on Vista?
because it didn't occur to them to do so?  Because they figured nobody would want access to your passwords? 

Ask ballmer.  wear a chair-proof suit.

---

### Post by FuturePilot on 2007-02-01
> **Brunellus said:**
> because it didn't occur to them to do so?  Because they figured nobody would want access to your passwords? 

Ask ballmer.  wear a chair-proof suit.
LMAO!:lol:

---

### Post by TBOL3 on 2007-02-01
> **Brunellus said:**
> because it didn't occur to them to do so?

What still boggles me is, Why do they base there OS on dos, ON DOS!!!

---

### Post by macogw on 2007-02-01
> **TBOL3 said:**
> What still boggles me is, Why do they base there OS on dos, ON DOS!!!

They don't.  Haven't in years.  NT != DOS.  That "command prompt" is a DOS emulator.

From what I've heard, MS does hash it.....but the hash is very well known, so it's useless.

---

### Post by saulgoode on 2007-02-01
My understanding is that Linux adds 8 random characters to the password you supply, thereby producing about 200 trillion (2e14, if I did that right) different possible hashes for the same password. A reverse lookup would need to be performed for each of these randomized hashes (or you get VERY lucky) for every single one of Ophcrack-generated hashes. 

Why doesn't Windows employ this added measure of security? Perhaps we should ask the NSA.

---

### Post by aysiu on 2007-02-02
If someone can boot a live CD on your computer, a password's security becomes moot, doesn't it?

---

### Post by unbuntu on 2007-02-02
> **aysiu said:**
> If someone can boot a live CD on your computer, a password's security becomes moot, doesn't it?

You can adjust the boot sequence and set a BIOS password...done.

---

### Post by aysiu on 2007-02-02
> **unbuntu said:**
> You can adjust the boot sequence and set a BIOS password...done.
Even that is an obstacle that can be overcome with physical access to the computer, but it **is** still an obstacle and will slow down attempts to gain root access.

---

### Post by Polygon on 2007-02-02
i read an article on some ubuntu blog on how to disable being able to run as root from a live cd to prevent that

yeah ive also used one of those password recovery programs (it was a linux image for a floppy disk) and i ran it and in about 5 seconds it gave me my password.

---

### Post by aysiu on 2007-02-02
> **Polygon said:**
> i read an article on some ubuntu blog on how to disable being able to run as root from a live cd to prevent that If you find it again, can you post the link, please?

---

### Post by Sarisar on 2007-02-02
Windows stores passwords < 14 characters long in two 7 character LM hashes.  14 characters + are stored in NTLM hashes (which are much harder to crack).

So for the shorter passwords you just have to crack a 7 character password... that is why it's so easy.

Actually you can just download the ultimate boot cd and change the passwords if you have physical access...

---

### Post by macogw on 2007-02-02
> **Sarisar said:**
> Windows stores passwords < 14 characters long in two 7 character LM hashes.  14 characters + are stored in NTLM hashes (which are much harder to crack).

So for the shorter passwords you just have to crack a 7 character password... that is why it's so easy.

Actually you can just download the ultimate boot cd and change the passwords if you have physical access...

15+.   14 are still stored as 2 7-char passwords.

---

### Post by macogw on 2007-02-02
> **aysiu said:**
> Even that is an obstacle that can be overcome with physical access to the computer, but it **is** still an obstacle and will slow down attempts to gain root access.

pop out the CMOS battery, all done.  Some lappies have a button on the bottom to make it extra easy cuz the mobo is hard to reach.

---

### Post by Polygon on 2007-02-02
> **aysiu said:**
> If you find it again, can you post the link, please?

im pretty sure it was on this blog: [http://ubuntu.wordpress.com](http://ubuntu.wordpress.com) , but i cant find it now... i hope im not mistaking it (disabling root when running from a live cd) for something else....

---

### Post by ~LoKe on 2007-02-02
Regardless of what has been said in this thread: If someone has physical access to your machine and has a slight idea of what they're doing, _your system has been compromised_.  If you have to worry about people doing stuff like this, then perhaps you need encryption.

The whole aspect of security now is not in place to stop this kind of thing, but rather attacks over the Internet.

---

### Post by natedawg on 2007-02-02
> **Sarisar said:**
> 
Actually you can just download the ultimate boot cd and change the passwords if you have physical access...

True, but if if you can crack a Windows password in a matter of minutes then why bother changing the password. Crack the password and know one will even know you gained access. 

Thanks for all the information guys.... It's clear now that Linux has a much better security system in place than Windows. Also there is limited protection if someone has physical access to the system. 

Its interesting that it is so easy to bypass Windows. I guess Microsoft relied  to much on the fact that Windows is closed source. This leads me to wonder how OSX compares... Whats it's password protection like?

---

### Post by Brunellus on 2007-02-02
> **TBOL3 said:**
> What still boggles me is, Why do they base there OS on dos, ON DOS!!!
there isn't any DOS in Windows these days;  all their DOS compatibility is through a compatibility layer.  Think WINE, but on Windows, for DOS.  

The kernel for Windows is descended from NT, which was supposed to be Microsoft's unix-killer.

And, incidentally, MS "suffers" from Bug 1, too, in the sense that they must move VERY carefully to preserve backwards compatibility.  No existing Microsoft users would have cared much for a Microsoft OS on which their existing apps were incompatible.

Apple has broken backwards compatibility and does so with relative impunity;  first, because they have such a tiny share of the total market, and second, because Macolytes will buy almost anything that comes in a white box with 'APPLE' printed on it.

---

### Post by raul_ on 2007-02-02
> **~LoKe said:**
> Regardless of what has been said in this thread: If someone has physical access to your machine and has a slight idea of what they're doing, _your system has been compromised_. 

The whole aspect of security now is not in place to stop this kind of thing, but rather attacks over the Internet.

Exactly. If people have physical access to your computer and all they want is to corrupt your data they can get a sledgehammer and do a "push the tempo" (fatboy slim's music video) on your computer

---

### Post by Hex_Mandos on 2007-02-02
There's an important legal difference there. Under my country's laws, data in digital format is not a "thing". Corrupting data through software means can't get you into jail (at least, not by itself). Destroying a physical object that belongs to someone else (ie the computer) is a criminal offense pretty much everywhere.

---

### Post by raul_ on 2007-02-02
Banging a computer doesn't get you in the jail either. At least i think that all you have to do is see a shrink and pay for the computer, and maybe do some community work

---

### Post by beercz on 2007-02-02
> **~LoKe said:**
> Regardless of what has been said in this thread: If someone has physical access to your machine and has a slight idea of what they're doing, _your system has been compromised_.  If you have to worry about people doing stuff like this, then perhaps you need encryption.

The whole aspect of security now is not in place to stop this kind of thing, but rather attacks over the Internet.

Surely part of computer security is the location of the computer itself.  It the computer holds sensitive data then shouldn't it be kept in a secure location, locked room/building or whatever, and have security passes, keys, swipecards etc. etc.?

Banks for example have all their servers locked away.

Computer security should encompass all aspects, not just remote attacks.

---

### Post by raul_ on 2007-02-02
> **beercz said:**
> Surely part of computer security is the location of the computer itself.  It the computer holds sensitive data then shouldn't it be kept in a secure location, locked room/building or whatever, and have security passes, keys, swipecards etc. etc.?

Banks for example have all their servers locked away.

Computer security should encompass all aspects, not just remote attacks.

True, but i think we're all talking about home security here (maybe some security at work, but we can't all work in a locked office with card access that will blow and destroy everything in a 100m radius if someone tries to break through)

---

### Post by beercz on 2007-02-02
> **raul_ said:**
> True, but i think we're all talking about home security here (maybe some security at work, but we can't all work in a locked office with card access that will blow and destroy everything in a 100m radius if someone tries to break through)
Yes this is true.  Still it helps to think about trying to keep the computer away from prying hands if possible.  Locking the front door when out of the house helps of course!!

---

### Post by raul_ on 2007-02-02
Then you agree that the Live CD and the BIOS battery arguments are rubbish in this context :) Everyone can break into your house, but i think that's another reality that is not in the domain of computer security development

---

### Post by Hex_Mandos on 2007-02-02
> **raul_ said:**
> Banging a computer doesn't get you in the jail either. At least i think that all you have to do is see a shrink and pay for the computer, and maybe do some community work

See a shrink? For a criminal offense? Unless you positively prove you're crazy (and that you were crazy BEFORE doing what you did), you're facing two lawsuits: a criminal trial for destroying someone else's property, and a civil procedure to repay damages (including moral damage, the money lost for not being able to use the computer, etc.). You MIGHT be able to try probation for the criminal charges, but you're not necessarily going to get it every time, and probably not if there were other charges, such as trespassing into someone's property (I know of people who talked their way into houses in order to plant malicious software, but there's no diplomatic approach to hammering a computer). 

Moreover, what if someone wants to stop you while you're holding the hammer? IF you threaten them with it, you'd be digging yourself deeper into a legal mess... why not just aim for a cleaner route?

---

### Post by raul_ on 2007-02-02
Of course i'm not talking about the kid next door who thinks it's cool to create a virus and format your hard drive. I'm talkink about things a bit more sophisticated. But yes, of course it's not a clean route to follow, but you wouldn't be stupid to the point of actually hammering a computer, and certainly not stupid to the point of doing it while the person was looking. 

My point was, if you have physical access to the computer, you can do anything with it. you can cut 2 cables, or spill water on the processor, or something like that, to corrupt data. These are "clean routes" i believe. I was not talking about hammering literally.

You can even overclock the processor and make the computer "unbootable". Of course that would only work with stupid people, who could always take it to the computer store, where it would probably get fixed. But it's a possibility. Just fry the processor and blame it on an electricty peak. I don't know.

But i think it's pointless trying to take this discussion away from the OS security implementation.

---

### Post by steve.horsley on 2007-02-02
Don't get too complacent. Linux still stores passwords in hashes. These are vulnerable to cracking of course, and I guess it's very likely that rainbow tables exist to make the task easier. The windows hashes may be easier to crack, I don't know, but if so, it's only a matter of degree.

But if a baddie gets physical access and can boot a live cd, you're screwed in so many other ways anyway.

---

### Post by Boomy on 2007-02-02
Easy password cracks in Windows make it convienient for computer technicians. If someone has access to your hardware they own your machine, so it doesn't matter how hard your password is to crack.

---

### Post by The Noble on 2007-02-02
Want really good protection? Password protect the bios, encrypt the hard drive, make your own file system, have a really good password, and bolt the bloody laptop to your arm. Oh wait, why even care? It's only some ones and zeros, and you only need to make sure that it is a pain to even bother. Most people stealing and cracking computers are the equivalent of script kiddies, and there are 1000 people using crap passwords and windows per every linux user. I live in america, and I bet that my laptop would only be scrapped for parts, even if I have no password. I don't even know anyone who actually knows how to use linux in the first place, let alone anyone with mal intent.

---

### Post by ice60 on 2007-02-02
linux passwords add extra charactors called salt to the password you pick, then the hashes are stored where only root can access them. i think the reason windows passwords are so easy to crack is because a weakness in the algorithm they use - any password that's under 14 charactors can be cracked by using precompiled hash tables. i think you can disable LM hashes though and that will make it harder to crack.

i loved cracking lm hashes a few years ago and read up on it all, but i can't really remember much about it now. you can find out about it by searching for 'rainbow tables'

[http://en.wikipedia.org/wiki/Rainbow_table](http://en.wikipedia.org/wiki/Rainbow_table)

here's a video :D

[http://www.irongeek.com/i.php?page=videos/backtrackplaintext](http://www.irongeek.com/i.php?page=videos/backtrackplaintext)

here's an mp3 about it. i might listen to it seeing as i can't remember very much and i think this is a good audio
[http://www.hopenumbersix.net/mp3/16/password_cracking_and_time-memory_tradeoff.mp3](http://www.hopenumbersix.net/mp3/16/password_cracking_and_time-memory_tradeoff.mp3)

---

### Post by beercz on 2007-02-02
> **raul_ said:**
> Then you agree that the Live CD and the BIOS battery arguments are rubbish in this context :) Everyone can break into your house, but i think that's another reality that is not in the domain of computer security development
No, I think that passwording the bios and disabling the ability to boot from a CD ROM are very important.  All I am saying is that if one were to leave the front door unlocked (or laptop visible in the car etc ...) then the computer could be stolen, hard disk removed and accessed on another machine.

I'm not in disagreement with anything said in this thread, not at all.  I merely state that there is more to computer security than merely using firewalls, strong passwords, preventing bootable CD-ROM drives and password protecting the BIOS.  That's all.

No flaming please :-)

---

### Post by raul_ on 2007-02-02
cool vid

---

### Post by raul_ on 2007-02-02
> **beercz said:**
> No, I think that passwording the bios and disabling the ability to boot from a CD ROM are very important.  All I am saying is that if one were to leave the front door unlocked (or laptop visible in the car etc ...) then the computer could be stolen, hard disk removed and accessed on another machine.

I'm not in disagreement with anything said in this thread, not at all.  I merely state that there is more to computer security than merely using firewalls, strong passwords, preventing bootable CD-ROM drives and password protecting the BIOS.  That's all.

No flaming please :-)

Yes of course. We agree those are important measures. But I think we both agree that's out of Microsoft/Apple/Linux's domain, so there is no point bringing those up when talking about security features in operating systems. That was the context

---

### Post by koenn on 2007-02-03
Linux passwords may be harder to crack than Windows', but they can be cracked. In fact, on UNIX, sysadmins would run a pasword cracker regularly to check for weak passwords. Same program still exists for Linux. [http://en.wikipedia.org/wiki/John_the_Ripper](http://en.wikipedia.org/wiki/John_the_Ripper)
I used once to find passwords on an old SCO Unix. It worked.

---

### Post by Hossie on 2007-02-03
> **ice60 said:**
> linux passwords add extra charactors called salt to the password you pick, then the hashes are stored where only root can access them. i think the reason windows passwords are so easy to crack is because a weakness in the algorithm they use - any password that's under 14 charactors can be cracked by using precompiled hash tables. i think you can disable LM hashes though and that will make it harder to crack.

i loved cracking lm hashes a few years ago and read up on it all, but i can't really remember much about it now. you can find out about it by searching for 'rainbow tables'

[http://en.wikipedia.org/wiki/Rainbow_table](http://en.wikipedia.org/wiki/Rainbow_table)

here's a video :D

[http://www.irongeek.com/i.php?page=videos/backtrackplaintext](http://www.irongeek.com/i.php?page=videos/backtrackplaintext)

here's an mp3 about it. i might listen to it seeing as i can't remember very much and i think this is a good audio
[http://www.hopenumbersix.net/mp3/16/password_cracking_and_time-memory_tradeoff.mp3](http://www.hopenumbersix.net/mp3/16/password_cracking_and_time-memory_tradeoff.mp3)

But there is a much greater danger. In Linux you do not even need to crack the root password. You can just disable the password for the user root with a LiveCD. This always works.

---

### Post by Sarisar on 2007-02-03
> **Hossie said:**
> But there is a much greater danger. In Linux you do not even need to crack the root password. You can just disable the password for the user root with a LiveCD. This always works.

Bottom line, if you have physical access to the computer, then you can crack _any_ machine given enough time.  Bios passwords can be broken mostly by resetting the bios (touch two pins together IIRC) which allows you to boot off CDs.  Windows machines can normally simply be broken into by booting in safe mode and logging in as the administrator password (which by default has no password).  If not you can use the ultimate boot cd to change the password.

If you encrypt the entire drive, that should stop (or at least greatly slow down) breaking into the OS.  But as I said, if you have physical access (and I should also add unlimited time) then _anything_ can get cracked.

Then again, if someone has broken into your home, I think you have slightly bigger concerns then they may read some of your emails!

---

### Post by mhw on 2007-02-14
Just a note, though. While it's true that physical security is the most important, that's OS independent.

In terms of OS, Linux much better than Windows, as it salts the Hash function, so you can't use Rainbow Crack on it.

However, easy passwords are still easy....I have three accounts on a machine, 1 of which has a rubbish (i.e. dictionary) password. John The Ripper got it in less 5 mins...2 hours later and it's nowhere near the others.

This is why you need to use non-dictionary passwords - it makes random (brute force) attempts much harder.

---

### Post by mhw on 2007-02-16
A little update - 24 hrs later, and still no joy. Admittedly on a laptop, so you could go better with a new desktop, but unless someone has some serious hardware, they would be unlikely to brute-force a decent (non-dictionary) password.

---

### Post by fakie_flip on 2007-02-17
I've ran John the Ripper on my password in Ubuntu Edgy for more than two weeks, and it has not cracked my password yet. Has anyone found a way his or her own password can be cracked in Ubuntu better than this way?

```

$ sudo nice -n -20 john -restore
Loaded 1 password (FreeBSD MD5 [32/32])
guesses: 0  time: 14:19:21:50 (3)  c/s: 6219  trying: hlouf4x
guesses: 0  time: 14:19:21:54 (3)  c/s: 6219  trying: guzm6ea
guesses: 0  time: 14:19:21:55 (3)  c/s: 6219  trying: tbsHg1!
```

---

### Post by bender5788 on 2007-02-17
Ah all this talk of physical access and cracking passwords reminds me of an old and fairly well known saying (well at least a rephrasing of it).
No amount of security or skill will ever prevent someone with unlimited time and unrestricted  physical access from cracking your computer.

---

