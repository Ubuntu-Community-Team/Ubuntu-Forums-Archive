---
title: "Firefox problems Ratel Value"
date: 2009-10-05
forum: System76 Support
---

### Post by tgs1952 on 2009-10-05
Recently purchased a Ratel value for my dad.

There seems to be a major problem with Firefox ( I assume 3.* since I just purchased the machine in Sept.)

On many websites it 'grays out' for some time. It is also unbelievably slow.

His previous machine was a 7 year old Dell laptop (250mgs of ram) running Xubuntu and it was way faster than the new machine which has a gig of ram and a much faster processor.

I too have experienced the 'gray out' in firefox occasionally on my Koala.

But he is having it constantly.

Thanks in advance.

---

### Post by miniyak on 2009-10-05
try using epiphany, chromium or other browser and see if you have the same issue.

chromium (google chrome), can be easily installed using ubuntu tweak, ubuntu tweak in turn can be found in synaptic package manager

Epiphany can be found in add/remove software

---

### Post by samalex on 2009-10-06
[QUOTE="tgs1952"]On many websites it 'grays out' for some time. It is also unbelievably slow.[/QUOTE]

Firefox 3.0 does this to me from time to time on my PanP5, and my only guess is it's due to the wrapper for Flash since it mainly does it on Flash enabled sites.  When Gnome grays out an application that means it's not responding, so I'm thinking the Flash wrapper is cranking behind the scenes and just causing Firefox to hang for a bit.  Most of the time Firefox comes back in a few seconds, but it is annoying.

I'm happy with what I have thus far, but I'm seriously thinking of doing a clean install of 32-bit Ubuntu 9.10 when it's released just because I've ran into a few problems like this with the 64-bit version of Ubuntu.  Not that Ubuntu or even System76 is to fault, but rather there's just not as much support for 64-bit Linux yet and Adobe said they will roll out [Flash 10.1 to all clients at the same time first half of 2010]("http://labs.adobe.com/technologies/flashplayer10/") which I'd rather not wait 6-9 months for a native, stable version of Flash.  At first it was just an annoyance but like you're running into it's happening more and more.

Sam

---

### Post by thomasaaron on 2009-10-06
Do you mean the whole machine is slower or just Firefox?

---

### Post by miniyak on 2009-10-06
flash 10 alpha has performed much better for me then the latest "stable" version of flash. Not that im recommending something labeled alpha. But if your having an issue already it wouldn't hurt to try it out.

For the record I like firefox and it is my main browser because it is so customizable. However it would lying if I said that its not going downhill because of bloat. Or maybe add-ons and plugins that drag it down. Whichever is the case, I would say that Chrome is noticeably faster and responsive then even firefox 3.5.

Other questions to bring up if firefox is the main issue. 

Do you have any RSS feeds? -too many can equal lag in responsiveness on start-up in some instances

What type add-ons are you using?- How many matters very little, what matters more is if you have an add-on that sucks up process cycles or "phones home"

How many tabs do you have running with dynamic content?- meaning demanding content, flash pages, gmail, docs, ect.

Have you messed around in the about:config?- if so, maybe you shouldn't have. If you haven't maybe you should look in to it. Paradox of attention, make sure you are certain of what your doing before using the about:config to tweak firefox.


Reinstalling firefox in synaptic may provide a magical solution to the issue but im not promising anything

---

### Post by tgs1952 on 2009-10-06
Thanks for the replies.

The problem I am describing is not my problem; it is my fathers. He does not live where I do. I purchased the Ratel for him and set it up for him.

When I set it up I noticed the problem with firefox. However, since I have had the same problem on my Koala occasionally, I didn't think too much about it. I will note, however, that I have not had that kind of problem with firefox on fedora on the box I use at work.

However, he called me two days later saying that the gray out is occurring constantly. My impression is that the problem is the browser - not the computer.

I came home tonight and had received a similar message with the addition that the back button has grayed out and the google search box is gone.

I had told him to try Epiphany if it is installed. I have no idea if he did. He is 78 years old - and not computer savvy though his entire home computing experience has been with Linux.

---

### Post by miniyak on 2009-10-07
ok, im getting the impression that some of the "other questions" i brought up probably don't apply in your fathers case.

I had this problem on my older dell. This could have been because there were too many things added or because of hardware performance, I'm not sure. However reinstalling firefox worked for me, I should note that almost all the previous add-ons were reinstalled after the fact without issue. 

If your dad has never used synaptic I would just give him a quick walkthrough reinstalling over the phone with an Ubuntu system in front of you. When helping someone over the phone I always find it very convenient to be doing the same things that are being advised.  

It was a while ago so I forget exactly, but Im pretty sure that the complete removal option was checked, apply, check to install, apply. A simple re-installation option maybe available though. Bookmarks and other personal settings will be lost with those methods. This can be avoided in various ways, like using x-marks for instance. Just depends on what your father wants to keep. 
> 
I had told him to try Epiphany if it is installed.

He will have to install Epiphany through Add/Remove or synaptic. Only firefox comes with Ubuntu in the default installation.

> the addition that the back button has grayed out and the google search box is gone.

the back button being grayed out could simply mean there is no page to go back to, and the search bar can be added back in if it was accidentally removed, (through View> Toolbars> customize> find search bar, drag and drop)

---

### Post by tgs1952 on 2009-10-07
> **thomasaaron said:**
> Do you mean the whole machine is slower or just Firefox?

No, I think it is just the browser. The machine seemed fine when I set it up.

Basically, he only uses the browser - slow browser = slow machine.

---

### Post by Teasdale on 2009-10-07
I have a Ratel, too, and it also has some odd issues with Firefox - some pages load with the content way, way down on the page, and one message board selectively loads a few avatars and refuses to show most of the others. I can't imagine any logical reason to explain why.

Epiphany works fine. Unfortunately, if you didn't install it for him, then he doesn't have it - it doesn't come already installed.

---

