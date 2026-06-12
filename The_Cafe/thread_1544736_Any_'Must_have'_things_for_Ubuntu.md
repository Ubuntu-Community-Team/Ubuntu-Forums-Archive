---
title: "Any 'Must have' things for Ubuntu?"
date: 2010-08-02
forum: The Cafe
---

### Post by AmenFPSB on 2010-08-02
I'm honestly not sure where this should go, I apologize if this is the wrong place.

But, are there any must have downloads for Ubuntu?
Be it games, themes/visual things, programs and so on?

I'm new to Ubuntu and LInux all together so I'd really like to know what kind of stuff you all recommend for use. I've seen screenshots of people with really awesome themes, but I have no idea where to look.

---

### Post by drpjkurian on 2010-08-02
Hi
You will have everything which is essential for an average user except in 'alternate version of Ubuntu' series.

---

### Post by jerenept on 2010-08-02
If you want themes, [gnome-look.org]("http://gnome-look.org") is usually a good choice. Just download the theme and install it using "System>Preferences>Appearance"

It is recommended to install the proprietary drivers for NVIDIA and ATi graphics cards,and install the package "fusion-icon"

```
sudo aptitude install fusion-icon
```

---

### Post by WorMzy on 2010-08-02
Everything "must have" for a typical user is included in a default installation. But if you want more themes, take a look at [http://gnome-look.org/]("http://gnome-look.org/").

If you think you're missing something on the software side of things, then open up the Software Centre (Applications -> Software Centre) or Synaptic Package Manager (System -> Administration -> Synaptic Package Manager), and use the search features provided to find software.

---

### Post by Macskeeball on 2010-08-02
If you haven't already done so, click on the Applications menu at the top left and then choose "Ubuntu Software Center." Once you're in the software center, take a look at the featured applications.

I came across this article a while back and found it quite good: ["Ubuntu 10.04 Post-Install Guide: What to do and try after installing Lucid Lynx!"](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

Also, see a thread we have here in The Community Cafe: ["Cool applications you use that others might not know of"](http://ubuntuforums.org/showthread.php?t=382137)


Since you're new to Ubuntu and Linux in general, there's a free PDF book about it: [Ubuntu Pocket Guide](http://www.ubuntupocketguide.com) The author also makes a printed version available for purchase.

---

### Post by darolu on 2010-08-02
Well "must have" stuff deppends on what you do; what kind of work do you usually do when using a computer? any specific area of interest? There are thousands (if not milions) of programs out there, so it's a bit difficult to recommend software if you don't tell us you area of interest.

I suppose you have already installed the necessary libraries to play restrictive formats like mp3, aac or .mov files, if you haven't install Ubuntu-restricted-extras package.

```
sudo apt-get install ubuntu-restricted-extras
```

On the visual-side, you've already been told the basics, compiz (desktop effects) and a good themes site. I strongly recommend installing **CompizConfig Settings Manager** to esasily configure your desktop effects, it is on synaptic or use your terminal:
```
sudo apt-get install compizconfig-settings-manager
```
Don't be affraid to use your command line, you will be a 'terminal-fan'soon.

If you like MacOSX-like Docks install AWN (Avant Window Navigator).

And you mentioned games, there are tons... my personal favourites are Secret Maryo Chronicles, Open Arena, Osmos and Frozen Bubble.

---

### Post by bodhi.zazen on 2010-08-02
> **AmenFPSB said:**
> I'm honestly not sure where this should go, I apologize if this is the wrong place.

Moved to the cafe as this is not a support question.

> But, are there any must have downloads for Ubuntu?
Be it games, themes/visual things, programs and so on?

I'm new to Ubuntu and LInux all together so I'd really like to know what kind of stuff you all recommend for use. I've seen screenshots of people with really awesome themes, but I have no idea where to look.

The answer to that question is dependent on what you intend to do with Ubuntu (Desktop, server, multimedia, etc) and highly personal.

Personally I remove things from a default install of Ubuntu, or use a minimal install and build up.

---

### Post by corrytonapple on 2010-08-02
For making the desktop look nice, I'm writing a How-To. Be looking for it. I'm Almost finished with it. I will post it here. (Lots of "its")

---

### Post by Random_Dude on 2010-08-02
Enable the firewall by typing in the terminal:

```
sudo ufw enable
```To install a GUI to configure your firewall more easily, install GUFW.

```
sudo apt-get install gufw
```
As for games, if you like FPS I recommend openarena.

Cheers :cool:


P.S. I've always wondered: Why isn't UFW enabled by default? Is there a special reason?

---

### Post by SunnyRabbiera on 2010-08-02
I would say Ubuntu Tweak, because it will help fetch multimedia codecs if you are unsure how plus it offers many features for the system.
VLC, the swiss army knife multimedia player
smplayer, anotgher swiss army knife player
nautilus elementary
and playonlinux

---

### Post by Zorgoth on 2010-08-02
cairo-dock :)

---

### Post by Legendary_Bibo on 2010-08-03
Cairo-Dock
Gnomenu
Compiz
Emerald Themes if you'd like
Ubuntu Tweak (it makes it easier to change the login screen stuff)
Get some new icons, cursors, and what not from Gnome-look.org, and you can also get some new themes (albeit limited) through the appearance settings.
I recommend the Bisigi themes. They're very nice to start out with. I have a mix of the Aquadreams with Airlines. It looks nice.

---

### Post by corrytonapple on 2010-08-03
I have submitted my How-To: It should be coming out soon. (Two or three days)

---

### Post by Khakilang on 2010-08-04
I guess its the Kernel or else it won't boot.

---

### Post by aeiah on 2010-08-04
> **Random_Dude said:**
> 
P.S. I've always wondered: Why isn't UFW enabled by default? Is there a special reason?


ive used ubuntu for a few years in various circumstances (including servers) and ive never had a reason to mess with firewalls in normal situations, because routers and gateways provide that for me. i just turn on the services i need (http, ssh) and create routing rules on the router/firewall. that's probably why it's off by default.

---

### Post by Random_Dude on 2010-08-04
> **aeiah said:**
> ive used ubuntu for a few years in various circumstances (including servers) and ive never had a reason to mess with firewalls in normal situations, because routers and gateways provide that for me. i just turn on the services i need (http, ssh) and create routing rules on the router/firewall. that's probably why it's off by default.

But for the regular non-expert everyday desktop user it wouldn't hurt to have it enable by default right? I mean, only after I googled arround I discovered that my firewall wasn't enabled and that I just needed to do:

```
sudo ufw enable
```

I mean, it's not hard to activate it, but for noob protection it should be enabled by defauld IMHO.

Cheers :cool:

---

