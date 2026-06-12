---
title: "Two Picasa 3.5 or 3.6 fixes: video (.mov, etc.) and fix the &quot;places&quot; sidebar freeze"
date: 2010-01-20
forum: Tutorials
---

### Post by jnewm on 2010-01-20
Hi all!

So, I'm posting this after I managed to make these two fixes to my Linux version of Picasa (3.6), running Jaunty.  However, since much of this advice came from outside the forums, and because I think it took a few new tweaks on my part, I am posting this pseudo-tutorial... in case it helps others!

(PS If you don't yet have Picasa 3.5 or Picasa 3.6 installed, go to [http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html](http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html) for instructions)

**#1 - Playing video files (.mov, etc.) in Picasa...**

Officially, Google tells you that Picasa for Linux won't play videos: [http://picasa.google.com/linux/faq.html#15a](http://picasa.google.com/linux/faq.html#15a).  They're wrong.  Thanks to AlanRick and this forum thread, [http://ubuntuforums.org/showthread.php?t=967713](http://ubuntuforums.org/showthread.php?t=967713), I found the amazing set of instructions at [http://wiki.winehq.org/picasa](http://wiki.winehq.org/picasa).  Thank you to Christian and whoever else put them up! However, it took me a while to wrap my head around the exact steps, and I believe it took a couple extra tweaks, so I'm going to lay them out here step by step.  (But please take a look at all the warnings on the site first; I've been synchronizing fine with my web albums, but you never know):

(1) Configure Wine generally - Run "winecfg" in a terminal, go to the "Applications" tab, then go to the "Windows Version" field, choose "Windows XP", and click "OK".

(2) Configure Wine for the Picasa wrapper - Run "/opt/google/picasa/3.0/bin/wrapper winecfg" in a terminal, and do the same.  (You can have program specific settings, and I think you need to have the right settings specifically for the wrapper. If anyone can confirm whether this step is necessary, please let us know.)

(3) Download Quicktime Alternative version 2.7.0 (quicktimealt270.exe) - It took me a little while to find this, at [http://codecguide.com/download_qt_old.htm](http://codecguide.com/download_qt_old.htm) (just choose a mirror for the right version).

(4) CONFIRMED UNNECESSARY [S] Install Quicktime Alternative straight up (probably unnecessary) - Okay, I accidentally installed Quicktime Alternative straight from the download when Firefox asked me if I wanted to open it with Wine.  I'm pretty sure this is unnecessary.  But if you want to do exactly what I did, go ahead and do the same.  Make sure to follow the configuration instructions laid out in the next step. (Again, if anyone can confirm that this step is unnecessary, let us know and I'll delete it.) [/S]

(5) Install Quicktime Alternative the right way (through the Picasa wrapper) - Run "/opt/google/picasa/3.0/bin/wrapper /home/quicktimealt270.exe" (of course substitute "/home/" for whatever path leads to your .exe file).  Then follow these configuration instructions (I remember the actual installation being slightly different then the posted instructions, but it was easy enough to follow and I don't remember exactly what was different, so I'm just re-posting verbatim): [INDENT](a) choose to install the "full" version thus "mplayer classic install" is checked; [/INDENT][INDENT](b) make sure the "configure settings for quicktime" box is checked; [/INDENT][INDENT](c) when the quicktime window settings is opened go to the "advanced" tab and choose to use GDI.[/INDENT](6) Link Picasa to the QuickTimePlayer.exe file (again maybe unnecessary) - Run "/opt/google/picasa/3.0/bin/wrapper QuickTimePlayer.exe" in a terminal.  (To give some background, I first tried running "/opt/google/picasa/3.0/bin/wrapper "c:/Program Files/QuickTime Alternative/QuickTimePlayer.exe"" and then "/opt/google/picasa/3.0/bin/wrapper "/home/username/.wine/dosdevices/c:/Program Files/QuickTime Alternative/QuickTimePlayer.exe"", but both of these commands gave me a whole bunch of error messages.  Then I tried the "/opt/google/picasa/3.0/bin/wrapper QuickTimePlayer.exe" command, and did not get any error messages. Accordingly, to the extent any of this was necessary, I suspect it was the latter that worked.)

(7) Restart Picasa (and Ubuntu?) - I'm pretty sure I had to do one or both of these.

(9) Configure Picasa - Go to "Tools" then "Options" then "File Types" and check the two movie file types. (PS I skipped 8 on purpose, because it made a smiley face with sunglasses) :).

(10) Maybe Restart Picasa (and Ubuntu?) again?

(11) Load your video files!  (I confirmed this to work with .mov, .3gp, and .3g2 files, because that's all I had.  I have also been synchronizing to the web, without problems so far.  Although, again, check the warnings at [http://wiki.winehq.org/picasa](http://wiki.winehq.org/picasa).)

One more time, please let me know if people can better deduce which steps were and were not necessary, so I can tighten ship on this tutorial!

**#2 - Fixing the Picasa freeze after you accidentally click on the "Places" sidebar**

After doing much face tagging that I really did not want to lose (PS I strongly suggest that anyone who spends a lot of time on face tagging backup their tags; I liked jaysiej's suggestions at: [http://www.google.com/support/forum/p/Picasa/thread?tid=0727103717c22cd7&hl=en#all](http://www.google.com/support/forum/p/Picasa/thread?tid=0727103717c22cd7&hl=en#all)), I made the brilliant decision to click the "Places" button below the sidebar on the bottom right corner of Picasa.  This froze Picasa, and caused Picasa to freeze immediately whenever I re-started it.  Thankfully, however, I found a solution at [http://markmail.org/message/44hajtxuivqq7ii7#query:picasa%20frozen%20places+page:1+mid:c45ivju4hsnd2llg+state:results](http://markmail.org/message/44hajtxuivqq7ii7#query:picasa%20frozen%20places+page:1+mid:c45ivju4hsnd2llg+state:results) (thanks to Henri and Ege!), which I will now re-post; so that it's on the forums, and because it took me a while to find the file location:

(1) Exit Picasa if it's running.

(2) Navigate to "/home/username/.google/picasa/3.0" (of course change "username" to your username, and you'll have to show hidden files to get there), and open "user.reg" (you may want to make a backup of user.reg first).  You could also just run "gedit /home/username/.google/picasa/3.0/user.reg" in a terminal.

(2) Change "active_metadata_tab"="thumbui/places_toggle"
to "active_metadata_tab"="thumbui/people_toggle" (all quotation marks included). 

(3) Save user.reg.

(4) Start Picasa!

That's it!

Alright everyone, please let me know if this helps even just one person.  So I can justify the two hours I spent writing this mess of a tutorial :P!

Thanks!
jnewm

---

### Post by nanonils on 2010-01-30
Amazing! That really does work! Odd that Google wouldn't make it default.

I found your step (4) unnecessary. 

Thank you much for figuring it out and assembling this guide!

---

### Post by jnewm on 2010-01-30
Hi Nanonils,

I agree, odd, and thanks for confirming, I cut out step #4.

No worries!  I'm really glad it helped, as I have a lot of paying back to do for all the people on the forum who've helped me! ;).

Take care!

---

### Post by nanonils on 2010-01-31
Aaaaand if you, too, 
[LIST]
[*]have the new Canon Powershot S90 and 
[*]find that movies save as *.mov and
[*]find that those movies are never rotated right and
[*]rotating them with Avidemux does not allow to keep the *.mov format and find that Picasa does not allow import of *.avi although this is checked in options,
[*]here is what works for me:
[/LIST]

1. rotate movie in *.MOV in Avidemux (called "filter")
2. convert *.AVI back into *.MOV using WinFF 
3. upload to your Picasa album
4. be disappointed about the resolution
5. be happy about being able to keep a movie that belongs to photos taken at the same time

---

### Post by elbono on 2010-02-10
Ah I just spent the last while figuring out how to get rid of the places freeze myself. I thought I was a little genius. I just deleted the line "active_metadata_tab"="thumbui/places_toggle" from user.reg and it worked fine for me. Thanks for the post though, it's very well presented.

---

### Post by jnewm on 2010-02-10
Thanks elbono, and although I'm sorry we had to duplicate efforts, I think that genius moment where you actually figure something out without express instructions makes it all worth it ;).  (At least for me...)

---

### Post by ernstblaauw on 2010-03-09
On my Ubuntu 10.04 64-bit, I'm running picasa with native wine (1.1.40), because with Google's environment, picasa 3.6 won't start.

I do not succeed in getting the movies to work. I installed Quicktime Alternative (as I use the open source ati drivers on a 64-bit system, I have to issue the command "LIBGL_DRIVERS_PATH=/usr/lib32/dri wine control.exe /home/USER/.wine/drive_c/Program\ Files/QuickTime\ Alternative/QTSystem/QuickTime.cpl" to launch the Quicktime control panel), but after that, Picasa crashes during the import of the first movie. If I start Picasa again, it asks to hide that movie file, but then it crashes on the next.
I tried installing newer QuickTime's, but without success. Does someone know how to enable the movie capabilities of Picasa on my system?

---

### Post by izar on 2010-03-10
great post.;)
does this let me use any movie type (eg. .mpg) or only apple types (like .mov) ?

---

### Post by nanonils on 2010-03-10
I can only get *.mov to work unfortunately. But I'm a bit of a novice.

---

### Post by kellemes on 2010-03-21
Thanks for re-posting the "freeze-fix", works fine for me.

---

### Post by jnewm on 2010-03-22
I'm so glad the post has been helpful...  Izar, by following these steps, I also had .3gp and .3g2 files working.  I'm not sure about .mpg files.  Have you tried yet?

---

### Post by izar on 2010-04-04
> **jnewm said:**
> I'm so glad the post has been helpful...  Izar, by following these steps, I also had .3gp and .3g2 files working.  I'm not sure about .mpg files.  Have you tried yet?
picasa detects only .mov files on my machine, yet it doesn't detect all .mov files and doesn't play them at all. 
note: i use picasa 3.0 for linux from deb package.

---

### Post by Danial on 2010-07-03
Thanks a lot for a wonderful guide.  I was able to install and fix the "places" freeze issue.  I am not sure about video files - as of now, unable to play mpeg (that is all I have at the moment)- I will keep checking into it.

Danial:p

---

### Post by tiredrobot on 2010-07-04
After this fix it seems to handle AVIs as well.  However, you have to have the codec.  I installed a free MJPEG codec from free-codecs.com, and XVid.  To install i downloaded the installer exe, and ran it using googles wrapper, as above.  

Once i did this and restarted picasa, it starts playing all the videos it could not formerly view at double speed.  Playback is in a wine video window of some sort.  This is very annoying, as the window keeps popping and grabbing focus.  Worth letting it run through all this while you take a break and do something else.

---

### Post by tiredrobot on 2010-07-04
Euh... i retract my last post.  It worked briefly, but now no longer finds the videos.  It found some, and they would play in a pop up when clicked.  some had a good thumbnail.  Some did not have a good thumbnail, but were found anyway.  But after a few restarts, eventually they all disappeared.

Frustrating.

---

### Post by ^_Pepe_^ on 2010-09-24
Hi!

Definitely, you saved my life.

After SEVERAL hours procrastinating, eeer, well....identifying faces, I clicked "places button"...

:-S

Thanks! (1000 times)

---

### Post by pulck on 2010-12-20
I tried the video fix on Ubuntu 10.10, but it causes problems. Picasa launches okay but when it scans through pics/videos the screen goes black momentarily and when it reappears there are screen refresh problems and Picasa is unusable.

Any ideas what might be causing this?

---

### Post by Bryan55 on 2011-01-14
Hi.
I have been having trouble with step 5 from the first post.

I entered
 "bryan@Bydand:~$ /opt/google/picasa/3.0/bin/wrapper/Downloads/quicktimealt270.exe"
but I got this
"bash: /opt/google/picasa/3.0/bin/wrapper/Downloads/quicktimealt270.exe: Not a directory"
edit.(changed it to  "/opt/google/picasa/3.0/bin/wrapper /home/bryan/Downloads/quicktimealt270.exe" but got no mpg's)
I'm not that good with command lines.

Some help please.
Bryan.

---

### Post by macd0g on 2011-02-20
yeah, i get to stage 5, and get this:

any takers?

monkey@monkey:~$ /opt/google/picasa/3.0/bin/wrapper /monkey/quicktimealt270.exe
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey''.
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey.exe'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey.exe''.
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey''.
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey.so'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey.so''.
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey.exe.so'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey.exe.so''.
monkey@monkey:~$ /opt/google/picasa/3.0/bin/wrapper /monkey/quicktimealt270.exe
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey/quicktimealt270.exe'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey/quicktimealt270.exe''.
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey/quicktimealt270.exe.exe'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey/quicktimealt270.exe.exe''.
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey/quicktimealt270.exe'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey/quicktimealt270.exe''.
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey/quicktimealt270.exe.so'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey/quicktimealt270.exe.so''.
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-iname `/monkey/quicktimealt270.exe.exe.so'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/monkey/quicktimealt270.exe.exe.so''.
monkey@monkey:~$

---

### Post by izar on 2011-08-10
great post:D
works to me with picasa 3.8 on ubuntu 10.10
although the link for the quicktimealt270.exe seems to be broken. i had to google the file name and that way i fond it.

---

### Post by verdomde on 2011-08-12
try  /opt/google/picasa/3.0/bin/wrapper /home/monkey/quicktimealt270.exe

I got the same error until I got the path right (plus i got the quicktimealt from filehippo and saved in Downloads folder).

Can confirm it works with natty 11.04 and picasa 3.8, 3gp and .mov, but not yet avi- not looked into that yet...

---

### Post by jacortijo on 2011-12-29
ubuntu 11.10 with picasa 3.8. 
works like a charm with w4m files but AVI are not detected!! 

any idea why?

---

### Post by wildneuro on 2012-01-25
Thanks a lot! All work. Video is work. No hangs. Thanks!:KS

---

### Post by ramoul on 2012-02-26
Anyone had any chances with AVI?

---

