---
title: "R Studio install and MiME multmedia requirements"
date: 2013-09-03
forum: Ubuntu Development Version
---

### Post by Ramesh_Jude_Fernando on 2013-09-03
Hi all,
I installed R and wanted RStudio on Saucy so I downloaded RStudio and ran the install which said I need libjpeg62, so used Synaptic to install that and then ran dpkg again with the RStudio deb package and installed fine this time exluding this error
Setting up rstudio (0.97.551) ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

---

### Post by Ramesh_Jude_Fernando on 2013-09-03
Sorry, for lack of information. What I am wondering is there any way to fix the error?

---

### Post by cariboo on 2013-09-03
What version of Ubuntu are you using, and despite the error messages, does the application work? I don't recognize some of the file extensions, so that can't be very common.

If you aren't running Saucy, you may get more help in the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") sub-forum

---

### Post by monkeybrain20122 on 2013-09-03
Rstudio is R IDE Nothing to do with multimedia as far as I know. OP says he uses Saucy which is still under development, I think that is the problem. I am using Rstudio in 12.04 and 13.04 on 32 and 64 bit machines, never encounter any problem.

---

### Post by cariboo on 2013-09-03
> **monkeybrain20122 said:**
> Rstudio is R IDE Nothing to do with multimedia as far as I know. OP says he uses Saucy which is still under development, I think that is the problem. I am using Rstudio in 12.04 and 13.04 on 32 and 64 bit machines, never encounter any problem.

My mistake, I thought I saw a couple of MS multimedia extensions, so assumed wrongly that it was a multimedia production studio.

---

### Post by rumi-proynova on 2014-03-21
I had this error message too when I installed it on Debian, and I thought that the installation failed. But then I noticed that the installation has succeeded after all, at least I was able to start it and execute a script. Maybe there will be errors when I use it more, but I hope not.

---

### Post by su:bhatta on 2014-03-21
> **Ramesh_Jude_Fernando said:**
> Hi all,
I installed R and wanted RStudio on Saucy so I downloaded RStudio and ran the install which said I need libjpeg62, so used Synaptic to install that and then ran dpkg again with the RStudio deb package and installed fine this time exluding this error
```
Setting up rstudio (0.97.551) ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu
```'

I have this too but there are no system problems as such. Nothing to report and apport is not triggered.
I opened a thread and was told by senior members that it is of no great import and it can be removed by :

```
sudo rm /usr/share/mime/packages/kde.xml  
sudo update-mime-database /usr/share/mime
```

You can find my thread here: [http://ubuntuforums.org/showthread.php?t=2208433](http://ubuntuforums.org/showthread.php?t=2208433)

---

