---
title: "Help A nOOb get rid of the virus called Windows XP"
date: 2006-07-26
forum: The Cafe
---

### Post by jdseek on 2006-07-26
Hello all, First I must say, ubuntu is the best I have seen so far.  I installed 5.10 on my other laptop last summer and it is still running fine to this day.  Since then I have tried everything to rid my work laptop of the "Blue Screen of DEATH" otherwise known as Windows XP.  (no joke I have re-installed windows on my Gateway 7508GX [[specs]]("http://support.gateway.com/s/Mobile/Gateway/7000Series/5333sp2.shtml") 14 times due to some driver conflict with my printer driver that is , per microsoft "as yet unresolved". and ubuntu is still ticking on my old Gateway SOLO)
What brought my attention back to ubuntu was [this site]("http://kenkinder.com/evdo-pc5740/") in addition to the buzz about the bcm43xx drivers in 6.06.

There are a few reasons that ubuntu is not yet my primary work OS.  If we can resolve at least a few of these I can migrate to 6.06  This may be kindof hard, since I am about the worst kind of mobile.  I drive a truck and am never in the same place longer than 10 hrs.
If I can follow kenkinder's howto and get my PC5740 working.  That is a must as I use it to connect to the net for work.

Also, I am fairly sure that even if the new kernel driver for my BCM4318 doesn't work, I can get it working with ndiswrapper. I have done that before (all too often).

There are programs that I must have for work.  I just need the end result to be similar.  I am willing to learn new things to do them.
If anyone knows of a linux equivalant, or a way to get the same end result, please help.

1.  I use PC Miler to get point-to-point truck specific routing and milages.  I hope there is an open source app that does about the same thing.  I would buy the linux version of PC Miler if it wasn't for the [price]("http://www.axonstore.com/detail.aspx?ID=33") I only paid $299 for PC Miler Streets/Hazmat for windows.  That seems small in comparison.

2. I use CoPilotTruck and Microsoft Streets&Trips for GPS navigation.  Truck specific routing isn't mandatory on this one, (but would be nice {wishfull thinking}) so any good gps navagation with a map of the US would do.  Turn by turn would be great if it exists.  I don't mind paying a little for it, but would rather have open source, perhaps even contribute to the effort of a new trucker specific app.

3. I use AcroSoft's FormMax form filler to fill out <trip_number-report>.afm files which I print, sign, and move to the next question.  For this one, all the .afm files are provided by the company and have to be used as is (due to the formating and barcodes provided on them).  I would need a linux equal to this one, not sure if wine will get it done.

4. I use a complicated process involving HP scanning software, irfanview, and alot of luck to scan papers into multi-page <trip_number>.tif [CCITT FAX 4] (black and white) files for emailing to my company.  This may turn out to be alot easier in linux as it may be there is a scanning tool that can natively save to .tif CCITT FAX 4.  I need the ability to easily darken the scanned page if needed (and it often is).

5. This is a toughie.  I am legaly required to maintain a logbook, I don't want to go back to paper (yuck), I use [Drivers Daily Log]("http://www.driversdailylog.com/") to prepare and print my logbook.  I have researched this one at great length, there doesn't appear to be a linux equal to this one.  And most likely won't be for a while.  Until the "Evil Empire" falls and more truckers migrate to linux.

[edit] **update** Drivers Daily Log works wonderfully under wine, and with only a little begging I hope to get Mr. Bjorklund to send me a new activation code. [/edit]

Thanks all, JD

---

### Post by Brunellus on 2006-07-26
Global Comment:  Have you considered Crossover Office?  I've never used it, but reports are good for compatibility with 'work-type' software.

And as for PC Miler--HOLY COW that's a huge price.  Do you think you can contact them and ask them if they can give you a break on a single-driver license?  The price you're quoting is a five-driver license, so it'd make sense for firm with that many drivers, but if you're a sole owner/operator I can understand the sticker shock.  Does PC Miler work in WINE?  

Navigation software's gonna be thin on the ground.  

off-topic:  this has got to count as the most blue-collar post in a while on the ubuntuforums.  So much for the whole "linux is for beardy freaky hippies and pencilnecked geeks" stereotype. Ubuntu:  Linux for Human Being who Get Things Done?

---

### Post by RavenOfOdin on 2006-07-26
> **Brunellus said:**
> . Ubuntu:  Linux for Human Being who Get Things Done?

I'm right at this moment envisioning Tux looking like Larry the Cable Guy. :D

Anyway, HP driver support is easily managed under Linux. Look into the HPIJS/HPLIP Toolbox.

---

### Post by jdseek on 2006-07-26
Well, this is a quick development.  I just cleared the first (and largest) hurdle.  I am proud to announce that I am currently sitting on an off-ramp in florida somewhere typing to you from my very own ubuntu 6.06 system that is connected to the internet via a VERIZON WIRELESS PC5740!!!!  Having a bit of trouble getting updates via this connection, but it works wonderfully for email and web, that is all that is required on a day to day basis once I get this thing set up.  

As far as wine, I can tell you for sure that PC Miler DOES NOT work under wine, I have not tried Crossover Office to date, but i will need something to give me truck route miles from anywhere USA to anywhere-else USA. (helps to shave a few hrs off my book)

I have contacted ALK Tech. resellers about a lower price tag for pc miler, the best I have come up with is $2,999.99 for a 2 user linux install of PC Miler 20 HazMat (no Streets, bummer).

I think they do that due to the expectation that a linux user is the large trucking company's network.  Their main focus is on selling "complete" trucking company software suites.  Combine all their utils and you can run a 100,000 truck fleet from a few workstations.

My main concern now is to get the form filler thing done.  Anything that can successfully edit and print an existing .afm woud be wonderfull.

P.S.  I am a Blue Collar bearded pencilnecked hippie geek, always have been.  My Dad's dad was a garbage man, my Mom's dad was a programmer.

I have been trying to rid myself of windows since 1996, when I got my first copy of win95.  With only marginal success.  This laptop is the only one still running windoze, I have tried almost every flavor of mature distro, and quite a few immature ones in a vain attempt to rid myself of the "blue screen of death" that ends every windows session early.
[it's funny, a printer/scanner with the windows xp logo on it crashes windows xp and microsoft can't fix it, neither can HP]  

P.S.S.  Later tonight I will post a howto for making my Verizion PC5740 work with both the liveCD and the full install of ubuntu 6.06 in the networking subsection.  It was waaaay simpler that I thought it should be.
And so far (5 hrs uptime) it has been reliable on what windows would call "NationalAccess" area, even while moving at 70 mph (no, I am not a crazy, homicidal maniac, my wife was online while I drove).

Thanks guys, JD

---

### Post by jdseek on 2006-07-26
oh, yeah, forgot to tell ya.

Git-R-Done!!

---

### Post by jdseek on 2006-07-27
the [HowTo for Verizon PC5740]("http://www.ubuntuforums.org/showthread.php?p=1305540#post1305540") is up, check it out and let me know how to make it better, thx

JD

---

### Post by DoctorMO on 2006-07-27
The drivers Log is a problem, it looks at first light to be restricted by legal requirements, if we could get specifications a good python application might do the trick.

---

### Post by jdseek on 2006-07-27
> Originally posted by **RavenOfOdin**
Anyway, HP driver support is easily managed under Linux. Look into the HPIJS/HPLIP Toolbox.

I think we may have solved #4, thanks, now I just have to figure out how to work it.

I have an idea about #3, will know more tommorrow.

Thanks all

JD

---

### Post by siimo on 2006-07-27
you sure are a n00b for calling windows a virus.

idiots that go around bashing windows is one of the reason why linux geeks arent taken seriously - they just have to go n attack ms/windows at every opportunity they get, maybe they are just jealous that ms is the most successful software company ever.

grow up.

---

### Post by DoctorMO on 2006-07-27
Stop wining siimo, I hate windows and I don't care how good it is. I hate it politicly and theres nothing that will ever change my mind. I don't need to make excuses for it's technical problems or enthuse about how features in linux are better than windows it's doesn't even make sense to compare something to null.

If something doesn't work for me in Linux but it does in windows, it doesn't work for me period.

Now that you've seen what real windows haters are like lay off jdseek yea.

---

### Post by siimo on 2006-07-27
thanks for providing a good example of what i was talking about. 
:rolleyes:

---

### Post by frodon on 2006-07-27
Please keep on topic and be respectful

Thanks

---

### Post by jdseek on 2006-07-27
> Originally posted by siimo
 you sure are a n00b for calling windows a virus.

First, I openly aknowledge my noobie status in the linux community, It's a badge I have proudly worn for a while now.
Secondly.  I define a virus as code capable of causing the computer to crash.  I know that is a broad definition, but In my case, both Microsoft Windows XP and HP's Printer driver were in that catagory as the conflict between them routinely crashed my XP install beyond repair.  The worst part about it is Microsoft and HP knew about my issue since september 2005, and I am not the only one having this problem.  As of 2:10PM CST today, ten months later, there was still not a fix.  And nobody is holding their breath.  After 14 re-installs I decided to find a better way.  FYI, if it was still supported it I would still be running Win98SE for my work box.


Which brings me to the reason I am posting again.  Drivers Daily Log will run under wine. I am hoping that FormMax will also, but I can't get 32bit wine run DDL.exe, or anything else beyond the winecfg for that matter. This is most likely due to my architecture, I am running an AMD64, Will the i386 ubuntu version work for me? This install was so painless I would gladly repeat it if it gained me wine.  What do I have to loose in going back to 32bit linux?  Besides headaches with wine.

Thanks for helping me along.

JD

---

### Post by Brunellus on 2006-07-27
> **siimo said:**
> you sure are a n00b for calling windows a virus.

idiots that go around bashing windows is one of the reason why linux geeks arent taken seriously - they just have to go n attack ms/windows at every opportunity they get, maybe they are just jealous that ms is the most successful software company ever.

grow up.
ah, growing up.  I can remember the arguments now--

KID #1 (to KID #2): You're so immature.
KID #2:  no, YOU'RE immature!
"Am NOT"
"Are TOO"

**Fight ensues**

I'm going to say that pointless microsoft flaming is distasteful and, well, SO, like, 2001 already.  I will also say that Ballmer & Co. have variously described Linux and other free software as a "virus" or "communistic," so it's not as if there's a great deal of moral high ground to be occupied.  

But let's keep the asterisks out of this thread.

---

### Post by erikpiper on 2006-07-27
Never used wine.. But 32 bit works just fine on Amd 64- You will want to install the K7 kernel from the repos after you install tho (Like 686- but for AMD procs. It is 32 bit)

---

### Post by jdseek on 2006-07-29
OK, I reinstalled ubuntu using the i386 image, updated to the K7 kernel, and completely updated my system again.

Wine installed OK this time. well, almost.  I was able to install DriversDailyLog using this command

```
sudo wine DDL330.EXE
```

DDL330.EXE is the windows installer for this program.

The installer appeared to work OK, however, attempting to run it resulted in this.
```

$ wine /home/me/.wine/drive_c/Program\ Files/Drivers\ Daily\ Log/driversdailylog.exe fixme:ole:CoRegisterMessageFilter stub
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  135
  Current serial number in output stream:  135
me@mybox:~$

```


how do I fix this?
On a most likely related note, AcroFill.exe, the executable for FormMax works but, when I load my .afm files all the text is missing.

Thanks in advance, JD

---

