---
title: "Rockbox on YOUR sansa fuze :o"
date: 2012-12-17
forum: The Cafe
---

### Post by tatmark1 on 2012-12-17
can I get some help doing this? I am trying to use the utility to do the install....but I cant seem to put the update into the root file because I am not finding it

---

### Post by Primefalcon on 2012-12-17
you'd probally get better help on the rockbox forums [http://forums.rockbox.org/](http://forums.rockbox.org/) since everyone there knows rockbox..

but it should just be a matter of downloading the utility, selecting the device, selecting the mount location, go to menu and select install bootloader, and then install the software.... I am running it on an Ipod nano 1g and it really was that simple to do

---

### Post by tatmark1 on 2012-12-17
i posted there as well...im guessing i didnt put the update file in the correct spot. i guess im having trouble finding the correct spot

---

### Post by Primefalcon on 2012-12-17
the steps are just go here: [http://www.rockbox.org/wiki/RockboxUtility#Download](http://www.rockbox.org/wiki/RockboxUtility#Download)

download the utility for your system, in my case it'd be the Linux (32 bit x86) and save it wherever, I'd say just do it to your desktop

right click the file and select extract here

I think you may have to run the utlity as root so open a terminal

and cd into created directy and run the command gksu ./RockboxUtility

click autodetect

go to action and select install bootloader then once done at the bottom of the window click install

you should be done

---

### Post by tatmark1 on 2012-12-17
here

---

### Post by Primefalcon on 2012-12-17
read my edited post above

---

### Post by tatmark1 on 2012-12-17
i am thinking i did that wrong as nothing happened

---

### Post by Primefalcon on 2012-12-17
> **tatmark1 said:**
> i am thinking i did that wrong as nothing happened
when it asks for your device did you click autodetect? if you did and it messed up go and manually select your device... make sure its the right version and everything though and if your manually doing it... make sure the mount point is correct as well

---

### Post by tatmark1 on 2012-12-17
it was already connected to the device mnt point is /run/lock

---

### Post by Primefalcon on 2012-12-17
> **tatmark1 said:**
> it was already connected to the device mnt point is /run/lock
bingo...... no.... its not... thats a linux thing... can you list or take a screen shot of the offered mount points?

---

### Post by tatmark1 on 2012-12-17
well i was just going by what the utility says 
i dont know how to find out what my choices are for the mount point

---

### Post by tatmark1 on 2012-12-17
i think i may have got it going...the utility is much further now

---

### Post by tatmark1 on 2012-12-17
i got it. thank you very much for your assistance.

---

### Post by Primefalcon on 2012-12-17
> **tatmark1 said:**
> i think i may have got it going...the utility is much further now
don't go selecting random points.. you could do a lot of damage...

but you select the mount point here: [https://dl.dropbox.com/u/1212637/rockbox.png](https://dl.dropbox.com/u/1212637/rockbox.png)

my guess is your looking for something like /media/sanza (or whatever your device is), if your in doubt.... ask!

---

### Post by tatmark1 on 2012-12-17
na i picked the right one and got it installed. thanks for your help

---

### Post by Primefalcon on 2012-12-17
> **tatmark1 said:**
> na i picked the right one and got it installed. thanks for your help
cool, glad I could be of help

---

