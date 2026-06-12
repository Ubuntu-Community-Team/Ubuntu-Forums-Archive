---
title: "No HELP in Ubuntu forums!!!"
date: 2006-10-29
forum: The Cafe
---

### Post by expat1 on 2006-10-29
I have spent nearly a week trying to install Ubuntu and everytime I get through all the steps to finally click the install system button and when I'm lucky I can sometimes get to 49%.

I have read more postings than I care to and not just here in this forum.

I noticed when I searched for **"installation freezes"** that there are at least 2 pages of people with the same trouble.

On the first page there are **3846 views** (probably people with the same problem as well) and a grand total of **84 replies** (half of which are people saying they have the same problem)

I guess my main concern is **WHERE IS THE HELP? **

---

### Post by wieman01 on 2006-10-29
Had the same issue initially. A fresh CD & the latest ISO did the trick for me.

---

### Post by indytim on 2006-10-29
Also, it would help if you'd post the hardware basics you are trying to install to ie. processor, amount of ram etc.  If you're running a low RAM pc for install, you may have to go the text version install.

IndyTim

---

### Post by Sukarn on 2006-10-29
Yeah, you might have a corrupt CD.

---

### Post by expat1 on 2006-10-29
After nearly a week and checking my cd (that I burned at a speed of 2) and the md5sum checked out and the memory test is all good...what's the point to redownload it again and go through all the shxx again just to post again for help and not to get any?

And if I was "Lucky" enough to get it up and running and I maybe had trouble with something else.........where the hell would I get help from?

---

### Post by bigken on 2006-10-29
or even try the alternate iso 
things you must do 1st if you going to duel boot defrag windows 
back up any important data burn the ubuntu iso at a slower speed 
just a few tips ;)

---

### Post by wieman01 on 2006-10-29
The thing is that you cannot expect help for something that is very much dependent on your circumstances... If you know what I mean. The root cause could be...

1. broken CD ROM
2. currupted ISO
3. scratched CD
4. any other hardware failure
5. anything else you could think of

It's tough to give you any useful advice if you don't tell us anything about your system. So rather than complaining you should feed us with some more information as to what you have done so far & what hardware you have got, etc. I am pretty sure there is somebody out there who can help.

---

### Post by ComplexNumber on 2006-10-29
try another distro

---

### Post by Sef on 2006-10-29
> try another distro

Complex Number is not being sarcastic or anything negative. He's just making the point that no distro works with every piece of hardware.

---

### Post by DoctorMO on 2006-10-29
Most people burn on cheap cds which are not produced to high standards. your likly to get errors some of the times because the cd rom drives have excelent error correction built in. but it will fail if the errors are too much.

keeping blank cds for a long time, in the light or in the heat will damage them too.

As for help, I refute that remark since I own existance calls it into question.

---

### Post by fuscia on 2006-10-29
i had a dvd, that i had reinstalled off before, go bad on me (causing a stall in installation). a freshly burned cd did the trick. this might not be the answer to *your* problem, but it would certainly be a good place to start.

---

### Post by caravel on 2006-10-29
When you boot from the installation media there is a menu that allows you to run a consistency check.  That is what I have done every time I've installed.  The first Ubuntu disc I ever downloaded was corrupt so I burned it again (it helps to have a CDRW and not a CDR in this situation) and it was still corrupt, so I redownloaded the ISO image this time checking the checksum file, and it went fine from there on.

The point about hardware incompatibilies is another valid one.  In the past I've removed some odd hardware ( in this case my PCI RAID controller, which I no longer use thankfully) in order to get the distro installed and searched for the drivers and set it up manually later.  It was not easy.

---

### Post by ComplexNumber on 2006-10-29
> **Sef said:**
> Complex Number is not being sarcastic or anything negative. He's just making the point that no distro works with every piece of hardware.
i wouldn't have thought what i'd written was in question. with some distros, they just plainly refuse to work with certain hardware or hardware configurations.

---

### Post by roderikk on 2006-10-29
I have had troubles with installing quite a few times myself as well. Therefore I usually do a server install and than later do sudo aptitude install ubuntu-desktop from the command line. If you also want a graphical login also install gdm . Good luck!

---

### Post by chaosgeisterchen on 2006-10-29
> **ComplexNumber said:**
> i wouldn't have thought what i'd written was in question. with some distros, they just plainly refuse to work with certain hardware or hardware configurations.

The possibility of starting a flamewar upon that is high as always.

@the topic:

Just use a higher quality disc and another ISO. It will work.

---

### Post by Sunnz on 2006-10-29
I was thinking, why do you need to burn your own CD?? Don't ShitIt send out CDs anymore?? Can someone point to me (to a url perhaps) what happened??? 6.10 won't be supported???

---

### Post by mips on 2006-10-29
1. Download the **Alternate[COLOR="Red"][/COLOR]** iso (Forget about the Desktop one)
2. Verify the md5sum of the iso
3. Burn the iso at the **lowest** possible speed, on my burner that is x8
4. Verify the cd/md5sum after completion
5. reboot and start the install.

---

### Post by wieman01 on 2006-10-29
> **mips said:**
> 1. Download the **Alternate[COLOR="Red"][/COLOR]** iso (Forget about the Desktop one)
2. Verify the md5sum of the iso
3. Burn the iso at the **lowest** possible speed, on my burner that is x8
4. Verify the cd/md5sum after completion
5. reboot and start the install.
Well, he has done exactly that. See post #5.

---

### Post by Virogenesis on 2006-10-29
> **Sunnz said:**
> I was thinking, why do you need to burn your own CD?? Don't ShitIt send out CDs anymore?? Can someone point to me (to a url perhaps) what happened??? 6.10 won't be supported???

Because the edgy build isn't included, from what I understand is the next release will have a cd release, basically ones considered to be more stable than the other. 
Edgy is considered the bleeding edge release, while dapper is considered stable. 
So they send out dapper instead if you get what I mean.
Ps: Might be wrong, don't think I am if I am please do correct me,

Thanks.

---

### Post by halfvolle melk on 2006-10-29
> **wieman01 said:**
> Well, he has done exactly that. See post #5.
Nowhere does it explicitly say what CD was used but "to finally click the install system button" says it's the live CD.

---

### Post by missmoondog on 2006-10-29
i've found that you're almost "lucky" just to get a linux distro installed. worst part of any linux distro i've tried is the installation. when i first received the ubuntu 5.04 cd's from shipit, NONE of those 10 cd's worked! I downloaded and burned my own cd, and that worked fine. next day, i tried another shipit cd in a different computer and it worked fine. tried that same cd in yet another computer and it didn't work. switched to a different shipit cd and that one worked. 

didn't have any issues what so ever installing zenwalk 3.0 ([http://users.zenwalk.org/](http://users.zenwalk.org/)) on any of my 7 machines, since switching from kubuntu. zenwalk also has built in w32 codecs and several other goodies by default, that you have to search your butt off for in ubuntu!

---

### Post by Virogenesis on 2006-10-29
what motherboard have you got might by a chipset conflict,
Post system specs, include motherboard specs (make & model), graphics card, if you have anything like onboard SATA not being used, turn it off in the bios as this might help figure out the issue, you're having. 
Same goes for SCSI but do try another cd infact, try another distro see if the same thing occurs pick one which uses a recent kernel.

---

### Post by AgenT on 2006-10-29
First, lose the attitude. No one in these forms is your personal slave or paid assistant. People here volunteer their time to help others. Have some respect. At least people *are* trying to help you. If you are not being helped, the chances are that it is YOUR fault. Look at the insane amount of people that do receive help and have their problems fixed. And always remember, no one here owes you anything. If they even try to help you, be grateful.

Also, your bad attitude is just working against you. No one here has the time to help every single person, so they pick and choose. And with an attitude like yours, they probably choose to help the other person.

And if you want others to help you, you need to help them first. Give them as much information as you can. Saying your CD will not work is usually not good enough (this is why everyone is asking you for more information which you have a habit of not providing). Basic questions like "my cd will not let me install" will get nothing but basic answers such as "burn at lower speeds" or "redownload and try again". Sometimes this is good enough, sometimes it is not. Think about it, no one can mind read your thoughts or read your computer and software specifications, so how are they supposed to figure out a solution to your problem?

---

### Post by mips on 2006-10-29
> **halfvolle melk said:**
> Nowhere does it explicitly say what CD was used but "to finally click the install system button" says it's the live CD.

Yeah, i did not see any explicit references to the alternate cd and it seems most people new to ubuntu download the desktop cd.

I added the other 4 points simply for the sake of others that might read this thread.

---

### Post by Sunnz on 2006-11-10
> **Virogenesis said:**
> Because the edgy build isn't included, from what I understand is the next release will have a cd release, basically ones considered to be more stable than the other. 
Edgy is considered the bleeding edge release, while dapper is considered stable. 
So they send out dapper instead if you get what I mean.
Ps: Might be wrong, don't think I am if I am please do correct me,

Thanks.
But, [6.10]("http://www.ubuntu.com/news/610released"), IS released now, isn't it?

---

### Post by Virogenesis on 2006-11-10
> **Sunnz said:**
> But, [6.10]("http://www.ubuntu.com/news/610released"), IS released now, isn't it?
&?
You'll probably find that they will do a shipit release on the next version, this version of the year has NEVER been considered the major release.
Its more cost effective to print one release rather than two, a year.
If you want 6.10 pay for it or download it.
I'm sure ebay has some ubuntu cds.

---

### Post by Sunnz on 2006-11-10
I don't know, they did ship 5.04 and 5.10 no?

---

### Post by Virogenesis on 2006-11-10
I believe they did but they never had the amount of requests for cds and they didn't have the long term support release.

---

