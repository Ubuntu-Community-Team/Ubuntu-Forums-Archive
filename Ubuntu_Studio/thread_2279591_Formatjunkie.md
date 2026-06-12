---
title: "Formatjunkie"
date: 2015-05-24
forum: Ubuntu Studio
---

### Post by Miykel on 2015-05-24
Having trouble trying to install formatjunkie, using the following code;
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
sudo add-apt-repository ppa:noobslab/apps
sudo apt-get update
sudo apt-get install formatjunkie

This string    sudo add-apt-repository ppa:jon-severinsson/ffmpeg     comes up with  incorrect format...
Can anyone help or is there another program to convert from  mp4 to mpeg
Many Thanks M

---

### Post by jejeman on 2015-05-24
avconv
is a ffmpeg fork. It is in ubuntu repositories. You can use that.

---

### Post by Miykel on 2015-05-26
Found this at Noobs Labs, worked fine.

[TABLE="class: code-table, align: left"]
[TR]
[TD]sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next
[/TD]
[/TR]
 [TR]
[TD]sudo apt-get update
[/TD]
[/TR]
 [TR]
[TD]sudo apt-get install ffmpeg
[/TD]
[/TR]
[/TABLE]

---

