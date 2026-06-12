---
title: "Youtube problems on Starling"
date: 2009-12-12
forum: System76 Support
---

### Post by Tart on 2009-12-12
Recently I decided to try 9.10 on my Starling, but I was disappointed with some of the features. So i went back to 9.04 (fresh install), I followed instructions from website and everything went smoothly. But youtube doesn't work. I just see black window, I do hear sounds sometimes, but most of the time it is just black window and nothing else. I did install restrictive codecs and such (followed instructions from sys76 web site). Did I miss something? My wife Starling works perfectly I have no idea what to do.

Thanks

---

### Post by AZ_RUNE on 2009-12-12
Have you tried re-installing the system76 drivers. Barring that swf in the repositories might be of help and you can try checking on all the codes your media (like Rhythmbox) player can use.  Often I snag a dependency that does what I need it to do. Also as a side note you can check out the steps Falko Timme uses to make the perfect Ubuntu Desktop (YMMV) at HowToForge.  Just google "Ubuntu 9.04 Perfect Desktop" in the search bar and see if his article helps.

AZ_RUNE

---

### Post by jeffran on 2009-12-12
You may just need to install Flash:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

I'm not sure why reinstalling the System 76 drivers will make a difference.

---

### Post by Tart on 2009-12-13
Thank you for your reply. Yes, I do have latest system76 drivers installed. Just to be sure I reinstalled them again. No luck. And I did install flash as well via Add/Remove, plus then you first start Firefox and it goes to site with flash it asks if you want to install plug in for it, and I did.

I tried reinstalling flash by following your link jeffran, but when I select APT for Ubuntu 9.04+ and click on "Agree and install now" nothing happens. :(

It looks like something definitely wrong with flash, I have problems watching videos on other sites.

---

### Post by thomasaaron on 2009-12-14
Please try running...

sudo apt-get --purge remove flashplugin-*
sudo apt-get install flashplugin-installer

Then, restart your browser.

---

### Post by Tart on 2009-12-14
It didn't help :-(. I'm attaching two screenshots one shows what I see usually on youtube, the other shows that plugins are installed with firefox.

---

### Post by thomasaaron on 2009-12-15
Have you tested with a wired connection?
Have you tested with a different wireless access point?

(I realize you're wife's starling works fine, but sometimes some APs can get a little weird.)

You might also want to try resetting the AP.

Essentially, we want to fully rule out the AP before digging much deeper. Frankly, a fresh install and our tutorial for installing restricted codecs should be all you need.

---

### Post by Tart on 2009-12-18
I tried wired connection yesterday. Same story. Initially any video shows as black with no controls available (as in picture), but sometimes, controls become available, and it turns into slide show (even if video is completely loaded), sound skipping back and forth often. Weird... must be something I installed.

Thank you for your help

---

### Post by houseworkshy on 2009-12-18
I've found with youtube videos that for some reason even after the restricted extras have been added it is sometimes nessesary to put the flash non free plugins in seperately through the synaptic package manager.  Another thing that can get in the way is browser settings such as whether you've allowed java script or not.  Also if you have noscript, or similar, in firefox that has to be configured to accept it too.

---

### Post by thomasaaron on 2009-12-18
Hi, Tart.

Are they only choppy in full-screen mode, or in the minimized mode as well?

Also, type...

about:plugins

...in your browser's URL bar, and let me know what it shows installed for Shockwave Flash. A screenshot would be great.

Also, just to clarify, you are using Firefox, right?

---

### Post by Tart on 2009-12-18
They are choppy in minimized mode. Yes I'm using firefox, and I actually did posted screenshot with about:plugins in message above. There was no changes since. 

I'll play around with my both netbooks on a weekend and compare two, see what I have installed on both and try to isolate the problem.

---

### Post by thomasaaron on 2009-12-18
OK. I think I see the problem. You are running Flash 9. I just imaged a Starling with 9.04 from our imaging server, and it is running Flash 10.

So, then I deleted flash and re-installed it to see if maybe...

sudo apt-get install flashplugin-installer

...was installing Flash9, and it is not. It correctly installs Flash 10.

So, please do the following, and report your results at each step:

1. In your URL browser, go to about:plugins and report the Flash Version you have installed.

2. Go to a terminal and run...

sudo apt-get --purge remove flashplugin-*

3. In your URL browser, go to about:plugins and report the Flash Version you have installed. (It shouldn't be there at all.)

4. Run...

sudo apt-get install flashplugin-installer

3. In your URL browser, go to about:plugins and report the Flash Version you have installed. (It should be Flash 10.)

Let's figure out where it is going wrong.

---

### Post by Tart on 2009-12-18
For some reason step 2 doesn't kill plugin (it did removed package - at least reported). See attached screenshot it is step 3.

Edit: I removed flash via Synaptic Package Manager, and followed rest of your recommendations, and now everything works fine.

Thank you so much for your help.

---

### Post by PatrickVogeli on 2009-12-19
I'll try to help!

sudo apt-get remove swfdec-mozilla

that should take care of removing the wrong version. Then you can install adobe's flash using the command Tom gave.

---

