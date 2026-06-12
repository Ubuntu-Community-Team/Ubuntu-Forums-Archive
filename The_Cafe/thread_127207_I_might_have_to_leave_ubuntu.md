---
title: "I might have to leave ubuntu"
date: 2006-02-08
forum: The Cafe
---

### Post by tikal26 on 2006-02-08
Hey:
So far I have learned to love ubuntu, but I just ran into a problem and I have no idea how to fix it. I am moving all my graphic work to Linux and I have find a way around to install MAYA, MAxwellan others, but I cannot install Realflow from Next Limit. They do not provide an RPM package but a script. They sy that you canuse RH8.0, RH 9.0, Suse 9.0, Or Fedora Core 2?, I tried to install the script but I ge tthe following error
bash: ./realflow: /bin/csh: bad interpreter: No such file or directory 
I don't know what is that supposed to mean. I already asked in their forum, but no luck. I don't know if the erro is sometinh bad I did when unzipping and unatarring the package or maybe there is someone who could help me. I really don't want to move away from ubutnu. I just hoped that commercial companies would support .deb a little bit better.

---

### Post by Brunellus on 2006-02-08
it wants you to have the csh shell installed, rather than bash...at least I think that's what it means.

---

### Post by tikal26 on 2006-02-08
and how you get chs shell installed?:-k

---

### Post by jcs296 on 2006-02-08
apt-get install tcsh

---

### Post by tikal26 on 2006-02-08
Padon my ignorance, but now I wonder how to I acces it or is that enough and just type it from yakuake. I just never used this stuff before.

---

### Post by rock freak on 2006-02-08
well if you got it from apt then just try running the script again!!

are you running it in sudo as well???? no idea if that will help does for me sumtimes!!!

hope you get it sorted!

---

### Post by steve.horsley on 2006-02-08
[QUOTE=jcs296]apt-get install tcsh[/QUOTE]

That will probably have to be **sudo apt-get install tcsh** after which you can try and run your install script again. If you need to install realflow as root, then use sudo in front of the command that starts the script, e.g. **sudo ./realflow-installer**

---

### Post by tseliot on 2006-02-08
[QUOTE=tikal26]Padon my ignorance, but now I wonder how to I acces it or is that enough and just type it from yakuake. I just never used this stuff before.[/QUOTE]
Don't worry, it's kind of easy.
First of all install csh and all you need to compile (actually the script may compile things for you):
```
sudo apt-get install csh build-essential gcc-3.4
sudo csh
```
(it will ask you your password)

cd path_to_your_script
sudo ./realflow-installer

If you have any other problem don't hesitate to ask.

---

### Post by tikal26 on 2006-02-08
It works now!!!
Thanks you very much to all of you that helped me. I have learned and managed to get my program running. I really appreciate your help. Now, is there a way to have the command in an icon or something like that so that everytime i want to open the program I don't have to run the script trough the console so that I can just click on an icon.
Again thanks.\\:D/

---

### Post by steve.horsley on 2006-02-09
Right-click the desktop and shoose create launcher, or right-click the panel and choose Add to Panel and add a custom launcher, or right-click your ubuntu icon and choose edit menus. 

That's three ways that I know of.

---

### Post by tikal26 on 2006-02-10
thanks, I that was easy. thanks

---

