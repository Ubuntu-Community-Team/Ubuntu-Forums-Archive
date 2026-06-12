---
title: "Ubuntu Netbook Edition *FAIL*"
date: 2010-06-23
forum: Testimonials &amp; Experiences
---

### Post by neu5eeCh on 2010-06-23
Just had the recent experience of trying to install Netbook Edition (and other Ubuntu derivatives) on my wife's HP Mini. 

Her Netbook, like others, does not come with an ethernet port - only wireless.

Catch 22: The Broadcom BCM4312 Wireless card isn't supported out of the box. That means she couldn't connect to the web to download the driver she needed to connect to the web so that she could download the driver she needed to connect to the web.

Wash. Rinse. Repeat.

This seems like a ripping, breathtaking oversight on Canonical's part. How many newbies carry a USB to Ethernet cable on them? I don't (though I've ordered one).

If Canonical is going to design a platform _specifically for Netbooks_, then it's a no-brainer. Period.  Make sure that all the wireless drivers for the various netbooks are included in the netbook edition (since many, if not most of them, can't connect to the web without wireless). Right?

Think about it, Canonical.

---

### Post by snowpine on 2010-06-23
Read the instructions before you rant, especially the "No Internet Access" sections:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

To address your specific concern, Canonical can't legally include the Broadcom driver out-of-the-box. It is proprietary, closed-source software, and really your complaint should be to Broadcom for not releasing an open-source driver. :)

---

### Post by neu5eeCh on 2010-06-23
Thanks for the link. I have posted this problem here (on another post) and at other forums. Your response is the first conclusively helpful response I have received.

As to my specific concern: If Canonical can't legally include the Broadcom driver (which is debatable but let's just agree to agree), then they should provide the instructions included in the link. This should be front and center. When a beginner clicks on the dead Wireless Icon, this information should be immediately available.

The point is this: **If** they are going to tout a Netbook centric OS, then they **need** to anticipate this problem (and it's not hard to anticipate). I stand by my rant. :-)

---

### Post by snowpine on 2010-06-23
I haven't used Ubuntu in a while :) so maybe my memory is a little foggy, but I seem to recall that, when using the Live CD, there is a Restricted Hardware Manager icon that pops up and tells you if your hardware requires a non-free driver. 

Lots of hardware requires a nonfree driver (not just Broadcom wireless) and I agree with you it is probably the #1 most frustrating issue with Linux these days. :)

---

### Post by 3rdalbum on 2010-06-23
The driver can be downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com) on another computer and transferred across on a flash drive, or if you have mobile broadband or a supported wifi USB dongle you can use those to get the driver.

I don't think Canonical is doing anything different to Microsoft; it's not always legally possible to redistribute a driver. I'll also point out that most netbooks include Ethernet, and in fact I had previously thought that ALL netbooks included Ethernet.

---

### Post by neu5eeCh on 2010-06-23
> **3rdalbum said:**
> The driver can be downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com) on another computer and transferred across on a flash drive, or if you have mobile broadband or a supported wifi USB dongle you can use those to get the driver.

I don't think Canonical is doing anything different to Microsoft; it's not always legally possible to redistribute a driver. I'll also point out that most netbooks include Ethernet, and in fact I had previously thought that ALL netbooks included Ethernet.

Thanks for the tip on packages. I checked it out.

Talk about dependency hell... I could download the driver, but that driver has dependencies and all those dependencies have dependencies. That's **way** above my pay scale. I could spend an entire day sorting through what's needed and what's not. I don't think that's the answer.

I **am** going to follow the instructions on the first link - see if that works.

As to Microsoft, they're not trying to persuade folks to use their system on the Netbook. They're already there. If they were in the same position as Canonical? One can only speculate.

---

### Post by snowpine on 2010-06-23
> **VTPoet said:**
> As to Microsoft, they're not trying to persuade folks to use their system on the Netbook. They're already there. If they were in the same position as Canonical? One can only speculate.

As far as I know, Microsoft doesn't ship Broadcom and other non-free drivers with a retail copy of Windows either. If you install Windows yourself, you need to track down all the drivers yourself too.

I think your actual rant is "installing the OS from scratch vs. using a preinstalled OS" rather than "Linux vs. Windows."

If you buy a system with Linux preinstalled it should work out out of the box just as well as a system with Windows preinstalled. If you buy a system with Linux preinstalled and try to install Windows, it will be just as big a headache as buying one with Windows preinstalled and trying to install Linux. :lolflag:

I think the moral of the story is that non-techie users are advised to either 1) purchase hardware with their choice of OS preinstalled or 2) purchase hardware that they've verified ahead of time is easily compatible with their choice of OS. Buying random hardware and crossing your fingers it will work with some 3rd party OS is a gamble.

---

### Post by tgm4883 on 2010-06-23
I previously thought all netbooks had a ethernet port too. My HP mini does. What model is your netbook without one?

---

### Post by Jazzy_Jeff on 2010-06-23
So you are complaining that a computer specifically designed to work with windows will not work completely out of the box on Linux?? I know if I want one to work out of the box on Linux, I would buy one designed for, um, Linux maybe.

---

### Post by WinterRain on 2010-06-23
> **Jazzy_Jeff said:**
> I know if I want one to work out of the box on Linux, I would buy one designed for, um, Linux maybe.

That's how people *should* think, but unfortunately the average person does not think that way. But I would expect more from an experienced linux person.

---

### Post by eltonw on 2010-06-23
> **VTPoet said:**
> Just had the recent experience of trying to install Netbook Edition (and other Ubuntu derivatives) on my wife's HP Mini. 

Her Netbook, like others, does not come with an ethernet port - only wireless.

Catch 22: The Broadcom BCM4312 Wireless card isn't supported out of the box. That means she couldn't connect to the web to download the driver she needed to connect to the web so that she could download the driver she needed to connect to the web.

Wash. Rinse. Repeat.

This seems like a ripping, breathtaking oversight on Canonical's part. How many newbies carry a USB to Ethernet cable on them? I don't (though I've ordered one).

If Canonical is going to design a platform _specifically for Netbooks_, then it's a no-brainer. Period.  Make sure that all the wireless drivers for the various netbooks are included in the netbook edition (since many, if not most of them, can't connect to the web without wireless). Right?

Think about it, Canonical.

Perhaps some of this might point you in the right direction:

HOW I installed Lucid on my Asus EEE 1000 PC:
[http://ubuntuforums.org/showthread.p...22#post9203922]("http://ubuntuforums.org/showthread.p...22#post9203922")[#136]

Seeing that you'll need the **Broadcom** drivers, and [COLOR="DarkRed"]going by your subsequent comments, I would suggest using a USB wifi card, such as a Lyksys, which should provide you with the necessary Internet connectivity[/COLOR] to download and install the Broadcom drivers, including whatever dependencies.

[COLOR="Sienna"][FONT="Comic Sans MS"]In addition, the following may be useful to you in furthering your knowledge of LINUX:[/FONT][/COLOR]
[http://ubuntuforums.org/showthread.php?t=1483371&highlight=eltonw]("http://ubuntuforums.org/showthread.php?t=1483371&highlight=eltonw")

HTH
... with cordial greetings from Montreal (Quebec), Canada.):P

(as the Germans say: "Man findet immer ein Ausweg" ... there's always a solution!)

---

### Post by neu5eeCh on 2010-06-23
> **Jazzy_Jeff said:**
> So you are complaining that a computer specifically designed to work with windows will not work completely out of the box on Linux?? I know if I want one to work out of the box on Linux, I would buy one designed for, um, Linux maybe.

And now the trolls show up...

Without fail, in this forum, the trolls always show up.

Unfortunately, the instructions at the link are not proving helpful. If you want to be, um, helpful, let me know. Otherwise spare me your snark.

---

### Post by neu5eeCh on 2010-06-23
Hi Elton, thanks for the links. 

Though I still consider myself a beginner, I've been using Linux for a solid six months now. The information, as pertains to Linux, is stuff I already know.

Getting a wifi card is a good suggestion.

---

### Post by neu5eeCh on 2010-06-23
Hey, good news! I manually entered my wireless network. Then, on rebooting a third time, Ubuntu told me the network was available and asked me if I wanted to connect. Hell yes.

However, Ubuntu still doesn't seem to search for other networks (like my neighbor's). Any guidance? While I'm connected?

---

### Post by Penguin Guy on 2010-06-23
> **snowpine said:**
> To address your specific concern, Canonical can't legally include the Broadcom driver out-of-the-box. It is proprietary, closed-source software, and really your complaint should be to Broadcom for not releasing an open-source driver. :)
I can't get my head round the fact that Canonical are basically saying: "No, we're not including that on the CD - it's illegal. Feel free to download it from our repositories though.". There may be a real legal reason for this, in which case - please excuse my ignorance.

---

### Post by neu5eeCh on 2010-06-23
And it gets weirder, Penguin, because, as I've discovered, the drivers *are* on the CDs, so the legal argument must balance on a split hair. According to the links provided above, Canonical really wants you to download the drivers from their repositories **but**, if you don't have a connection, you can find them tucked away on your LiveCD. But they don't tell you that. The only way you can find that out is to, rolls eyes, connect to the Internet.

---

### Post by eltonw on 2010-06-23
> **VTPoet said:**
> Hi Elton, thanks for the links. 

Though I still consider myself a beginner, I've been using Linux for a solid six months now. The information, as pertains to Linux, is stuff I already know.

Getting a wifi card is a good suggestion.

I simply thought it might be of some help to you. 
BTW, installation of a newer kernel might also improve the performance.
Let's hope that when Maverick Meerkat (Ubuntu 10.10) comes out we won't have those connectivity headaches, which, IMVHO are of *primordial importance*. No matter what problems you may have, *_as long as you can connect_*, you can get help. 

Without that, it's the old 'Catch 22' situation.:lolflag:

---

### Post by snowpine on 2010-06-23
> **Penguin Guy said:**
> I can't get my head round the fact that Canonical are basically saying: "No, we're not including that on the CD - it's illegal. Feel free to download it from our repositories though.". There may be a real legal reason for this, in which case - please excuse my ignorance.

Every country of the world has different laws regarding intellectual property and software patents. Canonical's goal of "Linux for Human Beings" means they want Ubuntu to be freely and legally available everywhere. If a particular piece of code (Broadcom driver, mp3 codecs, Adobe Flash player, DVD decryption software, etc) is a gray area, then Canonical leaves the decision whether or not to use it up to the individual user, to comply with the laws and restrictions of his/her home country.

---

### Post by tgm4883 on 2010-06-23
Seriously, what model netbook do you have?

---

### Post by blur xc on 2010-06-23
> **tgm4883 said:**
> Seriously, what model netbook do you have?

Yeah, I'm curious as well.  My wife has a dell mini 10 on which I installed ubuntu nbr, and had the same issue.  I googled a bit and found that the drivers were on the live cd.  I navigated to the folder in nautilus, and double clicked the deb file.  It told me it needed some dependencies, so I just browsed for those files and installed them first.  It took like, uh, I dunno, maybe 5 or 10 mins?  It really wasn't a big deal...

And I was still a newb Ubuntu-er at the time as well.

Now getting the gma-500 graphics working- that's another story...  but there's a script for that now.  I'm still afraid of upgrading to 10.04 though...  It works- don't need to mess with it.  It's just a netbook for browsing the web, that's all it's used for...

BM

---

### Post by aysiu on 2010-06-23
> **snowpine said:**
> 
To address your specific concern, Canonical can't legally include the Broadcom driver out-of-the-box. So what has changed legally since Jaunty? In Ubuntu 9.04, my Broadcom 4312 on the HP Mini worked out of the box. Suddenly with Karmic and Lucid, I have to manually install the driver.

I also get a useless Hardware Drivers dialogue box telling me to activate the WL driver, but when I try to activate it, it says it can't download the driver.

Don't offer to activate something you can't activate.

More details here:
[Jockey can't fetch STA drivers for Broadcom](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/534824)

---

### Post by snowpine on 2010-06-23
> **aysiu said:**
> So what has changed legally since Jaunty? In Ubuntu 9.04, my Broadcom 4312 on the HP Mini worked out of the box. Suddenly with Karmic and Lucid, I have to manually install the driver.

I always wondered that, too. I wonder if Broadcom said something to Canonical. :)

---

### Post by blur xc on 2010-06-23
> **snowpine said:**
> I always wondered that, too. I wonder if Broadcom said something to Canonical. :)

What does broadcom has to lose by Canonical including the drivers in a default Ubuntu installation?  Don't they distribute their drivers for free on their website (for windows computers)?  Wouldn't this line of reasoning in the end, however little, just hurt broadcom's sales?

BM

---

### Post by Ibidem on 2010-06-23
Well, Broadcom cards have 3 (Linux native) drivers:
1. bcm43xx; worked well per my reading (?), but was removed in kernel 2.6.26
2. Proprietary "wl" driver; includes firmware.
3. Open "b43" driver; requires firmware, usually obtained from wl.
Distributing the "wl" firmware if  not using  wl appears to be restricted.

Recently, OpenFWWF has created functional free firmware.  This is not yet included (or even packaged) in Ubuntu, though build tools are available; Fedora has included it since Fedora 11 or 12, allowing Broadcom to work OOB.   Here's hoping that Maverick ships with OpenFWWF.

---

### Post by neu5eeCh on 2010-06-23
> **blur xc said:**
> Yeah, I'm curious as well.  My wife has a dell mini 10 on which I installed ubuntu nbr, and had the same issue.  I googled a bit and found that the drivers were on the live cd.

I googled too. *And* posted queries at more than one Ubuntu related forum. No answers were forthcoming. Suppose I didn't use the right search terms. But why should users have to play the google lottery? It would be one thing if I were using slackware, but Netbook Edition _targets_ Netbooks. My advice to Canonical would be to anticipate this problem and provide clear instructions from the get go.

---

### Post by snowpine on 2010-06-23
> **VTPoet said:**
> I googled too. *And* posted queries at more than one Ubuntu related forum. No answers were forthcoming. Suppose I didn't use the right search terms. But why should users have to play the google lottery? It would be one thing if I were using slackware, but Netbook Edition _targets_ Netbooks. My advice to Canonical would be to anticipate this problem and provide clear instructions from the get go.

Helpful tip: There is a lot of good AND bad Ubuntu advice all over the internet. Rather than play the "google lottery" add the search term "site:ubuntu.com" to your search string. This google search will give the official Ubuntu Broadcom instructions as its first hit:

```
site:ubuntu.com broadcom
```

That is how I found the link in post #2. :)

---

### Post by aysiu on 2010-06-23
> **snowpine said:**
> Helpful tip: There is a lot of good AND bad Ubuntu advice all over the internet. Rather than play the "google lottery" add the search term "site:ubuntu.com" to your search string. This google search will give the official Ubuntu Broadcom instructions as its first hit:

```
site:ubuntu.com broadcom
```

That is how I found the link in post #2. :)
The Jockey developers could also fix the bug so that Hardware Drivers fetches the drivers off the Ubuntu CD if an ethernet connection isn't found.

---

### Post by WinterRain on 2010-06-23
> **aysiu said:**
> The Jockey developers could also fix the bug so that Hardware Drivers fetches the drivers off the Ubuntu CD if an ethernet connection isn't found.

Shouldn't you be playing with your mac? ;)

---

### Post by neu5eeCh on 2010-06-23
> **snowpine said:**
> Helpful tip: There is a lot of good AND bad Ubuntu advice all over the internet. Rather than play the "google lottery" add the search term "site:ubuntu.com" to your search string. This google search will give the official Ubuntu Broadcom instructions as its first hit:

```
site:ubuntu.com broadcom
```That is how I found the link in post #2. :)

Now **that's** a _great_ tip! Thanks Snowpine.

**Edit:** And I also agree with Aysiu. Fixing the "bug" would be the best solution.

---

### Post by snowpine on 2010-06-23
> **aysiu said:**
> The Jockey developers could also fix the bug so that Hardware Drivers fetches the drivers off the Ubuntu CD if an ethernet connection isn't found.

Big +1. It's not so much that Broadcom doesn't work out-of-the-box in Ubuntu (it doesn't in a lot of other distros, either) but that jockey can't deliver on its promises. :)

---

### Post by tgm4883 on 2010-06-23
I can't find a HP mini without an ethernet port. Are you sure it isn't covered with a plastic cover? Mine is on the right side near the back.

---

### Post by Jazzy_Jeff on 2010-06-24
> **VTPoet said:**
> And now the trolls show up...

Without fail, in this forum, the trolls always show up.

Unfortunately, the instructions at the link are not proving helpful. If you want to be, um, helpful, let me know. Otherwise spare me your snark.

I state the obvious and I am a troll? ok. I did not know this was a help forum. I thought it was a testimonials forum.

---

### Post by za.zen on 2010-06-24
> **Jazzy_Jeff said:**
> So you are complaining that a computer specifically designed to work with windows will not work completely out of the box on Linux?? I know if I want one to work out of the box on Linux, I would buy one designed for, um, Linux maybe.

> **WinterRain said:**
> That's how people *should* think, but unfortunately the average person does not think that way. But I would expect more from an experienced linux person.

Posts like these aren't helpful.

---

### Post by Ibidem on 2010-06-24
> **snowpine said:**
> Big +1. It's not so much that Broadcom doesn't work out-of-the-box in Ubuntu (it doesn't in a lot of other distros, either) but that jockey can't deliver on its promises. :)

Fedora 12+ works OOB, if you didn't notice.  And apparently gNewSense, and the other "linux-libre" distros might.  See [http://www.ing.unibs.it/openfwwf/](http://www.ing.unibs.it/openfwwf/) for the software.
If you have a choice between having something that's ready to go and something that needs an internet connection to get it working, which is better?

Note that I prefer "function" over "freedom" (as in libre).  Others may differ.  But when you exclude freedom while not having function (Ubuntu's present setup), that's useless.

Of course, a bug is a bug.  So has one been filed for Jockey yet?
I'd guess that using local repos on CD would be simple.

Ibidem

---

### Post by snowpine on 2010-06-24
> **Ibidem said:**
> Fedora 12+ works OOB, if you didn't notice.  And apparently gNewSense, and the other "linux-libre" distros might.  See [http://www.ing.unibs.it/openfwwf/](http://www.ing.unibs.it/openfwwf/) for the software.
If you have a choice between having something that's ready to go and something that needs an internet connection to get it working, which is better?

Not on my computer, unfortunately. :( Openfwwf is cool, but doesn't support all cards (yet). Hopefully it is just a matter of time.

---

### Post by Ibidem on 2010-06-24
Here is one, marked "fixed": [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/462771](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/462771)
And another? [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/463153](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/463153)
And the package request: [https://bugs.launchpad.net/ubuntu/+bug/487393](https://bugs.launchpad.net/ubuntu/+bug/487393)

---

### Post by marshmallow1304 on 2010-06-24
Another tip for getting online packages without a connection: [Keryx]("http://keryxproject.org/").




> **za.zen said:**
> Posts like these aren't helpful.
And this one is?

---

### Post by Jazzy_Jeff on 2010-06-24
> **za.zen said:**
> Posts like these aren't helpful.

Again, this is not the help forum. If it was posted there then I would have tried to help.

---

