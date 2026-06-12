---
title: "Pro Wrestling Superstar"
date: 2009-04-21
forum: Wine
---

### Post by Luke Fleeman on 2009-04-21
Hello all!

I recently switched over to Ubuntu, and the only program I have not been able to use effectively is a little one I really like called Pro Wrestling Superstar, which is available here: [http://pws.berlios.de/](http://pws.berlios.de/).

Whenever I use Wine to launch it, it says "Starting Pro Wrestling Superstar" but never actually begins. I would love if someone could assist me here. 

I already tried using different OS, and none of them make any difference. All the other configurations don't change anything either. 

Complicating the issue is the fact that I am a n00b, and I can't figure out how to do certain things. I am running Wine 1.0.1 on Ubuntu Intrepid Ibex. I have the proper drivers for my Video card.

I don't know how to run Wine from the terminal either. If someone could help out, I would appreciate it.

---

### Post by Luke Fleeman on 2009-04-22
Anyone?

---

### Post by Luke Fleeman on 2009-04-24
Does anyone know where I can go to get help for this? Since no one here knows what is wrong or wants to help, I just need a little assistance to make this one program work.

---

### Post by Luke Fleeman on 2009-05-01
If someone can help me, I am willing to compensate them. 

Someone could at least tell me to bugger off if there is no chance of getting help. the deafening silence is not helping me.

---

### Post by qwertymn on 2009-05-01
hi, i gave the app a try; it starts fine for me using native msvcrt. Looks like there's a bug in wine's msvcrt. Easiest way :

winetricks mfc42;
WINEDLLOVERRIDES="msvcrt=n" wine pws.exe

Also, better upgrade to newest wine 1.20

---

### Post by Luke Fleeman on 2009-05-01
Thanks so much for helping. I thought I was invisible.

How do I do the winetricks thing? Do I type that somewhere? I don't know how to do that. Synaptic Update Manager shows I have wine, and the menu shows wine. But I can't find the home folders for it.

Also, my update manager and all other stuff only offers 1.0.1. How can I get upgradeD?

---

### Post by qwertymn on 2009-05-02
> How do I do the winetricks thing? Do I type that somewhere? I don't know how to do that. Synaptic Update Manager shows I have wine, and the menu shows wine. But I can't find the home folders for it.

Also, my update manager and all other stuff only offers 1.0.1. How can I get upgradeD? 

Trys this command in the terminal:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) && sh winetricks mfc42

(I only switched to ubuntu a few days ago, and noticed wget is not installed by default, so maybe you first have to do 'sudo apt-get install wget')

After installation do:
cd ~/.wine/drive_c/Program\ Files/Pro\ Wrestling\ Superstar/
WINEDLLOVERRIDES="msvcrt=n" wine pws.exe

> Also, my update manager and all other stuff only offers 1.0.1. How can I get upgradeD?

I don't know, on fedora it worked like you had to add other repositories, how it works on ubuntu i do not yet know, i myself compile wine from source--> always the latest version

---

### Post by Luke Fleeman on 2009-05-02
Holy cow that is awesome. Thank you so much, I thought I would be ignored forever. You really made my day!

---

