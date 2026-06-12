---
title: "Wallpaper program"
date: 2006-10-26
forum: The Cafe
---

### Post by DoctorMO on 2006-10-26
[COLOR="Red"]**OK, ATTENTION! There is a new app I made which is much better than this. see here:**[/COLOR] [http://ubuntuforums.org/showthread.php?p=5581392](http://ubuntuforums.org/showthread.php?p=5581392)

[COLOR="Red"]**So please ignore this hacky script and use the app.**[/COLOR]

I've written this small python program which picks out a random background from your list of gnome backgrounds; including all it's settings (colours, options, transparency etc) and sets it as the current settings.

I've done this for a friend of mine who wanted a KDE like wallpaper option, I've created this as an icon and as a per hour using the Schedual program.

all good fun. send patches if you like.

(see attached)

---

### Post by Old Pink on 2006-10-26
Get in in the repositories! ;) 

Good application. :)

**HINT: **Extract this to your home directory, and add /home/user/changer to your startup session to have a random wallpaper selected at startup. ;)

---

### Post by Martin1 on 2006-10-26
I am the friend and this is a great add on everyone should have lets see it on the updates and included in the Ubuntu instalation. Incidentally see my new thread for comments on screen savers.

---

### Post by darkhatter on 2006-10-26
will this change my wallpaper every minute or so like it does in kde?

---

### Post by Brunellus on 2006-10-26
> **darkhatter said:**
> will this change my wallpaper every minute or so like it does in kde?
I imagine it Kan. I doubt that KDE users will Kondescend to Kast even an eye in its direKtion.

---

### Post by DoctorMO on 2006-10-26
Add Remove programs and add Schedula it's a nice cron editing program and add my program to run every minute.

---

### Post by darkhatter on 2006-10-26
> **Brunellus said:**
> I imagine it Kan. I doubt that KDE users will Kondescend to Kast even an eye in its direKtion.

I wasn't trying to start flamewar or anything I wanted to know if the feature was there

---

### Post by Brunellus on 2006-10-26
> **darkhatter said:**
> I wasn't trying to start flamewar or anything I wanted to know if the feature was there
My K-posts are all facetious. don't worry.  I just love poKing fun at the KDE naming Konventions.  (There I go again!).  It's just easy, since the K phoneme is a lot more common than the G one.

---

### Post by DoctorMO on 2006-10-26
There was no point in adding a timing feature... it would be like adding wheels to a tomato, very time consumming and utterly pointless.

Use cron that what it's there for.

---

### Post by darkhatter on 2006-10-26
ok

---

### Post by Polygon on 2006-10-26
there was a program like this in the repositories that i tried and it didnt work... so im happy that someone created this!

thanks

---

### Post by DoctorMO on 2006-10-26
I was rather hoping the almighty aysiu would praise my hours worth of work ;-)

It's been written in python instead of bash as the old one was because the way it was greping was very unsafe. this way it deals with the xml as an xml document; there is no reason why this could not edit the backgrounds options or get developed into a configuration utility with glade.

I won't be doing that; but the option is there.

---

### Post by darkhatter on 2006-10-26
why don't you take everything you did here and submit it to the gnome developers? That way it'll be built in

---

### Post by deepwave on 2006-10-26
Hehe... This is so off-topic but the thread title pogram reminds me of pogrom (or purge).

For a second, I thought you were talking about the background "rollback" issue that happened in Edgy's beta.  Guess not. ;-)

---

### Post by yabbadabbadont on 2006-10-26
I haven't dug into your python code yet, but how well do you think it would handle a list of wallpapers that contains more than 50,000 images?  I wrote some bash scripts that work well using Esetroot and Fluxbox, but I don't know how to adapt them to Gnome and Nautilus.

---

### Post by DoctorMO on 2006-10-27
50,000 wouldn't be a problem you'd just have to have them all defined in background.xml which might take some parsing.

---

### Post by yabbadabbadont on 2006-10-27
Having looked through your nice python code, I think I'll just modify it to make use of the wallpaper list my scripts keep updated (I have a cron job for that).  I like that, since your script is changing gconf settings, it doesn't matter if you have X running when it gets called by cron.  Very nice.  Thank you.

---

### Post by DoctorMO on 2006-10-27
Could you post your code? comparative notes and feature swapping?

---

### Post by yabbadabbadont on 2006-10-27
There aren't many features per say with these as I didn't need them to do much.  Some of the scripting logic was blatently stolen from Fluxbox's fbsetbg script. :-D

The wallpaper-list-create script needs to be run once before running any of the other scripts.  I usually have it set to run as a cron job every 30 minutes.  In Fluxbox, I would run wallpaper-set-rotate in my ~/.fluxbox/startup script and then kill it when exiting.  The wallpaper-name-overlay script adds the filename, with a semitransparent background, to the upper right corner of an image.  (Useful when you have serveral thousand images)  It uses the convert program from ImageMagick to do this.

EDIT: I recently discovered that Bash's RANDOM only returns values from zero to 32k.  So if you have more than 32k wallpapers, my scripts will only randomly display images from the first 32k listed in ~/.wallpaperlist  Just FYI.  (I'm going to write a simple C program to generate the random numbers for my script to fix this issue)

---

### Post by DoctorMO on 2006-10-27
thanks yabbadabbadont, Your a regular bash master some of that stuff is very advanced (at least from my perspective) I guess when ever I get into advanced stuff I move to perl or python rather than trying to do it in bash.

---

### Post by yabbadabbadont on 2006-10-27
It's just a matter of learning by example.  Anytime I find that an installed program is actually a script, I tear it apart to see how it works.  Most of the tricky bits in those scripts were what I got from fbsetbg.  Now I guess I'm going to have to finally break down and read "Dive Into Python" to see how to handle reading from plain text files.  The little Python I know, came from fixing/enhancing desklets from Adesklets.  (and a lot of that was trial and error :))

---

### Post by yabbadabbadont on 2006-10-28
Well I did some research and installed SPE for a Python IDE.  Very nice I must say.  It sure makes browsing through Python code much easier.  Since the only part of my scripts that I need to change for Gnome/Nautilus is the actual command to set the selected wallpaer, I'm going to gut your Python code so that it only does that (based on passed parameters).  In the past, I tried calling the gconf command line editor to adjust the settings, but it was very inconsistent about actually applying them to the desktop.  (even though the new wallpaper showed up correctly in the backgrounds list...)  I think that the commit_change_set() call your code uses will make all the difference.  Thanks again for providing your program.

---

### Post by DoctorMO on 2006-10-28
Not sure, if you want to add new backgrounds to the backgrounds list you should add more settings to the xml document and save back to ~/.gnome2/backgrounds.xml 

the gconf will only set the current background.

---

### Post by yabbadabbadont on 2006-10-28
That's just it, I don't want to add 50,000 odd backgrounds to the list.  (that would be monumentally stupid of me :D )  What I have done is to add ~/.current-wallpaper.jpg to the list and selected it.  Then the rotate script copies the new image to that name and overlays the filename on the image.  I ended up figuring out how to get gconftool to force an update of the gnome desktop, so I'm only using bash scripts now.  (It was good to see your python code though, thanks.)  I had some trouble with cron though.  The crontab mechanism used by Ubuntu appears to be the old style where you can't specify the home directory or the path in the crontab file.  (Why isn't vixie-cron in the repositories anywhere?)  I had to hack my scripts so that they are specific to my user's home directory.  It doesn't really matter, since I'm the only user of the system, but I would have preferred a more generic approach.

---

### Post by darkhatter on 2006-10-28
This is starting to sound messy, I think I'll just stick with kde

---

### Post by maniacmusician on 2006-10-28
lol have you been reading? It's only "starting to sound messy" because yabbadabbadont is a coding expert and is having fun taking parts of Martin's script to create his own hybrid background changer.

If you use martin's script with the original instructions given, you won't have any problems. So don't make judgemental statements like that just to promote kde. 


PS: I love kde too.

---

### Post by darkhatter on 2006-10-28
ok I see whats going now, another question do I have to manually right in all the wallpapers or can I point it to a directory and it'll pick from that.

---

### Post by maniacmusician on 2006-10-28
not sure, i don't use gnome. i'm no coder, but from the code, it looks like it takes the pictures from ~/.gnome2/backgrounds.xml. I'm guessing that's a list that's generated by whatever the default desktop management program is. So what I would try is, open the desktop manager, and using that, add all the pictures that you want to be included in this. and then using Schedula, add the changer program and tell it to run every minute or however often you want it to switch the wallpaper.

---

### Post by DoctorMO on 2006-10-28
darkhatter, we use the gnome desktop wallpapers settings because a wallpaper is more than just an image. it contains options, formating, primary and secomdary colours even trasparency if anyone would create the opens for it in gnome.

Not that I could get a directory working either, let me know and I'll add it as a feature.

---

### Post by yabbadabbadont on 2006-10-29
> **maniacmusician said:**
> lol have you been reading? It's only "starting to sound messy" because yabbadabbadont is a coding expert and is having fun taking parts of Martin's script to create his own hybrid background changer.

If you use martin's script with the original instructions given, you won't have any problems. So don't make judgemental statements like that just to promote kde. 


PS: I love kde too.

I apologize for taking the thread offtopic there for a bit.  Won't happen again.

---

### Post by maniacmusician on 2006-10-29
its no problem, I don't think anyone minds. the posts were interesting, even though I only half understood them. and it wasn't technically off topic. don't sweat it.

---

### Post by yabbadabbadont on 2006-10-29
I try to be a bit more polite with my posts here than I am when I post in the Gentoo forums.  Things are usually a little more courteous here than there.  :)

Since I have all 50 some odd thousand of my wallpapers in a directory tree, I ended up achieving the same thing using only regular bash shell scripts.  The trick is to use gconftool from the command line to set the picture_filename to "" and the picture_options to "none", then change them back to their proper settings so that gnome will force the desktop and all running applications to redraw using the new background.

---

### Post by vierranet on 2006-10-29
automatic background image change: 

> mkdir ~/.backgrounds
cd ~/.backgrounds
wget -c [http://easylinux.info/uploads/change_background.py](http://easylinux.info/uploads/change_background.py)
chmod +x change_background.py

    * To change desktop background every time you reboot your computer 

> export EDITOR=gedit && crontab -e

    * Add the following line at the end of file 

> @reboot ~/.backgrounds/change_background.py

    * ~/.backgrounds is hidden directory

    * Copy images you wish to see on your background to ~/.backgrounds directory

---

### Post by DoctorMO on 2006-10-29
nah, that will only change the background image. it won't touch any options which means that if you select a background which is stretched and then it tried to display a letter box image it'll be stretched horribly accross the screen.

The best way to do this is: have a directory where new files are picked up and added to the gnome backgrounds configuration. any files already in the backgrounds don't need to be added but the important thing is that setting changes in gnome backgrounds will remain.

---

### Post by Polygon on 2006-11-02
this really is a great program, except i hate it when it picks the (in my opinion) really ugly default/no wallpaper options......

---

### Post by Old Pink on 2006-11-07
Gave you a mention on my blog: [http://matt.moved.in/?p=38](http://matt.moved.in/?p=38)

This is really good, keep it up! :)

---

### Post by DoctorMO on 2006-11-07
glad you like it. I wonder if we can get in into gnome :-D

---

### Post by .t. on 2006-11-07
Mmmm.... wheeled tomato...

---

### Post by DoctorMO on 2006-11-07
Are you saying my application is a wheeled tomato? (you know where the quote is from?)

---

### Post by .t. on 2006-11-07
No idea where it's from (except your post). And I don't think it's a wheeled tomato, rather a great idea! Just a curious thing to say, that's all I thought...

---

### Post by DoctorMO on 2006-11-07
It's a quote from Black Adder the Third: Ink and Incapability

Dr Johnson: "Copy sir, I have no copy. making a copy is like putting wheels on a tamoto; time consuming and utterly pointless." (talking about his new Dictionary, after baldrick has burned it)

OK I am sad but it was an apt quote.

---

### Post by GazaM on 2006-11-07
[Desktop Drapes]("http://drapes.mindtouchsoftware.com/")

---

### Post by DoctorMO on 2006-11-07
Hmm, you've got to have the program running all the time :-/ the inotify trick is rather cool through I might get to know pyinotify.

---

### Post by heindsight on 2007-01-15
Thanks! been looking for something like this for a while :biggrin: 

I've made a couple of changes to ignore wallpapers marked as deleted in backgrounds.xml as well as the "No Wallpaper" wallpaper. I also commented out the ```
print "Setting background to" ...
``` line to stop the script from flooding my mailbox when running under crond.

here's a patch if anyone's interested...

---

### Post by Lowfront on 2007-02-05
how do i get this program working?

---

### Post by yabbadabbadont on 2007-02-05
> **Lowfront said:**
> how do i get this program working?

Read the first two posts in this thread.  Especially the "HINT" in the second post.  :D

---

### Post by Somenoob on 2007-02-05
Thanks DoctorMO. This looks quite useful.

The only method that I knew of for random/changing wallpapers was some script that i was to lazy to put into effect.

---

### Post by TheRealEdwin on 2007-02-18
Is there a way I can get this script to choose a wallpaper from another directory? I have my wallpapers on a NTFS drive that I share with my XP install.

/media/My Documents/My Documents/My Pictures/Wallpapers

---

### Post by yabbadabbadont on 2007-02-18
> **TheRealEdwin said:**
> Is there a way I can get this script to choose a wallpaper from another directory? I have my wallpapers on a NTFS drive that I share with my XP install.

/media/My Documents/My Documents/My Pictures/Wallpapers

As long as that drive is always mounted when you start Gnome, then it should just be a matter of using Gnome's wallpaper settings dialog to add all of them to the list of Gnome wallpapers.  The script then randomly selects from that list.

---

### Post by t_anjan on 2007-02-23
> **heindsight said:**
> Thanks! been looking for something like this for a while :biggrin: 

I've made a couple of changes to ignore wallpapers marked as deleted in backgrounds.xml as well as the "No Wallpaper" wallpaper. I also commented out the ```
print "Setting background to" ...
``` line to stop the script from flooding my mailbox when running under crond.

here's a patch if anyone's interested...

Exactly what I was looking for (the "delete" attribute part). Thanks!

---

### Post by tjasko12 on 2008-06-10
> **vierranet said:**
> automatic background image change: 



    * To change desktop background every time you reboot your computer 



    * Add the following line at the end of file 



    * ~/.backgrounds is hidden directory

    * Copy images you wish to see on your background to ~/.backgrounds directory

THANK YOU! I was looking for something this simple for a long time now. I love this script. A simple search helped me. Highly recommend this python script!

---

### Post by fredunderhill on 2008-06-30
i know i must be a noob, but how do you install the file that you download?

---

### Post by tjasko12 on 2008-07-26
[http://www.youtube.com/watch?v=TkA7VIWRJC4](http://www.youtube.com/watch?v=TkA7VIWRJC4)

I've created a simple how to video... Hope this helps anyone with changing their wallpaper! Very simple for all the new users out there. :)

---

### Post by Delever on 2008-07-27
This one worked perfectly for a while. It uses current user's home directory without hacks, so you may want to have a look at that.

Usage:
- Set cron job to execute this periodicaly (place it where you want)
- Drop images into ~/.backgrounds directory
- You can set up launcher to change to other background, just use command "python wallpapers.py"

I imagine some working program in repositories would be great, just to keep us from reinventing the whale.

---

### Post by tjasko12 on 2008-07-28
> **Delever said:**
> This one worked perfectly for a while. It uses current user's home directory without hacks, so you may want to have a look at that.

Usage:
- Set cron job to execute this periodicaly (place it where you want)
- Drop images into ~/.backgrounds directory
- You can set up launcher to change to other background, just use command "python wallpapers.py"

I imagine some working program in repositories would be great, just to keep us from reinventing the whale.
Umm, do you realize I already posted about this Python file?

[http://ubuntuforums.org/showpost.php?p=5463827&postcount=53](http://ubuntuforums.org/showpost.php?p=5463827&postcount=53)

;) It's in the video... :) Some people are new to Ubuntu, or Linux for that matter. So, I've decided to create a tutorial for them. :)

---

### Post by DoctorMO on 2008-08-11
Curious, I wonder why so many people are interested in this feature. I didn't think it would be quite so popular.

Let me know if you'd like it to be a deb file and if you'd like other things.

---

### Post by Delever on 2008-08-12
> **DoctorMO said:**
> Curious, I wonder why so many people are interested in this feature. I didn't think it would be quite so popular.

Let me know if you'd like it to be a deb file and if you'd like other things.

Well then, could you investigate possibility to add cron job automatically, so it may be possible to make simple GUI to configure things. Basically, this:

Change duration (needs foolproof way to update cron job list item)
Wallpaper directory

So we could bundle it into .deb and make newbies happier :)

---

### Post by DoctorMO on 2008-08-13
Yes yes yes, see here:

[http://ubuntuforums.org/showthread.php?p=5581392#post5581392](http://ubuntuforums.org/showthread.php?p=5581392#post5581392)

---

### Post by shane2peru on 2008-08-15
> **DoctorMO said:**
> I've written this small python program which picks out a random background from your list of gnome backgrounds; including all it's settings (colours, options, transparency etc) and sets it as the current settings.

I've done this for a friend of mine who wanted a KDE like wallpaper option, I've created this as an icon and as a per hour using the Schedual program.

all good fun. send patches if you like.

(see attached)

Thanks Doc!  Great app!  I have been looking for something like this.  Does anyone know of any way to get rid of the plain color background?  Can you explain it in human terms for the rest of us ;) ?   Thanks!!!

Shane

---

### Post by lecter255 on 2008-08-18
Hey doctorMO thanks for this excellent program. I have a question though.

when i added all my wallpaper, they are going to be displayed tiled by default, so when changer switches wallpapers, they are all tiled. I want them to be displayed zoom style. how do you suggest accomplishing that? is there something i can tweak in your script or some other trick?

Thanks in advance. inputs from others are welcomed as well of course

---

### Post by DoctorMO on 2008-08-18
lecter255, was that for the new app (linked above) or the old script?

Just so EVERYONE knows. The new app is MUCH better. Contains a nice gui for config and handles all the crontab stuff for you.

---

### Post by shane2peru on 2008-08-18
> **DoctorMO said:**
> lecter255, was that for the new app (linked above) or the old script?

Just so EVERYONE knows. The new app is MUCH better. Contains a nice gui for config and handles all the crontab stuff for you.

Where do you find the new app????  How did I miss that?  Anyway, here are a few other options just for looking at. [http://ubuntuforums.org/showthread.php?t=892860](http://ubuntuforums.org/showthread.php?t=892860) I gotta see the new one though!

Shane

---

### Post by DoctorMO on 2008-08-18
> [COLOR="Red"]**OK, ATTENTION! There is a new app I made which is much better than this. see here:**[/COLOR] [http://ubuntuforums.org/showthread.php?p=5581392](http://ubuntuforums.org/showthread.php?p=5581392)

[COLOR="Red"]**So please ignore this hacky script and use the app.**[/COLOR]

Quoted from the first page edit I did.

---

### Post by shane2peru on 2008-08-18
> **DoctorMO said:**
> Quoted from the first page edit I did.

Lol!!! :oops:  call me blind!  How did I miss that it is even in red! lol.  I gave your old script a try.  That is too funny. Thanks for hitting me over the head with that, some times I need that.

Shane

---

### Post by Niaerdh on 2010-08-10
Ubuntu noob here, how do i install it?

---

