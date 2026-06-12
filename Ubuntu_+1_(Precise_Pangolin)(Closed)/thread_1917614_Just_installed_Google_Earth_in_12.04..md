---
title: "Just installed Google Earth in 12.04."
date: 2012-01-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2012-01-30
I see Google Earth released a new update so I downloaded the .deb file and installed on the 64bit 12.04 and it seems to run great. I had a few issues with the package manager while installing it, but it installed OK. It seems to be working quite well. Just thought I would let others know it works.
Here is the link to the download.
[http://www.google.com/earth/download/ge/agree.html]("http://www.google.com/earth/download/ge/agree.html")

Also  WEB UPD8 has a write up on it: 
[http://www.webupd8.org/2012/01/google-earth-62-released-with-new-way.html]("http://www.webupd8.org/2012/01/google-earth-62-released-with-new-way.html")

---

### Post by philinux on 2012-01-30
> **irv said:**
> I see Google Earth released a new update so I downloaded the .deb file and installed on the 64bit 12.04 and it seems to run great. I had a few issues with the package manager while installing it, but it installed OK. It seems to be working quite well. Just thought I would let others know it works.
Here is the link to the download.
[http://www.google.com/earth/download/ge/agree.html]("http://www.google.com/earth/download/ge/agree.html")

Also  WEB UPD8 has a write up on it: 
[http://www.webupd8.org/2012/01/google-earth-62-released-with-new-way.html]("http://www.webupd8.org/2012/01/google-earth-62-released-with-new-way.html")

Have they fixed the font problem yet?

---

### Post by irv on 2012-01-30
> **philinux said:**
> Have they fixed the font problem yet?

Here is a screen shot.
[ATTACH]211684[/ATTACH]

EDIT: They are at Google Earth 6.2.

---

### Post by philinux on 2012-01-30
> **irv said:**
> Here is a screen shot.
[ATTACH]211684[/ATTACH]

EDIT: They are at Google Earth 6.2.

Yep still not fixed. I have the msttcorefonts installed but I had to use google-fix to sort it out.

[http://techgratuity.com/how-to-install-google-earth-6-2-on-ubuntu-linux](http://techgratuity.com/how-to-install-google-earth-6-2-on-ubuntu-linux)

Scroll down.

---

### Post by irv on 2012-01-30
Also WEB UPD8 had this on their web page: 

[ATTACH]211685[/ATTACH]

If the font looks broken under Ubuntu (like in the above screenshot), you can fix this issue by installing the 'msttcorefonts' package:

```
sudo apt-get install msttcorefonts
```

Then log out and log back in!

---

### Post by philinux on 2012-01-30
> **irv said:**
> Also WEB UPD8 had this on their web page: 

[ATTACH]211685[/ATTACH]

If the font looks broken under Ubuntu (like in the above screenshot), you can fix this issue by installing the 'msttcorefonts' package:

```
sudo apt-get install msttcorefonts
```

Then log out and log back in!

That did not work for me but google-fix did.

---

### Post by zika on 2012-01-30
> **irv said:**
> Also WEB UPD8 had this on their web page: 

[ATTACH]211685[/ATTACH]

If the font looks broken under Ubuntu (like in the above screenshot), you can fix this issue by installing the 'msttcorefonts' package:

```
sudo apt-get install msttcorefonts
```Then log out and log back in!Is package fonts-liberation enough or MSttCoreFonts is necessary?

---

### Post by mc4man on 2012-01-30
> **zika said:**
> Is package fonts-liberation enough or MSttCoreFonts is necessary?
Maybe - GE displayed as expected here without MSttCoreFonts installed, fonts-liberation is default included so  that could be why..

---

### Post by Xgen on 2012-01-30
Hmm...Error: Cannot install 'ia32-libs'. Works on Oneiric, though.

---

### Post by mc4man on 2012-01-30
> **philinux said:**
> That did not work for me but google-fix did.
I'll bet you have wine installed

Test here - 
fresh PP install, no wine, no MSttCoreFonts, GE works fine
installed MSttCoreFonts, GE works fine
installed wine-1.2 & it's deps, GE shows 'bad' fonts

removed wine - GE still bad
removed - ttf-droid ttf-umefont [COLOR="Red"]ttf-unfonts-core[/COLOR], GE back to good

So - what does 'install google-fix' mean?

Edit: re-installed wine which due to recommends installed ttf-umefont ttf-unfonts-core & broke the fonts again after log out/in
The 1st. one is nothing, removing ttf-unfonts-core restored proper fonts in Ge

---

### Post by philinux on 2012-01-30
No wine installed.

Google-fix from here.
 [http://techgratuity.com/how-to-install-google-earth-6-2-on-ubuntu-linux](http://techgratuity.com/how-to-install-google-earth-6-2-on-ubuntu-linux)

---

### Post by zika on 2012-01-30
> **philinux said:**
> No wine installed.

Google-fix from here.
 [http://techgratuity.com/how-to-install-google-earth-6-2-on-ubuntu-linux](http://techgratuity.com/how-to-install-google-earth-6-2-on-ubuntu-linux)
I can not see where to DL Google-fix from the page You gave.
On this page: [http://hackapc.com/how-to-install-google-earth-on-ubuntu-11.10.html](http://hackapc.com/how-to-install-google-earth-on-ubuntu-11.10.html) there is a link to Google-fix: [https://docs.google.com/uc?id=0B2iTttURwOa1YzM3YmE2MjgtYWMxNS00ZTQwLWFlZWMtMjRmMmU3OGNjMTMx&export=download&authkey=CIHT1OkH&hl=it](https://docs.google.com/uc?id=0B2iTttURwOa1YzM3YmE2MjgtYWMxNS00ZTQwLWFlZWMtMjRmMmU3OGNjMTMx&export=download&authkey=CIHT1OkH&hl=it) ...
Disclaimer: I did not try any of these (yet)...

---

### Post by mc4man on 2012-01-30
> **zika said:**
> I can not see where to DL Google-fix from the page You gave.
On this page: [http://hackapc.com/how-to-install-google-earth-on-ubuntu-11.10.html](http://hackapc.com/how-to-install-google-earth-on-ubuntu-11.10.html) there is a link to Google-fix: [https://docs.google.com/uc?id=0B2iTttURwOa1YzM3YmE2MjgtYWMxNS00ZTQwLWFlZWMtMjRmMmU3OGNjMTMx&export=download&authkey=CIHT1OkH&hl=it](https://docs.google.com/uc?id=0B2iTttURwOa1YzM3YmE2MjgtYWMxNS00ZTQwLWFlZWMtMjRmMmU3OGNjMTMx&export=download&authkey=CIHT1OkH&hl=it) ...
Disclaimer: I did not try any of these (yet)...

That worked well, likewise couldn't find the link on other page.

Using the fix took the fonts from crappy as shown in post 3 to good. (the broken fonts look here  was as in post 5

---

### Post by philinux on 2012-01-31
Dang. I'm pretty sure there was a valid link to [Google-fix]("https://docs.google.com/uc?id=0B2iTttURwOa1YzM3YmE2MjgtYWMxNS00ZTQwLWFlZWMtMjRmMmU3OGNjMTMx&export=download&authkey=CIHT1OkH&hl=it") aka replacement.7z before. Ah well.

---

### Post by mc4man on 2012-01-31
> **philinux said:**
> Dang. I'm pretty sure there was a valid link to [Google-fix]("https://docs.google.com/uc?id=0B2iTttURwOa1YzM3YmE2MjgtYWMxNS00ZTQwLWFlZWMtMjRmMmU3OGNjMTMx&export=download&authkey=CIHT1OkH&hl=it") aka replacement.7z before. Ah well.
Well anyway thanks for mentioning the google-fix deal, major improvement over the usable but not nice look as irv had posted in #3 (at least here

---

### Post by philinux on 2012-01-31
> **mc4man said:**
> Well anyway thanks for mentioning the google-fix deal, major improvement over the usable but not nice look as irv had posted in #3 (at least here

Looks there's more ways to get it looking better. [http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by Cavsfan on 2012-01-31
I installed Google Earth from the link above. I got the **replacement.7z** file from zika's link.

Tried this and it got an error on the 4th command.

```
sudo apt-get install p7zip-full
cd ~/Downloads
7z x replacement.7z
[COLOR="Red"]replacement cd /[/COLOR]
sudo cp-r * / opt / google / earth / free /
```

```
Processing archive: replacement.7z

Extracting  replacement/googleearth
Extracting  replacement/libfreeimage.so.3
Extracting  replacement/libphonon.so.4
Extracting  replacement/libQtCore.so.4
Extracting  replacement/libQtGui.so.4
Extracting  replacement/libQtNetwork.so.4
Extracting  replacement/libQtWebKit.so.4
Extracting  replacement/plugins/imageformats/libqgif.so
Extracting  replacement/plugins/imageformats/libqjpeg.so
Extracting  replacement/plugins/imageformats
Extracting  replacement/plugins
Extracting  replacement

Everything is Ok

Folders: 3
Files: 9
Size:       35418192
Compressed: 10366713
cavsfan@cavsfan-desktop:~/Downloads$ replacement cd /
[COLOR="Red"]replacement: command not found[/COLOR]
cavsfan@cavsfan-desktop:~/Downloads$ 

```

What do I need to do now?

---

### Post by DougieFresh4U on 2012-01-31
Used link provided in first post, when I went to install it wanted to add 249 'other' packages.

---

### Post by Cavsfan on 2012-01-31
Never mind.
**replacement cd /** should have been **cd replacement**
And
**sudo cp-r * / opt / google / earth / free /** should have been
**sudo cp -r * /opt/google/earth/free/**

DUH! -> me.

It works and looks good now.
Thanks

---

### Post by zika on 2012-01-31
> **Cavsfan said:**
> I installed Google Earth from the link above. I got the **replacement.7z** file from zika's link.

Tried this and it got an error on the 4th command.

```
sudo apt-get install p7zip-full
cd ~/Downloads
7z x replacement.7z
[COLOR=Red]replacement cd /[/COLOR]
sudo cp-r * / opt / google / earth / free /
``````
Processing archive: replacement.7z

Extracting  replacement/googleearth
Extracting  replacement/libfreeimage.so.3
Extracting  replacement/libphonon.so.4
Extracting  replacement/libQtCore.so.4
Extracting  replacement/libQtGui.so.4
Extracting  replacement/libQtNetwork.so.4
Extracting  replacement/libQtWebKit.so.4
Extracting  replacement/plugins/imageformats/libqgif.so
Extracting  replacement/plugins/imageformats/libqjpeg.so
Extracting  replacement/plugins/imageformats
Extracting  replacement/plugins
Extracting  replacement

Everything is Ok

Folders: 3
Files: 9
Size:       35418192
Compressed: 10366713
cavsfan@cavsfan-desktop:~/Downloads$ replacement cd /
[COLOR=Red]replacement: command not found[/COLOR]
cavsfan@cavsfan-desktop:~/Downloads$ 

```What do I need to do now?Disclaimer: I did not install any of these files but I suspect it should be done as:

```
cd replacement
sudo cp -r * /opt/google/earth/free/
```

Link that I pointed to is (by no means) „mine“...

---

### Post by mc4man on 2012-01-31
nv

---

### Post by Cavsfan on 2012-01-31
Thanks **zika**.

If you look at the post above yours I figured out the commands were wrong.

I did exactly what you said. I just googled a bit and found there should be a space between cp and -r.

Thanks again! It works well. I have been playing with it some and the fonts are good.

---

### Post by mc4man on 2012-01-31
> **philinux said:**
> Looks there's more ways to get it looking better. [http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)
That method is somewhat similar to the google-fix so I try one or the other, don't do the above after using the google-fix or GE will likely not open

---

### Post by Quackers on 2012-01-31
I just installed GE 6.2 (64 bit) from that package and it looks fine :-) 
I must have all the required fonts already.

---

### Post by zika on 2012-01-31
> **Cavsfan said:**
> Thanks **zika**.

If you look at the post above yours I figured out the commands were wrong.

I did exactly what you said. I just googled a bit and found there should be a space between cp and -r.

Thanks again! It works well. I have been playing with it some and the fonts are good.
I write slowly... ;)

---

### Post by Cavsfan on 2012-01-31
> **zika said:**
> I write slowly... ;)


Thanks! We were probably typing at the same time.  I was just surprised the commands were not in the correct format. 
There were spaces where there shouldn't be and no spaces where there should have been.
I am used to just copying and pasting with some minor changes as my files were in Downloads and not on my Desktop.
I usually copy stuff to gedit as text and modify it as needed and then paste it back into terminal.

But, I very much appreciate your help! :D

---

