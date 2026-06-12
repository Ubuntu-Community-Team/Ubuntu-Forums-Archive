---
title: "By default, YouTube didn't work in Firefox, and it wasn't easy to fix"
date: 2014-10-20
forum: Ubuntu, Linux and OS Chat
---

### Post by sjeon on 2014-10-20
**OS & Software**
Ubuntu 14.04 LTS 64bit
Firefox 28.0

**Problem**
My first thought after booting Ubuntu Live USB was to bring up YouTube. Here's the mess that followed:
1. Click on Firefox, and go to YouTube
2. A kind of annoying but helpful-looking popup appears, telling me Flash needs to be installed
3. I do what the popup says and it gives me a screen where it says it's looking for flash
4. It fails, and can't actually install Flash.
5. Great.. Now what?
6. Google for how to get flash working on ubuntu
7. First link had me wasting a few minutes on a suggestion which did not actually work
8. Great.. Now what?
9. Okay, maybe the official Flash website
10. An Ubuntu option! Great! Click on the link and it gives me the dialog for choosing what to do with an apt link. No options available...
11. Great... Now what?
12. Googled again, found another search result which contained outdated and partially incorrect, but still helpful instructions which actually did end up working.
13. Okay! It was a long road (probably 15min of nonsense) but Flash is finally working now.

**How I got Flash working on Firefox 28.0 on Ubuntu 14.04 LTS 64-bit**
# On your left, click on System Settings > click Software & Updates > click checkbox: Software restricted by copyright or legal issues (multiverse)
# Type the following into Terminal:
sudo apt-get update
sudo apt-get install flashplugin-installer

**Thoughts**
+ I'd guess it's partially related to some kinda technical problem with copyright or legal issues, and partially other things
+ It makes both Firefox and Ubuntu look bad to show a dialog offering to Flash install and to not actually deliver on that
+ There seems to be more than one sequence of operations for installing flash on ubuntu, and that was confusing and decentralized, with multiple sources saying multiple different things.

---

### Post by sjeon on 2014-10-20
I just realized this is incorrectly posted to the Hardware section, but I do not appear to be able to delete it or switch it to the proper section.

---

### Post by deadflowr on 2014-10-20
Not support
Moved to Ubuntu,Linux and OS Chat

---

### Post by craig10x on 2014-10-20
Ubuntu Restricted Extras (in the software center) is what installs all the various codecs (including flash)...once installed, everything should work ok...
Adobe Flash is no longer supported in linux, so a rather old version of flash will be installed...An advantage of Google Chrome (which you can get by downloading the deb file from their website and right clicking the file and have it open in the software center which will install it) is they have up to date flash for linux because they have an agreement with adobe and can offer the latest flash in Chrome (including the linux version)...,

Although, in the case of You Tube, they use HTML-5 now so i am surprised that it didn't work on their site even without flash installed...Most other sites still use flash for video, so for linux Chrome has a big advantage since it gives you the latest version...

---

### Post by Bucky Ball on 2014-10-21
You say you are booting from a LiveCD. Not much point installing flashplayer or anything else. Installing flash in Ubuntu is easy (just install flashplugin-installer or go the way you went). If you want to install flash, video drivers, wireless drivers, etc., permanently install Ubuntu to the hard drive. 

Even if you do manage to install drivers or anything else they will be gone on the next reboot. Anything you do install will be saved to RAM (as the install disk is read-only and you're not using a hard drive install) and wiped the moment you restart.

---

### Post by exodus3 on 2014-10-21
posting here so i can find this thread later, since i am going to be installing ubuntu soon and will most likely have more grief then OP if i can't find this thread later on 

thanks

---

### Post by Bucky Ball on 2014-10-21
@exodus3: The OP appears to be using a LiveDVD/USB boot so can't see how this thread will be of much help. Also, this is a non-support area of the forums.

Suggest you post your own thread in ***Installations & Upgrades***, which is a support area, if you have any issues installing. There is a lot of info re. installing Ubuntu out there so have a look around first, and not just on these forums. Good luck. ;)

---

### Post by sjeon on 2014-10-21
> **craig10x said:**
> Ubuntu Restricted Extras (in the software center) is what installs all the various codecs (including flash)...once installed, everything should work ok...
Adobe Flash is no longer supported in linux, so a rather old version of flash will be installed...An advantage of Google Chrome (which you can get by downloading the deb file from their website and right clicking the file and have it open in the software center which will install it) is they have up to date flash for linux because they have an agreement with adobe and can offer the latest flash in Chrome (including the linux version)...,

Although, in the case of You Tube, they use HTML-5 now so i am surprised that it didn't work on their site even without flash installed...Most other sites still use flash for video, so for linux Chrome has a big advantage since it gives you the latest version...

Screenshot: [http://i.imgur.com/yjaFRS5.jpg](http://i.imgur.com/yjaFRS5.jpg)
YouTube seems to use a mix of Flash and HTML5 at this point.

I think if it's possible to make Flash function in the default web browser packaged with the Ubuntu Live USB environment then it's a worthy objective. If that means Firefox needs to be replaced by Chromium as the default browser: So be it. In the windows world, a whole lot of people are used to and switched en masse from firefox to chrome. I want Firefox to be the superior browser, but in this case it verifiably and absolutely is failing to do what I expect it to do, and by extension, so is Ubuntu.

---

### Post by sjeon on 2014-10-21
> **Bucky Ball said:**
> You say you are booting from a LiveCD. Not much point installing flashplayer or anything else. Installing flash in Ubuntu is easy (just install flashplugin-installer or go the way you went). If you want to install flash, video drivers, wireless drivers, etc., permanently install Ubuntu to the hard drive. 

Even if you do manage to install drivers or anything else they will be gone on the next reboot. Anything you do install will be saved to RAM (as the install disk is read-only and you're not using a hard drive install) and wiped the moment you restart.

What I believe:
YouTube should work by default, or as close as possible to default, on the Ubuntu Live USB environent. If that means we need to abandon Firefox in favor of Chrome or Chromium (Didn't most of us already do that?) then so be it. If that means somebody needs to say "Hey Firefox. You're screwing up the Ubuntu user experience." then so be it. Why make Ubuntu default browser just a needless extra step on the way to installing Chrome or Chromium? Why require newbs to google for weird, obscure information in order to to basic things like go to YouTube? I do want Firefox to be good enough, but right now it's not.

---

### Post by mastablasta on 2014-10-21
> **exodus3 said:**
> posting here so i can find this thread later, since i am going to be installing ubuntu soon and will most likely have more grief then OP if i can't find this thread later on 

On install you just tick the box to install the extras.

> **sjeon said:**
> **OS & Software**

+ There seems to be more than one sequence of operations for installing flash on ubuntu, and that was confusing and decentralized, with multiple sources saying multiple different things.

problem? read the manual first rather than doing searches in Google which were likely more tailored to your past experience than to what you are looking for (yeah google search is really bad lately not just for linux!!)

How do we install software in Ubuntu? Open software center, search for the desired software, select it and click install. was that too hard?

yes there is more than one way to install programs in Linux. what you did was the same as opening software.... only someone told you what the package was and you skipped the search part and just put in the install command. This command is there so people can install things on server which doesn't have any GUI. or so you can do scripts more easily. or you can remotely connect to you desktop with a much  weaker PC or Smart Phone and install things on it. etc...

but my point is read first how things are done. if you don't understand something, then ask. 

internet is full of bad advice just as it has many good advice. but how would someone with no prior knowledge (not even "user manual knowledge") know which advice is good and which one is not? you just picked the first one provided by Google (=put your faith in Google's hands) and just ran the commands you saw or at least the ones that didn't seem too complicated.

---

### Post by sjeon on 2014-10-21
Ubuntu 14.04 LTS 64bit
Firefox 28.0
[COLOR=#303942][FONT=Ubuntu]Chomium 37.0.2062.120[/FONT][/COLOR]

Screenshots of how it all happened:
[http://imgur.com/a/quqg4](http://imgur.com/a/quqg4)

1. Went to a random youtube video and noticed it says it required flash. Clicked to install flash

2. Was brought to the official site, which seems like it ought to work. Pleasantly surprised that it automatically detects the browser and offers an "Ubuntu 10.04+" option. Click on Download and it makes sense that it'll work now.

3. Ubuntu software center says "Not found"

You can tell me to follow a series of technical instructions, but stop for a moment and think about this:
Ubuntu's version of firefox tells me it can install Flash, but it can't.
Ubuntu's version of chromium tells me it can install Flash, but it can't.
Ubuntu's version of Google Chrome includes Flash with it <-- _It just works._
Firefox on Ubuntu is kind of looking to me like IE on Windows: Just an obstacle in the way to everybody installing Chrome.

We can do better than this.
Ubuntu's default browser should be able to play YouTube and Flash by default or as close as possible to default, and it shouldn't tell me it can install Flash when it can't.

Boot up the 64bit 14.04 Live USB. Flash doesn't work, and it should. The flash install prompt when you go to youtube.com in Firefox and Chromium: That doesn't work either. Bones are broken, people. Don't just tell me to apply a band-aid.

---

### Post by vasa1 on 2014-10-21
> **sjeon said:**
> ...
Ubuntu's version of firefox tells me it can install Flash, but it can't.
Ubuntu's version of chromium tells me it can install Flash, but it can't.
...
Did you install restricted extras?

---

### Post by coffeecat on 2014-10-21
Since this is really the same issue as your Firefox thread, I’ve merged the two.

A few points:

[quote=sjeon]You have excuses, but they're not good enough.
These major browsers for Ubuntu (Including the default browser packaged with the OS) are telling me they can help me with instaling flash, but they're lying to me. They fail to actually install Flash.

So make your excuses, but the truth is that I wouldn't be here bothering you right now if Ubuntu's default browser could just go to youtube, ask me to install flash, actually do it, and then just let me watch youtube videos to test out Ubuntu instead of proving that Ubuntu has failed this test. [/quote]

[list][*]This is a forum of volunteer members, mostly ordinary users such as yourself, staff included. Please stop abusing forum members for things that are out of their control.
[*]Instead of complaining about things that cannot be changed – flash cannot be included in a default Ubuntu installation for licensing and **legal** reasons – please listen to the good advice that you are  being given. Getting flash to work in both chromium and Firefox is trivially easy.
[*]Chrome includes its own flash player but it is a proprietary browser and is not in the Ubuntu repositories for the same reason as above. Comparing the default chrome and chromium experience is misinformed.[/list]

By the way, to get flash working in chromium, you can install the pepperflashplugin-nonfree package which is in the Ubuntu (Universe) repository.

---

### Post by sjeon on 2014-10-21
abobe-flashplugin is not possible to install by default. you have to google around to instructions which tell you how to mod your repos and update the app cache via the scary black and white screen and then go type in some other things to the scary black and white screen so that then you go to youtube.

no one should have to google around to try to figure out how to get youtube working on ubuntu. it should just work.

---

### Post by sjeon on 2014-10-21
> **coffeecat said:**
> Since this is really the same issue as your Firefox thread, I&#8217;ve merged the two.

A few points:



[LIST]
[*]This is a forum of volunteer members, mostly ordinary users such as yourself, staff included. Please stop abusing forum members for things that are out of their control. 
[*]Instead of complaining about things that cannot be changed &#8211; flash cannot be included in a default Ubuntu installation for licensing and **legal** reasons &#8211; please listen to the good advice that you are  being given. Getting flash to work in both chromium and Firefox is trivially easy. 
[*]Chrome includes its own flash player but it is a proprietary browser and is not in the Ubuntu repositories for the same reason as above. Comparing the default chrome and chromium experience is misinformed. 
[/LIST]

By the way, to get flash working in chromium, you can install the pepperflashplugin-nonfree package which is in the Ubuntu (Universe) repository.

You're right. I'm being a jerk. I'm sorry.
I just think these instructions, while 100% valid, should not be required at all.
YouTube is one of those things that should require no Terminal commands and no obscure settings mods. It should all be very simple clicks of Yes and Next and then it should work. It's built to work like that, but it's not actually operating properly, so it's like a guy coming up on to me to the street, saying he'll sell me ice cream, I say "uh sure" and he just takes the money and says "Ice cream not found." Not cool. And then I come to you guys, and you're saying something kind of like "oh, making ice cream is easy. sugar, eggs, milk." None of this should be like this. YouTube should just work after a couple clicks of Yes and Next.

---

### Post by mastablasta on 2014-10-21
> **sjeon said:**
> 
You can tell me to follow a series of technical instructions, but stop for a moment and think about this:
Ubuntu's version of firefox tells me it can install Flash, but it can't.
.

I have a feeling that the message you see on that screenshot is from AdobeFlash (or Youtube) not from Firefox. Or from Ubuntu. See below...

> **sjeon said:**
> abobe-flashplugin is not possible to install by default. you have to google around to instructions which tell you how to mod your repos and update the app cache via the scary black and white screen and then go type in some other things to the scary black and white screen so that then you go to youtube.

 no one should have to google around to try to figure out how to get youtube working on ubuntu. it should just work.

it should just work. it is Adobe's product/software. so Adobe should comment on why it doesn't just work. or why clicking on the link doesn't install the program or at least offer to install it.

solution was made in Ubuntu where during system install user can tick a box that would install flash and other similar software that can not be included in LiveCD. I can't think of a better way.

I believe it is same with Windows - nothing like Flash or Codecs is included in their "liveCD"/install media. unless they reached some deal to distribute such stuff lately.

Note that Linux Mint does include such software (even in live CD)  as they operate from a country that has a different legal system regarding software patents.

---

### Post by Mike_Walsh on 2014-10-21
> **sjeon said:**
> You're right. I'm being a jerk. I'm sorry.
I just think these instructions, while 100% valid, should not be required at all.
YouTube is one of those things that should require no Terminal commands and no obscure settings mods. It should all be very simple clicks of Yes and Next and then it should work. It's built to work like that, but it's not actually operating properly, so it's like a guy coming up on to me to the street, saying he'll sell me ice cream, I say "uh sure" and he just takes the money and says "Ice cream not found." Not cool. And then I come to you guys, and you're saying something kind of like "oh, making ice cream is easy. sugar, eggs, milk." None of this should be like this. YouTube should just work after a couple clicks of Yes and Next.

Did you not read what coffeecat told you, a couple of posts back? It's NOT that Ubuntu don't WANT to make it easy for folk to use Flash, and to be able to watch YouTube (though personally, I can think of MANY things I'd RATHER spend my time doing than watching YouTube, but....I digress); the fact of the matter is that Canonical are not allowed to include FlashPlayer with their different 'Buntu releases, simply because it contravenes various legal & copyright accommodations that have long since been put in place with the media industry, to protect them from folk like you & me getting the content without recompensing the artists for their hard work. And also because Adobe, as has been stated, have stopped supporting the Linux version of FlashPlayer.

Google, on the other hand, have vast amounts of money to wave around under people's noses.....which is probably why they have the arrangement that they do with Adobe, to always have the most up-to-date version of FlashPlayer installed....but ONLY in Chrome, which is the branded version of the browser. Chromium, which Chrome is based on, is deemed to be open-source, so it suffers the same problems that a lot of other open-source software does,i.e., manufacturers refusing to play ball because there's nothing in it for them.

I admit, I don't understand the legal reasons WHY Canonical are allowed to offer FlashPlayer as a post-install 'add-on' for FireFox (I'm not a lawyer!), but that is just how it has been for several years now.

I hope you understand, too, and appreciate, the fact that the majority of open-source software is developed by people who most certainly do not make a living wage out of what they do; for many, they do it out of sheer enthusiasm.....so if they DO ask for occasional small donations, I, for one, do not think that is 'out-of-the-way', and am quite happy to make occasional, small contributions.

Regards,

Mike.

---

### Post by buzzingrobot on 2014-10-21
Flash is not installed by default.  Hence, it is not available in a Live mode session.  (I've been successful installing some packages into a Live mode, but have not tried to install Flash.)

When doing a actual physical installation, the installer offers on option to include certain proprietary tools, codecs, etc.  Those include Flash. It's also in the ubuntu-restricted-extras package, or via the flashplugin-installer package.

Firefox's unhelpful prompt to install Flash is a relic and something of a Windows-esque thing. We are likely stuck with it until Mozilla decides to remove it from its Linux builds. Ignoring it and installing Flash as described above is the way to go.

The only Flash-on-Linux that is getting *feature* updates is the version of Flash that is installed with Google Chrome. Adobe continues to provide *security* updates for  non-Chrome Flash for Linux, and those updates are quickly pushed out via the usual Ubuntu channels.  AKA, just run your normal updates and you will get the Flash updates.

---

### Post by craig10x on 2014-10-21
@buzzingrobot: You definitely can install ubuntu restricted extras (or just flash alone) from the software center on live session ubuntu...i have done it frequently...of course, it only works for the session...once you re-boot of course you lose any changes you made...

As was pointed out, to make it easier for newbies, when you actually INSTALL ubuntu, it gives you the option to check a box where it will install the restricted extras during the install, rather then waiting until after the install is completed...Since i know (as an old time ubuntu user) about restricted extras, i install them AFTERWARD myself but that is just my personal choice ;)

And as was mentioned, Ubuntu isn't permitted to install the codecs and flash by default because of licensing restrictions...but does offer you the ability to install it yourself...
I believe the reason is that Canonical could be sued where as YOU personally of course are not going to be, so you can install at your own responsibility... :D

Google Chrome (from Chrome itself not Chromium) is my favorite browser, so i always install it...and thanks to their agreement with adobe, i have up to date flash...but i still install restricted extras of course, to get all the codecs and to have a working flash (albeit old) when i ocassionally use Firefox...

---

### Post by cariboo on 2014-10-21
I really dislike the Software Centre, I use Synaptic Package Manager, to install most software packages. It's pretty easy to search for what you need. Once installed just type what you think you need, in this case flash, and it usually comes up with the right package. See the screenshot.

---

### Post by Ko_Char on 2014-10-21
Flash can't be easily installed in Live session because only main and restricted repos are enabled by default on Live session. 
Flash is in the multiverse repos (software restricted by copyright or legal issues)

But if you installed it on a local hard drive/virtual machine, the problem is gone because multiverse repos is enabled by default. 

I think it makes sense to only enable main and restricted repos for live session. Most people use live session for testing, installation, recovery. Only a few will use it to watch Youtube. And the size of USB is pretty limited. It could be just 2 GB. It is undesirable to download a lot of packages in USB session, which will just fill the USB and hang the whole Ubuntu.

---

### Post by craig10x on 2014-10-22
I have installed ubuntu restricted extras MANY times when running a live session...the ubuntu software center refreshes itself once you click on that package and adds multiverse repo and then gives you thhe option to click on and install it...I have also added a number of programs too...including installing google chrome!  But these were done running a live session dvd iso...i have never run a live session usb, but i don't see why that should be any different...perhaps it is???

It is true that multiverse is added automatically once you actually install...that i know from experience...

---

### Post by exodus3 on 2014-10-28
just an update .when i installed ubuntu 14 lts i did click the 3rd party support option .after the install i ran into a "need java driver"  dialog box   it would open a search box and search forever  and ever  never finding anything   so i opened the software center and typed "java" in the search ..the 1st install option in the results solved the problem for me

---

