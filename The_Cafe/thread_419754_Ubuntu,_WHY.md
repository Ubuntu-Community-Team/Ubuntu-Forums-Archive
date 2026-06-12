---
title: "Ubuntu, WHY?"
date: 2007-04-23
forum: The Cafe
---

### Post by MichaelSM on 2007-04-23
Hi. My name is Michael. I live in Australia which is a big place. Broadband Internet isn't available everywhere, plus some people can't afford it anyway, so Dial-up is essential for people in remote areas.
I'm one of those strange people who gather computer parts from all over the place, and make up boxes for others who cannot afford to buy PCs. 
Some months ago I decided upon Ubuntu 6.10 as my preferred distro. Gnome is nice and uncluttered, just a nice desktop to use. 
In the battle to get Linux/Debian/Ubuntu accepted, what clown made it so impossible and difficult to run dial-up on Edgy? !!!
Dial-up runs like a wet dream on EVERY OTHER DISTRO I'VE TRIED! 
It's ridiculous that someone like me has had to spend hours upon hours trying to get something so simple installed and running in Edgy, to NO AVAIL!!!! 
Somebody, somewhere, sometime, made an executive decision to stuff up dial-up with Edgy. WHY???
Everyone wants a sensible OS with Linux. Ubuntu is splendid in many ways, but it stuffs up in the most important area of all: Dial-up Internet connection. If you can't get that up and running, then all the other paraphernalia is a complete waste of time. 
Bloody Hell, when Linux first was devised, broadband didn't even exist! What sort of idiot would deliberately disable dial-up in Edgy? if the whole idea of Linux distros as an alternative to MS was and is to get it OUT THERE with people using it every day, why deliberately put in impediments to prevent it? 
Why, of all distros, was Edgy singled out to be a horror story with dial-up? 
Going by the many pages and posts on this excellent forum; and thank you to all the contributors who've tried to make sense of such a debacle - none of it is necessary at all.
I'm aware that open-source OS's depend upon the hard work and goodwill of hundreds of persons who compile and distribute Ubuntu and other Linux distros. 
However, it all becomes a bit of a joke when pretty desktops and themes take over from basic functionality. What's the point of a cute desktop if you can only get on the Net with broadband? 
Why is it, to repeat myself, that Mandriva and Xandros (to name only two) have no issues with dial-up at all, especially with external serial modems. It's just plug-and-play like a LAN connection. I can understand problems with Winmodems, but most of us are savvy enough only to play with SmartLink and Conexant chips for PCI installs, and Linux-ant is supportive of those chips.
Either way, it's a joke. Since when should someone getting on in their years have to access /modem/dev/ tty files and fiddle with editing Init strings etc. SIMPLY TO ENABLE A DIAL-UP CONNECTION? How f@#king absurd. !!! in this modern day and age!!!
To get back to my main point.....whichever geek from Ubuntu decided to abandon and to booby-trap Edgy re. dial-up needs a session with a realist. Why disable  something which was necessary, and which worked? 
I've accessed most parts of my tiny brain recently, trying to get dial-up running on Edgy, and there are pages upon pages in Ubuntu Forums trying to help with this stupid problem, which exists nowhere else. 
I think it's about time someone took a deep breath and owned up to making a silly mistake, and enabled a simple patch to rectify a deliberate modification which was both inane and unnecessary re. Edgy: OK I have a choice now otherwise. Go back to Dapper or update to Feisty in some forlorn hope that I can get my Mum on the Internet and using up hundreds of megs in the process of downloading and re-installing, JUST, and I repeat, JUST !!! to enable a dial-up connection! You HAVE to be kidding.....what a joke. 
if Ubuntu is trying to get out into the PC community, we'd better take a long and hard look at ourselves. 
Cheers, Michael.

---

### Post by koshatnik on 2007-04-23
Use a different distro. Or go back to windows. Or buy a mac. Destroy your keyboard. Go surfing. Ride a bike.

The possibilities are endless.

---

### Post by MichaelSM on 2007-04-23
Thank you for the advice. Considered and rejected. Mike.

---

### Post by Eddie Wilson on 2007-04-23
Very Strange. Where I live I can only get dial-up. I've had no problems with Edgy even tho my main system is Dapper. All I did to setup dial-up was  to install Gnomeppp. I set it up and had no more problems of any kind. Edgy really didn't have a good way to setup dial-up and thats why I used Gnomeppp.
Eddie

---

### Post by frup on 2007-04-23
I'm running feisty and I don't have a dial up connection but the network settings modem settings seems to only require the dialup number and username and password.
On the next tab I can choose which modem to choose (/dev/modem or ttys0-5 things) Tones or Pulses and finally if the connectiong is default, uses the ISP's DNS etc etc.

I wouldn't have thought anything would be missing especially when /dev/modem shows ups... I thought that was ubuntu registering my modem as a device... but again I've never used a modem on ubuntu... many probably haven't, maybe, because less people use modems, no ones realised it was broken?

---

### Post by MichaelSM on 2007-04-23
Hi Eddie. Nice to hear a good luck story, and I mean it! You mentioned Dapper: the main point I was on about was the strange trip with Edgy. Check out the forums to see some of the multitude of pages written about Edgy/dial-up. It isn't pretty. Something went a bit awry between D and E which made everything nearly impossible with dial-up. It's there on the books. I'm not the only person who's had a hard time. 
Cheers, 
Mike.

---

### Post by koshatnik on 2007-04-23
> **MichaelSM said:**
> Thank you for the advice. Considered and rejected. Mike.

My pleasure. Try and come across less ranty in future posts though.

---

### Post by Tundro Walker on 2007-04-23
[http://ubuntuforums.org/showthread.php?t=202838](http://ubuntuforums.org/showthread.php?t=202838)

That lists some ways to tweak online performance.  Not clear if it will impact dial-up or not.

For issues like this, I'd like to say it would be nice if Ubuntu had a "bounty hunter" type thing going, where someone could post a "bounty" to get a dev/programmer type to solve an issue.  Canonical would still have it's core-dev's working on main issues, but if someone had a side issue, they could bounty it for a 3rd party to look into.  However, I'd then be worried about gun-slinger types showing up sloppily coding something just to get the money, and then causing headaches for Canonical trying to integrate their weird code (which may work by itself or with a certain setup) into Ubuntu (which may end up causing confilcts.)

I'll take a different stance then some of the other folks that will reply to your some-what flamish comments.  IE: you're going to get some folks saying "it sounds like you don't like Ubuntu, so go use something else".  I'd like to think of this differently...Ubuntu must be doing a lot of things right if you've chosen to stick with it instead of other OS' that have better dial-up.  So, you'd like to simply see the dial-up work better, then you'd be a happy camper.

You might want to search around the forums and net in general to see if there really is a dial-up issue with Ubuntu.  Just from a quick google, I didn't find many complaining about it.  The chief complaint seemed to be that it didn't work too good with dial-up, because Ubuntu relies heavily on d/l'ing things from repo's.  So, dial-up folks may have issues since they're always d/l'ing things slow.  (And some of the patches and updates are huge...like 20mb or more)

Now, if you're having issues with disconnects, I know some have set disconnect limits.  For the telecom company that I work for (which offers dial-up ISP), if customers are on longer than 30 min w/o activity, they're auto-disconnected.  If they're on for 8 consecutive hours, even if they're still active, they get auto-disconnected.  The company I work for does this because it's also a phone company that resells major phone service.  Even when a customer is just making a local call, we get charged min's towards the major account, so they want to limit as much as possible.  Other ISP's, which are not also phone companies, aren't as restrictive.  A couple years ago, I was using Everyone's Internet for dial-up, and I could d/l 100mb files over the course of 24 hours or so w/o getting bumped off.  Sometimes, I couldn't go 1 hour w/o getting bumped off.  Dial-up is just iffy to begin with, but with DSL and Broadband, has really become the red-headed step child of the internet crowd.  (Which is sad, because dial-up is still widely used and is easier to get.)

---

### Post by igknighted on 2007-04-23
1) Ubuntu comes on one CD.  They can only fit so much.  If you have specific needs, look for a distro that distributes on multiple CDs, as more software/drivers are available.

2) Modems almost never work well with linux, as much of the functionality of common modems is built into the windows OS, not the modem itself.  As such, enabling these devices (called winmodems) is not easy.  If you know the chipset and brand of your modem, search for it on various linux sites to see how others got it working.

I promise you that there is no intention to leave modems out, but the modem manufacturers who build their devices around windows have done this.  If you want to help do something about this, email or write to you modem's manufacturer to complain about the lack of support for non-windows OS's.

---

### Post by MichaelSM on 2007-04-23
Hello FRUP. The weird thing about Ubuntu variants is how things change from one to the other, for no apparent reason. There seem to have been few problems if any using dial-up with 6.06, 'cause I used to use it myself; fine, then along came 6.10 which was a mess. I've been told that Feisty has rectified the dial-up problems. Cool. Wait and see. I can assure you that I'm not the only person having problems in this area. Also, what's weird is that everything can be in-putted to Gnome PPP and it's cool as on the face of it, but the connection is never accomplished. You have to try it to see it!
Cheers, Mike.

---

### Post by OffHand on 2007-04-23
Paragraphs are your friend ;)

---

### Post by MichaelSM on 2007-04-23
To Koshatnik. I apologise for my terse reply. Yes I made a rant, and I've been conscious of others who lose the plot on various issues. I guess I've joined them! I can only re-iterate my frustration that something so simple as a dial-up Internet connection was so deliberately mis-managed (a polite way to put it!) in Edgy, to the extent that there are pages and pages of crap on Ubuntu Forums regarding that particular matter, which, if you look, have no viable end. There is NO THREAD AT ALL which guarantees a certain and useful Internet connection with any sort of a dial-up modem, be it PCI or serial, in Edgy. Full stop. Unless one is a computer programmer, which I certainly am NOT, and neither are the friends and family whom I'm attempting to wean off Windows, which really isn't my problem at all. 
I appreciate the replies. It's an on-going issue. Thanks to all who responded.
Regards, Michael

---

### Post by MichaelSM on 2007-04-23
Hi, Offhand, I'm pretty good at paragraphs. I think you mean that you want them indented. If that makes any difference, I'll try it next time. 
Cheers,
 Mike.

---

### Post by Teg_Navanis on 2007-04-23
Or allow an extra space between paragraphs. Might not be the way you're taught it for print media, but it's convenient in online forums.

---

### Post by MichaelSM on 2007-04-23
Thank you, Teg_Navanis. It's just that when one gets going, protocols slip by the wayside. Spell-checkers aren't good at grammar and syntax. 
Spacing between paragraphs initialised forthwith.
Regards, Mike.

---

### Post by mips on 2007-04-23
> **OffHand said:**
> Paragraphs are your friend ;)

I was gonna mention that but i already told one person today, very tiring. I simply don't read their posts anymore.

---

### Post by dca on 2007-04-23
Not that this helps but I have had zero problems getting a seriel modem to work w/ Dapper.  It was as simple as going into System -> Administration -> Networking and letting Ubuntu auto-detect the modem.  The best feature I've found is the 'auto-re-connect' which allows dialing while the OS is still loading...  The only other OS that came close w/ dial-up is openSuSE 10.2 running KDE using YaST...  Where as Kubuntu stinks w/ modems because you rely on KPPP, Ubuntu uses the networking settings.  openSuSE's YaST is cross-platform so the set-up of your system is similar running KDE versus GNOME...

---

### Post by Tomosaur on 2007-04-23
> **MichaelSM said:**
> It's just that when one gets going, protocols slip by the wayside. 

Hello irony.

---

### Post by The Joe on 2007-04-23
Mike your post is rough. Remember, Ubuntu is in development, version by version. Don't be hard like that. Like you said, you had other distros that work, use them, you don't **have** to use Ubuntu.

Oh and btw, I don't find you strange for collecting computer parts and making computers for the poor, that's a great thing to do! (Now where's the thumbs up emoticon?)

---

### Post by forrestcupp on 2007-04-23
I'm not much help here, but I wonder if Feisty resolved the dial-up problems.  Anyway, Eddie Wilson said his main system is Dapper, but it also appears that he got dial-up working in Edgy too by using Gnomeppp.

---

### Post by goldaryn on 2007-04-23
> **MichaelSM said:**
>  few problems if any using dial-up with 6.06, then along came 6.10 which was a mess.

The LTS version exists for a reason..

---

### Post by dca on 2007-04-23
Indeed, in fact I only run 6.06 on my laptop & servers for that reason.  I don't expect to upgrade till the next LTS...  Dollars to doughnuts, 6.06 is a darn fine distro.  Not just desktop where it receives most of its accolades but also on the server.  One CD, and I can deploy a server w/ FTP & Samba in 25 mins.  One CD, that's better than carrying around my 3DVD collection of Debian and my 6CD collection of CentOS (the Directors Cut).....

---

### Post by jmagsho on 2007-04-23
Mike,

Not to state the obvious, but Edgy and Feisty are both considered to be 'development' releases I believe, and as such we all take our chances with regard to bugs, etc.

I too have experienced much frustration over things in Edgy that seemed to work just fine in Dapper.   I upgraded to Feisty last week, and found myself facing a whole other set of issues (network printing to my HP multifuction printer did not want to work after the upgrade.    After pulling out quite a bit of my hair, I finally figured out that it was a combination of a driver issue and a permissions issue that was causing my fits.   I was all set to revert back to Dapper because it was stable and in my experience rock solid.     If I come across something that I can't figure out as I move forward with Feisty, that is exactly what I'll do.

Good luck, and keep at it.

- Jason

---

### Post by Compucore on 2007-04-23
Depending on the type of modem in question. The earlier internal ISA modems you will not have that much of a problem since they have the UART chip and another chip called Rockwell which does take care of compressin and decompressing of the infor going to and from the computer through the modem. The PCI flavour winmodems more or less will not work unless your extremely lucky tha one has the same thing with the ISA models Again USR robotics has a PCI version that is almost exactly the same as the ISA and works very wellunder linux. Since it is a true modem and not a winmodems where they are missing the UART chips and the other chip that I had mentioned before. Some of the modem vendors don't use the UART chip and the rockwell chipsets anymore. with the exception of us robotics is that it cuts down on the cost of these internal modems. And rather than having it set up like the old ISA. they'll emulate the communiction port and the chipset on these things. 

Compucore



> **igknighted said:**
> 1) Ubuntu comes on one CD.  They can only fit so much.  If you have specific needs, look for a distro that distributes on multiple CDs, as more software/drivers are available.

2) Modems almost never work well with linux, as much of the functionality of common modems is built into the windows OS, not the modem itself.  As such, enabling these devices (called winmodems) is not easy.  If you know the chipset and brand of your modem, search for it on various linux sites to see how others got it working.

I promise you that there is no intention to leave modems out, but the modem manufacturers who build their devices around windows have done this.  If you want to help do something about this, email or write to you modem's manufacturer to complain about the lack of support for non-windows OS's.

---

### Post by Eddie Wilson on 2007-04-23
Hey Mike,
One thing I forgot to mention is that I really could not setup dial-up without using Gnomeppp. I already had it downloaded using Dapper so I just installed it in Edgy. If it hadn't been for already having gnomeppp I might have passed on Edgy. And durning 7.04 development I asked if maybe there would be an easy way to setup up dial-up. From what I've seen 7.04 will be a lot better distro. 
Good Luck,
Eddie

---

### Post by lakersforce on 2007-04-23
> **koshatnik said:**
> My pleasure. Try and come across less ranty in future posts though.

Geeze! Only thing the guy did was stating his oppinion. And he used a considerably amount of time doing it. So much for the friendly community.

---

### Post by jabeez on 2007-04-23
> **lakersforce said:**
> Geeze! Only thing the guy did was stating his oppinion. And he used a considerably amount of time doing it. So much for the friendly community.

no doubt, and I've been seeing more and more snooty little comments on the forums lately, alot of times for minor little spelling or grammar errors. I guess it's bound to happen as more and more people come into the community, there will be more and more snarky know-it-all types as well...............

---

