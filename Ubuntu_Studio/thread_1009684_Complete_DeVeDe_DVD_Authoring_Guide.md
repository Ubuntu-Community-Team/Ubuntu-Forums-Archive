---
title: "Complete: DeVeDe DVD Authoring Guide"
date: 2008-12-12
forum: Ubuntu Studio
---

### Post by pyromanic123boom on 2008-12-12
DeVeDe 
authoring guide


**Introduction:** I usually skip the preface of the book, after the first few sentences. So I will make it short. DeVeDe is a linux dvd authoring program. In my opinion, it is one of the best that exists for linux. I believe it does run under windows as well, so it is a great alternative in that respect. I will show you how DeVeDe works, in addition to some of the tricks that everyone picks up after they've used a program for a good length of time. 

Requirements:
-Download DeVeDe in the repositories for the latest version. This is rudimentary- open the terminal (apps-->acessories-->terminal) and type in sudo apt-get install devede
-Have some video files you'd like to make into a DVD. Either a movie, or about 2-3 hours of video.
-Possibly GIMP (repos) or other image-editor to make some better menus.
-Recordable media (dvds, cds)


[B][U]Guide:
Part One[/U][/B]
When you run DeVeDe, it will ask you which type of disc you'd like to create. We will be making a standard DVD, although most of the same things apply to any other type. 
[IMG]http://pyromanic.publichost.de/devede_guide/img1.png[/IMG]

Now you are presented with a screen titled "unsaved disc structure".
[IMG]http://pyromanic.publichost.de/devede_guide/img2.png[/IMG]

First thing to do is save the project as a devede file (file-->save). Save as the name of the dvd. 
Now the next thing to do is set your region. This means either NTSC or PAL. NTSC, or Region1, is the standard in North America. PAL, or Region2 is for Europe. These are the little globes with the number in it on the back of a dvd box. So depending on where you live, or your dvd player, choose your region. 

Mine would be NTSC. Now let's go to adding the movie or video files to the DVD structure. Before we begin, however, I need to say some things about a DVD. Manufactuers will ship a DVD with about 2 or 2.5 hours on it. I think this is why most movies now aren't too long. After that, the quality may start to become *slightly* noticable. Not very, though. So based on that, I made a DVD with Spiderman 1, 2, and 3 all on the same disc. That's about ~5.5 hours of video. When the fighting started up, you could see a little pixelated parts. But if you're willing to sacrifice quality for quantity, then this is you. When you're sending out a family dvd to the relatives for Christmas, you want to have it perfect. Then your limit is about 2.5 hours. 
Rename your first Title of the DVD. This is what will appear in the menu. (note that you can have a menu title, so you may want something like Episode #1, or Play Movie as the title name). Click Properties on the left side to rename the title. You can also set what will happen after it is played (if it is a list of episodes, you might not want to go back to the menu each time). 
[IMG]http://pyromanic.publichost.de/devede_guide/img4.png[/IMG]

Now on the right side, with the first title selected, you will want to add a video/movie file. Click "Add". I recommend not changing the audio track, but you will have to know your own video file. Then add any subtitles. In the case you're using an axxo release or something similar, subtitles are readily available on the internet. Just try them out before - rename them to the same title as the video, and Movie Player will load them automatically. (windows media player, too). When you add subtitles, speficy the language. Because they aren't burned in, you turn them on by pressing "subtitles" on your remote. Then it will say something like "1: ENGLISH", according to the track number and language code. You can also put subtitles in the upper screen, don't know why you would want to.
[IMG]http://pyromanic.publichost.de/devede_guide/img5.png[/IMG]

[IMG]http://pyromanic.publichost.de/devede_guide/img6.png[/IMG]

Here is an example of mine, after everything is adjusted.
[IMG]http://pyromanic.publichost.de/devede_guide/img7.png[/IMG]

Typically, I don't really change the automatic "advanced" settings, although I could if I needed to.
So click OK and then add any more titles if you want. (repeating the steps for the first title).
[IMG]http://pyromanic.publichost.de/devede_guide/img8.png[/IMG]>

If you added another movie, or if the % bar is over 99%, hit "Adjust Disc Usage". This actually automatically changes video bitrate settings, etc., to fit it onto a DVD. 

[IMG]http://pyromanic.publichost.de/devede_guide/img10.png[/IMG]

---

### Post by pyromanic123boom on 2008-12-12
**_Part Two_**

Let's customize our menu. Now, DeVeDe doesn't offer great menus. But, it's pretty enough for me, and if you know a few tricks, you can make it look terrific. If you don't want a menu, don't worry about it. Just go into "Menu Options" and set "Disc Startup options" to "Jump to first title at startup". However, a menu doesn't hurt.
Click on Menu Options, and let's get started with it. 
[IMG]http://pyromanic.publichost.de/devede_guide/img11.png[/IMG]

This is what you start with. I'll divide the menu into parts.
**Menu Title**
     Text: This is what will be displayed at the top of the menu. change text color too.
     Font: what the title text will be written in. face and size changable, along with shadow.

**Menu background (only PNG**)
     Change the background if you'd like. Must a png image; try GIMP or other image editor. The default is a disc.

**Menu music**
     Change music to a MP3 or no sound. Generally a short 2-3 minute clip, use youtube and audacity for soundtrack.

**Menu position**
H..................V
Top................Left
Middle.............Center
Bottom.............Right

Choose position. It is basic: top left, top center, top right, then middle and bottom. Easy.

**Menu Font and colors**
Font: the text face for the titles
Color for unselected titles: change color (if you have 2 titles, the one without the cursor is going to be this color).
Color for selected title: the title with that is selected with the cursor will be this color.
Color for shadows: a slight darkening effect for the text. I don't really like this option, I leave it off.
Background color for titles: this makes a long box-area around the title. Nice if you make it light, but then you have to change the title text colors darker to offset it. Here is my finished settings, 
[IMG]http://pyromanic.publichost.de/devede_guide/img12.png[/IMG]

And the finished menu (preview menu)

[IMG]http://pyromanic.publichost.de/devede_guide/img13.png[/IMG]



Once you have completed your menu to perfection, then click OK and you'll go back to the original screen. Adjust disc usage again if necessary, check region, and make sure everything is correct. Now click on Foward.
[IMG]http://pyromanic.publichost.de/devede_guide/img14.png[/IMG]

Then you will be presented with this screen. Choose a destination folder, and type in a short name for the dvd. (You're almost finished!)
[IMG]http://pyromanic.publichost.de/devede_guide/img15.png[/IMG]

Now click on OK, and it will start to make the DVD. The name you typed in at the end will be the name of the burnable ISO. All temporary folders will be cleared out after it is done. My computer takes about 2.5 hours to make a 2-movie DVD. Once the ISO is finished, let's burn.

---

### Post by pyromanic123boom on 2008-12-12
**_Part Three_**
Load a DVD into your tray. Wait for it to mount, it will appear in the left-side of your folders. 
[IMG]http://pyromanic.publichost.de/devede_guide/img16.png[/IMG]

Now right-click on the iso, and then click Write to Disc.
[IMG]http://pyromanic.publichost.de/devede_guide/img17.png[/IMG]

Then all you have to do is hit Write, and the DVD will be done in a few minutes!
[IMG]http://pyromanic.publichost.de/devede_guide/img18.png[/IMG]



Have fun! Please don't make DVDs from the internet to sell; share and impress your friends instead. 
Post any errors, issues, problems, etc., here. I will be glad to respond, and answer any questions.
*pyromanic123boom*

**The original html guide exists at [http://pyromanic.publichost.de/devede_guide/](http://pyromanic.publichost.de/devede_guide/). I have also sent it to the webmaster/programmer of devede, [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html). **

---

### Post by Gotit on 2008-12-20
Thanks for the great guide!
Can you tell us what version of DeVeDe you are using?  I have v3.6 from the repos and it looks like you have some additional options that would be useful.

Also, is there a way to change the color and/or font of the subtitles? I have made my own subtitle file using [[COLOR="Blue"]_jubler_[/COLOR]]("http://www.jubler.org/") and tried saving as .ssa, .srt and .sub.  I made my subtitles yellow with a black border and some "fancy fonts". But they all display as white with a black border (Sans ? font) when added them to my video with DeVeDe.

And yet another question:), do you have a recommendation for a good linux slide-show application?

---

### Post by Jackie999 on 2008-12-21
I've always booted back into XP to use convertxtodvd but then tried using it in Wine and realize it doesn't include a menu/chapters. I saw your guide and thought I'd give devede a go. The only problem I have, the first one I tried it told me it was something like 110% so I clicked the "adjust disk usage". When the conversion was complete - it was 2.5 gig. Then I tried another avi - it told me 102% - this time I did NOT click "adjust disk usage" and it completed at 2 gig. I'm thinking the 'disk usage' bar doesn't work? I don't know for sure, but I think convertxtodvd would have converted to almost fill the DVD - does anyone know if devede, since it converts to a smaller file, if quality is sacraficed on the final DVD?
Also, I don't pay much attention to whether a DVD is PAL or NTSC when I download it, yet devede asks me - what do I do if I don't know, and don't care - in order to get best/fastest conversion?
Thank you for your excellent guide.

---

### Post by pyromanic123boom on 2008-12-24
> **Gotit said:**
> Thanks for the great guide!
Can you tell us what version of DeVeDe you are using?  I have v3.6 from the repos and it looks like you have some additional options that would be useful.

Also, is there a way to change the color and/or font of the subtitles? I have made my own subtitle file using [[COLOR="Blue"]_jubler_[/COLOR]]("http://www.jubler.org/") and tried saving as .ssa, .srt and .sub.  I made my subtitles yellow with a black border and some "fancy fonts". But they all display as white with a black border (Sans ? font) when added them to my video with DeVeDe.

And yet another question:), do you have a recommendation for a good linux slide-show application?

You're welcome, and thanks. I failed to mention the important fact that the repos have an older version- 3.6, in your case. The newest version is 3.11b, available from getdeb: [http://www.getdeb.net/app/DeVeDe](http://www.getdeb.net/app/DeVeDe), for Hardy and Intrepid. 

As far as I know, the only thing you can do with subtitles is place them in the upper area of the screen. It doesn't look like you can do anything else with them. I don't add any black borders, and they just come up as white text on my movies. Maybe you can use Kino (video editor) to mux in some fancier subtitles, but I don't know very much about it.

Oh- for the slideshow, I have a few things. First is SuperShow, from the same guy who wrote DeVeDe- [http://www.rastersoft.com/programas/supershow.html](http://www.rastersoft.com/programas/supershow.html), and Second, dvd-slideshow: [http://dvd-slideshow.sourceforge.net/wiki/Main_Page](http://dvd-slideshow.sourceforge.net/wiki/Main_Page). I am not familiar with these, so I can't really tell you much abou them.

You could always try ManDVD, which is good for slideshows. But it is generally unstable and sometimes the dvds don't play.

---

### Post by pyromanic123boom on 2008-12-24
> **Jackie999 said:**
> I've always booted back into XP to use convertxtodvd but then tried using it in Wine and realize it doesn't include a menu/chapters. I saw your guide and thought I'd give devede a go. The only problem I have, the first one I tried it told me it was something like 110% so I clicked the "adjust disk usage". When the conversion was complete - it was 2.5 gig. Then I tried another avi - it told me 102% - this time I did NOT click "adjust disk usage" and it completed at 2 gig. I'm thinking the 'disk usage' bar doesn't work? I don't know for sure, but I think convertxtodvd would have converted to almost fill the DVD - does anyone know if devede, since it converts to a smaller file, if quality is sacraficed on the final DVD?
Also, I don't pay much attention to whether a DVD is PAL or NTSC when I download it, yet devede asks me - what do I do if I don't know, and don't care - in order to get best/fastest conversion?
Thank you for your excellent guide.

Ok, first the Adjust disc usage. I believe that DeVeDe has max quality settings- 5001 kbps for video, 224 kbps for audio. This is what it starts at, you can increase/decrease it in advanced settings. Past this point, you won't really hear or see any difference. So why have the bitrates so high? If you add another movie, it will automatically adjust the settings to the best possible, in order to fit. So the adjust disc usage just automatically adjusts bitrate settings to their maximum. Sure, some quality will be lost if you add too much video, like 5 hours. But I generally add about 3 to 3.5 hours on a single dvd. 

NTSC- north america
PAL- europe

Depending on where you live, you should go with that one. Neither one is faster, it's just screen resolution. Input doesn't matter, it's just output. If I burned PAL, nothing would play on my dvd player. But I can use a AVI file that came from a PAL dvd, as long as I change it to NTSC. I know it's a little confusing, so if it doesn't make sense, post it

---

### Post by Gotit on 2008-12-25
> **Gotit said:**
> 
Also, is there a way to change the color and/or font of the subtitles? 
Well I guess this is my X-mas present to anyone else who cares, but I did find a way to change the font.  Since DeVeDe uses a default font and spumux to add the subtitles into the movie, you can "trick" DeVeDe/spumux into using a different font by copying a truetype font into the ~/.spumux folder and renaming it to devedesans.ttf.  A more detailed procedure follows:

Go to your truetype fonts folder at:
```
/usr/share/fonts/truetype
```
Open the folder where the font you want to use resides (it must be a truetype (.ttf) font).

Highlight and copy the font

Go to:
```
/home/*username*/.spumux
```
In this folder you should see a font called:
> devedesans.ttf
this is the font DeVeDe uses for subtitles.
Paste the font you copied into this folder (note, this is a hidden folder so if you are using the file browser you may have to hit ctrl+H to see it)

Rename the existing devedesans.ttf to something else like orig-devedesans.ttf

Rename the font you pasted into the ~/.spumux folder to devedesans.ttf

Now when you add subtitles with DeVeDe it will call it's default font, but the font will actually be the one you renamed to devedesans.ttf.

---

### Post by tubunu on 2008-12-26
One other question, is it possible to add subtitles to the disc but make them as an option? If one doesn't want the subtitles they could be switched off? Thanks.

---

### Post by Gotit on 2008-12-26
> **tubunu said:**
> One other question, is it possible to add subtitles to the disc but make them as an option? If one doesn't want the subtitles they could be switched off? Thanks.

Yes, that's exactly what DeVeDe does.  DeVeDe adds a subtitle "track" it doesn't hard burn the text on the picture.

---

### Post by pyromanic123boom on 2008-12-26
> **Gotit said:**
> Yes, that's exactly what DeVeDe does.  DeVeDe adds a subtitle "track" it doesn't hard burn the text on the picture.

That's the main reason I use DeVeDe. It makes it more like a commercial dvd, slightly.

And thanks for the ttf trick, I will try using it later on!

---

### Post by tubunu on 2008-12-30
Oh, I didn't know that. Thank you very much for the info!

---

### Post by areseapea on 2009-01-10
I'm attempting to use devede to turn the .ts files from my PVR into DVDs.  I've used tovid to re-encode them to mpg files, and avidemux to chop out unwanted stuff.  The files play OK in Movie Player.

I'm using the 64bit version of devede direct from Rastersoft, version 3.11.

When I've set everything up and click Forward and pick the location, it creates the menu, and gets to the stage where it says "Converting files from title 1".  Then it stops.  There's no processor usage, no movement, no sign of life!

Is this a problem anyone else has seen?  Does anyone have any suggestions?

Thanks

---

### Post by silverwolf636 on 2009-02-14
Would anyone know why when I click on the iso to "write to disc", when the dvd is finished, I have no sound?

SOLVED: What an idiot!!! Never mind this question... My home dvd player is set up for surround sound; if it is not turned on, there is no sound. In other words, I was not turning on my surround sound when I test my burnt dvd's. I don't know how many dvd's I now have of misc backed up movies... DUH!!!

---

### Post by jluda on 2009-02-14
I have a question when i create it it divides it into 4 files movie_01_01.mpg, movie_menu2_0.mpg, movie.xml, movie_menu_0.xml. do i burn all of the files to the disk or which ones do i need to burn? i have been trying to make this work for awhile am confused please help.

---

### Post by zisun666 on 2009-02-17
Good job, but devede written by python, is slower?

---

### Post by gregconquest on 2009-02-19
> **jluda said:**
> I have a question when i create it it divides it into 4 files movie_01_01.mpg, movie_menu2_0.mpg, movie.xml, movie_menu_0.xml. do i burn all of the files to the disk or which ones do i need to burn? i have been trying to make this work for awhile am confused please help.

I don't know the direct answer to your question, but if you choose to make an .iso instead of "disc structure" or whatever it is, then you won't have to worry about this. When finished, you have one file named whatevernameyouchose.iso. That file is to be burned AS the DVD (usually write/burn IMAGE to disc). Don't just burn the file itself ONTO a DVD. Search for:
image dvd iso burn OR write 
for more information.

You can also save that file on a hard drive and burn more DVD's quickly anytime.

---

### Post by MeTylerDurden on 2009-02-19
I understand how to drag and drop subtitles into devede in adavanced options what I don't get is the 'encoding' there are 30 or more different choices> what would you do when you drop in a plain text document that says subtitles.. that is supplied with the avi. file

---

### Post by lupin492 on 2009-06-13
Hello!  I'd been using Devede for a time without problems, but now it tells me to "check if there is enough disk space".  Starting Devede from the console, I see it is using the /var/tmp/ directory for temps, wich is no good news in my case, cause my /var partition is just 1.5GB (I didn't plan to put big files there).
I tried changing this setting in de ~/.devede file, but it is overwritten by Devede.
Does anybody know if (and where) can I change this?  And why did it started to happen recently ?  My Devede version is 3.6 from the repos, and I'm running Hardy.
Anybody who answers: THANKS in advance !  :-)

---

### Post by cotcot on 2009-06-14
I do not have this problem (I have tested it after reading your question). Devede accepts the new path when it change it in .devede. The file permission is -rw-r--r-- . Maybe you could try changing the file permissions so that it cannot be overwritten.

---

### Post by lupin492 on 2009-06-21
> **cotcot said:**
> I do not have this problem (I have tested it after reading your question). Devede accepts the new path when it change it in .devede. The file permission is -rw-r--r-- . Maybe you could try changing the file permissions so that it cannot be overwritten.

Thanks, Cotcot.  After reading your post I realised I was trying to use /tmp as temporary location, so there arised a permissions issue.  Now I reconfigured it to be /home/ and it works ok.
Best regards!

---

### Post by thefunks on 2009-06-26
Can this program transcode video files like xvid and divx into files that will be recognized by a standard DVD player? In other words, do I need to transcode the xvid and divx into .VOB before I use this program or will it do the transcoding for me automatically, like Nero does?

Another way of asking this question - if I add xvid or divx video to my project will the resulting burned disc be a data disc or dvd disc?

Thanks.

---

### Post by lupin492 on 2009-06-30
[QUOTE=thefunks;7521178]Can this program transcode video files like xvid and divx into files that will be recognized by a standard DVD player? 

Yes, it will.  If you start choosing DVD disc, it will default to create a DVD image directly burnable and compatible with any standard DVD player.  The only suggestion I think of at this moment is: in the window where you "add files", there is a "bitrate" setting.  It defaults to 5001Kbps, but you can lower it if the final disc image results bigger than your disc capacity.  Furthermore, explore the "advanced options" tab in the same window.
Good luck!

PS: this might be useful: [http://www.majorsilence.com/node/64](http://www.majorsilence.com/node/64)

---

### Post by eladamri on 2009-11-18
I am having a problem with DeVeDe that I haven't been able to find a solution to on the forums. If I can't find one here I'll make a new thread about it.

I have successfully created my DVD video iso and burned it to a DVD. It plays the videos fine on my computer through Totem and VLC. However, when played in a DVD player the image is too large for the screen. This happens both in the menu and in each video such that you are losing about 10% of the picture on all four edges of the screen and you can only see the center.

I would think that I may have chosen the wrong aspect ratio or something, but the menu is cut off as well and the menu has no options to change the aspect ratio.

Please advise.

---

### Post by pyromanic123boom on 2010-01-05
> **eladamri said:**
> I am having a problem with DeVeDe that I haven't been able to find a solution to on the forums. If I can't find one here I'll make a new thread about it.

I have successfully created my DVD video iso and burned it to a DVD. It plays the videos fine on my computer through Totem and VLC. However, when played in a DVD player the image is too large for the screen. This happens both in the menu and in each video such that you are losing about 10% of the picture on all four edges of the screen and you can only see the center.

I would think that I may have chosen the wrong aspect ratio or something, but the menu is cut off as well and the menu has no options to change the aspect ratio.

Please advise.

I have never experienced this issue. Try this:  when you add a new title, go into the "advanced" section, and make sure "add black bars 16:9" is selected, not the other one which stretches the image (4:3). Maybe this has something to do with it. Also, once it creates an ISO image, you can open it with VLC instead of testing it with a dvd. Then if it works right you burn the dvd and you're good.

---

### Post by mrowl on 2010-01-22
> **areseapea said:**
> I'm attempting to use devede to turn the .ts files from my PVR into DVDs.  I've used tovid to re-encode them to mpg files, and avidemux to chop out unwanted stuff.  The files play OK in Movie Player.

I'm using the 64bit version of devede direct from Rastersoft, version 3.11.

When I've set everything up and click Forward and pick the location, it creates the menu, and gets to the stage where it says "Converting files from title 1".  Then it stops.  There's no processor usage, no movement, no sign of life!

Is this a problem anyone else has seen?  Does anyone have any suggestions?

Thanks

I tried using version devede_3.11-0~getdeb1_all.deb,
devede_3.14.0-0_getdeb1_all.deb,
devede_3.15.2-0~rastersoft1_all.deb

All 32bit versions on Hardy and had the result. When I reverted to 3.6 from the repos everything works fine. The only drawback is the menu options are very limited in this version.

Does anyone have any suggestions how to get the newer version to work?

---

### Post by mrowl on 2010-01-24
> **mrowl said:**
> I tried using version devede_3.11-0~getdeb1_all.deb,
devede_3.14.0-0_getdeb1_all.deb,
devede_3.15.2-0~rastersoft1_all.deb

All 32bit versions on Hardy and had the result. When I reverted to 3.6 from the repos everything works fine. The only drawback is the menu options are very limited in this version.

Does anyone have any suggestions how to get the newer version to work?

I meant to say I had the _same_ reasult. No activity.

Sorry

mrowl

---

### Post by stoppage on 2010-05-11
This app only works for me when I deselect "add a menu" option, otherwise it comes up with Memory fault which is rubbish. Without menu it's fine. Anybody any ideas?

---

