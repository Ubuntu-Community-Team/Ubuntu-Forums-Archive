---
title: "Looking for a download accelerator"
date: 2010-10-18
forum: The Cafe
---

### Post by m4tic on 2010-10-18
Basically i am looking for anything as close to Download accelerator pro for windows and mac. It's what i use to download large files at my institution. Now I bought a usb dongle which reports 5-7Mbps of speed on speedtest but sometimes I'm not getting what it promises like just now when trying to download libreOffice. Since I do not have windows, it be nice to have an easy download manager, i'm on Maverick any help?

---

### Post by m4tic on 2010-10-18
on that note, tomorrow i want to install Ubuntu restricted extras, i can't seem to find them, any link?

---

### Post by Half-Left on 2010-10-18
Use a bittorrent link if you can or you could look in the Software Centre for one. Gwget Download Manager?

---

### Post by undecim on 2010-10-18
You can't download a file faster than the server you're downloading from will upload it. My guess is that windows "Download accelerators" just give you the 20% of bandwidth windows restricts. Other than that, it might make sure that the highest compression supported by the download server is being used (which firefox already does), and let you pause/resume downloads. (which, again, firefox already does)

If you want a download manager though (i.e. so you can close firefox while still downloading) look at gwget.

EDIT: btw, Ubuntu restricted extras should be in the software center. If you are trying to install it from synaptic, you will need to enable your restricted software sources.

---

### Post by slackthumbz on 2010-10-18
```
sudo apt-get install ubuntu-restricted-extras
```

But of course you will have to make sure you've enabled all the extra repos before hand. If you were connected to the internet during the install then you should have had the option to install them then (it asks you about adding extra codecs for media and so forth. That IS the restricted extras pack as far as I could tell).

---

### Post by Earl_Maroon on 2010-10-18
The best download manager I have come across is wget, a simple command line tool that is included in Ubuntu by default. The best feature of it is that you can use it to resume a partial download at any point, in case you lose your connexion for some reason, or even have to stop it yourself. It handles large files perfectly, supports http and ftp, and can be used to download directories recursively too. Of course, CLI isn't optimal for everyone, but this is a simple program and you'd get used to it, I'm sure.

---

### Post by lukeiamyourfather on 2010-10-18
> **m4tic said:**
> Basically i am looking for anything as close to Download accelerator pro for windows and mac.

Try DownThemAll! for Firefox. It will use concurrent connections to "accelerate" downloads unlike some of the others mentioned in this thread (like wget).

[https://addons.mozilla.org/en-US/firefox/addon/201/](https://addons.mozilla.org/en-US/firefox/addon/201/)

Though it might not help much depending on what is being downloaded. Their servers might be at capacity.

---

### Post by A_T on 2010-10-18
multiget is in the repo - it can download using multiple threads.

---

### Post by m4tic on 2010-10-18
Thanks for all the repiles. I'm low on bandwidth right now and i'll be doing a clean install of maverick in a few minutes. i want to just download libreoffice today and the restricted extras i'm planning on downloading at my campus tomorrow which the computers are windows based. in the past, the scripts people used to package the extras always ended in broken packages (when 9.10 came out there was only for 9.04, same as 10.10 they seem to take time to package). Plus the the reason it's convenient to have .deb files is i can share easily with friends, most of them still shy away from adding ppa's.

---

### Post by m4tic on 2010-10-18
> **lukeiamyourfather said:**
> Try DownThemAll! for Firefox. It will use concurrent connections to "accelerate" downloads unlike some of the others mentioned in this thread (like wget).

[https://addons.mozilla.org/en-US/firefox/addon/201/](https://addons.mozilla.org/en-US/firefox/addon/201/)

Though it might not help much depending on what is being downloaded. Their servers might be at capacity.

Ahh thanks a lot, i've spent so much time on chrome i've neglected everything, i'll compare this with the others and will give feedback.

---

### Post by hate.mycrowsoft7 on 2010-11-10
> **m4tic said:**
> Basically i am looking for anything as close to Download accelerator pro for windows and mac. It's what i use to download large files at my institution. Now I bought a usb dongle which reports 5-7Mbps of speed on speedtest but sometimes I'm not getting what it promises like just now when trying to download libreOffice. Since I do not have windows, it be nice to have an easy download manager, i'm on Maverick any help?
There r two download managers (DM) I love most.They can't download video  files from youtube and from similar websites but if u can download any  file by firefox then the file can be downloaded by the DMs - Axel and  Skdownloader.
Axel can be found in the software center .If u know the download link then open terminal and type 
axel <download link>
Skdownloader is a java based downloader.To download skdownloader go to
 _[http://www.toolsbysk.com/skdownloade...ads/index.html]("http://www.toolsbysk.com/skdownloader/downloads/index.html")_
 U'll get a .sh file.To install copy the .sh file u downloaded to ur  Home Folder and open terminal and type 
sh somescript.sh
Skdownloader can  download a file in atmost 10 parts and its far better than Internet  Download Manager.:lolflag:

---

### Post by mips on 2010-11-10
wxDownload Fast
d4x
Multiget

---

### Post by mips on 2010-11-10
> **undecim said:**
> You can't download a file faster than the server you're downloading from will upload it. My guess is that windows "Download accelerators" just give you the 20% of bandwidth windows restricts. 

You need to look into multi-threaded & multi-server downloads as it will clarify things a bit.

---

### Post by mbz99 on 2010-11-11
DownthemAll
Jdownloader

CLI programs: 
Aria2
Axel

---

### Post by hate.mycrowsoft7 on 2010-11-16
For a better explanation of my post please check the url :

[http://www.techsupportalert.com/best-free-download-manager.htm](http://www.techsupportalert.com/best-free-download-manager.htm)

Its a great website on FOSS.   
):P

---

### Post by NightwishFan on 2010-11-16
This is a new program for Ubuntu, and is now my download manager of choice. [https://launchpad.net/steadyflow](https://launchpad.net/steadyflow) <3 Vala. :)

---

### Post by swamyuefa on 2012-05-22
> **hate.mycrowsoft7 said:**
> There r two download managers (DM) I love most.They can't download video  files from youtube and from similar websites but if u can download any  file by firefox then the file can be downloaded by the DMs - Axel and  Skdownloader.
Axel can be found in the software center .If u know the download link then open terminal and type 
axel <download link>
Skdownloader is a java based downloader.To download skdownloader go to
 _[http://www.toolsbysk.com/skdownloade...ads/index.html]("http://www.toolsbysk.com/skdownloader/downloads/index.html")_
 U'll get a .sh file.To install copy the .sh file u downloaded to ur  Home Folder and open terminal and type 
sh somescript.sh
Skdownloader can  download a file in atmost 10 parts and its far better than Internet  Download Manager.:lolflag:

thanks guys for this information, i am newbie to linux, but below link is not working
" [U][http://www.toolsbysk.com/skdownloade...ads/index.html]("http://www.toolsbysk.com/skdownloader/downloads/index.html") " 


[/U]

---

### Post by chamber on 2012-05-22
[IMG]http://www.mcarterbrown.com/gallery/data/506/necropost2.jpg[/IMG]

---

### Post by IWantFroyo on 2012-05-22
I used to use axel.

---

### Post by sffvba[e0rt on 2012-05-22
[IMG]http://i299.photobucket.com/albums/mm313/Zenzirouj/ThreadNecro.gif[/IMG]

*Back to sleep **old **thread...*


404

---

