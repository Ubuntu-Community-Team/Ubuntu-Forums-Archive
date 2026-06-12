---
title: "Replace F-Spot with Shotwell."
date: 2010-05-26
forum: The Cafe
---

### Post by vkontakte on 2010-05-26
I've just tried it. It looks better, it feels better, it imports much-much faster, it's just better than F-Spot.

---

### Post by vkontakte on 2010-05-26
I like the layout

---

### Post by sydbat on 2010-05-26
Good for you! Finding what works for you is what Linux is all about!

---

### Post by RiceMonster on 2010-05-26
```
sudo apt-get install shotwell
sudo apt-get remove f-spot
```

Hey look, you can do it yourself!

---

### Post by Mr. Picklesworth on 2010-05-26
Shotwell *is* hoped to replace F-Spot in 10.10.

Unfortunately, a lot of regressions need to be cured, and we need a tool to seamlessly move a user's photo library from F-Spot to Shotwell. (Lots of metadata isn't maintained). This could be tricky, as the two function very differently. For example, it would really suck if someone had carefully organized their photos into events using F-Spot's hierarchical tags, but had to do it all over again for Shotwell.

Various things that are hindering this:
[LIST]
[*]Does not support Raw images.
[*]Does not allow multiple versions of a single image. (There aren't many photo apps that do this, but F-Spot does and it fits really nicely with the Raw image stuff).
[*]Not quite as many editing tools. Easily remedied ;)
[*]Various bits of UI for dealing with photo metadata, such as tags, rating and description, could use A Lot of love.
[/LIST]

Shotwell is already in Fedora 13, so hopefully that will drive some extra interest.
I do really want it to succeed, mainly because I'm obsessed with Vala. The more successful apps written with Vala, the better off we are. (And if it was using Waf, maybe via BuildJ, I would be using Shotwell *Right Now* out of principle).

---

### Post by banerjeerupak on 2010-05-26
A nice idea would be a slow transition. First introduce Shotwell as part of the Ubuntu package. And then work on making the transition away from F-spot. It'll still give you the option of choosing to keep one or the other.

---

### Post by ugluck on 2010-05-26
my name is Daniel Planas, it's you may know me by some of my work in
ubuntu as a designer, I made some mockups of a possible reorganization
of the program. thus be located above the toolbar as most applications
and is more consistent for the user. I hope you like.

[http://i50.tinypic.com/vwsbch.jpg](http://i50.tinypic.com/vwsbch.jpg)

[http://i49.tinypic.com/1xz7ls.jpg](http://i49.tinypic.com/1xz7ls.jpg)

[http://i49.tinypic.com/ae409d.jpg](http://i49.tinypic.com/ae409d.jpg)

[http://i49.tinypic.com/30cu4ye.jpg](http://i49.tinypic.com/30cu4ye.jpg)

Daniel.P

---

### Post by BrokenKingpin on 2010-05-26
Shotwell cannot compete with F-Spot in it's current state in my opinion... maybe by the 10.10 release it will be much further along though.

On the Linux Action Show they talk about Shotwell in the Fedora 13 review, and also point out it is not ready (yet).

---

### Post by nubimax on 2010-05-26
Hope shotwell works for me f-spot never did. f-spot just put all my photos in one file and the only way I could arrange them was to delete f-spot.
M.

---

### Post by Dragonbite on 2010-05-26
Only thing F-Spot does that Shotwell does not is the Screensaver function.

---

### Post by philinux on 2010-05-26
I don't want any photo app that wants to "import". My pics are already organised in folders. All I need is an editor.

---

### Post by andrewabc on 2010-05-26
Does shotwell require mono? If not then I doubt it will be replace f-spot.

Because then there would only be tomboy requiring mono, and there is already a non mono replacement available. That would only get the anti mono people all upset that mono is installed for a single app.
Yet they had to get rid of GIMP to save space...

---

### Post by Excedio on 2010-05-26
> **andrewabc said:**
> Does shotwell require mono? If not then I doubt it will be replace f-spot.

Because then there would only be tomboy requiring mono, and there is already a non mono replacement available. That would only get the anti mono people all upset that mono is installed for a single app.
Yet they had to get rid of GIMP to save space...

Don't hi-jack the thread. Pretty please.

---

### Post by RiceMonster on 2010-05-26
> **andrewabc said:**
> Does shotwell require mono?

No.

---

### Post by andrewabc on 2010-05-26
> **Excedio said:**
> Don't hi-jack the thread. Pretty please.

Trying not to.

But if shotwell does replace f-spot, hopefully they get rid of tomboy and replace with non mono version. I think that would save around 20mb of disk space (for install cd), which could be put to better use.

---

### Post by cariboo on 2010-05-26
> **andrewabc said:**
> Does shotwell require mono? If not then I doubt it will be replace f-spot.

Because then there would only be tomboy requiring mono, and there is already a non mono replacement available. That would only get the anti mono people all upset that mono is installed for a single app.
Yet they had to get rid of GIMP to save space...

This thread was started by an anti-mono [s]troll[/s] user.

---

### Post by andrewabc on 2010-05-26
> **cariboo907 said:**
> This thread was started by an anti-mono [s]troll[/s] user.

Well maybe, and I probably took the bait. But that's because I don't like f-spot, not because of mono.
It's a terrible program for me.

To be fair GIMP hasn't put out a new release (dev or stable) in about 10 months. What happened?

---

### Post by Excedio on 2010-05-26
> **cariboo907 said:**
> This thread was started by an anti-mono [s]troll[/s] user.

What's your point? Original poster never mentioned it. Why should it be brought up? IMO you all are baiting the other's into an argument.

Anyway...trying out Shotwell, we'll see if I like it. I've been using gThumb for a while now, but it's pretty basic.

---

### Post by cariboo on 2010-05-26
> **Excedio said:**
> What's your point? Original poster never mentioned it. Why should it be brought up? IMO you all are baiting the other's into an argument.

Anyway...trying out Shotwell, we'll see if I like it. I've been using gThumb for a while now, but it's pretty basic.

This thread was moved from Maverick Testing, not by me, as the op is well known.

I've used shotwell for the last two releases, it does everything **I** need.

---

### Post by zekopeko on 2010-05-26
One thing I don't like about Shotwell (less in F-Spot's case) is that it looks empty. There is no elegance in that app. Why not copy iPhoto? That apps looks perfect to me for a casual user.

---

### Post by Dragonbite on 2010-05-26
> **zekopeko said:**
> One thing I don't like about Shotwell (less in F-Spot's case) is that it looks empty. There is no elegance in that app. Why not copy iPhoto? That apps looks perfect to me for a casual user.

That's part of why I like it, fairly simple with not a lot of junk.

Regarding Mono, I think it is actually a legitimate question, and it has been answered so the subject should not come up anymore.

---

### Post by zekopeko on 2010-05-26
> **Dragonbite said:**
> That's part of why I like it, fairly simple with not a lot of junk.

Regarding Mono, I think it is actually a legitimate question, and it has been answered so the subject should not come up anymore.

Well I would like a better sidebar. iPhoto's looks far better but then again OSX apps are usually very nice to use and look at.

---

### Post by Excedio on 2010-05-26
Well...I've tested it. I gotta say, it's kinda slow. Took ages to import my photos. Then it took a full 10 seconds to start (gThumb started right up). Lastly, when I tried to maximize the window it went grey.

For me...Shotwell = Fail

Now gThumb needs the ability to Publish to different locations.

---

### Post by Dragonbite on 2010-05-26
One thing I liked was that when the pictures were imported, they put them into a date folder location, but you can rename and move the pictures around in the folders to where you want them.

It isn't perfect, but it's a work in progress with a pretty good start (for me).

---

### Post by vkontakte on 2010-05-27
> **cariboo907 said:**
> This thread was started by an anti-mono [s]troll[/s] user.

```
$ ps aux | grep mono
user     4595  0.0  1.2 408856 41500 ?        Sl   May24   0:08 mono /usr/lib/tomboy/Tomboy.exe --search
user    23872  0.0  0.0   7668   824 pts/2    S+   12:34   0:00 grep --color mono
```
```
$ ps aux | grep gnome-do
user     4577  0.0  0.0   4136   568 ?        S    May24   0:00 /bin/sh /usr/bin/gnome-do
user     4583  0.0  1.1 433868 39728 ?        Sl   May24   3:44 /usr/bin/cli /usr/lib/gnome-do/Do.exe
user    23924  0.0  0.0   7668   824 pts/2    S+   12:36   0:00 grep --color gnome-do
```
huh?

---

### Post by pt123 on 2010-05-27
it needs to be able to import F-spot DB
F-spot is just slow, Google Picasa which uses Wine is so much faster, responsive and smoother.

---

### Post by Dragonbite on 2010-05-27
> **pt123 said:**
> it needs to be able to import F-spot DB
F-spot is just slow, Google Picasa which uses Wine is so much faster, responsive and smoother.

Picasa also provides watching folders so if you dump a folder of pictures into your Pictures/Photo or any other watched folder, it will automatically add it to your catelog. F-Spot and Shotwell do not.

Also, with Picasa I have it scanning my home file server's directory so I have one, central location to keep everything for all of the machines, and not have to "Import" them into my individual account.

I also wish I could just download entire albums from my Picasa Web albums.

---

### Post by mihai.ile on 2010-05-27
I also generally hate applications that need to "import" photos.
Tried shotwell and created a 450MB of thumbnail data for my photos collection.
WOW - 450MB just to be able to use the application...
You can also check on your pc's, it's the ".shotwell" folder

---

### Post by splicerr on 2010-05-28
> **Mr. Picklesworth said:**
> Shotwell *is* hoped to replace F-Spot in 10.10.

Unfortunately, a lot of regressions need to be cured, and we need a tool to seamlessly move a user's photo library from F-Spot to Shotwell. (Lots of metadata isn't maintained). This could be tricky, as the two function very differently. For example, it would really suck if someone had carefully organized their photos into events using F-Spot's hierarchical tags, but had to do it all over again for Shotwell.

Various things that are hindering this:
[LIST]
[*]Does not support Raw images.
[*]Does not allow multiple versions of a single image. (There aren't many photo apps that do this, but F-Spot does and it fits really nicely with the Raw image stuff).
[*]Not quite as many editing tools. Easily remedied ;)
[*]Various bits of UI for dealing with photo metadata, such as tags, rating and description, could use A Lot of love.
[/LIST]


Shotwell does support raw images. Just not the obsolete version shipped with Ubuntu ;) As for editing tools, right click and select "Open With External Editor" and you can unleash all the Gimp power you want. No, don't even try it if you are using the obsolete version shipped with Ubuntu. Seriously Shotwell is a very active project.  It's already awesome but by 10.10 it's going to be even more awesome.

---

### Post by Mr. Picklesworth on 2010-05-28
> **splicerr said:**
> Shotwell does support raw images. Just not the obsolete version shipped with Ubuntu ;) As for editing tools, right click and select "Open With External Editor" and you can unleash all the Gimp power you want. No, don't even try it if you are using the obsolete version shipped with Ubuntu. Seriously Shotwell is a very active project.  It's already awesome but by 10.10 it's going to be even more awesome.

Oh, indeed, I *am* looking forward to it. Just as F-Spot benefited from C#/Mono, I think Shotwell is going to benefit from being built with Vala. It's just a much more accessible language, which encourages some very rapid innovation and makes it way easier for new people to start contributing. (The Gnome desktop can be really problematic for that because so many things are written with straight C. Big learning curve).

I should mention I based my assessment on a pretty recent build from Shotwell's PPA. Maybe it's just *my* raw images (CR2) that it doesn't like? Or is this stuff you discuss new as in &#8220;in svn&#8221;?

Opening in an external editor like Gimp is all fine and dandy if people want to edit a single image at a low level. Where a photo *manager* can be extremely awesome is in providing quick high level editing, batch operations and fun toys (like panoramas!). I'm sure it will come with time, and the base is already a better since this application has a proper undo system. I just don't know if Maverick is the right time. Then again, PiTiVi is pretty fantastic these days, and I think it's benefiting from the attention.


Oh, and as far as things that are ahead of F-Spot at this point, I like that it doesn't have an add-ons system. Those things are the devil!
Please stay that way :)

---

### Post by splicerr on 2010-05-28
> **Mr. Picklesworth said:**
> I should mention I based my assessment on a pretty recent build from Shotwell's PPA. Maybe it's just *my* raw images (CR2) that it doesn't like? Or is this stuff you discuss new as in “in svn”?


I don't know about the version in PPA, but raw support has been in Shotwell for quite some time now in svn. If the version in the PPA is build with raw support you should get some output with.

```

strings `which shotwell`|grep  LibRaw

```

---

### Post by Mr. Picklesworth on 2010-05-28
> **splicerr said:**
> I don't know about the version in PPA, but raw support has been in Shotwell for quite some time now in svn. If the version in the PPA is build with raw support you should get some output with.

```

strings `which shotwell`|grep  LibRaw

```

Aha! Thanks for being thorough, splicerr. Indeed, 5.2 from Yorba's ppa did not have libraw support. I built it from SVN and it did. Yay! :)

---

### Post by GMU_DodgyHodgy on 2010-05-28
I tried Shotwell and it just did not work that well.  It was slower than F-Spot, made multiple copies of my photos that I had to go back and clean up and had fewer features.

For me it is not ready.  Also - F-spot issued a new release fixing bugs and making it faster.  It seems more updates are coming soon - so I think F-spot is still going to be the better option for photo management.

---

### Post by splicerr on 2010-05-28
Shotwell is definitely not slower than F-Spot. LOL, the sluggishness was exactly the reason why I gave F-Spot the boot. That and the fact that that F-Spot totally messed up the dates on my photos. See also:

[CENTER] [SIZE=3][F-Spot  Considered Harmful]("http://daniel-bartholomew.com/wordpress/2009/10/f-spot-considered-harmful/")[/SIZE]
[/CENTER]
 
But anyway I'm glad that now that they got the boot from Fedora they apparently decided to do something about it's sluggishness and the bugs.  I think they've just taken it for granted for far too long that they were the default photo manager in some GNOME based distros.

---

### Post by Swagman on 2010-05-29
I couldn't give a monkies butt how they manage photos but my missus keeps whinging that I haven't installed Picasa on this new install yet.

All she cares about is red eye removal and a graphical way  she can choose how many pix per page to print (and what quality)

She doesn't like drop down lists.

Last couple of days I've installed..

Digikam... far too technical (Where's the "Red Eye" button was her first comment)

Shotwell ... Better... Print lists not pretty enough !!

About to install Picasa ... Again.

---

### Post by yester64 on 2010-05-29
Some people don't get the point of programs like f-spot or shotwell.

These are program to organize images and to be able to display them at once. You don't need to browse through folder, instead having all images displayed either once or by events, tags, whatever.
Also these program use a database which is needed if you organzie images.
The first is a feature i was looking for and these two programs are the only ones (i know) that offer such a feature.

The problem with f-spot is that it is slow in processing large amounts of images. Shotwell sticks out so far, but can be overburdened too.

Shotwell is still in heavy development and some features are still missing. So what would the point of including an unfinished product for general use.
I like shotwell but i think it needs more development to be included as a installed standard program.

---

### Post by gnomeuser on 2010-05-29
I'm fairly happy with f-spot, and with Ruben stepping up as the new maintainer as well as announcing a lot of exciting changes in the development branch switching away seems like madness.

It is just yet another UI and data migration, the latter Shotwell doesn't even attempt to address afaik. 

If F-spot was dead and unmaintained then sure, but even then it's replacement must import existing libraries correctly or it is beyond worthless.

It's unprofessional to disregard this critical point when changing applications.

I smell an anti-mono crowd pleaser rather than any actual improvement nor any serious consideration taken to migration, future development and existing deployments.

---

### Post by Ric_NYC on 2010-05-29
Of course the pro-Mono "crowd" wants to keep F-Spot.

**_[COLOR="Red"]If[/COLOR]_** you're concerned about Mono, there are alternatives.
You can remove Mono yourself and install apps like gThumb, Picasa, Shotwell, Digikam (which has a lot of good reviews... especially if you use KDE) etc.

---

### Post by jrothwell97 on 2010-05-29
As it happens, I'm pro-Mono and I hate F-Spot. In terms of stability, speed and library portability, it's a disaster, and its UI is absolutely terrible.

That said, I can't speak for Shotwell having not tried it yet. It's definitely going to have to be better than F-Spot to be worthy of inclusion.

---

### Post by beastrace91 on 2010-05-29
> **philinux said:**
> I don't want any photo app that wants to "import". My pics are already organised in folders. All I need is an editor.

+1 On that. I always remove F-Spot because it annoys the crap out of me when I plug in a drive with pictures on it.

~Jeff

---

### Post by quinnten83 on 2010-05-29
> **philinux said:**
> I don't want any photo app that wants to "import". My pics are already organised in folders. All I need is an editor.
I want something that will just scan all my photofolders and allow me to see what is in them. I have like a bajillion dubplicates in several subfolders. And i can't get rid of them, because I don't know exactly which is the duplicate, since they tend to have different names.
As far as that goes, neither F-spot, nor Shotwell is any good for me.

---

### Post by yester64 on 2010-05-29
> **philinux said:**
> I don't want any photo app that wants to "import". My pics are already organised in folders. All I need is an editor.

You obviously don't need a photo manager. A photo viewer suits you more.
But that wasn't the topic.

---

### Post by kabel_kabel on 2010-05-29
I apologize for bumping into your conversation, i have question regarding f-spot, is it possible to resize photo with f-spot (i mean change the resolution)? I could not find it, maybe is not there :confused:
I thought you could know.

Kabel

---

### Post by zekopeko on 2010-05-29
> **kabel_kabel said:**
> I apologize for bumping into you conversation, i have question regarding f-spot, is it possible to resize photo with f-spot (i mean change the resolution)? I could not find it, maybe is not there :confused:
I thought you could know.

Kabel

I don't think it is.

---

### Post by andrewabc on 2010-05-29
> **kabel_kabel said:**
> I apologize for bumping into you conversation, i have question regarding f-spot, is it possible to resize photo with f-spot (i mean change the resolution)? I could not find it, maybe is not there :confused:
I thought you could know.

Kabel

Do you mean say 90% of original?
No.
It just asks you what pixels you want to resize to without even stating exactly what pixels you are adjusting (in Karmic) when exporting.

It is quite useless.

---

### Post by yester64 on 2010-05-30
> **quinnten83 said:**
> I want something that will just scan all my photofolders and allow me to see what is in them. I have like a bajillion dubplicates in several subfolders. And i can't get rid of them, because I don't know exactly which is the duplicate, since they tend to have different names.
As far as that goes, neither F-spot, nor Shotwell is any good for me.

Use Geeqie for Dupecheck. It does have the best dupecheck i have seen so far.
Gthumbs dupecheck really s****. Not that great at all.
F-Spot does have dupecheck too, but since i never really ran it (slow) i can not tell if you have an pullup option or if it is only at import.

---

### Post by kabel_kabel on 2010-05-31
> **andrewabc said:**
> Do you mean say 90% of original?
No.
It just asks you what pixels you want to resize to without even stating exactly what pixels you are adjusting (in Karmic) when exporting.

It is quite useless.
@ andrewabc:

Yes, i meant to say if you have 1600x1200 photo to resize it (or scale it down) to 800x600. When i read your response i realised that there is got to be something for resizing photos. It is hidden in "Photo -> Export", and as you said it is not corelated to the previous pixels of the photo, you just need to enter some number there.

Anyway, thank you for pointing that out.
Kabel

---

### Post by el cameleon on 2010-07-18
Hi,
I have just read all the thread and I still do not understad why F-Spot has been replaced by Shotwell. I have try Shotwell and I prefer it to F-Spot, but I do not understand why Canonical doesn't explain why it made this choice.
I am not convinced by the explanation about Mono dependency (which seem the reason why Fedora switch), because  of [the Mono Position Statement of Canonical]("http://en.wikipedia.org/wiki/Mono_%28software%29#cite_note-39"):
> *the Ubuntu Technical Board sees no reason  to exclude Mono or applications based upon it from the archive, or from  the default installation set.* Moreover, I didn't see anywhere that Tomboy will be replaced...
So if it is just because Shotwell is better why not explain it?

---

### Post by yajo on 2010-07-28
> **philinux said:**
> I don't want any photo app that wants to "import". My pics are already organised in folders. All I need is an editor.

I think the same regarding importing, but I think the main stuff of a photo manager is not editing. You have photo editors for that. The main pont is **sorting**.

I **HATE **importing. If I create a new folder with new photos, I want the manager to detect it, and the same if I rename an old folder or photos, or move them around.
That's the way Picasa works, and I think it's the best way. Also it's the philosophy of Gnome, isn't it? Simple and functional.

Rythmbox, for example, just reads the music folder you choose, and automatically indexes everything in real time. You can change songs' names and location whenever you want. That's the way!

At least in my case, I already have a lot of photos in a lot of folders,  with a lot of labels, and I already spent a lot of time in doing  that...

The thing I want a photo manager to do is being able to detect all those things and let me **sort **and **search **by date, label, folder, name, colors, persons, geolocation... and whatever sorting criteria you can imagine.

Of course other stuff like editing photos is always welcome, but I prefer to use one good application for sorting and another good one for editing than a single but not so good for both things.

---

### Post by Dragonbite on 2010-07-28
"Importing" should be used when pulling from a source, such as a camera, and copying it into your chosen location in the format that the program and user determines.

Otherwise, I would like it to scan the selected folder(s) for changes, or if that's too much then offer a "Rescan" or "Update" command that scans, thumbnails and indexes the pictures in the chosen folder at that time.

I still wish they would allow scanning and "importing" a Samba shared directory so I don't have to store everything on one computer and manually have to copy it to the server (which then has to be "imported" by the other systems).

---

### Post by aeiah on 2010-07-28
im looking forward to using shotwell once it matures a little. either shotwell needs to import f-spot tagging, or f-spot needs to improve its browsing performance. id be happy with either. f-spot's tagging method is very nice and intuitive - i wish all photo managers would implement tagging as metadata in the photo instead of in a database, so i can rename the photos, or share across platforms without losing that information

---

### Post by Ric_NYC on 2010-07-28
> Yorba has released [COLOR="Blue"]**Shotwell 0.6.1**[/COLOR], an update to our digital photo manager.  We would like to thank all of our bug testers and translators for their excellent work.

[B]It is highly recommended that all users upgrade.
[/B]
Major improvements since 0.5 include:

 * Basic support for RAW images, including import support for all common formats like CR2 and DNG
 * **Full support for working with PNG images**
 * Users can now zoom into photos
 * A new preferences dialog
 * The ability to open photos in an external editor, such as the GIMP, from within Shotwell
 * Photo tags and titles are imported automatically from XMP and IPTC metadata
 * A photo trash can
 * Numerous bug fixes and improved language support.


[http://www.yorba.org/blog/allison/2010/07/shotwell-061-released.html](http://www.yorba.org/blog/allison/2010/07/shotwell-061-released.html)

---

### Post by yajo on 2010-07-29
[Here]("http://trac.yorba.org/wiki/Shotwell#Shotwell0.7") it says that for version 0.7, shotwell will add the directory monitoring feature, along with some others also nice, like rating or video support. I'm happy now, I just have to wait :p

---

### Post by Dragonbite on 2010-07-29
> **yajo said:**
> [Here]("http://trac.yorba.org/wiki/Shotwell#Shotwell0.7") it says that for version 0.7, shotwell will add the directory monitoring feature, along with some others also nice, like rating or video support. I'm happy now, I just have to wait :p

Cool!

---

### Post by oscalation on 2010-10-06
i for one love this transition, first and foremost because shotwell is mono free. The comments made by richard Stallman are clear, the risk associated with the mono project outweigh the benefits. Anyone familiar with microsofts track record should know better. I refuse to use banshee, fspot, and all the other applications that depend on Mono. Removing mono would also save on space, another plus. Off topic maybe, valid points you bet. I hope Shuttleworth and Frields make the obvious decision with an official statement.. and soon

---

### Post by NightwishFan on 2010-10-06
I like Shotwell a lot. I also would like to learn more about Vala. I am glad it is getting attention.

---

### Post by Khakilang on 2010-10-06
> **pt123 said:**
> it needs to be able to import F-spot DB
F-spot is just slow, Google Picasa which uses Wine is so much faster, responsive and smoother.

I have install Picasa on my Linux computer as native and its work much the same maybe slightly better. You can download it here.

[http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)

---

### Post by Dragonbite on 2010-10-06
I've actually changed from F-Spot to DigiKam.  It does most of what I want and makes it easier to manage my photos.

Neither F-Spot nor Shotwell fully handles it in a way I like.  Of course, when I upgrade to MM, I'll have Shotwell to test things out and see if it is any better.

So Picasa and DigiKam are my favorites now.

---

### Post by directhex on 2010-10-06
> Removing mono would also save on space, another plus.

Rather less than you think, I suspect.

> Off topic maybe, valid points you bet. I hope Shuttleworth and Frields make the obvious decision with an official statement.. and soon

Already done:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html)

---

### Post by philinux on 2010-10-06
Shotwell is now the default in MM.

Before this thread descends OT.

Closed.

---

