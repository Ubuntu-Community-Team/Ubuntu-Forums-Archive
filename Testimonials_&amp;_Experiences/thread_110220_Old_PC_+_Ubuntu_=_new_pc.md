---
title: "Old PC + Ubuntu = new pc"
date: 2005-12-30
forum: Testimonials &amp; Experiences
---

### Post by samel on 2005-12-30
Hello everybody!

I just want to tell my story of success in installing Ubuntu.

My brother was given an old AMD K6-II without any memory nor hard disk.
This chirstmas Santa gave him 128 Mb simms for that machine (were hard to find) and a brand new HD.

Then I managed to make his old BIOS recongnize his hughe new HD (40 Gb is not that much!) thanks to a tool provided my Maxtor themselves.
Once that solved, I made my first trial to install Ubuntu there. No success. Grub gave me a nasty Error 18.

Looking for loading problems and Grub errors, I found that this one was also related to HD's size and BIOS. Now I knew how to solve it.

Second trial: Hand edit of the disk partition table: I created a 255 Mb /boot partition at the beginning of the disk, and then continued installing the usual way.

That was good but for sound.

Again in this site, well, in Ubuntu wiki, I red that some old drivers were dropped from 2.6 kernel. I tested some, and finally got the one I needed.
I listed it in /etc/modules to make it load each boot, and now it plays sounds.

After that, I "apt-*got*" some MP3 codecs, flash plugins for Firefox and a couple of things else for my brother to find what he was used to.

Last step was to put all his info in his now-we-can-call-it-new machine. I plugged it in my win98 (eech!!) network and like if it made it all his life, just presented me all shared folders I asked it to do. Grabbed all the files I wanted and... voilà! The computer got all it needed.

I have to say that I am really happy with the results. Previous experiences with Mandrake, Red hat and others weren't so pleasant to me.

I've seen that, even if Ubuntu isn't intended for working with old PCs, it can make them work in a quite functional manner (by adding them some memo, well, ok). No chances were to put any win in that box without expecting it to do nothing but explode.

Good work. +1 for Ubuntu!

PS . Excuses for the savage use and abuse of English. I do what I can.

---

### Post by greenpenguin on 2005-12-30
Good for you :)
Nice to hear someone enjoying Ubuntu.:)

---

### Post by Norberg on 2005-12-30
Congratulation!

---

### Post by AndyW on 2005-12-30
Congrats!
When I read 128 Mb simms I thought of the other day:
We got this old computer from somebody. I decide to take a hack at it, so I open it up and find some interesting stuff. First there was no ram, just 6mb of onboard ram! I couldnt find the ram slots, so I asked my dad. He pointed to these two slots (come to find out simms memory). I had never even seen this kind of memory, but as it turns out we had atleas 10 different sticks for it.
Anyways I decided I couldent do anything with it because we had no network cards for ISA slots. So I junked it.

---

### Post by poofyhairguy on 2005-12-30
RAM is the magic. More RAM the better for Ubuntu. CPU not so much. 

Thats why my 300 mhz iBook runs Ubuntu ok. 256 mb of ram. With 512 (Ubuntu magic number) it would fly.

Cool story. Good luck in future.

---

### Post by kencoe on 2006-04-05
[QUOTE=AndyW]Congrats!
When I read 128 Mb simms I thought of the other day:
We got this old computer from somebody. I decide to take a hack at it, so I open it up and find some interesting stuff. First there was no ram, just 6mb of onboard ram! I couldnt find the ram slots, so I asked my dad. He pointed to these two slots (come to find out simms memory). I had never even seen this kind of memory, but as it turns out we had atleas 10 different sticks for it.
Anyways I decided I couldent do anything with it because we had no network cards for ISA slots. So I junked it.[/QUOTE]

You are DEFINATELY makin me feel old right about now...

---

### Post by KermitJr on 2006-04-05
[QUOTE=kencoe]You are DEFINATELY makin me feel old right about now...[/QUOTE]

Tell me about it.  I still have 2MB and 4MB Memory sticks laying around... Less than that, I think, too.

---

### Post by Adrian_b on 2006-04-07
2mb?, that's barely enough for the windows calculator :s

---

