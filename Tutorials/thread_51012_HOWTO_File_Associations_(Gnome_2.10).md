---
title: "HOWTO: File Associations (Gnome 2.10)"
date: 2005-07-22
forum: Tutorials
---

### Post by FLeiXiuS on 2005-07-22
Yeah so I've grown tired of yelling at gnome for opening totem each and every time.  Even after forcefully uninstalling totem video files / mp3's still didn't open in the correct programs.  So I finally took action...

The myth of gnome 2.10 is that the "Open With" program will automatically do file associations for you.  Well this is a complete LIE.  There's a lot of manipulatations needed to get the currect applications opening with a specified file type.  Lets jump in!!


[ Gnome 2.10 uses a couple of ways to store file associations. ]
**1.)** /usr/share/applications/defaults.list
-- This method is perhaps one of the most important.  Following this comes..

**2.)** /usr/share/applications/mimeinfo.cache
-- This is the cache of the current mime types.  Updating the mime database doesn't work to well so of course you have to manually edit this as well.

**3.)** ~/.local/share/applications/
-- The dreaded "Open With"

**4.)** ~/.gnome/share/apps/
-- Same as the above

Enough of the explaining, lets get into the goodies.  First we will have to of course clear our "Open With" settings.  If we don't they will come back and haunt us forever.  Trust me on this one.  I found out after 20 minutes of staring..thinking...WTF?


[SIZE=3]**Step 1:**[/SIZE]
```

rm -R ~/.local/share/applications/*
rm -R ~/.gnome/share/apps/*

```
*[COLOR=Red]Note: Don't worry if it reads an error, your erasing them anyways.  :-P[/COLOR]*


[SIZE=3]**Step 2:**[/SIZE]
So now, lets create a situation...
Ok so I double-click on a mp3 and of course lovely totem opens up.  ROAR!  I would rather have it open in my lovely Gtk-2 beep-media-player.  Lets start out by editing the mime-types.  
```

$ sudo gedit /usr/share/applications/defaults.list

```

Looks awesome, doesn't it!  :-P  You'll notice browsing through the file that you will see...
```

audio/x-mp3=totem.desktop
audio/x-wav=totem.desktop

```
Well now wait, we don't want totem.  We want BMP!!!  All we need now is to figure out what bmp's desktop file is named.  Of course, I'm super smart and took a guess it was 'bmp.desktop' little did I know that it was correct.  If we didn't happen to know this you could always 'ls /usr/share/applications' and search for it there. 

Time to edit those lines above and remove totem.desktop. 
```

audio/x-mp3=bmp.desktop
audio/x-wav=bmp.desktop

```
Save and exit!  Great, 1 step closer to super sweet audio associations!  If you like you could also change some of the video mimes.  I hated totem so I've made changes to use xine instead.  So go back and make more changes if you please. 


[SIZE=3]**Step 3:**[/SIZE]
Now that we have the defaults edited, as I mentioned above "Open With" will destroy all.  Lets take our time to edit the exact mime-types above in the mimeinfo.cache file.

```

$ sudo gedit /usr/share/applications/mimeinfo.cache

```

Take a gander around (or use ctrl f :-P) and you'll see something like..
```

audio/x-mp3=totem.desktop;rhythmbox.desktop;.....
audio/wav=realplay.desktop....
audio/x-wav=realplay.desktop....

```
*[COLOR=Red]Note: You may not have realplay.destop, depends on your system.  We'll change these values anyways! Also, to the users who made more changes in step 2 please modify those correct values also.[/COLOR] *

Make the appropriate changes as I did below..
```

audio/x-mp3=bmp.desktop;
audio/wav=bmp.desktop;
audio/x-wav=bmp.desktop;

```
*[COLOR=Red]Note: You do need the semi-colon at the end of each line.  So don't forget to include it.  teehee![/COLOR] *

Save and exit and your good there!


[SIZE=3]**Step 4:**[/SIZE]
Final step, and yes it's easy :-).  All you have to do now is make your changes final.  I have yet to find another...simply just logout then back in to see the fantastic changes.

*[COLOR=Red]Note: I've tried 'update-mime-database' and 'update-desktop-datebase' and neither had ucceeded.  So please do your self a favor, just logout and then back in.  If you find an easier solution please notify me immediately.[/COLOR]*


Your possibilities are now endless.  I have also edited my video mime's to open xine rather then totem.  <3 Just read through the mime files and if you find something that looks interesting enough to change, do so and please your self.  Linux is all about customizing to your perfection.  

I hope this aids users who've already thrown 'hope' out the window.


EDIT:  Users who don't use Beep-Media-Player and use XMMS.  Change 'bmp.desktop' to 'XMMS.desktop'.

---

### Post by kori.mendocino on 2005-07-22
and can't you really do all that graphically in nautilus via **right click on file > preferences > 'open with' tab**? yes, sirre, you can...

but anyway, thumbs up for the howto

---

### Post by FLeiXiuS on 2005-07-22
Thats true also, but as I mentioned this method didn't always work for me.

---

### Post by FLeiXiuS on 2005-07-22
Thats true also, but as I mentioned this method didn't always work for me.

---

### Post by dabear on 2005-07-22
rm -R ~/.gnome/share/applications/* should be rm -R ~/.gnome/share/apps/*

---

### Post by FLeiXiuS on 2005-07-22
[QUOTE=dabear]rm -R ~/.gnome/share/applications/* should be rm -R ~/.gnome/share/apps/*[/QUOTE]

Woops, fixed.

---

### Post by Marrea on 2005-07-28
>    and can't you really do all that graphically in nautilus via **right click on file > preferences > 'open with' tab**? yes, sirre, you can... 

All I would like to do is have xine open rather than totem when I insert a DVD.  Is there an easy way to do this with nautilus similar to above?  It's easy enough to click on an mp3 file in your file list but what do you have to click on for a DVD in the drive?

I have so far tried editing a file called /etc/gnome.defaults.list and replaced all instances of totem with xine but it didn't stop totem opening up as the default.  I see from this thread that there is a different file, /usr/share/applications/defaults.list.  So it looks like I've been editing the wrong file?

(I've only recently started using Ubuntu and still finding my way around.)

---

### Post by Marrea on 2005-07-29
I've managed to sort this out.

I discovered that my /usr/share/applications/defaults.list was an exact copy of my /etc/gnome/defaults.list and all the totems in the former file had already been changed to xine.  This obviously happened when I made the changes to the latter file.   However, altering those files did not give me what I wanted:  xine opening as default on insertion of a DVD.

However, the problem was easily resolved via the GUI.   All I had to do was to go to **System > Preferences > Removable Drives and Media** and simply change totem to xine in the relevant box. 

Brilliant !    At _last_ xine opens when I insert a DVD.     :grin:  :grin:  :grin:

---

### Post by NeoChaosX on 2005-07-29
I wouldn't wipe out ~/.local/share/applications and it's contents completely if I were you. If you use Smeg for menu editing, any changes you make to the menu get wiped out by doing that.

---

### Post by Name on 2005-09-12
[QUOTE=Marrea]I've managed to sort this out.

I discovered that my /usr/share/applications/defaults.list was an exact copy of my /etc/gnome/defaults.list and all the totems in the former file had already been changed to xine.  This obviously happened when I made the changes to the latter file.   However, altering those files did not give me what I wanted:  xine opening as default on insertion of a DVD.

However, the problem was easily resolved via the GUI.   All I had to do was to go to **System > Preferences > Removable Drives and Media** and simply change totem to xine in the relevant box. 

Brilliant !    At _last_ xine opens when I insert a DVD.     :grin:  :grin:  :grin:[/QUOTE]

worked like a charm... now launching gmplayer

---

### Post by temporary11 on 2009-01-19
thanks for the HOW TO
I will try

---

### Post by dgermann on 2010-02-09
Hi--

I am using gnome 2.22.3 on Ubuntu 8.04.3. Is this thread where I need to look for this problem?

Symptoms:

1. When I go to open a .doc file attachment in evolution, it wants to use evince to open it, not OOo.

2. When I go to open an .odt file in Gnome's "Search for Files," it will not open it, or will open it in Kword but not OOo.

3. When I right click a file in nautilus, choose preferences and then open with, there are several instances of just about every application--text editor, OOo Word Processor, spreadsheet, you name it.

Or is there some other place I should be looking?

I also came across [this thread]("http://ubuntuforums.org/showthread.php?t=790250&highlight=file+association"), which seems to be pointing in the same direction as you are here.

Thanks!

---

### Post by Gonzalo_VC on 2011-10-02
Hi all. I don't think I got the point of some of you. I have my 10.04 (Gnome 2.3) Ubuntu opening ODT files with evince!!?? But I need Libreoffice to open them! (not the other way around).

The "open with" > "other application" > "remember association..." is not working. EVERY TIME evince opens them if I just click on the files :(

---

### Post by T.Ephraim on 2013-01-17
@FLeiXiuS: Thx a lot for the info! Helped me a lot, as I wanted to set the file assocs permanently for every user! 

GUI sucks in this case :)

Ciao
Ephraim

---

