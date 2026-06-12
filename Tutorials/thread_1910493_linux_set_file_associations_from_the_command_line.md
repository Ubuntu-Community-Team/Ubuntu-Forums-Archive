---
title: "linux set file associations from the command line"
date: 2012-01-17
forum: Tutorials
---

### Post by COKEDUDE on 2012-01-17
At various times it is helpful to know how to setup file associations from the command line. Sometimes file managers just won't work, other times you may have a corrupted file or bad line in your file. I will give 3 examples. 

Pick out out a file of the type of file you want to set. 
I picked an avi, m4a, and jpg. 
Then query the file to figure out the mimetype syntax. 
```
xdg-mime query filetype /home/bob/Downloads/vid1.avi
```

Check what the default program is of that mimetype. 
Figure out what the **programname.desktop** of the program you want to use is. The simplest way to do this is by checking your **mimeapps.list** file located here. Obviously change your username. 
```
vi /home/bob/.local/share/applications/mimeapps.list
```
If that doesn't work try searching for the file with a similar command. 
```
find / -iname '*vlc.desktop*' 2>/dev/null
```
If the **programname.desktop** file has a weird name then you will need to grep for that file. Handbrake has the weirdest file name I have seen so I will use that as my example. 
```
sudo grep -riI "handbrake" /usr/share/applications/* 2>/dev/null
/usr/share/applications/ghb.desktop:Name=HandBrake
```
Check what the default program is of that mimetype. 
```
xdg-mime query default video/x-msvideo
```

Set the file association. 
```
xdg-mime default vlc.desktop video/x-msvideo
```

The examples. 
```
xdg-mime query filetype /home/bob/Downloads/vid1.avi
xdg-mime query default video/x-msvideo
xdg-mime default vlc.desktop video/x-msvideo
```

```
xdg-mime query filetype /media/3CACE1E0ACE194A4/Anthem.m4a
xdg-mime query default audio/mp4
xdg-mime default vlc.desktop audio/mp4
```

```
xdg-mime query filetype /home/bob/Downloads/shellr.jpg
xdg-mime query default image/jpeg
xdg-mime default gwenview.desktop image/jpeg
```

Verify that what you were trying to set worked. First check the **mimeapps.list**. Then use your favorite file manager to verify your work or use xdg-open. 
```
vi /home/bob/.local/share/applications/mimeapps.list
```
```
xdg-open /home/bob/Downloads/vid1.avi 
```

---

### Post by dewdrop_world on 2012-07-17
Doesn't work for me. After "xdg-mime default ... ..." I have this in mimeapps.list:

```
text/x-lilypond=frescobaldi.desktop
```

That's based on:

```
$ xdg-mime query filetype ~/...../middle-fast-1b.ly
text/x-lilypond
```

I also logged out and logged back in, but xdg-open still insists on opening .ly files in gedit.

More ideas?

---

