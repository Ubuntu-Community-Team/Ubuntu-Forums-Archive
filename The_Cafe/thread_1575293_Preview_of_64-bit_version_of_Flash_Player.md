---
title: "Preview of 64-bit version of Flash Player"
date: 2010-09-15
forum: The Cafe
---

### Post by itreius on 2010-09-15
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by howefield on 2010-09-15
Nice, thanks for that.

---

### Post by j.bell730 on 2010-09-15
Ah! Awesome. Thank you very much!

---

### Post by TheLions on 2010-09-15
Thx!

---

### Post by 101011010010 on 2010-09-15
Thank you. :popcorn:

---

### Post by Half-Left on 2010-09-15
Just tried it and it's much better. I uninstalled the Ubuntu 32bit wrapper version.

easy way:

Put the libflashplayer.so in ~/.mozila/plugins (make the directory if you don't have it and yes Chrome will work).

---

### Post by FuturePilot on 2010-09-15
Awesome!

---

### Post by blur xc on 2010-09-15
> **Half-Left said:**
> Just tried it and it's much better. I uninstalled the Ubuntu 32bit wrapper version.

easy way:

Put the libflashplayer.so in ~/.mozila/plugins (make the directory if you don't have it and yes Chrome will work).

I just saw this on webup8 earlier today...   [http://www.webupd8.org/2010/09/adobe-finally-releases-new-adobe-flash.html](http://www.webupd8.org/2010/09/adobe-finally-releases-new-adobe-flash.html)

You can also stick it in /usr/lib/mozilla/plugins to make it available to all users.

Has anyone tried doing any benchmarks?

BM

---

### Post by kerry_s on 2010-09-15
> **itreius said:**
> [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

works fine for me so far.

---

### Post by tjeremiah on 2010-09-15
it still freezes sometimes when I go into fullscreen mode (meaning no frame is moving) and I have to exit and return to fullscreen for it to play but other than that, im glad to see a 64bit flash anything right now.

---

### Post by blur xc on 2010-09-15
Well- I googled "flash benchmark" and ran the first test I found, before and after...

[http://www.newgrounds.com/portal/view/465908](http://www.newgrounds.com/portal/view/465908)

before my score was 12239, and after was 15961 and it appeared to use less cpu.  It's hard to say because I've got a dual core cpu, and when one bar rises, the other drops, so how do you average?

I'll try it on some other 64bit computers in the house and see if it's a consistent improvement.

update- 
tried it out on my son's low spec laptop.  In Vista (32bit, I think) it scored 10445.  The 32bit ubuntu plugin scored 6194, and the new 64bit plugin scored 8205...  It's a step in the right direction...


BM

---

### Post by empty_spaces on 2010-09-15
Can anyone confirm if Hulu works with this?

---

### Post by marshmallow1304 on 2010-09-15
> **empty_spaces said:**
> Can anyone confirm if Hulu works with this?

Yes, Hulu works for me in Firefox on Gentoo.

---

### Post by kerry_s on 2010-09-15
hulu works fine here to.

---

### Post by sandyd on 2010-09-16
FINALLY!! will be updating flash installer w/ this tomorow. thnks!!

---

### Post by v1ad on 2010-09-16
Nice && thanks :D, nice to see flash moving into the proper direction.

---

### Post by Quake on 2010-09-16
So this 64 bit flash works better than the nspluginwrapper version?

---

### Post by formaldehyde_spoon on 2010-09-16
This is a nice little bonus, thanks! 
As long as it doesn't turn out to be less stable I'll use this instead of v.10 64 bit with the old security hole.

For the curious: they aren't calling Square version 10.1, nor 10.2 or whatever comes next, but it sounds like a close cousin of 10.1:
> **Is Flash Player &#8220;Square&#8221; available for all major operating systems?**
Yes. Flash Player &#8220;Square&#8221; is available for all versions  of Windows, Mac OS, and Linux platforms supported by Flash Player 10.1.  In addition, it includes native support for 64-bit browsers on Windows,  Mac OS, and Linux.

---

### Post by Irony on 2010-09-16
No sure which section to put this but as the title says;

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

For all those still faffing with 32 bit flash on 64 bit then this might be the answer. Its a preview release so expect to manually update regularly.

I've tried it on a few of my usual sites and so far so good.

To check the version of install go to;

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

or type in the address bar;

```
about:plugins
```

---

### Post by Grenage on 2010-09-16
Good spot, thanks for the heads-up.

---

### Post by cascade9 on 2010-09-16
Could adobe stop sodding around x86_64 linux users?....1st there is a 'beta' 64bit flash, then they pull it, then a few weeks later there is a 'preview' 64bit flash....I wonder if they will do the same thing when it comes to 'release' time? 

I wish flash would just die already. Its the biggest PITA on 64bit systems, by far. When its installed, it works well, but this back and forth is frustrating. Doing things manually isnt my idea of fun anyway, is one of the reasons why I got rid of windows.

---

### Post by muteXe on 2010-09-16
Is there a way to live without flash?
I've unistalled it from one of my machines in the hope that I could, for example, download a youtube vid onto my machine and watch it locally.  I have had no joy yet though :(

---

### Post by Grenage on 2010-09-16
> **cascade9 said:**
> Could adobe would stop sodding around x86_64 linux users?....1st there is a 'beta' 64bit flash, then they pull it, then a few weeks later there is a 'preview' 64bit flash....I wonder if they will do the same thing when it comes to 'release' time? 

I wish flash would just die already. Its the biggest PITA on 64bit systems, by far. When its installed, it works well, but this back and forth is frustrating. Doing things manually isnt my idea of fun anyway, is one of the reasons why I got rid of windows.

I think flash is over-used, but at least they had a reasonable reason for revoking the beta client.

---

### Post by philinux on 2010-09-16
Moved to the Cafe.

Any 64 bit users with the 32 bit plugin can just copy the new libflashplayer.so to ~/.mozilla/plugins restart FF and it will pick up the 64 bit version.

---

### Post by Blackra1n on 2010-09-16
Good news!

---

### Post by Irony on 2010-09-16
> **muteXe said:**
> Is there a way to live without flash?
I've unistalled it from one of my machines in the hope that I could, for example, download a youtube vid onto my machine and watch it locally.  I have had no joy yet though :(
There's gnash but it only works on a few sites;

[http://www.workswithu.com/2010/09/15/testing-gnash-0-8-8-on-ubuntu/](http://www.workswithu.com/2010/09/15/testing-gnash-0-8-8-on-ubuntu/)

---

### Post by muteXe on 2010-09-16
Cheers Irony.
It annoys me to think we're so dependant on flash.

---

### Post by MooPi on 2010-09-16
It even works with Hulu which the old version of 64 bit did not. Hooorah !

---

### Post by Untitled_No4 on 2010-09-16
There is no need to install and keep it updated manually since you can use SevenMachines' PPA ([https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)). It still has the old version of 64 bit Flash but I emailed SevenMachines and he/she confirmed that it's going to be kept updated.

---

### Post by Calash on 2010-09-16
> **philinux said:**
> Moved to the Cafe.

Any 64 bit users with the 32 bit plugin can just copy the new libflashplayer.so to ~/.mozilla/plugins restart FF and it will pick up the 64 bit version.

This is something that forever confuses me.  There are so many plugin locations depending on the flavor and version.  Do you know if this location will also work with Swiftfox?  Googling this is a nightmare because you get a ton of different results that sometimes work and sometimes don't/

I found where I could drop the plugin for Chrome...at least I found one in /var/lib or something like that.

---

### Post by MooPi on 2010-09-16
I have kept a 32 bit machine running just for sites like Hulu that did not support the 64 bit version. I'm now FREEEEE :-)

---

### Post by ubunterooster on 2010-09-16
> **muteXe said:**
> Is there a way to live without flash?
I've unistalled it from one of my machines in the hope that I could, for example, download a youtube vid onto my machine and watch it locally.  I have had no joy yet though :(
Try this: 
**[       FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/")            by [lovinglinux]("https://addons.mozilla.org/en-US/firefox/user/4352153/")       **

                                               [                  Add to Firefox       ]("https://addons.mozilla.org/en-US/firefox/downloads/latest/161869/addon-161869-latest.xpi?src=search")       
   
  
                      Rated 5 out of 5 stars     [                       **14 reviews**]("https://addons.mozilla.org/en-US/firefox/addon/161869/#reviews")             
                              **7,049** weekly downloads

---

### Post by formaldehyde_spoon on 2010-09-16
**This**(here, location of the post you're reading) thread has a much better title, but it's a little slow ;) : [http://ubuntuforums.org/showthread.php?t=1575293](http://ubuntuforums.org/showthread.php?t=1575293)
Perhaps a merge is in order?  > **cascade9 said:**
> Could adobe would stop sodding around x86_64 linux users?....1st there is a 'beta' 64bit flash, then they pull it, then a few weeks later there is a 'preview' 64bit flash....I wonder if they will do the same thing when it comes to 'release' time? 

I wish flash would just die already. Its the biggest PITA on 64bit systems, by far. When its installed, it works well, but this back and forth is frustrating. Doing things manually isnt my idea of fun anyway, is one of the reasons why I got rid of windows.
I'm looking forward to an html5-only life too, but I have to say flash in 64 bit Ubuntu has been incredibly easy for me: one single file in one single location, and never even the slightest hiccup.  Really can't think of anything easier!

---

### Post by formaldehyde_spoon on 2010-09-16
double post, sorry.

---

### Post by philinux on 2010-09-16
Threads Merged.

---

### Post by blueturtl on 2010-09-16
Fantastic. I was having full screen play issues with the previous 64-bit version and then heard Adobe was suspending the 64-bit player altogether. Now I get to install a new version and video playback is flawless in full screen mode, as it should be.

---

### Post by lovinglinux on 2010-09-16
> **ubunterooster said:**
> Try this: 
**[       FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/")            by [lovinglinux]("https://addons.mozilla.org/en-US/firefox/user/4352153/")       **

                                               [                  Add to Firefox       ]("https://addons.mozilla.org/en-US/firefox/downloads/latest/161869/addon-161869-latest.xpi?src=search")       
   
  
                      Rated 5 out of 5 stars     [                       **14 reviews**]("https://addons.mozilla.org/en-US/firefox/addon/161869/#reviews")             
                              **7,049** weekly downloads

Thanks for the referral. FlashVideoReplacer is becoming really popular \\:D/. Well, at least is the most popular extension I develop, followed by FLASH-AID :)

I have just released version 1.0.12 of FLASH-AID extension for Firefox, which supports the new 64bit version of flash. It detects your browser architecture, removes conflicting plugins, including the 32bit from the repositories, and install the latest flash version. It also allows to remove flash completely and install the 32bit if the 64bit doesn't work well for you.

You can get it from my blog...

[http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)

...from github...

[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)

..or from Mozilla (requires account until Mozilla approves the new version):

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)

---

### Post by lovinglinux on 2010-09-16
EDIT: nevermind

---

### Post by sandyd on 2010-09-16
> **lovinglinux said:**
> Thanks for the referral. FlashVideoReplacer is becoming really popular \\:D/. Well, at least is the most popular extension I develop, followed by FLASH-AID :)

I have just released version 1.0.12 of FLASH-AID extension for Firefox, which supports the new 64bit version of flash. It detects your browser architecture, removes conflicting plugins, including the 32bit from the repositories, and install the latest flash version. It also allows to remove flash completely and install the 32bit if the 64bit doesn't work well for you.

You can get it from my blog...

[http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)

...from github...

[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)

..or from Mozilla (requires account until Mozilla approves the new version):

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)

wow. your fast. imm still at work trying to figure out why people dont back up the work and cry when their stuff mysteriously vanishes, evene when I said that their computer needed a replacement hard disk. now, their wasting more time than it would have taken for me to replace the hd... and im going to be putting the beta version of my installer  into stable, so users get some form of a progress dialog.

---

### Post by lovinglinux on 2010-09-16
> **sandyd said:**
> wow. your fast. 

:)

The truth is that the extension was already prepared to support 64bit again once Adobe released it, so I just needed to uncomment a few lines and add a couple more ;)

---

### Post by sandyd on 2010-09-16
> **lovinglinux said:**
> :)

The truth is that the extension was already prepared to support 64bit again once Adobe released it, so I just needed to uncomment a few lines and add a couple more ;)
mine was too, but I had done a complete revamp of the installer, so I had to redo the 32bit beta button functions.

yikes! :p

but everythings working now ;)

---

### Post by lovinglinux on 2010-09-16
> **sandyd said:**
> mine was too, but I had done a complete revamp of the installer, so I had to redo the 32bit beta button functions.

yikes! :p

but everythings working now ;)

Cool. BTW, I'm also using git now and I'm loving it. Much simpler than my previous svn setup.

---

### Post by kerry_s on 2010-09-16
anyone able to type in text fields?
for example: i can't sign in to pandora radio, cause it won't input the text.

---

### Post by drs305 on 2010-09-16
> **kerry_s said:**
> anyone able to type in text fields?
for example: i can't sign in to pandora radio, cause it won't input the text.

Yes, I can type in text boxes. I typed an artist's name and it worked. I don't have an account, but I could *type* in the login boxes.

---

### Post by kerry_s on 2010-09-16
> **drs305 said:**
> Yes, I can type in text boxes. I typed an artist's name and it worked. I don't have an account, but I could *type* in the login boxes.

thanks, maybe an epipany browser problem.
i found i could copy & paste, so i just put my sign in info in the location bar & copied it to the text fields.

so i got my music, i'm happy. :D

edit: installed another browser & it works, so its a epiphany browser problem.

---

### Post by BigCityCat on 2010-09-16
I have a question.

If I am running a 32bit browser does this 64bit flash still run as 64bit? I have the plugin installed in usr/lib/mozzila plugins

I am assuming a 32 bit browser was installed with my installation even though I have the 64bit os because I didn't think Ubuntu installed a 64bit version of Firefox.

---

### Post by kerry_s on 2010-09-16
> I am assuming a 32 bit browser was installed with my installation even though I have the 64bit os because I didn't think Ubuntu installed a 64bit version of Firefox.

if your os is 64bit, then your browser is 64bit
unless
you maually installed a 32bit browser

---

### Post by lovinglinux on 2010-09-16
> **BigCityCat said:**
> If I am running a 32bit browser does this 64bit flash still run as 64bit? I have the plugin installed in usr/lib/mozzila plugins

It won't run.

---

### Post by BigCityCat on 2010-09-16
> **kerry_s said:**
> if your os is 64bit, then your browser is 64bit
unless
you maually installed a 32bit browser

and through the mozilla repositories for Firefox 4 beta?

---

### Post by kerry_s on 2010-09-16
> **BigCityCat said:**
> and through the mozilla repositories for Firefox 4 beta?

click "help-> about" in browser & see what it says.

---

### Post by lovinglinux on 2010-09-16
> **BigCityCat said:**
> and through the mozilla repositories for Firefox 4 beta?

They install the 64bit too.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by sandyd on 2010-09-16
Just tried the new version. Much better.

Less lagging. I can play thing thing arena 3 now *blush*

Sound finally synced with video.

thanks adobe :). Just please don't pull this version.

---

### Post by renkinjutsu on 2010-09-17
You'll have to update the plugin yourself every once in a while. I'm assuming it's not yet in the repository, so i wrote a script that fetches the tarball and extracts it into the /usr/lib directory..

You may then want to symlink it to the plugins folder of your browsers

```
#!/bin/bash

URI=$(curl -s "http://labs.adobe.com/downloads/flashplayer10.html" | grep Download\ plug-in\ for\ 64-bit\ Linux | grep -o 'http..............................................................................................................................')
URI=${URI%\"*}
wdir=/tmp
flashfile="${wdir}/flashplayer.tar.gz"

wget ${URI} -O ${flashfile}
tar xzf ${flashfile} -C /usr/lib

rm ${flashfile}
```

---

### Post by Foxcow on 2010-09-19
Hell yeah!


I too can confirm that hulu works in browser and that youtube videos will play in HD in full screen without a hiccup.

Its about time Adobe!

---

### Post by Excedio on 2010-09-20
Can you guys please try out the following?:

[My company's speedtest]("http://zvrs.com/customer-care/speed-test-ip-address")

[My ISP's speedtest]("http://speedtest.tampabay.rr.com/")

Also, any wordpress users out there? If yes, are you having a problem seeing your blog stats? My dashboard just says "Loading..." and the Blog Stats page just has a spinning "W" wheel.

---

### Post by Foxcow on 2010-09-20
> **Excedio said:**
> Can you guys please try out the following?:

[My company's speedtest]("http://zvrs.com/customer-care/speed-test-ip-address")

[My ISP's speedtest]("http://speedtest.tampabay.rr.com/")

Also, any wordpress users out there? If yes, are you having a problem seeing your blog stats? My dashboard just says "Loading..." and the Blog Stats page just has a spinning "W" wheel.



Thats odd.  Neither of them worked for me. :confused:

---

### Post by Excedio on 2010-09-20
> **Foxcow said:**
> Thats odd.  Neither of them worked for me. :confused:

Same here. My company's speedtest worked before using the new flash plugin. Hmmm...

Is anyone able to use them properly?

---

### Post by FuturePilot on 2010-09-20
Must be a thing with speed tests. This one doesn't work either. [http://www.speakeasy.net/speedtest/]("http://www.speakeasy.net/speedtest/")

---

### Post by Calash on 2010-09-20
I can confirm that none of the speed tests work for me since applying the latest plugin.

---

### Post by Cavsfan on 2010-09-20
I could not find the old thread everyone was complaining that Adobe had dropped 64 bit flash support.
But, I just checked my flash version (I am running 32 bit flash on my 64 bit machine) and it is outdated.
I found this page to download what they are calling the **Flash Player "Square" Preview Release**.
It is referred to as a "Preview Release" and it says it is not recommended for production systems or for any mission-critical work.
This page has the **"Square" preview** for both 32 bit and 64 bit flash to download. 
[[COLOR=blue]_http://labs.adobe.com/downloads/flashplayer10.html_[/COLOR]]("http://labs.adobe.com/downloads/flashplayer10.html")
I am going to "go for it".

---

### Post by BigCityCat on 2010-09-20
your about a week late, a lot of people are already using it. It should have a link to the download on that page you linked to.

---

### Post by BigCityCat on 2010-09-20
Here is a link to the discussion with instructions to install.
]
[http://ubuntuforums.org/showthread.php?t=1575293](http://ubuntuforums.org/showthread.php?t=1575293)

---

### Post by Foxcow on 2010-09-20
> **Calash said:**
> I can confirm that none of the speed tests work for me since applying the latest plugin.



Same here...

---

### Post by bodhi.zazen on 2010-09-20
Moved to the café.

What makes you think they ever stopped development ? They stopped development of the old flawed driver and, at the same time, announced they were working on a new driver.

---

### Post by v1ad on 2010-09-20
a little over a week late.

---

### Post by Cavsfan on 2010-09-20
Thanks for moving my post to here! :P Yes, I am just noticing that I am a week late.

I see the latest version for Linux Firefox is 10.1.85.3 while it installed version 10,2,161,22 :P
Youtube video works great. My ISP's speedtest didn't work, but speedtest.net did work very well.
I have Noscript installed and I thought maybe that was stopping my speedtest, but I guess not.

About time we got some 64 bit flash! :guitar:

---

### Post by Cavsfan on 2010-09-20
> **BigCityCat said:**
> Here is a link to the discussion with instructions to install.
]
[http://ubuntuforums.org/showthread.php?t=1575293](http://ubuntuforums.org/showthread.php?t=1575293)

You linked to this same thread. But, don't feel bad I had started a new thread and it was moved here.
All is good though! :)

---

### Post by Cavsfan on 2010-09-20
One thing though, I look at about : plugins and see 2 versions of flash installed. One is apparently the old 32 bit one I was using.
Should I remove it? I searched and found this
[COLOR="Blue"]/usr/share/ubufox/plugins/npwrapper.libflashplayer.so[/COLOR]
and [COLOR="Blue"]/var/lib/flashplugin-installer/npwrapper.libflashplayer.so[/COLOR]
Can I just delete these or what would I need to do?
Thanks!

---

### Post by FuturePilot on 2010-09-20
> **Cavsfan said:**
> One thing though, I look at about : plugins and see 2 versions of flash installed. One is apparently the old 32 bit one I was using.
Should I remove it? I searched and found this
[COLOR="Blue"]/usr/share/ubufox/plugins/npwrapper.libflashplayer.so[/COLOR]
and [COLOR="Blue"]/var/lib/flashplugin-installer/npwrapper.libflashplayer.so[/COLOR]
Can I just delete these or what would I need to do?
Thanks!

Uninstall the flashplugin-installer or flashplugin-nonfree package.

---

### Post by Cavsfan on 2010-09-20
> **FuturePilot said:**
> Uninstall the flashplugin-installer or flashplugin-nonfree package.

It was the flashplugin-installer D'oh!
Thanks!

---

### Post by Excedio on 2010-09-20
> **Cavsfan said:**
> Thanks for moving my post to here! :P Yes, I am just noticing that I am a week late.

I see the latest version for Linux Firefox is 10.1.85.3 while it installed version 10,2,161,22 :P
Youtube video works great. My ISP's speedtest didn't work, but speedtest.net did work very well.
I have Noscript installed and I thought maybe that was stopping my speedtest, but I guess not.

About time we got some 64 bit flash! :guitar:


I can confirm that speedtest.net works for me also. Strange though..my company uses speedtest.net re-skinned.

---

### Post by lovinglinux on 2010-09-21
Next major thread about flash 64bit will be something like..."critical vulnerability...take over after a crash...blah,blah,blah...download new version...not available for 64bit" :)

---

### Post by bodhi.zazen on 2010-09-21
> **lovinglinux said:**
> Next major thread about flash 64bit will be something like..."critical vulnerability...take over after a crash...blah,blah,blah...download new version...not available for 64bit" :)

Hopefully the next thread will read 

Opensoure alternate to flash.

There are several options, they work with varied success. I have no luck with webkinz (for the children)

[http://sourceforge.net/apps/trac/lightspark](http://sourceforge.net/apps/trac/lightspark)

[https://launchpad.net/lightspark](https://launchpad.net/lightspark)

There is also gnash.

Chromium dev

> Developers can download the Chrome developer channel version with Flash built in [here]("http://dev.chromium.org/getting-involved/dev-channel"). To enable the built-in version of Flash, run Chrome with the --enable-internal-flash command line flag.

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

---

### Post by jmszr on 2010-09-21
Here is a link to an interesting article/tutorial on open source alternatives (Gnash & Lightspark) to flash: [http://www.linux.com/learn/tutorials/360557:weekend-project-open-source-alternatives-to-adobe-flash-on-linux](http://www.linux.com/learn/tutorials/360557:weekend-project-open-source-alternatives-to-adobe-flash-on-linux) .

---

### Post by Foxcow on 2010-10-19
All of a sudden, I can't view Hulu in the browser anymore.  Anyone else experience this suddenly?

---

### Post by empty_spaces on 2010-10-19
Same here. Hulu works on my 32bit install, but 64bit flash just gives a blank screen, no messages.

---

### Post by DougieFresh4U on 2010-10-19
Hulu seems to be working ok on my 64 bit Maverick within browser.

---

### Post by CharlesA on 2010-10-19
Doesn't the 64-bit version of 10.10 use 32-bit flash?

---

### Post by Half-Left on 2010-10-19
> **CharlesA said:**
> Doesn't the 64-bit version of 10.10 use 32-bit flash?

Yep, with nspluginwrapper to make it function.

---

### Post by empty_spaces on 2010-10-19
> **CharlesA said:**
> Doesn't the 64-bit version of 10.10 use 32-bit flash?

I am using the 64bit flash preview version (as mentioned in the thread title) and Hulu isn't working right now (it was working a few days ago with the same setup)

---

### Post by Spr0k3t on 2010-10-19
I don't use Hulu much, but it's also not working on this end.  64bit flash preview.  The 32bit wrapper is working for the most part though.

---

### Post by Foxcow on 2010-10-19
I wonder if Hulu made a change to something because it was working beautifully for the first bunch of days after both versions of flash squared were released.

---

### Post by Cavsfan on 2010-10-19
I did a clean install of desktop 64 bit Maverick since I had tried the 64 bit Preview version and it came with the latest 32 bit flash version and of course Hulu works great.

---

### Post by tjeremiah on 2010-10-19
its a good thing HULU DESKTOP works fine.

---

### Post by Foxcow on 2010-11-13
It looks like Hulu is back again and speedtest.net works as well.  Speakeasy still does not work.

---

### Post by Cavsfan on 2010-11-14
> **Foxcow said:**
> It looks like Hulu is back again and speedtest.net works as well.  Speakeasy still does not work.

If you are using the 64-bit Flash Player "Square" Preview Release, I believe it has a security issue. 
I had installed NoScript on Firefox and had the 64 bit flash version installed. I went to this site to see how secure my browser was:
[[color=blue]_https://panopticlick.eff.org/_[/COLOR]](https://panopticlick.eff.org/)
And in most places at the bottom it mentioned the version of java I had and I know you will probably think I am crazy, but I believe the 64 bit preview 
flash version caused it to display the java version. 

I have since switched to the 32 bit version and it now says "no javascript" in a lot of places at the bottom of that site and 
this at the top "Within our dataset of several million visitors, only **one in 125,992 browsers have the same fingerprint as yours."**

You could try it yourself.

---

### Post by Foxcow on 2010-11-14
> **Cavsfan said:**
> If you are using the 64-bit Flash Player "Square" Preview Release, I believe it has a security issue. 
I had installed NoScript on Firefox and had the 64 bit flash version installed. I went to this site to see how secure my browser was:
[[color=blue]_https://panopticlick.eff.org/_[/COLOR]](https://panopticlick.eff.org/)
And in most places at the bottom it mentioned the version of java I had and I know you will probably think I am crazy, but I believe the 64 bit preview 
flash version caused it to display the java version. 

I have since switched to the 32 bit version and it now says "no javascript" in a lot of places at the bottom of that site and 
this at the top "Within our dataset of several million visitors, only **one in 125,992 browsers have the same fingerprint as yours."**

You could try it yourself.


I'll definitely have to take a look at that when I get more time.  Thanks for the heads up.

---

### Post by Cavsfan on 2010-11-14
> **Foxcow said:**
> I'll definitely have to take a look at that when I get more time.  Thanks for the heads up.
You are welcome and everything works great on the 32 bit version - Youtube, Hulu and that's all I have tried.

---

