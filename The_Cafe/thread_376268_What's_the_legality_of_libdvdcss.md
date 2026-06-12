---
title: "What's the legality of libdvdcss?"
date: 2005-03-13
forum: The Cafe
---

### Post by Mark Marple on 2005-03-13
Please forgive me if I sound ignorant with this question, but trying to get an understanding of whats going on.

I'm just curious as to why its so troublesome to get dvds to work in any Linux distro, (free that is)?  You always have to install libdvdcss2 to watch dvds that you own.  With Ubuntu, you have to go to an alternate repo. to get it.  Why can't something like this  be included with the base system?  I somewhat understand the whole copyright thing, but most people own dvds that want to play them on there computers.  I feel that dvd support should be a default in any linux distro.  You should have the right to play your store bought dvds.  I know that you will always have the ppl that will break rules with the the whole (duplicating) of dvds, but come on, we can't prevent the ability to play them from a default install.  Now don't get me wrong, I'm not an angel, getting MP3's or movies (bittorent wise), so don't bash me for being a do gooder....... :) 

 Also, with a post that I have made a couple days ago (concerning the Mplayer website), it somewhat worries me about someday even being able to play media type files.  How can the mpgs, mp3, avi, divx, wmv, etc, etc, extensions have restrictions on them, when its just a file extension.  I know that this type of ext. was created by someone or some company, but all computer stuff has been started and taken from one person who came up with the idea.  So in all reality, who really owns any of it.  Will the w32codecs possible come to an end someday?  Gstreamer just isn't strong enough yet.  I maybe getting all worked up for nothing, but it just worries me.

Well, I will leave my soapbox now.  Any thoughts and or comments would be appreciated.

Not trying to get into a heated debate between all of us, just curious as to why this situation is the way it is, and is there any hope of the linux community (being open source) to get around it.

Thanks!

---

### Post by tim1 on 2005-03-13
> Why can't something like this be included with the base system? I somewhat understand the whole copyright thing, but most people own dvds that want to play them on there computers. I feel that dvd support should be a default in any linux distro. You should have the right to play your store bought dvds. 

Unfortunately you don't have this right. Any DVD decoding software has to have a licence some DVD consortium (don't exactly know who owns the rights) to be legal. libddvdcss2 just breaks the copy proetection which is illegal in the United States (due to the DMCA) and the EU (due to european copyright law).

[QUOTE=Mark Marple]I know that this type of ext. was created by someone or some company, but all computer stuff has been started and taken from one person who came up with the idea.  So in all reality, who really owns any of it.[/QUOTE]

Yes this may sound, but the hard reality is that there are patents on everything, at least in the USA and now in Europe too. Mathematic algorithms are patented ... even progress bars are patented. The open source world has to face the legal system here, if it's sick or not (and it definitely is sick in more than one way).

greets, tim

---

### Post by kassetra on 2005-03-13
[QUOTE=Mark Marple]I'm just curious as to why its so troublesome to get dvds to work in any Linux distro, (free that is)? 

How can the mpgs, mp3, avi, divx, wmv, etc, etc, extensions have restrictions on them, when its just a file extension. I know that this type of ext. was created by someone or some company, but all computer stuff has been started and taken from one person who came up with the idea. So in all reality, who really owns any of it. 

Thanks![/QUOTE]

No worries.  Ok first off, the issue of why dvd-playback is not included by default is similar to why mp3-playback is not shipped in most distros.  Simply put, there are many legal issues that preclude a linux distro from shipping with dvd-playback and mp3-playback ready out of the box.

This first issue is tied in with your second question, the extensions themselves do not have the restriction - but the decoder and encoder (which allow you to play and record) files into these specific formats are tightly restricted.  So the extension itself is not restricted, but the specific format type is.

People can own data formats.  Jpg, gif, mp3, avi -- all of these file format types are owned, and in some cases, restricted for use.  You have to have permission to either read or write these formats.

Quicktime movies, such as those on Apple's site are an example.  The file format is called a "Sorenson" codec, and the allowance of reading and writing this format has not been granted officially (so far) to Linux.  Now, this format is represented by a mov extension, but the extension itself is not the issue.  Many free formats use the mov extension, and linux players can view and write those, but not the Sorenson format.

---

### Post by darkoptix on 2005-03-13
Hey, it's easier in linux than windows to watch a dvd...

---

### Post by Mark Marple on 2005-03-13
thanks fellows for your replies,

now that you shed some light on this, it kinda makes more sense.  I should have thought more about it before I spoke.  I guess if I think about it, MS doesn't have anything either.  Its the programs that you buy and get that do it.  Maybe I should have re-worded it to say something like "why doesn't totem-xine install with libdvdcss2". 

darkoptix.........U R correct!

tim1............i agree with the hard reality comment.  Unfortunate, but very true.

kassetra.........nice explanation about the file format info..........i guess the saying is true, "u do learn something new everyday"

thanks again fellows!

---

### Post by kassetra on 2005-03-13
[QUOTE=Mark Marple]thanks fellows for your replies,

now that you shed some light on this, it kinda makes more sense. I should have thought more about it before I spoke. I guess if I think about it, MS doesn't have anything either. Its the programs that you buy and get that do it. Maybe I should have re-worded it to say something like "why doesn't totem-xine install with libdvdcss2". 

darkoptix.........U R correct!

tim1............i agree with the hard reality comment.  Unfortunate, but very true.

kassetra.........nice explanation about the file format info..........i guess the saying is true, "u do learn something new everyday"

thanks again fellows![/QUOTE]

You are super welcome my friend!  As far as why totem-xine doesn't install with libdvdcss2... well, that's because if you want to play dvds on linux, you must circumvent some current legalities that are in place.  So if you want to watch something you purchased on your computer under Linux, you must go and retreive the library (which has dubious legal issues surrounding it) yourself, so that the author doesn't get in trouble for giving you the files to play dvds.

---

### Post by TravisNewman on 2005-03-13
It is? 
Windows: Install PowerDVD/WinDVD/etc; Put in DVD; Open PowerDVD; Sit back and watch
Linux (specifically Ubuntu): track down the repository that has libdvdcss (if you don't know already); add a line to sources.list; either apt-get it or install with synaptic; apt-get or install mplayer or xine; put in dvd; open mplayer/xine; sit back and watch.

It's still much easier in Windows. It isn't remotely difficult to install support in Linux, but still, Windows has it beat here, unfortunately.

If you were referring just to the way to install the software, then yes, it's easier.

---

### Post by Mark Marple on 2005-03-13
[QUOTE=kassetra]You are super welcome my friend!  As far as why totem-xine doesn't install with libdvdcss2... well, that's because if you want to play dvds on linux, you must circumvent some current legalities that are in place.  So if you want to watch something you purchased on your computer under Linux, you must go and retreive the library (which has dubious legal issues surrounding it) yourself, so that the author doesn't get in trouble for giving you the files to play dvds.[/QUOTE]

I think I finally GET IT........LOL!!!

---

### Post by BWF89 on 2005-03-13
> but most people own dvds that want to play them on there computers.
Am I the only one who when I go to the video store to rent a DVD doesn't want to sit in an uncomfortable chair having to sit within 3 feet of the screen so I can see peoples faces instead of sitting on my couch or recliner with a remote control to fast forward and rewind through the movie?

The only reason you would need to play DVD's on your computer would be if you were too poor (college students) to afford a TV, cable, and a DVD player and chose a computer over all of those.

EDIT: It's just free distros that aren't allowed to legally watch DVD's out of the box because they can't afford the liscence right? Because commercial distros such as SuSE can watch dvd's right out of the box (i believe).

---

### Post by kassetra on 2005-03-13
[QUOTE=BWF89]The only reason you would need to play DVD's on your computer would be if you were too poor (college students) to afford a TV, cable, and a DVD player and chose a computer over all of those.

EDIT: It's just free distros that aren't allowed to legally watch DVD's out of the box because they can't afford the liscence right? Because commercial distros such as SuSE can watch dvd's right out of the box (i believe).[/QUOTE]

Well, when I installed SuSE nothing multimedia-wise worked out of the box.  I had to install it all myself, mp3s, dvd-stuffs...  Same With Red Hat.

As for only people too poor watching dvds on their computers... uhhh I have a dvd player and tv in the living room and one with my computer, and I have cable, and most of the time I play my dvds while I'm at my computer... and I do have a remote for both dvd players...

I just prefer having a little dvd window sometimes on my computer while I'm working/playing/forum'ing.  Plus I think it's fun.

---

### Post by bored2k on 2005-03-13
[QUOTE=BWF89]The only reason you would need to play DVD's on your computer would be if you were too poor (college students) to afford a TV, cable, and a DVD player and chose a computer over all of those.[/QUOTE]

Have you ever heard of Multi-Tasking? [OS X lovers should know about this]
Sometimes I/we just dont have the spare time to go downstairs and leave the PC all alone. If im doing some process, like ... dvd ripping / editing i dont think you will  edit then record to a dvd and test it on a tv right ? the poor people part is bogus

So my brother rented Troy and Lion King, Troy is freaking 3 hours long and I wanna se LK, I grab the disc, go to my computer, et voila, there it is [excuse the example :-#].

---

### Post by kassetra on 2005-03-13
[QUOTE=bored2k]So my brother rented Troy and Lion King, Troy is freaking 3 hours long and I wanna se LK, I grab the disc, go to my computer, et voila, there it is [excuse the example :-#].[/QUOTE]

OOOOOOOOOOOH!  That's SOOOOOOOOOOOOOOO CUTE!  hehehehehehe.

---

### Post by darkoptix on 2005-03-13
For me to play dvds on my windows system, this is my experiance:
First, I just formated, so there ain't much in the way of formats or anything.
I stick in a DVD and up comes that stupid what should i do thing.
I say watch dvd, because that is an option...
It opens windows media player, and fails opening, say I need some software to play.
I think, wow I need this software(WinDVD, PowerDVD, whatever).
So, since I have no PowerDVD install cd, or anything, I have to go download...
Wow, any site I go to says I have to pay, screw that.
So now i go on some kind of p2p or whatever is wasy to install/download.
I check the size of powerdvd or whatever, and think wow thats huge, not worth downloading on dialup.
I give up and go on my xbox to XBMC, or my linux box to Mplayer and play the dvd or anything else for that matter.

The download for libdvdcss is only like 250kb which is acceptable. Once thats installed, xine is in repositories, so download that(still not big), and watch.

For watching anything else in windows, such as divx, ogm, xvid, 3ivx, or anything else, requires downloading illegal codec packs, or installing software that dies in 30 days. These codecs are avalible in linux not even nearly the ammount of hassle that windows gives.

---

### Post by Lovechild on 2005-03-13
The current solution for the patent problems with such things as mp3 and dvd support is removing those features, or stabbing every single lawyer in the face (note I'm not recommending the latter as society frowns upon such behavior)

---

### Post by TravisNewman on 2005-03-13
Ahhh, you're hilarious ;)

---

### Post by TravisNewman on 2005-03-13
[QUOTE=kassetra]OOOOOOOOOOOH!  That's SOOOOOOOOOOOOOOO CUTE!  hehehehehehe.[/QUOTE]
 Ahh you're hilarious ;)

---

### Post by Mark Marple on 2005-03-14
bored2k

I'm on kassetra's side.

I work from home so when at work, i put a dvd in the home computer and listen/watch while working on the work computer. Have 300 mp3s and still get tired of listening to music.

But I do prefer to watch the TV. 
17" monitor or 55" big screen.

My default is the latter.

just a little friendly fire at ya................... 8)

---

### Post by BWF89 on 2005-03-19
I just tried watching DVD's on my PC while I surf the net and................ **IT FREAKIN ROCKS**

---

### Post by bored2k on 2005-03-19
[QUOTE=Mark Marple]bored2k

I'm on kassetra's side.

I work from home so when at work, i put a dvd in the home computer and listen/watch while working on the work computer. Have 300 mp3s and still get tired of listening to music.

But I do prefer to watch the TV. 
17" monitor or 55" big screen.

My default is the latter.

just a little friendly fire at ya................... 8)[/QUOTE]
 Hey stopped mocking me now :-$ ... every has seen *it* !!

---

### Post by Buffalo Soldier on 2005-03-19
I believe the root of the problem is not with Open Source. If companies (content providers), RIAA, MPAA and governments all make do without restrictive, consumer-bullying DRM, Acts, Bill, and whatever Law... it will be much easier for all of us to enjoy our legally acquired DVD on our OS/platform of choice.

---

### Post by poofyhairguy on 2005-03-21
[QUOTE=panickedthumb]
It's still much easier in Windows.  [/QUOTE]

If the box maker (DELL, Hp or whatever) includes a DVD playing program. If not, than Ubuntu is better (programs is free). 

If the box maker set up the box, then the person might need a Ubunter to set up there system for them. When I do, I always add DVD support. So its easy for my friends.

---

### Post by Mark Marple on 2005-03-24
[QUOTE=bored2k]Hey stopped mocking me now :-$ ... every has seen *it* !![/QUOTE]

Hey bored2k.....
sorry about my last post.  That was meant for bwf89.  My APOLOGIES!
I hope I didn't offend you (or BWF89). 

I will look closer at the names next time.

NICE BWF89............it is to cool to do stuff like that.

Later!

---

### Post by issueperson on 2006-03-06
if i have a legal licensed copy of DVD software on windows, would it still beillegal to use the coedecs/libdvd2?

---

### Post by MacV on 2006-03-06
I too would like to know the answer to that.

---

### Post by aysiu on 2006-03-06
In the US? Yes.
Almost anywhere else? No.

---

### Post by MacV on 2006-03-06
Could you explain why it would be illlegal though? He(and most of us) have Windows version of said codecs all bought and paid for so why should we pay again for using Linux?

---

### Post by Corvillus on 2006-03-07
[QUOTE=MacV]Could you explain why it would be illlegal though? He(and most of us) have Windows version of said codecs all bought and paid for so why should we pay again for using Linux?[/QUOTE]
Why should you? Morally, you shouldn't. Legally, the DMCA prohibits all software which circumvents any type of DRM unless it's been properly licensed. Since this simply cannot be done with free software (where's the money to pay the license fee), there is no legal way to use open source codecs to do this in the US. As you might guess, the reason why you can legally play DVDs in Windows and Mac applications is because you're paying this license fee as part of the cost of the application or the OS.

---

### Post by Kevinator on 2006-03-07
Why would it be illegal? Because we elected people who have no interest in protecting our rights, and they passed a law that makes it illegal to circumvent copy protection. Because you didn't buy and pay for those codecs -- you paid for the limited right to use them in accordance with terms that probably don't allow you to use them under Ubuntu.

There are at least two separate issues here. libdvdcss is about breaking the encryption that is typically used on DVDs, and that is illegal under the DMCA (unless it is covered by Fair Use, which I'm not sure about). The second issue has to do with the actual codecs, which I believe are covered by software patents. There is simply no way to provide free (as in speech, or as in beer) implementations of patented algorithms unless the patent holder grants a very liberal license, which they typically do not.

Disclaimer: I am not a lawyer.

---

### Post by issueperson on 2006-03-07
any idea how illegal this is?
is it a misdemeanor or a felony?

(not saying i run anything illegally, i'm just curious)

---

### Post by Kevinator on 2006-03-07
It is a civil matter, not criminal. They can sue you if they want to, but they can't have you arrested.

Edit: I am still not a lawyer.

---

### Post by aysiu on 2006-03-07
I just spent some time perusing the court case transcripts on the MPAA website that can be found here:
[http://www.mpaa.org/Legal_cases_dvddecss.asp](http://www.mpaa.org/Legal_cases_dvddecss.asp)

It's actually interesting. I don't know if it is illegal for Americans to use; though, someone who knows better may step in and immediately provide documentation to the contrary.

Let me explain.

First of all, the court case in question was brought about by the major film studios against individuals (who happen to be American) making DeCSS freely available on the internet. One of the main arguments of the case by the plaintiffs was that DeCSS was *not* for the purpose of merely viewing DVDs on Linux but that it is also available for Windows and designed primarily for illegally *copying* commercial DVDs.

Nowhere is there any indication in the plaintiffs' arguments that they were moving to make the use of DeCSS for viewing purposes illegal; quite to the contrary, they seemed to be indicating that if such were the case, they would have no problem with it but that the ability to view DVDs in Linux was a "red herring" (yes, they actually use that term), and that DeCSS was really for making illegal copies of DVDs.

It's only because the judge bought this argument that DeCSS was ruled not to be legal for distribution. Of course, if it's not available for distribution in the US, it would certainly be difficult to use, even for viewing purposes, but the gist of the argument seemed to be based on the assumption that if one were to use DeCSS for strictly viewing-only purposes in Linux that that would have been acceptable to the MPAA and the major film companies.

One of the biggest offenses, apparently, was DeCSS's availability for Windows, the "more widely disseminated operating system."

Interestingly enough, the MPAA has an FAQ section where they say Linux users shouldn't have to use DeCSS because [InterVideo](http://www.intervideo.com/jsp/LinDVD.jsp) makes a Linux port called LinDVD; however, LinDVD has been discontinued for home consumer use: > **Can I get a copy of LinDVD?**
LinDVD, InterVideo's Linux software DVD player, is currently available only to manufacturers for evaluation and integration. 

**Edit**: Never mind: > Appellants' argument that DVD buyers have "authority of the copyright owner" to view the DVD was resoundingly rejected because Appellants offered no evidence that studios authorized DVD buyers to circumvent encryption technology to support use on multiple platforms Apparently you can't even use it to just *view* DVDs on "multiple platforms" even if you own the DVD.

Though, I think I was right about one thing: > In 1998 Congress passed and President Clinton signed the DMCA to allow the creators of copyrighted material to protect their works from digital piracy. Under the DMCA, it is illegal for anyone to traffic in a device designed to circumvent the encryption that protects copyrighted material. It appears to be, technically, the *distribution* of DeCSS and not the *use* that is illegal. Sure, you can't really use it unless someone distributes it to you, but...

---

### Post by Kevinator on 2006-03-07
The copying/"piracy" claim suited the MPAA's purposes, but is extremely questionable.

[http://www.linuxjournal.com/article/5227](http://www.linuxjournal.com/article/5227)
> Let's look at some of those lies. Here's our first: that the DVD Copy Control Association's attempt to suppress DeCSS lawsuit is (or was ever) about piracy. Yes? If so, why wasn't the DVDCCA up in arms about DVD-ripper programs 18 months ago? It's come out in the 2600 trial in New York that the DVDCCA knew about these programs perhaps as far back as that - and the rippers do exactly what the DVDCCA says DeCSS is for, which is allow people to make digital copies of DVDs that can be shipped over the Net and burned into writable CD-ROMs.

...

So what's the truth? The truth is that the war on DeCSS was never about piracy at all. What it's really all about is protecting the DVD player monopoly - and the DVDCCA, which is run by a cartel of consumer electronics companies, has been playing Jack Valenti and the Motion Picture Association of America for patsies.

---

### Post by MacV on 2006-03-07
I understand now. Thanks for the info.

---

### Post by lauralee on 2006-03-07
So the bottom line of all of this (for me) is that it is illegal for me to play a rented DVD on my laptop?

How sad.

---

### Post by NoNo_231 on 2006-03-07
I would like to ask something close to the theme. Is it illegal to copy someone the fonts used by windoze (which are not copyrighted by micro$) to Linux? In my country the are only two series of free Fonts that can be used, and it has no interoperability.

---

### Post by OffHand on 2006-03-07
[QUOTE=lauralee]So the bottom line of all of this (for me) is that it is illegal for me to play a rented DVD on my laptop?

How sad.[/QUOTE]
That's why the people of EFF are needed  :)
[http://www.eff.org/](http://www.eff.org/)
All this patent stuff isn't good for anyone but the big companies.

---

### Post by ronmarley1 on 2006-03-07
Nicholas Petreley, editor in Chief of "Tux" magazine ([http://www.tuxmagazine.com/](http://www.tuxmagazine.com/)) has a good editorial on the legal/ethical issues related to this topic.  "Tux" is a free journal that's the sister publication of "Linux Journal," but it's geared for new Linux users.  See page 5 of the Nov. 2005 issue for the editorial.

---

### Post by az on 2006-03-07
It's all in the software's EULA....

---

### Post by MacV on 2006-03-07
[QUOTE=azz]It's all in the software's EULA....[/QUOTE]

What end user actually spends their time reading that bloated thing though?:confused:

---

### Post by skirkpatrick on 2006-03-07
Ah, but you should know that ignorance doesn't not excuse one when it comes to law.  The EULA is always there and it is up to the user to read it and agree to it.  The ones that were the real problem said that you agreed to the terms if you opened the package and the terms were listed in the package.

---

### Post by MacV on 2006-03-07
True, ignorance of the law is not an excuse, but sometimes you have no choice but to accept the EULA to get what you want. Some of them are downright absurd. Have you heard about the Sony Cd one where it says you can't have filled for bankrupsy if you want to play thier cds on your comp?
Either way, the US gov has to re-write that law because all it does it make crimminals out of a majority of law abiding linux users.

---

### Post by issueperson on 2006-03-07
[QUOTE=MacV]Either way, the US gov has to re-write that law because all it does it make crimminals out of a majority of law abiding linux users.[/QUOTE]

ah, but if one were to use these illegal coedecs, one would hardly be law-abiding would they?

---

### Post by aysiu on 2006-03-07
[QUOTE=issueperson]ah, but if one were to use these illegal coedecs, one would hardly be law-abiding would they?[/QUOTE] Technically, no. But if the argument for the law against DeCSS is based on the idea that DeCSS is primarily for the illegal *copying* of DVDs in both Windows and Linux and not the *viewing* of DVDs in Linux alone (the supposed "red herring"), then viewing DVDs using DeCSS isn't the illegal part that the law is targeting--it's an unfortunately by-product.

---

### Post by issueperson on 2006-03-07
so i guess the issue is along the same lines as the illegal music downloading using kazaa, etc.?  as long as you aren't distributing, you probably wouldn't get in trouble.  and if you already owned the song you're downloading (or a licensed version of the DVD software for another platform in this case) you might have a good case in court?

what would it take to get legal DVD software for linux?  Is LinDVD a free program that Ubuntu programmers could incorperate into the distro for the legal, free playback of encrypted DVDs?

is there any free or cheap way to get your computer into conformity with the US legal system?

---

### Post by MacV on 2006-03-07
Linspire has that CNR thing, but I have no intrest in it.

---

### Post by aysiu on 2006-03-07
According to [the MPAA](http://www.mpaa.org/DVD_FAQ.asp), > **Q.  	 Some computer users say they only want to use DeCSS to view their DVDs on computers that use the Linux operating system. Windows- and Macintosh-based computers can play DVDs, so is it fair to deprive the Linux community?**
A. 	The Linux argument is a false issue. It has always been in the interest of the Motion Picture industry that there be as many legitimately licensed DVD players as possible, including those using non-Windows operating systems. However the argument that DeCSS was written for Linux players is simply false. The De-CSS utility was written for Windows-based software, not Linux.

Also, the development of two, separate, licensed DVD players for Linux systems - which use the CSS system - were recently announced. Sigma Designs ([www.sigmadesigns.com](www.sigmadesigns.com)) and InterVideo Inc. ([www.intervideo.com](www.intervideo.com)) both announced the roll-out of LICENSED, LEGAL Linux-based DVD players.  I went to both Sigma Designs and InterVideo and found no DVD-playing software for Linux that one could download or order for a fee. None. LinDVD is essentially a dead product. All I found on Sigma were some weird hardware things.

---

### Post by The Warlock on 2006-03-07
[QUOTE=issueperson]what would it take to get legal DVD software for linux?[/QUOTE]

A change in the law. That's about it, really. You'd need the DMCA to be ammended. I think a bill (DMCRA or something like that) was proposed a while back and was quietly smothered in MPAA bribes I mean lobbying money. All other solutions are either a) illegal on a technicality, which in the Linux world, translates freely to "hosted in offshore repositories that are ridiculously easy to access", or b) non-free, and non-free projects usually die fairly quickly on the Linux platform due to lack of support (there are exceptions, but these are few).

---

### Post by aysiu on 2006-03-07
[QUOTE=MacV]Linspire has that CNR thing, but I have no intrest in it.[/QUOTE] For American Linux users looking for a legal way to play DVDs, it may be one of the only choices around.

From [the Linspire webpage](http://www.linspire.com/lindows_products_details.php?product_id=11804): > The Linspire DVD player is a software multimedia player that includes legal, licensed commercial-quality codecs and auto-detection of DVDs to enhance the DVD playback experience under Linspire 4.5 and higher.

---

### Post by will_in_wi on 2006-12-01
This article seems to indicate that breaking the css stuff on the dvd for fair use is now legal. Any comments? Especially from free software lawyers?

[http://www.fcw.com/article96922-11-27-06-Web](http://www.fcw.com/article96922-11-27-06-Web)
The original document:
[http://a257.g.akamaitech.net/7/257/2422/01jan20061800/edocket.access.gpo.gov/2006/E6-20029.htm](http://a257.g.akamaitech.net/7/257/2422/01jan20061800/edocket.access.gpo.gov/2006/E6-20029.htm)

---

### Post by christhemonkey on 2006-12-01
The relevant section:
>  3. DVDs that cannot be viewed on Linux operating systems.
    Some commenters proposed an exemption to allow circumvention of CSS 
in order to use their computers running the Linux operating system to 
view motion pictures on DVDs. DVDs protected by CSS may be played only 
on authorized DVD players licensed by the DVD Copy Control Association 
(DVD-CCA). Proponents of an exemption assert that there is no licensed 
player available for the Linux operating system. However, there is 
evidence in the record that Linux-based DVD players currently exist. 
Moreover, there are many readily available ways in which to view 
purchased DVDs. Standard DVD players that can connect to televisions 
have become inexpensive and portable DVD players have decreased in 
price. Similarly, Linux users can create dual-boot systems on their 
computers in order to use DVD software that is compatible with, for 
example, the Microsoft operating system. There are also alternative 
formats in which to purchase the motion pictures contained on DVDs.
    Due to these alternative options for access and use by consumers, 
there is no reason to conclude that the availability for use of the 
works on DVDs is adversely affected by the prohibition. An exemption is 
not warranted simply because some uses are unavailable in the 
particular manner that a user seeks to make the use, when other options 
are available. If a user may access the DVD in readily-available 
alternative ways or may purchase the works in alternative formats, the 
need for the exemption becomes simply a matter of convenience or 
preference. The proposal by users of the Linux operating system is a 
matter of consumer preference or convenience that is unrelated to the 
types of uses to which Congress instructed the Librarian to pay 
particular attention, such as criticism, comment, news reporting, 
teaching, scholarship, and research as well as the availability for use 
of works for nonprofit archival, preservation and educational purposes. 
**The Register cannot recommend an exemption for this class of works.**


In a word, no.

(IAMNAL!)

---

### Post by dca on 2006-12-01
Geez, that's just filibustering...  M$ circumvents the rules by the user buying an actual complete DVD decoder and player like PowerDVD from Cyberlink. How that decoder is actually authorized or in the same boat as a Magnavox DVD player from the BestBuy or how the Xbox w/ a $29 adapter can play DVD(s) and not be compared to the libdvdcss is beyond me...

---

### Post by JeffS on 2006-12-01
This is the kind of crap that really chaps my hyde.

There should be no reason why I can't play my legally purchased DVD, on my legally purchased laptop, which runs my legally obtained Ubuntu Linux.

No doubt, this clause has MS lobbying money behind it.

I consider the restriction of not playing DVDs on Linux unconstitutional, discriminatory, and very immoral.

The bit:

"If a user may access the DVD in readily-available
alternative ways or may purchase the works in alternative formats, the
need for the exemption becomes simply a matter of convenience or
preference."

Isn't playing a DVD on Windows a matter of preference and convenience also?  Isn't playing a DVD on multiple devices, rather than one "blessed" device, a matter of preference and convenience?

Nope.  This is all a matter of locking out a very viable section of the market, restricting honest, law abiding users' freedoms, and helping Microsoft maintain it's desktop monopoly. ](*,)

---

### Post by dca on 2006-12-01
Agreed...
 
When you buy a DVD decoder/player for M$ a portion of the $9.95 to $19.95 gets kicked back somewhere...  That's why the decoder(s)/codec(s) are nec for viewing in Windows Media Player.  At least the licensing of Mpeg3 compression to the Germans is so miniscule, M$ just ponies up the monies I guess...

---

### Post by JeffS on 2006-12-01
After posting in this thread, I googled around for information on the legality of libdvdcss2.

What I mostly came up with was that there is restriction on redistribution (packaged with the main distro) within some countries, but that end users could download it on their own and use it legally.  

Also, libdvdcss2 has not been challenged in court.  

Now DeCSS has been challenged in court, and it is illegal to use it, because it basically hacked an errant Win95 DVD player for the decryption key.  But libdvdcss2 does a "range" or "best guess" algorithm.

From wikipedia (FWIW):

"libdvdcss uses a generated list of possible player keys. If none of them work (for instance, when the DVD drive enforces region coding) a brute force algorithm is tried so the region code of a DVD is ignored. Unlike DeCSS, libdvdcss has never been fought over in a courtroom."

So, as a regular user, I'm not worried about using libdvdcss.  I'm not doing anything illegal, if I so choose to use it.  It's just that it's legally questionable for someone to sell or redistribute libdvdcss, thus the Fedoras, Debians, and Ubuntus of the world refrain from including libdvdcss within their default installs.  But then it's available via 3rd party repos.

---

### Post by vayu on 2006-12-02
> 
"If a user may access the DVD in readily-available
alternative ways or may purchase the works in alternative formats, the
need for the exemption becomes simply a matter of convenience or
preference."


I don't understand how shelling out $200 for Windows is "simply a matter of convenience".  Being morally opposed to commercial television and therefore having no television and associated DVD players available does not make an "alternative format" a matter of convenience for me either.  My DVD player is a Linux based computer and monitor.

---

### Post by ctt1wbw on 2007-03-04
Sure it does.  I love Linux because it's free.  Almost 95% of the software is FREE.

And what's the big deal about open source video drivers?  You telling me that the only ones who make a video driver are the manufacturers of that video card?

And who's to say that the only ones who are authorized and allowed to build cars are Ford, Chevy and Dodge?  What if a group of people decide to build a car in their garage?  Are they violating something, just because they built a car that can do the same thing as a car made by Ford or Chevy?

I just don't get this whole thing.  I am watching a dvd on my laptop right now, runnin g Linux.  Does that mean I'm a lawbreaker or that I'm going to hell just because I can watch a dvd on my laptop?  Who cares.

---

### Post by aysiu on 2007-03-04
> **ctt1wbw said:**
> 
I am watching a dvd on my laptop right now, runnin g Linux.  Does that mean I'm a lawbreaker or that I'm going to hell just because I can watch a dvd on my laptop?  Who cares. Since you live in Virginia, then, yes, you're a lawbreaker, but you're not going to hell because of it.

I think you're not understanding this discussion. It isn't about what costs more or less. It's isn't about what's legal or not legal. It's about the software or, for some people, the drivers being proprietary.

Some of us don't care about whether it's proprietary or not. Some of us care but will still use it. Some of us care and refuse to use it.

---

### Post by ctt1wbw on 2007-03-04
> **aysiu said:**
> Since you live in Virginia, then, yes, you're a lawbreaker, but you're not going to hell because of it.

I think you're not understanding this discussion. It isn't about what costs more or less. It's isn't about what's legal or not legal. It's about the software or, for some people, the drivers being proprietary.

Some of us don't care about whether it's proprietary or not. Some of us care but will still use it. Some of us care and refuse to use it.


I have a dual boot XP/Ubuntu system.  On the same laptop.  Still a lawbreaker?

---

### Post by aysiu on 2007-03-04
> **ctt1wbw said:**
> I have a dual boot XP/Ubuntu system.  On the same laptop.  Still a lawbreaker?
Yes, unfortunately.

---

### Post by SunnyRabbiera on 2007-03-04
But meh, I know I bought and paid for my DVD drive, leagal or not I will use it on what OS I want :D

---

### Post by aysiu on 2007-03-04
Actually, I'm not 100% it is illegal, now that I'm doing some Googling on it.

This is [VLC's take on it](http://www.videolan.org/doc/faq/en/index.html#id289551): > **Is libdvdcss legal?**
The use and distribution of the libdvdcss library is controversial in a few countries such as the United States because of a law called the DMCA (Digital Millennium Copyright Act). If you are unsure about the legality of using and distributing this library in your country, please consult your lawyer. Here's [the SWiK take on it](http://swik.net/libdvdcss): > libdvdcss is a portable core library for the access of DVD video data that has been encrypted with CSS encryption.

libdvdcss is a sub project of VideoLAN, developed for the VideoLAN client. libdvdcss is also used in other video players such as xine, Mplayer and Totem.

libdvdcss&#8217; portability means that there are versions running on Linux, Windows, OSX, Solaris and BeOS.

In the US, under the DMCA law (and potential patent laws), it is possibly illegal to distribute libdvdcss &#8211; thus some distributions such as Ubuntu do not package the library with their official distribution. The question whether libdvdcss is legal or not has never been court tested, so there is no conclusive answer as to whether it can be used and distributed legally. and finally [the LinuxQuestions take on it](http://wiki.linuxquestions.org/wiki/Libdvdcss): > The libdvdcss library can be used to decode encrypted DVDs on a Linux system. Most - but not all - commercially marketed DVDs are encrypted. Contrary to the FUD and popular belief, the purpose of this encryption has nothing whatsoever to do with copy protection. It was developed so that an encrypted DVD could only be played on a licensed player. Licenses are granted by The DVD Forum.

While proprietary DVD players under Windows (such as WinDVD) carry a license and come with a built-in authentication, the situation is a bit more delicate under Linux. Linspire is one linux distribution that is actually licensed by the the DVD Forum.

Libdvdcss must not be confused with DeCSS (be sure to see the wikipedia page) - these are entirely different. Whereas DeCSS uses a cracked dvd player and was alleged to have constituted a breach of the law in Norway, and was fought over in court (proceedings eventually were dropped), libdvdcss has never been the subject of legal proceedings anywhere in the world. In contrast, libdvdcss itself is a key cracking program, and simply creates and tries keys until it hits on the right one.

Googling produces little firm information about the actual legal situation concerning libdvdcss in various specific jurisdictions. Binaries can be downloaded from many locations and libdvdcss compiles by default into MPlayer. It appears at this time that much of the fuss of a few years ago has died down.  So I would say if you want to be 100% certain your DVD playback in Linux is legal, use Linspire. It's possible (some would argue even likely) that libdvdcss2 is illegal in at least the US (if not other countries), but until there's a court case establishing as much, it's still speculation that DMCA would apply to libdvdcss and not just DeCSS.

By the way, I've merged this with a couple other similar threads so you can see more opinions on it all in one place.

---

### Post by SunnyRabbiera on 2007-03-04
Luckily with the linspire clause is that with CNR we can legally obtain the rights to play dvd's very soon :D

---

### Post by seijuro on 2007-03-04
> **SunnyRabbiera said:**
> But meh, I know I bought and paid for my DVD drive, leagal or not I will use it on what OS I want :D

Completely agree, more over I bought ALL of my DVDs LEGALLY and I don't give a s**t that some two faced politician made it technically illegal to decrypt them to watch on the OS of my choosing because of some media big wigs greasing his pockets with money.

---

### Post by SunnyRabbiera on 2007-03-04
Yup, I know I payed a good amount of money for this DVD player on my compy and I will use it as I please,
My philosophy is if I bought the thing I should do whatever i please with it.

---

### Post by imagine on 2007-03-04
Humans have a brain, sense, conscience. Don't let them be replaced by laws.

---

### Post by timjayko on 2007-03-04
aye to that

---

### Post by DoctorMO on 2007-03-04
They used to make decoder cards, like a little pci card that decodes DeCSS encoded discs and these apparently work in linux out of the box.

You know you can watch a DVD that hasn't been encrypted without installing libdvdcss? all you need to do now is replace all your dvds with non excypted versions (not happening) although at least your home video will work ;-)

---

### Post by saulgoode on 2007-03-04
In the United States, the Digital Millenium Copyright Act makes it illegal to circumvent encryption schemes which protect the rights of copyright holders. It is my opinion that watching a DVD using 'libdvdcss' is not a violation of the DMCA because CSS is not designed to protect the copyrights of a DVD's contents -- DVDs can be copied without decrypting them, therefore CSS has nothing to do with protecting copyrights and the DMCA does not apply. 

Of course, *copying* DVDs can be a violation of copyrights; but watching them is not.

---

