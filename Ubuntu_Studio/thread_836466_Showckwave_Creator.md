---
title: "Showckwave Creator"
date: 2008-06-21
forum: Ubuntu Studio
---

### Post by Affrikka on 2008-06-21
My family is creating a website for the high school band, and we need a program that can create SWF files so we can put videos/powerpoints etc on our website.

Where can I find a program that does this?


thanks,

-Mathieu

---

### Post by Affrikka on 2008-06-22
hello? anyone?

---

### Post by mcduck on 2008-06-23
I take it that you are loking for Flash creator (for .swf files) and not Shockwave creator (for .dcr files).

Even though Flash is often calles "Shockwave Flash" it definitely is not shockwave, and the two are not the same thing.

Adobe does not offer a Shockwave player for Linux, and there isn't any open source alternatives either. However the player runs ok under Wine, if you ever _really_ need it.As far as the content ccreation for Shockwave goes, there is basically only one program available, Director, and as you probably guessed, it's not for Linux.

For Flash, you can get the player/plugin from Adobe, but once again there is no Linux version of the Flash program itself. You can get Flash running with Wine if you want.

(Some years ago Flash was purely for simple vector graphics, while Shockwave handled bitmap graphics and video as well. Shockwave was mostly used for multimedia CD-roms and such, as internet connection speeds were too slow for such content. Today most of Shocwave's features have been copied into Flash, and Shockwave itself is rarely used, apart from some online games).

---

### Post by leonsmith on 2008-06-24
You can use recordmydesktop and xvidcap to do what you want. If you use recordmydesktop you will need to convert the file it produces to either a .swf or .flv file using ffmpeg. Google these and find plenty of docs and examples.

I have been using xvidcap because I can record a portion of the screen rather than having to select a window and it can produce .swf and .flv files without an external converter. 

Unfortunately, like every time I upgrade Ubuntu it breaks something, this time Hardy Heron broke xvidcap and it just doesn't work any more. Even grabbing the latest copy from source and rebuilding it, it runs a little bit then dies. Heron broke my ability to record audio on my other computer altogether. So now after making promises to my client I cannot do what I promised and will probably lose them as a client. My advice: never upgrade a working version of Ubuntu or switch to Windows.

---

### Post by Creative2 on 2008-06-24
fuoco tools can convert into swf 
if you prefer just take its functions

ffmpeg  -i INPUT.any -r 30 -s 320x240 -ar 44100 -b 500k  -ab 128k -y OUTPUT.swf  


NB you have to install ffmpeg after you have added medibuntu repository....
(google--->medibuntu---->how to repository)

---

### Post by pcjunkie on 2008-06-25
VLC media player, avilable on synaptic can encode into FLV and I think SWF is possible.

---

### Post by jethro10 on 2008-07-02
Also for very simple ones, you can create a presentation in Open Office Presentation and export it as a flash movie.
J

---

