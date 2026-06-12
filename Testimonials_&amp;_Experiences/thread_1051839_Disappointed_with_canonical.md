---
title: "Disappointed with canonical"
date: 2009-01-27
forum: Testimonials &amp; Experiences
---

### Post by clueless on 2009-01-27
I have been using Linux since Slackware 9 something... I never became a "guru" or anything, I just know how to install my OSs, troubleshoot any issues and make my computer work for me. For years I have only been using some flavour of linux and Ubuntu specifically since Dapper, I think.

But I have never suffered from linux like I have been suffering this year. I can't find any distribution that works for me. Opensuse is out of the question, the package manager is a disaster with all the dependency issues. While Intrepid is marginally unusuable.

I have a reasonably nice system, Athlon 64 X2 @ 4800+, 2GB RAM and 1 GB of Swap. But still, almost every two days the computer will freeze because all memory will be used. I have to restart the computer (when I get it in time, before completely freezing) almost every two days. Totem might also choose to freeze when if I pause video. Firefox will hog almost all my memory when viewing a web page with flash on it, making switching from a window to another or even closing a tab a procedure of at least 1 minute.

To top it off I am extremely disappointed with Canonical. I bought their codec pack which supports wmv videos etc. That is 30 euro... I wanted to show my "support". Big mistake. The codec pack is buggy, as their technical support (which was extremely helpful) found out too. I asked for a refund and they just ignore me. 9 days after I asked for the refund the didn't even answer to say "hey, we received your complain", then I sent a second email and only received a reply saying "I will pass this to the relevant department and someone will contact you if they can help". If they can help? What does that mean? 

Anyway I am just blowing off steam here... This year has been extremely bad for linux. I don't know about other distributions, to be fair, but I don't see big differences among them. I would like to try out opensolaris, but there is software that I need for my work, like skype, flash etc, so my only option here seems to be Windows or OSX. And since I really cannot stand the idea of going back to windows, I think I'm going to get me a macbook.

---

### Post by BennBuntu on 2009-01-27
If you're running 64 bit, have you tried Adobe's native 64 bit plugin? It's in alpha, but I've found it fixed my flash issues. 2008 year was smooth sailing for me, I've just installed preload cause most of my 2GB memory is never used.

You just stick it in your plugins folder, remove old ones first. [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Bit sad to hear bout Canonical's service.

---

### Post by Kevbert on 2009-01-27
Have you tried Ubuntu 8.04.2 ?  For me it's very stable and reliable (unlike 8.10 and 9.04 which seem to be buggy).  Also your swap seems to be on the low side (it should be at least 2Gb), you could try adding a swap file.

---

### Post by clueless on 2009-01-27
@ Bennbuntu

Trying out the alpha flash plugin is something I will surely do. I was hesitant to try it out before because the system was already too unstable with "stable" software, I did not want to find out what would happen with alpha software. But I see that it has managed to solve problems for many 64bit users, so I will try it out.


@ Kevbert

About the Swap size, I am not so sure though. Normally not much of my swap is used. Right now 1,3 GB of memory and only 12 MB of swap are used. But then, every now and then, something hogs the systems memory to a point that it gets all filled up. It gives me the impression that it would fill up all swap, regardless of its size.

I might try going back to 8.04, see how it goes.

---

### Post by marduk667 on 2009-01-27
I also would recommend 8.04.2, i am running it on 3 machines without problems!

---

### Post by clueless on 2009-01-27
I just installed the alpha flash plugin and already things got better. Firefox is much more responsive, starting a lot faster. With the old flash plugin even writing an url on the address bar would make it unresponsive for a couple of seconds, while there are no problems now. 

Before going back to 8.04.2 I want to make sure that there are no big differences between the versions of the software I use. But it seems that this is where I'm heading.

I would really like to see my money back from the canonical store though!

---

### Post by albinootje on 2009-01-27
> **clueless said:**
>  Before going back to 8.04.2 I want to make sure that there are no big differences between the versions of the software I use. But it seems that this is where I'm heading.


Gimp 2.6 is in 8.10, but not in 8.04.
But I found out that backporting it is not that very difficult, and there's probably pre-compiled backports available for Gimp 2.6.

You can check version differences e.g. here :
[http://packages.ubuntu.com/gimp](http://packages.ubuntu.com/gimp)

---

### Post by clueless on 2009-01-27
That's great, thanks!

I don't need Gimp, I am more interested in Evolution, Beagle, OpenOffice3... But as I see it I don't expect having any problems. The reason I was worried is that when I was using kde, I upgraded to kde4, the kontact suite did not work for me, switched back to kde3 and lost all my settings. But I don't expect anything like this happening now.

---

### Post by albinootje on 2009-01-27
> **clueless said:**
>  I don't need Gimp, I am more interested in Evolution, Beagle, OpenOffice3... But as I see it I don't expect having any problems.

Okay. There's a howto for OpenOffice 3.0 on Ubuntu 8.04 :
[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by Kevbert on 2009-01-27
If you want to find out what processes are using up all your memory run the following in a visible terminal:
```
top
```

---

### Post by clueless on 2009-01-27
@ albinootje
Thanks! OpenOffice.org will be a easy to install.


@ Kevbert
I know most of the programs that eat all my memory. They're mostly Firefox with Flash plugin, vuze and java and then every now and then some others, like beagle etc. My problem is that my computer freezes much too often and most of the time it's terribly slow, becoming unusuable. By the way, I spoke too soon about the alpha version of the 64bit flash plugin. While it's a big improvement, again displaying 2 or more videos (depending from the website too) the playback becomes terribly jerky.

The only solution I see is going back to hardy and if that doesn't work, switching completely to something else.

---

### Post by solwic on 2009-01-27
> **clueless said:**
> That's great, thanks!

I don't need Gimp, I am more interested in Evolution, Beagle, OpenOffice3... But as I see it I don't expect having any problems. The reason I was worried is that when I was using kde, I upgraded to kde4, the kontact suite did not work for me, switched back to kde3 and lost all my settings. But I don't expect anything like this happening now.

So you're using KDE?  If that's so, then there is your problem.  Kubuntu is about as stable as a three legged table (hey that rhymed).  

Also, if you are using Kubuntu with KDE4.x, OOo3 won't install properly (fyi).

Good luck getting things set up, and with getting your $$$ back from Canonical.

---

### Post by clueless on 2009-01-27
No, no I'm using Gnome... I was using Kubuntu until KDE4 became default. But that's another horror story :)

---

### Post by wolfen69 on 2009-01-27
> **clueless said:**
> This year has been extremely bad for linux.

bad for who? you? it's been a great year as far as i'm concerned. 

i like how 1 person has a couple of problems, and then declares that it was a bad year for linux. :roll:

have a nice day.

---

### Post by wolfen69 on 2009-01-27
> **jrock612 said:**
> So you're using KDE?  If that's so, then there is your problem.

if you want stability, use debian lenny with KDE(3.5). solid as a rock.

---

### Post by Tamlynmac on 2009-01-27
> wolfen69 	 		**Re: Disappointed with canonical**
 		 	Quote:
 	 	 		 			 				 					Originally Posted by **clueless** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6625009#post6625009") 				
 				*This year has been extremely bad for linux.*
 			 		 	 	 
bad for who? you? it's been a great year as far as i'm concerned. 

i like how 1 person has a couple of problems, and then declares that it was a bad year for linux. :roll:

have a nice day. 	

+1
Odd, didn't realize that 1 bad install = 1 bad year for Linux/Ubuntu
Seems somewhat narcissistic to me.
  	 	 	 	 	 	  Reinforced by the use of this section of the forum to obtain assistance, instead of posting in the appropriate sections. Post "bad year" then simply wait for help.

---

### Post by wolfen69 on 2009-01-27
> **clueless said:**
> I can't find any distribution that works for me. 

that right there tells me it's your hardware. i've done well over 80 installs of linux on various hardware, and rarely have any problems. yes, it is *your hardware* at fault. no one will ever admit that though. silly human pride i guess.

buy a pc with linux preinstalled or get new hardware, and you will fall in love. 

if you really want to use linux, you would get a preinstalled system (like mac maybe?) and save alot of money. 

i make too much damn sense sometimes. ;)

---

### Post by stchman on 2009-01-27
I run Hardy on (4) different machines no problems (3) of them run 64 bit.  My Athlon 64 3500+ runs 64 bit no sweat.

---

### Post by solwic on 2009-01-27
> **wolfen69 said:**
> 
i make too much damn sense sometimes. ;)

It's a blessing and a curse, isn't it?  

I know your pain, brother.  :P

---

### Post by Antman on 2009-01-27
If Ubuntu doesn't fit you there are MANY other distros to try.:popcorn:

---

### Post by clueless on 2009-01-27
wolfen69

This is the "Ubuntu Testimonials & Experiences" part of the forum. I have no intention to star a war or anything, I just shared my experience.

You say that it is my hardware, it might be, I have no idea, but I don't know how you are so sure about it. I am no new comer to linux, I have been using it exclusively for years, started with Slackware, have also used/installed Debian, Arch, Mandriva, SuSE, Fedora, Gentoo, have built 1 system with LFS, but for years have settled with Ubuntu. I might be no hacker, but I have solved issues, I can and do use the terminal every now and then.

In 2008 I have not found a distribution that worked for me. This is for various reasons. Various packages that did not work exactly as I expected. 8.10 that has presented annoyances. But I did not - and do not want to - enter to specifics. It was suggested to me that I should try going back to 8.04 and I was happy to take the advice, as you might have noticed. 

The thread has the title "disappointed with canonical" because while I have actively supported linux and ubuntu in particular, I didn't like the fact that still I have received no reply from them other than yes, the package you purchased is buggy.

In conclusion, this is the "Ubuntu Testimonials & Experiences" part of the forum and this was my testimonial. I did not post here to get help, although I was grateful to receive the advice. 

In this forum we have always tollerated/accepted other users' opinions, let's not turn this into a flame war.

---

### Post by Tamlynmac on 2009-01-27
> wolfen69
**[COLOR=Red]The Wolfman Cometh[/COLOR]**

That's really to much information.#-o
**[COLOR=Red][/COLOR]**

---

### Post by solwic on 2009-01-27
> **Tamlynmac said:**
> That's really to much information.#-o
**[COLOR=Red][/COLOR]**

:lolflag:

---

### Post by BennBuntu on 2009-01-27
If vuze is the new Azureus, I'd recommend ditching it for something more native. Deluge, or transmission for example. 
Few years since I used it, but Azureus on linux always had trouble loading, quitting, wrong java versions etc.

---

### Post by clueless on 2009-01-27
Yes Vuze is Azureus and I know it's a real pain. It's too heavy on the resourses and Firefox + flash + Azureus will almost certainly bring my computer to its knees. But it has really nice RSS support. I only use it when my computer sits doing nothing.

---

### Post by wolfen69 on 2009-01-27
clueless: don't take anything personal. i was trying to illustrate the fact that if every distro you try does not work, what does that tell you? that every distro is junk? no, they are not. you just happen to have one of the very few incompatible computers. 

if you *really* want to use linux, (and maybe you don't) buying a pc with ubuntu preinstalled will make you a very happy camper. it will be guaranteed to work perfect. and it's alot less money than a mac. take care and good luck.

i know you know your way around linux, but when push comes to shove, you either get compatible equipment or use something else. it's really quite simple. i didn't have to get compatible equipment. all 5 of my computers (all different configurations) just worked. i'd say linux is pretty damn good for being a rogue OS.

---

### Post by clueless on 2009-01-28
It's not my hardware. I built this computer myself, checking every component for linux compatibility. Besides I never said I ran into issues with any distro. 

Gnome, KDE and the applications I use for my everyday work are the same on every distribution. And while I have seen many improvements and I know much work is being done, lately I have been running into too many problems for the kind of work I do. That's it. 

And, once again, I was unhappy with canonical, as is the title of my thread, and not with ubuntu nor with linux! I have been running into problems lately, I mentioned it as my testimonial, but that's that. My real bad experience is buying the codec pack. 

That's it, I may be wrong but it's my experience, not everyone has to like it.

---

### Post by Keyper7 on 2009-01-28
> **clueless said:**
> That's it, I may be wrong but it's my experience, not everyone has to like it.

"This year has been extremely bad for linux" is not simply an "experience". It's an over-generalization and that's what people are complaining against.

---

### Post by clueless on 2009-01-28
I am sorry, it is only my view

---

### Post by Magnes on 2009-01-28
> **clueless said:**
> This year has been extremely bad for linux.

Not all Linux - Android does quite good. But i agree it wasn't good year for Ubuntu at least.

---

### Post by wolfen69 on 2009-01-28
> **clueless said:**
> It's not my hardware.

yeah, OK. if it's not your hardware, then what is it? why do millions of people use it? because they like problems? this is getting old. you know what? go get a mac. steve jobs needs a new pair of shoes. 

nevermind getting a pc with ubuntu preinstalled, that makes too much sense.

as far as hand picking your components for linux compatibilty, that doesn't matter. 10-15% of all hardware will fail diagnostics tests. hardware is the issue more often than software. i know, i test pc's for a living. yet the public is led to believe that all problems must be software related. "my hardware is bad?" no. never. can't happen. i blame the OS. that is the easy way out to talking yourself into buying a mac. if you choose not to listen to my nuggets of wisdom, that's OK. you're the one that's going to pay, not me. 

one last thing. how come i'm able to install ubuntu on so many computers without a problem? sheer luck? yeah, that must be it.

---

### Post by clueless on 2009-01-28
Once again and for the last time... It's not my hardware...

---

### Post by albinootje on 2009-01-28
> **clueless said:**
> 
The thread has the title "disappointed with canonical" because while I have actively supported linux and ubuntu in particular, I didn't like the fact that still I have received no reply from them other than yes, the package you purchased is buggy.

Perhaps it's an idea to file a bug report at launchpad.net about the buggy codecs pack ? Then you can also complain about the email response.
The majority of the people here are normal Ubuntu users, not affiliated with Canonical.

And.. if you're saying that you have been using the same machine with different Linux distributions in the past, and now have problems with Ubuntu, then the "it's your hardware" remark seems redundant to me.

---

### Post by Tamlynmac on 2009-01-28
> clueless 	 		**Re: Disappointed with canonical**
 		I am sorry, it is only my view 	


And, once again, I was unhappy with canonical, as is the title of my thread, and not with ubuntu nor with linux! 

Seems somewhat disingenuous. To say that your not "unhappy" with Ubuntu, then express an unfavorable "view" of said object that indicates the opposite. Odd


> Originally Posted by **clueless** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6625009#post6625009") 				
 				*I can't find any distribution that works for me.*


Perhaps, wolfen69 is correct - it may actually be a hardware issue. Considering no Linux distro will work for you. Arguing over hardware or concerns of hardware impact on functionality is irrelevant, if Linux/Ubuntu doesn't work on your system. Finding a solution may require a completely different frame of mind. There has been many changes made in Ubuntu and one should investigate any and all potential causes for failure. Not just assume. Have you installed any previously released versions of Ubuntu to check functionality? Perhaps 8.04 may be fully operational and 8.1 - not so much. Possibly, a hardware compatibility driver issue reared it's ugly head in 8.1.

albinootje, may be right on target "reporting to launchpad" regarding your codecs.

---

### Post by shqip on 2009-01-28
I don't think "clueless" has hardware problem. Linux especially Ubuntu is being attacked by those who are against Linux. This has happen to me too. Those people who are attacking Linux/Ubuntu users should be panished as they are giving Linux a bad name. I like Ubuntu/Linux and I want to see it take over simply because it is better, reliable and more secure.

---

### Post by Tamlynmac on 2009-01-28
> shqip 	 		**Re: Disappointed with canonical**
 I don't think "clueless" has hardware problem. Linux especially Ubuntu is being attached by those who are against Linux. This has happen to me too. Those people who are attacking Linux/Ubuntu users should be banished as they are giving Linux a bad name. I like Ubuntu/Linux and I want to see it take over simply because it is better, reliable and more secure. 

I believe your implying that the OP is a Linux/Ubuntu critic or troll?

I agree that that certain factions and/or individuals may not want to see Ubuntu/Linux succeed, I just wondered how you made the assessment? Occasionally, I'm able to identify some of these individuals based on the use of a responders own verbiage to generate flame or create a hostile environment and other indicators. I didn't get that from this posting and would seriously appreciate your insight. What made you suspicious, what terms did the OP use that led to that conclusion, etc.

I've been know to overlook the obvious.

---

### Post by solwic on 2009-01-28
> **Tamlynmac said:**
> 
Perhaps, wolfen69 is correct - it may actually be a hardware issue. Considering no Linux distro will work for you. 

I would agree that it's either a hardware issue or something you're doing/installing that's causing things to bug out.  

However, if you purchased something from Canonical (as in paid real money for) then I would be super pissed off if it was buggy.  No excuse for scamming people out of their dough with buggy packages.  

Do you have other hardware you can try Ubuntu on?  Maybe that'll help you see that it's more than likely your hardware giving you all the grief.

Good luck.

---

### Post by Keyper7 on 2009-01-28
> **clueless said:**
> Once again and for the last time... It's not my hardware...

Prove it.

You're saying you having problems. Some people here are saying they don't. It would simply be a matter of "your mileage may vary", but you're the one making accusations against Canonical and therefore the burden of proof lies on you.

---

### Post by clueless on 2009-01-29
Ok I don't know how else to say this. I don't want this discussion to go on because it is pointless but I feel like I have to reply.

First of all. Prove that I don't have a hardware issue? Why? And with my office machine? Just install another distro just to make you happy? And just because almost nobody here understood what I am saying?

I said that this year I haven't found a distribution that worked for me, meaning that covered my needs for my work.

My needs are:
A very good search engine:
The closest I have is beagle, which unfortunately cannot be relied upon. Google Desktop gave me better search results but does not index many file formats and web history, that for me are crucial.

A very stable PIM
Kontact 3.5 has always been very heavy. I expected something better with KDE4 that didn't came. I waited until 4.1 but KMail kept crashing, Akregator kept not showing the messages. I had been waiting these years for bug fixes that I am sure will eventually come, but at some point I decided to move on, since I can't have a person waiting for me on the other end of my office while I'm searching through emails and Kmail crashing.
So I moved to Evolution. Migrating thousands of emails was not easy, but I did it, while evolution was crashing between imports. Only to find out that evolution lately has a bug that makes it "forget" POP passwords. This is a great issue when you have a lot of email accounts. So I migrated a third time to Thunderbird. 
At this point I do use Thunderbird for my work but I don't have the integration I used to have and would like to see. In the future I will still have to migrate to either Evolution or KMail but can I be sure I will not see some other crucial bug or annoyance?

A web browser with flash 
I know flash is buggy software that has nothing to do with linux but for the work I have to do I need it.

A good photo organizer. F-Spot does the job for me, although there are some features I would like to see improved.

Stability and performance that were both lost with KDE4 and Intrepid.

These are my problems. I have no hardware problems, as I have said before. And I have not complained about any of these problems, I am not searching for solutions! I blew off some steam because this year I had a bigger combination of linux problems than other years.

Some questions I am sure I will get:

- Why did you upgrade from Hardy to Intrepid if you want a stable environment?
Because there were features missing from Hardy that I hoped would be covered in Intrepid. Now that I know, I plan going back to Hardy as it was suggested to me and see what I can add to it to make it work for me. 

- Why did you upgrade from 3.5 to KDE4?
Because I was hoping from improvements. I really liked the Kontact suite but it was too heavy. So I figured I would test it installing Kubuntu Intrepid and then migrate to Evolution, if it didn't work (which it didn't). KDE4 is said that it will be lighter and more responsive, but it was not lighter than 3.5, for me, until 4.1 when I switched to Gnome.

- Flash is not a Linux problem
I know

- Buy another computer preinstalled with linux (as it was suggested to me)
No thanks, it's not because of my hardare that I haven't found a PIM suite this year that works for me. What if I see that on my brand new laptop Evolution still forgets the passwords? Who will give me my money back?

- What do you want then?
Nothing! I never said I wanted anything! It's just that many people here got really offended that this year I was not happy with linux. I did not go around saying linux sucks, I'm going back to windows. I said that for me, linux has had a bad year, I have not found a distribution that has worked for me and I am thinking what are my options: keep trying with 8.04.2 or buying a macbook (and keeping linux on my desktops at home).

- Are you a troll?
I don't know how would anyone reach to that conclusion. I did everything to avoid confrontation here.

- File a bug report for the codec pack
The support guy told me he would let know the guys at Fluendo about the bug himself. He did an identical install to mine, verified the problem and would take care of notifying about the but. As I said, tech support was excellent, but I still haven't received a reply for my money back.


Only because I have whatever linux distribution running on my computer work would not mean it works for me! Between running and covering my needs there is a big difference. I never thought this whole thing would raise such an issue here or else I would have specified it better:
This year I have not found a distribution that works for me. For me, this has been a bad year for linux.

And with that I would hope to end this whole ridiculous thread.

---

### Post by shqip on 2009-01-29
> **Tamlynmac said:**
> I believe your implying that the OP is a Linux/Ubuntu critic or troll?
 
I agree that that certain factions and/or individuals may not want to see Ubuntu/Linux succeed, I just wondered how you made the assessment? Occasionally, I'm able to identify some of these individuals based on the use of a responders own verbiage to generate flame or create a hostile environment and other indicators. I didn't get that from this posting and would seriously appreciate your insight. What made you suspicious, what terms did the OP use that led to that conclusion, etc.
 
I've been know to overlook the obvious.
 
 
Who is OP? 
 
 
As for “clueless” I believe that he might have gone though a difficult period. It might have been a case of hardware or software problem and I sympathize with his problems and I hope he sorts them out. 
 
 
Nothing wrong with criticism. Criticism means improvement. You need to be able to take criticism in order to move forward and be on top. Listen to your critics. They might be right sometimes. 
 
 
By attacking a Linux/Ubuntu user you are basically attacking Linux. You are attacking the hard work all these developers put to make Linux one of the best OS available. 
 
 
Nothing made me suspicious of this posting and the guy who posted it, has nothing to prove to others. 
 
 
I did not get this from this post either and nothing made me suspicious, I do not understand how did you come to that conclusion!

---

### Post by stalkingwolf on 2009-01-29
I think it is " a terminal failure in the primary input device".

just my .02 worth.

---

### Post by Keyper7 on 2009-01-29
> **clueless said:**
> Prove that I don't have a hardware issue? Why?

Because people are trying to help you and you are dismissing them by simply saying "it's not the hardware". People are *conjecturing* hardware is involved. You are *sure* it's not. You say that like it's obvious, but so far you didn't give any convincing argument to support it.

---

### Post by wolfen69 on 2009-01-29
all i know is that if i tried several distros that did not work, this tells me something. whether or not the hardware is "faulty" then becomes a moot point. the fact is, it doesn't work. getting something that does work would become my priority. whether that be getting new hardware or a pc with linux preinstalled would become my priority. that is because my computing freedom is more important to me than it is to other people. if that meant getting a second job to be able to save enough money to buy one, then so be it. i will never use a microsoft or apple product ever again.

clueless: good luck and take care.

---

### Post by solwic on 2009-01-29
> **wolfen69 said:**
> all i know is that if i tried several distros that did not work, this tells me something. whether or not the hardware is "faulty" then becomes a moot point. the fact is, it doesn't work. getting something that does work would become my priority. whether that be getting new hardware or a pc with linux preinstalled would become my priority. that is because my computing freedom is more important to me than it is to other people. if that meant getting a second job to be able to save enough money to buy one, then so be it. i will never use a microsoft or apple product ever again.

clueless: good luck and take care.

+1.  It's like getting six copies of your car keys made and then blaming the keys for not working when the fact is that your bleedin' car is broke down.  Throwing new keys at it won't work; try fixing your car (aka computer)

But wolfen is right; if Linux doesn't work - if none of the distros work - then why not go back to Windows, or buy a Mac?  We're not going to hunt you down and shoot you if you give up Linux (well ok...wolfen might :P), so what's the big deal?

Use what works, home-fry.  Use whatever works.  :)

---

### Post by Tamlynmac on 2009-01-29
> jrock612
We're not going to hunt you down and shoot you if you give up Linux (well ok...wolfen might :razz:),
[B]
MIGHT? [/B]:rolleyes:

---

### Post by snowpine on 2009-01-29
Sounds like it was a good year for Linux, bad year for your homemade computer that won't run it. ;)

---

### Post by solwic on 2009-01-29
> **Tamlynmac said:**
> [B]
MIGHT? [/B]:rolleyes:

:lolflag:

---

### Post by jdrodrig on 2009-01-29
First of all, we are only in the day 29th of this year..so I guess "it is a bad year for Linux" is not that bad, people, relax! =)

Second. I dont get people that says "it is your hardware, because Linux works for me"...what does that mean? I hope you would then accept the response, it is not my hardware, because Windows works perfectly!...as soon as we get it that what we all are for is: Software+Hardware=Solutions... the sooner we will all understand each other...

---

### Post by wolfen69 on 2009-01-29
> **jdrodrig said:**
> 

Second. I dont get people that says "it is your hardware, because Linux works for me"...what does that mean?

well, it *is* the hardware if no linux will work. whether or not it is faulty isn't the point. getting something that does work, is the point. people buy macs with OSX preinstalled. it should just work. people buy a pc with windows preinstalled. it should just work. if you buy a pc with linux preinstalled, it will just work. there are no excuses any more when there are MANY vendors offering pc's with linux preinstalled. 

i have always built my own pc's in the past, but i just may buy one pre-built next time. a) to show support for the companies offering them. b) just so i don't have to search for compatible hardware. 

i'll never understand why people buy a computer with windows installed (knowing they are going to wipe it and install linux) then complain that linux won't run well. :roll:  wake up people! if you need to dual boot, get one with linux preinstalled, *then* install windows. but i guess that makes too much sense.

---

### Post by jdrodrig on 2009-01-29
it makes a lot of sense but not in a linux-diffusion strategy way...if you expect linux expansion to come mainly from purchasing new equipment, I think we better sit and get an snuggie, because hell will freeze first..

---

### Post by kk0sse54 on 2009-01-29
> **jdrodrig said:**
> First of all, we are only in the day 29th of this year..so I guess "it is a bad year for Linux" is not that bad, people, relax! =)

Second. I dont get people that says "it is your hardware, because Linux works for me"...what does that mean? I hope you would then accept the response, it is not my hardware, because Windows works perfectly!...as soon as we get it that what we all are for is: Software+Hardware=Solutions... the sooner we will all understand each other...

Not all hardware is compadible with linux even if it's working perfectly, so "it is your hardware, because Linux works for me" is some what applicable.

---

### Post by mdsmedia on 2009-01-29
> **snowpine said:**
> Sounds like it was a good year for Linux, bad year for your homemade computer that won't run it. ;)
Except that as Clueless explained in the previous page, it's not that he couldn't run Linux. Linux didn't have tools that suited him or they were buggy.

Personally I think the OP expressed his problems badly at first and didn't do too well in correcting himself or others later either, but then there are some posters who either haven't read his posts properly or at all.

---

### Post by clueless on 2009-01-30
> **mdsmedia said:**
> Except that as Clueless explained in the previous page, it's not that he couldn't run Linux. Linux didn't have tools that suited him or they were buggy.

Personally I think the OP expressed his problems badly at first and didn't do too well in correcting himself or others later either, but then there are some posters who either haven't read his posts properly or at all.

Thank you,

I might have expressed myself badly, because I have not expected this to take such dimensions to be careful about each and every word. Besides that this was not the point of the post, it was "disappointed with canonical". But I think that with a little good will it would not be too difficult to understand the idea that, yes, I can run linux on my computer, any distro, but I have not been happy with the quality or features of the software that I need in this past year. I tried explaining a second time but I saw that almost nobody actually read what I had to say. So I gave up in hopes that this whole thing will just eventually fade away.

---

### Post by jdrodrig on 2009-01-30
fade away? sorry, it will be forever engraved in ubuntu memory! (men can forget and forgive, the web cannot)... =)

---

### Post by clueless on 2009-01-30
Oh no, this will haunt me until the end then!

---

### Post by cb951303 on 2009-01-30
consider the possiblity of faulty hardware.

---

### Post by larukuinsane on 2009-02-13
first , hi to all.

omg!!! hahahahahha. And again  in this thread pulling out the phrase ... "hardware problems,faulty hardware etc.."!! .

"Clueless" it just  saying than  the features he needs (software features) are buggy.

But you know maybe i dont use those exacts features , ergo "My Ubuntu runs great and the software rocks!! maybe its your faulty hardware" ..... ¬.¬

it is so hard to recognize than some features in Ubuntu and other ditros are buggy??¿?.

and that its not solved with new hardware.....

And about the freezing of his PC maybe  its a "hardware problem" lol

Well its always a good  idea take a look for temperatures you know, just in case.

PD: im from Peru,  so  i apologize for the incorrect  use of English

---

### Post by ouija on 2009-02-13
Hey Clueless, have you tried playing back WMV content with that codec pack? More specifically, High Definition WMV files (that have VC-1 and Window Media Audio 10)?

Just curious how that worked for ya if you have tried yet... been contemplating the purchase myself..

---

### Post by bigbrovar on 2009-02-14
Its really sad the attitude of some people in this forum.. it seems the only Testimonial you want to hear about ubuntu are positives .. and when someone comes and makes post about ubuntu not working write for him .. he is hounded and labelled a troll. its really really sad.  i would agree with clueless in saying that the last 6months has been very bad quality and stability wise in the linux desktop. yeah hardy is turning out to be  a solid release.. but intrepid? has just not it quality and stability  wise. i started my linux experience with Fiesty fawn and was pleased when every one of my hardware worked right now of the box. i had a stable system that was fast and rock solid. that shaped my experience and expectation of linux. last yeah to show my support i got a dell xps m1330 ubuntu preinstalled to make sure i have 100% linux support i opted for the freedom loving intel graphic cards . it cost me $300 more than the vista version because i got it from the US through a friend who shipped it to me. i paid the cost of shipping. hardy was solid on that machine.. but when intrepid came out i did an upgrade and to my surprise  everything that worked on hardy were broken on ibex.. 

**bluetooth** = the default bluetooth setup is a big joke .. its just fancy but doesnt work.. on hardy i could rightclick and send to my nokia n810 and it worked.. not so with ibex.. pairing doesnt work.. so my bluetooth was is just a useless piece of crap..  i tried fedora 10 and experienced the same issue which made me feel its an upstream problem.. why for the love of me an OS would be allowed to ship with broken bluetooth support really beats me. i was able to solve this problem by install blueman.. but this kills the just works out of the box experience that a standard OS should have .. remember my dell came preinstalled with ubuntu.

**Internal Mic** = dont even go there .. it just doesnt work. i have tried everything under the sun but its still a no no .. i leave far from my girlfriend and it would have been cheaper and easier to skype but i guess that is out of the question.. again this was something that worked fine on hardy.. had the same problem with Fedora 10

**webcam** until recent webcam was a joke .. on hardy it worked right not of the box. with ibex.. i had to compile a driver. same problem on fedora 10.. although recent updates seem to have fixed the problem both on ubuntu and fedora.

**Finger print reader** all i had to do on hardy was install thinkfinger and swap my finger print 3 times and am good to go .. i use my finger print for all my authentications .. not with ibex.. the thinkfinger that came with it is broken and just doesnt work .. i had to install from a ppa to get it to work.. again its sad that i have to go through all this for a laptop that came ubuntu preinstalled .. 

also read this  [http://ubuntuforums.org/showthread.php?t=1068929](http://ubuntuforums.org/showthread.php?t=1068929) 

i never had that problem on hardy or even fedora10 .. right now i cant use any compositing compiz or metacity :( .. that means no AWN,Docky Cairo DOck.. just plain ol metacity .. i could as well be using dapper.


 add pulse audio issue which nagged me on both hardy and ibex. 


although i have to say its not all bloom . i like some nice improvement on ibex .. the improve network manager is an example of an application upgrade done right.. i also love the new gparted app which give you ability to add names labels to a drive. nautilus tabbing is another good thing.. and the intel video problem with compiz seem to have been fixed although i cant use composite due to aforementioned problem. 

on a whole i think ubuntu and canonical should work more to improve stability on ubuntu.. saying people should only use LTS is not good enough .. ubuntu can adopt something like debian and have an unstable branch.. anything that is displayed on the ubuntu website as stable .. should be stable .. and quality.. and ibex falls short on that IMHO.

---

### Post by solwic on 2009-02-14
> **bigbrovar said:**
> Its really sad the attitude of some people in this forum.. it seems the only Testimonial you want to hear about ubuntu are positives .. and when someone comes and makes post about ubuntu not working write for him .. he is hounded and labelled a troll. its really really sad.  

+1.  Took the words right out of my mouth.  It is very sad that we have created a derogatory term for those who disagree with us and then have somehow convinced ourselves that it's OK to label people with it and think it's a joke.  

Reprehensible, in my opinion.  And arrogant.  

But hey, I like Ubuntu, so I have nothing to worry about from the large group of people over there on the other side of the forum carrying the torches, right?

---

