---
title: "Hostname thread"
date: 2016-11-29
forum: The Cafe
---

### Post by ArgentWarrior on 2016-11-29
How do you come up with names for your computers? Do you have a naming scheme or do you just make something up?

I started naming my computers after provinces of Tamriel from the Elder Scrolls, and if I compile a custom kernel for the machine I name it after a faction native to the game that province was in. My laptop is "skyrim" with kernel version "Linux 4.8.10-stormcloak", my workstation is "morrowind" with kernel version "Linux 4.8.10-moragtong", my Solaris server is "cyrodiil", and my Dragonfly BSD box is "hammerfell". Which is kind of ironic because of Dragonfly's HAMMER filesystem.

---

### Post by TheFu on 2016-11-29
astronomical stuff (qbe, regulus, romulus, icarus, hadar ...)
superheros (batman, robin, superman, batgirl ...)
tv-characters (marvin, mred, lucy, sheldon ...)
Mexican related foods (burrito, enchilada, jalapeno, guacamole, fajitas ... )

That last set happened when some new servers arrived and everyone was hungry for lunch. ;)

Sometimes it is just the name on the case - dell, istar, nokia, rpi, 

If I'm doing hundreds of servers, it would be {purpose}-0001 .... -9999.  That way Ansible can manage them with 1 line in the inventory file.

Since we use DNS, the hostname isn't really what most people use anyway.  It is the DNS service-name that gets used: mail, spam, blog, pm, wallabag, nextcloud - plus with tab completion, we don't have to type all those names completely. Usually just the first few characters and tab fills it in.

---

### Post by &amp;KyT$0P# on 2016-11-29
For my VMs I use a script to generate a random pronounceable "word" of certain length.  Then I keep generating these "words" until it produces something I sort of like.  :mrgreen:

---

### Post by yetimon_64 on 2016-11-29
> **ArgentWarrior said:**
> How do you come up with names for your computers? Do you have a naming scheme or do you just make something up?...

I usually use a pretty unimaginative combination of the Linux/Ubuntu version in use and the machine brand/model or a general hardware description (if on my non branded desktop tower). For example the desktop might have a hostname of trusty-desktower or deb8stable-desktower to describe the release in use on the specific hardware. My laptop being a "HP" machine has trusty-HP-laptop or xenial-HP-laptop etc (or something very much like that).

Because I usually dual boot multiple Linux installs such an unimaginative (but system descriptive) system is easy to ID which set up I'm using at any particular time and can at times save me confusion as to what system I'm dealing with. My laptop dual boot system is pretty simple at the moment with only a trusty and a xenial install currently running, but in the past I've had up to seven Linux installs on the one hard drive at a time and such a naming scheme can certainly help with keeping track of where I'm running from.

One other thing, related to identifying multiple installs with the hostname, I use is to have conky display such a descriptive hostname with the "$nodename_short" conky functionality. That way I can easily view the current hostname in use from the desktop. Just have to remember to load the conky profile with such info blanked out when posting screenshots online etc. I have conky set up to reload a "redacted" version using a mouse gesture and a bit of scripting that rewrites and then reloads the ~/.conkyrc file to what I need shown only ("masking" the hostname, LAN IP and WAN IP etc) :).

---

### Post by SantaFe on 2016-11-30
I usually use characters from Looney Tunes.  For Example, my current computer's called George.
> 
  Hugo the Abominable Snowman: [holding Daffy, whose shirt makes him look like a rabbit] Oh, what a cute little pink bunny rabbit! 
 [cradling Daffy] 
Hugo the Abominable Snowman:Just what I always wanted. My own little bunny rabbit. I will name him  George, and I will hug him and pet him and squeeze him... 
 Daffy Duck: I'm not a bunny rabbit... 
Hugo the Abominable Snowman:...and pat him and pet him and... 
Daffy Duck: You're hurting me. Put me down, please. 
Hugo the Abominable Snowman:...and rub him and caress him and... 
Daffy Duck:   I AIN'T NO BUNNY RABBIT! 


---

### Post by kpatz on 2016-11-30
My naming schemes have changed over the years and were almost never consistent.

My very first firewall box I built using some ancient Slackware distro from circa 2000 I simply called "linux1" since it was my first and (at the time) my only Linux box.

My next firewall box, and my first Ubuntu box I named zuul, as in Zuul the Gatekeeper from Ghostbusters.  I figured it was an apt name for a firewall.

In 2015, I retired Zuul and built a new firewall box, which I named mordac, after "Mordac, the Preventer of Information Services" from the Dilbert comic strip.

My Mythbuntu box is simply called "mythtv."

My first file server I named Quattro, because I had an Audi at the time plus it had a quad core CPU, and 4 hard drives in a RAID configuration.

For my new file server, I adopted a more "formal" naming scheme: catzfs01.  catz is a play on my last name plus the fact that I love cats, and will be the prefix for all servers in the future.  fs = file server, 01 is the first file server.  If I build another in the future, it'll be catzfs02.  Quattro was repurposed as a backup for catzfs01, so I named it catzbs01.  Using this naming scheme allows my backup scripts to know what backup server goes with which file server.

VMs typically get a name starting with "vm" and some descriptor related to the OS running on it, such as "vmtest1604" for a test VM running Ubuntu 16.04.

Windows systems have had a varying naming scheme as well.  I used to name my laptops after my cats.  Now I use the brand and some unique number, like "Asus10" (Asus laptop with windows 10) or "Pavilion2014" (a HP Pavilion purchased in 2014).

---

### Post by nmccrina2 on 2016-12-07
I actually just changed my scheme. I used to name my computers after mathematicians (Euler, Gauss, etc.). However, a couple of weeks ago I picked up my Norton's Anthology of English Literature and was flipping through that while installing some OS or other and decided to mix it up and use the names of poets. Currently my desktop is Wordsworth and my laptop is Blake.

---

### Post by Jeroen_Mathon on 2016-12-07
The main server of my network is called core.n0xy.net

---

### Post by user1397 on 2016-12-08
I don't know why I never got creative with this...I always just used something descriptive but boring like "user1397-laptop" or "xubuntu-acer".  You just got me thinking though...perhaps I'll follow your style, but with Middle-earth names instead of Tamriel :)

---

### Post by euphoricmini on 2016-12-09
I use names from popular scifi TV series. Currently on a Kevin Sorbo kick, so my entire home network is based on the various ships from the show Andromeda.

---

### Post by v-mark-5 on 2016-12-11
For my personal laptops/desktops I use:

<my-name>-<device-model-number>

Like: mark-dell-xps

For my servers I just use location and a number squence:

uk1
uk2
ny1
ny2

---

### Post by MechaMechanism on 2016-12-12
Greek gods, like triton.  Or frontier or after my dead father jim or james.  Some have my domain name as the host name, domain.tld.

---

