---
title: "new server install.. did it work???"
date: 2007-07-25
forum: Server Platforms
---

### Post by twistedtwig on 2007-07-25
Hi all,

I have just reinstalled Ubuntu server addition onto my server (Feisty).. all seemed to go in brilliantly but I am finding some odd things that makes me think it might not have worked correctly.

when I do the command below this is the output I get:

jon@betty:/etc/logcheck$ sudo gedit logcheck.conf 
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
jon@betty:/etc/logcheck$ 


this is not something I have seen before with any of my ubuntu boxes.

Fire fox gives this error:

Firefox can't find the file at /usr/share/ubuntu-artwork/home/index.html.


in applications I Only have accessories and internet which in turn only have a couple of things in...

When I did the install I forgot it don't put gnome on by default so used the laptop quickly to find a way of installing it from the command line (couldn't remember what the packages where called or how to search for them).

I used this command:

apt-get install xorg gdm synaptic gnome-core gnome-system-tools netapplet

from this thread: [http://ubuntuforums.org/showthread.php?t=474355](http://ubuntuforums.org/showthread.php?t=474355)

I am guessing that it might actually be I have installed the wrong thing or not configured it correctly or something.

I am a bit stuck really... not got the dhcp network (or any internal network running yet so sitting in the garage with an 800-600 screen (OLD Compaq rack server) trying to figure it all out.

could someone be able to enlighten me please?

Thanks

---

### Post by lisati on 2007-07-25
It sounds a bit like something got changed or left out. When you're using Firefox, are you able to type in the address of a website and actually see the web page?

EDIT: I just noticed your comment that you don't have a network connection yet. Do you have any HTML files on your computer that you could look at?

---

### Post by twistedtwig on 2007-07-25
Sorry I think I am confusing you a little.

the server has two cards.. the external network and the internal... the internal didnt seem to be working (might have been firewall).

anyway.. i went through synaptic and just installed "gnome" and that seemed to do the trick... put firestarter on there and got the local network seeing the net (while I have static IP need to get DHCP Server up.. on that note.. I noticed both dhcp and dhcp3 server.. I will research this tomorrow but does anyone have thoughts on which I should use?)...

So the gnome thing is mainly sorted... well when I login it says it can not load the human theme xml file and firefox still doesn't find its stuff.. but it seems a little more alive now.

---

### Post by twistedtwig on 2007-07-26
just tried gedit again before work and I get more errors :(

jon@betty:/etc$ sudo gedit apt/sources.list
Password:
ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070: (snd_func_refer) error evaluating name
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968: (snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145: (snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070: (snd_func_refer) error evaluating name
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968: (snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145: (snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device

---

