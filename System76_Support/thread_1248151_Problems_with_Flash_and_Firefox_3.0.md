---
title: "Problems with Flash and Firefox 3.0"
date: 2009-08-23
forum: System76 Support
---

### Post by samalex on 2009-08-23
Hi,

Yesterday I removed IcedTea and was able to get Sun Java to install and work great, but now I'm unable to get Flash to work properly.

I've installed nspluginwrapper and flashplugin-installer from Synaptic, and though I have this under about:plugins:
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r32

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Any time I visit a site with Flash nothing happens.  There's a place holder for Flash but nothing actually happens, no right click or anything.

So I uninstalled flashplugin-installer and nspluginwrapper then followed instructions on installing the 64-bit Flash 10 (found on various posts in the system76 forum), and Flash now works, but Firefox crashes on most sites with only a "Segmentation fault" error (from running Firefox via command line).

So I'm at a loss on what to try next.  I need flash for my online class that starts tomorrow, so until I this fixed I might have to use Firefox on Windows via VirtualBox.

Any suggestions???  Thanks --

Sam

---

### Post by samalex on 2009-08-23
I uninstalled and reinstalled flashplugin-installer and nspluginwrapper and now Flash is working.  I hope things stay stable because I can't afford to have things hose on me, especially while taking a test because if the browser hoses before it's complete I have to go to campus and take the test there :-/  

I still don't know why the 64-bit Flash 10 isn't working though.  I'm not sure if the "Segmentation Fault" error is coming from the Flash plugin, Firefox, or what.  Does Firefox have any other logs I can check out?  I guess as long as the nspluginwrapper is working I'm good though.

Sam

---

### Post by thomasaaron on 2009-08-24
Yeah, I don't understand that one either. It runs fine on our shop Pangolin.

You might want to review the instructions to make sure you're installing it correctly.

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


That nspluggin-wrapped 32-bit flash will give you problems. You should only have to restart firefox if it does, though.

After installing the 64-bit version, try typing...

about:plugins

in your URL bar in firefox. See what plugins it shows installed for flash.

---

