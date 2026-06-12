---
title: "Firefox clone or better alternative"
date: 2009-10-21
forum: The Cafe
---

### Post by infestor on 2009-10-21
i use ubuntu jaunty x64 and firefox from repos...i have been suffering from its slowness for almost years...i also have xp 32 bit installed on my PC on the side...firefox in ubuntu is significantly slower than it is on xp (i disregard flash playing, a major issue for all browser i guess on linux)

i tried epiphany but the user interface is quite different (ctrl+enter doesnt append [www...com]("http://www...com") and middle click you cannot scroll etc.)

arora refused to work

flock has the same performance as firefox

opera's presto layout engine just sucks

so is there an alternative you guys can suggest me or a "magic" trick for firefox that i had not known?

---

### Post by RiceMonster on 2009-10-21
Chromium.

---

### Post by hoppipolla on 2009-10-21
> **RiceMonster said:**
> Chromium.

or Chrome, but otherwise 100% seconded :)

I only really use Firefox and Arora as backup browsers, Chrome and Chromium are for most of my web browsing :)

---

### Post by Dougie187 on 2009-10-21
> **hoppipolla said:**
> or Chrome, but otherwise 100% seconded :)

I only really use Firefox and Arora as backup browsers, Chrome and Chromium are for most of my web browsing :)

Same with me. Chromium/Chome are both awesome browsers with little-to-no problems.

---

### Post by infestor on 2009-10-21
didnt know that chrome run on linux

---

### Post by jeremyswalker on 2009-10-21
Did you try Swiftfox? Or doing a search for "Firefox tweaks"? Or, as everyone else said, there is always Chrome.

---

### Post by johnboy1313 on 2009-10-21
chrome is good, seamonkey is ok too

---

### Post by tjwoosta on 2009-10-21
> i tried epiphany but the user interface is quite different (ctrl+enter doesnt append [www...com](www...com) and middle click you cannot scroll etc.)

Really? Thats strange I use crtl+enter all the time in epiphany and it works fine here.  Also there is a plugin for autoscroll  (the midlle click scroller thing)

---

### Post by Ric_NYC on 2009-10-21
> **infestor said:**
> i use ubuntu jaunty x64 and firefox from repos...**i have been suffering from its slowness for almost years**...


Chromium is the answer for your suffering!
Hallelujah!

---

### Post by infestor on 2009-10-21
ok...how do i install chromium for jaunty x64 natively?

---

### Post by Firestem4 on 2009-10-21
> **jeremyswalker said:**
> Did you try Swiftfox? Or doing a search for "Firefox tweaks"? Or, as everyone else said, there is always Chrome.

I tried swiftfox and I liked it, however it stopped working correctly for me for some reason. 

Another great alternative is swiftweasel. It's pretty much like swiftfox except its all open-source (swiftfox has some closed-sourced additions made by the author, take it as you will. I don't have a big problem with it, again it just stopped working for me lol).

Anywho, Both swiftfox and swiftweasel have packages for different CPU architectures, X86, AMD64, i386/i686 and etc.

Swiftfox has a .deb installer and a repo I believe. To install swiftweasel, literally drag the folder from the tarball anywhere you want it to reside and launch it from there.

---

### Post by hoppipolla on 2009-10-21
Man I wish I could remember lol

*hunts around the interwebs... I KNOW I did this fine... o.O

Ok well this will work for Chromium - add these two repos to Synaptic:

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

and then execute this command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5

```

I'll see if I can work out how to install Chrome as well o.O


EDIT -- God knows man, try adding this repo for Chrome and see if it pops up in Synaptic (it's impossible to find it on the Chrome pages as far as I can tell but this is the repo I have on my machine):

deb [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb) stable main

---

### Post by infestor on 2009-10-21
> **hoppipolla said:**
> Man I wish I could remember lol

*hunts around the interwebs... I KNOW I did this fine... o.O

Ok well this will work for Chromium - add these two repos to Synaptic:

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

and then execute this command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5

```I'll see if I can work out how to install Chrome as well o.O

i cannot gey the key :( request times out

---

### Post by hoppipolla on 2009-10-21
> **infestor said:**
> i cannot gey the key :( request times out

Yeah it's taking ages on here too.  I think this is the address: [http://keyserver.ubuntu.com:11371/pks/lookup?search=0xFBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0xFBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5&op=index)

I wish I knew how to just give you a copy of the key from here o.O

---

### Post by hoppipolla on 2009-10-21
yay the Chromium key! I have it!

Here it is:

> Public Key Server -- Get ``0x5a9bf3bb4e5e17b5 ''

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESaSPtAEEAK1nJtoDZ0ewpOOf0ET6Vp28LqO9mB4ubWjzXyRSbiha5pCvnnSIU1K+7Gzb
t3r0iUV9eKLUmf8pqfF/9kwsoqFqFSCjp+XjUzXsEChcGBWvyfGdTX8ClFfwNxSVLvGSqmdX
gZhs0F8tQB0lPWHGy3VvEt7wG/VHqpcOYpdNYRqxABEBAAG0IExhdW5jaHBhZCBQUEEgZm9y
IGNocm9taXVtLWRhaWx5iEYEEBECAAYFAknOwV0ACgkQ9rPTxuzZSv0f2QCeLjemEkq5tYjI
xtFpw3F11szeakYAoKsBZcl3Az08cYEd9UNZjQE1j4YtiEYEEBECAAYFAknS5Z8ACgkQrZOR
ep7Yx+qZ8wCfZYBABDkYO0Ulrivpxn6hARmgLxEAn0SeWaGjVQ4UE3zpNESguf+t9K1xiLYE
EwECACAFAkmkj7QCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRBam/O7Tl4XtV/2BACs
/RTpEWB/NUlluJmp1e6iFoyyfbT+HOD3hg35aQMzbdcmijsAiY9MvIfZ0YKWyqNUdGpDj5n0
bUNO0IcvKBBkOn5o4CiBsMp4DJHdrgJU4S00nAJK00E8I/yAv+x4C9uOacW3yrzSHs7Hv/vG
6Z1Jh+1JrabK13hdhwOL8+aY6Q==
=9P6G
-----END PGP PUBLIC KEY BLOCK-----

Just bung that in a text file and import it! (I'm sure you knew that :) )

---

### Post by infestor on 2009-10-21
[s]ok i managed to get the key and install chromium *woop*

but one bothersome question more: how can i not see the rss button the addressbar?[/s]

---

### Post by infestor on 2009-10-21
ok i managed to get the key and install chromium *woop*

but one bothersome question more: how can i not see the rss button on the addressbar?

also middle click autoscroll doesnt appear!?

---

### Post by NoaHall on 2009-10-21
Or if you use the chromium install script, it'll install the repos + key for you. See code.


```
#!/bin/bash
unset basehttp
unset latest
cd /tmp/
rm LATEST* > null
export basehttp=http://build.chromium.org/buildbot/snapshots/chromium-rel-linux
echo "Downloading latest version information..."
wget --quiet $basehttp/LATEST

if [ -f $HOME/chrome-linux/LATEST ]
  then
  echo "Installed dev version is `cat $HOME/chrome-linux/LATEST`"
   else
   echo "Cannot get Google Chromium version - not installed?"
fi

echo "Latest Chromium Dev version is `cat /tmp/LATEST`"

if [ $((`cat /tmp/LATEST`)) -eq $((`cat $HOME/chrome-linux/LATEST`)) ]
then
   echo " You have the latest version of Chromium Browser"
   exit 0
else

read -p "Press any key to continue installation or Ctrl-C to abort"
export latest=`cat /tmp/LATEST`
echo "Downloading desktop icon image..."
wget --quiet http://upload.wikimedia.org/wikipedia/commons/c/c0/Chromium_Icon.png
echo "Downloading latest Chromium build..."
wget --no-verbose $basehttp/$latest/chrome-linux.zip && rm -rf $HOME/chrome-linux/

mkdir -p ~/.config/chromium/
mkdir -p ~/.config/chromium/Default/
mkdir -p ~/.config/chromium/Default/User\ Scripts

wget -qO ~/.config/chromium/Default/User\ Scripts/AdSweep.user.js http://www.adsweep.org/AdSweep.user.js

echo "Unpacking new version..."
unzip -o -qq /tmp/chrome-linux.zip -d $HOME/

#echo "Creating plugins folder and linking flashplugin..."
#
#if [ -d $HOME/chrome-linux/plugins ]
#  then
#      echo "The plugin folder already exists! It will be replaced."
#      rm -rf $HOME/chrome-linux/plugins/
#      ln -s /usr/lib/mozilla/plugins/ $HOME/chrome-linux/
#  else
#      mkdir $HOME/chrome-linux/plugins
#      ln -s /usr/lib/mozilla/plugins/ $HOME/chrome-linux/
#fi
              

echo "Creating links..."
if [ -d $HOME/bin/ ]
  then
	echo "The bin folder already exists!"
  else
  mkdir $HOME/bin
fi

if [ -d $HOME/bin/icons ]
  then
	echo "The bin/icons folder already exists!"
  else
  mkdir $HOME/bin/icons
fi

if [ -L $HOME/bin/chromium-linux ]
  then
	echo "The /bin/chrome link already exists! it will be replaced."
	rm $HOME/bin/chromium-linux > null
	ln -s $HOME/chrome-linux/chrome $HOME/bin/chromium-linux
  else
  ln -s $HOME/chrome-linux/chrome $HOME/bin/chromium-linux
fi

if [ -f $HOME/bin/icons/Chromium_Icon.png ]
  then
	echo "The icon image already exists!"
	rm /tmp/Chromium_Icon.png
  else
  mv /tmp/Chromium_Icon.png $HOME/bin/icons/
fi

echo "Creating menu link"

echo -e "#!/usr/bin/env xdg-open\n
[Desktop Entry]\r
Encoding=UTF-8\r
Version=1.0\r
Name=Chromium Linux\r
Comment=Browse the WWW\r
Type=Application\r
Exec="`echo $HOME`/chrome-linux/chrome --enable-plugins --enable-user-scripts"\r
Terminal=false\r
Categories=Network\r
Name[en_US]=Chromium Browser\r
Comment[en_US]=Browse the WWW\r
Icon[en_US]="`echo $HOME`/bin/icons/Chromium_Icon.png"\r
Icon="`echo $HOME`/bin/icons/Chromium_Icon.png"" > $HOME/.local/share/applications/chromium-linux.desktop
mv /tmp/LATEST $HOME/chrome-linux/
rm /tmp/chrome-linux.zip
echo "Installation/Upgrade complete"
#fi
exit 0
fi
```

Forums won't let me upload the file, so just copy and paste that into a file, then chmod +x, then run it.

---

### Post by hoppipolla on 2009-10-21
> **infestor said:**
> ok i managed to get the key and install chromium *woop*

but one bothersome question more: how can i not see the rss button the addressbar?

I dunno, to be honest I never really use RSS.

I mean, there is a possibility that some things don't work yet on Chromium... you could always use FF for that or find a link to it on the page? o.O

---

### Post by Ant. on 2009-10-21
Like suggested a couple of times, SwiftFox is a brilliant browser, really made a noticeable difference on my old laptop with an AMD CPU. I'm gonna have to check out Chromium, Chrome really impressed me when I was on XP temporarily.

---

### Post by infestor on 2009-10-21
> **hoppipolla said:**
> I dunno, to be honest I never really use RSS.

I mean, there is a possibility that some things don't work yet on Chromium... you could always use FF for that or find a link to it on the page? o.O

wow...such vital thing as RSS is not implemented on chromium yet? baah, i am surprised.

---

### Post by Grifulkin on 2009-10-21
> **infestor said:**
> wow...such vital thing as RSS is not implemented on chromium yet? baah, i am surprised.

I would hardly call RSS vital.

---

### Post by hoppipolla on 2009-10-21
> **Ant. said:**
> Like suggested a couple of times, SwiftFox is a brilliant browser, really made a noticeable difference on my old laptop with an AMD CPU. I'm gonna have to check out Chromium, Chrome really impressed me when I was on XP temporarily.

lol I know, I have just personally lost SO much interest in Firefox and Mozilla ._.

Chrome, Arora and Webkit in general have kinda... showcased to me how much better browsers can be particularly on Linux, and until I see things like improved performance from Firefox particularly in Linux, I will be siding with alternatives I'm afraid! :)

---

### Post by infestor on 2009-10-21
the performance of the chromium is fantastic...just what i was looking for...but...(forget the rss)...still no smooth scrolling? i mean this is like an alpha release...but hey, i will bear it since the performance tops all the other small stuff (like mouse gestures, aww i so much miss it)

---

### Post by Ric_NYC on 2009-10-21
> **infestor said:**
> the performance of the chromium is fantastic...just what i was looking for...but...(forget the rss)...**still no smooth scrolling?** i mean this is like an alpha release...but hey, i will bear it since the performance tops all the other small stuff (like mouse gestures, aww i so much miss it)

Try this.

[http://chromium.exxe.ath.cx/smoothscroll/](http://chromium.exxe.ath.cx/smoothscroll/)

---

### Post by Niko Johnson on 2009-10-21
I like opera... its sleak, stable and sexy just like linux!  -- nixie pixle

---

### Post by keiichidono on 2009-10-21
> **infestor said:**
> the performance of the chromium is fantastic...just what i was looking for...but...(forget the rss)...still no smooth scrolling? i mean this is like an alpha release...but hey, i will bear it since the performance tops all the other small stuff (like mouse gestures, aww i so much miss it)

Smooth scrolling is there, no autoscrolling, no RSS. Flash/java should work.

---

### Post by Mr. Picklesworth on 2009-10-21
Yup, Chromium is beautiful. For those various extensions you can't live without, check out [http://www.chromeextensions.org/](http://www.chromeextensions.org/) . (For example, if you really want Adblock, although personally I find it's redundant - and a bit unfair to use - when the browser is fast enough that the ads have no impact).

I've been able to completely drop Firefox at this point. It's a really neat browser :)

---

### Post by lovinglinux on 2009-10-21
Chromium is fast, but that's not enough, specially considering Firefox 3.6a1 is almost as fast. Besides, [Firefox can be optimized](http://ubuntuforums.org/showthread.php?t=1193567).

Chromium cannot deliver the same experience and level of customization as Firefox. If you use your browser just to read blogs, then it's perfectly fine. But if you use your browser as a productivity tool, then Firefox is unbeatable.

---

### Post by Mr. Picklesworth on 2009-10-21
> **lovinglinux said:**
> Chromium cannot deliver the same experience and level of customization as Firefox.

Okay, open up Chromium. Head to chrome:extensions. Hey, look at that!
Now, check out chromeextensions.org, Google "chrome extension", and look at Feedly (which has a currently private test version for Chrome that works very well).

It can deliver precisely the level of customization, although granted the community of add-on developers is a lot smaller.

---

### Post by lovinglinux on 2009-10-21
> **Mr. Picklesworth said:**
> It can deliver precisely the level of customization, although granted the community of add-on developers is a lot smaller.

Chrome extensions API is in it's infancy and the community of add-ons developers is just a fraction of Firefox. I'm sure Chrome will compete with Firefox in this field too, but not now.

---

### Post by hoppipolla on 2009-10-22
> **lovinglinux said:**
> Chrome extensions API is in it's infancy and the community of add-ons developers is just a fraction of Firefox. I'm sure Chrome will compete with Firefox in this field too, but not now.

Yeah well said there - I was about to point out that even if this is one area where Chrome falls behind a little, it is about the ONLY area at present and it's being resolved as we speak!

Until I saw 4.0 i would have said that Mozilla will fall behind for sure in this one, but I think it depends what they pull out their hats for that release.

---

### Post by cb951303 on 2009-10-22
I'm one of the people that left FF for Chromium. Do I miss firefox addons? Yes, but chromium makes up for it in the speed and -dare I say it- stability department.

---

### Post by Tibuda on 2009-10-22
> **hoppipolla said:**
> Man I wish I could remember lol

*hunts around the interwebs... I KNOW I did this fine... o.O

Ok well this will work for Chromium - add these two repos to Synaptic:

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

and then execute this command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5

```

I'll see if I can work out how to install Chrome as well o.O


EDIT -- God knows man, try adding this repo for Chrome and see if it pops up in Synaptic (it's impossible to find it on the Chrome pages as far as I can tell but this is the repo I have on my machine):

deb [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb) stable main

If you are using karmic, you can type **ppa:chromium-daily** in synaptyc instead of **deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main** and it will already grab the key for you. This is a step on making it easier, but I still hope they implement a "ppaurl" thing like apturls.

---

### Post by Ric_NYC on 2009-10-22
Chromium is a fresh new look on Ubuntu.
Gnome and FF have that "90's look".

---

### Post by froggyswamp on 2009-10-22
> **Ric_NYC said:**
> Chromium is a fresh new look on Ubuntu.
Gnome and FF have that "90's look".
+1
Google also doesn't say "speed doesn't really matter nor startup time" and doesn't preach for displaying a menu by default despite rarely being used. I hate Google but a tip of my hat for that.

---

### Post by infestor on 2009-10-22
if i could get auto-scroll, mouse gestures and rss working on chromium i would really be blissful

---

### Post by Tibuda on 2009-10-22
> **infestor said:**
> if i could get auto-scroll, mouse gestures and rss working on chromium i would really be blissful

For mouse gestures, install Easystroke. You'll be able to bind gestures to hotkeys in any application (or global). For RSS, you could try Google Reader.

---

### Post by hoppipolla on 2009-10-22
sorry to act ignorant, but what IS smooth scrolling? Is it when it smooths out the juddering of the mouse wheel?

---

### Post by Tibuda on 2009-10-22
> **lovinglinux said:**
> Chrome extensions API is in it's infancy and the community of add-ons developers is just a fraction of Firefox. I'm sure Chrome will compete with Firefox in this field too, but not now.

This has the same meaning as "Linux community of application developers is just a fraction of Windows. I'm sure Linux will compete with Windows in this field too, but not now."

Still you are "loving linux".

---

### Post by Jim_in_Omaha on 2009-10-22
> **lovinglinux said:**
> Chromium is fast, but that's not enough, specially considering Firefox 3.6a1 is almost as fast. Besides, [Firefox can be optimized](http://ubuntuforums.org/showthread.php?t=1193567).

Chromium cannot deliver the same experience and level of customization as Firefox. If you use your browser just to read blogs, then it's perfectly fine. But if you use your browser as a productivity tool, then Firefox is unbeatable.

I know that 3.5.3 is faster than the standard Ubuntu Firefox distro version (3.0 ??) I did not know there was a 3.6a1. On the WinXP side for my work laptop upgrading to 3.5.3 made a night and day difference in speed. (old but reliable T30 IBM)

---

### Post by hoppipolla on 2009-10-22
> **Jim_in_Omaha said:**
> I know that 3.5.3 is faster than the standard Ubuntu Firefox distro version (3.0 ??) I did not know there was a 3.6a1. On the WinXP side for my work laptop upgrading to 3.5.3 made a night and day difference in speed. (old but reliable T30 IBM)

I do still find Firefox quite slow. But then I'm on the 3.5....something :) heh

---

### Post by lovinglinux on 2009-10-22
> **Jim_in_Omaha said:**
> I did not know there was a 3.6a1.

It's an alpha version, available for testing from Mozilla FTP site. The difference is amazing, specially when playing flash videos. 

There is also a 3.7something.

---

### Post by hoppipolla on 2009-10-22
> **lovinglinux said:**
> It's an alpha version, available for testing from Mozilla FTP site. The difference is amazing, specially when playing flash videos. 

There is also a 3.7something.

Thing is though it has to be said that people say this about EVERY new Firefox release lol

I hope that now they start to pick up their game now they have Chrome and a handful of other new webkit-based browsers to compete with! :)

---

### Post by lovinglinux on 2009-10-22
> **hoppipolla said:**
> Thing is though it has to be said that people say this about EVERY new Firefox release lol

Yep, but I have benchmark data to prove it ;)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124167&stc=1&d=1249840668[/IMG]

---

### Post by hoppipolla on 2009-10-22
> **lovinglinux said:**
> Yep, but I have benchmark data to prove it ;)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124167&stc=1&d=1249840668[/IMG]

I wish I knew what that meant lol

Is higher better or worse? xD

I'll get the new Firefox when it comes out, and I guess it would be quite nice to see Mozilla still in the game :)

For now though, I'm very much on Chrome!

---

### Post by infestor on 2009-10-22
imho *webkit* kicks ***...best layout engine ever (so far)...

---

### Post by Onyros on 2009-10-22
I had been using Opera as my main browser up until 9.64. Ever since upgrading to Opera 10, it has become slow, problematic, buggy. I tried Chromium out and it has become my primary browser, alongside uzbl (which is also webkit based).

Haven't looked back, and even though I still keep Opera and Firefox installed, in terms of speed they're not even comparable to the two I'm using mostly now,

---

### Post by lovinglinux on 2009-10-22
> **hoppipolla said:**
> I wish I knew what that meant lol

Is higher better or worse? 

Higher is better. From left to right you see the improvement for each browser since the release of Jaunty until the middle of August. As you can see I started with 200 points and ended with 1100. The test is [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) benchmark.

---

### Post by hoppipolla on 2009-10-22
> **lovinglinux said:**
> Higher is better. From left to right you see the improvement for each browser since the release of Jaunty until the middle of August. As you can see I started with 200 points and ended with 1100. The test is [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) benchmark.

But isn't Chromium still much higher?

I mean I know they don't have to actually match or beat Chromium to make Firefox a valid choice, but it would be cool if they got close! Chrome is like lightning!

---

### Post by lovinglinux on 2009-10-22
> **hoppipolla said:**
> But isn't Chromium still much higher?

I mean I know they don't have to actually match or beat Chromium to make Firefox a valid choice, but it would be cool if they got close! Chrome is like lightning!

Yep, it is. But the difference is not dramatic. I think Firefox will get there, specially considering Chromium is not a finished product.

---

### Post by tom66 on 2009-10-22
Chromium.

Super-fast (1 second opening time and also fast with web pages) and it hasn't crashed once.

---

### Post by cb951303 on 2009-10-23
> **lovinglinux said:**
> Yep, it is. But the difference is not dramatic. I think Firefox will get there, specially considering Chromium is not a finished product.

You call that not dramatic?

Chromium not being finished only means that the gap will widen with time as it gets close to be a finished product :)

---

### Post by lovinglinux on 2009-10-23
> **cb951303 said:**
> You call that not dramatic?

Yes, is not that dramatic when considering what you can perceive visually. You have to try 3.6.a1 and see for yourself.

> **cb951303 said:**
> Chromium not being finished only means that the gap will widen with time as it gets close to be a finished product :)

Not necessarily. The vanilla Firefox works much faster than my current profile, so I believe once Chromium finishes adding the missing features, the performance will drop.

---

### Post by cb951303 on 2009-10-23
> **lovinglinux said:**
> Yes, is not that dramatic when considering what you can perceive visually. You have to try 3.6.a1 and see for yourself.

I just did and I'm not convinced at all.

Gecko will surely progress and may even be on par with WebKit in the future but IMHO the XUL interface will always the bottleneck. It's very sluggish, it looks horrible on linux and it's not even necessary considering all the cross-platform GUI toolkits that we have.

Have you tried chromium? I really don't understand how one can't see the difference "visually" between 3.6 and chomium 4.x.

Anyway, OP is asking for a FF alternative and I don't think FF 3.6 counts :)

---

### Post by lovinglinux on 2009-10-23
> **cb951303 said:**
> I just did and I'm not convinced at all.

Gecko will surely progress and may even be on par with WebKit in the future but IMHO the XUL interface will always the bottleneck. It's very sluggish, it looks horrible on linux and it's not even necessary considering all the cros-platform GUI toolkits that we have.

Have you tried chromium? I really don't understand how one can't see the difference "visually" between 3.6 and chomium 4.x.

Anyway, OP is asking for a FF alternative and I don't think FF 3.6 counts :)

Well, I forgot to mention my version of 3.6.a1 was compiled from source with PGO and processor optimization flags. Ooops, sorry :oops:

---

### Post by 3rdalbum on 2009-10-23
Opera is very good; I've been running Opera 10 since its first beta. On my netbook with a slow SSD, Opera is the only browser that was tolerably fast and never went grey due to excessive I/O.

I also like the screenshot tabs. They sound like a bit of a gimmick at first, but then if you have 20 tabs open you can quickly see which ones are Ubuntu Forums and which are OSnews. Opera Link is also very handy to keep my bookmarks and speed dial synchronised between netbook, desktop, and server (and mobile phone, if I had one).

And Opera Turbo helps speed up things when I'm on the mobile broadband.

If Facebook worked reliably with Opera, I'd simply never open Firefox. Hopefully the Facebook improvements should be coming to Opera soon.

---

### Post by hoppipolla on 2009-10-23
> **lovinglinux said:**
> Well, I forgot to mention my version of 3.6.a1 was compiled from source with PGO and processor optimization flags. Ooops, sorry :oops:

This is silly, of course Firefox will perform better if you do stuff like that, that is seriously not a sign of a good browser ._.

Mozilla need to pick up their game for 4 or they will lose quite a few people, particularly on Linux.

---

### Post by HappinessNow on 2009-10-23
> **Dougie187 said:**
> Chromium/ChomeBoth actually better then Firefox.

---

### Post by kvarley on 2009-10-23
Swiftfox / Swiftweasel

---

### Post by lovinglinux on 2009-10-23
> **hoppipolla said:**
> Mozilla need to pick up their game for 4 or they will lose quite a few people, particularly on Linux.

I agree on that. But I believe they will. They have been optimizing Firefox considerably lately. I can't imagine myself going back to 3.0.

---

### Post by hoppipolla on 2009-10-23
> **lovinglinux said:**
> I agree on that. But I believe they will. They have been optimizing Firefox considerably lately. I can't imagine myself going back to 3.0.

I am trying to keep an open mind. I mean there's no point in me after years of supporting Firefox and Mozilla suddenly jumping ship just because Google have released what I perceive to be a good browser. I'll try not to take sides too passionately on this one lol ^_^

---

### Post by infestor on 2009-10-27
is there a page where i can see the changelog of chromium? it really updates a lot and so far i did not manage to find the changelog.

---

### Post by alfplayer on 2009-10-28
> **infestor said:**
> is there a page where i can see the changelog of chromium? it really updates a lot and so far i did not manage to find the changelog.

[http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/)

---

### Post by infestor on 2009-10-30
just upgraded to karmic...firefox 3.5 seems to catch the speed :) (at last!)

---

### Post by Nixie Pixel on 2009-12-05
> **Niko Johnson said:**
> I like opera... its sleak, stable and sexy just like linux!  -- nixie pixle
I never said that about Opera! But I did about Linux.

:)

---

### Post by Dark Aspect on 2009-12-05
> **infestor said:**
> i use ubuntu jaunty x64 and firefox from repos...i have been suffering from its slowness for almost years...i also have xp 32 bit installed on my PC on the side...firefox in ubuntu is significantly slower than it is on xp (i disregard flash playing, a major issue for all browser i guess on linux)

i tried epiphany but the user interface is quite different (ctrl+enter doesnt append [www...com]("http://www...com") and middle click you cannot scroll etc.)

arora refused to work

flock has the same performance as firefox

opera's presto layout engine just sucks

so is there an alternative you guys can suggest me or a "magic" trick for firefox that i had not known?

[SeaMonkey]("http://www.seamonkey-project.org/") is a light weight version of Firefox.

---

### Post by crimesaucer on 2009-12-05
EDITED after installing the official Google Chrome beta:


Well, after having a really bad experience with a buggy Chromium 64 that took 3 hours to build from source, I decide to try the new official Google Chrome and all I have to say is that it's totally stable and works very nicely. It's very fast, but I still prefer firefox, and I don't like the tracking features of Chrome (I would prefer something like Iron).

---

