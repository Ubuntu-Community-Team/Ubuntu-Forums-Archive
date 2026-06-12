---
title: "Netbook Remix - Oh Dear"
date: 2010-02-01
forum: Testimonials &amp; Experiences
---

### Post by bignose27 on 2010-02-01
Hi,
I recently was given an Acer Aspire One A110AW netbook. It has an awful OS on it called linpus lite. After some research, I came to the conclusion that it was restrictive and had to go.

Ubuntu Netbook Remix seemed to be the answer to my prayers! Right up until I had loaded it. Since then I have had one problem after another. In the last 48 hours, I have spent more time on a windows machine in forums than I have using my netbook. The reason for this is the error messages that have come in - thick and fast.

After two attempts I downloaded the NBR image. I loaded it to the netbook via USB using UNETBOOTIN. This was OK after a few attempts.

Once loaded everything seemed OK until I tried to play a DVD. Then I get the message "No URI handler implemented for DVD" After some time over the forums I realise that the default media player doesn't actually play media that well at all. It seems that I need codecs and Ubuntu Restricted etc etc.

Now, when I'm attempting to add this software, it either can't complete or has some problem that components are already intalled and the new ones can't be. So I try a different approach. I try other media players like MPlayer. Guess what? Similar issues again but still no DVD to watch.

Then I thought I'd try and install WINE. I found it, tried to install it and got the "Package dependencies cannot be resolved" message. Installation halted can't go any further.

Now I decide to try something else as its getting hard to play a DVD or load a simple program. I know, I'll try loading my Orange Mobile Broadband dongle, in for a penny in for a pound.

This is the one where when its placed in the usb slot it is recognised? No. The memory card inside is, but not the modem.

All in all, I entered this with good faith. All I really have done is spend hours trying to get this netbook working on a basic level. Every time I try to do something simple, I am met with errors and messages. I naively believed that there was a serious alternative to windows, basically it isn't.

I am not a computer expert, I cannot program. All I want to do is simple tasks on a machine that will allow me to do them. 

Given my experience over the last few days I can easily see why MS and MAC dominate. Linux have had their best chance ever to shine with the advent of netbooks, but if the numbers for sale on ebay are any guide, the masses don't want anything other than something that is simple - and that appears not to be Linux. 

*Am I being unfair asking for something to be reasonably easy to understand without a degree in ICT?*

---

### Post by armandh on 2010-02-01
my mini-9 is sporting OOTB 9.04 [and just works]
the factory Delbuntu was the pits.
I found the net book specific OS disfunctional.

---

### Post by bignose27 on 2010-02-01
"I found the net book specific OS disfunctional."

I didn't like to say because I don't know what the other distros were like. I was maybe labouring under a misapprehension that because it was netbook specific it would do the job.

I've a lot to learn haven't I?

---

### Post by arubislander on 2010-02-01
> **bignose27 said:**
> I recently was given an Acer Aspire One A110AW netbook. It has an awful OS on it called linpus lite. After some research, I came to the conclusion that it was restrictive and had to go.

How about your own experience... why was Linpus Lite restrictive to you? What did you want to do that it didn't allow you to?

If you are going to install another OS on a machine with custom hardware and an OS specifically geared to work on that hardware, you shouldn't be surprised that you get problems...

It would be a little like getting a windows machine and installing MacOS on it...

---

### Post by Swagman on 2010-02-01
I  didn't know netbooks had an optical drive ?  My daughters Eeepc don't have one.

oh well... For legal reasons various codecs CANNOT be included by default. You can install them yourself though.

I'm going to tell you to open a terminal for the simple reason you can copy & paste this text in it.

Firstly you need various codecs.. right ?

```
sudo apt-get install ubuntu-restricted-extras
```

That will take a while

When it's done
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Bobs your mothers brother.

---

### Post by bignose27 on 2010-02-01
Unfortunately Robert appears not to be my mother's sibling.

Linpus cannot be easily customised (backgrounds, themes etc). You can however play a DVD from an optical drive via USB. You can also play DVD files from a USB drive!

You're right, there isn't optical drive in it. I connected one via USB. I also used a USB hard drive with the DVD files on in the same way too. Both work on a pc but not the netbook/ubuntu.

Codecs? For the same legal reasons I suppose, I can connect my DVD to a MS machine and actually watch a DVD without having to do anything?

I have opened the terminal and entered the code you have thoughtfully placed in the message.

The message in return is:

"ubuntu restricted extras is already the newest version.
The following packages were automatically installed and are no longer required:"

It then lists the lib packs that were installed and " 0 upgraded 0 newly installed 0 to remove and 0 upgraded "

The next code went in and returned "ldconfig deferred processing taking place" This is how the machine is and has been since I tried it. No DVD playback since though.

Your assistance is (believe it or not) greatly appreciated, Thank you!   But it doesn't work.

---

### Post by Swagman on 2010-02-01
Sorry to hear that didn't work for you. I don't have a usb dvd drive to try on my daughters (3 of them) EeePC's.

> Codecs? For the same legal reasons I suppose, I can connect my DVD to a MS machine and actually watch a DVD without having to do anything?

That's because you already paid for the licences in your Windows install. And I bet you still had to install Flash etc ?

If you require help to resolve your netbook issues you will need to post in the relevant section as no-one (hardly anyone) will see it here.

Hope you get it sorted soon.

Paul

---

### Post by davidryderuk on 2010-02-01
> 
It then lists the lib packs that were installed and " 0 upgraded 0 newly installed 0 to remove and 0 upgraded "

The next code went in and returned "ldconfig deferred processing taking place" This is how the machine is and has been since I tried it. No DVD playback since though.


An alternative is to manually download the package (libdvdcss2) from the medibuntu repository and then install it:

1. Get the package from the following link:

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)

2. Double click on the deb file. 

3. When package installer opens click on "Install Package".

> 
Then I thought I'd try and install WINE. I found it, tried to install it and got the "Package dependencies cannot be resolved" message. Installation halted can't go any further.

Are you following the guide on wine's website? If so then I recently had the same problem. Whilst the "wine" package refuses to install, the "wine1.2" package seems to work quite well.

```
sudo apt-get install wine1.2
```

> 
Now I decide to try something else as its getting hard to play a DVD or load a simple program. I know, I'll try loading my Orange Mobile Broadband dongle, in for a penny in for a pound.

This is the one where when its placed in the usb slot it is recognised? No. The memory card inside is, but not the modem.

I don't know a lot about 3G dongles. I do know that I got one to work on my computer by rebooting with the dongle plugged in. It might be worth trying.

---

### Post by Jazzy_Jeff on 2010-02-01
Install the VLC media player from the repositories. That should play every video format you can throw at it.

---

### Post by armandh on 2010-02-01
every install I do gets VLC added and 
[www.medibuntu.org](www.medibuntu.org) has all the needed stuff in about 4 copy/paste to terminal.
flash is now sooooo easy, a few clicks after being redirected to adobe

---

