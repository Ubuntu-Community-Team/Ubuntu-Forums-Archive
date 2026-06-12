---
title: "Experience"
date: 2012-03-05
forum: Testimonials &amp; Experiences
---

### Post by gmhafiz on 2012-03-05
Hello all. I am excited about the upcoming release of 12.04 LTS release. I know this is an important release and I wish it will be  a good one. I immediately downloaded the torrent and installed on my machine. I would like to share my experience on using it and there are a few areas in which it can be improved upon. My comments here are more focused towards usability.

Specs:
Intel C2D E6750
ATI HD4850
Gigabyte P35-DS3 motherboard

**Installation:**
[LIST]
[*]Booted it on virtualbox. Installed on the usb drive. Then I used the pen drive to install it into one of my empty partition
[*]Chose manual partition, automatic login and downloaded all codecs. Installation went without a hitch.
[*]On booting up, the grub2 showed precise pangolin alongside with arch linux an windows xp entries. Nice.[/LIST]

**Initial Usage:**
[LIST]
[*]I am greeted with unity interface. I wasn't sure whether I can do work faster this way. Nevertheless I went ahead and start using it.
[*]I noticed that there were 100MB updates. So I updated all and restarted.
[*]I tried to find chrome, but it wasn't in the software centre. So I am left with chromium. I have always been using chromium but I am not sure how the general population will respond if they see chromium there.
[*]The left bar was too big so I reduced the size to the smallest.[/LIST]

**Music**
[LIST]
[*]I wanted to install clementine so I went to add the ppa from its website. Unfortunately, there's no build for 12.04 yet. But then I remembered why don't I just search it in the software centre? There it was! It was only version 1.0.1, so I can't play with dev build.
[*]I also used rhythmbox to index all my songs. The buttons in the lyric tab  shouldn't have underscore.
[[IMG]http://i.imgur.com/4B3s4.jpg[/IMG]](http://imgur.com/4B3s4)
[/LIST]

**Multiple hard drives**
[LIST]
[*]Since my songs are stored in a different hard disk than the OS, I would like them mount automatically at boot. I know adding them manually by editing /etc/fstab but I wonder how would a normal person wanted it. In windows, they are accessible from My Computer. On ubuntu, I will have to click on it before clementine can access the songs inside. This cannot be good.
[*]So I scoured the software centre to look for automatic disk drive mounting and found ntfs configuration tool. Well it's good that it can handle windows partition but what about my ext4 formatted hard drive? Again I scoured the software centre and found "mount manager". I configured my mount points and all the options but I am sure it will quickly confuse a windows user. Also, QT software don't look nice under unity.
[/LIST]

**Make link**
[LIST]
[*]I'd like to make a link from my second HDD into /home/user/Music. Make link crashed. But it seems like the latest update that I installed yesterday fixed it.
[*]I deleted the existing /home/user/Music and copied the shortcut into /home/user. The copied shortcut didn't have the music emblem. I needed to restart the computer for ubuntu to recognize the shortcut and offered the emblem. The arrow shortcut is still there. However, I would prefer it to be gone or make it smaller though because it obfuscate the music emblem.
[/LIST]

**Email**
[LIST]
[*]Next I would like to try setting up email. thunderbird pops up, entered my gmail and it automatically retrieved all the necessary settings for it. It asked me for imap or pop3, Since it defaulted to imap, I just clicked next. All of my email were synced locally and I was happy that it worked fine... so far.
[*]I noticed it doesn't support threaded email like in the gmail.com
[*]I edited my gmail draft in thunderbird and saved it. When I went to chromium for my gmail, the exising draft were not edited. Instead, a new draft appeared with my changes.
[*]I wish thunderbird will have better intergration with gmail in the future updates
[/LIST]

**Broadcast**
[LIST]
[*]Next I added facebook account. Adding a new account worked although there seem to be less streamlined. The UI can be a bit confusing as I took a bit of time to figure out where to click.
[*]But then I changed my mind not to have fb updates - they were too many. So I deleted it and added twitter instead. I needed to have it authorized. To my surprise, it showed a hindi translated page of twitter. I am a foreigner staying in India but I don't know how to read hindi characters! Fortunately I knew that I had to click on the green button and all is well. I know this is not ubuntu problem but maybe something can be done to send twitter a UserAgent string that matches OS's language, in my case English.
[/LIST]

**Shutdown restart**
[LIST]
[*]Before I forget, IMO there should be a Restart Computer option alongside with shutdown, log out, etc. It doesn't make sense when you want to restart, but had to choose Shut Down option first. I used to make fun of win xp that users had to click on Start button before shutting it down.
[/LIST]

**Rar**
[LIST]
[*].rar is a proprietary format but I thought rar support was downloaded alongside all the codecs during installation. It asked me between rar or unrar. A clueless newbie will simply click ok so it should be fine. 
[*]Probably adding rar support during the installation is a good idea to reduce user confusion
[/LIST]

**Chromium**
[LIST]
[*]I preferred chrome/chromium because I can easily switch profiles as I share the desktop with my wife. On Alt-Tab, two chromium windows are combined into a single icon and after a second, I can see both windows stacked vertically. IMO, selecting the windows should use UP and DOWN button instead of LEFT and RIGHT. When the windows were stacked horizontally, switching chrome windows by LEFT and RIGHT makes sense of course.
[*]I'm spolied with compiz's Alt-Tab preview since I can instantly see what the app is doing instead of showing icons.
[[IMG]http://i.imgur.com/abd4E.jpg[/IMG]](http://imgur.com/abd4E)
[/LIST]

**Totem Video Player**
[LIST]
[*]It failed to load srt automatically although both movie(.mp4) and srt files had the same name
[*]I had to go to View > Subtitles > Select Text Subtitles and to my surprise, the movie restarted! No change since oneiric yet.
[/LIST]

**Image editor**
[LIST]
[*]There's a built-in photo manager but what if I wanted to edit some photos/images. I needed simple software that can make bubble annotations to add texts onto the photos. I haven't scoured the software centre but the best and simplest I can find is Pinta image editor.
[/LIST]

**Ubuntu One**
[LIST]
[*]Worked brilliantly.
[/LIST]

**Top Bar Nav**
[LIST]
[*]If you see in the screenshot, the letter "M" in the word Movie seemed stretched out. This happens both in VM and installed 12.04
[/LIST]
[[IMG]http://i.imgur.com/DubBh.png[/IMG]](http://imgur.com/DubBh) 
[LIST]
[*]There's a space here too.
[/LIST]
[[IMG]http://i.imgur.com/fah7wl.png[/IMG]](http://imgur.com/fah7w)

**Adding new user**
[LIST]
[*]Here are the steps I took and my comments
[*]Click my username on the top right corner
[*]Click User Accounts...
[*]Unlock
[*]Click plus button (same as adding twitter account, plus button is not informative and will leave user confused. My suggestion is to replace "+" with "Add new account".)
[*]Standard was default, typed in a new username and create.
[*]I thought I was finished since the dialog window is closed. I needed to click on the text "Account disabled" (which is doesn't looked like a button at all), key in a password, and click "Change" (why? I hadn't put in a password for this account before)
[/LIST]

**Menu cut off**
I occasionally got this bug though it is hard to reproduce. Simple clicking on and menu on the top nav bar will produce a bug shown in the screenshot below.
[[IMG]http://i.imgur.com/pgIHu.jpg[/IMG]](http://imgur.com/pgIHu)

**Dash Home**
[LIST]
[*]It's great if I know what software I wanted to open but that required typing which can be slow or I could forget the name. Using mouse should be faster and IMO linux mint 11 has the best menu.
[*]I already had indexed my songs from rhythmbox and clementine but clicking on Music icon showed nothing and typing a band from my collection also returns nothing
[*]Clicking on video icon showed recently viewed videos and not my whole collection. It'd be nice if I can just type the name of the movie I have and it pops right there.
[/LIST]


**Misc**
[LIST]
[*]There are other nitpicks such as low resolution icon of some software during ALt-Tab which makes it looked ugly
[*]Searching for files should be easier to access. Maybe take KDE approach by integrating file searching into the Dash Home instead of making user to click on Nautilus > GO > Search for files. Oh since I'm in the picture folder, it didn't include result for my video that I am looking for!
[*]Not sure about orange coloured folder icons. Since the default BG is purple, maybe a blue-purplish hue will be nice.
[/LIST]


**Wife Test**
[LIST]
[*]So I gave this beta release to my wife and surprisingly she loved it. This is the first time she is seeing unity interface. She said things like "Neat" and "Better" than her previous experience with linux mint, oneiric and arch linux(duh!).
[*]I'm glad that she liked it and I hope the general population will do as well!
[/LIST]

All in all, you guys are doing great job. There are still some time for the fixes to be made... if I am heard at all :P

--

---

### Post by Bucky Ball on 2012-03-05
Nice work! I'm sure you will be heard and very helpful for devs and users alike. ;)

I particularly like the 'Wife Test' to finish off; nice touch ...

---

### Post by Elfy on 2012-03-05
*Thread moved to **Ubuntu Testimonials & Experiences**.*

---

### Post by CrByte on 2012-03-05
> **gmhafiz said:**
> 

**Multiple hard drives**
[LIST]
[*]Since my songs are stored in a different hard disk than the OS, I would like them mount automatically at boot. I know adding them manually by editing /etc/fstab but I wonder how would a normal person wanted it. In windows, they are accessible from My Computer. On ubuntu, I will have to click on it before clementine can access the songs inside. This cannot be good.
[*]So I scoured the software centre to look for automatic disk drive mounting and found ntfs configuration tool. Well it's good that it can handle windows partition but what about my ext4 formatted hard drive? Again I scoured the software centre and found "mount manager". I configured my mount points and all the options but I am sure it will quickly confuse a windows user. Also, QT software don't look nice under unity.
[/LIST]

**Make link**
[LIST]
[*]I'd like to make a link from my second HDD into /home/user/Music. Make link crashed. But it seems like the latest update that I installed yesterday fixed it.
[*]I deleted the existing /home/user/Music and copied the shortcut into /home/user. The copied shortcut didn't have the music emblem. I needed to restart the computer for ubuntu to recognize the shortcut and offered the emblem. The arrow shortcut is still there. However, I would prefer it to be gone or make it smaller though because it obfuscate the music emblem.
[/LIST]

**Rar**
[LIST]
[*].rar is a proprietary format but I thought rar support was downloaded alongside all the codecs during installation. It asked me between rar or unrar. A clueless newbie will simply click ok so it should be fine. 
[*]Probably adding rar support during the installation is a good idea to reduce user confusion
[/LIST]

**Top Bar Nav**
[LIST]
[*]If you see in the screenshot, the letter "M" in the word Movie seemed stretched out. This happens both in VM and installed 12.04
[/LIST]
[[IMG]http://i.imgur.com/DubBh.png[/IMG]](http://imgur.com/DubBh) 
[LIST]
[*]There's a space here too.
[/LIST]
[[IMG]http://i.imgur.com/fah7wl.png[/IMG]](http://imgur.com/fah7w)

--

nice write up.

The quoted things are what really needs to be done for me to use this as a main desktop OS. Multiple hard drives been a must for me.

---

### Post by mastablasta on 2012-03-05
re: Chromium - Firefox can also switch profiles. i have a couple of them on....
 
but i think it needs to be launched with profile manager.

---

### Post by craig10x on 2012-03-05
By the way..wasn't sure if you were aware, Chrome isn't offered in the software center (only the open source Chromium version) but you can grab the .deb file from the Google Chrome website and have the software center install it for you...(just by right clicking on the file and selecting that option)...

---

### Post by madjr on 2012-03-05
> **forestpiskie said:**
> *Thread moved to **Ubuntu Testimonials & Experiences**.*

why is this in testimonials?

most of the things mentioned are bugs in precise beta.

some things will change/improve, so itsnt testimonials better reserved for non dev releases?

---

### Post by Tamlynmac on 2012-03-06
> madjr
why is this in testimonials?
most of the things mentioned are bugs in precise beta.
some things will change/improve, so itsnt testimonials better reserved for non dev releases? 	

I agree 100%.

It states in the T&E guideline (top of page):
> Please do not use this section for support questions,[SIZE=1] [COLOR=Red]**bug reports**[/COLOR][/SIZE], or debate.

Using the T&E to point out bugs or issues with respect to a release in development (alpha/beta), doesn't make any sense to me either. Not to mention, the unorthodox format (screenshots - attachments).

Just my $0.02

---

### Post by Bucky Ball on 2012-03-06
> **gmhafiz said:**
> I would like to share my experience on using it and there are a few areas in which it can be improved upon.

This is the OPs experience of the OS. It is not really a bug report concerning the 12.04 LTS daily build or 12.04 LTS really. ;)

---

### Post by gmhafiz on 2012-03-06
> **Bucky Ball said:**
> Nice work! I'm sure you will be heard and very helpful for devs and users alike. ;)

I particularly like the 'Wife Test' to finish off; nice touch ...
Thanks!

> **mastablasta said:**
> re: Chromium - Firefox can also switch profiles. i have a couple of them on....
 
but i think it needs to be launched with profile manager.
I now remembered that. But there's no easy way to do it for a normal person.

> **craig10x said:**
> By the way..wasn't sure if you were aware, Chrome isn't offered in the software center (only the open source Chromium version) but you can grab the .deb file from the Google Chrome website and have the software center install it for you...(just by right clicking on the file and selecting that option)...
There could be two scenarios:
1. A normal user did not find chrome, goes to google and download ubuntu version. Or;

2. A normal person did not found chrome and goes to software centre. He/she did not find chrome but chromium was showed instead. It may looked like chrome but colour is all blue. User gets suspicious and goes to google website to download one. Now the user a perception that the software centre may not have all the softwares a normal user wanted, defeating the purpose of the repository as a one-stop place to download and maintain softwares.

> **Bucky Ball said:**
> This is the OPs experience of the OS. It is not really a bug report concerning the 12.04 LTS daily build or 12.04 LTS really. ;)
It's kinda both. I mentioned it is "more focused on usability".
If any of you are kind enough, please open a bug report if  you can reproduce them. I myself have found a few more bugs but I am going to do a fresh re-installation to make sure of them before reporting all the bugs I have found.

What about usability issues? Where is the correct channel I should report to?

---

### Post by Tamlynmac on 2012-03-06
> Bucky Ball
It is not really a bug report concerning the 12.04 LTS daily build or 12.04 LTS really.

> **Menu cut off**
I occasionally got this bug though it is hard to reproduce.

> 
**Totem Video Player**
[LIST]
[*]It failed to load srt automatically although both movie(.mp4) and srt files had the same name
[*]I had to go to View > Subtitles > Select Text Subtitles and to  my surprise, the movie restarted! No change since oneiric yet.
[/LIST]
The OP even noted the menu cut off bug. Have no idea if they reported it.

I don't see the logic in writing a testimonial or experience for a version that's still under development. Until the version has been released - it's in a constant state of flux. Thus, the experience would only be applicable at the time it was written. Changes occurring prior to release, could easily null & void the experience. Just seems foolish to post a TorE until the version has been released and other members have installed it.

It's been my experience that not all members are involved with the alpha or beta releases, preferring to wait until or after the release date. Perhaps, logic might suggest that the forums provide a place for commenting on releases in development. But since feedback isn't (I don't think) provided to Canonical from the forums, it may not make sense to start another forum.

Just my $0.02

---

