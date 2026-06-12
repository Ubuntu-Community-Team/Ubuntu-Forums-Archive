---
title: "Insignia MP3, anyone know what types of movies it takes?"
date: 2007-12-25
forum: The Cafe
---

### Post by smartboyathome on 2007-12-25
I got a new 2GB Insignia mp3 player to replace my CD player (getting very old and is already starting to break down), but can't seem to get it to play videos. I have read that the Insignia Video 4GB can play WMV and MPEG4, and there was a suggestion of an app to use (WinFF + ffmpeg) to convert my .avi movies to WMV/MPEG4, but it still won't play. Anyone know what format the 2GB Insignia MP3 plays?

Also, I tried installing the CD on my Vista comp, and it won't convert the WMV to the format I need. Anyone that has one of these, help please. :)

---

### Post by empedocles on 2007-12-25
I got reasonable results with mencoder:
 mencoder MyMovie.avi -ovc lavc -oac mp3lame -lameopts cbr:br=128 -ffourcc XVID -lavcopts vcodec=mpeg4:vbitrate=256 -vf scale=220:176,crop=220:176 -ofps 15 -o mymovie_insignia.avi


Your mileage may vary

---

### Post by smartboyathome on 2007-12-25
Thanks, i got on my mom's computer and encoded the movie, but I will try this out on a few other movies.

---

### Post by smartboyathome on 2007-12-26
That code works, thanks. :)

---

### Post by jcorral2 on 2008-01-03
i have an iBook G4 ... and i just bought this Insignia 4G ... so far songs only under mp3 format work .. and pics using .JPG work ... i could not get Vid to work ... Someone tell me what exact formats are allowed on the Insignia and which are NOT allowed .... Do i need a converter if have a MAC .... what do i do .. Help ................ by the way mine Froze up earlier today and still wont shut off .. its stuck and have to take it back

---

### Post by smartboyathome on 2008-01-03
1) If your Insignia freezes, hold the power button for 30-40 secs, and it will shut itself down.
2) Here is the script I made for converting my movies to the correct format:
```
#!/bin/sh
# **********************************************
# *           Insignia Video Encoder           *
# * Encodes your video for your Insignia sport *
# *             By smartboyathome              *
# **********************************************

echo "Type the path to your video that you want to encode and press [ENTER]: "
read pathdecoded

echo "Type where you want the encoded video to be put (including the video's file name) and press [ENTER]: "
read pathencoded

echo "Encoding, please wait..."
mencoder $pathdecoded -ovc lavc -oac mp3lame -lameopts cbr:br=128 -ffourcc XVID -lavcopts vcodec=mpeg4:vbitrate=256 -vf scale=220:176,crop=220:176 -ofps 15 -o $pathencoded >/dev/null 2>/dev/null

# WMV to AVI
# mencoder $pathdecoded -ofps 23.976 -ovc lavc -oac copy -o outfile.avi

echo "Done!"
```

Simply save it in your home folder, make it executable (right click on it and click properties, then browse through the tabs until you see a checkbox which says "run this as a program" or "make executable"). Then, run this command to copy it to your bin file so you can execute it on the fly:
sudo cp ~/insignia-encode /usr/bin/

---

### Post by penquin on 2008-02-21
try using the following [http://mediacoder.sourceforge.net/download.htm](http://mediacoder.sourceforge.net/download.htm) 
then use this guide [http://www.anythingbutipod.com/forum/showthread.php?t=23552&highlight=mediacoder+insignia](http://www.anythingbutipod.com/forum/showthread.php?t=23552&highlight=mediacoder+insignia)
but change the format to xvid. and it works fine. no fuss or muss

---

