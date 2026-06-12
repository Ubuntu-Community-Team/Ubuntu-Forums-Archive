---
title: "How can I set the default dvd player to VideoLan?"
date: 2007-01-07
forum: Ubuntu Customization Guide
---

### Post by ramasdf123 on 2007-01-07
How can i set the default dvd player to be VideoLan and not the movie player?

---

### Post by hanzomon4 on 2007-01-07
Right click on a video file and select properties. 
Then click on the "Open with" tab and select VLC.  
Repeat this for any other formats you have(.wmv, .avi, .ogg, etc)

There's probably a better way to do this that I don't know about...

---

### Post by tagra123 on 2007-01-07
> **ramasdf123 said:**
> How can i set the default dvd player to be VideoLan and not the movie player?

From a terminal:

type

```
gconf-editor
```

Click on the arrow to Expand Desktop

then

Click on the arrow to Expand Gnome

Then click on Volume Manager

Look for autoplay dvd command on th right side of the screen
Double Click

The value should be 

totem %M

change it to

/usr/bin/vlc dvd://


same thing for VCD

/usr/bin/vlc vcd://


etc ...


Now when ever a dvd is inserted it will start with VLC -- same for VCD.  10X better then totem

Hope it helps

---

### Post by dj1120 on 2007-01-14
Thanks you answered a question I have had for a couple of weeks!!

---

### Post by ramasdf123 on 2007-01-19
LOL, thanks man this helps

your guys :guitar: !

---

### Post by Trekko on 2007-01-29
That did'nt work for me, Vlc is just starting up but not playing.

I had to add the command
```
/usr/bin/vlc /media/cdrom
```
instead.

Probebly because a missing symlink called dvd? Please correct me on this if it is'nt right.

---

### Post by Starchild on 2007-04-04
System > Preferences > Removable Drives and Media (Multimedia tab)

write ```
vlc %m
``` in command section for Video DVD Discs

---

### Post by akbob on 2007-04-28
System|Preferences|Removable Drives and Media|Multimedia
Enter  /usr/bin/vlc %d (or browse to your location for vlc command)

worked in 6.1 and 7.04

---

### Post by jlc on 2007-05-01
Try this:

```

gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "vlc dvd://"

```

When you stick a dvd in, that should pop up vlc.

---

### Post by mad chey on 2007-05-13
> **tagra123 said:**
> From a terminal:

type

```
gconf-editor
```



i got stuck here, as this was the reply

 gconf: command not found

---

### Post by jlc on 2007-05-14
aptitiude search gconf-editor?

---

### Post by voodooo on 2007-05-15
> **mad chey said:**
> i got stuck here, as this was the reply

 gconf: command not found

you typed it with a whitespace before *-editor*? cause this just happened to me, without blank it worked fine :)

---

### Post by linux_believer on 2007-08-21
Thanks tagra123

Worked perfectly!!!

---

### Post by JaxDomino on 2008-03-07
I can't believe I can finally watch movies sing Ubuntu.  I am one step closer to getting rid of Windows for good!

---

### Post by anton on 2008-06-30
I've tried this with Hardy and can't get it to work.  Totem keeps opening every time I insert a DVD.

I've used gconf-editor as well as entering the gconftool-2 command from the therminal. 

Please help . . .

---

### Post by bob27 on 2008-07-03
Found a great multimedia guide that solved it for me:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=default+dvd+vlc](http://ubuntuforums.org/showthread.php?t=766683&highlight=default+dvd+vlc)

This was the section that helped me:


UBUNTU 8.04 HARDY HERON USERS ONLY

To change the default DVD player in Hardy Heron to VLC (not Kubuntu, issues with Xubuntu), copy and paste this command into the terminal:

gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to Places > Computer > Edit > Preferences > Media > DVD Video and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD.

---

### Post by mentaluproar on 2008-07-03
That last post fixed things for me, but when the disc loads automatically, I am left without working DVD menus.  It just loads the first file it finds on the disc.  When I load it manually (open disc) it runs just fine.  What is the next step?

---

### Post by connord94 on 2008-07-05
> **bob27 said:**
> Found a great multimedia guide that solved it for me:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=default+dvd+vlc](http://ubuntuforums.org/showthread.php?t=766683&highlight=default+dvd+vlc)

This was the section that helped me:


UBUNTU 8.04 HARDY HERON USERS ONLY

To change the default DVD player in Hardy Heron to VLC (not Kubuntu, issues with Xubuntu), copy and paste this command into the terminal:

gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to Places > Computer > Edit > Preferences > Media > DVD Video and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD.

This worked, VLC opened, but then Gnome committed suicide and I was took to the user log on screen, and had to log back in.


Help ?

Connor

+++++++Edit+++++++

It worked perfectly second time round, thanks :D


Connor

---

### Post by jackrussell_333 on 2008-11-13
that's just the information I was looking for . Thanks a million you saved me from pulling out every hair I have left in my head

---

### Post by uberdonkey5 on 2009-01-11
> **bob27 said:**
> Found a great multimedia guide that solved it for me:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=default+dvd+vlc](http://ubuntuforums.org/showthread.php?t=766683&highlight=default+dvd+vlc)

This was the section that helped me:


UBUNTU 8.04 HARDY HERON USERS ONLY

To change the default DVD player in Hardy Heron to VLC (not Kubuntu, issues with Xubuntu), copy and paste this command into the terminal:

gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to Places > Computer > Edit > Preferences > Media > DVD Video and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD.

I open a disk with vlc that I had recorded (and played well before) i.e. had no menu. vlc went crazy trying to open it but without success (just kept trying).

Tried it with commercial DVD and vlc just went dark grey (didn't function). Whats going on??? Do I have to change preferences in vlc??

---

### Post by uberdonkey5 on 2009-01-11
> **bob27 said:**
> Found a great multimedia guide that solved it for me:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=default+dvd+vlc](http://ubuntuforums.org/showthread.php?t=766683&highlight=default+dvd+vlc)

This was the section that helped me:


UBUNTU 8.04 HARDY HERON USERS ONLY

To change the default DVD player in Hardy Heron to VLC (not Kubuntu, issues with Xubuntu), copy and paste this command into the terminal:

gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to Places > Computer > Edit > Preferences > Media > DVD Video and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD.

I open a disk with vlc that I had recorded (and played well before) i.e. had no menu. vlc went crazy trying to open it but without success (just kept trying).

Tried it with commercial DVD and vlc just went dark grey (didn't function and then had to force quit). Whats going on??? Do I have to change preferences in vlc??

---

### Post by freewaybear on 2009-02-26
> **uberdonkey5 said:**
> I open a disk with vlc that I had recorded (and played well before) i.e. had no menu. vlc went crazy trying to open it but without success (just kept trying).

Tried it with commercial DVD and vlc just went dark grey (didn't function and then had to force quit). Whats going on??? Do I have to change preferences in vlc??

I have the exact same problem :( so I just had to bump this :D

---

### Post by thoralf on 2009-03-07
solution #3 worked for me.

however, it somehow feels terribly wrong that there are three possible ways / config-files that need to be changed to achieve the desired behaviour. as much as i like gnome in general, i have to say that it fares even worse than windows in this respect.

t.

---

### Post by Alex82 on 2009-03-13
> **uberdonkey5 said:**
>  Tried it with commercial DVD and vlc just went dark grey (didn't function). Whats going on??? Do I have to change preferences in vlc??

Hello I am having the same problem also, when Vlc autoruns it is just greyed out and wont work, but still works fine when accessed from applications>sound and video>VLC media player

any suggestions would be greatly appriciated

---

### Post by jimbo1 on 2009-05-09
> **Alex82 said:**
> Hello I am having the same problem also, when Vlc autoruns it is just greyed out and wont work, but still works fine when accessed from applications>sound and video>VLC media player

any suggestions would be greatly appriciated


I fixed the above problem of VLC greying out:
Right click applications menu, edit menus, sound and video, right click VLC and select properties and change the command field to read vlc %f

Hope this works for you!

---

