---
title: "How to manage themes for unity"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by palimmo on 2012-04-23
Hi!
I would like to try different themes for unity.
I've read that gtk3 themes are the right ones.
Hence I've tried some new ones from gnome-look, extract them in folder \home\.themes
and then chose with Myunity.
But they are always terrible...
Is there something wrong I did?
gtk3-engines-unico is installed.

thanks!

---

### Post by Frogs Hair on 2012-04-23
Even though it is not required I would log out and in after selecting the theme. I use the Gnome Tweak Tool/Advanced settings instead of Myunity, so I don't know if that is the cause. I have noticed Unity 3D is a bit fussy when changing themes. If using The Gnome shell use only Gnome 3.4 themes.

---

### Post by palimmo on 2012-04-23
> **Frogs Hair said:**
> Even though it is not required I would log out and in after selecting the theme. I use the Gnome Tweak Tool/Advanced settings instead of Myunity, so I don't know if that is the cause. I have noticed Unity 3D is a bit fussy when changing themes. If using The Gnome shell use only Gnome 3.4 themes.

Ok. I'll try logging out and then in again.

Gnome tweak tool.. it doesn't show automatically new folders present in \.themes...

---

### Post by Peter09 on 2012-04-23
Slightly of topic. I have started to used the Mono themes - such as 
 
[http://iloveubuntu.net/awoken-22-token-icon-theme-released-numerous-new-icons-and-extended-support](http://iloveubuntu.net/awoken-22-token-icon-theme-released-numerous-new-icons-and-extended-support)
 
I find that the normal icon set - which consists of lot of colours is rather garish. Having my major applications in a mono theme is much more peaceful :p
 
Only problem is running an app which has a normal Icon - it sticks out like a sore thumb.

---

### Post by Baldrick_NZ on 2012-04-23
> **Frogs Hair said:**
> Even though it is not required I would log out and in after selecting the theme. I use the Gnome Tweak Tool/Advanced settings instead of Myunity, so I don't know if that is the cause. I have noticed Unity 3D is a bit fussy when changing themes. If using The Gnome shell use only Gnome 3.4 themes.

I find Ubuntu Tweak seems to be easier to use and has more options, not in repos but can be found by googling 'ubuntu tweak'. :-)

---

### Post by palimmo on 2012-04-24
Could you, please, show some themes that you were able to apply successfully?

---

### Post by cottfcfan on 2012-04-24
Palimmo..
There aren't that many themes available at the moment compatible with gnome 3.4.
[http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=167](http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=167)
Mediterranean night
Orion
Malys-unisex
are 3 that I have found.
Personally I extract them to /usr/share/themes, then use ubuntu tweak to set them.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by palimmo on 2012-04-24
> **cottfcfan said:**
> Palimmo..
There aren't that many themes available at the moment compatible with gnome 3.4.
[http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=167](http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=167)
Mediterranean night
Orion
Malys-unisex
are 3 that I have found.
Personally I extract them to /usr/share/themes, then use ubuntu tweak to set them.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

thanks! Does it mean that I should use only themes for >= gnome 3.4?

---

### Post by Dngrsone on 2012-04-24
Are there any decent themes that do not have white?  I do not like white, especially since I do a lot of my computering in the dark.

---

### Post by Frogs Hair on 2012-04-24
> **Baldrick_NZ said:**
> I find Ubuntu Tweak seems to be easier to use and has more options, not in repos but can be found by googling 'ubuntu tweak'. :-)

Already installed .

---

### Post by Frogs Hair on 2012-04-24
There is a list of 3.4 themes on this thread which has grown a little bigger since posted . [http://ubuntuforums.org/showthread.php?t=1953322](http://ubuntuforums.org/showthread.php?t=1953322)

---

### Post by cottfcfan on 2012-04-24
> **palimmo said:**
> thanks! Does it mean that I should use only themes for >= gnome 3.4?
Yes, if you're using 12.04, then only gnome 3.4 themes are compatible.

---

### Post by palimmo on 2012-04-24
> **cottfcfan said:**
> Yes, if you're using 12.04, then only gnome 3.4 themes are compatible.
thanks!

---

### Post by palimmo on 2012-04-24
Well... there's something wrong with my machine.
I've tried this theme
[http://gnome-look.org/content/show.php/Zukitwo?content=140562](http://gnome-look.org/content/show.php/Zukitwo?content=140562)
and it is 3.4.
I used MyUnity and I've logged off/in and this is the result.
(I obtained always something like this.. I've tried several different themes...)

---

### Post by cottfcfan on 2012-04-24
Have you install the gtk engines as shown on the page?
```
sudo apt-get install gtk2-engines-murrine gtk2-engines-pixbuf
```

Also you may have to change your icon theme to suit.

---

### Post by palimmo on 2012-04-24
> **cottfcfan said:**
> Have you install the gtk engines as shown on the page?
```
sudo apt-get install gtk2-engines-murrine gtk2-engines-pixbuf
```

Also you may have to change your icon theme to suit.

```
gtk2-engines-murrine is already the newest version.
gtk2-engines-pixbuf is already the newest version.
```

:confused:

---

### Post by cottfcfan on 2012-04-25
What folder are you extracting the Themes to??

---

### Post by palimmo on 2012-04-25
> **cottfcfan said:**
> What folder are you extracting the Themes to??

home\.themes

---

### Post by cottfcfan on 2012-04-25
Try extracting them to /usr/share/themes
That may solve your problem.

---

### Post by zombifier25 on 2012-04-25
I thought there is no difference between ~/.themes and /usr/share/themes except for the availability of the themes. I extract all my themes to ~/.themes and found no problem.

---

### Post by cottfcfan on 2012-04-25
I think /usr/share/themes, makes the theme system wide, were /home/.themes is user specific.
Not too sure though, someone may correct me.

---

### Post by palimmo on 2012-04-25
I think I could not have some packages....
Have you any idea?

---

### Post by cottfcfan on 2012-04-25
when I can get on gnomelook.org, i'll try the latest Zukitwo theme myself.
The website appears to be down at the moment.
I can't see why you would be missing any packages.
Have you tried putting the themes in /usr/share/themes?

---

### Post by palimmo on 2012-04-26
I've tried to extract the theme Zukitwo in usr/share/themes and open it with MyUnity.
Well... same problem and same orrible result...
 :(

---

