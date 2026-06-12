---
title: "Firefox 3.5 anyone?"
date: 2009-08-20
forum: System76 Support
---

### Post by imhavoc on 2009-08-20
So, now that I have 9.04 installed, I have a simple, easy path to Firefox 3.5. I haven't seen anyone talking about it here.

Is anyone using it yet? Impressions? Breakages? Anything?

---

### Post by pedja_portugalac on 2009-08-20
I used it few days ago, installed over some script, and I couldn't access my Bank account with it. So I recovered Ubuntu with official one. Now no problem doing that.

---

### Post by gila_monster on 2009-08-20
> **imhavoc said:**
> So, now that I have 9.04 installed, I have a simple, easy path to Firefox 3.5. I haven't seen anyone talking about it here.

Is anyone using it yet? Impressions? Breakages? Anything?

I had no trouble with it. Under 9.04, though, it appears that you must have 3.0 installed if you have 3.5 installed -- you can't just replace 3.0 using the respositories. (I expect this will change in 9.10.) The problem is that /usr/bin/firefox is actually a soft link to /usr/bin/firefox-3.0. So when you click a link in your email client, it will just run /usr/bin/firefox, which is 3.0, instead of running 3.5.

Okay, so we fix that by changing it to point to 3.5. The problem is that every update to 3.0 changes it back to 3.0! Very annoying.

Other that that, I had no real difficulties. A few minor moments with some of my add-ons not being compatible (yet) with 3.5, but that was mostly in the themes department.

---

### Post by jdb on 2009-08-20
> **imhavoc said:**
> So, now that I have 9.04 installed, I have a simple, easy path to Firefox 3.5. I haven't seen anyone talking about it here.

Is anyone using it yet? Impressions? Breakages? Anything?

I've been using it for a while, just upgraded to 3.5.2.
The only problem I've had is that I couldn't open asx audio streaming files on this website:

[http://www.radioreference.com/apps/audio/?ctid=2064]("http://www.radioreference.com/apps/audio/?ctid=2064")

I don't know if it had anything to do with 3.5 though.

If I chose "real player" instead of "windows media player" I got a ram file instead of an asx file & it opened with mplayer-plugin.

When I downloaded the asx file then:

```
mplayer -playlist filename.asx
```

worked.

Other than that I've had no problems but it doesn't look much different, I haven't looked around to see whats new in it.


jdb

---

### Post by samalex on 2009-08-21
How are you guys installing Firefox 3.5?  I'd like to upgrade, but using the one through Ubuntu repositories calls it something other than Firefox which threw me, so I uninstalled and went back to 3.0.

Also do I need to reinstall any plugins, like Flash, with 3.5 or will it pickup everything used with 3.0?

Thanks --

Sam

---

### Post by gila_monster on 2009-08-21
> **samalex said:**
> How are you guys installing Firefox 3.5?  I'd like to upgrade, but using the one through Ubuntu repositories calls it something other than Firefox which threw me, so I uninstalled and went back to 3.0.

Also do I need to reinstall any plugins, like Flash, with 3.5 or will it pickup everything used with 3.0?

Thanks --

Sam

I installed 3.5 from the repos. As you noted, it will be branded Shiretoko rather than Firefox, but it **is** Firefox 3.5. I didn't have to do anything with the plugins, worked just fine for me.

Hmmm. Okay, small correction. Using Firefox on Ubuntu will put the Firefox data in the .mozilla subdirectory in your home directory. Firefox 3.0 puts things in another subdirectory called firefox, but when I started Shiretoko/3.5, it cloned that directory to another directory called firefox-3.5. Everything worked, but because it has a different subdirectory, extensions like Newsfox didn't quite do what I expected. Newsfox worked fine, but any RSS feed I added from Shiretoko didn't show up in Firefox 3.0 because of the different directories. Note that I was an early adopter, and I'm not sure if it still actually does this (I've modified my installation a bit since then). Can anyone confirm?

---

### Post by HotShotDJ on 2009-08-21
Firefox 3.5 from the Ubuntu repositories (aka Shiretoko) works just fine.  I had to do a few "work-arounds" to get it just right, though:

1 - Fonts: The new 3.5 does not respect your gnome settings for font hinting.  Fix this by creating a file called .fonts.conf (the leading "dot" is important, don't leave it out!) and pasting the following code into it:```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```
2 - The default Ubuntu Firefox Modifications add-on (Ubufox)doesn't work with Firefox 3.5.  You'll need version 0.8a1, which you can get from one of the mirrors here: [http://packages.ubuntu.com/it/karmic/all/ubufox/download](http://packages.ubuntu.com/it/karmic/all/ubufox/download)

---

### Post by samalex on 2009-08-21
Are any of you running the beta Flash 10 64-bit for Linux using Firefox 3.5?  I still haven't installed that, but I might do FF 3.5 and Flash 10 64-bit at the same time.  Also will I still have to uninstall the current version of Flash used by FF 3.0 since FF 3.0 and FF 3.5 have different plugin directories?

Thanks --

Sam

---

### Post by yescookie on 2009-08-21
> **jdb said:**
> I've been using it for a while, just upgraded to 3.5.2.
The only problem I've had is that I couldn't open asx audio streaming files on this website:

[http://www.radioreference.com/apps/audio/?ctid=2064]("http://www.radioreference.com/apps/audio/?ctid=2064")

I don't know if it had anything to do with 3.5 though.

If I chose "real player" instead of "windows media player" I got a ram file instead of an asx file & it opened with mplayer-plugin.

When I downloaded the asx file then:

```
mplayer -playlist filename.asx
```

worked.

Other than that I've had no problems but it doesn't look much different, I haven't looked around to see whats new in it.


jdb
I'm using 3.5.2 too,I can play the audio well,You just need chose "web player" and make sure you have flash player.

---

### Post by jdb on 2009-08-21
> **yescookie said:**
> I'm using 3.5.2 too,I can play the audio well,You just need chose "web player" and make sure you have flash player.

I can play it from firefox fine in different formats, ram & webplayer both work, but I couldn't play the asx format from firefox.

It doesn't really matter, it's just something I noticed.

jdb

---

### Post by pedja_portugalac on 2009-08-22
> **samalex said:**
> How are you guys installing Firefox 3.5?  I'd like to upgrade, but using the one through Ubuntu repositories calls it something other than Firefox which threw me, so I uninstalled and went back to 3.0.

Also do I need to reinstall any plugins, like Flash, with 3.5 or will it pickup everything used with 3.0?

Thanks --

Sam

There's a program called Ubuntuzilla over which you can install latest versions of Mozilla Firefox, Mozilla SeaMonkey, and Mozilla Thunderbird on Ubuntu Linux. It will completely remove Firefox 3 and install as only browser newest Firefox, for the moment 3.5.2 with all your plug ins, bookmarks, etc, preserved. You can also allow it to check alone for new realizes. In my opinion this is the best way to always have the newest version of Firefox or other packages named above, installed the way it should be and no Shiretoko or whatever. Here's the link to download ubuntuzilla:

[http://downloads.sourceforge.net/project/ubuntuzilla/ubuntuzilla/4.7.4/ubuntuzilla-4.7.4-0ubuntu1-i386.deb?use_mirror=freefr](http://downloads.sourceforge.net/project/ubuntuzilla/ubuntuzilla/4.7.4/ubuntuzilla-4.7.4-0ubuntu1-i386.deb?use_mirror=freefr)

---

### Post by nanotube on 2009-08-24
and here's a link to project site, with instructions etc.:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

