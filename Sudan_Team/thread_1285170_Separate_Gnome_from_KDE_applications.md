---
title: "Separate Gnome from KDE applications"
date: 2009-10-07
forum: Sudan Team
---

### Post by zero-n on 2009-10-07
If you are using Gnome as a default Desktop environment or you are using KDE, when you install Kubuntu-desktop or ubuntu-desktop packages all application Gnome & KDE are merged together if you don't like it that way you can use this program:

 [COLOR="Red"][[COLOR="Red"]_**Gnome Menu Extended**_[/COLOR]]("http://linux.softpedia.com/progDownload/Gnome-Menu-Extended-Download-34178.html")[/COLOR] 

it works on Gnome & KDE

---

### Post by mhmdfoss on 2009-12-13
mix of tow environments apps make headache reallllly thank you

---

### Post by zero-n on 2009-12-14
Sorry i have missed something the above application will work only on Gnome & not KDE.

But there is no problem for KDE you can use **[COLOR="Red"]K Menu Gnome[/COLOR]**.

**[COLOR="Red"][Download]("http://www.kde-apps.org/CONTENT/content-files/31031-kmenu-gnome_1.2.2-1_all.deb")[/COLOR]**

[COLOR="red"]**[Screenshot 1]("http://www.kde-apps.org/content/preview.php?preview=2&id=31031&file1=31031-1.png&file2=31031-2.png&file3=31031-3.png&name=K+Menu+Gnome+(Debian+package)&PHPSESSID=f899313bd19ada2425f6211853144292")**[/COLOR]
[COLOR="red"]**[Screenshot 2]("http://www.kde-apps.org/content/preview.php?preview=3&id=31031&file1=31031-1.png&file2=31031-2.png&file3=31031-3.png&name=K+Menu+Gnome+(Debian+package)&PHPSESSID=f899313bd19ada2425f6211853144292")**[/COLOR]
**[COLOR="red"][Screenshot 3]("http://www.kde-apps.org/content/preview.php?preview=1&id=31031&file1=31031-1.png&file2=31031-2.png&file3=31031-3.png&name=K+Menu+Gnome+(Debian+package)&PHPSESSID=f899313bd19ada2425f6211853144292")[/COLOR]**

---

### Post by mhmdfoss on 2009-12-14
perfect work mr ZERO

THANKS

---

### Post by bowens44 on 2009-12-14
I've been using this for awhile now, it's a great solution.

---

### Post by ejlal on 2009-12-14
> **zero-n said:**
> Sorry i have missed something the above application will work only on Gnome & not KDE.

But there is no problem for KDE you can use **[COLOR=Red]K Menu Gnome[/COLOR]**.

**[COLOR=Red][Download]("http://www.kde-apps.org/CONTENT/content-files/31031-kmenu-gnome_1.2.2-1_all.deb")[/COLOR]**

[COLOR=red]**[Screenshot 1]("http://www.kde-apps.org/content/preview.php?preview=2&id=31031&file1=31031-1.png&file2=31031-2.png&file3=31031-3.png&name=K+Menu+Gnome+%28Debian+package%29&PHPSESSID=f899313bd19ada2425f6211853144292")**[/COLOR]
[COLOR=red]**[Screenshot 2]("http://www.kde-apps.org/content/preview.php?preview=3&id=31031&file1=31031-1.png&file2=31031-2.png&file3=31031-3.png&name=K+Menu+Gnome+%28Debian+package%29&PHPSESSID=f899313bd19ada2425f6211853144292")**[/COLOR]
**[COLOR=red][Screenshot 3]("http://www.kde-apps.org/content/preview.php?preview=1&id=31031&file1=31031-1.png&file2=31031-2.png&file3=31031-3.png&name=K+Menu+Gnome+%28Debian+package%29&PHPSESSID=f899313bd19ada2425f6211853144292")[/COLOR]**

thank you zero-n!
i downloaded K Menu Gnome and the menus look nice and tidy
but i wonder if there is any fix for the system confusion between kubuntu/ubuntu when it starts up?...because it took longer time and its really annoying
am using karmic btw and my default desktop is gnome

---

### Post by zero-n on 2009-12-14
try this :

1- Download [COLOR="Red"]**Startup-Manager**[/COLOR].

```
sudo apt-get install startupmanager
```

2- Open startup-manager :  System >> Administrations >> StartUp-Manager

3- In StartUp-Manager go to [COLOR="red"]**Appearance**[/COLOR] tab.

4- In the bottom you will find Usplash Theme drop down menu , change it to [COLOR="red"]**usplash-theme-ubuntu**[/COLOR]

5- We are done & the startup Usplash logo should change to Ubuntu logo instead of Kubuntu logo.


StartUp-Manager is a very helpful tool try to look at other options.
I hope this will work for you

---

### Post by ejlal on 2009-12-15
hey
@zero-n thanks 
i installed startup manager but nothing changed i guess i wasn't clear when i described my problem
so here it is....
when i start up my laptop i got a screen showing that kubuntu is loading and when this one  finish i got another screen showing that ubuntu is loading too(those are the splash screens right?) then i got the screen at which i got to choose which user want to log-in and the desktop  to use..
any ideas?

---

### Post by zero-n on 2009-12-15
In karmic koala they replace Usplash with Xsplash so my above answer won't work for you.

till now i can't help but i will still googling until i find a soultion



if you have a problem try to post it in new post ;)

because of the title so anyone can use our solution if we find it.

---

### Post by pritamps on 2009-12-30
You just uninstall kubuntu-artwork-usplash package (or reinstall the ubuntu one if you don't want to uninstall this one). That will replace the splash screens.

---

