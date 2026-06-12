---
title: "playlist doesnt work - m3u file"
date: 2010-07-12
forum: Server Platforms
---

### Post by krack3rz on 2010-07-12
I found some code and tuts that tell me how to create a playlist, and I followed it to the letter but it doesnt work...I'm guessing it has somethin to do with my configuration settings with apache, otherwise here's the code:

```
<embed type="audio/mpeg" name="musicplaylist" src="/../../music/musicplaylist.mp3" width="250" height="35" hidden="false" autostart="false" loop="true" ></embed>
```
*i replaced code with /../../ in source for here otherwise it is different*

so inside the m3u file the code is:
```
# my playlist named:musicplaylist.m3u
/../../music/file_name1.mp3
/../../music/file_name2.mp3
/../../music/file_name3.mp3
```

Help! ](*,)

---

### Post by ajgreeny on 2010-07-12
I always use .pls file type for playlists, not m3u.  Perhaps worth trying that with this format, produced from folders of music files on my machine with rhythmbox.
```
[playlist]
X-GNOME-Title=Marillion_Misplaced_Childhood
NumberOfEntries=10
File1=file:///home/andrew/Music/Marillion/Misplaced_Childhood/01_Pseudo_Silk_Kimono.mp3
File2=file:///home/andrew/Music/Marillion/Misplaced_Childhood/02_Kayleigh.mp3
File3=file:///home/andrew/Music/Marillion/Misplaced_Childhood/03_Lavender.mp3
File4=file:///home/andrew/Music/Marillion/Misplaced_Childhood/04_Bitter_Suite.mp3
File5=file:///home/andrew/Music/Marillion/Misplaced_Childhood/05_Heart_of_Lothian.mp3
File6=file:///home/andrew/Music/Marillion/Misplaced_Childhood/06_Waterhole.mp3
File7=file:///home/andrew/Music/Marillion/Misplaced_Childhood/07_Mylo.mp3
File8=file:///home/andrew/Music/Marillion/Misplaced_Childhood/08_Perimeter_Walk__Threshold.mp3
File9=file:///home/andrew/Music/Marillion/Misplaced_Childhood/09_Childhoods_End.mp3
File10=file:///home/andrew/Music/Marillion/Misplaced_Childhood/10_White_Feather.mp3
```

---

### Post by gobbledigook on 2010-07-12
hi there! 

i don't think you can just embed a .m3u playlist and expect a browser just to play it... i think you need to embed a player and get that to play the playlist :)

i use xspf, a tutorial [**_here_**]("http://www.boutell.com/newfaq/creating/playlist.html") may help

---

