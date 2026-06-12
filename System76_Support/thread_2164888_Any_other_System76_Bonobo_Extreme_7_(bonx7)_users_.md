---
title: "Any other System76 Bonobo Extreme 7 (bonx7) users around?"
date: 2013-08-02
forum: System76 Support
---

### Post by Ken_Young on 2013-08-02
I believe I have one of the first System76 Bonobo Extreme 7 laptops.   I had ordered a bonx6, but System76 upgraded me to a bonx7, which was darn nice of them.  It has the new Haswell processor, and it's very very fast.  It has a few problems however, which I have been unable to resolve via phone or website support.   I am hoping I can compare notes about the issues I'm seeing, to learn if I have some defective hardware, or if there are just a few software issues with this very new box.    Anyone else got one of these things and wanna talk?

The main unresolved problem I have is that the headphone jack does not work at all.   I've tried several sets of known-good headphones, and they are never detected and the audio always come out through the internal speakers.

---

### Post by Matt12334 on 2013-08-05
Hi, I don't have a Bonobo (I'm still waiting on my Galago, in fact), but I think manually changing your audio output should fix it.  Open the dash, type "sound", open the sound application, and select your headphones instead of the built-in speakers. Hopefully that works!

---

### Post by isantop on 2013-08-05
I think this is due to the firmware on your machine. Certain users elected to receive their systems with the pre-release firmware in order to get their systems faster. I think your system has the pre-release firmware.

We will have a BIOS update available by Wednesday. If you haven't yet opened a support ticket, go ahead and open one, and we'll send you instructions once the update is available.

---

### Post by Edward_G_Prentice on 2013-08-18
I have one on order. As soon as I get it, I'll check out the audio.

---

### Post by linuxgnuru on 2013-08-22
I have the bonx6 for about 3 months now; and love every bit of it. Just wish I had opted for more than 8GB of ram heh.

---

### Post by Edward_G_Prentice on 2013-08-29
I now have my bonx7. despite the system hangs, I love the machine. Does anyone know what's different between bonx6 and bonx7? The site has a "getting started" for bonx6 but not bonx7, and the system76 wiki never mentions bonx7 as near as I can tell. Is there any bonx7 specific documentation anywhere?  I'm exploring and learning, but it would be nice to have something to start me off.  I have not yet had a chance to check out the headphone audio. Have you resolved your problem yet Ken_Young?  Are there any other bonx7 owners lurking?

---

### Post by isantop on 2013-08-29
The differences are mostly internal. The BonX7 uses Haswell processors and GTX 700 series GPUs, rather than Ivy Bridge and GTX 600s. 

Externally, the only difference is that the DisplayPort is now a Thunderbolt port, and it's moved to the side (instead of the back).

---

### Post by ionFreeman on 2013-09-13
I'm about to buy one. Is everybody happy with theirs?

---

### Post by rrohde on 2013-10-16
I received my bonx7 yesterday, and I am quite happy with it. 

I had an ASUS G75VW, which I handed down to my wife (she's a gamer like me). The bonx7 is based on the Clevo P370SM (also, Sager uses that model as their NP9380). 

Compared to my ASUS G75VW, the bomx7's fan is constantly on, regardless of how little I am doing (goes for Windows7 and Ubuntu 13.10 which I upgraded to right away). Any idea as to how to "fix" that? 
Another thing that bothers me is the fact that the DC power cable from the (even larger than ASUS's) power brick is really short. When lounging in my chair, it barely reaches up from the floor.

The keyboard is decently lit, the additional colors are fun to play with. The chicklet style keyboard on the G75 felt more solid, and the bonx7's keys are just too closely grouped together (with some questionable choices regarding the placement of the HOME and END keys.  However, there's a real (not just a sticker) Ubuntu Super Key. Kudos to System76. :) 
The performance is pretty awesome and step up from the G75. The clickpad is great, and works really well. In order to right-click, you move to the lower right corner - it works well in Ubuntu.  

What I don't like so much is the fact that some of the Fn keys are hardware coded, which means they work, however, they don't get an indicator message and don't affect the software, e.g. pressing Fn+F1 to disable the clickpad, it does it on a hardware level, but Ubuntu is not notified, nor does it toggle the touchpad on/off in the Ubuntu System Settings. Same goes for the keyboard backlight brightness, In Windows, mind you, there's a driver for that.

I opted for the ColorPRO clossy screen and it's stunning. The colors pop and everything is super crisp. Reminds of my older Dell XPS and MacBook Pro. 

Oh, and here's a huge plus for all of those who struggled with the lack of a working LCD screen brightness on laptops with NVIDIA cards: The bonx7's Fn +F8 and Fn+F9 keys do work like a charm, and for the first time in years I was able to adjust my screen brightness in Ubuntu. :) 

Overall, I am very happy with the bomx7, I just wish there were more info on the wiki, the system76 driver doesn't really give out any feedback info on whether it's installed or not. I believe mine just stopped working - but how would I know? 

Oh, and what about BIOS updates, etc? I feel a little left alone compared to what's available from other manufactures, such as ASUS or DELL to keep stuff up-to-date. 
...and how can I fix the 24/7 fan noise? Again, the ASUS was super quiet and only got louder when playing 3D heavy games -- not browsing the web. ;)

---

### Post by jimjam05 on 2013-10-16
I too have the (bonx7) Bonobo Extreme and have neither problem. The whole system is quiet and headphones worked out of the box. I have a fingerprint scanner that doesn't work but not a show stopper.  Great product in my opinion!

---

### Post by rrohde on 2013-10-17
> **jimjam05 said:**
> I have a fingerprint scanner that doesn't work but not a show stopper.  Great product in my opinion!

That's an easy fix, even though the fingerprint implementation in Ubuntu is not as solid as I would like. Also, the pop-up that prompts you to swipe your finger sometimes is behind the active window... Oh, and it doesn't work all the time as it simply stops detecting fingerprints during a session. 

Here's the fix ([https://launchpad.net/~fingerprint/+archive/fingerprint-gui):](https://launchpad.net/~fingerprint/+archive/fingerprint-gui):) 

Installation
=========
0. First of all, if you have installed Fingerprint GUI manually before, get rid of it completely. Remove all binaries, shared libraries, any other files and undo all the changes you have made to your system config files (especially to files under /etc/pam.d/).

1. Add this PPA to your sources:

    sudo add-apt-repository ppa:fingerprint/fingerprint-gui
    sudo apt-get update

2. Install the packages:

    sudo apt-get install libbsapi policykit-1-fingerprint-gui fingerprint-gui

3. Log out of your session and log back in (we need the new session defaults to be picked up).

Setup
=====
After installation launch “Fingerprint GUI” and enrol your fingerprints.
That should be all you need to do!
Try locking your screen, logging out and in, sudo in terminal and running graphical apps requiring root privileges.

---

### Post by John Jason Jordan on 2013-11-09
I really want a Bonobo Extreme, but I insist on a Blu-ray burner. I e-mailed System 76 about the possibility of a Blu-ray burner in the Bonobo Extreme and they replied that Blu-ray won't work in Ubuntu. I beg to differ, as I have a Blu-ray burner in my Xubuntu 12.04 desktop, and it works fine. I think the salesperson was just trying to get rid of me. I'll probably get a Sager instead, although I'll have to buy it with that other OS.

---

### Post by GeneSalamin on 2013-11-10
ZaReason offers Blu-ray burners on their Linux systems.

---

### Post by John Jason Jordan on 2013-11-10
> **GeneSalamin said:**
> ZaReason offers Blu-ray burners on their Linux systems.

Yes, and so do the majority of other laptop vendors, including Sager. Isn't the Bonobo Extreme based on a Sager? And Puget Systems offers Blu-ray burners on their Linux laptops as well. 

I currently have a five-year old Lenovo T61 with a dock. The dock has spoiled me. I want my new laptop to have a dock. But, except for Lenovo and maybe one or two others, docks like I have for my T61 are no more. Today you need to get a USB 3.0 dock. I don't mind having a USB dock, but for almost all laptops (including the ZaReason laptops) the USB 3.0 ports are on the sides, usually near the front. That means a cable running down the side of the computer, getting in the way of books and papers. That is unacceptable. I want my new laptop to have at least one USB 3.0 port on the back.

The combination of a USB 3.0 port on the back and a Blu-ray burner limits me to just a handful of brands and models. For example, I'd love to get a 15.6" laptop, but I haven't found a single one with a USB 3.0 port on the back, hence my only choices are 17" laptops. I'd also love to get a new Thinkpad because then I could get a real dock and I wouldn't need the USB 3.0 port on the back, but Lenovo doesn't offer Blu-ray burners on any of their laptops. Nor does System76, although I see no reason why they couldn't on the Bonobo Extreme. If it's based on a Sager and Sager offers a Blu-ray burner, then the bay must be capable of holding a Blu-ray drive.

My current top pick is an eRacks King:

[http://eracks.com/products/laptops/KING/]("http://eracks.com/products/laptops/KING/")

Which is also based on a Sager (NP9370). Most people are not aware that eRacks sells laptops, but in e-mails with them I have found that they not only offer some high end laptops, but they seem extremely flexible. For example, their website configuration page does offers Ubuntu 12.04, but not Xubuntu. When I said that I preferred Xubuntu 12.04 their response was "no problem, we'll put whatever Linux you want on it." However, they also offered to put Linux on a different Sager if I wanted, and that bothers me. Surely there will be issues with some Sager laptops - e.g., the video might not work well. That makes me wonder how well they test their models like the King. The Linux parts of my brain tell me to put more faith in System76.

---

### Post by John Jason Jordan on 2013-11-10
> **GeneSalamin said:**
> ZaReason offers Blu-ray burners on their Linux systems.

I didn't mean to sound anti-ZaReason in my previous post.

I participate in a local LUG that runs a Linux Clinic where people (usually newbies) bring their computers for assistance. A couple of months ago a fellow brought in a ZaReason with an SSD drive. I watched it go from cold to fully booted Ubuntu in nine seconds (I timed it). I'd be using a ZaReason today if I could get one with a USB 3.0 port on the back.

---

### Post by GeneSalamin on 2013-11-10
JJJ, if you have good feelings about ZaReason, and are just unhappy about the location of their USB 3.0 ports, contact them and ask if they can accomodate your wish.  In my discussions with them, ZaReason is quite willing to customize.  If it's only a cable reroute, I'd guess they will do it for you.

---

### Post by isantop on 2013-11-11
Blu-Ray doesn't work in Ubuntu. The movies require lots of highly-technical, unfinished doftware to work correctly, and it's not a user-ready solution. They will work for burning data-only Blu-Ray disks, but these offer little advantages when compared to USB flash drives, which are generally cheaper per gigabyte and fully re-writeable and modifyable. In our eyes, offering a Blu-Ray drive standard implies that watching Blu-Ray movies works fine, which is not the case.

If, at some point in the future, support for Blu-Ray movies becomes more mainstream, we'll definitely offer them as standard or options.  Additionally, you're free to purchase a Blu-Ray drive for your system and install it once you receive the system.

---

### Post by John Jason Jordan on 2013-11-11
> **isantop said:**
> Blu-Ray doesn't work in Ubuntu. The movies require lots of highly-technical, unfinished doftware to work correctly, and it's not a user-ready solution. They will work for burning data-only Blu-Ray disks, but these offer little advantages when compared to USB flash drives, which are generally cheaper per gigabyte and fully re-writeable and modifyable. In our eyes, offering a Blu-Ray drive standard implies that watching Blu-Ray movies works fine, which is not the case.

If, at some point in the future, support for Blu-Ray movies becomes more mainstream, we'll definitely offer them as standard or options.  Additionally, you're free to purchase a Blu-Ray drive for your system and install it once you receive the system.

You can play most Blu-ray movies right now, although the newer ones are starting to come out with BD+ encryption. Playback of DB+ encrypted movies is still in development. There are also Windows Blu-ray players that will work in Wine (Aisoft Blu-Ray Player is one). And, as you mentioned, Blu-ray devices can be used for data or, more importantly, you can copy the contents to your hard drive. I haven't tried it as I have no Blu-ray movies with BD+ encryption, but I have heard that you can rip them to other formats. 

But most importantly of all, I have had my T61 about five years, and that's how long I'd like my next laptop to be functional. If I buy a Bonobo Extreme today I feel that I am buying something that will be obsolete in six months.

---

### Post by isantop on 2013-11-12
Like I said, you can definitely add a Blu-Ray drive yourself, if you prefer. As it stands, setting up Blu-Ray playback isn't something that's user-friendly yet (even if it is possible).

---

### Post by John Jason Jordan on 2013-11-12
> **isantop said:**
> Like I said, you can definitely add a Blu-Ray drive yourself, if you prefer. As it stands, setting up Blu-Ray playback isn't something that's user-friendly yet (even if it is possible).

Where does one buy the Blu-ray drive? Do you sell it? Sager? And you are talking about a drive to replace the DVD drive that comes with the Bonobo Extreme, right?

---

### Post by isantop on 2013-11-13
I would look at Newegg or Best Buy.

---

