---
title: "An Emulator for OSX?"
date: 2007-04-30
forum: The Cafe
---

### Post by teddybairs1 on 2007-04-30
Just a curiosity, as I'm not really a programmer by any means but I thought I'd throw it out there and see if it gets any responses.

I was reading on another thread a guy was wondering if there was anything like WINE, which is an implementation of the Windows API on a Unix or Unix type environment (and so by definition is not strictly an emulator), which would allow a program written for OSX to operate on a Linux platform.

As far as I know, no such program exists. What I was wondering, and I pose this question to those who would know more about it, is how hard it would be to write one? From my understanding, OSX has a Unix core, and shares many similarities with Linux under the hood. How hard would it be to write additional code to allow OSX programs which some people find indispensible to run under Linux? It certainly couldn't as difficult as the Wine project is because we're dealing with "genetically" related OSes as opposed to a completely "foreign" kernel like the nt kernel as compared to the linux kernel.

Just a thought, something to get people thinking and maybe start something. Wish I could, just don't have the time to study programming more.

---

### Post by ericesque on 2007-04-30
just for curiosity's sake, which Mac app are you looking to run?

I've not heard of any OSX emulation.  But then again, think of how useful something like that could possibly be... Mac has...what, 10 different apps it can run?  And then there's probably about 100 people that use a Mac.

I think the verdict is that it's either quicker to port each individual app, or just shoot all the mac users.

---

### Post by Kujen on 2007-04-30
> **ericesque said:**
> just for curiosity's sake, which Mac app are you looking to run?

I've not heard of any OSX emulation.  But then again, think of how useful something like that could possibly be... Mac has...what, 10 different apps it can run?  And then there's probably about 100 people that use a Mac.

I think the verdict is that it's either quicker to port each individual app, or just shoot all the mac users.

A Linux user bashing OSX for how few users there are? The ironing is delicious.

---

### Post by jiminycricket on 2007-04-30
It would need to have Cocoa, Carbon, and all the other stuff like Quartz 2d, Core Animation, etc.  OS X is basically an evolution of NeXTSTEP's APIs.

There's a project called GNUStep that you can install which does implement some of the NeXT stuff though..

---

### Post by Bushfire on 2007-04-30
Yeah, what application? I'm having a hard time thinking of one that would make this a worthwhile project (not a Mac bash, I'm quite fond of them, it's just that most programs will have a Windows version). Garage Band, iPhoto?

---

### Post by yoasif on 2007-04-30
> **Bushfire said:**
> Yeah, what application? I'm having a hard time thinking of one that would make this a worthwhile project (not a Mac bash, I'm quite fond of them, it's just that most programs will have a Windows version). Garage Band, iPhoto?Final Cut Pro?

---

### Post by mech7 on 2007-04-30
> **Bushfire said:**
> Yeah, what application? I'm having a hard time thinking of one that would make this a worthwhile project (not a Mac bash, I'm quite fond of them, it's just that most programs will have a Windows version). Garage Band, iPhoto?

But many of the windows versions do not run correctly under WINE.. so maybe it would be easier to support Mac apps then windows?

---

### Post by fuscia on 2007-04-30
does pearpc (is that what it's called?) work on linux? i think that's an emulator for osx. i once looked into it when i still had windows. (my interest did not hold up well against the 'wtf?' factor.)

---

### Post by mech7 on 2007-04-30
> **fuscia said:**
> does pearpc (is that what it's called?) work on linux? i think that's an emulator for osx. i once looked into it when i still had windows. (my interest did not hold up well against the 'wtf?' factor.)

I thought PearPC was an emulator for PowerPC and now kinda useless since they switched to intel ?

---

### Post by fuscia on 2007-04-30
> **mech7 said:**
> I thought PearPC was an emulator for PowerPC and now kinda useless since they switched to intel ?

ew! that's probably true. i wonder if one could find a ppc version of osx more easily now (read: "cheaper").

---

### Post by G Morgan on 2007-04-30
The OSX API is extremely unstable and keeping up with it would make the WINE teams task look like a walk in the park. Given the difficulty of the task and the comparative gain I can say with almost certainty that it will never happen.

---

### Post by Sunnz on 2007-04-30
> **teddybairs1 said:**
> From my understanding, OSX has a Unix core, and shares many similarities with Linux under the hood. How hard would it be to write additional code to allow OSX programs which some people find indispensible to run under Linux?Well... not quite...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=24821&d=1170940659[/IMG]Out of the 5 top APIs, only 2 are currently (somewhat) available to Linux: BSD and Java.

Most Mac apps that you wanted are likely to be written in Cocoa, and maybe quicktime if it is something like Final Cut Pro. So yea, it isn't just UNIX base...

---

### Post by teddybairs1 on 2007-04-30
Here's a cut and paste of the other thread which got me wondering:

[I]Before I get launched on a minor rant, here's my question:

Is there anything like 'wine' for Mac OSX applications?

After seven years on a Mac I have been using Ubuntu for about five months. I am unbelievably happy with it. I can do things now that I could not have done, or could not have afforded to have done on a Mac. The only grit in the oyster is that sometimes I like to write music. I write it in midi format, use a good quality midi bank to play it back, and when I'm happy with it I export it as an ogg file (or mp3, aif, wav whatever, I don't care, but I want to be able to export it).

I've just spent the day downloading 'jack', 'lilypond', 'rosegarden', 'qsynth' etc. etc. and have got completely lost. I may be thick but it took me half a day to discover the command 'jackd -d alsa', and even then when I use the command, more often than not, and for no apparent reason I get the stderr...

Code:

'JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

...and, of course, jackd doesn't say which application is using 'device hw:0' and 'ps aux' doesn't help, so I can't stop it, so rosegarden and qsynth won't start up, so I'm left tearing what's left of my hair out; and then for no apparent 'jackd' suddenly works, But neither rosegarden nor lilypond come with any sf2 files, so I have to google for them and they are in sfark format and that requires the sfarkxtc_lx86 unzipper which is supposed to work on linux but doesn't, so in desperation I install 'wine' and download the windows version of it and unpack my sf2 database and gradually everything begins to work but then I find that I can't export the results to ogg.

To cut a long story short, I used to use a beautiful piece of Mac OSX shareware called 'Harmony Assistant'. I could write music on old fashioned staves, it had a midi bank to play back the music, and I could export the final results in ogg or any other format. Is there anything like 'wine' for OSX that would allow me to use the one piece of OSX software that I cannot do without? Alternatively, can anybody talk me through the train-wreck that is audio on linux?[/I]

I wouldn't know about the apps for mac personally, but it seems to me that there are at least a few which some people depend on and have no good replacements in Linux just yet.

---

### Post by A_POET on 2007-04-30
Textmate is a good "mac-only" app.  they DO have a program for eindows called "e" that supports textmate's bundles, and apparently there is an open source pc equivalent in the works clled intype.  but whatever...nice app wish it was *nix...

---

### Post by G Morgan on 2007-05-01
> **A_POET said:**
> Textmate is a good "mac-only" app.  they DO have a program for eindows called "e" that supports textmate's bundles, and apparently there is an open source pc equivalent in the works clled intype.  but whatever...nice app wish it was *nix...

We are hardly short of text editors in the OSS world. Nothing matches the almighty Vi in any case.

---

