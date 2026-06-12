---
title: "To what extent does Ubuntu's approach to Free software &quot;work&quot;?"
date: 2007-05-28
forum: The Cafe
---

### Post by aysiu on 2007-05-28
A recent thread, in which a new user complained about Ubuntu not including MP3 playback by default, got me thinking: does Ubuntu's approach to free and non-free software "work"? What is Ubuntu trying to accomplish by not including non-free software by default but also allowing you ways to easily install non-free software? And, given what they are trying to accomplish, is this approach successful?

So the first question is: What is Ubuntu trying to accomplish?

Second question: Is this the best approach to achieving that goal?

My personal take is... I don't know. Some users may feel educated. Many more feel frustrated. And those who are educated... how many actually change their habits? I know I still play MP3s instead of Oggs. I still use Nvidia drivers on my desktop instead of nv drivers. Maybe education is enough, even if it doesn't change people's behavior.

What do you all think?

How is Ubuntu's approach to free/non-free software more or less "successful" (please define what you think that word means in this context) than Debian's or Fedora's or Linux Mint's?

---

### Post by mostwanted on 2007-05-28
> **aysiu said:**
> 

So the first question is: What is Ubuntu trying to accomplish?

I suspect they were trying to avoid a lawsuit in the US while making their distro free (as in beer) at the same time. After Fluendo manufactured a free (as in beer), but proprietary plugin to play mp3, this has changed into a sort of ethical issue I suppose. 

It's not because mp3 is a proprietary format. Word Documents and other proprietary documents are supported by default in Ubuntu. It must be because Mark Shuttleworth feels that including more proprietary bits than is absolutely necessary would be unethical. 

> **aysiu said:**
> 
Second question: Is this the best approach to achieving that goal?


Well they make the user aware that mp3 is a proprietary format, but they also make it easily installable (provided they have an Internet connection). I think they should include it in the default installation, but leave it disabled.

---

### Post by 23meg on 2007-05-28
[QUOTE=aysiu]So the first question is: What is Ubuntu trying to accomplish?[/QUOTE]

Providing an environment where non-Free software is tolerated as a temporary necessary evil, and stressing a strong preference for Free software at the same time, as well as allowing people who want to use non-Free software easy means of doing so.

[QUOTE=aysiu]Second question: Is this the best approach to achieving that goal?[/QUOTE]

I'm mostly satisfied with Ubuntu's take on software freedom: no proprietary applications or codecs by default, proprietary drivers allowed only when absolutely necessary for making the system function, non-Free software clearly segregated and uninstallable, completely Free derivatives encouraged. It's a good compromise, and it's one of the basic reasons I chose to contribute to Ubuntu.

One concern I have is with Multiverse being enabled by default, and the user not being warned when installing something from it. It could have been (and still can be) handled better in the transition to easy codec installation.


[QUOTE=aysiu]How is Ubuntu's approach to free/non-free software more or less "successful" (please define what you think that word means in this context) than Debian's or Fedora's or Linux Mint's?[/QUOTE]

It's quite similar to Debian's except for being opt-out instead of opt-in, pretty close to Fedora's as far as I know, and Linux Mint is just a mess in this regard, so no need for comparison. It's not possible to determine how "successful" any approach is going to be in the short term, so it's best to just make your stance clear, choose the distro that provides the most compatible scheme with it, and contribute to improving that scheme if needed.

---

### Post by Adamant1988 on 2007-05-28
I think Ubuntu as an operating system strikes a very fine balance between free and non-free, only using non-free when it is essential to getting your system to run, which is fair.  However, I think that Canonical could be doing more to further the free-software agenda, and make it more available. 

These are all JUST my opinions, but I think these things would help to further Free Software: 

From Ubuntu.com I should be able to purchase: 
[list]
[*] Complete versions of the repositories on CD, allowing me complete system functionality WITHOUT an internet connection.  Canonical should also be working with ISVs to get applications included on CD complete with their own complete repo on that disk (meaning that all potential dependencies that are not guaranteed to be included in Ubuntu will be on that disk) 

[*] hardware that is open-source friendly.  (If there is a distributor of laptops who is at a certain level of partnership with Ubuntu, their products should be available directly from Ubuntu.com.   The same goes with Graphics cards, etc.

[*] Devices that are open-standards compliant and will work well with Ubuntu.  Mp3 players, Printers, Cameras, Palm Pilots, you name it.  Any of these items that are compliant with open standards and will work properly on Ubuntu should be available DIRECTLY from the Ubuntu.com website. 
[/list]

My opinion is that if Canonical would like more people to be using Free Software, they need to be doing everything they can to make that transition as absolutely painless for us as possible.  Using any of the above methods, as well, Canonical could start bringing in some money to pay more developers, etc.

---

### Post by ajgreeny on 2007-05-28
This is surely down to patent infringement possibilities in the USA, in particular, which is why a lot of users' wish for vlc as the default media player is not possible.  It's a shame in some ways, but if someone is "clever" enough to look at ubuntu seriously, then it shouldn;t take them long to find out how to add the various codecs etc, needed to play just about anything.

---

### Post by aysiu on 2007-05-28
Ubuntu's choices are mainly made with their philosophy in mind. Legal issues come second.

Read more here:
[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)
[http://www.ubuntu.com/community/ubuntustory/licensing](http://www.ubuntu.com/community/ubuntustory/licensing)

---

### Post by Matakoo on 2007-05-28
> **aysiu said:**
> My personal take is... I don't know. Some users may feel educated. Many more feel frustrated. And those who are educated... how many actually change their habits? I know I still play MP3s instead of Oggs. I still use Nvidia drivers on my desktop instead of nv drivers. Maybe education is enough, even if it doesn't change people's behavior.

To be honest, I kinda feel like Adrian Kingsley-Hughes here (and that's really odd since I don't agree with him all that often...) in his article about Dell and Linux.

*# At this time, we are not including any support for proprietary audio or video codecs that are not already distributed with Ubuntu 7.04. These include MPEG 1/2/3/4, WMA, WMV, DVD, Quicktime, etc. We are evaluating options for providing this support in the future.*

**Now this is bad.  Really bad.  The bottom line here is that Dell are happy to ship systems with no ability to handle the kinds of common media that computer users will encounter.  Yeah, sure, this isn&#8217;t an issue if you know what you&#8217;re doing with a Linux box, but then again people with that kind of knowledge aren&#8217;t usually the kind to give their money to Dell.  The innocents buying a Linux rig from Dell expecting a system with all the features they&#8217;ve come to expect from a PC, will be in for a real disappointment.**

Sure, they're easy to install. Especially mp3-support, since that basically means clicking "Yes" the first time you try to play one. People expect that kind of functionality of a computer today, no matter what OS it's running. Or a lot of people do anyway, and your everyday non-technical user is not going to care why it doesn't work out of the box. They just want the functionality, and is not likely to care about issues of free software versus non-free.

Hey, I consider myself fairly knowledgeable about the differences but I still enable all of that on every machine I install Ubuntu on. It's just a drag that I have to do it. If we want people to embrace Linux, such things just need to work. Otherwise, people will just think that Linux just doesn't cut it.

Actually, that's a good case for having two versions of Ubuntu as Mr Shuttleworth mentioned somewhere. One pure free, and one with some non-free add-ons. Kinda like Freespire does it, really.

---

### Post by 23meg on 2007-05-31
> **Matakoo]your everyday non-technical user is not going to care why it doesn't work out of the box. They just want the functionality, and is not likely to care about issues of free software versus non-free.[/QUOTE]

They don't *have to* care said:**
> If we want people to embrace Linux, such things just need to work. 

Well, they work, don't they?

[QUOTE=Matakoo]Actually, that's a good case for having two versions of Ubuntu as Mr Shuttleworth mentioned somewhere. One pure free, and one with some non-free add-ons.[/QUOTE]

No it's not. The normal Ubuntu will include the Restricted component, but not proprietary codecs, and the all-Free one will be that minus Restricted, and a few fonts with not-absolutely-Free licenses. Proprietary codecs and applications will always be out of the picture. If people must have non-Free codecs out of the box, there are derivatives that do it.

---

### Post by FuturePilot on 2007-05-31
I think it works great. I like the fact that Ubuntu tries to stay with it's roots in the Debian philosophy of keeping everything included by default "free". But I also like the way that it makes it easy to install the non-free stuff. I try to stay away from proprietary stuff as much as possible, but I won't be able to change some habits. I'm not going to convert all my MP3s to OGG because my MP3 player can't play that format. And I need those Nvidia drivers because without them, well, performance stinks.

I think Ubuntu is trying to accomplish an open source OS but at the same time still being practical about it. I think the best way to get people to change their habits is to inform them more about the open source alternatives. Like OGG instead of MP3.

---

### Post by BoyOfDestiny on 2007-05-31
> **ajgreeny said:**
> This is surely down to patent infringement possibilities in the USA, in particular, which is why a lot of users' wish for vlc as the default media player is not possible.  It's a shame in some ways, but if someone is "clever" enough to look at ubuntu seriously, then it shouldn;t take them long to find out how to add the various codecs etc, needed to play just about anything.

Agreed. Not to mention the DMCA here as well.

libmad (MP3 decoder) and decss (for decrypting encrypted DVDs) are both GPL'd. 
**To call them non-free is misleading**. 
Unless of course violating patents or circumventing a encryption scheme (however ineffective said scheme is) makes software non-free... I wouldn't apply that definition however, or a lot of software would fall under non-free.

About DMCA, and some of it's ill effects
[http://www.eff.org/IP/DMCA/](http://www.eff.org/IP/DMCA/)

MP3 Patents
[http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues)

---

### Post by sloggerkhan on 2007-05-31
I think it's stupid to worry about software patents in the US when they've never been uphelp by our supreme court.... However I can understand not wanting to spend money on litigation.

---

### Post by BuffaloX on 2007-05-31
> **aysiu said:**
> 
(edited)
1: Complaint about Ubuntu not including MP3:
2: Does Ubuntu's approach to free and non-free software "work"?
3: What is Ubuntu trying to accomplish by not including non-free software by default but also allowing you ways to easily install non-free software? And, given what they are trying to accomplish, is this approach successful?
Is this the best approach to achieving that goal?

How is Ubuntu's approach to free/non-free software more or less "successful" (please define what you think that word means in this context) than Debian's or Fedora's or Linux Mint's?

1: Free as speech mp3 software exist like the lame encoder/decoder.
I find it a little annoying that this is not included, It&#347; only potentially a problem in US AFAIK. So remove mp3  for US shipments. We have SAMBA which also communicate with proprietary protocols. I don understand why SAMBA is OK, and mp3 is not. Please educate me on this.

2: I'd say yes, the Ubuntu approach is generally well balanced, some issues are a little tough, like proprietary hardware drivers, and Ubuntu attempts to find middle ground as I see it.

3.1: By not including non free software, we avoid some of the problems associated with most proprietary software, like protocol/format lock-in, potential spy/mal-ware, however easy access or maybe even inclusion of non free software can occasionally be OK, if the service rendered is essential AND the provider is trustworthy. This will often be a very individuall estimation, because need and trust is personal.
Giving easy access, and let it be up to the user, is always the safest bet.

---

### Post by GSF1200S on 2007-05-31
> **Matakoo said:**
> To be honest, I kinda feel like Adrian Kingsley-Hughes here (and that's really odd since I don't agree with him all that often...) in his article about Dell and Linux.

*# At this time, we are not including any support for proprietary audio or video codecs that are not already distributed with Ubuntu 7.04. These include MPEG 1/2/3/4, WMA, WMV, DVD, Quicktime, etc. We are evaluating options for providing this support in the future.*

**Now this is bad.  Really bad.  The bottom line here is that Dell are happy to ship systems with no ability to handle the kinds of common media that computer users will encounter.  Yeah, sure, this isn’t an issue if you know what you’re doing with a Linux box, but then again people with that kind of knowledge aren’t usually the kind to give their money to Dell.  The innocents buying a Linux rig from Dell expecting a system with all the features they’ve come to expect from a PC, will be in for a real disappointment.**

Sure, they're easy to install. Especially mp3-support, since that basically means clicking "Yes" the first time you try to play one. People expect that kind of functionality of a computer today, no matter what OS it's running. Or a lot of people do anyway, and your everyday non-technical user is not going to care why it doesn't work out of the box. They just want the functionality, and is not likely to care about issues of free software versus non-free.

Hey, I consider myself fairly knowledgeable about the differences but I still enable all of that on every machine I install Ubuntu on. It's just a drag that I have to do it. If we want people to embrace Linux, such things just need to work. Otherwise, people will just think that Linux just doesn't cut it.

Actually, that's a good case for having two versions of Ubuntu as Mr Shuttleworth mentioned somewhere. One pure free, and one with some non-free add-ons. Kinda like Freespire does it, really.

I kind of agree here... I also agree with the post directly above. I think complete noobs who want to be free of Windows or who have heard good things about Linux will be in for a rude surprise.

People here are willing to mess with stuff, but whos to say that new users arent immediately going to become irritated and go pick up Vista from there local computer store?

---

### Post by 23meg on 2007-05-31
[QUOTE=GSF1200S]whos to say that new users arent immediately going to become irritated and go pick up Vista from there local computer store?[/QUOTE]

Me, on the assumption that everyone who can buy those computers knows how to double click a media file, and would expect it to play when double clicked.

---

### Post by GSF1200S on 2007-05-31
> **23meg said:**
> Me, on the assumption that everyone who can buy those computers knows how to double click a media file, and would expect it to play when double clicked.

Yeah, pertaining to mp3s. What about other formats that one encounters that arent as easily remedied? WMV, AVI, etc.. I know I had to go on a codec search after installing Kubuntu to make all of my different formats to play- it didnt just tell me "go here to download the codec." I have absolutely no problem doing this, as its fun and I learn things. Im just saying the average mom isnt going to know what to do and might become frustrated...

I hope im wrong and youre right, believe me... Windows' monopoly has stupified far to many people...

---

### Post by runningwithscissors on 2007-05-31
> **BuffaloX said:**
> 1: Free as speech mp3 software exist like the lame encoder/decoder.
I find it a little annoying that this is not included, It&#347; only potentially a problem in US AFAIK. So remove mp3  for US shipments. We have SAMBA which also communicate with proprietary protocols. I don understand why SAMBA is OK, and mp3 is not. Please educate me on this.
SMB was not invented by Microsoft. They are merely the most prominent users of it and run a heavily modified version of it. And the organisations holding the patents on mp3s have been quite litiguous. So, it's better to be on the safe side unless you have the funds to fight out a long drawn out patent battle in the courts, which you'd have little chance of winning as well.
What I don't understand is why these average whinging losers just don't use another format for their music? Linux distros are not going to fight your battles for you, neither are they going to license the codec for you to use. It costs a lot of money.

> **BuffaloX said:**
> 2: I'd say yes, the Ubuntu approach is generally well balanced, some issues are a little tough, like proprietary hardware drivers, and Ubuntu attempts to find middle ground as I see it.Which is very appropriate, I think.

> **BuffaloX said:**
> 3.1: By not including non free software, we avoid some of the problems associated with most proprietary software, like protocol/format lock-in, potential spy/mal-ware, however easy access or maybe even inclusion of non free software can occasionally be OK, if the service rendered is essential AND the provider is trustworthy. This will often be a very individuall estimation, because need and trust is personal.
Giving easy access, and let it be up to the user, is always the safest bet.Completely agree.

---

### Post by 23meg on 2007-05-31
> **GSF1200S said:**
> Yeah, pertaining to mp3s. What about other formats that one encounters that arent as easily remedied? WMV, AVI, etc.. 

I don't know about Kubuntu, but in Ubuntu, the codec installer will install all the GStreamer stuff available, which is virtually everything people will need with the default setup (Totem with GStreamer backend).

[https://wiki.ubuntu.com/EasyCodecInstallation](https://wiki.ubuntu.com/EasyCodecInstallation)

---

### Post by jrusso2 on 2007-05-31
I think Ubuntu's approach has slowly gotten better with feisty but there is still room for improvement.  I would like to see them work out arrangements like Freespire where they can include codecs,dvd,  properietary drivers, flash and proprietary firmware on the cd-rom so it can be installed easily and new users can be up and running.

I would also like to see them make an effort to fill in the gap where drivers are needed and unavailable for winmodems and printers.

To me this is the only way for Linux to ever succeed on the desktop.

Even if they have to provide some kind of proprietary dvd decrpytion to be legal like mandriva did with lindvd.

At least until the open source alternatives are working and ready.

I have been using Linux for 11 years now so I am not some newbie user.  I have been hearing about Linux on the desktop being a year away for ten of those years.

I would love to see it really happen but I think the political wing of Linux has everyone bullied into thinking they can't break with the program to make this work for regular users.

---

### Post by Matakoo on 2007-05-31
> **23meg said:**
> They don't *have to* care; they can just double click the file, install the codecs and move on. This is part of what Mr. Hughes and his counterparts in other IT sites pretend not to understand; it's a big red herring really, but they love to make an issue out of it, it's their mission as masters of the FUD.

Well, they work, don't they?

Sort of, yes. A great step forward but there is some way to go yet. It works great for some formats, but less so for other formats (biggest culprit being those covered by the w32codecs, at least on my machine, not to mention DVD playback). And in Kubuntu it doesn't work at all.

Now, if something doesn't work with the automatic codec download what is a non-technical minded person gonna do (and they probably does not even know what a codec is for)? It's no problem for those who know what they're doing or not afraid of trying, but those are fewer in numbers.

I agree that Hughes and his ilk are good at spreading FUD, but in this case he has a point even though he exaggerates. I also agree that there are problems with having them included by default, so I guess the obvious answer is to make the codec-download more fool-proof, and work in all official versions. 

> **23meg said:**
>  No it's not. The normal Ubuntu will include the Restricted component, but not proprietary codecs, and the all-Free one will be that minus Restricted, and a few fonts with not-absolutely-Free licenses. Proprietary codecs and applications will always be out of the picture. If people must have non-Free codecs out of the box, there are derivatives that do it.

Yes, I know that. Shuttleworth's distinction is just a small step in "separating" the free-at-any-cost crowd from the more pragmatic ditto.

Somehow I don't see the point of just that rather minor distinction, really. The restricted section is mostly "only" proprietary drivers, and not installed by default anyway. Well, okay. Minor distinction was an exaggeration. My point is that if you want a FOSS-only system, you probably know what you're doing and wouldn't enable the restricted portions of the system anyway. Besides, for those people there is always Debian or Slackware - and they're probably already running a FOSS-only system.

No, I think Freespire's approach here is far more sensible when it comes to catering to both kinds of user. I don't really like their distro otherwise, but that may be just me. And it's odd...when I tried it it refused to recognize my mouse. First time I've seen that on a bog standard USB-mouse...

---

### Post by Matakoo on 2007-05-31
> **runningwithscissors said:**
> 
What I don't understand is why these average whinging losers just don't use another format for their music?

How many portable music players do you know of that can play ogg-files? Personally, I can think of none (but I haven't paid all that much attention to the small print on every model either). Right or wrong, mp3 and/or wma are de-facto standards and people are bound to run into them sooner or later. Legally or otherwise.

---

### Post by Pobega on 2007-05-31
Ubuntu's approach is good for what Ubuntu is being used by. non-free things aren't included by default (Are they in Feisty?), and Ubuntu's lax rules allow documentation licensed under the GFDL to be included in their repositories; Debian has been having problems with packaging programs due to the proprietary nature of the GFDL.

Plus, it keeps Ubuntu out of trouble. If Ubuntu included illegal codecs by default then it would get hammered down, especially considering the size of it's userbase.

---

