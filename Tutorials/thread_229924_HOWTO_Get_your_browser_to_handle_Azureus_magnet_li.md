---
title: "HOWTO: Get your browser to handle Azureus magnet links"
date: 2006-08-05
forum: Tutorials
---

### Post by Nick Rivers on 2006-08-05
If you're wondering how to get your browser to handle Azureus magnet links then here's how:

Open a terminal and enter the followuing commands

```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/opt/azureus/azureus %s"
```

```
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
```

```
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true
```

That's it.  Now when you click on an Azureus magnet link in your browser, it will be opened in Azureus.

---

### Post by Haegin on 2006-10-09
Great but the first link has curly quotes so it should be 
```

gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/opt/azureus/azureus %s"

```
with non curly quotes.

---

### Post by Nick Rivers on 2006-12-27
Thanks for catching the typo! I've corrected the code in my original post. :)

---

### Post by leetcharmer on 2007-07-21
> **Human Prototype said:**
> Great but the first link has curly quotes so it should be 
```

gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/opt/azureus/azureus %s"

```
with non curly quotes.

in the quotes, it should prolly just say "azureus %s" ... that's the only thing that made it work for me :D

---

### Post by analog_G on 2007-09-26
I also had trouble using /opt/azureus/azureus %s.
I installed azureus with Synaptic.  Path to azureus on my machine is 
/usr/bin/azureus.
Using the first posted code with "/usr/bin/azureus %s" worked for me.
Thanks for your suggestions.

---

### Post by ko_ko_now on 2009-11-18
thanks, my FF problem fixed ,

i used the:

```
$> which azureus
``` command to find the right path of azureus and replace it to the first command.



-

although i fix the problem...
i have a question, are the commands "vuse" and "azureus" the same?

```

$> which vuze
/usr/bin/vuze

$> which azureus
/usr/bin/azureus

```

---

### Post by Spartan.II.117 on 2009-11-18
This also works for deluge, you just have to change the path to match

---

### Post by trytenn on 2009-11-19
I wrote in wrong thread

---

### Post by greylander on 2009-11-20
Spartan, I tried this with Deluge and it didn't work.  What version of deluge do you have (and how/where did you get it)?

I have deluge 1.1.6 which seems to be the latest available in the normal repositories.  But I think deluge is actually up to 1.2.x.

Even if I try to invoke deluge directly from command line with magnet link as parameter, it just starts deluge and (apparently) ignores the link.  Maybe this is just because deluge 1.1.6 does not support the magnets?

Can you show the exact gconftool command you use for deluge?  Is it like this?

```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/opt/azureus/azureus %s"
```

Is it possible that additional quotes are needed around the %s?


EDIT:  Correction, deluge 1.2.0-rc3 is in the repositories and I just upgraded, but I still can't get it to work.  There are two problems:  (1) deluge starts but apparently does not add the torrent of the magnet link -- maybe I am not seeing because magnet links are handled differently somehow?  (2) if deluge is already running, it appears it starts up a second instance of deluge instead (and still does not start the magnet torrent).

Any idea what I might be doing wrong?

---

### Post by jackhynes on 2009-11-20
Any chance of getting it working in Transmission? Also will this work in Chromium?

---

### Post by kommunisti on 2009-11-20
> **jackhynes said:**
> Any chance of getting it working in Transmission? Also will this work in Chromium?

Transmission doesn't support magnet links, yet. They are planning to include magnet support in the upcoming 1.8 release.

---

### Post by patryk77 on 2010-01-10
Wonderful post, just what I was looking for.

I installed the new Transmission 1.80b4

```
sudo apt-get install build-essential libcanberra-gtk-dev libcanberra-pulse libcanberra-dev libgconf2-dev libnotify-dev libgtk2.0-dev intltool libcurl4-openssl-dev libssl-dev
```

Should install all the dependencies I believe.

Then simply download the latest Beta from [http://www.transmissionbt.com/index.php](http://www.transmissionbt.com/index.php)

```
./configure --prefix=/usr/
make
sudo make install
```

Then simply replace the original command with
```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/transmission %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true
```

And *voilà*!

Your very own Transmission with Magnet Link support ;)

Notice: This is still Beta software. While it is working for me and hasn't crashed so far, your mileage may vary.

Also, notice that I simply overwrote the original installation. This ***IS NOT!!!*** the proper way of doing things if you are not as lazy as I am :-\"

---

### Post by hobo14 on 2010-01-10
> **patryk77 said:**
> Wonderful post, just what I was looking for.

I installed the new Transmission 1.80b4

```
sudo apt-get install build-essential libcanberra-gtk-dev libcanberra-pulse libcanberra-dev libgconf2-dev libnotify-dev libgtk2.0-dev intltool libcurl4-openssl-dev libssl-dev
```

Should install all the dependencies I believe.

Then simply download the latest Beta from [http://www.transmissionbt.com/index.php](http://www.transmissionbt.com/index.php)

```
./configure --prefix=/usr/
make
sudo make install
```

Then simply replace the original command with
```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/transmission %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true
```

And *voilà*!

Your very own Transmission with Magnet Link support ;)

Notice: This is still Beta software. While it is working for me and hasn't crashed so far, your mileage may vary.

Also, notice that I simply overwrote the original installation. This ***IS NOT!!!*** the proper way of doing things if you are not as lazy as I am :-\"

Thanks Patryk, I'm (at least ;) ) as lazy as you, and yours was the perfect solution for my magnet link needs.

---

### Post by freddybob on 2010-01-23
> **greylander said:**
> (1) deluge starts but apparently does not add the torrent of the magnet link -- maybe I am not seeing because magnet links are handled differently somehow?  (2) if deluge is already running, it appears it starts up a second instance of deluge instead (and still does not start the magnet torrent).

Same two problems for me.  Though I notice in Deluge's status bar it says there is one torrent queued.

---

### Post by neilblue on 2010-08-22
Hi,

I got this working using:
```

gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/deluge %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true

```

And latest deluge 1.2.2 from synaptic.

When you add a magnet URL, it is listed as a hash code and then changes to the file name when the download starts.

Hope this helps

Cheers
Neil

---

### Post by heepie on 2012-01-12
Any updates on this with Ubuntu 11.10

It doesn't use gconf anymore but dconf. How to enable magnet links?

---

