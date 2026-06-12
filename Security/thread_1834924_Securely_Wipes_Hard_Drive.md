---
title: "Securely Wipes Hard Drive"
date: 2011-08-28
forum: Security
---

### Post by karmila on 2011-08-28
Hi All...

Last month I need to rent a notebook for my work. And next week i will return the notebook.
So, what application i can use for completely erase the data on the disk?
Because i store some company and client data in it.

Thanks.

---

### Post by Lampi on 2011-08-28
use shred:

```
sudo shred -vzn0 /dev/partition-you-want-to-wipe
```

---

### Post by docbop on 2011-08-28
Google for DBAN  Dericks Boot And Nuke  it is bootable linux for doing secure wipes of hard drives. It offer assorted levels secure wipes, needless to say the more secure the longer it takes. I have worked for banks and others with sensitive data and we used DBAN to wipe drives.  I keep a copy of DBAN in my toolkit of CD's it's real handy.   

Also what is nice is you can start it, then remove the CD and let it run and just power off when done.

---

### Post by haqking on 2011-08-28
> **karmila said:**
> Hi All...

Last month I need to rent a notebook for my work. And next week i will return the notebook.
So, what application i can use for completely erase the data on the disk?
Because i store some company and client data in it.

Thanks.

Degauss it ;-)

---

### Post by walt.smith1960 on 2011-08-28
The question unasked is whether it needs to be returned with the operating system intact. If so, degaussing or DBAN probably may not be a viable option.  Too late now but for others assuming there's an OS and apps installed when you get it, you could create an image.  When you're done, you can do a secure wipe then restore the image and it'll be exactly like it was when you got it.  If you got it bare naked, nuke away:P. That's how I'd handle it anyway.

---

### Post by karmila on 2011-08-28
> **Lampi said:**
> use shred:

```
sudo shred -vzn0 /dev/partition-you-want-to-wipe
```

Thanks for pointing me 'shred'
I read the manual but don't yet really understand 'n0' part from the option. :confused:

> **docbop said:**
> Google for DBAN  Dericks Boot And Nuke  it is bootable linux for doing secure wipes of hard drives. It offer assorted levels secure wipes, needless to say the more secure the longer it takes. I have worked for banks and others with sensitive data and we used DBAN to wipe drives.  I keep a copy of DBAN in my toolkit of CD's it's real handy.   

Also what is nice is you can start it, then remove the CD and let it run and just power off when done.

Found it!
Thanks. Once again, a great application that not much people know about :)

> **haqking said:**
> Degauss it ;-)

Can you point me a link how to do it?

> **walt.smith1960 said:**
> The question unasked is whether it needs to be returned with the operating system intact. If so, degaussing or DBAN probably may not be a viable option.  Too late now but for others assuming there's an OS and apps installed when you get it, you could create an image.  When you're done, you can do a secure wipe then restore the image and it'll be exactly like it was when you got it.  If you got it bare naked, nuke away:P. That's how I'd handle it anyway.

They only rent the hardware.
So, I can do everything best to wipe out the data completely :)

Sorry for forgot to mention it before.

---

### Post by haqking on 2011-08-28
I was joking about the degaussing ;-)

shred should do what you want

---

### Post by karmila on 2011-08-28
> **haqking said:**
> I was joking about the degaussing ;-)

shred should do what you want

LoL :P
I should have known that.

So i need live cd then, if i want to to shred all disk?

```
# shred -u -n 5 /dev/sda
```
Is the command above okay?

---

### Post by Thewhistlingwind on 2011-08-28
Of the course, if the data isn't on there yet, may I recommend encryption? (Which, if done right, is a guaranteed way to stop anyone from getting the data in readable form.)

---

### Post by haqking on 2011-08-28
> **Thewhistlingwind said:**
> Of the course, if the data isn't on there yet, may I recommend encryption? (Which, if done right, is a guaranteed way to stop anyone from getting the data in readable form.)


he doesnt want to encrypt data, he wants to remove all trace of it as he is handing the laptop back and doesnt want to leave data on the machine.

---

### Post by agillator on 2011-08-28
Although I use 'shred' and 'wipe' and other techniques at times depending on the need, for your purpose I would second the recommendation for Derick's Boot and Nuke (DBAN). It is the simplest, and in my mind the most effective, way to sanitize a drive. It is accepted for drives containing Top Secret data according to military regulations which should tell you how effective it is.  And by the way, that means ANY drive it finds on the computer. If you have a drive attached you DON'T want nuked, you need to physically disconnect it.   So I suggest you download DBAN, burn the CD, then boot from the CD. When done, keep the CD. It comes in handy.

---

### Post by karmila on 2011-08-28
> **Thewhistlingwind said:**
> Of the course, if the data isn't on there yet, may I recommend encryption? (Which, if done right, is a guaranteed way to stop anyone from getting the data in readable form.)

Thanks for suggestion but now...

> **haqking said:**
> he doesnt want to encrypt data, he wants to remove all trace of it as he is handing the laptop back and doesnt want to leave data on the machine.

> **agillator said:**
> Although I use 'shred' and 'wipe' and other  techniques at times depending on the need, for your purpose I would  second the recommendation for Derick's Boot and Nuke (DBAN). It is the  simplest, and in my mind the most effective, way to sanitize a drive. It  is accepted for drives containing Top Secret data according to military  regulations which should tell you how effective it is.  And by the way,  that means ANY drive it finds on the computer. If you have a drive  attached you DON'T want nuked, you need to physically disconnect it.    So I suggest you download DBAN, burn the CD, then boot from the CD. When  done, keep the CD. It comes in handy.

Thanks i'll go with [Darik's Boot and Nuke ]("http://www.dban.org/")

---

### Post by Thewhistlingwind on 2011-08-28
> **haqking said:**
> he doesnt want to encrypt data, he wants to remove all trace of it as he is handing the laptop back and doesnt want to leave data on the machine.

Who said you can only do one or the other? ;)

---

### Post by Lampi on 2011-08-29
> **karmila said:**
> So i need live cd then, if i want to to shred all disk?
That's the idea if you want to wipe the whole disc. Make sure to use the right partition: it won't ask twice, it will just do it >> your data is gone.

> **karmila said:**
> ```
# shred -u -n 5 /dev/sda
```
Is the command above okay?
-u is useless if you wipe partitions, this is useful to wipe specific files in a filesystem.

-n 5 is overkill and will take hours on a large drive - I bet nobody is able to recover data after you wiped it once, especially on large drives.

using -z is up to you, I usually do it like that

---

### Post by karmila on 2011-08-29
> **Lampi said:**
> That's the idea if you want to wipe the whole disc. Make sure to use the right partition: it won't ask twice, it will just do it >> your data is gone.


-u is useless if you wipe partitions, this is useful to wipe specific files in a filesystem.

-n 5 is overkill and will take hours on a large drive - I bet nobody is able to recover data after you wiped it once, especially on large drives.

using -z is up to you, I usually do it like that

Really much thanks Lampi :popcorn:

---

### Post by wacky_sung on 2011-08-30
Actually those so called secure data wipes are not very secure because no matter many times / layer of wipes you have done especially you have stored sensitive data .There is a still a possibility for your data to be retrieved. The only best data wipe is to use a hammer to crash your hard disk which totally damage crash the hard disk dics inside.

---

### Post by tgm4883 on 2011-08-30
> **wacky_sung said:**
> Actually those so called secure data wipes are not very secure because no matter many times / layer of wipes you have done especially you have stored sensitive data .There is a still a possibility for your data to be retrieved. The only best data wipe is to use a hammer to crash your hard disk which totally damage crash the hard disk dics inside.

*Source needed

---

### Post by zkissane on 2011-08-30
> **agillator said:**
> It is accepted for drives containing Top Secret data according to military regulations which should tell you how effective it is. 

While I love me some DBAN, no disk with TS data leaves its facility in one piece, even after a wipe.  They get physically pulverized into powder.

---

### Post by tubbygweilo on 2011-08-30
Discussion from another thread concerning the merits of dban vs dd


See thread [Have formatted my entire hardrive Still Rootkits]("http://ubuntuforums.org/showthread.php?t=1712761") post [#23]("http://ubuntuforums.org/showpost.php?p=10592422&postcount=23") & [#24]("http://ubuntuforums.org/showpost.php?p=10592819&postcount=24")

---

### Post by Thewhistlingwind on 2011-08-30
> **wacky_sung said:**
>  The only best data wipe is to use a hammer to crash your hard disk which totally damage crash the hard disk dics inside.

That part is DEFINITELY wrong.

You don't smash it with a hammer.

You take out the individual plates and grind them down with a wood file.

At this point of course, recovery is very expensive, so unless your hiding your data from the NSA, you probably don't have to worry about anyone recovering the data.

Also, I've had plenty of people tell me that:

1) The guttman wipe is voodoo, and totally unnecessary.

2) The guttman wipe isn't enough.

*shrug* Which is why I recommend encryption over "wipes" in every case.

That's unambiguously secure.

---

### Post by tubbygweilo on 2011-08-30
Encrypt and forget but then [538]("http://xkcd.com/538/") trumps all:P

---

### Post by tgm4883 on 2011-08-30
> **Thewhistlingwind said:**
> That part is DEFINITELY wrong.

You don't smash it with a hammer.

You take out the individual plates and grind them down with a wood file.

At this point of course, recovery is very expensive, so unless your hiding your data from the NSA, you probably don't have to worry about anyone recovering the data.

Also, I've had plenty of people tell me that:

1) The guttman wipe is voodoo, and totally unnecessary.

2) The guttman wipe isn't enough.

*shrug* Which is why I recommend encryption over "wipes" in every case.

That's unambiguously secure.

> **tubbygweilo said:**
> Encrypt and forget but then [538]("http://xkcd.com/538/") trumps all:P

While encryption is a really great idea, it is not the end all be all for securing your data. By itself, it still fails to protect against an evil maid attack

---

### Post by agillator on 2011-09-01
The only real way to wipe a hard drive is to disassemble it, degauss the platters, run them through an acid bath, grind the remains to powder, launch them into the sun, and shoot all the people who handled them during the process. The point is let's don't go overboard which is something we all tend to do on this subject. Something like the preceeding seems just a little extreme when the item of concern is an image of last month's rent check. Today's battle plans may be useless to the enemy tomorrow, in which case security concerns are different than if they were useful a year from now. I know your personal information is important to you, but do you really think the NSA is interested enough in you to spend the time and money to extract it from your hard disk? If so, you have more problems than destroying your personal information. There has been a lot of good, useful information here. But let's do keep our perspective. The original objective was, after all, to drain the swamp.

---

### Post by wacky_sung on 2011-09-01
> **agillator said:**
> The only real way to wipe a hard drive is to disassemble it, degauss the platters, run them through an acid bath, grind the remains to powder, launch them into the sun, and shoot all the people who handled them during the process. The point is let's don't go overboard which is something we all tend to do on this subject. Something like the preceeding seems just a little extreme when the item of concern is an image of last month's rent check. Today's battle plans may be useless to the enemy tomorrow, in which case security concerns are different than if they were useful a year from now. I know your personal information is important to you, but do you really think the NSA is interested enough in you to spend the time and money to extract it from your hard disk? If so, you have more problems than destroying your personal information. There has been a lot of good, useful information here. But let's do keep our perspective. The original objective was, after all, to drain the swamp.

The only way to full destroy the data forever is to destory the disc of the hard disk. If you think by using software to wipe it is not a full fool solution.I have no doubt why sensitive on the hard disk is so easily to obtain.

---

### Post by cryptotheslow on 2011-09-01
@wacky_sung Please do provide some evidence for your claims. I challenge you to take a hard drive with data on, DBAN it then recover the data.

---

### Post by tgm4883 on 2011-09-01
> **cryptotheslow said:**
> @wacky_sung Please do provide some evidence for your claims. I challenge you to take a hard drive with data on, DBAN it then recover the data.

DBAN isn't even necessary. Nobody every accepted "[The Great Zero Challenge]("http://hostjury.com/blog/view/195/the-great-zero-challenge-remains-unaccepted")". *Theoretically* you might need it but dd seems to work just fine

---

### Post by cryptotheslow on 2011-09-01
Indeed. Most I've ever done is one pass from /dev/random and occasionally use sfill of just zeros if I've recently deleted a bunch of files I want to be sure are gone. Certainly neither Testdisk nor Photorec can find anything afterwards.

But then it doesn't really matter to me, anything critical (passwords / bank stuff etc.) is kept in a Truecrypt container - and that's just to keep it away from prying eyes should the PC get stolen or I lose my USB thumb.

Life's just to short to spend any more time worrying about it. I figure if "they" (whoever that is) really want it, then my door will be kicked in and I won't have any choice in the matter. And that simply isn't going to happen just to get the details to access my usually overdrawn bank account :)

---

### Post by wacky_sung on 2011-09-02
> **cryptotheslow said:**
> @wacky_sung Please do provide some evidence for your claims. I challenge you to take a hard drive with data on, DBAN it then recover the data.

I will take your challenge with USD XxX Million.Send the hard disk to me and i will prove it all. Don't cut the crap to waste my time when i recover it.

---

### Post by tgm4883 on 2011-09-02
> **wacky_sung said:**
> I will take your challenge with USD XxX Million.Send the hard disk to me and i will prove it all. Don't cut the crap to waste my time when i recover it.

meh empty promise with impossible scenario. Get real

---

### Post by bodhi.zazen on 2011-09-02
One pass of dd is considered sufficient.

Citation : [http://www.springerlink.com/content/408263ql11460147/](http://www.springerlink.com/content/408263ql11460147/)

If you are going to make a claim you can recover data that has been over written you will need a more credible citation then "send me the hard disk and some cash".

If you need more then that , look at scrub

scrub -fSp dod /dev/sda

Citation: [man scrub](http://linux.die.net/man/1/scrub)

> The dod scrub sequence is compliant with the DoD 5220.22-M procedure for sanitizing removeable and non-removeable rigid disks which requires overwriting all addressable locations with a character, its complement, then a random character, and verify. Please refer to the DoD document for additional constraints.

scrub is faster then dd or dban ;)

---

### Post by wacky_sung on 2011-09-02
> **tgm4883 said:**
> meh empty promise with impossible scenario. Get real

Well, get real if you can afford to pay me as i got a team working together with me. FYI i used to work in hard disk manufacturer and we have recovered countless near impossible but we did it. Action speak louder than words, if you can afford to pay and i will recover.PM me your sum before you conclude with your own personal theory which does not stand.

---

### Post by Thewhistlingwind on 2011-09-02
> **wacky_sung said:**
> Well, get real if you can afford to pay me as i got a team working together with me. FYI i used to work in hard disk manufacturer and we have recovered countless near impossible but we did it. Action speak louder than words, if you can afford to pay and i will recover.PM me your sum before you conclude with your own personal theory which does not stand.

From the sound of your jive, it costs millions to recover a drive? (Without even debating the possibility, validity, or credibility of your claims.) If this is the case, I doubt OP is carrying million dollar data.

And he can't smash the drive, he's RENTING the hardware.

---

### Post by tgm4883 on 2011-09-02
:roll:> **wacky_sung said:**
> Well, get real if you can afford to pay me as i got a team working together with me. FYI i used to work in hard disk manufacturer and we have recovered countless near impossible but we did it. Action speak louder than words, if you can afford to pay and i will recover.PM me your sum before you conclude with your own personal theory which does not stand.

:roll: We've already posted information on why a simple dd pass is enough. You are saying it isn't, and have shown no proof. Unfortunately for you, the burden of proof falls on you.

---

### Post by bodhi.zazen on 2011-09-02
> **tgm4883 said:**
> :roll:

:roll: We've already posted information on why a simple dd pass is enough. You are saying it isn't, and have shown no proof. Unfortunately for you, the burden of proof falls on you.

+1

Data recovery from a failed drive != recovering data that has been over written.

---

### Post by wacky_sung on 2011-09-02
> **tgm4883 said:**
> :roll:

:roll: We've already posted information on why a simple dd pass is enough. You are saying it isn't, and have shown no proof. Unfortunately for you, the burden of proof falls on you.

Well, what you guys see is only the conventional theory where you don't even know the hard disk is manufactured and those damage discs inside the hard disk being recovered. I will show you proof when you give me your hard disk.It is pointless for me to debate over things in which already proven in the market. I have no doubt why sensitive data has been recovered from ignorance / lack of knowledge from people who think that's the only way. By the way, are you aware that some people are paying huge sum of dollar to recover their love ones decease data , police retrieving sensitive data from crime, etc. Good luck with your venture of your theory.I shall end here.

---

### Post by cryptotheslow on 2011-09-03
Yes, in the past I have used professional services to recover essential data from damaged or completely failed drives. And yes, they are expensive - but then it is a specialist subject and they do have to maintain clean environments and a whole raft of expensive bench equipment to do the job.

But that is not what we are discussing here.

I will happily send you a working hard drive that has been wiped along with a directory and file listing of what was on it and **if **you manage to recover even one file that is identifiable as having been on the drive (i.e. not some generic OS related file) then I'll pay your fee.

You will waste a lot of time trying and it will cost me nothing as you will be unable to do so. If you do manage it then great - you get paid and will certainly have a unique position within the data recovery field. Hell, I'll even run some cheesy blog on the whole thing you can refer to when you succeed :D

---

### Post by tgm4883 on 2011-09-03
> **cryptotheslow said:**
> Yes, in the past I have used professional services to recover essential data from damaged or completely failed drives. And yes, they are expensive - but then it is a specialist subject and they do have to maintain clean environments and a whole raft of expensive bench equipment to do the job.

But that is not what we are discussing here.

I will happily send you a working hard drive that has been wiped along with a directory and file listing of what was on it and **if **you manage to recover even one file that is identifiable as having been on the drive (i.e. not some generic OS related file) then I'll pay your fee.

You will waste a lot of time trying and it will cost me nothing as you will be unable to do so. If you do manage it then great - you get paid and will certainly have a unique position within the data recovery field. Hell, I'll even run some cheesy blog on the whole thing you can refer to when you succeed :D

+1 I'll add to this

---

### Post by cryptotheslow on 2011-09-03
OK - I'll have a think through about how this challenge could be done so as to provide a mechanism that is irrefutable by either side should a file be recovered.

It would certainly require data escrow of some kind. A quick summary proposal that comes to mind:

1. Drive is wiped (dd / shred / DBAN) - TBD which method.
2. An OS is installed to the drive. - TBD what OS / partition format
3. Several data files are saved to a known location. TBD - format and content of files.
4. Drive image to file taken.
5. Drive image file strongly encrypted. Maybe Truecrypt with a 1MB key?
6. Encrypted image sent to 3rd party escrow.
7. Drive is wiped and despatched to whoever takes up the challenge.
8. Challengee provides "recovered" file to 3rd party escrow for validation.
9. Challenger provides keyfile to 3rd party escrow.
10. Escrow validates recovered file is genuine. TDB how? - Content check / CRC etc.?


If multiple challengees then for each drive the contents of the data files must be unique and a new encrypted image file made and held in data escrow.

If there's enough community interest in this we could even set up a monetary escrow that people can donate too to serve as a reward for the first challenger to successfully recover a file. Not sure this is too great an idea though - I'd personally prefer to see it done just as a technical capability exercise.

It could be an interesting project if done properly. An open challenge to all comers. Not sure where all the drives would come from though :)

---

### Post by tgm4883 on 2011-09-04
> **cryptotheslow said:**
> OK - I'll have a think through about how this challenge could be done so as to provide a mechanism that is irrefutable by either side should a file be recovered.

It would certainly require data escrow of some kind. A quick summary proposal that comes to mind:

1. Drive is wiped (dd / shred / DBAN) - TBD which method.
2. An OS is installed to the drive. - TBD what OS / partition format
3. Several data files are saved to a known location. TBD - format and content of files.
4. Drive image to file taken.
5. Drive image file strongly encrypted. Maybe Truecrypt with a 1MB key?
6. Encrypted image sent to 3rd party escrow.
7. Drive is wiped and despatched to whoever takes up the challenge.
8. Challengee provides "recovered" file to 3rd party escrow for validation.
9. Challenger provides keyfile to 3rd party escrow.
10. Escrow validates recovered file is genuine. TDB how? - Content check / CRC etc.?


If multiple challengees then for each drive the contents of the data files must be unique and a new encrypted image file made and held in data escrow.

If there's enough community interest in this we could even set up a monetary escrow that people can donate too to serve as a reward for the first challenger to successfully recover a file. Not sure this is too great an idea though - I'd personally prefer to see it done just as a technical capability exercise.

It could be an interesting project if done properly. An open challenge to all comers. Not sure where all the drives would come from though :)

I honestly think you are overthinking this, but if you want to make this super secure do it like this. (IMHO, I think just copy a file to the drive, format it, then send it for recovery)

1) Someone encrypts a file with a private key that is not associated with a known public key. They then upload this encrypted file to a website that other people can download.
2) Format a drive in a Linux capable format (I have many extra drives I could donate to this cause)
3) Copy the public key to the hard drive
4) Overwrite the drive with dd
5) Send drive to whoever wants to recover it
6) They then use the public key they recover from the hard drive to decrypt the file, posting the contents of the file to a forum.
7) Whoever encrypted the file then posts the public key
8) Everyone else can then decrypt the file for verification

No escrow company needed

---

### Post by karmila on 2011-09-04
Hi guys, thanks for all suggestions and the discussion :)

So, if i may conclude i have this options:
**1. shred**
> **Lampi said:**
> use shred:

```
sudo shred -vzn0 /dev/partition-you-want-to-wipe
```

**2. DBAN**
> **docbop said:**
> Google for DBAN  Dericks Boot And Nuke  it is  bootable linux for doing secure wipes of hard drives. It offer assorted  levels secure wipes, needless to say the more secure the longer it  takes. I have worked for banks and others with sensitive data and we  used DBAN to wipe drives.  I keep a copy of DBAN in my toolkit of CD's  it's real handy.   

Also what is nice is you can start it, then remove the CD and let it run and just power off when done.

**3. scrub**
> **bodhi.zazen said:**
> If you need more then that , look at scrub

```
scrub -fSp dod /dev/sda
```

Citation: [man scrub]("http://linux.die.net/man/1/scrub")



scrub is faster then dd or dban :wink:

**4. dd**
> **bodhi.zazen said:**
> One pass of dd is considered sufficient.

Citation : [http://www.springerlink.com/content/408263ql11460147/](http://www.springerlink.com/content/408263ql11460147/)

If you are going to make a claim you can recover data that has been over  written you will need a more credible citation then "send me the hard  disk and some cash".

*However, if i want to wipe entire disk, what options i should use with dd? Considering i will run it from a live cd.*


And yes, encrypting the partition should make the data safer ;)

---

### Post by bodhi.zazen on 2011-09-04
> **karmila said:**
> Hi guys, thanks for all suggestions and the discussion :)

*However, if i want to wipe entire disk, what options i should use with dd? Considering i will run it from a live cd.*


```
d if=/dev/zero of=/dev/sda bs=1M
```

Will wipe the first hard drive. /dev/sdb is the second, and on.

---

### Post by karmila on 2011-09-04
> **bodhi.zazen said:**
> ```
d if=/dev/zero of=/dev/sda bs=1M
```Will wipe the first hard drive. /dev/sdb is the second, and on.

Thank you :popcorn:

---

### Post by cryptotheslow on 2011-09-05
> **tgm4883 said:**
> I honestly think you are overthinking this, but if you want to make this super secure do it like this. (IMHO, I think just copy a file to the drive, format it, then send it for recovery)

1) Someone encrypts a file with a private key that is not associated with a known public key. They then upload this encrypted file to a website that other people can download.
2) Format a drive in a Linux capable format (I have many extra drives I could donate to this cause)
3) Copy the public key to the hard drive
4) Overwrite the drive with dd
5) Send drive to whoever wants to recover it
6) They then use the public key they recover from the hard drive to decrypt the file, posting the contents of the file to a forum.
7) Whoever encrypted the file then posts the public key
8) Everyone else can then decrypt the file for verification

No escrow company needed

That's much simpler :D

The only real problem now is that the only person who claims it can be done wants $NNN million up front....   errrr right :lolflag:

---

### Post by DZ* on 2011-09-05
> **cryptotheslow said:**
> That's much simpler :D

The only real problem now is that the only person who claims it can be done wants $NNN million up front....   errrr right :lolflag:

But how do we distinguish between the two equally unlikely events: recovered content vs broken encryption? :-)

---

