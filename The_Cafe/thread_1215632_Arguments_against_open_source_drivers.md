---
title: "Arguments against open source drivers?"
date: 2009-07-17
forum: The Cafe
---

### Post by JDShu on 2009-07-17
Hi, as I delve more into the world of open source, something has been puzzling me. What is the reason that hardware companies do not open source their drivers? As far as I can tell, there is no reason not to since the companies sell the hardware and not the drivers. Can other hardware companies somehow use the code to improve their own hardware or something?

---

### Post by Eisenwinter on 2009-07-17
Other companies can use the code to improve their own drivers, which means it'll make their hardware run better.

---

### Post by MikeTheC on 2009-07-17
Companies fear each other pinching their tricks.

---

### Post by Grant A. on 2009-07-17
Well, some companies, such as Nvidia, license too much Intellectual Property from other companies. Therefore, it would be a legal backbreaker to get all of the companies to agree on a worldwide royalty-free distribution license.

---

### Post by Closed_Port on 2009-07-17
> **Grant A. said:**
> Well, some companies, such as Nvidia, license too much Intellectual Property from other companies. Therefore, it would be a legal backbreaker to get all of the companies to agree on a worldwide royalty-free distribution license.

Do they? And ATI and Intel don't?

---

### Post by c1rcu1t on 2009-07-17
All I can say is that I wish they would.

---

### Post by Skripka on 2009-07-17
> **Closed_Port said:**
> Do they? And ATI and Intel don't?

As I recall, ATi does not--cannot speak for Intel.

---

### Post by aysiu on 2009-07-17
> **Eisenwinter said:**
> Other companies can use the code to improve their own drivers, which means it'll make their hardware run better.
Is this really true?

So if Nvidia said "Here's the code for our drivers," then all of a sudden ATI drivers would improve? I don't see how that could possibly be the case.

---

### Post by MaxIBoy on 2009-07-17
This is the reason I've heard, and it seems very plausible to me.


[LIST=1]
[*]Drivers work with the hardware on a very deep level. If you have the code for the drivers, you can deduce things about the hardware.
[*]Both ATi and nVidia know that, chances are, they are violating each other's hardware-related patents, because that is unavoidable.
[*]If either company were to release the code to their drivers, then the other company could find which patents are being violated in the hardware, and sue.
[*]There are similar problems with software patents held by both companies.
[/LIST]

---

### Post by utnubuuser on 2009-07-17
It's "The Kernel's (Nvidea/Ati) secret recipe". (Pardon the pun).

---

### Post by lykwydchykyn on 2009-07-17
While I could speculate, this article contains some actual statements from Nvidia on the subject:

[http://blogs.zdnet.com/open-source/?p=2588](http://blogs.zdnet.com/open-source/?p=2588)

I can't seem to find the actual press release cited in the article, and they didn't provide a link to it.

---

### Post by Closed_Port on 2009-07-17
> **MaxIBoy said:**
> 
[*]Both ATi and nVidia know that, chances are, they are violating each other's hardware-related patents, because that is unavoidable.

ATI are open sourcing their drivers. So this doesn't seem to convincing.

---

### Post by MaxIBoy on 2009-07-17
> **Closed_Port said:**
> ATI are open sourcing their drivers. So this doesn't seem to convincing.Not quite. They are "scrubbing" sections of code from the drivers before doing so, removing anything that might be incriminating. Really, they're not open-sourcing their drivers, they're just releasing large chunks of "sample" code. Which, from a legal standpoint, is probably the best they can do.

---

### Post by Closed_Port on 2009-07-17
> **MaxIBoy said:**
> Not quite. They are "scrubbing" sections of code from the drivers before doing so, removing anything that might be incriminating. 

Well, afaik, they are keeping some stuff that they licensed closed source, but actively support the open source drivers.

---

### Post by Mehall on 2009-07-17
Yes, new ATI drivers will be open source, but the older ones cannot be, from a legal standpoint.

---

### Post by ghindo on 2009-07-17
Earlier this week, I (coincidentally) saw a video about open source drivers and hardware manufacturers that was very, very interesting.

The speaker in the video mentioned what several posters already have - that the graphics industry is a very competitive and fast-moving industry and as a result, it isn't very enticing for companies like Nvidia and ATI to open source their graphics drivers.

Another interesting point the speaker mentioned was that releasing open source drivers could get a hardware manufacturer into some legal trouble.  For example, if a manufacturer produces a wireless device with open source drivers, and somebody uses those drivers to make the device run at frequencies it isn't supposed to, the manufacturer could get into big legal trouble.

If you'd like to watch the video (and I would absolutely recommend that you do), it's [**here**]("http://mirror.linux.org.au/pub/linux.conf.au/2008/Wed/mel8-094.ogg").  It's about an hour long, but definitely worth a viewing.

---

### Post by JDShu on 2009-07-17
Thanks for the answers, brought lots of things to light. Thanks especially to ghindo, the video was very interesting as a discussion of the pros and cons of open sourcing drivers, as well as the process of open sourcing.

---

### Post by Dimitriid on 2009-07-17
Ive heard the arguments here before but I wonder: why is this not happening with AMD vs Intel?

---

### Post by swoll1980 on 2009-07-17
I don't get why Flash is closed source. They don't sell it. Wouldn't opening the source just gain even more users? What would Adobe have to loose?

---

### Post by Viva on 2009-07-17
> **swoll1980 said:**
> **I don't get why Flash is closed source. They don't sell it.** Wouldn't opening the source just gain even more users? What would Adobe have to loose?

That is news to me. Adobe Flash costs a LOT, only the flash player/plugin is freeware.

---

### Post by ghindo on 2009-07-17
> **swoll1980 said:**
> I don't get why Flash is closed source. They don't sell it.Uhhhh

[http://www.adobe.com/products/flash/](http://www.adobe.com/products/flash/)

---

### Post by swoll1980 on 2009-07-17
> **ghindo said:**
> Uhhhh

[http://www.adobe.com/products/flash/](http://www.adobe.com/products/flash/)

uhhh. I'm talking about the flash player. Not the Flash Professional CS4. You guys really couldn't figure that out on your own? I guess I will have to narrow it down from now on.

---

### Post by Skripka on 2009-07-17
> **swoll1980 said:**
> uhhh. I'm talking about the flash player. Not the Flash Professional CS4. You guys really couldn't figure that out on your own. I guess I will have to narrow it down from now on.

The two are related.

Adobe open sources Flash plugins--and then where does that leave Flash CS4?  If folks know the code behind Flash, they can contrive FOSS alternative to the pricey Flash CS4-- loosing Adobe money.

---

### Post by swoll1980 on 2009-07-17
> **Skripka said:**
> The two are related.

Adobe open sources Flash plugins--and then where does that leave Flash CS4?  If folks know the code behind Flash, they can contrive FOSS alternative to the pricey Flash CS4-- loosing Adobe money.

Can't they just reverse engineer the Flash CS4 like they did the player? I know the open source flash players have their problems, but there getting that squared away.

---

### Post by Skripka on 2009-07-17
> **swoll1980 said:**
> Can't they just reverse engineer the Flash CS4 like they did the player? I know the open source flash players have their problems, but there getting that squared away.

There's a difference between reverse engineering a 10MB plugin...and a 1GB application ;)

---

### Post by T.J. on 2009-07-17
The hurdles toward licensing were resolved at least in part when ATI/AMD went though their specs and released what they were able.

NVidia might be able to do the same, but they probably won't because they feel they have to protect their interests.  Not that it matters really.   The Nouveau project is "clean room" reverse engineering the driver. (For the non-techies - that is legal as long as they have no contact with anyone from NVidia where they could be accused of getting confidential information.)

I'd rather have an open driver anyway.  If Nvidia wants to help, they could release as much tech data as they are able.

---

### Post by swoll1980 on 2009-07-17
> **Skripka said:**
> There's a difference between reverse engineering a 10MB plugin...and a 1GB application ;)

Once they have the plugin figured out, wouldn't it be the same as Adobe open sourcing the player? I'm not trying to argue, I was just wondering about some of this stuff for a while now. I'm sure you now more about this stuff than me.

---

### Post by Viva on 2009-07-17
> **swoll1980 said:**
> Can't they just reverse engineer the Flash CS4 like they did the player? I know the open source flash players have their problems, but there getting that squared away.

They reverse engineered flash already. Look up Gnash.

---

### Post by starcannon on 2009-07-17
With most hardware being fairly apples and apples, the real magic is happening in the software/drivers. That in my opinion is why.

Just to add to the off topic Flash/Gnash discussion. Flash is what you want, Gnash is something to toy with, but if you need flash files to work properly just use the linux version of flash and be happy /shrug or not.

---

### Post by windows-killer on 2009-07-17
> **JDShu said:**
> Hi, as I delve more into the world of open source, something has been puzzling me. What is the reason that hardware companies do not open source their drivers? As far as I can tell, there is no reason not to since the companies sell the hardware and not the drivers. Can other hardware companies somehow use the code to improve their own hardware or something?

There are three reasons my friend:D
you may not believe it or people here will start flaming me but ill tell you the reasons. these guys will lose business if they do that. Open source is not always the right way. 

1) Linux users like to use open source software only, which means they refuse to use closed source software. This tells the software driver company that: Linux users have their own drivers that "somehow work" with lots of effort of course. They also ignore us because of our because we force them to make us open source drivers/ software WHICH IS NOT GONNA HAPPEN!!!

2) Linux users scare away third party software developers because they always ask the developer for the source code. This scares the dev and he refuses to make software for Linux all together and he is right!!! 

3) This is also very important! Market share!!! Canonical and other distro companies/sponsors dont count the number of users that use their operating system. what that means, is that third party developers don know the number of Linux users out there. they think that Linux is only 1% of the desktop market and thats completely wrong! 


So there you go, you got the facts. If anyone disagrees...then sorry but thats the truth and you have to accept it. Dont get me wrong I love Ubuntu, but that is my contribution to make it grow. If you guys dont move forward then no drivers for you, no software for you . ohh and what mean by forward....stop suggesting people to use the damn command line we are in 2009!!! whatever the reason is its still not valid...MOVE FORWARD NOT BACKWARD.


let me ask you this, would you tell everyone your password of your bank account? am sure you wouldint so thats how it goes.

---

### Post by swoll1980 on 2009-07-17
> **windows-killer said:**
> There are three reasons my friend:D
you may not believe it or people here will start flaming me but ill tell you the reasons. these guys will lose business if they do that. Open source is not always the right way. 

1) Linux users like to use open source software only, which means they refuse to use closed source software. This tells the software driver company that: Linux users have their own drivers that "somehow work" with lots of effort of course. They also ignore us because of our because we force them to make us open source drivers/ software WHICH IS NOT GONNA HAPPEN!!!

2) Linux users scare away third party software developers because they always ask the developer for the source code. This scares the dev and he refuses to make software for Linux all together and he is right!!! 

3) This is also very important! Market share!!! Canonical and other distro companies/sponsors dont count the number of users that use their operating system. what that means, is that third party developers don know the number of Linux users out there. they think that Linux is only 1% of the desktop market and thats completely wrong! 


So there you go, you got the facts. If anyone disagrees...then sorry but thats the truth and you have to accept it. Dont get me wrong I love Ubuntu, but that is my contribution to make it grow. If you guys dont move forward then no drivers for you, no software for you . ohh and what mean by forward....stop suggesting people to use the damn command line we are in 2009!!! whatever the reason is its still not valid...MOVE FORWARD NOT BACKWARD.


let me ask you this, would you tell everyone your password of your bank account? am sure you wouldint so thats how it goes.

A bunch of crap ^

---

### Post by MaxIBoy on 2009-07-17
> **windows-killer said:**
> There are three reasons my friend:D
you may not believe it or people here will start flaming me but ill tell you the reasons. these guys will lose business if they do that. Open source is not always the right way. 

1) Linux users like to use open source software only, which means they refuse to use closed source software. This tells the software driver company that: Linux users have their own drivers that "somehow work" with lots of effort of course. They also ignore us because of our because we force them to make us open source drivers/ software WHICH IS NOT GONNA HAPPEN!!!

2) Linux users scare away third party software developers because they always ask the developer for the source code. This scares the dev and he refuses to make software for Linux all together and he is right!!! 

3) This is also very important! Market share!!! Canonical and other distro companies/sponsors dont count the number of users that use their operating system. what that means, is that third party developers don know the number of Linux users out there. they think that Linux is only 1% of the desktop market and thats completely wrong! 


So there you go, you got the facts. If anyone disagrees...then sorry but thats the truth and you have to accept it. Dont get me wrong I love Ubuntu, but that is my contribution to make it grow. If you guys dont move forward then no drivers for you, no software for you . ohh and what mean by forward....stop suggesting people to use the damn command line we are in 2009!!! whatever the reason is its still not valid...MOVE FORWARD NOT BACKWARD.


let me ask you this, would you tell everyone your password of your bank account? am sure you wouldint so thats how it goes.I don't know about you, but I'm not in the habit of putting personal information in my source code...

---

### Post by windows-killer on 2009-07-17
> **MaxIBoy said:**
> I don't know about you, but I'm not in the habit of putting personal information in my source code...

what personal info??

---

### Post by swoll1980 on 2009-07-17
> **windows-killer said:**
> what personal info??

Bank code. Remember? Your the one that mentioned it in the first place.

---

### Post by MaxIBoy on 2009-07-17
Oh, I don't know... the password of my bank account, for example.

---

### Post by windows-killer on 2009-07-17
> **swoll1980 said:**
> A bunch of crap ^

your behavior tells me that you are not open to peoples opinion that is different from yours. you are not an OPEN person at all:D
it looks like Linux users are not following the "Freedom of choice rule."
why? because a closed source developers HAVE the FREEDOM to keep to keep their code PRIVATE if they want to.

---

### Post by windows-killer on 2009-07-17
> **MaxIBoy said:**
> Oh, I don't know... the password of my bank account, for example.

LoL 
now you are thinking realistically. why would you share "open source" your bank account password anyway? because you dont want to lose money! 
You got it little boy, am proud of you!:D

---

### Post by swoll1980 on 2009-07-17
> **windows-killer said:**
> LoL 
now you are thinking realistically. why would you share "open source" your bank account password anyway? because you dont want to lose money! 
You got it little boy, am proud of you!:D

All your base are belong to us.

---

### Post by MaxIBoy on 2009-07-17
> **windows-killer said:**
> LoL 
now you are thinking realistically. why would you share "open source" your bank account password anyway? because you dont want to lose money! 
You got it little boy, am proud of you!:DI accidentally the entire point.

---

### Post by Viva on 2009-07-17
> **windows-killer said:**
> There are three reasons my friend:D
you may not believe it or people here will start flaming me but ill tell you the reasons. these guys will lose business if they do that. Open source is not always the right way. 

1) Linux users like to use open source software only, which means they refuse to use closed source software. This tells the software driver company that: Linux users have their own drivers that "somehow work" with lots of effort of course. They also ignore us because of our because we force them to make us open source drivers/ software WHICH IS NOT GONNA HAPPEN!!!

2) Linux users scare away third party software developers because they always ask the developer for the source code. This scares the dev and he refuses to make software for Linux all together and he is right!!! 

3) This is also very important! Market share!!! Canonical and other distro companies/sponsors dont count the number of users that use their operating system. what that means, is that third party developers don know the number of Linux users out there. they think that Linux is only 1% of the desktop market and thats completely wrong! 


So there you go, you got the facts. If anyone disagrees...then sorry but thats the truth and you have to accept it. Dont get me wrong I love Ubuntu, but that is my contribution to make it grow. If you guys dont move forward then no drivers for you, no software for you . ohh and what mean by forward....stop suggesting people to use the damn command line we are in 2009!!! whatever the reason is its still not valid...MOVE FORWARD NOT BACKWARD.


let me ask you this, would you tell everyone your password of your bank account? am sure you wouldint so thats how it goes.

That is a load of ******** tbh. And a regular user need not use command line at all.

---

### Post by windows-killer on 2009-07-18
> **Viva said:**
> That is a load of ******** tbh. And a regular user need not use command line at all.

Look around the forums its FULL of commands. It looks like its back in the 80s

---

### Post by Grant A. on 2009-07-18
> **windows-killer said:**
> There are three reasons my friend:D
you may not believe it or people here will start flaming me but ill tell you the reasons. these guys will lose business if they do that. Open source is not always the right way. 

1) Linux users like to use open source software only, which means they refuse to use closed source software. This tells the software driver company that: Linux users have their own drivers that "somehow work" with lots of effort of course. They also ignore us because of our because we force them to make us open source drivers/ software WHICH IS NOT GONNA HAPPEN!!!

2) Linux users scare away third party software developers because they always ask the developer for the source code. This scares the dev and he refuses to make software for Linux all together and he is right!!! 

3) This is also very important! Market share!!! Canonical and other distro companies/sponsors dont count the number of users that use their operating system. what that means, is that third party developers don know the number of Linux users out there. they think that Linux is only 1% of the desktop market and thats completely wrong! 


So there you go, you got the facts. If anyone disagrees...then sorry but thats the truth and you have to accept it. Dont get me wrong I love Ubuntu, but that is my contribution to make it grow. If you guys dont move forward then no drivers for you, no software for you . ohh and what mean by forward....stop suggesting people to use the damn command line we are in 2009!!! whatever the reason is its still not valid...MOVE FORWARD NOT BACKWARD.


let me ask you this, would you tell everyone your password of your bank account? am sure you wouldint so thats how it goes.

Sources?

---

### Post by swoll1980 on 2009-07-18
> **windows-killer said:**
> Look around the forums its FULL of commands. It looks like its back in the 80s

Commands are cross platform (KDE, Gnome, xfce). That's why they are given in favor of GUI directions. Not because their isn't a GUI tool for the job. While there are things that can't be done in a GUI environment, they would be nothing a Desktop user would have to bother with.

---

### Post by bodhi.zazen on 2009-07-18
I think this thread has run it's course, :lolflag:

Let's please keep these discussions a bit more respectful .

---

