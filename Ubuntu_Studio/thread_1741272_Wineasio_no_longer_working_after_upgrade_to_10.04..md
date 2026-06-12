---
title: "Wineasio no longer working after upgrade to 10.04. No ALSA wavout option in winecfg."
date: 2011-04-27
forum: Ubuntu Studio
---

### Post by indstr on 2011-04-27
Hi. I recently upgraded from Ubuntu Studio 9.10 to 10.04, and everything went really smoothly... Smoother than I expected.

But I am currently having one problem: I can't seem to get wine applications to work with JACK and I suspect it is a problem with either wineasio or the way I have my wine set up. 

Versions of everything I am running:

jackd 1.9.7 
wine 1.3 (also had same problem with 1.2 though)
alsa-base 1.0.24 (also had same problem with 1.0.22)
wineasio 0.9.0 

Sound card is m-audio delta 44. 

Here's what happens, I can load jackd just fine, and native Linux apps can connect in JACK normally, and they work. However when I try to load anything through wine, I get this error message:

```
Cannot connect ports owned by inactive clients: "reaper" is not active

```So I opened winecfg, and something is wrong with it and I think this is most likely the problem. It looks like this:

[IMG]http://img855.imageshack.us/img855/5888/noalsawavoutcropped.png[/IMG]

The problem, I think, is that there are no Wave in or out devices under ALSA. I know there used to be in my 9.10 config and this is what I used. 

I have tried messing with the JACK wav in/out in winecfg but it gives the same error as above in the jackd terminal window

I sort of wonder if something needs to be set in .asoundrc (it is currently blank) but I'm not really sure what.

Any input?

It's probably something simple ..

Any help is appreciated. Thanks

P.S... I also noticed when I run winecfg the terminal output says this:

fixme:mixer:ALSA_MixerInit No master control found on M Audio Delta 44, disabling mixer



[IMG]http://www.freeimagehosting.net/image.php?e7433c15b6.png[/IMG]

---

### Post by sgx on 2011-04-28
You can try different wineasio versions, I had to go back to a
7 or 5 in some cases, as wine moves on like a juggernaut, leaving
musicians in the dust...when you get good combos of wine/wineasio,
make sure you save the packages for later. Someone in a recent post
here, also got lucky just overwriting with a different version.

and then the  regsvr32 wineasio.dll

Cheers

---

