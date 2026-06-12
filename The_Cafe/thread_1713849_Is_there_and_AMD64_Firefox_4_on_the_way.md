---
title: "Is there and AMD64 Firefox 4 on the way?"
date: 2011-03-24
forum: The Cafe
---

### Post by Legendary_Bibo on 2011-03-24
I went to see if there was an update for FF on my Linux computer yesterday, and there wasn't, but I read that you could get it by adding the PPA which I did and then found the package firefox-4.0 which I installed which to my surprise turned out to be called Minefield and was only a 4.0 beta (which is fine), but when I went to the page to get the official FF release all they had was an i686 version which will run with the ia-32 thingy, but test looks atrocious, and for some reason flash doesn't work. Right now Minefield 4.0 is behaving very well at least and for once scrolling works right even on 4chan! :) which is why I started using Opera because it was the only browser where scrolling didn't suck. I would like to have an official release, but this beta is fine too. On a side note, for some reason the Firefox menu button isn't there unless I use an add on called 'hide menubar'. I'm loving the speed improvement, and the minimalistic appearance with all the functionality I loved about FF. Also, Mozilla please stop changing the location of the buttons.

---

### Post by NightwishFan on 2011-03-24
This covers it better than I could: [http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/](http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/)

I prefer the terminal way at the bottom. Much easier.

[QUOTE="omgubuntu.co.uk"]To do this, open up the Ubuntu Software Center, head to Edit > Software Sources and click the &#8216;Other Software&#8217; tab. Press &#8216;Add&#8217; and then paste ppa:mozillateam/firefox-stable into the relevant field.

After adding the PPA you will be prompted to update your sources. Once done you can head to System > Administration > Update Manager to perform an upgrade

Alternatively you can do the above via the Terminal (Applications > Terminal).  Just enter the following two commands separately, entering your password when asked: -[/QUOTE]

```
sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Lucradia on 2011-03-24
Firefox 5 will also have 64-bit windows build avail. But of course, flash won't work for it, since adobe doesn't have x64 flash for windows.

---

### Post by Quadunit404 on 2011-03-24
> **Lucradia said:**
> Firefox 5 will also have 64-bit windows build avail. But of course, flash won't work for it, since adobe doesn't have x64 flash for windows.

[Um, yes they do.]("http://labs.adobe.com/technologies/flashplayer10/square/") It's currently just a preview version, though.

---

### Post by Legendary_Bibo on 2011-03-24
> **NightwishFan said:**
> This covers it better than I could: [http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/](http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/)

I prefer the terminal way at the bottom. Much easier.



```
sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get upgrade
```

I'm led to believe that I added the wrong PPA considering how I now have Firefox 3.6.17pre which is called Namaroko. I will have to do this.

---

