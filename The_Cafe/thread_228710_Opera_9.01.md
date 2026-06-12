---
title: "Opera 9.01"
date: 2006-08-03
forum: The Cafe
---

### Post by _simon_ on 2006-08-03
Is now available:

[http://www.opera.com/download/?platform=linux](http://www.opera.com/download/?platform=linux)


Changelog for Opera 9.01 for Linux


Release Notes

Opera 9.01 is a recommended upgrade.

[B]Changes Since Opera 9.0

User interface[/B]

Solved problems with error console popping up unrequested. Console Filter setting in opera.ini has been renamed to Error Console Filter.
Newsfeeds can be renamed again.
Right-click to save images no longer puts the file in the list of transfers.
Fixed problems with setting external source viewer path. Preference field no longer requires quotation marks if containing spaces.
Solved issue where Opera would get focus, but elements would not be activated when clicked while Opera was in background.
Search field now shows dropdown when using the down arrow key.
Using search from right-click menu remembers the last search engine used.
"Find" and "Find next" options no longer grayed out in source viewer "Edit" menu.
Typed-in history now disabled and cleared with visited history in preferences.

**Mail, messaging, and newsfeeds**

Multiple IMAP backend improvements and bug fixes.
Improved speed in handling filters with large number of messages.
Fixed problem with recognition of uuencoded attachments.
Changed quoting colors in mail for improved readability/accessibility.

**Display and scripting**

Solved letter-spacing issue in form fields when using zoom.
Fixed problem with some Chinese sites where clicking any link would trigger language-switching script.
Fixes to contenteditable support.
Fixed scripting issue causing embedded content not to appear.
META refresh works with javascript: URIs again.
Allow forms to be submitted if the default value of their inputs exceeds their own maxlength.
Solved problems logging on to the Internet banking services of Volksbank Raiffeisenbank.
XSLT: Added support for exls:node-set function.
DOM: Added support for range.intersectsNode.

**Plug-ins and Java**

Allow Flash from other domain to access script in page; fixes problems with sites where Flash pop-ups cannot be closed.
Fixed problems with direct embedding of URLs using the MMS and RTSP protocols causing some Web radios and media players to fail.
Fixed bug where Java Applet did not load when width and height set to 0.
Fixed problem where some Flash pages would not prompt users missing Flash to install.
[B]
Miscellaneous[/B]

Multiple stability improvements. Fixes include issue described in this Opera advisory.
Solved refresh problem causing some frames pages to turn blank.
HTTP accept language now stated correctly, works with Hotmail and other localized Web services again.
Fixed automatic saving of cookies.
Solved upload problems with Imageshack and similar services.
Improved compatibility with Adobe Type Manager and better handling of large quantities of installed fonts.

**UNIX-specific changes**

Background color for widgets is now gray (#505150) instead of dark blue (#375175).
Dragging the config.xml file into Opera now correctly opens the widget.
First click and drag on a widget scrollbar now correctly scrolls content.

---

### Post by BWF89 on 2006-08-03
The new version of Firefox came out today also :D

---

### Post by Erunno on 2006-08-08
Does anyone know by chance if you can get Opera 9.01 through one of the Ubuntu/Canonical repositories ? I've been waiting for a few days now but so far nobody bothered to upload the new version to the repos.

Cheers,
Erunno

---

### Post by wvslkr on 2006-08-08
If not now be patient.  M guess 2 days tops.  Think the world will end meantime?;)

---

### Post by Colonel Kilkenny on 2006-08-08
> **Erunno said:**
> Does anyone know by chance if you can get Opera 9.01 through one of the Ubuntu/Canonical repositories ? I've been waiting for a few days now but so far nobody bothered to upload the new version to the repos.

Cheers,
Erunno

It's quite strange that it hasn't been yet uploaded to Canonical repository..
But anyway, you can use deb.opera.com instead (if I remember the address correctly..)

---

### Post by _simon_ on 2006-08-08
You can download an ubuntu deb straight from the opera site that I linked to in the first post.

They have debs for:

6.06 Dapper Drake
5.10 Breezy Badger
5.04 Hoary Hedgehog
4.10 Warty Warthog

Here's the link again: [http://www.opera.com/download/?platform=linux](http://www.opera.com/download/?platform=linux)

Just select Ubuntu from the drop down menu.

---

### Post by Terracotta on 2006-08-08
> **_simon_ said:**
> You can download an ubuntu deb straight from the opera site that I linked to in the first post.

They have debs for:

6.06 Dapper Drake
5.10 Breezy Badger
5.04 Hoary Hedgehog
4.10 Warty Warthog

Here's the link again: [http://www.opera.com/download/?platform=linux](http://www.opera.com/download/?platform=linux)

Just select Ubuntu from the drop down menu.

It would be a wee bit easier if it showed up in the canonical commercial repositories.

---

### Post by _simon_ on 2006-08-08
Can't get much easier than download and double click ;)

---

### Post by Terracotta on 2006-08-08
> **_simon_ said:**
> Can't get much easier than download and double click ;)

True, but it's even easier to get a pop-up with: updates, click on it :D no need to search for anything :D

---

### Post by Vlatko on 2006-08-09
do i have to uninstall the 9.00 first?

---

### Post by Terracotta on 2006-08-09
> **_simon_ said:**
> Can't get much easier than download and double click ;)

> 
 True, but it's even easier to get a pop-up with: updates, click on it  no need to search for anything 


> 
do i have to uninstall the 9.00 first?



@ _simon_ see what I mean? (Not trying to be mean here though)

Not sure if you have to uninstall 9.00, uninstalling won't harm you anyway, while not uninstalling might harm your computer if you're not certain it won't.

---

### Post by Psquared on 2006-08-09
You can also get it through Automatix. Its pretty slick.

---

### Post by Erunno on 2006-08-10
I'm sorry for bothering you with this kind of newbie question, but how do I install the downloaded .deb file with aptitude ?

sudo aptitude install opera_9.01-20060728.6-shared-qt_en_i386

doesn't work for me.

Cheers,
Erunno

---

### Post by FISHERMAN on 2006-08-10
> **Erunno said:**
> I'm sorry for bothering you with this kind of newbie question, but how do I install the downloaded .deb file with aptitude ?

sudo aptitude install opera_9.01-20060728.6-shared-qt_en_i386

doesn't work for me.

Cheers,
Erunno

open a terminal
cd to your deb
sudo dpkg -i XXX.deb

---

### Post by CronoDekar on 2006-08-10
That's [Opera 90.1](http://operawatch.com/news/2006/08/opera-901-opera-is-moving-fast-&#8211;-really-fast.html)! ;)

---

### Post by Oreo on 2006-08-12
I used to be able to play Shockwave flash videos from Foxnews.com.
Now all I get is the audio.
I've tried reinstalling xine and the Macromedia flash player version 7.
My Tools/Advanced/Plugins seems to list the player fine, but all I get is audio.

Can anyone help?

Phil

---

### Post by Nightmist on 2006-08-12
Hasn't Opera 9.01 been out for over a week or something now? I checked some time ago, and decided to check again today if I could get the latest version with Synaptic or something, but no luck.

Was just wondering since I would rather upgrade it that way. Being a newb I'm not really sure how downloading and installing manually should work (do I have to uninstall the old one? how do I extract? etc.)

---

### Post by Colonel Kilkenny on 2006-08-13
> **Nightmist said:**
> 
Was just wondering since I would rather upgrade it that way. Being a newb I'm not really sure how downloading and installing manually should work (do I have to uninstall the old one? how do I extract? etc.)

You can just get a .deb file from opera.com.
Just choose Opera 9.01 for Linux i386 and then Ubuntu 6.06 Dapper Drake (or whatever version you are using)
Download that .deb to desktop and double click it and just install. No need to remove old install of Opera. Then you can remove the .deb-file.

---

### Post by Ziox on 2006-08-13
> **Nightmist said:**
> Hasn't Opera 9.01 been out for over a week or something now? I checked some time ago, and decided to check again today if I could get the latest version with Synaptic or something, but no luck.

Was just wondering since I would rather upgrade it that way. Being a newb I'm not really sure how downloading and installing manually should work (do I have to uninstall the old one? how do I extract? etc.)

Waiting for the upgrade is the best way, but as for installing from .deb package, just double click on it, if you are running dapper.

But, yeah...Opera's been out since the 8th or even earlier so...don't know why it is taking them so long...(but hey, great jobs guys anyway :D )

---

### Post by gkiller on 2006-08-22
Another week has passed... still no 9.01 in the commercial repository...

I e-mailed Canonical asking if they are going to put up the new version a few days ago, but no answer yet.

---

### Post by missmoondog on 2006-08-22
yeah, what's up with it still not being in the repositorys?

sheesh!!

---

### Post by Donnut on 2006-08-22
Thanks, just got it and firefox.

---

