---
title: "Make a script to easily convert to image sequence?"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by WACOMalt on 2009-11-02
Hey, I frequently have to convert video files to image sequences to load them into my FX package of choice. I am still fairly new to linux and, although I know the command to do this, I want to know if it's possible to make a script where I could drag the video file onto the icon and it would make a folder with the name of the clip, and in there would be all the frames, named the same as the video file was.

The command I have been using is:

ffmpeg -i video_file directory/filename.%04d.png

Even better would be if you drag the file onto the icon, and a window pops up asking how much frame padding in the file name, and maybe what format to output to.

Can someone show me how this would be accomplished? or write it for me? (I'd rather write it myself as I need to learn)

---

### Post by rylleman on 2009-11-02
Here's a nautilus script that does what you want.
Place it in your nautilus script folder and make it executable "chmod +x convert-movie-to-png-seq".
To use it select the movie file you want to convert, right click and select the script from the menu>scripts.
Image sequence is created in a new folder named as the original movie file name without the extension.

The frame padding is hard set to 04 now, I didn't spend to much time trying to get that part to work. I think you need to do some sed line to get the d in there.
[conv_movie_to_png-seq]("http://www.rylanderanimation.se/resources/conv_movie_to_png-seq")

---

### Post by WACOMalt on 2009-11-02
wow, thanks so much!

Now, this is great for my home computer, but likely at work I wont have enough access to add this to nautilus. Is there a way to make this work in launcher form?

When I tried the ffmpeg -i video_file directory/filename.%04d.png command in a launcher, it *half* worked. It seemed to dislike the %04d part. It would just spit out a single file called scene.04d.png.  If I can get it to accept the %04d (or pass frame padding a different way to ffmpeg) then I would be able to make this into a portable launcher (that I could easily use at work)

thanks! I'll be using this at home in the least.

oh, and being somewhat new to nautilus scripts, where is the nautilus script folder? and will a reboot be needed for the script to show up?

---

### Post by rylleman on 2009-11-02
Your nautilus script folder is in a hidden .gnome2-folder in your home-folder. Hit ctrl+H to see hidden folders.
(When you got script installed you can right click in nautilus and select scripts>open script folder, but for this first script you have to go through ~/.gnome2/nautilus-scripts.)
Shouldn't be necessary to reboot.
And for your work, if you got normal user rights with your home folder you should be allowed to add the script there as well.

Strange that you can't get it to work, the %04d is the way ffmpeg defines numbered sequences. It works here when I do some testing.

---

### Post by WACOMalt on 2009-11-02
Well it's not so much that it doesn't work. It just doesnt work in launcher form. At least when I run it as "application in terminal"

in the terminal, inputting that code for my file works perfect.

Anyways, thanks so much again, and I'll be adding this at work. They use CentOS though, is there anything different there that you know of?

---

### Post by WACOMalt on 2009-11-03
Cool, I just tested it at work and home, and both worked perfect!

Now, for my purposes, I would still prefer a launcher that did the work. So I can drag and drop to an icon. And it would send the sequences to a folder inside the source file's folder.

If only I could get a launcher with a % symbol in it to work properly... I'll see what I can do.

---

