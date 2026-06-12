---
title: "need a os suggestion"
date: 2010-10-01
forum: The Cafe
---

### Post by northwestuntu on 2010-10-01
anyone suggest a solid fast os?  all i use is the browser most the time so i don't need anything with bells and whistles all over bogging down the machine.  only other thing is a good default file manager and a os that is up to date on security issues.  

currently using lubuntu and that's fast, but a little buggy and i don't like pcman file manager that much.

i should mention im not a advanced linux user so looking for something ready out of the box.

thanks

---

### Post by Dustin2128 on 2010-10-01
arch or gentoo are my top two for a light OS. 

Yet, NWF still insists that every single linux distro is exactly the same :D

---

### Post by sikander3786 on 2010-10-01
Ubuntu default installation has been pretty fast for me. What are your system specs? Do you really need a light weight OS?

What about Chromium OS?

[http://www.chromium.org/chromium-os](http://www.chromium.org/chromium-os)

I am going to install it this weekend. I have heard that it is also a light weight and fast OS. Don't know if it supports my hardware. Need to do a bit of research on that.

What I have found uptil now is that you need an Ubuntu install, 8.04 or higher to compile it. Thats what is forcing me to try it :-) Google likes Ubuntu! Goobuntu!

---

### Post by Tibuda on 2010-10-01
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by northwestuntu on 2010-10-01
> **sikander3786 said:**
> Ubuntu default installation has been pretty fast for me. What are your system specs? Do you really need a light weight OS?

What about Chromium OS?

[http://www.chromium.org/chromium-os](http://www.chromium.org/chromium-os)

I am going to install it this weekend. I have heard that it is also a light weight and fast OS. Don't know if it supports my hardware. Need to do a bit of research on that.

What I have found uptil now is that you need an Ubuntu install, 8.04 or higher to compile it. Thats what is forcing me to try it :-) Google likes Ubuntu! Goobuntu!

i have a amd 3800 dual core with 4 gigs of ram.  so it's a little bit older hardware.  i do like having a faster system though.  lubuntu is very fast compared to ubuntu.  i didn't think chrome os was built for desktops?

---

### Post by northwestuntu on 2010-10-01
> **Dustin2128 said:**
> arch or gentoo are my top two for a light OS. 

Yet, NWF still insists that every single linux distro is exactly the same :D

i have looked at those distros before, but seems like you need to be more of a advanced linux user to set those up.

---

### Post by northwestuntu on 2010-10-01
> **Tibuda said:**
> [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

i did use crunchbang for about 4 months, but the development seems kinda slow and thought they were moving away from ubuntu based.

---

### Post by sikander3786 on 2010-10-01
> i didn't think chrome os was built for desktops?

It wasn't and it isn't, still I am crazy to try it out. I'll let you know if it works.

Regarding your hardware, Lucid boots in 18-20 sec on one of my AMD 3800+ with 2 GB or memory. It is always responisve. Firefox is up in 3-5 sec on a cold start. You have got a pretty better hardware than that. You use only browser, how fast you want it to be?

---

### Post by Spice Weasel on 2010-10-01
Tiny Core.

1. Install browser.
2. Install rox-filer/thunar/pcmanfm/mc/etc.
3. Done. 16MB RAM usage and near instant boot.

---

### Post by Tibuda on 2010-10-01
> **northwestuntu said:**
> i did use crunchbang for about 4 months, but the development seems kinda slow and thought they were moving away from ubuntu based.

Yes, they are moving to a Debian base, but the development is not slow. And it is a very solid distro, and with a Debian squeeze base, the apps are updated as they are released, unlike Ubuntu.

Most of the "development" of a Ubuntu-based distro is to adapt the distro to every new release. This was one of the reasons behind of the move to Debian. And some issues with karmic.

---

### Post by northwestuntu on 2010-10-01
> **sikander3786 said:**
> It wasn't and it isn't, still I am crazy to try it out. I'll let you know if it works.

Regarding your hardware, Lucid boots in 18-20 sec on one of my AMD 3800+ with 2 GB or memory. It is always responisve. Firefox is up in 3-5 sec on a cold start. You have got a pretty better hardware than that. You use only browser, how fast you want it to be?

i would like to know if it does work. although i wonder how well it would work.  don't know i would want to make that my default os.

im not really concerned about boot time.  when i talk about speed im talking about opening and closing programs and files.  ubuntu isn't super slow or anything, but if compared to lubuntu it is.  i open my browser in lubuntu and it's almost instant and in ubuntu it kinda takes a little bit.  i just see no reasons why anyone wouldn't want a more responsive system?

---

### Post by Dustin2128 on 2010-10-01
SliTaz maybe? Or slackware if you're not compilaphobic.

---

### Post by northwestuntu on 2010-10-01
> **Dustin2128 said:**
> SliTaz maybe? Or slackware if you're not compilaphobic.

i did a quick search of that. i never heard of that before.  it seems like puppy linux doesn't it?  runs of your memory, but so does that mean you have to always have a usb drive connected i can't install to HD?

---

### Post by gutterslob on 2010-10-01
If you want an 'out of the box' type, go with Slitaz. Boots and runs extremely fast (faster than it takes a fanboy to say 'Arch', in fact) It does come with PCmanFM, but you could easily remove that and replace with something like Thunar. Puppy is another decent option (you said you don't need bells and whistles, right?). Heard good things about TinyCore, but I don't have any experience with it.

If you insist on a distro the comes with a full desktop environment (as opposed to a window manager), the Xfce version of Aptosid (formerly sidux) is a good choice. Pretty fast, comes with the familiar APT (since it's based on Debian) and has a decent selection of included apps. Only downside (or upside, depending on your point of view) is that it's based on Debian's Unstable Branch (Sid), so you have to be careful with your updates (similar to Arch in that sense). 

CrunchBang is pretty decent as well, and the new Statler Alpha version is based on Debian. There's both a Xfce and an Openbox version. The community is one of the nicest on the internet, I have to say.

If you're willing to spend the time setting up something from scratch, you could always do a minimal Debian, Crux or Arch install and just add the apps/libs/resources you need. Heck, even a minimal Ubuntu might prove light enough, depending on your hardware. 

Terminal apps are the way to go if you're after utmost lightness. I'm not saying you should browse with E-Links (appealing, but not too practical for flash and stuff), but you could consider ncurses alternatives for stuff like audio players, newsfeed readers, irc/chat clients, file management...etc.

---

### Post by cchhrriiss121212 on 2010-10-01
Go for crunchbang stalter + chrome/chromium, you won't get many setups faster or more stable than that. As already mentioned, crunchbang development is by no means slow, I've used it daily with no issues since alpha 1.

---

### Post by slooksterpsv on 2010-10-01
> **northwestuntu said:**
> i have a amd 3800 dual core with 4 gigs of ram.  so it's a little bit older hardware.  i do like having a faster system though.  lubuntu is very fast compared to ubuntu.  i didn't think chrome os was built for desktops?

You could do Xubuntu and install LXDE. That way it's light, still Ubuntu based so security is good, etc. I mean your hardware is still amazing. I'm running Ubuntu 10.04 on a quad core with 2gb of ram and it's fast for me. - Running anything like Siltaz is like saying the computer is 10 years old, which it certainly is not.

So I'm installing LXDE right now to see how it incorporates if I want to switch to that WM on my system, I'll let you know the results.

EDIT: Holy crap that was fast to log in. Wow I kind of like this... hehe I may have to use LXDE, it's that nice on Ubuntu (Not Lubuntu).

I'm going to use this for a few days (although it killed my compositioning)

---

### Post by gutterslob on 2010-10-01
> **northwestuntu said:**
> i did a quick search of that. i never heard of that before.  it seems like puppy linux doesn't it?  runs of your memory, but so does that mean you have to always have a usb drive connected i can't install to HD? No, you can easily install it to your HDD. 

It's pretty straightforward, just check the documentation.
[http://doc.slitaz.org/en:handbook:installation](http://doc.slitaz.org/en:handbook:installation)

My desktop's pretty fast, but I still have a Slitaz partition on it. I like the idea of pressing the power button and getting to work straight away (Slitaz probably conquered 10sec boot long before most 'big repo' distros even thought of it)

---

### Post by Dustin2128 on 2010-10-01
> **northwestuntu said:**
> i did a quick search of that. i never heard of that before.  it seems like puppy linux doesn't it?  runs of your memory, but so does that mean you have to always have a usb drive connected i can't install to HD?
[http://www.slitaz.org/en/doc/handbook/install.html](http://www.slitaz.org/en/doc/handbook/install.html)

---

### Post by northwestuntu on 2010-10-01
thanks for the ideas everyone.  i'll check in to a lot of these suggestions to see if they fit what im looking for.

---

### Post by Dragynn on 2010-10-01
As to some of the other recs here:

SliTaz rocks, best tiny distro there is IMO, heard of it from one of the mods here. It does come with an HD installing option which I have used a couple times, works like a charm, only uses about 30 megs of RAM at idle on an HD install, around 140 if you run in ram (runs like a charm on 256 mb's of ram, great for resurrecting old machines), plenty of packages in their repo, the Xvesa 3.0 version will boot on anything ever made pretty much. It comes with only Midori broswer, so you will have to load FF from repo.

Puppy linux is seriously awesome in many ways, and there are literally dozens of "puplets" (user-made versions) that are purpose built for one thing or another. It's very stable, the only gripe I have is that the main official version (currently 5.1.1) has toooooo much software built in, that may be a plus for a lot of folks. The current version is actually based off Ubuntu themes, and can use Ubuntu's repo's for software. So Puppy probably has one of the largest potential software bases of any distro out there. There is a version called "BrowserLinux" that might be what you are looking for, I use a version that I have cut a lot of the software out of, and added Iron 5.0.381 as the browser, and I swear it is the fastest OS/browser combo I have ever seen or used. If you have enough ram, try this out, works fine with a gig, if you got more, you NEED to try this out. I like 5.1.1 Lucid Puppy, Turbodog Xtreme (a seriously cut-down no frills version, fast as lightning), and Browserlinux. 

I'm currently running Gnome Zen Mini, a mini version of PCLinuxOS that comes with all the infrastructure and almost no programs loaded, a roll-yer-own type of distro, comes with FireFox and a text editor and that's about it, you add the rest as you see fit. I find it to be fast, trouble-free, stable, well-mannered, nice looking, user-friendly, and solid. I have done a hard install of it, but you can run it in ram if you have enough, that will be my next experiment on my newest machine.

Good Luck!

---

### Post by Dustin2128 on 2010-10-01
> **Dragynn said:**
> As to some of the other recs here:

SliTaz rocks, best tiny distro there is IMO
agreed.
It's amazing how much software they can pack into a disc smaller than damn small linux, while still using 2.6 instead of 2.4 kernel.

---

### Post by TBABill on 2010-10-01
Since Mint won't be faster than Ubuntu/Lubuntu, the fastest AND easiest combination I have found is PCLinuxOS 2010.7. Even in KDE it is just super fast. And it's the only distro I have found to support a Broadcom wireless device out of the box (without having to download anything). It's simplistic to the point that you update just like in Lubuntu. Click reload in synaptic, mark all upgrades, click apply and enjoy. And the fact that it uses Synaptic keeps it familiar. It comes in LXDE, KDE, Gnome, Xfce, E17 and probably others. Install all the different environments and select which to boot into at the login screen.

EDIT: Currently only comes in 32 bit, but faster than any 32 or 64 bit distro I have used. On par with the speed of Lubuntu and Peppermint but with a lot more functionality because of the other desktop environment choices.

---

### Post by NightwishFan on 2010-10-01
I was saying that you are most likely to a 1% increase in performance using something like Gentoo over Debian. The up-to-date Squeeze seems to be around equal to Ubuntu.

[LIST]
[*]Though for something small or light, I have never used, but hear good things about Mint.
[*]You could also try Xubuntu, which has always been nice. The upcoming Maverick release is targeting a lot of minimal apps.
[*]Puppy is amazing, moving on.
[*]Regular Debian may be up your alley as it does not require Pulseaudio as much as Ubuntu does with Gnome.
[*]Install a command line only Ubuntu from the alternate CD, and build your own custom machine. I like fluxbox, perhaps that using XFCE's thunar file manager and Midori or Firefox as the browser.
[/LIST]

---

### Post by drawkcab on 2010-10-02
If PCman is bringing you down, just replace it with Thunar.  

I personally prefer lxde to openbox and, if PCman is bothering you my guess is that you would dislike openbox.  (no disrespect to crunchbang which is a great little distro)  

Maybe you would like to try peppermint linux?  It's another ubuntu-based distro that features a nicer-looking/functioning lxde desktop.  Again, install Thunar and you're off to the races.

But, as others have pointed out, there are a lot of options if you want a quick os that runs lxde.  Some of us just feel at home on Debian/Ubuntu.

---

### Post by snowpine on 2010-10-02
> **northwestuntu said:**
> anyone suggest a solid fast os?  all i use is the browser most the time so i don't need anything with bells and whistles all over bogging down the machine.

Browser Linux:

[http://browserlinux.com](http://browserlinux.com)

---

### Post by armageddon08 on 2010-10-02
I think SliTaz is the fastest distro out there. But if you want large repositories..I think you'll be better off with Crunchbang, Mint LXDE or Archbang.

---

### Post by Plumtreed on 2010-10-02
I'm surprised that Peppermint ICE hasn't been suggested...Designed to be used in association with Cloud applications it is very lightweight yet versitile.

Google PeppermintOS to read about Peppermint One and Peppermint ICE......and link to a good, helpful forum!

---

### Post by Warpnow on 2010-10-02
Using Slitaz right now. Its really nice.

---

### Post by northwestuntu on 2010-10-03
now im thinking of just going back to ubuntu?  i know my dual core can run it ok although i do enjoy the speed of lighter distros.  does anyone here have a at least a dual core and still runs a light distro or they only run a light distro with old computer?

---

### Post by Dr. C on 2010-10-03
One suggestion to speed up Firefox is to install the [Better Privacy]("https://addons.mozilla.org/en-US/firefox/addon/6623/") extension to get rid of Local Shared Objects (LSOs) or "Flash Cookies". I have seen a marked improvement in browsing performance when 200 - 300 of these things are removed.

By the way Ubuntu 10.04 runs great for browsing on a Pentium 4M 1.8 GHZ with 1GB of ram once the LSOs are gone.

---

### Post by NightwishFan on 2010-10-03
Can these flash cookies be removed with Bleach Bit?

Also, I generally just disable flash until I want to watch something, then when I am done disable it again. (You can do so in FF via Tools -> Addons -> Plugins)

---

### Post by Dr. C on 2010-10-04
> **NightwishFan said:**
> Can these flash cookies be removed with Bleach Bit?

Also, I generally just disable flash until I want to watch something, then when I am done disable it again. (You can do so in FF via Tools -> Addons -> Plugins)

Yes that is another option. They hide in /home/*<user>*/.macromedia so one can just delete them also.

---

### Post by Khakilang on 2010-10-04
> **northwestuntu said:**
> now im thinking of just going back to ubuntu?  i know my dual core can run it ok although i do enjoy the speed of lighter distros.  does anyone here have a at least a dual core and still runs a light distro or they only run a light distro with old computer?

I have an Intel Dual Core 1.8Ghz with 1.5Gb RAM and nVidia 7200GS graphics card and I am running Ubuntu 10.04 just fine. Boot time take less than 20 sec and I am happy with it. I have tested SliTaz on an older computer. Pentium 4 1.5GHz with 512MB RAM, S3 graphics card and a 20GB hard disk. To my surprise its run very fast but unfortunately it doesn't have my USB wifi adapter which is rt73USB. I think I have to find it and install myself. Thats the only grip I have with SliTaz.

---

### Post by koleoptero on 2010-10-04
Have a look also at [Linux Mint Debian Edition]("http://www.linuxmint.com/blog/?p=1527"). Much much lighter than ubuntu, and still gnome.

---

### Post by Shakz on 2010-10-04
Peppermint OS is super light and yet functional. Based on linux mint which is based on Ubuntu.....right now anyway.

---

### Post by northwestuntu on 2010-10-04
> **FineE said:**
> One suggestion to speed up Firefox is to install the [Better Privacy]("https://addons.mozilla.org/en-US/firefox/addon/6623/") extension to get rid of Local Shared Objects (LSOs) or "Flash Cookies". I have seen a marked improvement in browsing performance when 200 - 300 of these things are removed.

By the way Ubuntu 10.04 runs great for browsing on a Pentium 4M 1.8 GHZ with 1GB of ram once the LSOs are gone.

i use flash block myself.  makes web surfing so much faster.

---

### Post by northwestuntu on 2010-10-04
> **koleoptero said:**
> Have a look also at [Linux Mint Debian Edition]("http://www.linuxmint.com/blog/?p=1527"). Much much lighter than ubuntu, and still gnome.

yeah ive considered mint before, but from what ive read there's few differences between ubuntu and mint.

---

### Post by hhh on 2010-10-04
> **northwestuntu said:**
> yeah ive considered mint before, but from what ive read there's few differences between ubuntu and mint.
Follow his link and read deeper. He's not talking about Mint, he's talking about Mint Debian, based on Debian testing instead of Ubuntu.

---

### Post by northwestuntu on 2010-10-04
> **hhh said:**
> Follow his link and read deeper. He's not talking about Mint, he's talking about Mint Debian, based on Debian testing instead of Ubuntu.

yes ive looked in to that also, but since it's there 1st release i think ill stay away.  plus i prefer 64bit :) ive heard good things about it though.

---

### Post by Dustin2128 on 2010-10-04
> **northwestuntu said:**
> yes ive looked in to that also, but since it's there 1st release i think ill stay away.  plus i prefer 64bit :) ive heard good things about it though.

mint's pretty nice; its the first distro I'd recommend to a newcomer. But for whatever reason, kde compositing isn't working too well on my old desktop (dedicated geforce ti 4200). Probably some driver issue or something since its not net connected.

---

### Post by Dragynn on 2010-10-04
> **Dustin2128 said:**
> agreed.
It's amazing how much software they can pack into a disc smaller than damn small linux, while still using 2.6 instead of 2.4 kernel.

I know right! 30mb iso, that's just insane, at that size I didn't expect it to have even a file manager/browser, but it's got everything you really need right out of the box. 

On another note, still digging on PcLinuxOS, which like Puppy Linux, has the Iron browser in the repo :) which as you and I both know, is the best and fastest browser around ;-);-);-):biggrin:

---

