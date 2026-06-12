---
title: "Adobe Flash Player 10 64 Bit"
date: 2009-08-01
forum: System76 Support
---

### Post by jdmelton on 2009-08-01
For those who might be interested, Adobe has released an alpha version of their Flash Player 10.

The download page is here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I installed it on my Serval (P3) running Ubuntu 8.04 AMD64 LTS and it is working great.

To install, you must first remove any other Adobe Flash Players, including the 32 bit version. It is not necessary to remove the various lib32 helper libraries if they are installed.

--- Edit: This does not work now since the file name was changed. Follow the instructions the Tom provided in his post below. ---

In case you are not familiar with how to do this, one way is to download the file, then browse to it in Nautilus and double-click it. Then choose open with Firefox.

---

### Post by TheBuzzSaw on 2009-08-01
It is what I use on my Wild Dog.

Works great!

---

### Post by paulbary on 2009-08-02
I installed it on a linux-mint 64 machine and found that it goes into buffering mode and pauses the video a good bit more than the prior version. Could just be my installation but for now I've switched back to the February version.

Paul

---

### Post by darco on 2009-08-02
> **paulbary said:**
> I installed it on a linux-mint 64 machine and found that it goes into buffering mode and pauses the video a good bit more than the prior version. Could just be my installation but for now I've switched back to the February version.

Paul

Make sure that you uninstall the previous version. I too have Mint64 and it works perfectly (both versions, x32,x64)

darco

---

### Post by thomasaaron on 2009-08-03
Here are our recommended instructions for installing the 64-bit plugin...

> 1. Shut down Firefox

2. Run the following commands from a terminal...

sudo apt-get remove flashplugin-*
sudo apt-get remove nspluginwrapper

3. Click the link at the very bottom of this page...
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
...to download the latest 64-bit Flash plugin. Save it to your Desktop and extract it to your Desktop.
Drag libflashplayer.so from the extracted folder onto your Desktop.

4. Run these commands from the terminal...
mkdir -p .mozilla/plugins
mv ~/Desktop/libflashplayer.so .mozilla/plugins

5. Restart Firefox

---

### Post by Eldera on 2009-08-03
[quote=thomasaaron]1. Shut down Firefox[/quote]

Are these instructions for Firefox 3.0, Firefox 3.5, or both?:D

---

### Post by gila_monster on 2009-08-03
Should work for both. I've done something similar, works for both versions.

---

### Post by 3Miro on 2009-08-03
I was using the old alpha on my desktop and I was happy with it. Then I upgraded to the new alpha and now things crash too often. The 32-bit + nswrapper version that came installed on my Pangolin works fine and I don't plan on changing that.

---

### Post by gila_monster on 2009-08-03
> **3Miro said:**
> I was using the old alpha on my desktop and I was happy with it. Then I upgraded to the new alpha and now things crash too often. The 32-bit + nswrapper version that came installed on my Pangolin works fine and I don't plan on changing that.

Do you happen to recall the actual version numbers of each? My script always downloads the old one, I think. Works pretty well for me.

---

### Post by thomasaaron on 2009-08-04
gila monster,

That script is just wrapping a 32-bit version with ndiswrapper. The ACTUAL 64-bit version is far better. Does a much better job with hulu, etc...

---

### Post by gila_monster on 2009-08-04
> **thomasaaron said:**
> gila monster,

That script is just wrapping a 32-bit version with ndiswrapper. The ACTUAL 64-bit version is far better. Does a much better job with hulu, etc...

No, sir, my script downloads 64-bit. In fact, it explicitly removes ndiswrapper. I can post it if anyone wants to see it.

I never did have a lot of luck with the 32-bit Flash with ndiswrapper.

---

### Post by thomasaaron on 2009-08-04
Hmmm... I guess I've never seen that script then. I would like to see it, though.

EDIT: Do you mean this is a script you wrote yourself?

---

### Post by gila_monster on 2009-08-04
> **thomasaaron said:**
> Hmmm... I guess I've never seen that script then. I would like to see it, though.

EDIT: Do you mean this is a script you wrote yourself?

I had one I wrote myself, but I liked this one better, so I use it. I'll fire it to you by email, unless you think it would be useful to post here.

---

### Post by thomasaaron on 2009-08-05
Excellent. Thanks, gila_monster.

---

### Post by AK49er on 2009-09-09
> **thomasaaron said:**
> Here are our recommended instructions for installing the 64-bit plugin...
Hello, i am a noob to linux and am trying to get this to work i followed the instructions and i think it worked but am not sure. How can i confirm that this did work for me and i didn't mess anything up ? Oh and i am running Linux mint 7 64 bit. I did notice that after the last command in the terminal the file i draged to the desktop disapeared, i am assuming this is a good sign and i tried to play Youtube videos and they worked good as well. I am loving this linux os so far and am glad to have gotten away from M$. :guitar:

---

