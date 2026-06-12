---
title: "Video of a Windows application working within Ubuntu"
date: 2008-05-23
forum: Virtualisation
---

### Post by newbiehardy on 2008-05-23
Hi there,

Here is a video demonstration of how my windows-based charting software works in Hardy Heron using VirtualBox.

It will give newbies a good idea of how VirtualBox operates.

Click on the YouTube video here - [http://www.youtube.com/watch?v=PEIupV0jMIQ]("http://www.youtube.com/watch?v=PEIupV0jMIQ")

Here is a clearer screenshot of both windows and linux applications on the same desktop: [URL="http://img521.imageshack.us/img521/3587/metastockusingvirtualboys5.png"]http://img521.imageshack.us/img521/3587/metastockusingvirtualboys5.png
[/URL]
The software with the blue top bar (Metastock Professional) is a windows application while the ones in brown (innotek VirtualBox) and grey (Firefox 3) are Ubuntu's applications.

While the content is focussed on my charting software, the installation procedure should work for any other Windows XP software.

Hope this information would help those keen to run their windows applications on Ubuntu.

Cheers.

---

### Post by Rhubarb on 2008-05-23
It should be possible to run metastock in wine as well, but may not be good for newbies:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7761&iTestingId=11331](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7761&iTestingId=11331)

---

### Post by newbiehardy on 2008-05-23
I've downloaded the latest version of wine (0.9.59) using Synaptic Package Manager from my Hardy Heron to try to run Metastock. Unfortunately, even though I've readup various ways to install it, I've been unable to get Metastock to work under wine. Perhaps more experienced Ubuntu users can code their way around those problems.

Then I tried using Crossover Standard (trial version). While Metastock can work with it, there are several issues that need to be resolved:

1. At each startup, an error box will appear claiming that the font equis.ttf cannot be found. 

2. The function to include symbols into the charts does not work.

3. The main problem I have is that the syntax of the directory structure is referred to by Metastock. While the data and charting software are contained in the same "bottle", somehow Metastock uses another format to set the directory path for smartcharts and templates. That sometimes included backslashes in the path. So sometimes, I was unable to save of my smartcharts and templates.

But I'm sure that the guys at CrossOver can help users to resolve those problems, given time.

For me, the key issue was one of my data providers included an ActiveX component in his verification process. That totally hung my system when I tried to execute in under CrossOver Standard. That was despite installing IE 6 into that same bottle.

Hence, I had to resort to using VirtualBox instead. I'm very happy with this virtualisation software as everything operates very smoothly in it.

---

### Post by Rhubarb on 2008-05-24
Good points newbiehardy.
To get the latest version of wine, don't use the version that's in the ubuntu repositories.
Instead, winehq has their own updated repository (currently wine 1.0 rc 2 should be available now / soon):
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Getting ActiveX installed by intsalling IE6 can be done AFAIK, but it must be installed in the same ~/.wine directory as metastock is installed in.

Virtualbox is excellent visualization software, but having an XP license seems as though it's a necessary expense + evil for it to work.

---

