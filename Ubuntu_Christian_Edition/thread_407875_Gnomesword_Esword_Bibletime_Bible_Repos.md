---
title: "Gnomesword/ Esword/ Bibletime Bible Repos?"
date: 2007-04-12
forum: Ubuntu Christian Edition
---

### Post by accludetuner on 2007-04-12
I've been using esword on windows for a little over a year now and have accumulated over 120 bible versions in english alone, 50+ commentaries, and all kinds of maps, study notes, dictionaries, thesauruses, and so on.  I spent over 3 hours adding them to esword in linux.  While I was in the process of updating it I thought there had to be an easier way to update than manually doing them like this.  Then I thought about maybe adding a repository for bible tool updates and such.

It may be a little more difficult for esword since it's not directly a linux app, but what about gnomesword/bibletime?  They are not bad programs at all and being open source should continue to progress nicely.  There's actually plenty of modules available for them at [http://www.crosswire.org/sword/modules/index.jsp](http://www.crosswire.org/sword/modules/index.jsp)  and many more on newsgroups/blogs.  They are already pretty easy to install (just unzip in /usr/share/sword) but what about making a repository for the modules.  That may encourage ubntu users to embrace the sword project more and keep it open source.  Don't get me wrong, I love esword, but I'm all about simplicity, functionality, & am trying to stay open source as much as possible.  Just a suggestion but I'd rather see a better integrated and easily updated gnomesword than running esword in wine.  It would be nice to run apt-get/ automatix/ synaptic and get bible updates too ;)

So tell me what you think and if we can get going on it soon.

BTW, I will host all of my current esword and gnomesword modules soon and post links here for anyone looking for add-ons.

---

### Post by ubuntu27 on 2007-04-12
Gnome Sword can download the modules or plugins automatically within.
I don't rememebr how but, there was an option (preferences ?) to type the URL for the modules, and it will download it for you.

---

### Post by david_kt on 2007-04-12
> **accludetuner said:**
> I've been using esword on windows for a little over a year now and have accumulated over 120 bible versions in english alone, 50+ commentaries, and all kinds of maps, study notes, dictionaries, thesauruses, and so on.  I spent over 3 hours adding them to esword in linux.  While I was in the process of updating it I thought there had to be an easier way to update than manually doing them like this.  Then I thought about maybe adding a repository for bible tool updates and such.

It may be a little more difficult for esword since it's not directly a linux app, but what about gnomesword/bibletime?  

I install Esword manually using this method:
[http://ubuntuforums.org/showthread.php?t=404042]("http://ubuntuforums.org/showthread.php?t=404042")

and I think it is just a few seconds different from installing in windows if you have that how to at hand.

By the way, if you have E-sword in your windows box, what you could do is just copy and paste the whole folder from windows box to linux box, just take a few clicks.

DK

---

### Post by LaserJock on 2007-04-15
> **accludetuner said:**
> It may be a little more difficult for esword since it's not directly a linux app, but what about gnomesword/bibletime?  They are not bad programs at all and being open source should continue to progress nicely.  There's actually plenty of modules available for them at [http://www.crosswire.org/sword/modules/index.jsp](http://www.crosswire.org/sword/modules/index.jsp)  and many more on newsgroups/blogs.  They are already pretty easy to install (just unzip in /usr/share/sword) but what about making a repository for the modules.  That may encourage ubntu users to embrace the sword project more and keep it open source..

There are several Sword modules in the Ubuntu repositories. There are 14 Bible texts (in various languages), 4 commentaries, and 3 dictionaries. Many of those were packages by a few of us in the Ichthux team. Generally they are pretty easy to do. One thing to note though is that not all the Sword modules are distributable in the Ubuntu repositories because of copyright/license issues.

-LaserJock

---

### Post by jonathonblake on 2007-04-25
> **accludetuner said:**
> I've been using esword on windows for a little over a year now and have accumulated over 120 bible versions in english alone.

I am not sure that there are that many English language Bibles for e-Sword that can be legally distributed. I know that there are not 50 English language commentaries for e-Sword that can be legally distributed.

> over 3 hours adding them to esword in linux.  

The fastest/easiest way to install e-Sword resources when migrating systems, is to copy uncompressed modules to the new directory.

>It may be a little more difficult for e-Sword since it's not directly a Linux app, but what about 

A little more difficult?  

I guess it depends upon which e-Sword resources you want to host.

Anything that is, or was at either eStudySources.com, or e-Sword.net is off limits --- copyright and/or licence violations.

The last time I counted, *Currently Available e-Sword Resources* listed 5,000 resources for e-Sword.  
These resources are scattered all over the internet. Uncompressed, you are looking at somewhere around 10 Gigabytes.  Compression using tar and gzip might reduce that to 1.5 or so gigabytes.

I do think that the module installer for e-Sword that Jereme created makes it much easier for users to download the files they want from e-Sword.net.   It probably should be ported to Windows.

>Just a suggestion but I'd rather see a better integrated and easily updated gnomesword than running esword in wine. 

Gnomesword has a feature that allows one to update/install new resources from the main repository of *The Sword Project*   Either it, or BibleTime, or both also allow one to add other repositories.  

xan

jonathon

---

