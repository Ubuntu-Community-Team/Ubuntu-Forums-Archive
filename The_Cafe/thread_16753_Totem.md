---
title: "Totem ?"
date: 2005-02-23
forum: The Cafe
---

### Post by ThePainter on 2005-02-23
Hi,
Apparently totem is added to UBUNTU because it is small and keeps the distro to one CD but does anyone actually use it and how.
Ive installed all the plugins and dvd libs and ffmpeg etc.just about everything listed under gstreamer in synaptic. Ive done all the stuff from the "ubuntuguide" website like creating a dvd link etc.
It plays avi's but they are jumpy and the audio runs out of sync on a few of them and when I try to open a dvd it just errors so I tried to open the vob's as mpg's but it just goes into an infinite loop trying to open them one after another from the playlist.
Everytime I get it to close and reopen it tries to open the last file on startup and errors again.
I cant even uninstall it without uninstalling the UBUNTU desktop.
I was trying to make UBUNTU usable with the default apps but this is a no go.

I give in and install VLC and it plays everything perfectly.

So I was wondering if anyone has actually got Totem to work and if so how ?

---

### Post by tim1 on 2005-02-23
Install totem-xine, this will remove totem-gstreamer, but that's ok. That plays nearly everything. However gstreamer progresses nicely these days and will be a good alternative to mplayer/xine/vlc soon.

greets, tim

---

### Post by adbak on 2005-02-23
I don't use Totem.  Instead I use MPlayer and GXine.  GXine is my favorite, but sometimes wmv files don't play with sound, so I'll rely on MPlayer to do that, and vice versa.  I prefer GXine over MPlayer because I can set the video to full screen and for some reason I can't do that with MPlayer.

---

### Post by poofyhairguy on 2005-02-23
[QUOTE=adbak]I don't use Totem.  Instead I use MPlayer and GXine.  GXine is my favorite, but sometimes wmv files don't play with sound, so I'll rely on MPlayer to do that, and vice versa.  I prefer GXine over MPlayer because I can set the video to full screen and for some reason I can't do that with MPlayer.[/QUOTE]


I second this. Totem is not very good. Gxine kicks for some people, and Mplayer hits for the others.....

---

### Post by darkoptix on 2005-02-23
I use MPlayer because it... works... With totem, it would freeze when i tried to play dvds, didn't support much out of the box. MPlayer works great.
I haven't had much time to spend with xine, so I won't commant about that. 
However totem should be dropped and brought in with a better video player... whatever it may be.

---

### Post by adbak on 2005-02-23
[QUOTE=darkoptix]I use MPlayer because it... works... With totem, it would freeze when i tried to play dvds, didn't support much out of the box. MPlayer works great.
I haven't had much time to spend with xine, so I won't commant about that. 
However totem should be dropped and brought in with a better video player... whatever it may be.[/QUOTE]
 The problem with dropping Totem is that the devs have to pick a multimedia player that infringes or possibly infringes on NO copyrights whatsoever (i.e. no 3rd party or un-free codecs).  That's why you can't play MP3s or DVDs ootb.

---

### Post by poofyhairguy on 2005-02-23
[QUOTE=adbak]The problem with dropping Totem is that the devs have to pick a multimedia player that infringes or possibly infringes on NO copyrights whatsoever (i.e. no 3rd party or un-free codecs).  That's why you can't play MP3s or DVDs ootb.[/QUOTE]

I think eventually what will happen is that an unofficial "second disk" could be created that would have the needed packages (such as media codecs, java, acroread, ect.) that could make Ubuntu functional at the level that many desktop users demand. 

I'm trying to learn how to do this myself.

---

### Post by Ste on 2005-02-24
I've started to use vlc over everything, except DVD's I use xine or mplayer for that.
Never really rated totem it would never play much for me. I can understand why the devs use it tho.

[QUOTE=POOFYHAIRGUY]I think eventually what will happen is that an unofficial "second disk" could be created that would have the needed packages (such as media codecs, java, acroread, ect.) that could make Ubuntu functional at the level that many desktop users demand.

I'm trying to learn how to do this myself.[/quote]

Keep us informed of your progress ;)

---

### Post by Kakalto on 2005-02-24
Does totem have an extension or something to add an equalizer? (Or does VLC?)

---

### Post by ThePainter on 2005-02-24
Hi,
STE: Why dont you use VLC for DVD's ? I use it and it works great.

Last week I tried to install MPlayer following the instructions in this forum but theres loads to install with it and I started to hit dependency issues during the installs where somethings needed to be older versions to what I had installed and it wouldnt install them so I took back out everything I had installed and installed VLC instead and with one fiel to install I could play everything so I was wondering whats the point of all that work when VLC is simple and works.
The only thing that could be added to VLC is a m3u playlist saver. It plays m3u's but you have to create them with another program. I found a good text based one called "fapg" that works great you just type these four letters then the playlist format and then where you want the playlist and where the audio files are and bang its there.
But at the moment Im just using the default RythmBox music player because It minimises to the sys tray so it doesnt get in the way.

Im in the process of installing the Hoary beta as we speak so Ill just have to wait and see what works with that. Ill report back if or when my system is running again cos Ive heard a few horror stories about non-boot hoary's, but if no one tries betas the advance of Linux will stop so here we go  :neutral:

---

### Post by ThePainter on 2005-02-24
I had some asx files from XP that linked to internet radio and I just opened them in a text editor and took out the URL and added it to Rythmbox manually.
If you still have XP in Im sure I found a way to open them in WMP and resave them as M3u's, it gives you a choice of save as formats in the save as extension drop down.
If not then try googling for a m3u creator, thats how I found the text based one I mensioned in my last post.
Cant help with the equaliser.

---

### Post by Ste on 2005-02-24
[QUOTE=ThePainter]Hi,
STE: Why dont you use VLC for DVD's ? I use it and it works great.[/QUOTE]

It didn't play one of them before, seems to work now tho.
Only thing about vlc is the volume seems to be a little low, I have adjusted it up fully but still not as loud as mplayer or xine  :???: [edit] it was because the volume was down in mplayer  :-& [/edit]

---

### Post by ThePainter on 2005-02-24
Hi,
I have one DVD that if I try to play it from the menu vlc just closes but all my others work OK.
I just open it as a file in VLC and select all the main .VOB's and it just plays them from its playlist.
I probably feel comfortable with VLC cos I used it a lot in XP because it will play partially downloaded movies from EMULE and Kazaa. where as WMP just scratches its head at them.

---

