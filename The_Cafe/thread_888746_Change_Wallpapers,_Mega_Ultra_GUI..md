---
title: "Change Wallpapers, Mega Ultra GUI."
date: 2008-08-13
forum: The Cafe
---

### Post by DoctorMO on 2008-08-13
Hey guys,

Due to "customer" demand I've quickly put together a gui and crontab python libs for setting auto changing wallpapers. See screenshot attached for demo.

You need to install 3 debs, 2 python libs and one app. It'll put a menu item in your system > preferences folder for you to configure it.

This is new, so report bugs here: [https://code.launchpad.net/gnome-wallchanger](https://code.launchpad.net/gnome-wallchanger)

Download via PPA here: [https://launchpad.net/~doctormo/+archive](https://launchpad.net/~doctormo/+archive)

---

### Post by DeadSuperHero on 2008-08-13
Pretty innovative idea! I'd like to see this for KDE!

---

### Post by joshdudeha on 2008-08-13
Looks good man (:

Um.. did you spell DeviantArt : DiviantArt? lol

---

### Post by DoctorMO on 2008-08-13
> Um.. did you spell DeviantArt : DiviantArt? lol 

Yes, although spellings are something I want corrected... I'm more interested in getting someone to _try_ it ;-)

---

### Post by Ub1476 on 2008-08-13
I'm trying it now, set it to change Walls from my ~/Picture folder, every 1 min. 10 seconds after I closed it (you might put an "Apply" and "Stop" button) it changed the wall. Now it did it again. Probably one minute after the second.. Works fine with this simple test at least. I don't feel like shutting my comp off so I wont test that :)

EDIT:

Deviantart works fine too.
OK, when I set it to GNOME, it takes pics from Appearance. Is this correct, or is it suppose to be from gnome art?

EDIT2:
Now it used the two same pics in three turns (1-2-1). That can't be right.

---

### Post by DoctorMO on 2008-08-13
> when I set it to GNOME, it takes pics from Appearance. Is this correct, or is it suppose to be from gnome art?

That is correct, gnome art doesn't have rss feeds or anything to really do this sort of thing with. If you know of a good wallpaper site with rss feeds I'll happily add it.

> Now it used the two same pics in three turns (1-2-1). That can't be right. 

It is random, and the sample size is not always huge, for instance in the gnome-wallpapers there are typically 5 images. and the rss feeds generally only get 20 or so samples.

---

### Post by kaivalagi on 2008-08-13
Great idea

I am trying to install through apt, after adding your ppa repo to my sources.list, but it isn't working for me.

I am running hardy 64 bit, and I think you only have the packages defined as 32bit in your repo, although your attachments are for all architectures...

Is there a simple setting you can update for your repo packages?

Thanks

---

### Post by DoctorMO on 2008-08-13
All signs point all arch setup in all the packages... unknown reason why the builds are specific.

anyone know?

---

### Post by kaivalagi on 2008-08-13
> **DoctorMO said:**
> All signs point all arch setup in all the packages... unknown reason why the builds are specific.

anyone know?

Apologies, it must have been me...must have been a typo on my part :oops:

Although it does only show up as an i386 build in PPA, I found it just fine through synaptic and it installed without issue...

I'll let you know how I get on...

---

### Post by DoctorMO on 2008-08-13
> Although it does only show up as an i386 build in PPA, I found it just fine through synaptic and it installed without issue...

Not a suprise, their all PurePython(tm) so they don't require any specific arch.

---

### Post by kaivalagi on 2008-08-13
Well, works nicely...good job

The only option that would be nice would be when using deviantart images, to have the ability to either keep or delete old images that have been used. Over time there will be quite a lot of space used, potentially on images that no one wants to keep

Thanks for the app, much appreciated, I'll be using it from now on :)

---

### Post by lukjad on 2008-08-13
The local folder choice didn't work though. The rest is working beautifully. Thanks!

---

### Post by DoctorMO on 2008-08-13
> The local folder choice didn't work though. The rest is working beautifully. Thanks! 

Patched in 2.1 version (see PPA or download again)

> to have the ability to either keep or delete old images that have been used

I had a checkbox for that already, since it would deplete a folders wallpapers over time if used with the folder setting. But I trust users to know what their doing. See the new version.

---

### Post by kaivalagi on 2008-08-13
> **DoctorMO said:**
> I had a checkbox for that already, since it would deplete a folders wallpapers over time if used with the folder setting. But I trust users to know what their doing. See the new version.

Thanks

---

### Post by graabein on 2008-08-13
> **DoctorMO said:**
> That is correct, gnome art doesn't have rss feeds or anything to really do this sort of thing with. If you know of a good wallpaper site with rss feeds I'll happily add it.

Nice work DoctorMo!

How about adding:

[LIST]
[*][http://www.socwall.com/php/rss_RecentWPs.php](http://www.socwall.com/php/rss_RecentWPs.php)
[*][http://interfacelift.com/wallpaper_beta/rss/](http://interfacelift.com/wallpaper_beta/rss/)
[/LIST]

As rss feeds?

---

### Post by Barrucadu on 2008-08-13
Works great, I've packaged it for Arch (I also needed to package python-moxml-config and python-crontab to get it to work).

---

### Post by master5o1 on 2008-08-13
> **Mr. Psychopath said:**
> Pretty innovative idea! I'd like to see this for KDE!

KDE 4.1 has changing backgrounds

---

### Post by DoctorMO on 2008-08-13
Version 2.2, just put it on my PPA and updated the package attached to this thread.

> How about adding:

    * [http://www.socwall.com/php/rss_RecentWPs.php](http://www.socwall.com/php/rss_RecentWPs.php)
    * [http://interfacelift.com/wallpaper_beta/rss/](http://interfacelift.com/wallpaper_beta/rss/)

I enabled the rss widgets so you can put socwall.com in as the rss url and it'll work. But interfacelist isn't an image rss feed and the links in the rss feed go to html pages not images. (I had to create a special lister class for deviantart since that works in a similar way)

I've also improved the gui a lot so you can tell what the directories are for and I think it looks much cleaner.

the remove old checkbox now old effects stuff that's been downloaded.

couple of fixes for urls with spaces and such. (have a look at the updated screenshot for wow)

---

### Post by tubasoldier on 2008-08-13
> **master5o1 said:**
> KDE 4.1 has changing backgrounds

So does KDE 3. But it doesn't download automatically which is what this is all about.

---

### Post by DoctorMO on 2008-08-14
I've posted an update to 2.3, fixed cron bugs and a few other things (icon ect)

Thank you to all those helping with testing, I can hopefully have this all wrapped up today and not need to edit it again.

---

### Post by firefeather on 2008-08-14
> **DoctorMO said:**
> That is correct [it uses Gnome appearance prefs], gnome art doesn't have rss feeds or anything to really do this sort of thing with. If you know of a good wallpaper site with rss feeds I'll happily add it.

It is random, and the sample size is not always huge, for instance in the gnome-wallpapers there are typically 5 images. and the rss feeds generally only get 20 or so samples.

So I tested it after removing some wallpapers I didn't care to have in the rotation, but one or two of those still rotated through; my guess is that I'd need to end my session before those aren't in the rotation. Is that correct?

---

### Post by DoctorMO on 2008-08-14
No, you'd need to just remove the from the source; so if it's a folder just delete the files. if it's gnome then remove the entries.

---

### Post by firefeather on 2008-08-14
> **DoctorMO said:**
> No, you'd need to just remove the from the source; so if it's a folder just delete the files. if it's gnome then remove the entries.

Hmm. I'm using the GNOME source but the first time I tried it, there was an entry that shouldn't have been. Oh well. No worries!

I enjoy the program---running it through cron rather than a daemon is a brilliant plan. I am saving memory (and notification area space) from not having to run Destkop Drapes to get the same effect. The fact that you put it in a deb package sealed the deal for me. Great job!

---

### Post by DoctorMO on 2008-08-14
> I enjoy the program---running it through cron rather than a daemon is a brilliant plan. I am saving memory (and notification area space) from not having to run Destkop Drapes to get the same effect. The fact that you put it in a deb package sealed the deal for me. Great job!

There isn't a reason it should be a daemon to be honest. Cron already does the job and recreating it's functionality would not be in the best interest of the user.

Some other daemons are a waste like that, I'm sure the update manager (that checks for updates) could be done as a cron too.

---

### Post by firefeather on 2008-08-14
> **DoctorMO said:**
> Some other daemons are a waste like that, I'm sure the update manager (that checks for updates) could be done as a cron too.

Very good point. Along those lines, [Gnome-schedule]("http://gnome-schedule.sourceforge.net") is a great way to manage (and get your head around) cron jobs. I recommend it. :)

On another note, I've found that since I installed your program, I've had to run [FONT="Courier New"]killall nautilus[/FONT] to get my desktop icons to show up and my wallpaper to show correctly after I boot. Is it possible the script makes Nautilus wig out? I may not be able to contribute by coding, but bug reporting, maybe.

---

### Post by Lord Xeb on 2008-08-15
It won't install because python-central isn't satisfied. It is already installed though e_e

---

### Post by DoctorMO on 2008-08-15
> On another note, I've found that since I installed your program, I've had to run killall nautilus to get my desktop icons to show up and my wallpaper to show correctly after I boot. Is it possible the script makes Nautilus wig out? I may not be able to contribute by coding, but bug reporting, maybe.

But report, did you have it set to on reboot or every few mins? What other settings did you have?

> It won't install because python-central isn't satisfied. It is already installed though e_e

You must be either using Ibex or Debian then; I know debian has old python-central libs. more details?

And yes, bug reports raise your launchpad karma :-)

---

### Post by firefeather on 2008-08-16
Since you mentioned launchpad, I will post all info I have on there. :)

---

### Post by picpak on 2008-08-16
> **DoctorMO said:**
> That is correct, gnome art doesn't have rss feeds or anything to really do this sort of thing with. If you know of a good wallpaper site with rss feeds I'll happily add it.

Would Flickr work?

[http://www.flickr.com/photos/tags/wallpaper](http://www.flickr.com/photos/tags/wallpaper)

---

### Post by kaivalagi on 2008-08-16
> **picpak said:**
> Would Flickr work?

[http://www.flickr.com/photos/tags/wallpaper](http://www.flickr.com/photos/tags/wallpaper)

+1

It would be nice to have the ability to enter a flickr url, and display all pictures in that photostream...

Not sure how tricky it would be to actually identify the images for downloading?

Will as flickrLister class be possible?

---

### Post by DoctorMO on 2008-08-16
> Would Flickr work?

I just fixed some interesting rss stuff to make the Flikr rss feeds work. I tested this with the wallpapers tag you suggested.

> It would be nice to have the ability to enter a flickr url, and display all pictures in that photostream...

Not sure how tricky it would be to actually identify the images for downloading?

Will as flickrLister class be possible? 

I don't know if all Flikr photo streams have rss feeds. If not then you can make a flikrLister class and get it to do that for you.

Checkout 2.4 for these changes.

---

### Post by kaivalagi on 2008-08-16
> **DoctorMO said:**
> I just fixed some interesting rss stuff to make the Flikr rss feeds work. I tested this with the wallpapers tag you suggested.



I don't know if all Flikr photo streams have rss feeds. If not then you can make a flikrLister class and get it to do that for you.

Checkout 2.4 for these changes.

That would be by far the best source of images for me

They do have rss feeds (who doesn't these days :))

They are in the form:

```
http://api.flickr.com/services/feeds/photos_public.gne?id=12345678@N00&lang=en-us&format=rss_200
```

I think, after it's been running issue free with a few of us here, this whole project should be submitted into the ubuntu repos!

---

### Post by DoctorMO on 2008-08-16
That URL is a 404 so I couldn't use that. Although did you try and use the 2.4 version where I fixed how Flikr delivers via rss? It should work for any valid rss 2.0 link from flikr including one very much like you posted (except valid)

There is a bug with restarting gnome, if you guys want to restart gnome and see if you can get it to mess up your icons and background :-)

---

### Post by kaivalagi on 2008-08-16
> **DoctorMO said:**
> That URL is a 404 so I couldn't use that. Although did you try and use the 2.4 version where I fixed how Flikr delivers via rss? It should work for any valid rss 2.0 link from flikr including one very much like you posted (except valid)

There is a bug with restarting gnome, if you guys want to restart gnome and see if you can get it to mess up your icons and background :-)

I gave an example of the feed url not knowing you had it working already in a new version...the id number was made up

I didn't even realise you had updated it again, I'm glad you have this setup in a PPA :)

Anyway, I have updated to 2.4 and have my own rss from flickr setup and working just fine

Thanks

---

### Post by DoctorMO on 2008-08-16
> I gave an example of the feed url not knowing you had it working already in a new version...the id number was made up

It may surprise you to learn that rss is an xml file and the program doesn't use the url _format_ but the xml contents. So no more made up urls please! :-P

> Anyway, I have updated to 2.4 and have my own rss from flickr setup and working just fine

Oh good, H'rah for good coding.

---

### Post by DoctorMO on 2008-08-17
OK so that bug (with nautilus) doesn't seem to happen for anyone else. Although I'd like it if anyone else sees it to change their download dir to their home dir and see if that clears up the problem. So far I have no choice but to mark it as invalid for now.

---

### Post by DoctorMO on 2008-08-18
I've been thinking about how sometimes the randomness pulls up a desktop I don't like. I know I could put a button on the top bar as a program icon. But what do others think?

---

### Post by kaivalagi on 2008-08-18
> **DoctorMO said:**
> I've been thinking about how sometimes the randomness pulls up a desktop I don't like. I know I could put a button on the top bar as a program icon. But what do others think?

Having the option to include a "thumbs down" button would be good. What would be even nicer is to have it save the offending image filename and not download it again...

Just having the button would be a good thing though, I too come across pictures I don't like (mostly my own :)) and would like to replace it with a different one.

---

### Post by hardyn on 2008-08-18
you should submit this as a [needs packaging] @ the launchpad... see if you can slide it into intrepid or i+1.

good job!

---

### Post by DoctorMO on 2008-08-18
[https://blueprints.launchpad.net/gnome-wallchanger/+spec/gnome-control](https://blueprints.launchpad.net/gnome-wallchanger/+spec/gnome-control)

I've added it as a blueprint so I can come back to it sometime later or someone else can do it. It's not a huge job.

> you should submit this as a [needs packaging] @ the launchpad... see if you can slide it into intrepid or i+1.

If you know of another method other than REVU let me know.

---

### Post by pt123 on 2008-08-18
look forward to testing it

---

### Post by hardyn on 2008-08-19
> **DoctorMO said:**
> [https://blueprints.launchpad.net/gnome-wallchanger/+spec/gnome-control](https://blueprints.launchpad.net/gnome-wallchanger/+spec/gnome-control)

I've added it as a blueprint so I can come back to it sometime later or someone else can do it. It's not a huge job.



If you know of another method other than REVU let me know.



[https://lists.ubuntu.com/archives/ubuntu-motu/2007-March/001474.html](https://lists.ubuntu.com/archives/ubuntu-motu/2007-March/001474.html)

I added a request for an updated wifi driver and it was a addresed almost immediately, so the system does work... and if you package your own deb, im sure it would be in as soon as it were approved.

---

### Post by lecter255 on 2008-08-19
hi doctor mo i am using the new version now. how do i change the wallpaper to display in zoom mode every time?

---

### Post by DoctorMO on 2008-08-19
> I added a request for an updated wifi driver and it was a addresed almost immediately, so the system does work... and if you package your own deb, im sure it would be in as soon as it were approved.

What are you saying? it lacks context...

> hi doctor mo i am using the new version now. how do i change the wallpaper to display in zoom mode every time?

Change the python code in random-wallpaper.py so that it saves the zoomed setting on each change. Submit a bug into launchpad if you think it should be added as a feature.

---

### Post by lecter255 on 2008-08-19
hi doctormo. i found the random-wallpaper.py in the gnome-wallchanger package but i am not sure how to change the code so it sets to zoom everytime. the file only has one line reproduced below. how do i change it?

PYTHONPATH=::/usr/lib/python2.5/site-packages/gtk-2.0/:$PYTHONPATH /usr/bin/python /usr/share/wallpaper-changer/random-wallpaper.py $1

---

### Post by DoctorMO on 2008-08-19
> hi doctormo. i found the random-wallpaper.py in the gnome-wallchanger package but i am not sure how to change the code so it sets to zoom everytime. the file only has one line reproduced below. how do i change it?

That isn't the py file, that's the bash script. Look for the py file.

---

### Post by kaivalagi on 2008-08-19
> **lecter255 said:**
> hi doctor mo i am using the new version now. how do i change the wallpaper to display in zoom mode every time?

I am using version 2.4 from the launchpad repo.

I just configure the style setting in "Change Background Settings" off the right click on the desktop.

If wallchanger is running, you can still go into these settings and change the default style, it then takes affect immediately and stays in that style. Just make sure you don't mess about with the background image selection.

Or am I missing the point here?

Hope that helps

---

### Post by DoctorMO on 2008-08-19
> If wallchanger is running, you can still go into these settings and change the default style, it then takes affect immediately and stays in that style. Just make sure you don't mess about with the background image selection.

Yep, that is indeed true, I think perhaps this fellow has some backgrounds which needs tiling and some that need stretched. It's an interesting problem.

---

### Post by firefeather on 2008-08-19
This thread just hit Lifehacker. :)

---

### Post by lecter255 on 2008-08-19
ok the problem is when changer changes a wallpaper, it's in tiled mode, so i go to change desktop wallpaper to set it to zoom, then close it. then when changer changes wallpaper again, the next wallpaper is in tile mode again. how do i make the default zoom or scaled? i just want all of them displayed in one mode, either zoom or scaled. 

Thanks!

---

### Post by lecter255 on 2008-08-19
wait i think i got it to work... the trick is to turn off changer, change the settings in change desktop background, close it, then turn on changer again. this way it seems changer will be using the modified settings as default. i think that's what's happening...

computer science works in mysterious ways... lol thanks guys for this help. one tiny suggestion. it would be cool if the wallpapers will fade into the next one. just a thought.

---

### Post by 5m0k3 on 2008-08-19
This inspired me to create a simple bash script to have my computer check the time on startup and use a different wallpaper, depending upon whether it is morning, afternoon, or night. It will also change at designated times via cron. I also use festival TTS to greet me on boot with good morning, good afternoon, or good evening sir, depending on the time of day.

---

### Post by lecter255 on 2008-08-19
lol good stuff. this should definitely get into repo though.

---

### Post by ranger_cole on 2008-08-19
Where is the folder wallpaper-changer located?  Not listed under places and not inside any other folder I could find.  I am newbie and am trying to learn linux.

---

### Post by DoctorMO on 2008-08-19
> Where is the folder wallpaper-changer located? Not listed under places and not inside any other folder I could find. I am newbie and am trying to learn linux.

It's any folder that you yourself create, I put mine in /home/doctormo/Graphics/Wallpapers others have a folder called wallpapers in their home directory. Either way you just have to create a new folder and dill it with the pictures you want to use.

---

### Post by ProphetSix on 2008-08-19
Following this thread, (from LifeHacker), as I've been looking for something to do this for about a month now.

One question: in Mac OSX, they have the ability to fade/slideshow between the wallpapers. Kinda of like a transition effect, or a video fade. Can any of those "special effects" be brought into this?

Thanks.

---

### Post by hufferd on 2008-08-19
> **DoctorMO said:**
> Hey guys,

Due to "customer" demand I've quickly put together a gui and crontab python libs for setting auto changing wallpapers. See screenshot attached for demo.

You need to install 3 debs, 2 python libs and one app. It'll put a menu item in your system > preferences folder for you to configure it.

This is new, so report bugs here: [https://code.launchpad.net/gnome-wallchanger](https://code.launchpad.net/gnome-wallchanger)

And PPA stuff here: [https://launchpad.net/~doctormo/+archive](https://launchpad.net/~doctormo/+archive)

Am I doing something wrong I cant install the deb packages?

---

### Post by hufferd on 2008-08-19
> **hufferd said:**
> Am I doing something wrong I cant install the deb packages?

Strike my last comment I got it figured out YAY! 

:guitar:

---

### Post by DoctorMO on 2008-08-19
> One question: in Mac OSX, they have the ability to fade/slideshow between the wallpapers. Kinda of like a transition effect, or a video fade. Can any of those "special effects" be brought into this?

No, it would be a compiz type effect that would have to be done separately. It _could_ be done in there and tied in the config. People hardly ever see their backgrounds change anyway.

---

### Post by ProphetSix on 2008-08-19
> **DoctorMO said:**
> No, it would be a compiz type effect that would have to be done separately. It _could_ be done in there and tied in the config. People hardly ever see their backgrounds change anyway.

OK, thanks for the idea and info. I'll start playing around in Compiz and see if it gives the effect I want, and than I'll look at tying the two together. If it works, I'll post back here.

---

### Post by StGermain on 2008-08-20
I can't install it on Feisty?

---

### Post by DoctorMO on 2008-08-20
> I can't install it on Feisty? 

No, although it would work on Feisty the packages are not built for it. Is this a problem?

---

### Post by ranger_cole on 2008-08-20
The random wallpaper changer appears to have created a folder called wallpaper-changer.  It is listed as a choice when you open advanced background settings.  How can I find this folder?

---

### Post by hufferd on 2008-08-20
> **ranger_cole said:**
> The random wallpaper changer appears to have created a folder called wallpaper-changer.  It is listed as a choice when you open advanced background settings.  How can I find this folder?

I just did a folder / file search and got it that way :)

---

### Post by DoctorMO on 2008-08-20
> The random wallpaper changer appears to have created a folder called wallpaper-changer. It is listed as a choice when you open advanced background settings. How can I find this folder?

I just did a folder / file search and got it that way

You should not need to find the folder, it is only where the app is installed. You should change the folder to a location in your home directory and it should be reported as a bug that the default is the app location (none-writeable)

---

### Post by ranger_cole on 2008-08-20
I found it in filesystem/usr/share.  I cannot move files to this folder do not have permission.  How do you get permission?

---

### Post by DoctorMO on 2008-08-20
> I found it in filesystem/usr/share. I cannot move files to this folder do not have permission. How do you get permission? 

You should not move files here, it is the wrong place. create a folder in your home directory and CHANGE the setting in the config.

---

### Post by ranger_cole on 2008-08-20
Ok.  Thanks for the info.

---

### Post by amazingtaters on 2008-08-20
Well, it's not working for me, I'm running Ibex

---

### Post by DoctorMO on 2008-08-20
> Well, it's not working for me, I'm running Ibex 

Errors? reasons? settings? bug report? did you try and run random_wallpaper command fromthe command line and get the output?

---

### Post by Tiler on 2008-08-20
I believe this is more of a note than a bug.  I'm finding that when the RSS feed updates, it starts over from the beginning.  Anyone else finding this?

---

### Post by DoctorMO on 2008-08-20
> I believe this is more of a note than a bug. I'm finding that when the RSS feed updates, it starts over from the beginning. Anyone else finding this?

It's random... they will sometimes repeat.

---

### Post by DoctorMO on 2008-08-21
Is there anyone who wants more features in this tool? the ability to get a new wallpaper by clicking a button in the toolbar or desktop menu? or perhaps an option to go through wallpapers sequentially instead of randomly and an option to avoid repeating?

---

### Post by Lord Xeb on 2008-08-21
I use linux mint which runs on Ubuntu 7.10

---

### Post by DoctorMO on 2008-08-21
> I use linux mint which runs on Ubuntu 7.10 

I don't understand.

---

### Post by firefeather on 2008-08-22
> **DoctorMO said:**
> Is there anyone who wants more features in this tool? the ability to get a new wallpaper by clicking a button in the toolbar or desktop menu? or perhaps an option to go through wallpapers sequentially instead of randomly and an option to avoid repeating?

For me, not especially...I like how lightweight it is!

---

### Post by quinnten83 on 2008-08-22
I read about this on lifehacker and I used the ppa repo to install.
But in my case nothing happens.
I can launch the gnome-wallpaper-config. But no matter what settings i change, my background remains the same even after the time lapse.
I am sure I am doing something wrond, so before I go giving reports about bugs, maybe someone could explain how I need to work this.
Please explain it to me like I am 4,5 cause I just might be.

---

### Post by DoctorMO on 2008-08-22
> I can launch the gnome-wallpaper-config. But no matter what settings i change, my background remains the same even after the time lapse.
I am sure I am doing something wrond, so before I go giving reports about bugs, maybe someone could explain how I need to work this.
Please explain it to me like I am 4,5 cause I just might be.

Oh no, that sounds like a bug. Please go to the command line and type in:

> random-wallpaper

And post here any error messages.

---

### Post by quinnten83 on 2008-08-22
Here it is:
```
darrell@Desktop:~$ random-wallpaper
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/random-wallpaper.py", line 23, in <module>
    from config import config
  File "/usr/share/wallpaper-changer/config.py", line 24, in <module>
    config = Config(settings_file, settings_folder)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 433, in __new__
    config = newConfig(file, filename, manager, True)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 469, in __new__
    version  = child.getAttribute('version'),
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 372, in __new__
    child = Hash(xmldoc, **options)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 171, in __init__
    self.set_xml(data)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 503, in set_xml
    parent = self,
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 370, in __new__
    child = XMLValue(xmldoc, **options)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 381, in __new__
    return ValueString(data, **options)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 722, in __init__
    return ValueBase.__init__(self, data, **options)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 667, in __init__
    Base.__init__(self, value, **options)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 171, in __init__
    self.set_xml(data)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 676, in set_xml
    return self.set(result)
  File "/usr/lib/python2.5/site-packages/moxml/config.py", line 726, in set
    self.value = str(value)
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe7' in position 55: ordinal not in range(128)
darrell@Desktop:~$ 
```

I can't make much sense of it.
But then again I am not a coder (yet, stranger things have happened).

---

### Post by Polygon on 2008-08-23
the default folder for saving wallpapers in, i dont have permission for.

> 
mark@Aurora:~$ random-wallpaper 
 @ Downloading: [http://backend.deviantart.com/rss.xml?q=in%3Acustomization/wallpaper%20sort%3Atime%20penguins&type=deviation](http://backend.deviantart.com/rss.xml?q=in%3Acustomization/wallpaper%20sort%3Atime%20penguins&type=deviation)
 @ Downloading: [http://backend.deviantart.com/rss.xml?q=in%3Acustomization/wallpaper%20sort%3Atime%20penguins&type=deviation](http://backend.deviantart.com/rss.xml?q=in%3Acustomization/wallpaper%20sort%3Atime%20penguins&type=deviation)
 @ Downloading: [http://snowflakedancer.deviantart.com/art/Gridlock-82398010](http://snowflakedancer.deviantart.com/art/Gridlock-82398010)
 @ Downloading: [http://fc03.deviantart.com/fs29/f/2008/100/0/e/Gridlock_by_snowflakedancer.png](http://fc03.deviantart.com/fs29/f/2008/100/0/e/Gridlock_by_snowflakedancer.png)
 < Saving downloaded file to /usr/share/wallpaper-changer/Gridlock_by_snowflakedancer.png
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/random-wallpaper.py", line 43, in <module>
    filename, wp = lister.getRandom()
  File "/usr/share/wallpaper-changer/lister.py", line 44, in getRandom
    return self.getItem(random.choice( self.getList() ))
  File "/usr/share/wallpaper-changer/lister.py", line 253, in getItem
    return lister.getItem(self, meta['src'])
  File "/usr/share/wallpaper-changer/lister.py", line 55, in getItem
    return self.downloadItem( itemref )
  File "/usr/share/wallpaper-changer/lister.py", line 68, in downloadItem
    fh = open(path, 'wb')
IOError: [Errno 13] Permission denied: '/usr/share/wallpaper-changer/Gridlock_by_snowflakedancer.png'
mark@Aurora:~$ 


ALSO

i just found a great idea for the saving wallpapers thing, you could have it so you can set a maximum size (like 50 mb) for the size of the wallpaper folder, and if it goes over that, it starts deleting the older wallpapers to make room for new ones.

---

### Post by lukjad on 2008-08-23
Also, in the version I use there is a small problem. If you leave an xfc file in the same folder as the other desktop backgrounds, the symbol of the file will be shown massively blown up. Not very pretty.

---

### Post by Polygon on 2008-08-23
and also another feature request:

have it search within folders, like i have a folder:

/wallpapers/

that is sorted into like

/wallpapers/1024x768
/wallpapers/1600x1200

etc.... but if i just specify 

/wallpapers/ 

it only takes the wallpapers from that folder, not recursively, it would be amazing if you could add that =)

---

### Post by lukjad on 2008-08-23
But only as an option. Sometimes you may not want all of the folders to be looked in.

---

### Post by dajashby on 2008-08-24
Hi,

Since you ask, I'd like to be able to specify a local directory and have it searched recursively for wallpapers...

Another nice feature is to be able to specify a display style per wallpaper or per directory - i.e centred, tiled, etc.

Derrick

---

### Post by leftyfb on 2008-08-25
> **DoctorMO said:**
> Is there anyone who wants more features in this tool? the ability to get a new wallpaper by clicking a button in the toolbar or desktop menu? or perhaps an option to go through wallpapers sequentially instead of randomly and an option to avoid repeating?

Please add the ability to avoid repeating. Since I have it using an "ubuntu wallpaper" feed from flickr and i'm getting the same 5 or 6 wallpapers every time. This is the furthest thing from random.

---

### Post by DoctorMO on 2008-08-25
> Please add the ability to avoid repeating. Since I have it using an "ubuntu wallpaper" feed from flickr and i'm getting the same 5 or 6 wallpapers every time. This is the furthest thing from random.

Well, it does only random between those listed in the rss feed and sometimes that is quite limited. Although flikr has at least 20 or so per rss feed.

I'll see about working on various things.

---

### Post by DoctorMO on 2008-08-25
OK I've just updated it to 2.5, this includes various fixed and features:

  * Record each of the wallpapers that have been used.
  * Try and pick a random image from the not used set instead of total set
  * Fix bug where it was requesting the list twice, even for simple feeds
  * Fix bug where it would remove a wallpaper that was being used because it
    was selecting the same one again.
  * Add refresh button to gnome-config to allow instant random background.
  * Add recursive option to folder view to select multiple files.
  * Make sure it old keeps track of the last 50 wallpapers used.

Various other features are still under consideration depending on how many people want them.

---

### Post by Shazaam on 2008-08-30
Works great. Good stuff.

---

### Post by DoctorMO on 2008-08-31
> Any chance of a Gutsy version?

I know you edited this out of your post, but I'd just like to say that it probably would be too much effort to make prior versions are debs. I wouldn't even know where to start with the packaging. Yet it's very likely that you could run the setup.py from the orig package on REVU or from source and install it on gutsy/fiesty. You may also be able to get someone else to package it for those older platforms.

---

### Post by kaivalagi on 2008-08-31
> **DoctorMO said:**
> I know you edited this out of your post, but I'd just like to say that it probably would be too much effort to make prior versions are debs. I wouldn't even know where to start with the packaging. Yet it's very likely that you could run the setup.py from the orig package on REVU or from source and install it on gutsy/fiesty. You may also be able to get someone else to package it for those older platforms.

I don't know the whole story so this is a big what if...:)

Isn't it possible to just add the hardy PPA location to the sources.list on a gutsy ubuntu OS? I know I have done things the other way round, having a gutsy repo working in hardy...

I may be totally off the mark here but I'd say it's worth a shot!

---

### Post by Shazaam on 2008-08-31
Thanks DocktorMo for the info. I edited the post after coming to the same conclusion. :)
kaivalagi...
Tried that, met dependency (versions) problems. I may play around with it later. It works fine in Hardy.

---

### Post by DoctorMO on 2008-08-31
All those who wanted to look at the earth-view like that bloke with the script from life-hackers. I've added that in. It was 6 lines of code and some glade changes. Most of the changes I've done are for packaging to get it into REVU and approved for insertion into the package system.

> Thanks DocktorMo for the info.

You welcome.

---

### Post by Uberschizo on 2008-09-02
hi

great software, tried it loved it, but can someone tell me how i can change wallpaper using this, at wish, like a keyboard shortcut. 
and how do i uninstall this?

thanks

schizo

---

### Post by DoctorMO on 2008-09-02
> great software, tried it loved it, but can someone tell me how i can change wallpaper using this, at wish, like a keyboard shortcut.
and how do i uninstall this?


Glad you like it (enough to uninstall it), you can go to the Add/Remove programs and uninstall it from there. Or use: > sudo apt-get remove gnome-wallchanger

For shortcut keys, there really isn't one yet, although there should be something.

---

### Post by Uberschizo on 2008-09-03
:-) thanks doc, any plans of including a hotkey? one must always know how to remove stuff one installs, in linux as in life

ciao

schizo

---

### Post by DoctorMO on 2008-09-03
you could always use this guide to add it yourself: [http://ubuntuforums.org/showthread.php?t=42404](http://ubuntuforums.org/showthread.php?t=42404)

---

### Post by Bruce M. on 2008-09-08
I've been looking for this program for a long time.

Or I should say: one like this.  :)

You've done a great job.  Thank you.

Have a nice day.
Bruce

---

### Post by lukjad on 2008-09-08
Sorry but this last version (2.6) doesn't work for my Local folder. I even tried switching folders, to no avail. I also cannot figure out how to remove the program (and config files). Is there anyway that I can debug it?

---

### Post by DoctorMO on 2008-09-08
run 'random-wallpaper' from the command line and report back with any errors or output and I'll look into it.

---

### Post by lukjad on 2008-09-08
Hmm... It looks like it's a permission problem.

```
lukjad007@stationx:~$ random-wallpaper
 * /home/lukjad007/.emilia
 * /home/lukjad007/EDDY DISK
 * /home/lukjad007/.thumbnails
 * /home/lukjad007/.gnome_private
 * /home/lukjad007/.dvdcss
 * /home/lukjad007/nethack-343-Guidebook.txt
 * /home/lukjad007/desktop background
 * /home/lukjad007/.esd_auth
 * /home/lukjad007/.bash_logout
 * /home/lukjad007/nethack-343-Guidebook.pdf
 * /home/lukjad007/python-crontab_0.5_all.deb
 * /home/lukjad007/CD
 * /home/lukjad007/.quiteinsane_gimp_plugin
 * /home/lukjad007/.holotz-castle
 * /home/lukjad007/pm.txt
 * /home/lukjad007/.adanaxis
 * /home/lukjad007/.gvfs
 * /home/lukjad007/.netxrc
 * /home/lukjad007/Linux quotes
 * /home/lukjad007/.update-manager-core
 * /home/lukjad007/LinuxMint-5-r1.iso.torrent
 * /home/lukjad007/convert.php_files
 * /home/lukjad007/dvdrip-data
 * /home/lukjad007/.hplip
 * /home/lukjad007/.pulse-cookie
 * /home/lukjad007/7 things.flv
 * /home/lukjad007/.Xauthority
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/random-wallpaper.py", line 47, in <module>
    filename, wp = lister.getRandom()
  File "/usr/share/wallpaper-changer/lister.py", line 51, in getRandom
    list = self.getItems()
  File "/usr/share/wallpaper-changer/lister.py", line 81, in getItems
    self._list = self.getList()
  File "/usr/share/wallpaper-changer/lister.py", line 213, in getList
    return self.imgList(self._dir)
  File "/usr/share/wallpaper-changer/lister.py", line 221, in imgList
    fh = open(path, "rb")
IOError: [Errno 13] Permission denied: u'/home/lukjad007/.Xauthority'

```

---

### Post by DoctorMO on 2008-09-08
It looks like you have it pointed at ~/ too, I can fix the bug but I don't recommend turning on recursive while also pointing at ~/.

The problem will be fixed in a later version.

---

### Post by lukjad on 2008-09-08
I checked that the recursive is off.

---

### Post by DoctorMO on 2008-09-08
Yes the problem is pointing it at ~/, because there are unreadable files in there.

---

### Post by lukjad on 2008-09-08
How do I fix this? Do I change the directory to another location?

---

### Post by DoctorMO on 2008-09-08
For now, yes.

---

### Post by lukjad on 2008-09-08
My desktop would be a good place?

---

### Post by DoctorMO on 2008-09-08
Make a new directory called Wallpapers in your home directory and put stuff in there.

---

### Post by lukjad on 2008-09-08
That's were it was! It was called "background" or "desktop background".

---

### Post by gliphwriter on 2008-09-09
> **DoctorMO said:**
> Is there anyone who wants more features in this tool? the ability to get a new wallpaper by clicking a button in the toolbar or desktop menu? or perhaps an option to go through wallpapers sequentially instead of randomly and an option to avoid repeating?

:)I don't know about anyone else, but I would love it you could change to a specific background at a specified time of day.  That would be a cool feature.:)

---

### Post by DoctorMO on 2008-09-09
> I don't know about anyone else, but I would love it you could change to a specific background at a specified time of day. That would be a cool feature.

That... would be a completely different program. Or well something more interesting. Give me $100 and I'll build it for you.

---

### Post by lukjad on 2008-09-09
That sound nice but not only that. I prefer it as it is if it is either/or.

---

### Post by DoctorMO on 2008-09-09
> That sound nice but not only that. I prefer it as it is if it is either/or. 

I thought of a way it could be done inside the current tool. although I'd still want paying for the feature.

---

### Post by gliphwriter on 2008-09-09
> **DoctorMO said:**
> That... would be a completely different program. Or well something more interesting. Give me $100 and I'll build it for you.

$100?...don't get me wrong, your work is great but you asked what other features would be nice...you didn't say what would you be willing to pay for.  I already have it change like i want using the method at this site.

[http://www.lifehacker.com.au/tips/2008/08/18/rotate_desktop_backgrounds_in_ubuntu-2.html](http://www.lifehacker.com.au/tips/2008/08/18/rotate_desktop_backgrounds_in_ubuntu-2.html)

Just thought it would be a useful feature.

---

### Post by lukjad on 2008-09-09
Is there a way to uninstall the current install so that I can reinstall the older one?

---

### Post by DoctorMO on 2008-09-09
It's cute that people think my time is worthless. I don't mind building things for my friends or myself. And I wanted good ideas that I would like to add to make it more useful for myself and encourage people to use what I have already built so people don't waste their time recreating it.

Although I appreciate your just asking for nice features, but it's a feature I don't want to do, so REJECTED. You still have the option of adding it yourself and sending me the patch.

---

### Post by lukjad on 2008-09-09
Sorry you feel that people think your time is worthless. I don't. I'm sure that gliphwriter didn't either. You *did* ask if anyone wanted to have any other features. Not all of us can but if someone has the means to, how can they contact you to arrange payment?

---

### Post by gliphwriter on 2008-09-09
:confused:Calm down DoctorMO, i never said your time was worthless.  There is really no need to get a tude about it.  I was only suggesting something.  Maybe if you hadn't been so bold about the $100 and had a donation site I could have contributed...as I've done with many other developers.  Since the feature has been "REJECTED" as you put it I will just look elsewhere.  Thank you for your time and a very good program.

---

### Post by DoctorMO on 2008-09-09
> Calm down DoctorMO, i never said your time was worthless

I'm not angry, actually I'm amused as the community had this odd attitude to free labour.

> I will just look elsewhere

Ah the great threat, hehe. Oh my heart! the pain *Gak* *fake dramatic death*

> You did ask if anyone wanted to have any other features. Not all of us can but if someone has the means to, how can they contact you to arrange payment?

Email me, I'm happy to add features that are interesting and things I'd like to see. Anything else and I'll be bold as I like in offering my labour to the market of peoples wallets.

I admit it was a bit of test to see how the community would react, they get so much for free. Is it little wonder not many real developers hang around in the forums?

---

### Post by lukjad on 2008-09-09
You have to admit that your request came out of the left field. If you had stated it out front there may have been a more time to consider what we would like and what we feel is a fair price. $100 is a lot to just hand over at the drop of a hat, even a very nice hat. You can dictate your terms, I just prefer when they are there from the beginning  I have no problem with people asking for money for their products. 

Since I am still stuck somewhere between shock, anger and bemusement right now before I start to argue with you about the merits of you little "test" I'll just go somewhere and cool off. You should know that you came off rather harsh. Just so you know.

---

### Post by CyanideSun666 on 2008-09-09
Haven't read through all the pages, but, as far as what is posted in the first post, it works great :) Thanks!

---

### Post by DoctorMO on 2008-09-09
> Since I am still stuck somewhere between shock, anger and bemusement right now before I start to argue with you about the merits of you little "test" I'll just go somewhere and cool off. You should know that you came off rather harsh. Just so you know.

Ah then regardless of the intent of my message I owe you an apology. There is no harshness intended; although I've been thinking about how little help I've been getting from the community in general, that may have bolted as some kind of subconscious complaint.

Anyway, I'm open to haggling and group buying. And I reckon the ort to be a website for this sort of thing. Canonical doesn't seem interested in an ecosystem where developers can earn real money from their work.

---

### Post by Polygon on 2008-09-09
you accept like 10 pages of suggestions then one random suggestion you suddenly want money for? you could of just 'no' or 'that would be a lot of work for just a simple hobby' or even just ignored it, but now you demand money for features? no one is forcing you implement features, but demanding 100 bucks for a feature, thats just stupid. NOTHING costs 100 bucks, hell i could buy microsoft word for 100 bucks, and that is a program that is collection of the talents and hard work of hundreds maybe even thousands of engineers.

if you want money for your program, fine. make people pay for the program, close off the source, code extra features so people dont pirate your programs, and watch as people find a way to crack it and use it for free anyway...at least until someone comes along and makes a program that does what your does, for free, and open sourced, and everyone starts using that and all your work goes to waste.

i know i will never support your program if you have this kind of attitude, heck, ill learn python myself and make a program that does what yours does for free if i want something that badly. I have never paid for a program in my life (office 2003 was an exception, and videogames also) and im not going to start now.

its not free labor, its a SUGGESTION. which means you don't have to take it. don't start complaining how the community has given you no help about this when, guess what! the majority of the community doesn't know how to code, and if they did, they would most likely chase their own ideas or join bigger projects then some small wallpaper changer GUI utility. If you have qualms about giving the ubuntu community a nice program for free, then stop developing for the opensource community. go make apps for windows or the iphone/ipod touch app store.

---

### Post by DoctorMO on 2008-09-09
Wow Polygon, you've made my naughty list. Do you even know what the _real_ programs i work on for the community are? I don't give a rats **** about the amount of help I get on this tiny little program I threw up in 2 days, nor do I have a need for any money really.

But getting messages from people with your attitude explaining why money should never be involved in Free Software and every programmer should be a socialistic volunteer is an absolute insult. I give up every free hour of every day to programming FOSS and organising my LoCo events and do it for the good of the community.

Investigating how the ecosystem can thrive on it's own dime was the whole freeking reason for my query. Instead thanks to people like you the free software world will always be eating the scraps of other peoples development and only programmers will get what they want out of Linux.

No Polygon, your wrong, dead wrong and worse than that you've shown your not interested in building a real community where people can earn a living doing work for each other based on users needs. Your interested in leeching.

To everyone else: We need to start thinking about paying for development, what ever it is we have a need to be fixed or developed. Otherwise we'll be subject to what ever development Canonical is being paid to do, or what ever volunteer can slave his spare his time on and wants to do.

---

### Post by kaivalagi on 2008-09-10
For what it's worth DoctorMo, I appreciate your efforts on this useful app, as I know how much time and energy this sort of thing can take up.

Continue to enhance your app as you see fit, as I am sure the vast majority of users are happy with it's features. I am :)

---

### Post by easyease on 2008-09-10
> **gliphwriter said:**
> :)I don't know about anyone else, but I would love it you could change to a specific background at a specified time of day.  That would be a cool feature.:)check thios out and it doesnt cost $100.
[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

deb package available here 
 [http://www.getdeb.net/category.php?id=11](http://www.getdeb.net/category.php?id=11)

---

### Post by DoctorMO on 2008-09-10
Linear progression option + times of the day option would do that feature too.

But the way this program works is quite a bit different to wallpapoz which seems to manage lists and categories. (also requires compiz)

---

### Post by Shazaam on 2008-09-10
DoctorMo...
I might have missed it amongst the other posts but I have a question. When you go to System>Preferences>Appearance>Background I have noticed that a second instance of each picture is being put there. I have made a separate folder and pointed wallpaper-changer to it for the pictures that I want it to use, I also have the box checked "Remove wallpapers after use" checked. Is this a bug or do I have it set up wrong? Should I find and clean out the default Ubuntu Background folder?

---

### Post by DoctorMO on 2008-09-10
What it does is it adds the currently used background to the gnome background settings so you can get to it if you want. It also allows you to collect backgrounds you want to keep. Send me a screen shot (annotated for effect) of the problem.

---

### Post by Shazaam on 2008-09-10
Double pics....

---

### Post by DoctorMO on 2008-09-10
OK i think I know what's going wrong. Can you report it in launchpad? that way I can get to it and not have to rush about this afternoon.

[https://bugs.launchpad.net/gnome-wallchanger](https://bugs.launchpad.net/gnome-wallchanger)

---

### Post by Shazaam on 2008-09-10
> **DoctorMO said:**
> OK i think I know what's going wrong. Can you report it in launchpad? that way I can get to it and not have to rush about this afternoon.

[https://bugs.launchpad.net/gnome-wallchanger](https://bugs.launchpad.net/gnome-wallchanger)

Will do thanks.

---

### Post by Polygon on 2008-09-10
the point of my post was, you know that no one is ever going to pay you 100 dollars to add the discussed feature to the program, which can be done with a cron script anyway.

even programs for already establilshed application stores for like the iphone, the programs there cost like 2 dollars each. why the heck are you demanding 100?

and i highly doubt any such 'community' where programmers can earn a living programming will ever exist on linux, cuase everyone expects everything to be free.....if you start asking for money people will not use it and search for a free alternative. hell, this utopian 'community' doesn't even exist on windows either. or mac. The only example ive seen is the iphone application store, and second life. and even there, people search for free alternative before they are forced to shell out money for a program.

and im not just a leecher. I actively report bugs, i give suggestions on how to improve stuff. i was active in my LoCo before it kinda died.

if your calling me a leecher, then the vast VAST majority of people who use a computer is also a leecher. They don't want to pay for programs. they will search 20 pages of google to find a free alternative for a program. and it makes sense, why pay money for a program when you can get one just as good....for free?

im not an expert on the FOSS philosophy, but im sure there is something in there about this

---

### Post by DoctorMO on 2008-09-10
> demanding

Demand sir? you will need to cite where I held a gun to his head and **Demanded** he pay me. Because as far as I was concerned and no matter how ridiculous the offering, it was still a choice I was offering for services rendered. How dare you tell me how to conduct my freedom to offer services, regardless of your opinions on the cost.

> and i highly doubt any such 'community' where programmers can earn a living programming will ever exist on linux

Your doubt is where the problem is, $2 would be fine if 50 people did likewise. Programmers aren't cheap, if any part of the FOSS community wants to demand, ask, suggest or otherwise proffer direction of development then I *require* them to invest before I will listen; code, money, time in bug tracking.

You have no voice, I'm not interested in what you have to say, you'll use what ubuntu gives and like it. Do you want the community to be a brigard of beggars? constantly running after scraps and social sympathy to get any bugs fixed?

I'd rather destroy the social convention that software is free to make than destroy the option of users to employ all tools (including money) to getting what they want.

Ultimately your arguing against the freedom of people to choose to have work done and the freedom of programmers like myself to offer such a choice.

---

### Post by Polygon on 2008-09-10
sure your free to charge money for stuff, but that makes your program less popular and less people will use it.

and the community wont be a community of beggers, you forget that there are programmers int eh community as well. if they want it badly enough, someone will just make a similar program for free. or fork yours.

---

### Post by DoctorMO on 2008-09-10
> but that makes your program less popular and less people will use it.

This isn't a popularity contest; and why would they need to fork? patches welcome. Just because I want money to do some work doesn't mean I'd deny someone their ability to do said work.

> and the community wont be a community of beggers, you forget that there are programmers int eh community as well. if they want it badly enough, someone will just make a similar program for free. or fork yours.

Only developers will get what they want, none developers will be beggars. Either evoking such ridiculous notions such as the popularity contest one above or some other daft social edifice.

Without spending money you can either use what someone has already made (scraps) or you can ask a developer to fix or add a feature (begging). Or perhaps you think programmers owe users a debt of some kind?

---

### Post by Voorhees1979 on 2008-09-10
This is a great app many thanks. I am having some issues though. When I click on change picture every 5 mins or 1 min it wont change (yes I have ticked the right box). I have to hit open the app back up and click refresh for the background to change. Any ideas?

Many Thanks

---

### Post by DoctorMO on 2008-09-10
Can you tell me what the response is to this command:

> crontab -l

---

### Post by Voorhees1979 on 2008-09-10
Hi thanks for the reply. Output is:

voorhees@voorhees:~$ crontab -l

* * * * * /usr/bin/random-wallpaper

 I have set my own local folder, and it is set to Rescursive as I have my photos in lots of different folders. This part is working for me as they change when I hit refresh.

Thanks

---

### Post by DoctorMO on 2008-09-10
that should run every minute. try running /usr/bin/random-wallpaper from the command line and post back if it worked (changed the background) or if there were errors.

---

### Post by Voorhees1979 on 2008-09-10
Hi

Thanks again for the reply. I ran the cmd

* /home/voorhees/Photos/2008/2008-03-21--18.54.04/Picture 009.jpg
 ! /home/voorhees/Photos/2008/2008-03-21--18.54.04/Picture 009.jpg
 * /home/voorhees/Photos/2008/2008-03-21--18.54.04/Picture 005.jpg
 ! /home/voorhees/Photos/2008/2008-03-21--18.54.04/Picture 005.jpg

etc etc, i wont spam all the output but there was no errors and the picture changed stright away, but of course it only changed once, I guess that is due to the command not saying change every minute or what ever.

Thanks

---

### Post by DoctorMO on 2008-09-10
No that command is run by cron every minute, that command only changes the background once... which leads me to suspect problems with cron or some other unforseen problem.

---

### Post by _Atreides_ on 2008-09-10
Doctor Mo I just wanted to take you for this app! I'm not really paying attention to the argument going on about it. I hope you can add more features if you want too and refine your app and hopefully get it added to the main repositories! Again thank you for your hard work!:KS

---

### Post by cobra741 on 2008-09-29
Heya Doc Mo :) 

Just wanted to say thanks for this great wee app.. works a treat!! 

Cheers,

---

### Post by DoctorMO on 2008-09-29
I like hearing of people who use my apps. It's what keeps programmers going in the wee hours.

---

### Post by lukjad on 2008-09-30
Whoa! It's been a long time since I saw this thread in my CP. How ya been?
Also, I tested and this program doesn't seem to work on Feisty. If you want any more info on that, tell me and when I reinstall Feisty I'll run whatever commands you want/need.

---

### Post by DoctorMO on 2008-09-30
These threads do bounce a bit, mostly because people discover the program and it's all cool.

I think it might be just the way the debs are made with fiesty. Can you confirm if there are errors when you run either of the scripts?

---

### Post by lukjad on 2008-09-30
Which command should I run? I will do them as soon as it is reinstalled. I am now living on a Live CD for about two weeks.

---

### Post by DoctorMO on 2008-09-30
firstly run 'random-wallpaper' then try 'gnome-wallchanger-config'

---

### Post by lukjad on 2008-09-30
Will do. Once I have Feisty up and rinning, I'll send you the output.

---

### Post by koradji on 2008-10-18
Dr Mo,

Thanks for the app.

After installing in Intrepid, am getting a "Terminated Unexpectedly" error dialog each time, I believe, the crontab entry tries to execute.

Cron entry looks correct and running manually from the command line is OK so I would assume it's a permissions issues of some sort.

How can I help debug the issue ?

Regards
tmcg

---

### Post by DoctorMO on 2008-10-19
Thanks for checking it out in intrepid. Check your dmesg log in /var/log/dmesg and see if it says anything. also check various other logs too.

I wonder if it's a bug in the crontab.

---

### Post by wersdaluv on 2008-10-19
Wow! It really is mega ultra! hahahaha

---

### Post by DoctorMO on 2008-10-19
> **wersdaluv said:**
> Wow! It really is mega ultra! hahahaha

Your welcome!

---

### Post by DougieFresh4U on 2008-10-19
I want to add the wallpaper changer. I need to add the 3 files posted to go along with it.. But when I click each of the files, a pop-up comes up  and says '**the associated helper files do not exist'.** I ran into this problem before and don't remember what I did to install a group of files. If I haven't explained enough please let me know. Also the 3 files are at the begining of this thread

[B]You need to install 3 debs, 2 python libs and one app. It'll put a menu item in your system > preferences folder for you to configure it.

This is new, so report bugs here: [https://code.launchpad.net/gnome-wallchanger](https://code.launchpad.net/gnome-wallchanger)

And PPA stuff here: [https://launchpad.net/~doctormo/+archive](https://launchpad.net/~doctormo/+archive)
Attached Thumbnails
Click image for larger version Name: screenshot-wallchanger.png Views: 784 Size: 859.4 KB ID: 81486  
Attached Files
File Type: deb 	python-crontab_0.5_all.deb (5.6 KB, 266 views)
File Type: deb 	python-moxml-config_0.9_all.deb (8.2 KB, 219 views)
File Type: deb 	gnome-wallchanger_2.6-0ubuntu1_all.deb (19.6 KB, 84 views)[/B]

---

### Post by lukjad on 2008-10-23
The problem seems to be that python-central. See screenshot.

---

### Post by DoctorMO on 2008-10-23
I'm building an intrepid machine now so I can properly test the deps.

Hopefully I'll have a working ppa that you can install out of the box.

---

### Post by gioele on 2008-11-01
With 8.10 the crontab doesn't seem to be working like previously reported. Running /usr/bin/random-wallpaper at the shell works great. By changing the cron to /usr/bin/random-wallpaper > /tmp/log.txt 2>&1 I was able to get:

[FONT="Courier New"]...
> Using wallpaper /home/gioele/wallpaper/nov08/november08-vibrant-blue-calendar-1280x960.jpg
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/random-wallpaper.py", line 72, in <module>
    client.commit_change_set(changeSet, True)
glib.GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Not running within active session)[/FONT]

I hope this helps finding the issue...

---

### Post by DoctorMO on 2008-11-02
Hmm, that seems to suggest that no active gconf sessions were running in that user at that time. Very odd.

I'm upgrading to intrepid now so I'll be able to debug it some more.

---

### Post by barbedsaber on 2008-11-02
where are the config files stored. I broke it (go me) and now I want to start as if it was never there. :)

---

### Post by DoctorMO on 2008-11-02
~/.gnome2/backgrounds_advanced.xml - this is the config I use. What did you break btw and how? because it shouldn't be possible to break the config and if you do that's a bug in my eyes.

---

### Post by barbedsaber on 2008-11-03
I thought it had stopped responding, so I killed it. It was just waiting for a response from deviant art, but my slow internet connection had screwed up part way through. Now it wont open without superuser privileges.

---

### Post by DoctorMO on 2008-11-03
Hmm, investigation has shown some nasty problems. Intrepid's new version of gconf which uses dbus doesn't work any more for cron jobs. It looks like a security feature but results in a bloody problem.

I'll have to totally rewrite how that script works for the cron before it'll work right.

---

### Post by lukjad on 2008-11-03
Yet another reason to wait to install 8.10. ;)

---

### Post by cheics on 2008-11-12
Wow!
I wonder what took so long for someone to write this!
I was going to give it a shot myself had it taken much longer

Kudos to you

---

### Post by Frak on 2008-11-12
Reminds me of DeskLickr for Mac.

---

### Post by DoctorMO on 2008-11-12
Yes, except it's been irreducibly broken by gnome developers. Cron Jobs can no longer access the gnome registry without the program being _inside_ the GUI.

Since the whole idea was to NOT have to run a daemon program (another one) this application has been borked and there isn't a fix for it.

I'm hoping a gnome developer will be able to tell me why they decided to break my application.

---

### Post by lukjad on 2008-11-13
So, to make this work I need to run Hardy?

---

### Post by DoctorMO on 2008-11-13
I haven't totally given up hope. I've joined the gconf mailing list and I'm going to be going directly to those who brought about this breakage. Perhaps they have some method which I have not been able to think of for fixing it.

---

### Post by lukjad on 2008-11-13
I hope so. After all that work you did, it would be a shame for it to stop working.

---

### Post by cheics on 2008-11-16
> **DoctorMO said:**
> I haven't totally given up hope. I've joined the gconf mailing list and I'm going to be going directly to those who brought about this breakage. Perhaps they have some method which I have not been able to think of for fixing it.

Looking forward to the Intrepid fix with glee

---

### Post by cheics on 2008-11-16
> **DoctorMO said:**
> I haven't totally given up hope. I've joined the gconf mailing list and I'm going to be going directly to those who brought about this breakage. Perhaps they have some method which I have not been able to think of for fixing it.

Looking forward to the Intrepid fix with glee

---

### Post by DoctorMO on 2008-11-16
> Looking forward to the Intrepid fix with glee 

Yea me too. If you see anything about this problem online and want to do a bit of research to help me. Please do link and post information here. So far gconf developers have ignored my questions.

---

### Post by cariboo on 2008-11-16
Not quite the same as the original program, but I've been using Desktop Drapes to change wallpapers,
I've go a 140Gb /home partition, so a directory with 500+ wallpapers in it, is not a big deal.

Jim

---

### Post by Sporkman on 2008-11-16
Awesome, thanks!!

8)

---

### Post by moosefist on 2008-12-12
I hope you can get it worked out.  I would love to have something like this in intrepid

---

### Post by DoctorMO on 2008-12-12
No change yet, I've asked a number of people a UDS MountinView, but no luck.

---

### Post by lukjad on 2008-12-13
Does this work on any other distros? Also, on any other DMs?

---

### Post by tbone7 on 2008-12-13
I'll follow this thread actively in hope of life being brought in to this great application once more.

---

### Post by sanjit on 2008-12-14
Umm...There's a [screenlet]("http://gnome-look.org/content/show.php/Wallpaper+changer?content=76973") that changes wallpapers at regular intervals.

---

### Post by tbone7 on 2008-12-14
Of course, but the majority of other wallpaper changer applications, incl the screenlet application, need to run as daemon. The beauty of this is that it doesn't.

---

### Post by malathion on 2008-12-15
Interesting app, and it *almost* does what I want it to do.

I had an idea to have a different wallpaper for different times of day; early morning, morning, noon, afternoon, evening, night. Therefore I wanted to set the interval between changes to 240 minutes (4 hours x 6 periods = 24 hours), but this app will not allow me to set an interval higher than 100 minutes. Is this something that could be patched?

I see you have bigger problems though...

---

### Post by Dianoga on 2009-01-28
> **malathion said:**
> Interesting app, and it *almost* does what I want it to do.

I had an idea to have a different wallpaper for different times of day; early morning, morning, noon, afternoon, evening, night. Therefore I wanted to set the interval between changes to 240 minutes (4 hours x 6 periods = 24 hours), but this app will not allow me to set an interval higher than 100 minutes. Is this something that could be patched?

I am using this in arch, but I have an option to change minutes to hours/days/month. So if you set it to 4 hours, wouldn't that do what you want?

---

### Post by DoctorMO on 2009-01-28
> I am using this in arch, but I have an option to change minutes to hours/days/month. So if you set it to 4 hours, wouldn't that do what you want?

You've got a modified version?

---

### Post by Dianoga on 2009-01-28
> **DoctorMO said:**
> You've got a modified version?

I installed it using the PKGBUILD from: [http://aur.archlinux.org/packages.php?ID=19101](http://aur.archlinux.org/packages.php?ID=19101). Looks like it uses the latest stable source in launchpad. Not sure how that relates to the .deb though.

---

### Post by jamesisin on 2009-01-29
Well, I had this running (and loving it) in Hardy.  But that move to 8.10 rather, as you know, borked things.

For my part, everything works except the cron job.  I can manually select anything from the config dialog and even click the Refresh button to manually randomize a new image.  But it won't do a damned thing on its own.

Great work so far.  I hope you find something useful in terms of fixing this problem with 8.10 (and later).

When you get a fix, let me know and I'll do a write up on my blog (which I started but didn't finish because of the forking borking).


James

---

### Post by jofunu on 2009-02-03
In the meantime, if like me you just want the wallpaper to change after each login, set /usr/bin/random-wallpaper as a startup program under Sessions.

The gnome-wallchanger-config will fail silently while the cron job is still there. If you want to change the settings while using the above method you must remove the cron job using crontab -e in a terminal. 

I think each time you run gnome-wallchanger-config it will re-add the cron job, so each time you want to run it you will have to remove the job again.

---

### Post by DoctorMO on 2009-02-03
> The gnome-wallchanger-config will fail silently while the cron job is still there. If you want to change the settings while using the above method you must remove the cron job using crontab -e in a terminal.

Or I suppose you could just turn off the repeat in the gnome-wallchanger-config.

---

### Post by jamesisin on 2009-02-06
No, I rarely restart or logout of my machine.  Unless there is a problem.  So, I just change the background by pushing the button (for now).

Looking forward to a solution.

---

### Post by kaivalagi on 2009-02-06
> **jamesisin said:**
> No, I rarely restart or logout of my machine.  Unless there is a problem.  So, I just change the background by pushing the button (for now).

Looking forward to a solution.

A **short term** solution would be to use a script which loops and calls the random-wallpaper script at regular intervals.

e.g.:

```
#!/bin/sh

while true; do
	random-wallpaper #randomise the wallpaper
	sleep 30m # wait for 30 minutes
done 

```

Then just call the script in your session startup. Change "30m" to be whatever you want to wait for, 2 hours would 120m for example.

Script attached

---

### Post by theApokalypsis on 2009-02-09
great app. just what I was looking for.

thanks DoctorMO

---

### Post by binskipy2u on 2009-02-09
which apps, debs and libs do i install and in what order from the main page..
i am currently using desktop drapes, but every single reboot, its empty and i have to reload all pictures.. i have no idea why, figured it would make sense that it would keep what you put in there for it to rotate..
thanks

---

### Post by DoctorMO on 2009-02-09
kaivalagi, that is the kind of thing that's needed. But instead of being a script (which IMO is a waste of resources) there should be a GUI level cron.

Perhaps it's time I fixed the problem by bringing a user cron into the GUI session. I don't know, I'd need to talk more to the ubuntu core devs about the best way to do it.

---

### Post by kaivalagi on 2009-02-09
> **DoctorMO said:**
> kaivalagi, that is the kind of thing that's needed. But instead of being a script (which IMO is a waste of resources) there should be a GUI level cron.

Perhaps it's time I fixed the problem by bringing a user cron into the GUI session. I don't know, I'd need to talk more to the ubuntu core devs about the best way to do it.

I totally agree, using a script to update something every 30 minutes is far from ideal...cron for updates every minute or more makes total sense.

So, I assume the idea is to setup a user cron job rather than a system level one from the GUI, so gconf access is back again for each execution? Or is that a no go either?

---

### Post by JBlade on 2009-02-15
Great program!  I'll survive with it's limited functionality due to my using Iblex until it can be fixed!  I'm rather patient.  Props to you for your hard work.

---

### Post by Ninesvnsicks on 2009-04-12
Has anyone come up with a solution for the auto-changing problem?  It doesn't seem to be deleting the wallpapers after use even tho I have the option enabled.  Also I had an idea I am using 2 monitors would it be possible to have it put a different wallpaper on each screen a "Multi Monitor" section.  Right now it just stretches the images across both and looks really pixelated.

---

### Post by Ninesvnsicks on 2009-04-12
I'm having more problems, I was using the refresh button to change the wallpaper and now when I go to open gnome-wallchanger-config I get this error.

```

ninesvnsicks@ninesvnsicks ~ $ gnome-wallchanger-config
0.8
Looking for translations in /usr/share/wallpaper-changer/po
/usr/share/wallpaper-changer/gnome-wallchanger-config.py:59: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  return gtk.glade.XML(os.path.join(glade_dir, file), inital, app)
/usr/share/wallpaper-changer/gnome-wallchanger-config.py:80: GtkWarning: gdk_window_set_icon_list: icons too large
  self.window.show()
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/gnome-wallchanger-config.py", line 242, in <module>
    manager = SettingsManager()
  File "/usr/share/wallpaper-changer/gnome-wallchanger-config.py", line 55, in __init__
    self.initGUI()
  File "/usr/share/wallpaper-changer/gnome-wallchanger-config.py", line 95, in initGUI
    self.changeChange(self.widget('change_'+change))
  File "/usr/share/wallpaper-changer/gnome-wallchanger-config.py", line 159, in changeChange
    self.updateCron()
  File "/usr/share/wallpaper-changer/gnome-wallchanger-config.py", line 202, in updateCron
    tab = CronTab()
  File "/usr/lib/python2.5/site-packages/crontab.py", line 94, in __init__
    self.read()
  File "/usr/lib/python2.5/site-packages/crontab.py", line 103, in read
    cron = CronItem(line)
  File "/usr/lib/python2.5/site-packages/crontab.py", line 183, in __init__
    self.parse(line)
  File "/usr/lib/python2.5/site-packages/crontab.py", line 204, in parse
    self.set_slices( value.split(' ') )
  File "/usr/lib/python2.5/site-packages/crontab.py", line 211, in set_slices
    self.slices.append(CronSlice(value=o[i], **s_info[i]))
  File "/usr/lib/python2.5/site-packages/crontab.py", line 277, in __init__
    self.value(value)
  File "/usr/lib/python2.5/site-packages/crontab.py", line 292, in value
    raise ValueError, 'Unknown cron time part for %s: %s' % (self.name, part)	
ValueError: Unknown cron time part for Minutes: @reboot
ninesvnsicks@ninesvnsicks ~ $

```

BTW DoctorMO I love hitchhikers guide to the galaxy :P

---

### Post by jamesisin on 2009-04-12
I am sure you will all be interested in this:

[http://brainstorm.ubuntu.com/idea/18979/](http://brainstorm.ubuntu.com/idea/18979/)

Especially solution number six (you're welcome).

---

### Post by Ninesvnsicks on 2009-04-14
I hope it works with 9.04 since it's coming out in 9 days.

---

### Post by DoctorMO on 2009-04-15
It's Done!

I got it fixed, see here:

[http://doctormo.wordpress.com/2009/04/15/wallchanger-finally-for-intrepid-and-jaunty/](http://doctormo.wordpress.com/2009/04/15/wallchanger-finally-for-intrepid-and-jaunty/)

Let me know about problems.

---

### Post by Roanoke on 2009-04-16
The ability to specify wallpaper source files' size would be nice (IE exactly a certain size, less than or equal to a certain size, and greater than or equal to a certain size). Also, a smooth transition from one image to the next would be awesome. Otherwise, this is great. The earth view is particularly nice.

---

### Post by jamesisin on 2009-04-18
Do you have a debugger?  It's not really working for me (8.10).

---

### Post by DoctorMO on 2009-04-18
Could you run it from the command line and report back the error? Perhaps add it to a launchpad bug report?

[https://bugs.launchpad.net/gnome-wallchanger](https://bugs.launchpad.net/gnome-wallchanger)

---

### Post by Roanoke on 2009-04-18
Oh, and something else: I configured my panels to only show 1px when hidden, but there's now a margin between the top and bottom of the wallpaper and top and bottom of the available screen estate. How can I fix this without distorting the wallpaper by stretching it?

---

### Post by jamesisin on 2009-04-18
You know, I'm not sure where I'd begin with a bug report... it's gone renegade.

I killed all four (I think it was four) items using my System Monitor (2 python items, a shell, and something else if I remember correctly) and now it's functioning.

Note that I did *not* say "killed all four items *and restarted them*".  If I run ```
ps waxf | grep wallpaper
``` the only item I get returned is ```
10231 pts/0    S+     0:00      \_ grep wallpaper
```.  And yet it's working.

So, how would I go about running it from the command line in this scenario?

---

### Post by jamesisin on 2009-04-18
> **Roanoke said:**
> Oh, and something else: I configured my panels to only show 1px when hidden, but there's now a margin between the top and bottom of the wallpaper and top and bottom of the available screen estate. How can I fix this without distorting the wallpaper by stretching it?

You have to change your image style by right-clicking on the desktop and choosing "Change Desktop Background" from the context menu.  Make certain you see the wallpaper-changer image selected and then set the Style (I keep mine at Scaled, but you perhaps want Fill Screen or Centered).

---

### Post by Roanoke on 2009-04-18
Thanks. That worked.

---

### Post by DoctorMO on 2009-04-18
> . And yet it's working.

Yes it runs from the crontab, no sense creating a daemon to do the crontab's job eh.

Check it like this: `crontab -l`

> So, how would I go about running it from the command line in this scenario?

There are two scripts, one is the gnome settings gui and the other is the script that runs from the crontab. I'd need to know which one fails.

---

### Post by Ninesvnsicks on 2009-04-18
Is it possible to add a feature for multi monitor systems to display a separate wallpaper on each monitor?  Right now it stretches them across both and looks really pixelated.

---

### Post by DoctorMO on 2009-04-18
It's possible if you worked with me or paid me to do it for you. Wouldn't be hard or expensive.

---

### Post by Ninesvnsicks on 2009-04-18
> **DoctorMO said:**
> It's possible if you worked with me or paid me to do it for you. Wouldn't be hard or expensive.

Awwww :*( I have no job atm and I'm not a programmer I wish I did and was tho.  But if you need someone to test it on their system I am happy to.

---

### Post by DoctorMO on 2009-04-18
Ninesvnsicks: Who does these day.

---

### Post by Ninesvnsicks on 2009-04-18
> **doctormo said:**
> ninesvnsicks: Who does these day.
lol

---

### Post by jamesisin on 2009-04-18
I am still plugging for your tool:

[http://brainstorm.ubuntu.com/idea/19200/](http://brainstorm.ubuntu.com/idea/19200/)

Also, you didn't give me instructions for running the changer from the command line.  Tell me how and I'll get you the results.

---

### Post by DoctorMO on 2009-04-18
It's simply:

```

random-wallpaper

```

---

### Post by zephyrcat on 2009-04-19
Though I haven't gotten to try this yet, I would suggest adding I Can Has Cheezburger and/or Failblog to the options. I believe they both have RSS feeds.

---

### Post by CraigPaleo on 2009-04-20
Marvelous! Someone was recently asking about something like this that would change with the weather. Would it be easy to incorporate that functionality into this program?

---

### Post by kaivalagi on 2009-04-20
> **CraigPaleo said:**
> Marvelous! Someone was recently asking about something like this that would change with the weather. Would it be easy to incorporate that functionality into this program?

It randomises wallpaper, it has no way to connect wallpaper type to a situation - last time I checked anyway

I guess with the British weather the way it is  you could just setup wallpapers for all weather types and randomise twice a day, you never know it might be better than the forecast :)

---

### Post by DoctorMO on 2009-04-20
Add a rote option which would disconnect the randomiser and pick the next one in line. And then add an rss feed with the weather images? Sure.

---

### Post by kaivalagi on 2009-04-20
I stand corrected :)

---

### Post by melat0nin on 2009-04-20
Unfortunately it doesn't work for me.  When I run gnome-wallchanger-config from the terminal I see this:

```
laurence@melat0nin:~$ gnome-wallchanger-config 
Looking for translations in /usr/share/wallpaper-changer/po
```

(nothing out of the ordinary)

and when I change the wallpaper it gives a message telling which wallpaper it is changing to, but nothing happens.  I have disabled the Compiz wallpaper plugin and logged out and back in but neither made a difference.

Any thoughts?  I am running Intrepid.

---

### Post by DoctorMO on 2009-04-20
melat0nin: have you made sure that the correct background is set in System > Preferences > Appearance > Background(tab)

---

### Post by melat0nin on 2009-04-20
> **DoctorMO said:**
> melat0nin: have you made sure that the correct background is set in System > Preferences > Appearance > Background(tab)

That was the problem, sorry!  I didn't notice there was another entry in the list of images.

---

### Post by Roanoke on 2009-04-21
Is the earthview wallpaper "prerecorded"?

---

### Post by DoctorMO on 2009-04-21
No it's as live as you can get. I'm watching the weather patterns, look out for hurricanes when they appear on the weather news.

---

### Post by Roanoke on 2009-04-21
Oooh, cool. :D

---

### Post by Ninesvnsicks on 2009-04-24
I just installed jaunty 9.04 and I added the repository to software sources and imported the key but when I open synaptic gnome-wallchanger is not there?

---

### Post by kaivalagi on 2009-04-25
> **Ninesvnsicks said:**
> I just installed jaunty 9.04 and I added the repository to software sources and imported the key but when I open synaptic gnome-wallchanger is not there?

Did you click "reload" in Synaptic first to update the package information?

---

### Post by Ninesvnsicks on 2009-04-25
> **kaivalagi said:**
> Did you click "reload" in Synaptic first to update the package information?

Of course I also tried apt-get update and apt-get install and it still doesn't find it.

[IMG]http://img257.imageshack.us/img257/1599/screenshotvvy.png[/IMG]

---

### Post by DoctorMO on 2009-04-25
As far as I can see... I didn't have a jaunty release. But if you'd like to have one, I'll make one.

Check this page to see if the software you need from my ppa is available: [https://launchpad.net/~doctormo/+archive/ppa](https://launchpad.net/~doctormo/+archive/ppa)

---

### Post by Ninesvnsicks on 2009-04-25
Oh well that would certainly explain it lol, ok page says published 1 hour ago so I'm just waiting for it to show up thanks DoctorMO.

EDIT:
Well it showed up but when I went to install I got this error:
[IMG]http://img24.imageshack.us/img24/1253/10216683.png[/IMG]

---

### Post by melat0nin on 2009-04-25
> **Ninesvnsicks said:**
> Oh well that would certainly explain it lol, ok page says published 1 hour ago so I'm just waiting for it to show up thanks DoctorMO.

EDIT:
Well it showed up but when I went to install I got this error:
[IMG]http://img24.imageshack.us/img24/1253/10216683.png[/IMG]

I had the same problem; the solution was to install the relevant debs from DoctorMO's launchpad PPA page.  After that I could install gnome-wallchanger no problem.

---

### Post by DoctorMO on 2009-04-25
I've just pushed some jaunty deps too... sorry about that.

---

### Post by Ninesvnsicks on 2009-04-25
I just did what melat0nin did and it seems to work fine :)

BTW how do you guys like Ubuntu 9.04 so far?

---

### Post by Roanoke on 2009-04-25
It doesn't work for me (it doesn't save its config, either). Terminal output, after setting custom settings:
```

$ gnome-wallchanger-config
Looking for translations in /usr/share/wallpaper-changer/po
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/random-wallpaper.py", line 28, in <module>
    backgrounds = get_lister('default', config)
  File "/usr/share/wallpaper-changer/lister.py", line 360, in get_lister
    return item(*vars)
  File "/usr/share/wallpaper-changer/lister.py", line 44, in __init__
    for item in config['used']:
TypeError: 'NoneType' object is not iterable
$

```

---

### Post by melat0nin on 2009-04-26
I guess the thing to do now is find some nice wallpaper RSS feeds!

I tried to muddle through and write a PHP parser for the Interfacelift RSS feed which would work with gnome-wallchanger, but my skills don't stretch to that :(

---

### Post by melat0nin on 2009-04-26
Yeah it's not working right for me, either.

When I try to tell it to use a local folder full of wallpapers, it gives this message to the terminal:

```
 @Downloading: http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg
 < Saving downloaded file to folder/world_sunlight_map_rectangular.jpg
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/random-wallpaper.py", line 31, in <module>
    filename = wallpapers.getRandom()
  File "/usr/share/wallpaper-changer/lister.py", line 68, in getRandom
    return self.useItem(item)
  File "/usr/share/wallpaper-changer/lister.py", line 80, in useItem
    item = self.getItem(itemref)
  File "/usr/share/wallpaper-changer/lister.py", line 101, in getItem
    return self.downloadItem( itemref )
  File "/usr/share/wallpaper-changer/lister.py", line 113, in downloadItem
    fh = open(path, 'wb')
IOError: [Errno 2] No such file or directory: u'folder/world_sunlight_map_rectangular.jpg'
```

...needless to say, the wallpaper doesn't change.

Any thoughts?  I've installed in Jaunty from the PPA.

---

### Post by Ninesvnsicks on 2009-04-27
Mine seems to be changing my wallpaper fine however, the delete wallpaper after use doesn't seem to be deleting them.

---

### Post by jamesisin on 2009-04-27
> **Ninesvnsicks said:**
> Mine seems to be changing my wallpaper fine however, the delete wallpaper after use doesn't seem to be deleting them.

Mine doesn't save them and I have it marked to do so.  You might try reversing the setting and see if it's backward.

---

### Post by Ninesvnsicks on 2009-04-27
I tried to change any setting but it wont let me change anything that might be why I'm having the problem when I first set it up I had it unchecked.  Basically it's not letting you change settings.

---

### Post by jamesisin on 2009-04-30
Not sure how it came to this, but it's not running again.  This time I can't find any reference to wallpaper-changer in ps/top/system monitor (top and the sys mon don't change when I click the Refresh button, but ps does list /bin/sh /usr/bin/gnome-wallchanger-config and \_ /usr/bin/python /usr/share/wallpaper-changer/gnome-wallchanger-config.py when I have the dialog running).

I tried running wallpaper-changer from the command line and it merely echoes the current image being used (including its path).

Any other trouble shooting I can do?

---

### Post by Roanoke on 2009-04-30
Looks like it's failing for everybody.

---

### Post by xeddog on 2009-04-30
Been a long time since anyone added anything to this thread, but for an improvement, how about the ability to display a separate wallpaper on each monitor in a multiple monitor system?

xeddog

---

### Post by yabbadabbadont on 2009-04-30
> **xeddog said:**
> Been a long time since anyone added anything to this thread, but for an improvement, how about the ability to display a separate wallpaper on each monitor in a multiple monitor system?

xeddog

I'm pretty sure that that issue has already been raised, and responded to, within the last several pages of this thread.  :D

Edit: Yep, here->[http://ubuntuforums.org/showpost.php?p=7096871&postcount=208](http://ubuntuforums.org/showpost.php?p=7096871&postcount=208)
Edit2: And the reply is here->[http://ubuntuforums.org/showpost.php?p=7096893&postcount=209](http://ubuntuforums.org/showpost.php?p=7096893&postcount=209)

---

### Post by Ninesvnsicks on 2009-05-01
Yeah, I'm not sure what "work with me" means in this case but I am willing to help out anyway I can but I'm not a Linux guru, I'll certainly test the multi monitor if he doesn't have a setup like that.

EDIT:
I still can't change any settings.

---

### Post by Ninesvnsicks on 2009-05-04
Any updates?

---

### Post by DoctorMO on 2009-05-04
No updates Ninesvnsicks, sorry. I've been focusing on paid work and I just happen to get sick this weekend :-(

---

### Post by Ninesvnsicks on 2009-05-04
oh ok np I am sick too with a cold or something.

---

### Post by Ninesvnsicks on 2009-05-10
Is anyone else having trouble with not being able to make changes to settings?

---

### Post by Roanoke on 2009-05-11
Everyone.

---

### Post by DoctorMO on 2009-05-11
I hope not, what are the steps?

---

### Post by Ninesvnsicks on 2009-05-11
you open the config and change something then exit and it doesn't change.  If you reopen it the old settings are still there.

---

### Post by Roanoke on 2009-05-11
Trying to change settings on jaunty fails (settings don't change).

---

### Post by DoctorMO on 2009-05-11
hmm, change a few settings, same thing?

Load it from the cli and see if there are any error messages and report a bug on launchpad: [https://bugs.launchpad.net/gnome-wallchanger](https://bugs.launchpad.net/gnome-wallchanger)

I think perhaps it might be either permissions or a newer version of python-moxml causing errors. But I'd need to know the errors. Also make sure to report the moxml version:

apt-cache policy python-moxml-config

---

### Post by Ninesvnsicks on 2009-05-13
I ran gnome-wallchanger-config from cli and it didn't give any errors from switching settings however it did break my wallchanger, now it wont download and change the background when I hit refresh I get this error.

```

~$ gnome-wallchanger-config
Looking for translations in /usr/share/wallpaper-changer/po
/usr/share/wallpaper-changer/gnome-wallchanger-config.py:58: GtkWarning: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
  return gtk.glade.XML(os.path.join(glade_dir, file), inital, app)
 @ Downloading: http://backend.deviantart.com/rss.xml?q=in%3Acustomization/wallpaper%20sort%3Atime%20digital 1680x1050&type=deviation
 @ Downloading: http://3ric-Design.deviantart.com/art/Wallpaper-77-105304605
 @ Downloading: http://fc01.deviantart.com/fs38/f/2008/338/1/7/Wallpaper_77_by_3ric_Design.jpg
 < Saving downloaded file to folder/Wallpaper_77_by_3ric_Design.jpg
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/random-wallpaper.py", line 31, in <module>
    filename = wallpapers.getRandom()
  File "/usr/share/wallpaper-changer/lister.py", line 68, in getRandom
    return self.useItem(item)
  File "/usr/share/wallpaper-changer/lister.py", line 80, in useItem
    item = self.getItem(itemref)
  File "/usr/share/wallpaper-changer/lister.py", line 315, in getItem
    return lister.getItem(self, meta['src'])
  File "/usr/share/wallpaper-changer/lister.py", line 101, in getItem
    return self.downloadItem( itemref )
  File "/usr/share/wallpaper-changer/lister.py", line 113, in downloadItem
    fh = open(path, 'wb')
IOError: [Errno 2] No such file or directory: u'folder/Wallpaper_77_by_3ric_Design.jpg'
~$ 

```

```

~$ apt-cache policy python-moxml-config 
python-moxml-config:
  Installed: 1.0-0ubuntu1
  Candidate: 1.0-0ubuntu1
  Version table:
 *** 1.0-0ubuntu1 0
        500 http://ppa.launchpad.net jaunty/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by Roanoke on 2009-05-13
I tried to configure it to use earthview updated every 5 minutes.
```

~$] gnome-wallchanger-config 
Looking for translations in /usr/share/wallpaper-changer/po
Traceback (most recent call last):
  File "/usr/share/wallpaper-changer/random-wallpaper.py", line 28, in <module>
    backgrounds = get_lister('default', config)
  File "/usr/share/wallpaper-changer/lister.py", line 360, in get_lister
    return item(*vars)
  File "/usr/share/wallpaper-changer/lister.py", line 44, in __init__
    for item in config['used']:
TypeError: 'NoneType' object is not iterable

```
```

 apt-cache policy python-moxml-config 
python-moxml-config:
  Installed: 1.0-0ubuntu1
  Candidate: 1.0-0ubuntu1
  Version table:
 *** 1.0-0ubuntu1 0
        500 http://ppa.launchpad.net jaunty/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by Ninesvnsicks on 2009-05-20
Any luck guys?  Mine has completely stopped working now.

---

### Post by Ninesvnsicks on 2009-05-26
Does anyone know if there are any other programs like this out there I need something.

---

### Post by DoctorMO on 2009-05-26
Ninesvnsicks, you've given up? do I take it that emailing me, irc or any other communication medium would have been too much? We're all busy chaps down here, can you make sure you've prodded me more than a couple of times about it.

I've updated both packages in my ppa, let me know if they fix the issues.

---

### Post by Ninesvnsicks on 2009-05-27
Hmm, I went to the launchpad page and it said email hidden so I went to create an account and it wasn't sending to my email but now it seems to have worked the 2nd time around so now I can see your email.  I go on freenode once and a while but you don't have a channel listed and you don't' seem to be on.  I just tried to update it and I got a few errors first this window:

[IMG]http://img30.imageshack.us/img30/977/24865229.png[/IMG]

Then here are the details:
```

Selecting previously deselected package gnome-wallchanger.
(Reading database ... 114834 files and directories currently installed.)
Unpacking gnome-wallchanger (from .../gnome-wallchanger_2.7-1ubuntu3_all.deb) ...
Processing triggers for man-db ...
Setting up gnome-wallchanger (2.7-1ubuntu3) ...
Compiling /usr/share/wallpaper-changer/lister.py ...
SyntaxError: ('invalid syntax', ('/usr/share/wallpaper-changer/lister.py', 122, 16, '            else:\n'))

pycentral: pycentral pkginstall: error byte-compiling files (5)
pycentral pkginstall: error byte-compiling files (5)
dpkg: error processing gnome-wallchanger (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-wallchanger
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-wallchanger (2.7-1ubuntu3) ...
Compiling /usr/share/wallpaper-changer/lister.py ...
SyntaxError: ('invalid syntax', ('/usr/share/wallpaper-changer/lister.py', 122, 16, '            else:\n'))

pycentral: pycentral pkginstall: error byte-compiling files (5)
pycentral pkginstall: error byte-compiling files (5)
dpkg: error processing gnome-wallchanger (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-wallchanger

```

---

### Post by DoctorMO on 2009-05-27
[http://divajutta.com/doctormo/](http://divajutta.com/doctormo/)

Sorry about that, bug crept in. Just uploaded a new version.

---

### Post by Ninesvnsicks on 2009-05-27
I'm still getting the same errors PS I am Ninesvnsicks on freenode I'm in channel #doctormo at the moment hehe.

---

### Post by DoctorMO on 2009-05-27
You were too quick, it takes a second to update the ppa

---

### Post by Ninesvnsicks on 2009-05-27
Oh ok didn't know that lol.  It's working now and lets me change settings now woot Thanks :)

---

### Post by Roanoke on 2009-05-27
Works now, thanks a ton :D

---

### Post by HandleWithCare on 2009-06-18
So I used this program in jaunty. At first it did nothing, after running the program once as sudo it stopped giving errors (permission things). I set the program to change the background every minute, from a local folder and remove after use unchecked. I had to go away for a while and when I came back I still had the same background but all the images in the local folder were gone. So I did some testeng. When i run the config trough command line and hit refresh I see the following:
```
> Using wallpaper /home/user/Pictures/Wallpaper/newfile.jpg
! Deleting Old File /home/user/Pictures/Wallpaper/oldfile.jpg
```
So it removes the old picture even when I uncheck the checkbox. On top of that,the background doesn't change! I tried every option, when I use the earth view option I can see the file being downloaded (commandline) but then the old picture is deleted and nothing happens.
So, this means that I lost about 150 wallpapers because of this, so a fix would be very nice. If any further info is needed, please let me know.

---

### Post by Ninesvnsicks on 2009-06-19
@HandleWithCare, Do you have random-background selected in System > Appearance > Background?

---

### Post by HandleWithCare on 2009-06-20
@Ninesvnsicks: There's no such option (ubuntu 9.04)

---

### Post by Ninesvnsicks on 2009-06-20
> **HandleWithCare said:**
> @Ninesvnsicks: There's no such option (ubuntu 9.04)

There is for me in Ubuntu 9.04

---

### Post by EateryOfPiza on 2009-07-06
> **HandleWithCare said:**
> @Ninesvnsicks: There's no such option (ubuntu 9.04)

He might mean System > Preferences > Appearance > Background

@DoctorMo: I believe the script overwrites the user's current crontab. Could you fix the script so that it would not do so? Or could you tell me which file has the crontab editing methods, I can't seem to find it. (Bug report here: [https://bugs.launchpad.net/gnome-wallchanger/+bug/396290](https://bugs.launchpad.net/gnome-wallchanger/+bug/396290))

---

### Post by DoctorMO on 2009-07-06
@EateryOfPiza - Oh dear! So sorry about that are you on IRC? I'll deal witht he bug report now though.

---

### Post by EateryOfPiza on 2009-07-06
I wasn't but now I'm on freenode. What channel?

I think I narrowed down the bug to this. In the crontab.py, under the CronTab class, under the write() method, it calls render(), which only reads the crons list, but does not read the lines list as well.

To fix this, render() must read the lines list into the final string. That would fix the comments disappearing.

For the other cronjobs in the CronItem class, it misidentified one of my cronjobs as not valid, so it got thrown into the lines list. (So fixing the above would temporarily fix this problem, but would not fix the underlying problem of an invalid validator.) Here is the specific line:

00 05  *  *   *      /home/user/Documents/code/apod-getter/update-apod

Not sure why it's not valid, since that cronjab works.

---

### Post by DoctorMO on 2009-07-06
All fixed, test please.

---

### Post by hellocatfood on 2009-07-08
I've been using the wallchanger happily for a few months and thought I'd try downloading wallpapers from deviantart. I clicked on "Remove wallpapers after use" though made a backup of my wallpapers just in case. Surprisingly it did actually delete all of my old wallpapers instead of just deleting the ones that were downloaded. Is that the way it's supposed to work?

Also, I unchecked the box and still find that it's deleting my wallpapers. 

Any help would be appreciated!

---

### Post by DoctorMO on 2009-07-08
Hey there,

No problem, just run the random-wallpaper command from the command line (terminal) and post the results into a bug report on launchpad:

[https://bugs.launchpad.net/gnome-wallchanger](https://bugs.launchpad.net/gnome-wallchanger)

---

### Post by Hamms on 2009-07-16
First of all, fantastic app; every feature I decided I wanted when I started looking for a random wallpaper changer is here.

... Unfortunately it seems to be broken for me; it won't actually update my wallpaper at the given iterval (five minutes). I suspect the problem is with cron; when I call gnome-wallchanger-config, I get ```
Ignoring invalid crontab line `*/5 * * * * /usr/bin/random-wallpaper`
```And then the program seems to start fine. Also, the last line when I call crontab -l is `*/5 * * * * /usr/bin/random-wallpaper` with no newline at the end ... is this normal?

Calling random-wallpaper works as intended; should I throw this up as a bug on launchpad, or is it more a problem with my cron settings?

Thanks again for a great app!

EDIT:
ach, nevermind. For some reason, every line in my crontab was commented out ... I cleared it out and added in the line I wanted and it seems to be working just fine.

---

### Post by DoctorMO on 2009-07-17
It still might be a bug, the warning about ignoring the line because it's invalid means that the very line I generate to generate wallpapers is not a line crontab.py likes.

Oh and thanks for the complements, always great to know a program is useful.

---

### Post by jacomago on 2009-09-02
Hi

I had a similar problem to Hamms, I inputted a bug report at [https://bugs.launchpad.net/bugs/423463](https://bugs.launchpad.net/bugs/423463)

Plus I'm trying to teach myself python so if you give me a general idea of how I could add a way of changing wallpaper at certain time of the day I'll try look into doing it as I like the idea myself.

---

### Post by DoctorMO on 2009-09-02
Hey jacomago,

If your trying to learn python and Ubuntu development in general, you can't go wrong on the wallchanger project. It's small, compact and not complex at all.

It's split up into two parts, both of which are on launchpad and you can use bzr branch command to grab them.

gnome-wallchanger
libpython-crontab

Let me know if you need any help.

---

### Post by lordbah on 2009-09-12
Installed on 9.04. I haven't done anything with cron yet, just trying to get it to work when run manually. So far, no luck.

Running random-wallpaper from command line comes back
 > Using wallpaper /home/lordbah/Wallpaper/img.jpg

i.e. looks like it works. But the background does not change.

A couple of pages back there is some mention that System/Preferences/Appearance, on the Background tab, is supposed to have a "random wallpaper" choice. Did I understand that right? I don't see anything like that, just a dozen or so thumbnails that I had there before. Would this be a thumbnail with the text "random wallpaper" on it? Should it be that clock/paintbrush image I see in wallchanger.png?

---

### Post by DoctorMO on 2009-09-12
OK so there should be a wallpaper in your apperences which changes automatically. It should point to a symbolic link inside of ~/.gnome2/wallpaper.png and this symbolic link is what gets updated.

---

### Post by lordbah on 2009-09-12
Aha, if I hover over the thumbnail, I see the path. Never knew that. There is one which is ~/.gnome2/random-background. However the outline is around the thumbnail for "No Desktop Background". I selected random-background and hit Close. The background did not change. I brought up System/Preferences/Appearance again and random-background is now the one with the selection highlight around it. I closed it again, ran random-wallpaper, it printed out that it was using a different file. Back to System/Preferences/Appearance and random-background is still highlighted and now is a thumbnail of the new file. But the actual desktop background has not changed, it is still the same orange/brown gradient as the thumbnail for No Desktop Background.

EDIT: Logged out and back in, and now all seems to be working as it should. Thanks.

---

### Post by uschxc on 2009-09-18
> **DoctorMO said:**
> OK so there should be a wallpaper in your apperences which changes automatically. It should point to a symbolic link inside of ~/.gnome2/wallpaper.png and this symbolic link is what gets updated.

a thousand thanks for writing this application and keeping up with this thread Mr. Owens.  i wish you great luck and success in getting this into the ubuntu repos.

i've gotten the application to work from your repositories however the wallpaper only changes when i hit refresh in the application.  i have it set to rotate every 15 minutes for the earth backdrop and it never does.  what can i check on and report back to fix it?

---

### Post by hellocatfood on 2009-09-18
> **uschxc said:**
> i've gotten the application to work from your repositories however the wallpaper only changes when i hit refresh in the application.  i have it set to rotate every 15 minutes for the earth backdrop and it never does.  what can i check on and report back to fix it?

I had this same problem awhile back. I set it to download from deviantart and then when I switched back refreshed itself.

Other than that I'm not sure what else can help

---

### Post by DoctorMO on 2009-09-18
uschxc - could you paste the results from this command please?

crontab -l

I've uploaded a package which should fix the issue, it's because there isn't a return at the end of the crontab file. 0.9.3 of python-crontab should fix that.

It'll come through in your updates if you installed via the repositories. Just make sure the new version is installed and then change the update time to refresh the crontab settings.

---

### Post by hhh on 2009-09-21
Dear DoctorMo,

Your app was mentioned in the comments of this post... (edit- Ah, by you!)
[http://webupd8.blogspot.com/2009/09/real-time-earth-wallpaper-for-linux.html](http://webupd8.blogspot.com/2009/09/real-time-earth-wallpaper-for-linux.html)

Cool app! If you read all the comments, you'll see that I mentioned that the image source of opentopia.com is itself using the images from [http://www.die.net/earth/](http://www.die.net/earth/) . This results in a time delay. What files should I edit to use the images from die.net?

Cheers.

[hhh]("https://addons.mozilla.org/en-US/firefox/addon/11953/")

---

### Post by DoctorMO on 2009-09-21
You you like me to update the app with this address?

All you do is change /usr/share/wallpaper-changer/lib/lister.py Line 331


earth_url = '...' <- here
class earthLister(lister):

Of course if the other url is better, than I should update the sources. You could also create a bzr branch with the modification and I could merge it in.

---

### Post by hhh on 2009-09-21
Fast reply, hah! I came back to post that changing that line in lister.py to ```
earth_url = 'http://static.die.net/earth/mercator/1600.jpg'
``` then running random-wallpaper in terminal created a new photo (1600.jpg). Setting that as the background seems to be working.

I like this URL better as it's much closer (dead on, maybe?) to what the actual light conditions are outside. I was using the script posted by Andrew last night and was a bit annoyed that it was dark outside but my wallpaper showed sunlight where I was.

Two more questions, if you don't mind...
Do I need to make an entry in Startup Applications for this application, or now that it's running will it continue to do so?

Is there documentation for this? For example, is the above question covered somewhere, plus telling users that the usr/share/wallpaper-changer folder listed in the UI actually defaults to home/"User Name"/Pictures. If there isn't any, I'd be glad to help.

Thanks again for your time, DocMo!

---

### Post by hhh on 2009-09-21
> **DoctorMO said:**
> You could also create a bzr branch with the modification and I could merge it in.
I'm not a programmer, I don't know how to do that.

---

### Post by DoctorMO on 2009-09-21
> I'm not a programmer, I don't know how to do that. 

Would you like to learn how? and do you have a launchpad account?

> Two more questions, if you don't mind...
Do I need to make an entry in Startup Applications for this application, or now that it's running will it continue to do so?

No, it doesn't work like that as it's not a daemon. It runs from crontab, so as long as your wallpaper is set to the random wallpaper in System > Preferences> Appearance (Background Tab) then it should update when the crontab element runs.

You can check that the crontab element is in place with `crontab -l`

---

### Post by hhh on 2009-09-21
I'd be glad to open a Launchpad account. PM me with details whenever you have time.

Re: updating the source, there's a Usage Guideline paragraph here that's probably relevant...
[http://www.die.net/earth/how.html](http://www.die.net/earth/how.html)

---

### Post by DoctorMO on 2009-09-21
Sure, yet another reason to finish what I'm working on.

---

### Post by murderslastcrow on 2009-09-21
Swweeeeeet! Great idea.

---

### Post by onon_onon on 2009-10-07
First of all, thanks for giving a shot, I really like the idea of wallpaper-changer.
But I found some issues in gnome-wallchanger 2.7-1ubuntu4.
At first, all the commands in cron are saved as comment, with #. Once I edit it with crontab -e, gnome-wallchanger-config is able to see and update the job.
Second, when I run random-wallpaper from command line, I see a try to delete /usr/share/backgrounds/simple-ubuntu.png instead of the new wallpaper, of course denied by permissions. I commented out those lines in /usr/share/wallpaper-changer/random-wallpaper.py and then waited for the wallpaper to change by cron, but no luck.
What now give me the third issue: I don't know why, but backgrounds_advanced.xml and background.png in .gnome2 can't be updated by cron, only by command line. Cron is set with my own user, so I cannot see a permission problem. Also, the script is able to download the images and save them in my wallpapers folder. If I put a > /home/user/wallchanger.log after the cron command, the file is created with no errors, just the edit of backgrounds_advanced.xml and background.png fails.
Any clues?
Thanks in advance.

---

### Post by onon_onon on 2009-10-07
I'm still testing it and I found another clue. It actually CAN edit the backgrounds_advanced.xml file, but it fails at some point. If I remove the <used array="item"/> from it, the script restore the tag and then stop working. It only works if I call it from command line. Maybe some error is preventing the script to run?

---

### Post by DoctorMO on 2009-10-07
I'm looking into rebuilding it, doing some more testing. poke me in a few days.

---

### Post by onon_onon on 2009-10-07
I never worked with python, but I do with a few other languages and I will be glad to help, if you need. Really enjoyed the idea of auto switching wallpapers.

---

### Post by uschxc on 2009-10-07
> **onon_onon said:**
> I never worked with python, but I do with a few other languages and I will be glad to help, if you need. Really enjoyed the idea of auto switching wallpapers.

^^ i'm with him.  i'm getting too old to not have cut my teeth on a scripting language yet and i'd love to get some background on one.  will you have a karmic repo up soon?

---

### Post by DoctorMO on 2009-10-07
Hopefully, although this version 3.0 will take a day or so to sort out.

[https://launchpad.net/gnome-wallchanger](https://launchpad.net/gnome-wallchanger)

You can download the code via bzr already, have a look through it. I'm putting in a proper plugin system though, so most of that has changed already.

---

### Post by onon_onon on 2009-10-09
Latest code from launchpad is working fine, good job.

---

### Post by keiichidono on 2009-10-09
How is this better than say, wallpaper tray?

---

### Post by onon_onon on 2009-10-10
They are all the same (also new Karmic dynamic wallpaper), but this one can get images from internet.

---

### Post by Ninesvnsicks on 2009-10-12
Any chance of getting a port of this for windows?  I use both os's in my house would be nice to have on all the machines :)

---

### Post by DoctorMO on 2009-10-13
Ninesvnsicks, I think there are already existing tools that do this kind of thing for Windows users.

As for my tool, I don't think it's technically possible because it's very specific to gtk and the gnome desktop.

But even if it was, I'm not able to support windows, for political reasons.

---

### Post by Ninesvnsicks on 2009-10-13
yeah I don't blame you the only reason I even use windows is because my games run like crap in Linux and video encoding.  I have an old system I need to upgrade lol.  there are some that are sort of like your tool but I haven't found one that does the rss feeds.

---

### Post by DoctorMO on 2009-10-14
Not to get too off topic, but the video encoders/demuxers under Ubuntu are so much better (faster etc) than the ones that come with Windows. Check out the Avidemux Gtk+ package in Add/Remove...

---

### Post by Ninesvnsicks on 2009-10-14
There are video encoders that come with windows?  I use TMPGEnc to make dvd's of my videos mostly, is Avidemux Gtk+ a video editor or a converter I mostly take my avi's and put them to dvd format.

---

### Post by DoctorMO on 2009-10-14
Off Topic: For DVDs you probably don't want transcoding the video then, you just want some menu creation (DeVeDe) and Brasero to compile and burn the result.

hopefully you've used Avidemux to convert your videos into mpeg2 video with ac3 audio streams.

---

### Post by Keikowned on 2009-11-04
I get this error when attempting to install with the .deb package
(Error: Dependency is not satisfiable: python-crontab) 

Any way to fix this situation?

---

### Post by DoctorMO on 2009-11-04
You have to install the python-crontab deb from my PPA, you should be installing this from the PPA and not from a random deb file.

---

### Post by Keikowned on 2009-11-05
> **DoctorMO said:**
> You have to install the python-crontab deb from my PPA, you should be installing this from the PPA and not from a random deb file.

Ok, I added the PPA (authed key etc) and updated list. But I don't see it at the Update Manager to download.

---

### Post by AldenIsZen on 2009-11-12
> **Keikowned said:**
> Ok, I added the PPA (authed key etc) and updated list. But I don't see it at the Update Manager to download.

Same here. I added the PPA, but am unable to find gnome-wallchanger, and I have refreshed synaptic. Am I doing something wrong perhaps?

---

### Post by jimmycorcoran on 2009-11-13
cant get it to install

---

### Post by hellocatfood on 2009-11-13
> **jimmycorcoran said:**
> cant get it to install

We're going to need more details than that :p What error messages do you get when you try to install?

---

### Post by AldenIsZen on 2009-11-13
I get a pop-up when looking for updates. The main body states:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.In the scrollable field the error is as such:
> 
Failed to fetch [http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Arthur_D on 2009-11-13
Listen guys, what I did was installing plasma-desktop, running it on top of the Gnome desktop and placing it as a startup application; then I can have this feature and not fiddle with apps that don't work (not saying that this doesn't work, but 2 other such apps didn't work).
That and K3b is the only things I need KDE for. ;)

---

### Post by AldenIsZen on 2009-11-13
Thanks, but I don't care to install any KDE apps as that means I must install KDE and that has led to issues for me in the past. I plan on trying out OpenSUSE later, and that may help me see the benefits of KDE, as I haven't played with Kubuntu enough to see why I would like it better than gnome. Sure there is some pretty stuff, but there were lots of bugs last time I tried and I just want it to work, above all else.

 In this case, I think there is an issue with the repository or something. I am not knowledgeable to know what that is. I believe that it works, we just can't get it installed is our main issue at the moment.

Doc, you mentioned that this would be a good place to start assisting with free software. Any pointers on where to go to start learning to program? /edit - I found [this]("http://pine.fm/LearnToProgram/") (pine.fm/LearnToProgram/) site for learning Ruby. Much easier than I thought!

---

### Post by krige on 2010-04-06
> **AldenIsZen said:**
> Same here. I added the PPA, but am unable to find gnome-wallchanger, and I have refreshed synaptic. Am I doing something wrong perhaps?

Same here: I added the PPA, but am unable to find gnome-wallchanger. Running Ubuntu 10.04 amd64.

---

### Post by DoctorMO on 2010-04-06
It's not going to work in Lucid, there isn't any builds done.

---

### Post by AldenIsZen on 2010-04-13
Is till haven't been able to get this instaled using the PPA. I have added it to my software sources, and also added the key... I am using Karmic, which seems to be OK. I tried updating, I tried sudo apt-get install gnome-wallchanger, and I get the error "E: Couldn't find package gnome-wallchanger".

 Have I done something wrong?

---

### Post by hellocatfood on 2010-04-13
It relies on the python-xml package, which was in Jaunty but not in Karmic (and I doubt it'll be in Lucid either).

So, until the code is changed I doubt it'll start working anytime soon.

---

### Post by AldenIsZen on 2010-04-13
Thanks. Oh well, have to just make do without. I never did get around to trying Suze.

---

### Post by hellocatfood on 2010-04-13
If you're making your operating system decisions based on a wallpaper changer then you'll be doing a lot of bouncing around! Here's the bug report for the problem that I mentioned: [https://bugs.launchpad.net/gnome-wallchanger/+bug/510098](https://bugs.launchpad.net/gnome-wallchanger/+bug/510098)

Gnome-wallchanger was one the better solutions, but it's not the only one.

---

### Post by AldenIsZen on 2010-04-14
> **hellocatfood said:**
> If you're making your operating system decisions based on a wallpaper changer then you'll be doing a lot of bouncing around!

 No, I was going to try Suze since it has pretty good KDE support, better than Kubuntu by many accounts. I like to try different things, and the fact that it has features that appeal to me such as a wall-paper switcher helps. Notice I said that I would do without, for now, and stick with Ubuntu.

 Thank you for the link, I will check it out.

/edit - Added myself to those bug affects. Do you have some decent alternatives that you can recommend?

---

### Post by hellocatfood on 2010-04-14
Wallpaper tray is the only one that comes close to wallchanger. Just be warned, don't set the change interval to 0, you'll likely freeze your system

```
sudo apt-get install wallpaper-tray
```

---

### Post by tica vun on 2010-04-14
Meh, I have to stitch wallpapers together in gimp to fit my 2560*1600 + 1920*1200 monitor setup anyway, it'd look ugly if it just pulled them off some random feed.

---

### Post by AldenIsZen on 2010-04-14
> **hellocatfood said:**
> Wallpaper tray is the only one that comes close to wallchanger. Just be warned, don't set the change interval to 0, you'll likely freeze your system

```
sudo apt-get install wallpaper-tray
```

 I installed it, but can't seem where to find it to launch it, or what the command is. I can pull up the man page, but that is not the command to launch it.

---

### Post by hellocatfood on 2010-04-14
It's a panel application. Right-click on your panel and select Add to Panel. From there you'll be able to see it. You can click on the icon to change the background.

---

### Post by Ninesvnsicks on 2010-05-03
If it relies on the python-xml package can we just install python-xml?  Also when will their be builds for 10.04? Cuz I love this app :)

---

### Post by hellocatfood on 2010-05-03
If you really want to you can install python-xml from here: [https://launchpad.net/ubuntu/karmic/i386/python-xml/0.8.4-10.1ubuntu2](https://launchpad.net/ubuntu/karmic/i386/python-xml/0.8.4-10.1ubuntu2) I tried installing it after that and it didn't work. I think python-xml relies on an older version of python

---

### Post by BK201 on 2010-06-06
sorry, I'm new to linux, and this forum too.. is there any possibility to make it work on lucid? Cause everything i read about this changer sounds like it's the one I looked for..

---

### Post by DoctorMO on 2010-06-06
Hey BK201, it's quite possible that any python programmer would be able to get it working and make a release, if you'd like to pay me to get it working for you, please do email me.

---

### Post by rEnr3n on 2010-09-27
Why can't I install gnome-wallchanger?

E: Couldn't find package gnome-wallchanger

---

### Post by DoctorMO on 2010-09-27
It doesn't exist for newer Ubuntu releases.

---

### Post by axwack on 2010-10-04
How much memory and overhead on the system is this?

---

