---
title: "apt-get/synaptic bandwidth limiting (mini-HOWTO)"
date: 2005-03-16
forum: Tutorials
---

### Post by francesc on 2005-03-16
I'm sure many of you miss an option to limit the donwload-rate in apt-get, it's quite useful if you share bandwidth, ... so I decided to write a mini-HOWTO about it.

Download bandwidth limiting can be accomplished using trickle (an user-space bandwidth shaper) with the http and ftp file retrieval "plug-ins" of apt.

First of all you have to install trickle, then you have to make apt-get use trickle for downloads, for example with the http method :

dpkg-divert --local --rename /usr/lib/apt/methods/http
echo '#!/bin/sh' > /usr/lib/apt/methods/http
echo '/usr/bin/trickle -s -d 25 /usr/lib/apt/methods/http.distrib' >>  usr/lib/apt/methods/http
chmod 755 /usr/lib/apt/methods/http

Repeat this process for the ftp method (if you have any ftp repository) replacing http for ftp.

The "-d 25" sets the rate-limit to 25KB/s. You may want to remove the -s/-d switches and configure trickled.

If you want to remove it:

rm /usr/lib/apt/methods/http
dpkg-divert --local --remove /usr/lib/apt/methods/http

---

### Post by tkiesel on 2005-03-29
[QUOTE=francesc]
dpkg-divert --local --rename /usr/lib/apt/methods/http
echo '#!/bin/sh' > /usr/lib/apt/methods/http
echo '/usr/bin/trickle -s -d 25 /usr/lib/apt/methods/http.distrib' >>  usr/lib/apt/methods/http
chmod 755 /usr/lib/apt/methods/http
[/QUOTE]

Executing the first line works just fine, with the consequence that /usr/lib/apt/methods/http disappears and /usr/lib/apt/methods/http.distrib appears. However, when trying to execute the second line, the fact that /usr/lib/apt/methods/http no longer exists gets in the way.

```
tkiesel@gecko:~ $ sudo echo '#!/bin/sh' > /usr/lib/apt/methods/http
bash: /usr/lib/apt/methods/http: Permission denied
```

I'm hoping to make my apt play nice with my MMORPG gaming brother-in-law, and would very much like getting this to work.  :)

---

### Post by deathburger on 2005-03-30
[i]```
tkiesel@gecko:~ $ sudo echo '#!/bin/sh' > /usr/lib/apt/methods/http
bash: /usr/lib/apt/methods/http: Permission denied
```[/i]

Try 'sudo bash' first? Some things seem to like to work only when you've got a root shell.

---

### Post by enbuyukfener on 2008-02-23
Thanks for this.

For those having issues, switch to the root user before running this to make things easier.

At the console:
```
su
>Password: *****
```

Also, on the 3rd line, you might want to change the path at the end to /usr/lib/apt/methods/http (note the slash at the start). This is assuming most will run the commands from their home directory.

---

### Post by bwhite82 on 2008-02-23
Tiny correction, on Ubuntu systems, I belive the command has to be:

> sudo su

---

### Post by gsmanners on 2008-02-24
Another thing that would work is to make a shortcut with this command:

> trickle -s -d 25 gksu synaptic

---

### Post by Mithrilhall on 2008-02-24
You could also try Wondershaper and if you're looking for something with more features you can go with MasterShaper.

[http://lartc.org/wondershaper/](http://lartc.org/wondershaper/) - Available via apt-get

[www.mastershaper.org/](www.mastershaper.org/)

---

### Post by tkmunzwa on 2008-08-14
> **francesc said:**
> 
dpkg-divert --local --rename /usr/lib/apt/methods/http
echo '#!/bin/sh' > /usr/lib/apt/methods/http
echo '/usr/bin/trickle -s -d 25 /usr/lib/apt/methods/http.distrib' >> usr/lib/apt/methods/http
chmod 755 /usr/lib/apt/methods/http


For me, the second line was failng with a "File not found" error, then I noticed the path is missing the initial '/'

All in all, tt should be
```
sudo su
dpkg-divert --local --rename /usr/lib/apt/methods/http
echo '#!/bin/sh' > /usr/lib/apt/methods/http
echo '/usr/bin/trickle -s -d 25 /usr/lib/apt/methods/http.distrib' >>  **/usr/lib/apt/methods/http**
chmod 755 /usr/lib/apt/methods/http

```

The traffic shaping is working brilliantly for me. Previously, my hardy box at the office was clobbering the bandwidth on every update, the boss was not very pleased.

---

### Post by airtonix on 2008-08-14
```
 			 				trickle -s -d 25 sudo gnome-terminal
```

> You could also try Wondershaper and if you're looking for something with more features you can go with MasterShaper.

Havent tried mastershaper, walthough i did try wondershaper when two of us were playing mmorpgs in a house of 5 that all used the net, we resorted to squid.

---

### Post by michallo on 2008-10-19
I've found better sollution on internet. 
Create /etc/apt/apt.conf.d/76download file with content:
Acquire
{
Queue-mode "access";
http
{
Dl-Limit "25";
};
};

After that apt-get will be limited to 25KB/s

---

### Post by gmoon on 2009-04-12
Don't reinvent a square wheel, when we already have a full-feature one built into apt:

[http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg01872.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg01872.html)

```
# cat /etc/apt/apt.conf.d/76download
Acquire
{
        Queue-mode "access";
        http
        {
                Dl-Limit "65";
        };
};
```

All we need is an option added to synaptic that allows tweaking this value.

If you want to see this option added to Synaptic, go vote here:
[http://brainstorm.ubuntu.com/idea/17981/](http://brainstorm.ubuntu.com/idea/17981/)
[http://brainstorm.ubuntu.com/idea/13051/](http://brainstorm.ubuntu.com/idea/13051/)

---

### Post by Dooglus on 2010-03-30
I have a bunch of machines here all running ubuntu.  I use a package called 'apt-cacher' to make sure each update is only downloaded once and shared between all the computers that want it.  The first computer to request a package triggers a download, and all the rest that request it later get the same copy, from apt-cacher's cache.

That makes things faster and reduces the amount of data I transfer from the ISP.  Useful especially when new releases arrive - it means I only download the 700MB of new packages one time.

It also has this setting in the config file:

# Rate limiting sets the maximum bandwidth in bytes per second to use
# for fetching packages.

Hope that helps.

Chris.

---

### Post by s4ms3milia on 2011-06-03
> **gmoon said:**
> Don't reinvent a square wheel, when we already have a full-feature one built into apt:

[http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg01872.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg01872.html)

```
# cat /etc/apt/apt.conf.d/76download
Acquire
{
        Queue-mode "access";
        http
        {
                Dl-Limit "65";
        };
};
```

All we need is an option added to synaptic that allows tweaking this value.

If you want to see this option added to Synaptic, go vote here:
[http://brainstorm.ubuntu.com/idea/17981/](http://brainstorm.ubuntu.com/idea/17981/)
[http://brainstorm.ubuntu.com/idea/13051/](http://brainstorm.ubuntu.com/idea/13051/)

This was very helpful. Been looking for this for some time now, works awesome :).

---

### Post by sinisterstuf on 2012-02-10
I'm a bit late to the party but in case anybody else stumbles upon this thread you can actually just:[INDENT]```
     apt-get -o Acquire::http::Dl-Limit=10 upgrade
```[/INDENT]The -o is short for --option and allows you to specify an apt configuration that you would normally write in a file, as in the example in the parent post. It's the same thing, just easier!

---

### Post by chepe263 on 2012-05-22
> **sinisterstuf said:**
> I'm a bit late to the party but in case anybody else stumbles upon this thread you can actually just:[INDENT]```
     apt-get -o Acquire::http::Dl-Limit=10 upgrade
```[/INDENT]The -o is short for --option and allows you to specify an apt configuration that you would normally write in a file, as in the example in the parent post. It's the same thing, just easier!

i wish i had read this in the beginning hahaha
:lolflag:

---

### Post by dewdrop_world on 2012-07-22
Thanks to everyone for this thread. I don't mind the use of bandwidth after the update manager pops up and I clicked the button to go ahead and upgrade. What was driving me nuts is that apt would hog every last bit of bandwidth *just to check for updates*... every morning, usually when I'm trying to look up something else online.

Looking forward to seeing how it behaves tomorrow :)

---

