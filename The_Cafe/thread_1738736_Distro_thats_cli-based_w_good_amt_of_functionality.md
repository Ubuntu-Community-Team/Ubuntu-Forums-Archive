---
title: "Distro thats cli-based w/ good amt of functionality"
date: 2011-04-25
forum: The Cafe
---

### Post by user1397 on 2011-04-25
I remember seeing some distro a while ago that was all cli-based (no GUI whatsoever) but it had a decent amount of functionality for an average user.  It had a browser, media player, some games, etc

Anyone know what I'm talking about?

---

### Post by NormanFLinux on 2011-04-25
Its spare but newbies don't like cli. Its boring. I remember it from the DOS days. Terminals can access it and do you really want a glorified terminal with a blinking cursor and a black screen?

---

### Post by user1397 on 2011-04-25
> **NormanFLinux said:**
> Its spare but newbies don't like cli. Its boring. I remember it from the DOS days. Terminals can access it and do you really want a glorified terminal with a blinking cursor and a black screen?

I much prefer GUIs to command lines, I just thought this concept was cool that's all

---

### Post by Paqman on 2011-04-25
It wouldn't be at all hard to make your own, if you knew what apps you wanted. Just use the Alternate or Minimal image and install a command line system, then apt-get whatever packages you wanted. Job done.

---

### Post by user1397 on 2011-04-25
> **Paqman said:**
> It wouldn't be at all hard to make your own, if you knew what apps you wanted. Just use the Alternate or Minimal image and install a command line system, then apt-get whatever packages you wanted. Job done.

I just don't know the names of the best cli apps, except for w3m or links2.  I know there's a distro out there already pre-configured, I just can't find it! :(

---

### Post by Lucradia on 2011-04-25
> **ubuntuman001 said:**
> I just don't know the names of the best cli apps, except for w3m or links2.  I know there's a distro out there already pre-configured, I just can't find it! :(

finch is a CLI based Pidgin (Doesn't need gconf due to lack of proxy features.)

---

### Post by Spice Weasel on 2011-04-25
> **NormanFLinux said:**
> Its spare but newbies don't like cli. Its boring. I remember it from the DOS days. Terminals can access it and do you really want a glorified terminal with a blinking cursor and a black screen?

The bare CLI is a glorified terminal with a blinking cursor and black screen, but there is a little thing known as the framebuffer:

[http://soucali.com/pspnews/modules/mydownloads/images/shots/PSPRadio_links2.png]("http://soucali.com/pspnews/modules/mydownloads/images/shots/PSPRadio_links2.png")

(web browsing with graphics outside of X with links)

You can even play movies in the framebuffer with mplayer.

Of course, newbies would want a X11 GUI, but some people don't need that.

---

### Post by Lucradia on 2011-04-25
> **Spice Weasel said:**
> The bare CLI is a glorified terminal with a blinking cursor and black screen, but there is a little thing known as the framebuffer:

[http://soucali.com/pspnews/modules/mydownloads/images/shots/PSPRadio_links2.png]("http://soucali.com/pspnews/modules/mydownloads/images/shots/PSPRadio_links2.png")

(web browsing with graphics outside of X with links)

You can even play movies in the framebuffer with mplayer.

Of course, newbies would want a X11 GUI, but some people don't need that.

Framebuffer a package? Or code implementation in only some programs?

---

### Post by Pogeymanz on 2011-04-25
I think there was a distro call INX that is what you are looking for. It's pretty cool, from the five minutes that I played with it.

---

### Post by user1397 on 2011-04-25
> **Pogeymanz said:**
> I think there was a distro call INX that is what you are looking for. It's pretty cool, from the five minutes that I played with it.

Ah, I think this was it, but I'm not sure, I'll have to check it out myself.

---

### Post by Paqman on 2011-04-25
> **ubuntuman001 said:**
> I just don't know the names of the best cli apps, except for w3m or links2.  I know there's a distro out there already pre-configured, I just can't find it! :(

Hmm, if you don't know what the apps are called, you might struggle to use them on a command line ;)

---

### Post by 3Miro on 2011-04-25
Get Ubuntu alternate install and then press F3 on the first screen (where you choose "Install or Test CD"). Then you can install a CLI only version of Ubuntu.

I have seen similar options in Slackware

Arch and Gentoo also install CLI and let you add graphics (if you want to).

---

### Post by user1397 on 2011-04-25
I guess I wasn't clear enough in my first post but I just wanted to see if anyone knew of an existing distro like that.

I know I can use a minimal ubuntu install or any number of other distros as a base and build a cli-only distro myself, but that is not my intent.  I just wanted to find that distro again, and check it out a bit

---

### Post by Lucradia on 2011-04-25
> **ubuntuman001 said:**
> I guess I wasn't clear enough in my first post but I just wanted to see if anyone knew of an existing distro like that.

I know I can use a minimal ubuntu install or any number of other distros as a base and build a cli-only distro myself, but that is not my intent.  I just wanted to find that distro again, and check it out a bit

Nope.avi

---

### Post by user1397 on 2011-04-25
> **Lucradia said:**
> Nope.avi
?

---

### Post by jeffathehutt on 2011-04-25
I'm not sure what distro you are looking for, but perhaps [this list]("http://distrowatch.com/search.php?category=All&origin=All&basedon=All&notbasedon=None&desktop=No+desktop&architecture=All&status=Active") might be helpful?  That is most of the active distributions on distrowatch that do not include a desktop. :)

---

### Post by ikt on 2011-04-25
> **jeffathehutt said:**
> I'm not sure what distro you are looking for

It was INX:

[http://inx.maincontent.net/](http://inx.maincontent.net/)

---

### Post by user1397 on 2011-04-26
i guess it was inx the one i'm talking about, guess ill mark this as solved

---

### Post by Primefalcon on 2011-04-26
A command line browser thats pretty good in terms of functionality is lynx

---

### Post by nothingspecial on 2011-04-26
To enable the framebuffer

```
sudo -i
mkdir -p /etc/udev/my-rules.d/
echo 'KERNEL=="fb0",  OWNER="root", MODE="0660"' > /etc/udev/my-rules.d/framebuffer.rules
exit
sudo usermod -a -G video $USER
sudo reboot
```

---

### Post by snowpine on 2011-04-26
Some good CLI tutorials and application suggestions on this site:

[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

INX was kind of cool, definitely served its niche well.

---

### Post by marshag63 on 2011-04-26
+++++1 INX!

Tutorials, menus to do things right off the bat like connect to your wireless router via Ceni, fire up text webbrowser like Elinks and surf the web (try going to the [www.shoutcast.com](www.shoutcast.com) and finding a station you want to listen to, open the link and playinx will play it for you), browse your harddrive, usb or network files, IRC chat, email,text editing, you can even view pictures and watch a short animated movie in the framebuffer.  Run it in a virtual box or install to a USB stick. There are also a couple of games and network monitoring.  A very good introduction to basic concepts.

Learn the power of apt-cache search and apt-cache show.

MDG

---

