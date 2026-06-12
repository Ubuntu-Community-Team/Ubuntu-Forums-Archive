---
title: "Burned two linux mint discs for a newbie co-worker"
date: 2009-08-08
forum: Testimonials &amp; Experiences
---

### Post by wandalalakers on 2009-08-08
I'm scared to burn ubuntu or kubuntu for newbies because they won't know how to install flash, mp3, dvd support etc.  I thought about making a custom image for this co-worker.  I'll have to deal with video driver incompatability because I'm sure she will ask if her screen doesn't look right.

I was able to persuade a co-worker to try out Mint. I showed her a boot CD with Ubuntu 8.04 and a flash drive with LM 4 KDE. She was awed at what I could do without being logged into our work server. Surf the Internet, play games, openoffice, etc. She gave me three blank DVD+Rs. I burned "LM 5 KDE" and "LM 5" for her. I wish ubuntu and kubuntu came with the 3rd party plugins to make life easier for newbies.

I'm going to burn discs for two other co-workers next week.  I told them that I use linux at home instead of windows and they were intrigued.  I also told them that I use OpenOffice instead of Micro$oft Office because it's free.  They were more intrigued.

---

### Post by Tclarkie on 2009-08-08
lol, its like they haven't seen open source software before (its happened to me to)

---

### Post by .nedberg on 2009-08-08
> **pcdoctor said:**
> I wish ubuntu and kubuntu came with the 3rd party plugins to make life easier for newbies.

+1

I have also started to recommend Mint rather than K/Ubuntu, though I use Kubuntu. I allways explain the differences though, and tell them I can't help that much with Mint as it is a bit different (I know, it is not much different).

---

### Post by 3rdalbum on 2009-08-08
I don't recommend Mint to new users anymore - it can't be dist-upgraded to a new version.

I can't believe that you think Flash and MP3 support are difficult for new users to install! The first time Ubuntu runs into those formats, it asks the user if they want to install it, and then Ubuntu downloads and installs the necessary package.

DVD playback is something a new user would have to research (although I think it's actually in the Ubuntu help files) but Flash and MP3 are foolproof.

---

### Post by .nedberg on 2009-08-08
> **3rdalbum said:**
> it can't be dist-upgraded to a new version.



Hum, I didn't know that! Time to stop then I think... As I said, I don't use it.

It is not that flash and friends are hard, but I have seen some people do it the "Windows way". And that can involve some problems. apt-getting it is better, but not always what new users will do...

---

### Post by stalkingwolf on 2009-08-08
I used to keep a spare laptop with Ubuntu all tricked out as a loaner.

I would just let people borrow it or give it to customers while i was working on theirs.  then if they wanted to install i would install and set everything up, give them the introductry lessons and tell them to call if they had problems or questions.  Of Course i always bookmarked this site for them.

---

### Post by ugm6hr on 2009-08-08
I had to get my Ubuntu Mini 9 out to allow someone to show a .pptx presentation (the available laptop had Office 2003).

Only people there: 1 Mac user already aware of both OO.org and Ubuntu (but not particularly keen to leave the Apple bandwagon); 1 MS user very interested to know how long I've been on Linux.

Perhaps a couple of conversations to be had in the future... But I have never recommended Linux overtly to anyone other than family members (who I am prepared to personally support).

---

### Post by harry2006 on 2009-08-08
i would prefer recommending Ubuntu to Mint for newbies.

---

### Post by HappyFeet on 2009-08-08
I myself always hand out Linuxmint CD's. Having all codecs preinstalled is a blessing for the unwashed masses. But if they want *me* to install it, I install and set up Ubuntu for them.

---

### Post by javyn999 on 2009-08-08
Ya know there are plenty of web pages out there with a big long sudo apt-get install paragraph with all those codecs, flash players, and dvd support.  Why not just give her Ubuntu and a link to one of those.  Tell her to copy and paste the command into Terminal and wallah.

---

### Post by wandalalakers on 2009-08-08
> **3rdalbum said:**
> I don't recommend Mint to new users anymore - it can't be dist-upgraded to a new version.

I didn't know that either.  I always do a new install but I keep hearing horror stories about doing an upgrade instead of a new install with with *buntus.  I did stumble upon this:

[http://www.linuxmint.com/blog/?p=861](http://www.linuxmint.com/blog/?p=861)

Warnings:

    * This upgrade path is for the Main Edition only, from a Mint 6 Felicia to a Mint 7 Gloria system.
    * There is no guarantee that it will work for you. In fact this is quite a risky process. If you’re experienced and if you know how to troubleshoot and solve common Linux problems (in particular X11, kernel modules and APT problems) then you’re probably OK. If you’re a novice user we recommend you perform a fresh installation of Linux Mint 7 instead.
    * You should make backups of all your data before upgrading.

Upgrading graphically (easier):

    * Open a terminal and type the following commands: “apt update” and “apt install mintupgrader-felicia-main”
    * Open mintMenu and run “Menu->Administration->Upgrade to Linux Mint 7&#8243;
    * Follow the instructions. Choose the default options. Ignore errors (in particular GPG and gtk2-engines-aurora errors).

Upgrading from the command line (faster, safer):

Open a terminal and type the following commands:

    * gksu gedit /etc/apt/sources.list (Change all occurrences of “felicia” to “gloria”, and all occurences of “intrepid” to “jaunty” then save the file and close the editor)
    * apt update
    * apt remove mintassistant
    * apt install linuxmint-keyring
    * apt update
    * apt install mint-info-main (choose “Y” or “I” to install the package maintainer’s version)
    * apt install mint-meta-main(choose “Y” or “I” to install the package maintainer’s version)

In the terminal, repeat the following commands until both show no upgrades available:

    * apt upgrade
    * apt dist-upgrade

Then type the following commands:

    * apt install mint-meta-main
    * sudo rm -rf /boot/gfxmenu/default.message
    * sudo ln -s /boot/gfxmenu/linuxmint.message /boot/gfxmenu/default.message

Finally, open “Login Window” from the menu, click on the “Local” tab and choose the Arc-Wise theme. (If after rebooting you get an error about the theme at the login prompt, repeat this step.)

To get GDM to play the default Linux Mint sound, open “Login Window”, click on the “Accessibility” tab, and set the sound for “Login screen ready” to “/usr/share/sounds/linuxmint-gdm.wav”.

---

### Post by HappyFeet on 2009-08-08
> **javyn999 said:**
> Ya know there are plenty of web pages out there with a big long sudo apt-get install paragraph with all those codecs, flash players, and dvd support.  Why not just give her Ubuntu and a link to one of those.  Tell her to copy and paste the command into Terminal and wallah.

That's all well and good, but most people I know can barely be bothered to open their web browser, and type in youtube.com. Getting them to do anything else is next to impossible. If they want it installed, I will set up ubuntu for them. Giving them a Mint CD to try is more for testing purposes.

---

### Post by windows-killer on 2009-08-08
> **3rdalbum said:**
> I don't recommend Mint to new users anymore - it can't be dist-upgraded to a new version.

I can't believe that you think Flash and MP3 support are difficult for new users to install! The first time Ubuntu runs into those formats, it asks the user if they want to install it, and then Ubuntu downloads and installs the necessary package.

DVD playback is something a new user would have to research (although I think it's actually in the Ubuntu help files) but Flash and MP3 are foolproof.

it should be easier! 
for example, when you install ubuntu and when it boots for the first time, it should have an icon on the desktop named "extras" so that users would click it and it would auto-install the ubuntu restricted extras. How hard is this to implement?!

---

### Post by bobbob1016 on 2009-08-08
Why not roll your own with remastersys or whatever it is called.  Install the base ubuntu, install all codecs, flash, remove some fluff, and install firefox addons like adblock.  Then burn it to a disc.

---

### Post by XubuRoxMySox on 2009-08-08
> **bobbob1016 said:**
> Why not roll your own with remastersys or whatever it is called.  Install the base ubuntu, install all codecs, flash, remove some fluff, and install firefox addons like adblock.  Then burn it to a disc.

That's what I did and it was so cool! I created my own homebrew remix of minimal Ubuntu with LXDE (super-lightweight desktop, super-simple, clickable icons). It had OPenOffice, Firefox, Thunderbird, Skype, etc, and all the codecs and whatnot to play DVDs, edit videos and music, etc. My requirements were:

1.) It had to run fast and flawless on an old Dell that is shared between a lot of kids during the day,

2.) It had to have a "familiar" looking desktop with clickable icons for all the stuff the kids need to do (I simply re-named Firefox to "Browse the Web" and OpenOffice Writer to "Word processor," AlsoPlayer to "Music Box," etc.) so that anyone could use it even if all they've ever known is Windows or Mac, and

3.) It had to have all the codecs and stuff preinstalled so the kids could sync their ipods and mp3 players to it and print the cue sheets for the dance routines they're learning.

Once in a while one of the kids or a parent would comment on how fast and how completely simple the system was, and then I'd thank them and tell them it's "Robin's Custom Linux Remix."

I gave out a few CDs of it too (with Synaptic and a few extras added that weren't in my original) and actually "converted" a couple of dancers (and one dancer's entire family) from Windblows to Ubuntu!

The homebrew still has some buggy little sound issues though, off and on. In a dance studio that matters a lot! So I tried an LXDE multimedia distro called [PCLXDE]("http://www.pclinuxonline.com/?p=174"). It worked well on this old Dell but hardware issues kept popping up one after another. 

I can't wait for Lubuntu to arrive though. If it's free of the little "auto-mute" annoyance that persists in my homebrew remix, I'll be happy to switch. Until then for newbies with low-resource machines like mine and who need some multimedia stuff, I'm using a minimal Ubuntu + LXDE mixture for now.

---

### Post by tgalati4 on 2009-08-09
Distribution upgrades tend to break a lot of things anyway, so no loss in giving a minty disk to someone to try.

---

### Post by wandalalakers on 2009-08-09
> **bobbob1016 said:**
> Why not roll your own with remastersys or whatever it is called.  Install the base ubuntu, install all codecs, flash, remove some fluff, and install firefox addons like adblock.  Then burn it to a disc.

I actually gave her my custom LM KDE 5 and LM 5 discs that were created with Remastersys.  I also have a Xubuntu custom that I created using Remastersys.  Trust me, this user would ask me how to install flash.  I don't want to install the software for this user because I'm not getting paid for it.  I always fix relatives computers for free and I have installed two desktops for friends for free with Xubuntu.  If this friend that I gave the LM discs has any trouble, I'll refer her to the net.

---

### Post by 3rdalbum on 2009-08-09
> **windows-killer said:**
> it should be easier! 
for example, when you install ubuntu and when it boots for the first time, it should have an icon on the desktop named "extras" so that users would click it and it would auto-install the ubuntu restricted extras. How hard is this to implement?!

1. The idea behind the current codec installer system is that the user is educated about why the software isn't included, while still making it easy to install.

2. Ubuntu is meant to have a clean desktop by default, rather than being littered with desktop icons from the get-go.

---

### Post by 5zerocool on 2009-08-13
Newbs with Live CDs kind of scare me too. I don't want people to get mad at me if they wipe windows off of their machine and can't play their favorite game or watch dvds. I know that none of them have ever used a command line and they barely know how to get online.

---

### Post by XubuRoxMySox on 2009-08-13
Seriously I hate what Linux Mint has done with Firefox, but I really like the idea of the other stuff preinstalled to make the newbie experience as easy and trouble-free as possible.

If a newbie friend of mine doesn't like my clever little LXDE/Ubuntu remix, I would give him a Mint CD.

But I would encourage him to uninstall Firefox and Mint Update, then remove the Mint repositories (leaving only the Ubuntu and Medibuntu repos), then reinstall Firefox and Update Manager from the Ubuntu repos.

That's Mint without the Firefox bugaboo I dislike so much. That bugaboo in Mint Firefox - even if removed manually -  returns every time Firefox is updated, but with the update coming from Ubuntu repos instead of the Mint one, the bugaboo wouldn't be included.

You'd get all the Minty freshness and elegance, the preinstalled codecs and multimedia stuff, but none of the sneaky stuff in Firefox.

-Robin

---

### Post by tiga2001 on 2009-08-27
> **dixiedancer said:**
> Seriously I hate what Linux Mint has done with Firefox
-Robin

What kind of sneaky stuff are you talking about? I don't remember seeing anything weird in Linux Mint's firefox. But it's possible that I just missed it, because recently I've switched to Firefox 3.5 and I downloaded that straight from firefox.com . The reason I didn't get it from apt-get is because I'm still using Linux Mint 5 LTS for compatibility with some of my research code (mainly cmake and gcc/g++), and the repository from launchpad didn't have it in Spanish (which I am trying to learn).

---

### Post by XubuRoxMySox on 2009-08-27
> **tiga2001 said:**
> What kind of sneaky stuff are you talking about? I don't remember seeing anything weird in Linux Mint's firefox. 

Installed (or updated) from Mint's repositories, the Google search tool (up there in the upper right corner) is rigged up as a "Mint search" tool that *uses* Google (minus some of Google's extra features) and becomes an automated fund-raiser for the project. The vast majority of the money Mint makes is from that search tool - many times more than they bring in from donations and from the Mint start page combined, according to an entry a couple of months ago in Clem's blog.

If Ubuntu offered something like that, I would install it and use it to help Canonical advance Ubuntu. The reason I find it objectionable in Linux Mint is that it's "involuntary." There's a work-around of course (like installing it as you did from Mozilla rather than from the repositories), but the work-around they described in that blog is automatically undone if Firefox updates from the repos.

-Robin

---

### Post by Viva on 2009-08-27
If ubuntu used something like that, they wouldn't be able to use the "Mozilla Firefox" name and branding. Any modified versions of mozilla firefox should take explicit permission from the mozilla foundation to use their branding. I don't think mozilla will give permission if canonical are taking away their biggest income source.

---

### Post by tiga2001 on 2009-08-28
So how come Linux Mint gets to use custom search and also get the Firefox branding? Does that mean they went through negotiations with Mozilla to put their Google box in place of Mozilla's?

---

### Post by Viva on 2009-08-28
I'm not sure really, I haven't used mint for some time. If they did take the permission of the mozilla foundation, but I just can't see mozilla doing that when mint is taking away their primary revenue source. Maybe, mint is using their own branding for firefox?

---

