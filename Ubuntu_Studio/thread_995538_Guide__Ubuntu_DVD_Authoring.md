---
title: "Guide:  Ubuntu DVD Authoring"
date: 2008-11-27
forum: Ubuntu Studio
---

### Post by pyromanic123boom on 2008-11-27
[U][B]I have now created a new, complete, more detailed guide for devede. 
forum link: [http://ubuntuforums.org/showthread.php?t=1009684&highlight=devede+complete](http://ubuntuforums.org/showthread.php?t=1009684&highlight=devede+complete)

original site link: [http://pyromanic.publichost.de/devede_guide/](http://pyromanic.publichost.de/devede_guide/)[/B][/U]


**Guide:  Ubuntu DVD Authoring**

**Introduction**
If you're like me, you may find a lot of Linux multimedia applications lacking; they don't compare to mainstream Windows.  I have tried out a lot (too many, really) DVD authoring related programs for Ubuntu.  I will be showing you the most fail-proof way, without involving the mess.

**DVD Applications/Reviews**
_ManDVD, 4/10:_ Provides some better graphical menus, but is very prone to crashing and isn't fully translated. DVDs are shaky as well.
_DVDStyler, 6/10:_ I love CUI tools, but not when it comes to something complex like DVDs. It just makes it harder and nobody wants to bother with typing in a huge string of commands when you make a DVD. It has a GUI, though, which is-
_Q-DVDStyler, 8/10:_ Great program.  Offers a lot of options, so it makes it somewhat confusing if you're unsure.  Website has great guides on this program.
_Tovid, 6/10:_ Although I know this probably deserves a better rate, it just doesn't work for me.  It is CUI, and only has some shaky GUIs, which don't unlock its full power. Website is great.
_DeVeDe, my choice. 9.5/10:_ Very excellent, straight to the point, no nonsense. Menus aren't always the best, but you can make them pretty if you bother. Possible to fit two 2hr. movies on a single layer DVD. Subtitle support, and they're not burnt in.(subtitle button on your remote). YES!

**Guide: DeVeDe**
After I tried out every tool, I have settled on DeVeDe. It is clear, and makes things simple. Figure out your DVD Player Region: be it NTSC or PAL.

To start, you will need a standard AVI file. If you need to convert, try Avidemux. (Available in the repos). I have successfully put two 2hr. movies onto one DVD. (both were about 700mb avis). So, with settings on default, you can add roughly 4 hours of video!

Open Devede. When it asks you what type you'd like to create, choose Video DVD. Now, on the left, it says "title 1". When we make a menu (you don't have to), this will be the text for the button. So you might change Title 1 to My Movie Here, or whatever you would like. Then on the right, add the video files for that title. You also can load subtitles in (srt or sub format) and set the language code for it. Remember to set the region code. Mine is NTSC.

[IMG]http://pyromanic.publichost.de/dvdauthoring/img1.png[/IMG]

Now you've got your first title in. Add another movie, or video clip, or something. Remember you can add about ~4 hours, but you don't want to go over 4 GiBs. Hit the button that says "Adjust Disc Usage." 

[IMG]http://pyromanic.publichost.de/dvdauthoring/img2.png[/IMG]

Now we'll go onto the Menu. click on Menu Options. There are many options here, you may need to play with them to figure them out. 

1) You can add a title to the top of your Menu. Type it in, or leave it blank.
2) font for the title, text color and shadow for the text.
3) Background image and background music. Image has to be in PNG, (try Gimp, repos). 
4) Next is the placement of your title buttons. This is where the program is lacking a bit, they don't let your place your button exactly where you want. Basically it splits the screen in half, and lets you pick top, middle, or bottom on either side. If you're using a blank background, this is fine; if it's an image, you may have to edit the image for space. 
5) Next is font information for your buttons, along with Un-selected (what color the text will be on your tv) and selected. What color it will be when you click on it. Then there is shadow and background color. This makes a longish oval like shape around each title. It looks nice if you do it right, although it is not good if you have an image background. Usually I just edit the transparency and then it creates a blackout around it.
6) Here you can select if you want the menu to be shown when the dvd is played, or not at all. Of course, it will be still there, but it won't automatically go to it. Sometimes I use this if I've made an ugly menu. 

[IMG]http://pyromanic.publichost.de/dvdauthoring/img3.png[/IMG]

[IMG]http://pyromanic.publichost.de/dvdauthoring/img4.png[/IMG]

Preview the menu and edit it around.

**Finishing Up**
Click OK on the menu, and now you will go back to the main screen. Make any last minute changes (check region, etc), and then click on Forward. Here choose the output folder, and also type in the name of your desired ISO file. It will make the DVD, and then create an ISO and delete the temporary files. Makes it very convenient for burning.

[IMG]http://pyromanic.publichost.de/dvdauthoring/img5.png[/IMG]

[IMG]http://pyromanic.publichost.de/dvdauthor/img6.png[/IMG]

**Burning**
Put in a blank DVD, and then navigate to the folder with the ISO. Once the disc is mounted, right click on the iso and click burn. Then choose your burner and write!


guide by pyromanic123boom

---

### Post by sarc on 2008-11-29
I'd like to ask what are Devede's best advanced settings to make a best quality DVD from a miniDV digital recording?

I have found that capturing from Kino as raw DV and making a DVD with Devede gives good picture quality (much better than on-the-fly conversion to AVI or mpg from Kino for example), but I get jagged motion at times. I need to pick the right interlacing and bitrate, but I have no idea of linear, belnd, FFMpeg deinterlace... and what bitrate to use?

Any advice on best advanced settings is appreciated!

---

### Post by johnonfire on 2008-11-30
I ran apt-get update and install devede and it tells me I have the latest version of DeVeDe, but my version doesn't have the same options as yours.  Most of the options shown in your images are there but just located elsewhere.  However when I fill a disk with more than 100% of a single layer disc, there is no Disk Usage option to adjust compression.  So, I can't put anything longer than 2 hours on my disks.  Any advice?

I'm running Hardy-gnome and DeVeDe version 3.6-0.0

---

### Post by binbash on 2008-11-30
> **johnonfire said:**
> I ran apt-get update and install devede and it tells me I have the latest version of DeVeDe, but my version doesn't have the same options as yours.  Most of the options shown in your images are there but just located elsewhere.  However when I fill a disk with more than 100% of a single layer disc, there is no Disk Usage option to adjust compression.  So, I can't put anything longer than 2 hours on my disks.  Any advice?

I'm running Hardy-gnome and DeVeDe version 3.6-0.0

Devede's latest version is 3.11b

---

### Post by pyromanic123boom on 2008-11-30
> **johnonfire said:**
> I ran apt-get update and install devede and it tells me I have the latest version of DeVeDe, but my version doesn't have the same options as yours.  Most of the options shown in your images are there but just located elsewhere.  However when I fill a disk with more than 100% of a single layer disc, there is no Disk Usage option to adjust compression.  So, I can't put anything longer than 2 hours on my disks.  Any advice?

I'm running Hardy-gnome and DeVeDe version 3.6-0.0

I have DeVeDe 3.11. The older version is in the repos; but check out [http://www.getdeb.net/app/DeVeDe](http://www.getdeb.net/app/DeVeDe) for the newest version in a deb package. 

The deal with putting more than 2 hours is that it will automatically adjust (when you hit the adjust button) video bitrate settings to fit that amount of video. Of course, with 4 hours there is virtually no visible change - but I imagine if you tried to cram a lot of video it would look terrible, i.e., more than 5 hours. 

So just install the up-to-date deb from the website, and good luck!

---

### Post by pyromanic123boom on 2008-11-30
> **sarc said:**
> I'd like to ask what are Devede's best advanced settings to make a best quality DVD from a miniDV digital recording?

I have found that capturing from Kino as raw DV and making a DVD with Devede gives good picture quality (much better than on-the-fly conversion to AVI or mpg from Kino for example), but I get jagged motion at times. I need to pick the right interlacing and bitrate, but I have no idea of linear, belnd, FFMpeg deinterlace... and what bitrate to use?

Any advice on best advanced settings is appreciated!


Ok, I did some searching around, and here's what it looks like you should do.
Once you capture as a DV file, load it into Avidemux (repos). Then select some auto-settings on the left-

**Video**
MPEG-4 ASP (XviD4)

**Audio**
MP3 Lame 

Then click save, type in the file name and remember to put .avi afterwards, it isn't automatic with the file extension! There are many more settings in Avidemux - basic video editing and filters. Good luck.

---

### Post by sarc on 2008-11-30
Thanks I'll try it

---

### Post by flight23 on 2008-12-07
.

---

### Post by pyromanic123boom on 2008-12-12
I have now created a new, complete, more detailed guide for devede. 
forum link: [http://ubuntuforums.org/showthread.php?t=1009684&highlight=devede+complete](http://ubuntuforums.org/showthread.php?t=1009684&highlight=devede+complete)

original site link: [http://pyromanic.publichost.de/devede_guide/](http://pyromanic.publichost.de/devede_guide/)

---

### Post by sarc on 2008-12-31
I get an error message opening my .dv file from avidemux (2.4.3): culd not open the file.  Seems like avidemux is not compatible with the DV format... any ideas?

---

