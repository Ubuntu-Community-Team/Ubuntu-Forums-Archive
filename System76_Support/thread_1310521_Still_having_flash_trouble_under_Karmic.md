---
title: "Still having flash trouble under Karmic"
date: 2009-11-01
forum: System76 Support
---

### Post by Ed.Corcoran on 2009-11-01
So I updated to Karmic with very few hiccups. However, Flash is still giving me havoc like it did under Jaunty. The 32 bit will work for a while and then, all of the sudden, it will do some sort of soft crash where every flash thing in all my Firefox tabs goes away and becomes a white or grey box. Then, at some point later on, I get a hard crash. 

64 bit Flash is still doing what it was doing, crashing whenever I go to Youtube or Hulu (although Vimeo works fine) and bringing down Firefox. I've been experimenting with Chromium, and I get slightly better results. Flash will still crash, but I just get an error saying "The following plugin has crashed: /home/ed/.mozilla/plugins/libflashplayer.so". Chromium uses different threads for each tab, so Chromium doesn't crash when Flash does. Also, Youtube works under Chromium sometimes, but Hulu still causes a Flash crash.

Any ideas? I can't just disable Flash. I don't want to get stuck using the 90s version of the Internet, all spinning gifs and under construction signs.

---

### Post by HotShotDJ on 2009-11-01
> **Ed.Corcoran said:**
> 64 bit Flash is still doing what it was doing, crashing whenever I go to Youtube or Hulu (although Vimeo works fine) and bringing down Firefox.Odd.  While I've had the same experience as you with the 32 bit + nspluginwrapper, the 64 bit flash has been great.  What method(s) have you tried for installing it?  Here is what I did:

System -> Administration -> Synaptic Package Manager.  Enter "Flash" in the quick search box and mark anything that is installed for Complete Removal.  Click apply, and then allow Synaptic to do its thing.  After the complete removal is complete, click on the "Status" button in the left panel and check for anything under "Installed (autoremovable)" making sure to mark them for complete removal. Again, click "apply" and let Synaptic do its thing.

Now you can run Get64bitFlash as detailed [HERE]("http://ubuntuforums.org/showpost.php?p=7904240&postcount=1").  This worked for me both in Jaunty and now in Karmic with my System76 Pangolin (PanP5).

If this doesn't work for you, then I am officially perplexed.  Maybe you could link me to something that is causing your crashes so that I can see if I can reproduce the problem on my system.  However, generally, I've had no problems on YouTube or Hulu.

---

### Post by ctsdownloads on 2009-11-01
I would certainly recommend using the 64bit version assuming you are not using your webcam with Flash at all. [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

That said, because I need to have access with my webcam and the fact that ndiswrapper is and will likely continue to be a mess, I am very happy with Ubuntu 32bit on my PCs. Both of my System76 computers appear to do well with it. Best of all, I am not spending my time fighting with 64bit work-a-rounds for Flash, Air, etc. Life is a lot more pleasant. The key for a quick switch is a dedicated /Home partition. Makes updating easy. This is what worked for me, your mileage may vary. :popcorn:

---

### Post by silvertuna on 2009-11-01
Sound works fine in my Karmic except in Firefox.  No youtube or hulu sound and the controls like pause do not work. I replaced my firefox profile to no avail.  But Firefox sound works on my TV via HDMI connection.  Should i try the flash solution above?  Could this be related to your problems or should i open a new thread?

SiverTuna pan4 64bit Karmic

---

### Post by HotShotDJ on 2009-11-01
> **silvertuna said:**
> Should i try the flash solution above?  Could this be related to your problems or should i open a new thread?

SiverTuna pan4 64bit KarmicIt is possible that your issue is related... BUT, the fact that sound works with HDMI for YouTube and Hulu suggest otherwise.  Here's what I think is going on...

Open your sound preferences by right-clicking on the volume button in your panel and selecting "Preferences."  Now, click on the Hardware Tab.  Select your sound card (Something like "Internal Audio") and then look at the "Profile" drop-down... If my guess is correct, you have it set "Digital Audio (HDMI) Output"  -- try setting it to "Analog Stereo Duplex" and see if that fixes the problem.

Note:  The exact labels may differ on your hardware, but I think the information above should give you an idea of what we are looking for.

---

### Post by silvertuna on 2009-11-02
Thanks, but the output is set on Internal Audio Analog Stereo, not HDMI.  :(

---

### Post by Ed.Corcoran on 2009-11-02
> **HotShotDJ said:**
> Odd.  While I've had the same experience as you with the 32 bit + nspluginwrapper, the 64 bit flash has been great.  What method(s) have you tried for installing it?  Here is what I did:

System -> Administration -> Synaptic Package Manager.  Enter "Flash" in the quick search box and mark anything that is installed for Complete Removal.  Click apply, and then allow Synaptic to do its thing.  After the complete removal is complete, click on the "Status" button in the left panel and check for anything under "Installed (autoremovable)" making sure to mark them for complete removal. Again, click "apply" and let Synaptic do its thing.

Now you can run Get64bitFlash as detailed [HERE]("http://ubuntuforums.org/showpost.php?p=7904240&postcount=1").  This worked for me both in Jaunty and now in Karmic with my System76 Pangolin (PanP5).

If this doesn't work for you, then I am officially perplexed.  Maybe you could link me to something that is causing your crashes so that I can see if I can reproduce the problem on my system.  However, generally, I've had no problems on YouTube or Hulu.
I followed the instructions on that link and Flash is acting the same way it was. Hulu still crashes in the exact same way in both Firefox and Chromium. I also followed these instructions:
[http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
But I got output from that command, so that's not it.

---

### Post by Ed.Corcoran on 2009-11-02
whoops, double post
And I can't figure out how to delete a post. Weird.

---

### Post by ctsdownloads on 2009-11-02
> **HotShotDJ said:**
> Odd.  While I've had the same experience as you with the 32 bit + nspluginwrapper, the 64 bit flash has been great.


Wait, huh? 32bit Flash does not use nspluginwrapper last time I looked - it's supported without it. :lol:

---

### Post by HotShotDJ on 2009-11-02
> **ctsdownloads said:**
> Wait, huh? 32bit Flash does not use nspluginwrapper last time I looked - it's supported without it. :lol:Where did you get that idea?  nspluginwrapper is still a dependency for flashplugin-installer.  See screenshot... I only selected flash-installer, and it pulls in nspluginwrapper with it.  Also, here is the output from a command line:```
$ sudo apt-get install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nspluginwrapper
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer nspluginwrapper
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/217kB of archives.
After this operation, 754kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by Ed.Corcoran on 2009-11-02
I think I've figured out the problem.
At this thread: [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905) they talk about the LAHF instruction set and how some processors don't have it which causes 64 bit flash crash. gunnar123 notes that some processors will say they have it, but really don't. He then gives some quick C code that will tell for sure. I compiled his code and, sure enough, it gave me a segfault. The solution given in that thread is to compile the given C code into a .so and put that in the plugins directory. I did that, but it didn't help.

Any ideas?

---

### Post by Ed.Corcoran on 2009-11-02
I think I fixed it.
I followed these instructions: [https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-February/068347.html](https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-February/068347.html)  and now Hulu works in Firefox. It doesn't work in Chromium, but it doesn't crash either. Which is fine with me. Apparently it's all pulseaudio's fault. ******* pulseaudio. Pulseaudio is probably also the reason that I'm coming down with the flu.

---

### Post by ctsdownloads on 2009-11-02
> **HotShotDJ said:**
> Where did you get that idea?  nspluginwrapper is still a dependency for flashplugin-installer.  See screenshot... I only selected flash-installer, and it pulls in nspluginwrapper with it.  Also, here is the output from a command line:```
$ sudo apt-get install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nspluginwrapper
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer nspluginwrapper
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/217kB of archives.
After this operation, 754kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

Yeah, none of my 32 bit systems are using it as it is used for 64bit systems. It exists in the 32bit repos, but us not needed. Just checked. It exists, but when I ran the install for ubuntu-restricted-extras, it was not installed [nor should it have been]("http://plugindoc.mozdev.org/linux-amd64.html#intro-32bit").  ;)

Just for giggles on my 32bit system, I re-ran sudo apt-get install flashplugin-installer. Nothing about nspluginwrapper was requested. I am assuming you must be speaking of a 64bit install, not a 32bit one?

---

### Post by ctsdownloads on 2009-11-02
> **Ed.Corcoran said:**
> I think I fixed it.
I followed these instructions: [https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-February/068347.html](https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-February/068347.html)  and now Hulu works in Firefox. It doesn't work in Chromium, but it doesn't crash either. Which is fine with me. Apparently it's all pulseaudio's fault. ******* pulseaudio. Pulseaudio is probably also the reason that I'm coming down with the flu.

Sorry to hear about the flu, that stinks. Drink lots of liquids now and make a store run early! Just got over it myself.

---

### Post by HotShotDJ on 2009-11-03
> **ctsdownloads said:**
> I am assuming you must be speaking of a 64bit install, not a 32bit one?Well... yes.  Why else would we have been talking about installing 64 bit flash? ;)

---

### Post by silvertuna on 2009-11-03
> **Ed.Corcoran said:**
> I think I fixed it.
I followed these instructions: [https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-February/068347.html](https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-February/068347.html)  and now Hulu works in Firefox. It doesn't work in Chromium, but it doesn't crash either. Which is fine with me. Apparently it's all pulseaudio's fault. ******* pulseaudio. Pulseaudio is probably also the reason that I'm coming down with the flu.
Didnt work for me.

---

### Post by silvertuna on 2009-11-03
This didnt work either.  Uninstalled Flash in Synaptic.  Extracted and copied the 64-bit libflashplayer.so into the mozilla folders - crashed Firefox.

libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

/usr/lib/mozilla/plugins/libflashplayer.so

or

~/.mozilla/plugins/libflashplayer.so

---

### Post by silvertuna on 2009-11-03
killall pulseaudio did not restore Flash sound.

FYI, Flash sound DOES work when i am HDMI'd to our digital TV.  The sound comes out of the TV speakers.

---

### Post by thomasaaron on 2009-11-03
Try this...

sudo apt-get install libadns1 

This is for the flashplugin-installer, not for the 64-bit version.

---

### Post by silvertuna on 2009-11-03
Ran the command. Did it install Flash or do i need to do something else after installation of libadns1 to install Flash? I dont see any Flash listed in Firefox about/plugins. Here is is the output.

>  
sudo apt-get install libadns1
password for silvertuna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
Suggested packages:
  adns-tools
The following NEW packages will be installed:
  libadns1
0 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
Need to get 62.1kB of archives.
After this operation, 172kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libadns1 1.4-2 [62.1kB]
Fetched 62.1kB in 0s (112kB/s)
Selecting previously deselected package libadns1.
(Reading database ... 275035 files and directories currently installed.)
Unpacking libadns1 (from .../libadns1_1.4-2_amd64.deb) ...
Setting up libadns1 (1.4-2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
silvertuna@ubuntu:~$ 

Now when i try to play youtube i get this -

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

---

### Post by ctsdownloads on 2009-11-03
> **HotShotDJ said:**
> Well... yes.  Why else would we have been talking about installing 64 bit flash? ;)

Sorry, had to double check - no idea why it would asking you for nspluginwrapper then. I can safely say you do not need it, despite what Apt-get is thinking. ;)

ubuntu-restricted-codecs will not install it, but will install Flash 10. That is really weird about flashplugin-installer forcing nspluginwrapper. I'd avoid nspluginwrapper like the plague myself. Nothing but headaches.

---

### Post by HotShotDJ on 2009-11-03
> **ctsdownloads said:**
> Sorry, had to double check - no idea why it would asking you for nspluginwrapper then. I can safely say you do not need it, despite what Apt-get is thinking. ;)If you are using a 32 bit browser on a 64 bit system, then you don't need nspluginwrapper.  But, as far as I know, it is required if one wants to use any 32 bit plugins in a 64 bit browser.  It is possible that I'm wrong, of course.  Where did you find your information?  I can't find anything by googling to support your statement.

---

### Post by ctsdownloads on 2009-11-03
> **HotShotDJ said:**
> If you are using a 32 bit browser on a 64 bit system, then you don't need nspluginwrapper.  But, as far as I know, it is required if one wants to use any 32 bit plugins in a 64 bit browser.  It is possible that I'm wrong, of course.  Where did you find your information?  I can't find anything by googling to support your statement.

It's not documented in the literal sense, as the need is for 64 bit systems. But [this page sheds some light]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") on it, despite not being super clear. 

All it is used for is to make 32 bit plugins work on a 64 bit system, more less.

Please take a look at my screenshots to show you what I am talking about. Note the version of 32bit Ubuntu and the packages shown installed or not installed. ;)

---

### Post by HotShotDJ on 2009-11-03
> **ctsdownloads said:**
> It's not documented in the literal sense, as the need is for 64 bit systems. But [this page sheds some light]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") on it, despite not being super clear.The light shed at that page is that one must use a 64 bit version of Flash in order to use the 64 bit version of Firefox and have Flash without the use of nspluginwrapper.  The other option shown is to install the 32 bit version of Firefox and then install 32 bit plugins for it.  For both those options, nspluginwrapper is not needed.  It is only required for using 32 bit plugins with a 64 bit browser.  There is nothing on that page that suggests (literally or otherwise) anything else.
> **ctsdownloads said:**
> Please take a look at my screenshots to show you what I am talking about. Note the version of 32bit Ubuntu and the packages shown installed or not installed. ;)None of that is relevant.  We are talking about 64 bit systems.  Of course you don't need nspluginwrapper on a 32 bit Ubuntu installation -- the option of using a 64 bit browser is not available in 32 bit Ubuntu.

---

### Post by ctsdownloads on 2009-11-04
> **HotShotDJ said:**
> The light shed at that page is that one must use a 64 bit version of Flash in order to use the 64 bit version of Firefox and have Flash without the use of nspluginwrapper.  The other option shown is to install the 32 bit version of Firefox and then install 32 bit plugins for it.  For both those options, nspluginwrapper is not needed.  It is only required for using 32 bit plugins with a 64 bit browser.  There is nothing on that page that suggests (literally or otherwise) anything else.
None of that is relevant.  We are talking about 64 bit systems.  Of course you don't need nspluginwrapper on a 32 bit Ubuntu installation -- the option of using a 64 bit browser is not available in 32 bit Ubuntu.

The page is fairly obvious in implying that nspluginwrapper is a 64 bit only thing, but that's open to interpretation I guess. ;)

I must have totally missed that. As for this entire debate being unneeded, I was under the strong impression that you were talking about 32bit Ubuntu as you can see below, sorry for the confusion.

> 
[QUOTE]Originally Posted by ctsdownloads View Post
Wait, huh? 32bit Flash does not use nspluginwrapper last time I looked - it's supported without it.
Where did you get that idea? nspluginwrapper is still a dependency for flashplugin-installer. See screenshot... I only selected flash-installer, and it pulls in nspluginwrapper with it. Also, here is the output from a command line:[/QUOTE]

You can see above, where the confusion started for me. Based on that statement, I could only conclude you realized I was saying that 32 bit Ubuntu does not need nspluginwrapper for Flash. Sorry you misunderstood. :-s

You can see the leap though, from my perspective, where confusion is bound to happen.

Going from:
> Where did you get that idea? nspluginwrapper is still a dependency for flashplugin-installer.


On to:
> Of course you don't need nspluginwrapper on a 32 bit Ubuntu installation -- the option of using a 64 bit browser is not available in 32 bit Ubuntu.

Is bound to leave me scratching my head a little. At any rate, yes, we clearly agree that Ubuntu 32 bit has NO NEED to use nspluginwrapper for Flash. :)

Anywho, get well from that flu and best of luck!

---

