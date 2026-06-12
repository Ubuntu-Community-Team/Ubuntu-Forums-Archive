---
title: "[SOLVED] Lilypond and NtEd: install but no selection in menu to run"
date: 2008-10-12
forum: Ubuntu Studio
---

### Post by 73ckn797 on 2008-10-12
I installed Lilypond with Denemo and NtEd from repos. Neither can be used due to no selection added into the Applications/Sound & Video or anywhere else.

Had Musescore installed but it shuts off when trying to import any xml music file exported from Finale. Musescore has been uninstalled. Finale runs under Wine but has no sound output.

Any help?

Uninstalled Lilypond completely.

---

### Post by paulmerchant on 2008-10-12
I haven't tried NtEd, but I've been running Denemo and recently completed a couple of simple scores. (It's quite nice even though there are still a few random bugs.) When I installed Denemo from the repos, I got a menu entry. It's under the Sound & Video menu as GNU Denemo.

Even if you don't get a menu entry, you can run programs from the command line. Just open a terminal and type:
~$ denemo

You can also add your own menu entry. If you are running Gnome, use the Main Menu application under System | Preferences. The command simply needs to be: denemo

---

### Post by 73ckn797 on 2008-10-12
> **paulmerchant said:**
> I haven't tried NtEd, but I've been running Denemo and recently completed a couple of simple scores. (It's quite nice even though there are still a few random bugs.) When I installed Denemo from the repos, I got a menu entry. It's under the Sound & Video menu as GNU Denemo.

Even if you don't get a menu entry, you can run programs from the command line. Just open a terminal and type:
~$ denemo

You can also add your own menu entry. If you are running Gnome, use the Main Menu application under System | Preferences. The command simply needs to be: denemo


I did find Denemo just like you mentioned, before I saw your reply. Still would not import the xml file. I cannot find where NtEd is installed. I will try to run it using the same basic command you mention. This is really for my son who uses Finale. I am trying to sell him on Ubuntu. His gaming will be the biggest obstacle to breaking away from Windows Vista.

---

### Post by 73ckn797 on 2008-10-12
Thanks for the info on menu selections. It was also some basic learning for Ubuntu/Linux.

I do not understand about Lilypond. Tried the terminal command but only showed command references. I am not even sure if it is a stand alone program or not.

---

### Post by Stochastic on 2008-10-13
Lilypond doesn't have a GUI, it merely takes text files as input and outputs a pdf or ps file of music (or a midi file if that's what you tell it to do).  You have to write text in the lilypond language to "write music" directly with lilypond.  It takes a bit of learning, but in the end it's the most flexible and stable way of doing things.  I personally love this method as there is no GUI attempting to guess what I'm trying to do on the microlevel.

Denemo and NtEd are both GUI frontends to lilypond so I think you need lilypond installed for them to function correctly.

---

### Post by 73ckn797 on 2008-10-15
Solutions and answers in responses. Was checking it over for another person.

---

### Post by jonkulp on 2008-10-19
> **73ckn797 said:**
>  Finale runs under Wine but has no sound output.

Any help?

Uninstalled Lilypond completely.

I've gotten Finale's Demo version to run with playback under Wine by using the Timidity MIDI player.  If I recall correctly, you have to go into WINE's configuration and select Timidity as the MIDI playback device.  To get Timidity, do "sudo apt-get install timidity"

I remember now that I blogged on this topic here:

[http://jonkulp.blogspot.com/2008/01/running-finale-on-linux.html](http://jonkulp.blogspot.com/2008/01/running-finale-on-linux.html)

Good luck! (BTW, it's worthwhile learning Lilypond :) )

---

