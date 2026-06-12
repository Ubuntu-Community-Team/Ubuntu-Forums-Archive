---
title: "Music player not playing m4a"
date: 2016-01-30
forum: Ubuntu Phone and Tablet
---

### Post by Nordic_Wolf on 2016-01-30
I'm using the BQ Aquaris E4.5 and have a problem playing m4a files.

I have no problems playing mp3 files, when I place them in the Music folder the app finds them and plays them fine. When I add a m4a file though, the player doesn't find the file until I restart the phone. Only after a restart I see the song but when I click it the song will open but not play, the app also becomes completely unresponsive . I checked the ID tags but everything is complete. Tried it with 3 different songs and all have the same problem, they play fine on the desktop and on my Android phone.

Anyone who might have a clue what the problem here could be?

---

### Post by ajgreeny on 2016-01-30
Open a terminal and type command:
```
sudo apt-get install ubuntu-restricted-extras
``` or use software-center if you want a GUI.

---

### Post by Nordic_Wolf on 2016-01-30
Yeah that was my first thought too, but this is Ubuntu Touch so unfortunately this doesn't help. 

Thanks for the help though.

---

### Post by coffeecat on 2016-01-30
I don't have much to suggest in regard to your m4a files that are not playing, but I can tell you that Music player in my BQ Aquaris E5 plays m4a files just fine. Have you tried creating new m4a files using different software from that you used for the ones which are causing problems?

---

### Post by QDR06VV9 on 2016-01-30
To convert m4a to mp3[URL="http://soundconverter.org/"]
SoundConverter[/URL][COLOR=#111111][FONT=Ubuntu] can do this without having to mess around on the command-line, and it's available in the Ubuntu Software Center:


Or you can do it command line using FFMPEG
[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]ffmpeg -v 5 -y -i input.m4a -acodec libmp3lame -ac 2 -ab 192k output.mp3[/FONT][/COLOR]


```[COLOR=#111111][FONT=Ubuntu]
I have not used the above^^^^ for quite awhile now.
More info here ... [/FONT][/COLOR][http://askubuntu.com/questions/65331/how-to-convert-a-m4a-sound-file-to-mp3](http://askubuntu.com/questions/65331/how-to-convert-a-m4a-sound-file-to-mp3)

---

### Post by howefield on 2016-01-30
> **Nordic_Wolf said:**
> Anyone who might have a clue what the problem here could be?

Might be this bug [https://bugs.launchpad.net/music-app/+bug/1408681](https://bugs.launchpad.net/music-app/+bug/1408681)

If you think it is, it would be useful to mark it as affecting you too.

---

### Post by Nordic_Wolf on 2016-01-30
> **howefield said:**
> Might be this bug [https://bugs.launchpad.net/music-app/+bug/1408681](https://bugs.launchpad.net/music-app/+bug/1408681)

If you think it is, it would be useful to mark it as affecting you too.
Thanks, this explains the problem indeed, marked it as affecting me too.

---

### Post by howefield on 2016-01-30
Thank you :)

---

