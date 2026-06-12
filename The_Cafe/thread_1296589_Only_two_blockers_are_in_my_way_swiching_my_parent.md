---
title: "Only two blockers are in my way swiching my parents computer"
date: 2009-10-20
forum: The Cafe
---

### Post by jc0811 on 2009-10-20
As the family I.T. guy I drive to my parents house from time to time if they have issues with the computer. Also to visit them too. :)


My mother is a teacher that teaches in Spanish in the elementary school. Right now she uses Office 2003 and using the International character toolbar. It's very easy for her to type in Spanish. If she wants a special Spanish character she just go to the International character toolbar and click on what she wants. She presses shift when she wants it capitalized with that certain symbol in place. 

This makes it very easy for her instead of having to memorize key combination's. 

Their needs are pretty basic by the way. Besides what I pointed out earlier. They sometimes receive powerpoint slides from family and friends, view photos from the digital camera or view footage from the camcorder, Internet (of course) which includes home banking and youtube videos. 

This is the smaller issue of the two. I was wanting to know if anybody uses Office 2003 on Ubuntu or Kubuntu. Just wondering too if it's a perfect seamless procedure after you have WINE configured of course. 

The next issue is kinda a big issue. My mother also uses a iPod nano. She got for Christmas last year. I was going to say she uses iTunes to sync her ipod. But it's actually me that does it for her. She just rips from her cd collection onto her ipod. 

I know sooner or later she will want to use iTunes to purchase songs or albums from there. She hasn't done any purchases from the iTunes store right now by the way. But I know she is not opposed to that. What do I do in this case? 

Also a side note my parents own a Epson Stylus Photo R200 printer. I am not sure how well either Ubuntu or Kubuntu would work with that printer. 

I am leaning more towards Kubuntu because it resembles Windows more than Ubuntu. I think it will be easier for them moving from Windows. I still intend to keep Windows so it will be a dual boot option. 

I would like them to switch to a Linux distribution since my mother will be retiring soon, a faster machine and better security. Also since the recent bank trojan on Windows operating systems.

[http://www.cbsnews.com/stories/2009/09/30/tech/cnettechnews/main5353515.shtml](http://www.cbsnews.com/stories/2009/09/30/tech/cnettechnews/main5353515.shtml)

I thought I should pick up the pace and have them switch to Linux. I hope someone can help out with this.

---

### Post by KhanTG on 2009-10-20
Your first issue with Spanish Characters, I really don't know (but I'll look into it).  PowerPoint presentations can be created and viewed with OpenOffice.org Presentation (OO.o Writer or AbiWord might have what you want with the Character thing)... 
  I don't have an iPod, but my brother-in-law was able to get his to sync with Banshee Media Player.
  The printer should work out of the box (check first using a live CD or USB), if not check out this [post]("http://wiki.soslug.org/wiki/adding_an_epson_stylus_photo_r200_printer_to_kubuntu_pclunuxos_and_debian") 

  Back to M$ Office... I have installed 2000 with WINE without a hitch... haven't tried 2003 yet (but I really only use OO.o)

  As for the distro.. well I really don't like KDE personally (but that is MY taste, not necessarily ours).. I have turned many people on to Linux using the Gnome desktop (I just think it's easier)... I have also found that Linux Mint (based on Ubuntu and can use the repos with no issues) is great for new Linux users; mainly because it is more similar to Windows... 

Good luck with helping your folks, and I hope I wasn't too drawn out.. LOL

---

### Post by pwnst*r on 2009-10-20
virtualbox

---

### Post by AllRadioisDead on 2009-10-20
> **pwnst*r said:**
> virtualbox
That's not a very simple or practical solution.

---

### Post by CharmyBee on 2009-10-20
It's more practical than say, jeopardizing the OS functionality they are familiar with.

---

### Post by tacantara on 2009-10-20
> **pwnst*r said:**
> virtualbox

+1 pwnst*r and CharmyBee

As a VB user since I started using Ubuntu, I find it to be much better than Wine at handling the very few Windows-only items that I have to run (iTunes, smart card software/firmware, and some U.S. Army software for completing forms online).  As long as you have a licensed version of Windows, you can set up a virtual machine and add necessary programs to it with relative ease.

---

### Post by dj-toonz on 2009-10-20
I'd second everything what's been said virtualbox is the way to go, What I do under Ubuntu, as I need to run Itunes for my Iphone (just install windows xp in a virtual machine)

---

### Post by KhanTG on 2009-10-20
VirtualBox is great, but it might add a level of confusion... and frustration as the Vbox version will be remarkably slower than Windows already is.  If you are looking for "replacements" then there are plenty out there.. There really is no point to installing ANY Linux distro if you are just going to use Windows for most of your work anyway.

---

### Post by dj-toonz on 2009-10-20
On my system using windows in virtual-box is just like using windows normally, don't play games or any 3D stuff, just use it to sync the Iphone in Itunes and a couple of other software i.e windows live messenger, windows is using 3.2Gigs of ram, dual core of my system, 80gig's & I don't see any slowness from using windows

---

### Post by earthpigg on 2009-10-20
+1 to vbox.

you could also set them up to dual boot. "here, mom, this is how you pick between Linux and Windows. pick whichever you like whenever you want. when you pick linux, call me before ever entering your password for anything other than logging in and this here add/remove applications thing."

also, for purchasing music.... amazon.com's music store is linux-friendly, i hear? yes/no?

another option.

another option is also to go back in time and scold whoever gave your family the 'gift' of vendor-locked-in products like iPods.

time travel support is expected sometime in the Linux kernel's 2.8 series, and there is alpha-quality support for physically traveling through time on FreeBSD's -CURRENT branch.

---

### Post by Nerd King on 2009-10-21
MS Office.. Wine is pretty good but takes time to set up, you might find Crossover is easier (albeit you have to pay for it). OpenOffice is a good alternative, but there is the problem with some incorrect rendering of docx files from Office 2007, and the themes from pptx (Powerpoint 2007) files don't carry over as they're not embedded in the file anymore. Having said that, they're using 2003 so can't use 2007 formats as things stand anyway so they're not missing out on something they already have, but will likely blame ubuntu when they can't open what people send them, regardless of whether office 2003 would have the same issue.

Language switching in Linux is easy (in Gnome at least). Simply add to your Gnome panel (kde probably has an equivalent) the keyboard indicator applet. Add your chosen languages, and they just click to switch keyboard layouts. Job done.

The IPod: Forget ITunes, it just isn't going to work reliably. You can fiddle and tweak and get older stuff working with a poke and a fiddle but it's not worth it. Not sure about whether you can get files onto a nano, but if you can then we can look at alternatives. Might I suggest getting them into Rhythmbox/Banshee for music playing on the computer and encourage them to use a DRM-free solution for buying music, ie introduce them to it and show them how to use it? Explain the benefits that they actually OWN the music and will be able to transfer it to other devices.

My experience with epson printers has been good, and the r200 is a brilliant little printer. It takes some punishment and keeps on going. The only downer I find with printing in Ubuntu is not seeing the ink levels. I believe there is an app that will do this, I can't remember the name off the top of my head but a quick google should see you right. That said, if a printer's not working, sometimes it's wise to try it in Windows to get a proper idea of what's gone wrong. Printing in Linux is still not seamless.

Btw I'd not worry about Kubuntu being more like Windows. I've found non-techies get on just fine with Gnome, if anything KDE confuses them more. 9/10 times if I show a non-techie gnome (standard), my pimped-out gnome (with compiz and gnome-do and kde they will choose gnome of one flavour or another.

---

### Post by pwnst*r on 2009-10-21
> **ihermit said:**
> That's not a very simple or practical solution.

how isn't it? THEY won't be installing it.

---

### Post by KhanTG on 2009-10-21
> **pwnst*r said:**
> how isn't it? THEY won't be installing it.

Maybe not... but THEY will have to use it.  Never over estimate your client's savvyness; if they KNEW what they were doing, it wouldn't be in your hands to fix.
   I personally use Vbox for testing purposes, but never on a daily basis... I really don't like having to start my machine then start another machine just to do what I need to do.
   Said it before, and I stand by it: "There really is no point to installing ANY Linux distro if you are just going to use Windows for most of your work anyway."

---

