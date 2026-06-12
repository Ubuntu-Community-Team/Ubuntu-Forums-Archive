---
title: "Steam text blurred"
date: 2009-03-12
forum: Wine
---

### Post by SladeHN on 2009-03-12
Hello. I am totally new to Ubuntu and Linux altogether, though not UNIX completely, I also have Mac. I recently got tired of all of my Windows problems, and went ahead and installed Ubuntu over it on my PC
Anyway, to the point. I have installed WINE, and have no clue about whether or not Gecko was also installed, being the latest version, I assume, i figured it was.
I went on ahead to the Steam site and downloaded it. I have installed [these fonts]("http://http://supportwiki.steampowered.com/wiki/Steam_Problem:_Missing_or_scrambled_text_in_Steam_menus") And right away once I started the installer, the text would not display. I continued the installation anyways, and proceeded to log in. It looks horrible, as if the text has been written four times over itself. I have no clue what to do or what could possibly be wrong. 
Help?
Thanks,
~Slade

[ATTACH]106214[/ATTACH]

[ATTACH]106215[/ATTACH]

[ATTACH]106216[/ATTACH]

---

### Post by Aries-Belgium on 2009-03-12
I had the same problem but in every Windows application. Look at this FAQ entry on winehq: [http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf](http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf)

That fixed my problem.

---

### Post by SladeHN on 2009-03-13
Thanks, I'll try it afterschool or tomorrow when I have some free time and tell ya how it works out.

---

### Post by SladeHN on 2009-03-14
Okay, so I reinstalled Ubuntu, and steam, and everything seemed dandy. I decided to start up Counter-Strike:Source, and it popped up to the loading screen, and then proceeded no more. I decided to install the 96 Drivers for my Nvidia GeForce 7900 GT and then I rebooted. Upon rebooting and relaunching steam, the text on steam blurred just like before. I've read the URL you suggested, but am not quite sure what you're trying to tell me to do.

---

### Post by Aries-Belgium on 2009-03-15
> **SladeHN said:**
> I've read the URL you suggested, but am not quite sure what you're trying to tell me to do.

Like the FAQ says:
> Place above in a text file called settings.txt and it can be inserted into the registry with the command regedit settings.txt.

---

### Post by SladeHN on 2009-03-15
Yeah, I've created it, and when I type regedit settings.text into the terminal, im assuming thats where, it says:
file not found "settings.txt (2)"

---

### Post by Aries-Belgium on 2009-03-16
> **SladeHN said:**
> Yeah, I've created it, and when I type regedit settings.text into the terminal, im assuming thats where, it says:
file not found "settings.txt (2)"

The filename you want to open with regedit doesn't exist. Check if the filename you create has the exact same name (case sensitive!!!) than the filename you want to open with regedit.

---

