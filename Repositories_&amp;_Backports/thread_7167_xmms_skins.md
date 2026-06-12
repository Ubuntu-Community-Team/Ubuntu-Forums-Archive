---
title: "xmms skins?"
date: 2004-12-04
forum: Repositories &amp; Backports
---

### Post by the stranger on 2004-12-04
how do i add xmms skins?

thanks in advance!

---

### Post by LongTooth on 2004-12-04
Start off will Synaptic> Search>...key in 'xmms-Skins'. That shoud get you half a dozen or so skins. If that is not enough go to google.com/linux and search for xmms skins. You will be directed to a site with the Xmms skin tarballs. Have you made a folder in your home directory labled 'downloads'? It's the first thing I do when I install a distro. Your broswer will ask you where to download the tarballs. Make sure you direct it to the 'downloads' folder you made. Go to 'Computer' on your panel,>home>downloads. Click on the downloaded tarball. FileRoler will open. Highlight the file. In the panel up top, pick 'Extract'. You will be given a choice as to where to extract the file to. Your home directory>downloads is the best choice -remember the 'download' folder you made? Put it there. Once that is done you will see the extracted package. 

The next step is to move that skin to the file where the XMMS skins are located. Do a whereis Xmms skins at the CLI. You will get something like /usr/bin/XMMS/Skins. Or usr/local/bin/XMMS/Skins. You'll have to look for it. Anyway, once you know where the XMMS skins are you are half way there. 

You've extracted the downloaded XMMS skins. CD into the directory that contains the skins you've extraced (hopefully the 'downloads' folder you made). Since you've extracted them into your 'download' directory that is where you should be -cd downloads.  Do a 'ls'. you should see you new extracted XMMS skins package there as well as other things. Since you know where you XMMS skins are and you've cut and past it-you have done that, haven't you?. Your next job it to move the new skins. Stay in the folder where you've extracted the new skins. Sudo mv [newXMMSskinpackage] /usr/local/bin/XMMS/Skins -or something like that. That will move the new skin into your XMMS. Hope this helps.

---

### Post by Xian on 2004-12-04
Attached is a nice Winamp style skin. There's many out there to choose from.

---

### Post by jazzorist on 2004-12-05
XMMS skin folder is also located in your home dir : ~/.xmms/Skins . You put your extracted theme(s) in this folder, hit Alt+S and you can browse/select your skins. ;)

..J..

---

### Post by TravisNewman on 2004-12-05
Can a mod with power here move this to the proper location?

Just a side-note, I'm typing this a lot today

---

### Post by clasqm on 2004-12-05
[QUOTE=LongTooth]
The next step is to move that skin to the file where the XMMS skins are located. Do a whereis Xmms skins at the CLI. You will get something like /usr/bin/XMMS/Skins. Or usr/local/bin/XMMS/Skins. You'll have to look for it. Anyway, once you know where the XMMS skins are you are half way there. 
[/QUOTE]

Longtooth is exactly right. But there is an easier way.

Firstly, xmms will use any of the bazillions of winamp 2.x skins available on the net. These are normally packaged as a .wsz or zip file. (wsz is just a zip file with a funny extension)

Now, assuming you will be the only user of these skins: Once downloaded, just put the .tgz, .wsz or .zip in /home/<your login>/.xmms/Skins 

This directory is created automatically when xmms is run the first time. No need to decompress them, just put the archives there, run xmms and select the skin of your choice. Easy!

---

