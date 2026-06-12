---
title: "The new Gthumb is ruined!"
date: 2010-10-11
forum: The Cafe
---

### Post by futz on 2010-10-11
Installed Ubuntu 10.10 on a couple machines and quickly discovered that my favorite photo viewer has been ruined. I've used Gthumb since I started running Linux and always loved it. My Karmic machine has Gthumb v2.10.11 on it and it's fine. 

The new version is 2.11.3 and it SUCKS! They messed it up bad and turned a very nice program into an unuseable piece of junk.

And please don't suggest crap like F-Spot or Shotwell or Picasa or whatever. They're all useless to me. That kind of viewer is fine if you only have a few pics, but for really large collections they're worse than useless. I've tried them all - Gthumb was the only one that suited me and worked well. Now that may be gone forever... :frown:

---

### Post by Lucradia on 2010-10-11
Comparison screenshots please?

---

### Post by jcolyn on 2010-10-11
And what exactly is the issue with it?????

---

### Post by alphacrucis2 on 2010-10-11
I'm running the 2.12.0 version from the webupd8 ppa and I think it's great. What's the problem?

---

### Post by mjc1 on 2010-10-12
> **futz said:**
> The new version is 2.11.3 and it SUCKS! They messed it up bad and turned a very nice program into an unuseable piece of junk.

2.11.3 was an early release from a development series (months ago). Don't use it. If Ubuntu or Debian has packaged 2.11.3, file a bug report and tell them to use 2.12.0.

> And please don't suggest crap like F-Spot or Shotwell or Picasa or whatever. They're all useless to me.

Relax, and upgrade to 2.12.0.

If you still have problems, file bug reports with actual details upstream, at [http://bugzilla.gnome.org/enter_bug.cgi?product=gthumb](http://bugzilla.gnome.org/enter_bug.cgi?product=gthumb).

- Mike

---

### Post by philinux on 2010-10-12
2.11.3 is the default version in Maverick.

---

### Post by empty_spaces on 2010-10-12
I'm on Maverick using Gthumb 2.11.3.
Tried to edit an image yesterday, but just could not find the crop tool.
Ended up using Shotwell to crop the image. That was the first time that I have used Shotwell, and it worked out pretty well.

---

### Post by philinux on 2010-10-12
> **empty_spaces said:**
> I'm on Maverick using Gthumb 2.11.3.
Tried to edit an image yesterday, but just could not find the crop tool.
Ended up using Shotwell to crop the image. That was the first time that I have used Shotwell, and it worked out pretty well.

Top right. Icon looks like an artists palette. Click it and all will be revealed.

---

### Post by empty_spaces on 2010-10-12
> **philinux said:**
> Top right. Icon looks like an artists palette. Click it and all will be revealed.

Thanks.
I guess I missed it because Gthumb was not maximized, and I could only see the partial list of options for the palette

---

### Post by mjc1 on 2010-10-12
> **philinux said:**
> 2.11.3 is the default version in Maverick.

2.11.3 is old, and has a lot of bugs that have long since been fixed. The manual is completely out of date. Avoid it.

Grab 2.12.0 from the webupd8 ppa instead. You will be much happier.

- Mike

---

### Post by futz on 2010-10-12
> **mjc1 said:**
> 2.11.3 is old, and has a lot of bugs that have long since been fixed. The manual is completely out of date. Avoid it.

Grab 2.12.0 from the webupd8 ppa instead. You will be much happier.

- Mike
I went there and used the ppa, but all I can get right now is 2.11.5.

Anyway, I figured out how to get rid of that nasty Thumbnail Pane. That was my biggest problem with the newer version.

The other problem I still don't know how to fix - Image Preview is gone. It's Properties all the time now. I like my thumbnails real small so I can fit lots - I used to like the Image Preview.

Now that my initial shock over the changes is over I guess I can live with it. They've taken away some features I used to occasionally use, but I mostly used Gimp for any real editing anyway, so that's not a big deal. 

EDIT: Oops! Just found them. You have to be viewing a picture before the editing option shows up. Slightly strange, but no problem once you know about it.

EDIT2: Anyone know where to set the keyboard options so I can just hit the 0 key (like I used to) to open the selected pic or pics in Gimp (or whatever program I set for that hotkey)?

---

### Post by Phrea on 2010-10-13
[This]("http://ftp.debian.org/pool/main/g/gthumb/")?

---

### Post by nilarimogard on 2010-10-13
> **futz said:**
> **I went there and used the ppa, but all I can get right now is 2.11.5.**

Anyway, I figured out how to get rid of that nasty Thumbnail Pane. That was my biggest problem with the newer version.

The other problem I still don't know how to fix - Image Preview is gone. It's Properties all the time now. I like my thumbnails real small so I can fit lots - I used to like the Image Preview.

Now that my initial shock over the changes is over I guess I can live with it. They've taken away some features I used to occasionally use, but I mostly used Gimp for any real editing anyway, so that's not a big deal. 

EDIT: Oops! Just found them. You have to be viewing a picture before the editing option shows up. Slightly strange, but no problem once you know about it.

EDIT2: Anyone know where to set the keyboard options so I can just hit the 0 key (like I used to) to open the selected pic or pics in Gimp (or whatever program I set for that hotkey)?

That's impossible, the Ubuntu 10.10 gThumb version in the PPA is 2.12.0: [https://launchpad.net/~webupd8team/+archive/gthumb/+packages]("https://launchpad.net/~webupd8team/+archive/gthumb/+packages")

So unless you're running Karmic (but in the first post you said you're using Maverick), using the PPA will install gThumb 2.12.0

---

### Post by futz on 2010-10-13
> **nilarimogard said:**
> That's impossible, the Ubuntu 10.10 gThumb version in the PPA is 2.12.0: [https://launchpad.net/~webupd8team/+archive/gthumb/+packages]("https://launchpad.net/~webupd8team/+archive/gthumb/+packages")

So unless you're running Karmic (but in the first post you said you're using Maverick), using the PPA will install gThumb 2.12.0
Ahhhh!!! The light goes on! :p Yes, I used that ppa on my Karmic install. I don't use those other (Maverick) machines much (one was built for someone else and is shipping out probably today - she'll be thrilled with 2.11.3). So today I'll install 2.12.0 on the other one and test it out. Thanks for the slap upside the head. :D

---

### Post by mjc1 on 2010-10-15
> **futz said:**
> EDIT: Oops! Just found them. You have to be viewing a picture before the editing option shows up. Slightly strange, but no problem once you know about it.

EDIT2: Anyone know where to set the keyboard options so I can just hit the 0 key (like I used to) to open the selected pic or pics in Gimp (or whatever program I set for that hotkey)?

Pressing "e" opens the editing mode for the selected image in gThumb.

Pressing "g" opens the selected image(s) in the Gimp.

- Mike

---

### Post by futz on 2010-10-15
> **mjc1 said:**
> Pressing "e" opens the editing mode for the selected image in gThumb.

Pressing "g" opens the selected image(s) in the Gimp.

- Mike
Perfect! Thanks Mike. :)

---

### Post by night-wing on 2010-10-18
Hi.
Is there a way to install the "old" gthumb (with picture preview) in maverick? I tried to do this with the .deb - packages from lucid/karmic manually, but gthumb hangs, when I swith to a folder with .jpg - files.
The new gthumb is horrible for me...

---

### Post by Zoot7 on 2010-10-18
You could always grab the source for an older version of it, and tell apt not to upgrade it with an **aptitude hold gthumb**.

---

### Post by night-wing on 2010-10-18
The old gthumb does not work with maverick. It hangs up...

---

### Post by del_diablo on 2010-10-18
Outdated dev package in my stable Ubuntu?
[http://ubuntuforums.org/showthread.php?t=1587178](http://ubuntuforums.org/showthread.php?t=1587178)
I think I won the topic.

---

### Post by almich on 2010-10-21
I also updated to maverick recently an I am now using gthumb 2.12.0. A feature I very often used in the old versions was to move an image to another folder by right clicking and selecting &quot;Move&quot;. Unfortunately this feature disappeared. Sometimes I also used drag and drop to move images. Drag and drop still works in the new version, but images are no longer moved but they are copied. Does anybody know, if the possibility to move an image is hidden so well or if it's no longer present?

---

### Post by mjc1 on 2010-10-21
> **almich said:**
> I also updated to maverick recently an I am now using gthumb 2.12.0. A feature I very often used in the old versions was to move an image to another folder by right clicking and selecting &quot;Move&quot;. Unfortunately this feature disappeared. Sometimes I also used drag and drop to move images. Drag and drop still works in the new version, but images are no longer moved but they are copied. Does anybody know, if the possibility to move an image is hidden so well or if it's no longer present?

You are supposed to use cut and paste. That is, use Ctrl+X to cut the selected files, navigate to the destination folder, and press Ctrl+V to paste them.

I'm not a fan of that approach, but that's the current situation. Hopefully, someone will code a copy/move plugin similar to the 2.10.x dialogs...

- Mike

---

### Post by proteusmoteus on 2010-10-28
Got previous gthumb version working in 10.10. Download both [gthumb]("http://packages.ubuntu.com/karmic/gthumb") (@ bottom of page) and [gthumb-data]("http://packages.ubuntu.com/karmic/all/gthumb-data/download"). Install with 'sudo dpkg -i gthumb*'.

My main complaint was lack of preview pane. Used gthumb w/ directory list on top left, file list below (no thumbs) and a big preview pane to the right. W/o a preview pane the main way I viewed images is gone. Currently sticking w/ old version, but others might be interested in trying geeqie (previously called gqview) which can also compare pictures to locate duplicates.

---

### Post by Schrute Farms on 2010-10-28
> **almich said:**
> Sometimes I also used drag and drop to move images. Drag and drop still works in the new version, but images are no longer moved but they are copied. Does anybody know, if the possibility to move an image is hidden so well or if it's no longer present?

Drag the file(s) over to the folder where you want to move them.  Before you let go of the mouse button, press shift (or maybe control) you will see an arrow appear over the cursor.  That will make it a move & not copy.

I'm not too fond of the changes to Gthumb either.  It still does everything I need it to, they just moved stuff around & made some stuff a little harder to do.  I thought that maybe I'd get used to it, but I'm thinking about downgrading back to the older version.

---

### Post by futz on 2010-10-28
> **Schrute Farms said:**
> Drag the file(s) over to the folder where you want to move them.  Before you let go of the mouse button, press shift (or maybe control) you will see an arrow appear over the cursor.  That will make it a move & not copy.
Ya, drag and drop is fine for some things, but I'm often sorting many directories of pics into many other main directories. I often can't see the destination directory from where the source dir is. I have many large hard drives and several other machines on the network, as well as a file server. Pics are sorted to and from various places on all these machines. The old move and copy commands with the recently used directory list were a HUGE time saver. I want them back!!!

> I'm not too fond of the changes to Gthumb either...
...I thought that maybe I'd get used to it, but I'm thinking about downgrading back to the older version.
Me too.

The new version is super lazy slow too. Takes forever to read directories and display thumbs, and pic display has slowed drastically as well. I'm real unhappy with it.

Seems like the developers are starting to gradually move towards making it just another useless small-collection viewer. There are too many of those already. They're fine for casual users with small pic collections, but useless for me.

Gthumb was good. Now it **sucks**. I still use it, but if it gets any worse I'm on the hunt for a better viewer program (already am, actually).

--------------------------

EDIT: I remember when Amarok did something stupid like Gthumb is doing. They took an excellent program (v1.4) and totally destroyed it (v2.0).

---

### Post by george1984 on 2010-10-29
proteusmoteus.....

Thanks for the instructions. I now have Gthumb 2.10 working in Maverick. Having to use the new version (actually I upgraded to 2.12 using the ppa) was spoiling Maverick for me.

futz.....

I am still gratefully using Amarok 1.4 using Bogdan's ppa. Loosing this would be a disaster. Gthumb seems to be abandoning its distinctive character in a similar way. Oh Dear.

---

### Post by proteusmoteus on 2010-10-29
Figured out how to keep update-manager from trying to update my preferred gthumb version.

Using aptitude to hold packages is [apparently broken]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/75332"). So the recommended command would be:

```
echo "gthumb hold" | sudo dpkg --set-selections
echo "gthumb-data hold" | sudo dpkg --set-selections
```

---

### Post by futz on 2010-10-30
Found yet another complaint with the newer Gthumb: When I select multiple pics to edit in Gimp and hit G, instead of opening all the pics in a single instance of Gimp like it used to, now the stupid thing starts one instance of Gimp per pic! Ridiculous! Good thing I have lots of RAM. :P

In the old Gthumb I could have gone to a menu and edited that so it worked right. That option is not available in the newer Gthumb (it's probably buried in a config file somewhere).

EDIT: Couldn't take it anymore. Switched back to 2.10.11 last night and I'm staying there. It's a far superior program to the newer versions.

---

### Post by JeanTONIC on 2010-11-01
Thanks [proteusmoteus]("http://ubuntuforums.org/member.php?u=1007538") ; after 2 weeks wandering. I finally found the solution to have my gthumb with preview, slideshow and old catalogs.
Incredible this evolution of a good product.

---

### Post by HankB on 2010-12-02
> **JeanTONIC said:**
> Thanks [proteusmoteus]("http://ubuntuforums.org/member.php?u=1007538") ; after 2 weeks wandering. I finally found the solution to have my gthumb with preview, slideshow and old catalogs.
Incredible this evolution of a good product.

Me too!

I tried the New and Improved gthumb this morning and had a pretty negative response. There was no slideshow button. I actually opened help and found that I could add it to the toolbar by going to edit -> toolbar. But there was no toolbar item in the edit menu. Not wanting to be one who goes back, I installed the newer and improveder version from the ppa. The toolbar was even more sparse. And it would not even display pictures. Go full screen and the selected image showed up as a thumbnail thoughtfully centered in the middle with no visible way to enlarge it. W-T-F!

I'm happy to see developers actively trying to improve their product but in this case there seem to be several huge backward steps.


Thanks, proteusmoteus, for your help getting the older version installed.

Edit: I spoke too soon. the old gthumb segfaults while opening directories with many images. :(

best,
hank

---

### Post by madjr on 2010-12-02
this is an example of why they are going to change things with the software center . they are tired of repackaging other peoples software (and limiting the authors)

[http://www.youtube.com/watch?v=GT5fUcMUfYg](http://www.youtube.com/watch?v=GT5fUcMUfYg)

---

### Post by mjc1 on 2010-12-02
> **HankB said:**
> Me too!

I tried the New and Improved gthumb this morning and had a pretty negative response. There was no slideshow button.

There should be. There is in mine (though I run Fedora 14). Check that you have the slideshow extension enabled in Edit>Extensions.

> I actually opened help and found that I could add it to the toolbar by going to edit -> toolbar. But there was no toolbar item in the edit menu.

Huh? Where in the gThumb help file does it say that? Can you post a screenshot of that? (I ask because I wrote the gThumb help file in 2.12.x.)

> Not wanting to be one who goes back, I installed the newer and improveder version from the ppa. The toolbar was even more sparse. And it would not even display pictures.

It wouldn't show any pictures? Weird. Again, check that everything is enabled in Edit>Extensions.

- Mike

---

### Post by HankB on 2010-12-02
> **mjc1 said:**
> There should be. There is in mine (though I run Fedora 14). Check that you have the slideshow extension enabled in Edit>Extensions.



Huh? Where in the gThumb help file does it say that? Can you post a screenshot of that? (I ask because I wrote the gThumb help file in 2.12.x.)



It wouldn't show any pictures? Weird. Again, check that everything is enabled in Edit>Extensions.

- Mike
Hi Mike,
The first two issues you asked about were with the version that ships with Maverick. The last was with 2.12.1.

I found and deleted all of my gthumb configuration files (~/.config/gthumb ~/.gconf/apps/gthumb ~/.gnome2/gthumb) and had another go with 2.12.1. On the first startup I found that all extensions were disabled. I enabled some and find that I can now view images. (It seems like a confusing default to not enable image viewing for an image viewer, but thanks for your tip to fix that.)

Thanks for your help.

---

### Post by mjc1 on 2010-12-02
> **HankB said:**
> On the first startup I found that all extensions were disabled.

Probably this bug: [http://bugzilla.gnome.org/show_bug.cgi?id=635475](http://bugzilla.gnome.org/show_bug.cgi?id=635475)

2.12.2, when released, should have the fix.

- Mike

---

### Post by proteusmoteus on 2010-12-02
@[HankB]("http://ubuntuforums.org/member.php?u=4414") to resolve crashing of gthumb 2.10

After [mjc1]("http://ubuntuforums.org/member.php?u=251109")'s advice about extensions I tried out the latest gthumb to see if I could customise away my dislikes now. After some experimentation I tried to roll back to gthumb 2.10.11 and experienced the crashing problem you did.

Eventually I tracked down the crashing problem to a *.comments *that gthumb creates in some picture directories. The newer gthumb version must have made it incompatible w/ gthumb 2.10.

Try running 'find ~/pics -name .comments' to search for and remove this item in subdirectories of the appropriate parent.

---

### Post by mjc1 on 2010-12-02
> **proteusmoteus said:**
> 
Eventually I tracked down the crashing problem to a *.comments *that gthumb creates in some picture directories. The newer gthumb version must have made it incompatible w/ gthumb 2.10.

Try running 'find ~/pics -name .comments' to search for and remove this item in subdirectories of the appropriate parent.

Or use gThumb 2.10.12 (not 2.10.11).

2.10.12 was specifically released to fix that problem.

- Mike

---

### Post by keepitsimpleengr on 2010-12-03
Gthumb has a PPA for ubuntu for it's newly released version 2.12.1.

See [http://www.webupd8.org/2010/09/gthumb-2120-stable-has-been-released.html]("http://www.webupd8.org/2010/09/gthumb-2120-stable-has-been-released.html")

I deleted the 2.11&#8943; version from the ubuntu 10.10 (Linux-x86_64), added the repository and installed 2.12.1.

In this version, 2.12.1, slideshows are an extension, and must enabled.  They worked for me. :D

However, 2.12.1 does not support multiple x-screens (multiple monitors) as prior version did.  All full screen views open on the screen where the initial gthumb was launched, bug filed. :eek:

---

### Post by kvant on 2010-12-03
Sorry if this was said before, but I wanted to say that:

Gthumb is awesome! One of my favourite GNU/Linux apps.

The other thing is that the new version  that you can get through the PPA that somebody mentioned a post or two ago has many new and very nice features.

You can batch rename files with very easy interface too etc.

---

### Post by inTooManyForums on 2010-12-13
I too want to beat up on the new gThumb.
I just installed Ubuntu 10.10. I pulled gThumb 2.11 off of the SPM.
There's no preview pane!?! 
I tried to install gThumb 2.12 but the dependency try for GTK2 seems truly messed up.
I installed the recommended GTK+-2.0-dev. This got me even more dependency failures.
I tried installing earlier versions but got similarly long lists of dependency failures.
I tried random loads of ANYTHING with GTK2 similarity (incl gtk#) without success.
I'm currently assuming the preview pane absence is due to QUIET dependency failures. I dearly hope I'm wrong on that.
Other gThumb design complaints:
Putting an entire directory tree in the upLeft pane competes with display real-estate for a large preview pane.
Putting "Catalogs" as a psuedo directory entry does this also. And it confuses the issue as to the purpose of the upLeft pane. Does it list files or does it list concepts?
When pictures or media names get duplicated into the "Pictures" concept, am I duplicating disk space or is there a file list somewhere?
This pane also lists devices !?! Why would I want that in software for browsing pictures???? Why can't I just organize by categories? And WHY WOULD I *EVER* WANT TO MIX CATALOGS, FILES, DEVICES, AND A GLOBAL PICTURES LIST ?????
And why should clicking on a picture bring up a "Properties" pane? This pane is a muddled list of meta-data and misc file info provided by Nautilus...or any other file browser.
Worse, this list is headed by a drop-down menu with only one item???? Why????
Now lets move on to the icon list.
Not as much changed here, but it seems to have the same fuzzy catch-all design thinking....doing everythiing from everywhere.
Why do I want an extremely specific button "Organize" by date, that I won't push very often that does just one thing (duplicating pictures into dates) that I personally never want to do? Shouldn't that go into a menu somewhere that won't use display real-estate? Further, this button alone is the only reason for the entire title pane for the icons pane...excpt for the folder name that is duplicated elsewhere....and another button (that I forget) that I don't usually want.
If you REALLY INSIST on this mostly useless button, shouldn't it go in the toolbar????
Jeez, I hate this new design.
Things that could be really handy might include a larger list of keyboard shortcut keys properly grouped on the keyboard. But, remarkably, this list got shorter. I can now do less with simple keystrokes.
The "Extensions" idea would seem to have merit. But 99% of the extensions are already turned on!?! Further, most of those "Extensions" consist of features that already existed in prior versions...LMAO. I assume this is so I can TURN OFF more features that I have come to know and love about earlier gThumb versions.
BTW: One of the things I've always liked about gThumb (over file browsers) is the limited whitespace between thumbnails...so I can see many pictures at once. Don't touch that!
And please give us back the preview pane.
I still haven't listed all the truly awful design decisions in this new gThumb. I've already made too many  enemies among you.
But the original poster of this thread is correct. Please consider just throwing away these recent "improvements" and return to simple.
Please?

---

### Post by mjc1 on 2010-12-13
> **inTooManyForums said:**
> I tried to install gThumb 2.12 but the dependency try for GTK2 seems truly messed up.

The whole point of the gThumb rewrite was to get rid of the dependency on old obsolete libraries and move to the new ones (libexif to exiv2, gnome-vfs to gfile/gio/gvfs, remove bonobo, etc...), so you will need a quite recent version of gtk. No surprise there. If the Debian or webupd8 packager has messed up the dependencies, please contact the packager with a bug report.

> Putting an entire directory tree in the upLeft pane competes with display real-estate for a large preview pane.
Lots of users, including me, asked for a tree view, and I'm delighted to have it. If you dislike it, grab the vertical divider bar and shrink its size to zero.

> This pane also lists devices !?! Why would I want that in software for browsing pictures????
Because sometimes the pictures are on devices. Take cameras for example. Often you will find photos on cameras...

> And why should clicking on a picture bring up a "Properties" pane? This pane is a muddled list of meta-data and misc file info provided by Nautilus...or any other file browser.
No, it is primarily a display of exif and xmp metadata. Nautilus doesn't show you that. Serious photographers care deeply about the embedded metadata, which records the shooting conditions (shutter speed, aperture) and other info (copyright, author, location, gps coords, ...)

> Worse, this list is headed by a drop-down menu with only one item???? Why????
To accommodate future functions - for example, if a user implemented a geotagging plug-in, a map widget could be added here. Or perhaps a preview pane.

> Now lets move on to the icon list.
Not as much changed here, but it seems to have the same fuzzy catch-all design thinking....doing everythiing from everywhere.
I don't follow you here. What's fuzzy about the icon list?

> Why do I want an extremely specific button "Organize" by date
<snip>
If you REALLY INSIST on this mostly useless button, shouldn't it go in the toolbar????
Jeez, I hate this new design.
I agree that the "Organize" UI could be improved, though I personally don't use it. But it doesn't provoke rage in most users. Perhaps you could submit a patch, or if coding isn't your thing, a sketch or mockup of a better layout.

> Things that could be really handy might include a larger list of keyboard shortcut keys properly grouped on the keyboard. But, remarkably, this list got shorter. I can now do less with simple keystrokes.
Not so remarkable - rewriting an entire program tends to be a lot of work, and refinements like keyboard shortcuts will get missed in the initial passes, as the developer focuses on core functions. Why don't you submit a patch, or a suggested list of keyboard improvements? The upstream bugzilla is the appropriate place for that: [https://bugzilla.gnome.org/enter_bug.cgi?product=gthumb](https://bugzilla.gnome.org/enter_bug.cgi?product=gthumb)

> The "Extensions" idea would seem to have merit. But 99% of the extensions are already turned on!?! Further, most of those "Extensions" consist of features that already existed in prior versions...LMAO.
LMAO? Why? The code was completely rewritten in a modular form, to reduce complexity, make maintenance easier, to ensure that the plugin structure was flexible enough to actually work for most use cases, and to provide examples of how to implement plugins.

How would you have done it?

> I assume this is so I can TURN OFF more features that I have come to know and love about earlier gThumb versions.
Yes, if you wish to minimize the memory and resource footprint of gThumb, you can now disable unused features.

> And please give us back the preview pane.
Lots of people have mentioned that, I imagine that the main developer will consider it. You could make inquiries on the gThumb mailing list.

> I still haven't listed all the truly awful design decisions in this new gThumb. I've already made too many  enemies among you.

Well, long negative rants where the user says they're LMAO about the plugin structure tend not to be appreciated, unless from someone who has already earned respect by contributing code, patches, or generally useful suggestions. Especially in projects that are entirely produced by volunteers. Just saying.

Personally, I didn't like the cumbersome file copy/move procedure in the new version, so I paid someone to write a patch to re-implement something similar to the old dialog, and the main developer has accepted the patch into git master. Somehow, I missed the step where you say the software SUCKS and the developers are IDIOTS for not implementing my FAVORITE feature and WRECKING everything that was GOOD and HOLY about the old the gThumb, and now I have to use WINDOWS to see my LOLCAT photos, GEEZ! :biggrin:

- Mike

---

### Post by ridgeland on 2010-12-13
Thanks futz for this thread.  I stopped using gthumb because the new version as you said:
> The new version is 2.11.3 and it SUCKS!
I saw Update-Manager installing an updated version I tried again.  Searching here for how to install the good old version I found the comments by Mike (mjc1).  Yeah! Thanks Mike for coming to gthumb's rescue. 
Edit -> Extensions
and now the new version has all the old did plus more.

Now my favorite image viewer is back!

Mike, please get a splash screen going so when an install has 0 extensions a splash screen suggests to the user that much more functionality is available by just turning on extensions.  I think Ubuntu dropped the ball on this one.

---

### Post by mjc1 on 2010-12-13
> **ridgeland said:**
> Now my favorite image viewer is back!

Mike, please get a splash screen going so when an install has 0 extensions a splash screen suggests to the user that much more functionality is available by just turning on extensions.

Not a bad idea, I've filed an enhancement request at [http://bugzilla.gnome.org/show_bug.cgi?id=637149](http://bugzilla.gnome.org/show_bug.cgi?id=637149).

- Mike

---

### Post by inTooManyForums on 2010-12-13
Sorry for the long negative rant.
My app area is astrophotography and other scientific image processing and image perception with ai. I'm working on a thesis in mathematical inference. Yes, I've written a lot of code in many languages, incl C++. I prefer larger paradigms. So I was really attracted to categorical classification as gThumb has.
And, yes, I confess I like LOLCAT photos too :)
My reaction has been shock and dismay when I watched a lot of investment in gThumb suddenly vaporize. I'll try to be more focused and objective.
I suspect it is premature to suddenly offer code suggestions. I would prefer to discuss philosophy since this version seems to represent the beginning of significant philosophical departure.
In a nutshell, an image organizing system is really hard to design (not telling you anything here). Its just that the Maslowes hierarchy of needs just for image handling (not processing) is a BIG problem. My list is something like:
1) Flexibility for all the different types of users
2) Display real estate management
3) simple operation (one hand?)
4) speed (needs to be higher up?)
5) really simple image processing with quick/easy/flexible interface to Gimp (or that other commercial system).
etc.
I can think of several design improvements/additions for each of the above. But this is meant to be only a short response.
So I have a question: What is the best way to submit philosophy, design, wishlists, with code to follow? i.e. to profitably engage...assuming I haven't totally pissed everybody off already.

---

### Post by mjc1 on 2010-12-13
> **inTooManyForums said:**
> My list is something like:
1) Flexibility for all the different types of users

The main gThumb developer generally prefers to keep the number of configuration options to a minimum. However, there is still room to make the UI more flexible; just don't expect to be able to add 15 checkboxes in the preferences dialog.

Everyone likes UI improvements, sensible keyboard shortcuts, speed increases (that's hard though!), etc.

> 
5) really simple image processing with quick/easy/flexible interface to Gimp (or that other commercial system).


You know that pressing "g" opens Gimp, right? (And pressing "e" opens the internal tools.) Tighter integration with the Gimp is unlikely, I suspect.

> So I have a question: What is the best way to submit philosophy, design, wishlists, with code to follow? i.e. to profitably engage...assuming I haven't totally pissed everybody off already.

If you have a coding idea you'd like to get feedback on, you can talk to the developers at the gthumb mail list: [http://mail.gnome.org/mailman/listinfo/gthumb-list](http://mail.gnome.org/mailman/listinfo/gthumb-list)

Feature requests and bug reports go to the gnome bugzilla.

Patches are best posted to the bugzilla, although small patches can go to the mail list too.

Hope this helps! Not that many people actively contribute code to gThumb, so new contributors are always welcome! (I do not remember ever receiving patches from Canonical, for example...)

For people who aren't natural coders, the manual could use some work - copying the existing format isn't too hard.

- Mike

---

### Post by mjc1 on 2010-12-13
I forgot to say: please see [http://live.gnome.org/gthumb/development](http://live.gnome.org/gthumb/development) for the basic info about developing code for gThumb.

- Mike

---

### Post by nilarimogard on 2010-12-14
> **ridgeland said:**
> Thanks futz for this thread.  I stopped using gthumb because the new version as you said:

I saw Update-Manager installing an updated version I tried again.  Searching here for how to install the good old version I found the comments by Mike (mjc1).  Yeah! Thanks Mike for coming to gthumb's rescue. 
Edit -> Extensions
and now the new version has all the old did plus more.

Now my favorite image viewer is back!

Mike, please get a splash screen going so when an install has 0 extensions a splash screen suggests to the user that much more functionality is available by just turning on extensions.  I think Ubuntu dropped the ball on this one.

A lot of the extensions are enabled by default, however there was a bug in a recent version which caused all the extensions to be disabled by default. That's fixed in the latest version (in Debian and the [WebUpd8 gThumb PPA]("https://launchpad.net/~webupd8team/+archive/gthumb"))

---

### Post by mjc1 on 2010-12-15
> **futz said:**
> Found yet another complaint with the newer Gthumb: When I select multiple pics to edit in Gimp and hit G, instead of opening all the pics in a single instance of Gimp like it used to, now the stupid thing starts one instance of Gimp per pic! Ridiculous! Good thing I have lots of RAM. :P

That particular bug has been fixed. The fix will be in 2.12.2.

- Mike

---

### Post by hirumono on 2011-01-12
I am sorry to agree with the title of this topic. My personal preference for gThumb, which I have been using for many years with utter satisfaction, seems to be gone, as the main reason for its use - simple, powerful features - is no more. I was surprised - pleasurably so - to see the new interface when I installed it on my new Ubuntu 10.10: the new thumbnails row on the lower part of the screen is pretty, though of limited use with big folders. I started working on my picture collection and I realized that something was missing: the lack of a preview pane was pretty much strange in a picture manager, but I could live with it just by enlarging the thumbnails size. But then I noticed that my main tools, namely the 'Copy to' and 'Move to' menu items, were missing, too. A fast search on Google showed that these features were gone for good, because the main developer wanted so. I respect his decision; in fact, this is *his* program. On the gThumb mailing list he answered the question of those missing features by saying that "cut and paste is the preferred way to move files." Good to know.
I tried to work with gThumb with the 'new' tools - cut, copy and paste - but after a while I had to give up. These commands are just toys, useful for unexperienced people who may have some dozens of pictures to sort out - not thousands of them.
To sum it up, it seems that gThumb has lost its powerful features to follow the mass of Mac-style, elegant, pretty, stupid 'apps' so many people seem to love. I cannot say anything but thanks to the developer for all the good work with a simple, efficient, *free* (let's remember this) software. But I wonder: must developers afford some kind of costs to maintain features that time has shown to be useful and appreciated? 
Sorry if this looks like a rant; in fact, it is just my personal goodbye to a wonderful program that seems to have followed the 'happy puppy' trend.

---

### Post by sdowney717 on 2011-01-12
so what program is good to use instead?

I see similar things with my kin2m phone and the MS zune software. brain dead with no way to view the files in explorer.
so your forced to do the 'sync' option to mirror the files or you can drag them one at a time. then after you drag them they reorient in the display page so you got to scroll back down to where you were. it is just awful pain to use. IMO.

---

### Post by mjc1 on 2011-01-12
> **hirumono said:**
> the lack of a preview pane was pretty much strange in a picture manager, but I could live with it just by enlarging the thumbnails size.

A lot of people have asked for the preview pane; I expect it will return. The properties widget only shows metadata at the moment, but it has been set up to accept other modes, like a preview.

> But then I noticed that my main tools, namely the 'Copy to' and 'Move to' menu items, were missing, too. A fast search on Google showed that these features were gone for good, because the main developer wanted so.

Not quite correct. I submitted a patch to re-add the copy/move dialogs, and it has been accepted. You can check out git master if you know how. Otherwise, wait, it will return in the series after 2.12.x.

> To sum it up, it seems that gThumb has lost its powerful features to follow the mass of Mac-style, elegant, pretty, stupid 'apps' so many people seem to love.

2.12.x was a total rewrite of gThumb - it was badly needed for a variety of reasons that were obvious to anyone familiar with the code.

The new modular code accepts plugins, incidentally, for anyone who wishes to add a feature. Like a preview pane, for example. Hint, hint. :D

- Mike

---

### Post by hirumono on 2011-01-12
> **mjc1 said:**
> A lot of people have asked for the preview pane; I expect it will return. The properties widget only shows metadata at the moment, but it has been set up to accept other modes, like a preview.

Yes!! That's really good news!  :)

> **mjc1 said:**
> Not quite correct. I submitted a patch to re-add the copy/move dialogs, and it has been accepted. You can check out git master if you know how. Otherwise, wait, it will return in the series after 2.12.x.

This is WONDERFUL news!!  :D  I must say that I didn't expect this after Paolo's (pretty much definitive) answer on the mailing list... I am very happy to hear that there's still room for those quick-and-powerful features!
I can only thank you for your work and your (really) fast reply!!!  :D


> **mjc1 said:**
> 2.12.x was a total rewrite of gThumb - it was badly needed for a variety of reasons that were obvious to anyone familiar with the code.

The new modular code accepts plugins, incidentally, for anyone who wishes to add a feature. Like a preview pane, for example. Hint, hint. :D 

I hope the new code will allow gThumb to become even more powerful and versatile. Thank you very much, you really made my day!

---

### Post by koleoptero on 2011-01-12
I'd like to say that I am in total disagreement with the topic. Then new gthumb is an absolute improvement over the old one imo, and I love using it, which i have been doing ever since it came on the webupd8 ppa (8 months ago iirc).

Of course sicne it's been rewritten there are bugs but that's to be expected.

I hope the developers keep up the good work.

---

### Post by mrpenguin on 2011-03-25
I dont like the bottom viewer of the entire folders pictures ... whatever its called.
Because of the bottom part I cant see the full picture and have to move it down to see all of the picture ... I hate that

How do I get rid of the bottom part so that its like the previous version ... when I click on a photo to open then I see the entire picture ??

---

### Post by ridgeland on 2011-03-25
Turn off
View -> [ ] Thumbnail Pane

---

### Post by hirumono on 2011-03-27
Or you can press F11 to go full screen after launching GThumb. There's no way to start full screen (yet), but this may be a quick workaround for now.

EDIT: I just found out that you can reposition the thumbnail vertically pane on the left instead of the bottom of the screen.
Just go to Preferences, it's the second pull-down menu.

A big THANK YOU for restoring the "Copy to" and "Move to" menus in gThumb! YAY!!!  :D

---

### Post by ridgeland on 2011-03-27
Opening window size can be adjusted using the Gnome configuration editor.  Just open it and Find gthumb there find the gthumb/ui entry.  Then change window_height and window_width to whatever size you want.

---

### Post by mrpenguin on 2011-03-27
> **ridgeland said:**
> Turn off
View -> [ ] Thumbnail Pane

So easy ! Thanks :D

---

### Post by futz on 2011-06-11
> **mjc1 said:**
> A lot of people have asked for the preview pane; I expect it will return.
That would be very nice. I'm currently using v2.13.1 and not very happy. Gthumb has become **very** slow, both when loading directories of thumbs and (worst of all) when viewing pics. Very annoying. It used to be snappy-quick. I should not be waiting for anything on a machine like I'm running, but I wait for Gthumb now.

> Not quite correct. I submitted a patch to re-add the copy/move dialogs, and it has been accepted.
Ah, I see them there. I'll have to test them out and see if they're as good as in the old, good Gthumb.

---

### Post by eric-yorba on 2011-06-11
> **futz said:**
> And please don't suggest crap like F-Spot or Shotwell or Picasa or whatever. They're all useless to me. That kind of viewer is fine if you only have a few pics, but for really large collections they're worse than useless.
Just for reference, how many photos do you have?  I know we have Shotwell users that have well over 10,000 photos who run without a hitch.

---

### Post by futz on 2011-06-11
> **eric-yorba said:**
> Just for reference, how many photos do you have?  I know we have Shotwell users that have well over 10,000 photos who run without a hitch.
Heh :D "[COLOR="Red"]Well over 10,000[/COLOR]" is what I consider to be "[COLOR="Red"]only a few pics[/COLOR]".

I just did a rough count on this machine alone - somewhere around 907,000 pics and rising. :) There are lots more on other machines on my network.

---

### Post by eric-yorba on 2011-06-13
> **futz said:**
> Heh :D "[COLOR=Red]Well over 10,000[/COLOR]" is what I consider to be "[COLOR=Red]only a few pics[/COLOR]".

I just did a rough count on this machine alone - somewhere around 907,000 pics and rising. :) There are lots more on other machines on my network.

What happens when you try to import that makes Shotwell unusable?

---

### Post by futz on 2011-06-13
> **eric-yorba said:**
> What happens when you try to import that makes Shotwell unusable?
Hehehehehe:P

I don't have a year to wait for it to import all those pics. I've never understood the reason some pic viewers want to "import" pics. What is the point? The pics are just fine in the directories they're already in. They're already organized the way I want them. Why import them?

Any pic viewer that wants to import my pics gets dumped quick. I don't have time for that foolishness. I've always used Gthumb, or back when I used Windoze, ThumbsPlus, or viewers like that. Just navigate to the directories where my pics are and view or organize from there. Simple and fast.

I was playing with Shotwell the other day and it imported hundreds, if not thousands of little symbol/icon things from some stupid game I have installed. I didn't ask it to, and I don't know if I should tell it to "Move to Trash". Has it made copies of them all so if I trash them the game doesn't break? And if it has made copies of every pic it imported isn't that a huge waste of drive space? Hundreds of gigs on this machine to make duplicate copies to make Shotwell happy?

---

### Post by eric-yorba on 2011-06-14
> **futz said:**
> I was playing with Shotwell the other day and it imported hundreds, if not thousands of little symbol/icon things from some stupid game I have installed. I didn't ask it to, and I don't know if I should tell it to "Move to Trash". Has it made copies of them all so if I trash them the game doesn't break? And if it has made copies of every pic it imported isn't that a huge waste of drive space? Hundreds of gigs on this machine to make duplicate copies to make Shotwell happy?

There's only one way that could have happened -- your pictures folder was set to something strange, like your home directory or /

In that case Shotwell would consider the files as being inside its library, so it would not make a copy of the images.  Shotwell has its own trash, which doesn't actually move files on the disk; rather it just remembers that you trashed the photo from within Shotwell.

---

### Post by michaelwilliamson on 2011-08-01
Ok, so I understand the need for a rewrite, but the new version isn't as snappy!

IS there any way at all to get it to open multiple instances when double clicking on associated files?

This is a crucial feature for me and is sorely missed!

I know I can open new windows from the menu, but I really need to set my preference to always open new windows!

---

### Post by zazuge on 2011-09-15
well I agree with the title from my POV
and i understand the developers perspective too (combinatory explosion, dependency hell and other nightmarish creatures of the programming dungeon )
but It's not good to break the user experience
It was preferable to wait (or fork) a major version for this rewriting because it removes alot of the old gthumb features

when people jump from a minor version to another they expect the features and experience is the same
 
and the last thing i deplore the loss of custom commands key bindings 
i used to select the best photos by using the approve custom command
now i don't see anything similar in the new version
oh well i returned back to the old version thanks to some tips in this thread
I'll wait until the new gthumb had matured enough

---

### Post by mjc1 on 2011-09-16
> **zazuge said:**
> and the last thing i deplore the loss of custom commands key bindings

Click the Tools button, then Personalize.

> I'll wait until the new gthumb had matured enough

Well, 2.13.90 has just been released, in preparation for the 2.14.x stable series.

- Mike

---

### Post by fixerdave on 2011-09-24
Well, I can't say I'm happy with the way the new gThumb rolled out...  but such is life.  It's not like I can ask for my money back ;)

But, I would be interested in a few pointers.  I can get gThumb 2.13 on my workstation by using the PPA, but not for my media server.  Sigh...  It happens to be an old Mac Mini running Ubuntu 10.10 -- yeah, PowerPC.  It works fine except I can't get gThumb to do a slideshow.  It's stuck on v2.11.3 and there's just no option for a slideshow, none, nothing in the extensions, nada.  I'm making the assumption that the slideshow extension relies on something that just isn't available for PPC.  Adding the webupd8team PPA just doesn't help... I'll again assume no PPC in that repository.

So... any hints on what the slideshow extension is missing?  Any pointers to compiling my own version of 2.13?  Do you think I'll get a slideshow with the new version or will I still be missing that essential whatever-it-is?

I mean... it's a media server, attached to the big TV... a slideshow is kind of the point.  And, yeah, I looked at the options, F-spot, Shotwell... I start, and then I just cringe.  Gthumb just works the way I think, the way I have everything set up, the way I want to work... well, except for no slideshow.

---

### Post by mjc1 on 2011-09-26
2.11.3 was a development (unstable) release. It's pretty old now.

The slideshow function might not have been in that release.

---

### Post by proteusmoteus on 2011-10-24
Recent fresh distro install gave me gthumb 2.13.1. Hoping it re-evolved back into a useful image browser I tried to get used to it.

Still [no image preview]("https://bugzilla.gnome.org/show_bug.cgi?id=634298"). Second the properties pane pops in and out of existence depending on which mode you are in. Half the time it pops up it obscures the part of the tree I was working from.

If the properties pane would stay up or [stay minimized]("https://bugzilla.gnome.org/show_bug.cgi?id=609803") (preferred since it cant preview images) then I could work around it. As it was it felt like gthumb was fighting me the entire time I was using it, so once again I downgraded back to 2.10

Surprised there is no alternative image browser but most image applications seem to avoid browse functionality. Tried to use geeqie but it was an ugly mess (tear-off menus, non-standard single click browsing, etc). The nearest alternative seemed to be Gwenview, but downgrading seemed simpler than loading in KDE dependencies.**[]("http://gwenview.sourceforge.net/")**

---

### Post by ac_d600 on 2011-10-25
You could maybe give XnViewMp a try..

[http://www.xnview.com/](http://www.xnview.com/)

not sure if its what your looking for, but I have been using
it for a couple of months now and it works well.

---

### Post by proteusmoteus on 2011-10-25
Thanks for the suggestion [ac_d600]("http://ubuntuforums.org/member.php?u=686399") it looks very close to what I want.

Installed a deb (from [here]("http://www.wubijacq.com/xnviewmp/")). Menu entry didnt launch but /opt/XnViewMP/xnview.sh worked fine. Found several small reasons to stick with gthumb 2.10 though (how to downgrade is on page 3 of this thread)

1) Fullscreen info overlay. Easily made to disappear by pressing "i" but it wouldnt remember this state after leaving and coming back into fullscreen. Small but persistent annoyance
2) Fullscreen viewing would occasionally throw a single pixel horizontal line on the picture
3) Seemed slightly slower than gthumb
4) KDE option overload. For example, would prefer all of the picture manipulation drop downs to not be present unless a "manipulate" tool was selected from the menu. Could have worked around if first three issues weren't present

---

### Post by MrVas on 2011-11-08
> **Schrute Farms said:**
> Drag the file(s) over to the folder where you want to move them.  Before you let go of the mouse button, **press shift** (or maybe control) you will see an arrow appear over the cursor.  That will make it a move & not copy.Thank you for the tip!!! I actually got used to the new gThumb, although I can see how having the old version made some actions a little easier. I'll take gThumb any day over any other image viewer, and since switching to OS X, I would LOVE to see a macosx version.

---

