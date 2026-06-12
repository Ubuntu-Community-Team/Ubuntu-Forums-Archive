---
title: "Help Brainstorm for Ubuntu Tool Disc."
date: 2009-04-22
forum: The Cafe
---

### Post by Wiebelhaus on 2009-04-22
*Disclaimer* 

This is not a dude trying to make a another Distribution or a guy saying he's going to try to sell it or any of that nonsense.

**

I've been using Ubuntu for personal use for years but in the last two years I've been using Ubuntu full time and to repair Windows machines and I would keep a few live cd's around to test hardware and gather system specifications so a few weeks ago I decided I would remaster a custom tool disc to use for an all in one make my life at the bench easier. It's working so well that now I'm looking to expand it.

I'm respectively asking you folks to help me brainstorm or provide advice on yours that you use or to just help me make mine better.

Here's what I have so far:

A fat trimmed 8.04.2 Live disc , remastered with:

Locked with Log in to prevent unauthorized use.
Anti_Viruses
Partimage
qparted
G_Mountiso
ophcrack
wifi_radar & wrapper
PcFile man(I like it)
VLC (for testing media)
Ntfs_Tools
Network_Tools
baobab
Preconfigured for data recovery over personal network
Sysinfo (For specification gathering , is there something more robust?)
A bunch of how to's and informational docs in documents
And of course my favorite the terminal and all it's tools.
That's all I can think of right now.

Any ideas on rare or hard to find tools , More robust tools or any ideas 
on how to improve on my initial tech disc?

Thanks guys & girls and I can upload it somewhere if anyone wants it but it's nothing special , just a crude tool disc.

Cheers!

---

### Post by juancarlospaco on 2009-04-22
**Here's my creation, Jaunty based, made with VM-Builder**

[IMG]http://img223.imageshack.us/img223/4636/temp3.jpg[/IMG]


[IMG]http://img261.imageshack.us/img261/1616/temp2h.jpg[/IMG]

the same but with Kaspersky+AVG+ClamAV

Zenity+NTFS-3g makes a "Scandisk"

Zenity+"python -m SimpleHTTPServer" makes a backup web-folder

Zenity+"xset dpms force off" makes an option "Turn off monitor when scanning"

appnr.com makes a lightweight replacement for add/remove and Synaptics

---

### Post by tommynz1975 on 2009-04-22
Please consider joining 

[HTML]http://brainstorm.ubuntu.com/[/HTML]

and outline your idea....

the idea  of this site is  for the community to build on your idea  to make it something great for the developers to put together.....

a lightweight tools disc would be great.. yes they do exist I am sure..

example hermons boot cd.   for windows/linux

---

### Post by Wiebelhaus on 2009-04-22
Thanks , will do.

---

### Post by Wiebelhaus on 2009-04-22
> **juancarlospaco said:**
> **Here's my creation, Jaunty based, made with VM-Builder**

[IMG]http://img223.imageshack.us/img223/4636/temp3.jpg[/IMG]


[IMG]http://img261.imageshack.us/img261/1616/temp2h.jpg[/IMG]

the same but with Kaspersky+AVG+ClamAV

Zenity+NTFS-3g makes a "Scandisk"

Zenity+"python -m SimpleHTTPServer" makes a backup web-folder

Zenity+"xset dpms force off" makes an option "Turn off monitor when scanning"

appnr.com makes a lightweight replacement for add/remove and Synaptics

That's cool mate , thanks for the switches.

---

### Post by swoll1980 on 2009-04-22
How do you update the virus definitions?

---

### Post by Wiebelhaus on 2009-04-22
> **swoll1980 said:**
> How do you update the virus definitions?

On the one I made , the FS is live so you just update as normal but when you reboot it's gone.

I planned on running a script maybe once a week for full updates and re burning the ISO but it updates fine live.

---

### Post by swoll1980 on 2009-04-22
> **sx66gns said:**
> On the one I made , the FS is live so you just update as normal but when you reboot it's gone.

I planned on running a script maybe once a week for full updates and re burning the ISO but it updates fine live.

cool

---

### Post by juancarlospaco on 2009-04-22
Thanks , i dont want to.

---

### Post by Dragonbite on 2009-04-23
> **sx66gns said:**
> On the one I made , the FS is live so you just update as normal but when you reboot it's gone.

I planned on running a script maybe once a week for full updates and re burning the ISO but it updates fine live.

What about a startup script that downloads the latest virus definition on bootup or when the application is first launched?

---

### Post by juancarlospaco on 2009-04-23
> **Dragonbite said:**
> What about a startup script that downloads the latest virus definition on bootup or when the application is first launched?

i have just like you say...

---

### Post by Wiebelhaus on 2009-04-23
> **Dragonbite said:**
> What about a startup script that downloads the latest virus definition on bootup or when the application is first launched?

I like it! Good idea mate , thanks.

---

