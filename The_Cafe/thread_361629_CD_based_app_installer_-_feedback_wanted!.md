---
title: "CD based app installer - feedback wanted!"
date: 2007-02-14
forum: The Cafe
---

### Post by deanlinkous on 2007-02-14
Hey all.
Would a CD based software installer be useful? needed? wanted? crap?
As in, you pop in a cd, it autoplays, your browser pops up with a friendly webpage that lets you browse the software available on the CD with descriptions, screenshots, and maybe a mini-review or something and to install you just click on a button? 
Thoughts?

edit - this would be for free/open software only! :D (remember I am a zealot)

---

### Post by PatrickMay16 on 2007-02-14
Whouuugughhhh!!!!!!!! I think this could be pretty good. It could be used so that linux software could be sold in shops, like PC world. Or over the internet, for people who can't afford to download stuff (like people in countries with poor net access, or people with dialup).

---

### Post by Adamant1988 on 2007-02-14
> **deanlinkous said:**
> Hey all.
Would a CD based software installer be useful? needed? wanted? crap?
As in, you pop in a cd, it autoplays, your browser pops up with a friendly webpage that lets you browse the software available on the CD with descriptions, screenshots, and maybe a mini-review or something and to install you just click on a button? 
Thoughts?

edit - this would be for free/open software only! :D (remember I am a zealot)

YEAH! I suggest some kind of "Fair use" technology to prevent anyone from loading proprietary bits!

Anyway, not needed right now, but if Linux makes it to the OEMs software installation via some kind of method other than the net will be needed, perhaps usb keys since they're so cheap..

---

### Post by deanlinkous on 2007-02-14
No need to use protective technology to restrict proprietary bits, if it is not a product on the webpage then it cant be installed using this method. 

Not suggesting anything professional. Nothing for OEMs or tier2 or any of that stuff. Just a homegrown effort to provide some software on a CD with a dead easy simple installer. Webpage, screenshots/description/mini-review maybe and a install button. Maybe a link to the homepage for the software and maybe a link to a forum thread to discuss the software  or rate the software or both....

Just ISOs you can download or order for a couple bucks that provide software packages on a cd with a simple wepage front end. For a couple extra bucks you can request a CD with certain packages on it.

Maybe have a office ISO, game ISO, graphics ISO, multimedia ISO or something...

Actually I could have a  (install from cd) button and a (install from the net) button.

It would simply be software that is currently in the repo or that I can ensure would install cleanly.

It would not provide anything that synaptic does not but it would be a bit simpler and no changing sources.list. It would not be a real application. It would simply be a page that called scripts that used dpkg/apt to install stuff silently and created a desktop icon.

Thanks for the feedback..........

---

### Post by ssam on 2007-02-14
if you are targeting ubuntu (and/or debian/linspire/etc) then you just need you web pages to link to .deb files on the disk. .debs will get automatically installed by gdebi.

---

### Post by Jammy_Stuff on 2007-02-14
I'm really interested in this. Out of interest, how would you go about making an install from CD button?

---

### Post by deanlinkous on 2007-02-14
A link on the page that calls a script on the cd the script uses apt/dpkg to silently install the software....

---

### Post by deanlinkous on 2007-02-14
I just figure that some users think that synaptic is too confusing and does not provide enough information.

Users are use to popping a cd in and having it pop up and have clicky buttons to install stuff.

I actually came up with this a couple/few years ago and dismissed it as stupid so never did anything with it.

---

### Post by Omnios on 2007-02-14
Would be nice to have it so that synaptic or apt-get can mount a install cd with just a list o fwhat is on the CD.

 This would be a very powerfull tool for those who install Ubuntu and Ubuntu stuff on other peoples  computers Like my Dads as he only has dial up.

---

### Post by deanlinkous on 2007-02-14
> **Omnios said:**
> Would be nice to have it so that synaptic or apt-get can mount a install cd with just a list o fwhat is on the CD.

 This would be a very powerfull tool for those who install Ubuntu and Ubuntu stuff on other peoples  computers Like my Dads as he only has dial up.

That is basically what it is.  Also providing links to the software homepage, maybe the discussion forum, along with a screenshot or two, description, maybe a review along with a install button of course. :) Screenshots,mini-review, and description are stored on the CD of course. 

I dismissed it years ago because I did not think anyone would bother with it since we had synaptic -  now I am just wondering if it would be useful.

---

### Post by Polygon on 2007-02-14
isnt this sorta already implemented? like if you put a live cd in your ubuntu computer, synaptic thinks that the cd is a repo and you can install stuff from it?

but this does sound like a cool idea though

---

### Post by deanlinkous on 2007-02-14
As stated  -  this does not do anything that synaptic is not capable of doing. This would be a bit more simple, should autostart when you insert the disk, and offer a link to the packages homepage, and maybe a link to a forum thread to discuss the software along with screenshots. Thats about it. :D

---

### Post by piratepenguin on 2007-02-14
I've work started (well, just about) on this kindof a thing, and I still HOPE to have something ready before software freedom day in September this year (most of the work being done when I get off school for the Summer).

Wiki's @ [http://piratepenguin.is-a-geek.com/~declan/freecd/](http://piratepenguin.is-a-geek.com/~declan/freecd/)

It will be distribution and operating system agnostic, and hopefully use (a cross-platform implementation of) [conary](http://wiki.rpath.com/wiki/Conary) for package management.

Since I chose Mozilla for the dev framework, I should be putting out a Firefox (and IceWeasel!) extension which allows you to install new packages, and I should be able to put out an interesting contrib website based on that.

And it will be entirely, and utterly, Free.

(found the thread from your post to the gNewSense mailing list, btw ;))

---

### Post by deanlinkous on 2007-02-14
WOW sounds (WAY) above and beyond what I have planned.That sounds really interesting and cool! I feel ashamed of my little idea now...  gNewSense ROCKS! ;)

---

