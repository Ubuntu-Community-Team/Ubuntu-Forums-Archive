---
title: "[SOLVED] GIMP won't load anymore"
date: 2008-11-13
forum: Ubuntu Studio
---

### Post by kg87 on 2008-11-13
Hey again guys and girls. 

gradually making the transition from XP (well, trying).

I found out about Gimpshop today and was intrigued, so I downloaded the .deb, and ran it. At first, I saw no difference in the GUI at all. so I got a little hasty and decided to uninstall gimp. now,

After reinstalling, GIMP fails to load FULL STOP. 

all i get now is "Starting GIMP Image Editor", then it does nothing, and that taskbar icon dissapears.. 

anyone able to shed some light??

thanks in advance

---

### Post by bswilson on 2008-11-13
I'm just curious why you're trying to install The Gimp from a Debian package, versus using the version in the Ubuntu repositories?  Version 2.6 is in there the 8.10 repos for sure.

Maybe try running this command to purge and then reinstall.

```
sudo dpkg -rP gimp && sudo apt-get update && sudo apt-get install gimp gimp-data gimp-data-extras
```

---

### Post by kg87 on 2008-11-13
hi thanks for the reply, i was installing gimpshop from the package, It basically transforms gimp's interface to be more like Photoshop, which is more familiar territory.

there was a problem with the command you gave me

> sudo dpkg -rP gimp

-r is remove and -p is purge right?, I am a tad of a noob..

so basically, i modified it by doing

> sudo dpkg -r gimp
       sudo dpkg -P gimp


and then the rest of it.. 

but the same problem still applies :S

---

### Post by kg87 on 2008-11-14
anymore ideas guys?

Solved it myself.. 

There is a problem with Gimpshop and 2.6, as in gimpshop is based on 2.2 so basically

```
sudo apt-get remove gimpshop
```

worked for me! Thanks anyway!

---

### Post by ideebe on 2008-11-15
[img]http://www.ideewomen.com/cn/uploads/200811111137220.jpg[/img]Women's beauty sourses from heart, just like the IDee jewelry reveals unique beauty carelessly, palpitates the will of the people easily. The IDee accessories are all designed uniquely, both elegant and fashion. Especially the series of mounting is matched by luxurious swarovski quartz, pearl, agate and so on, sparkles the eye-catching ray. The intoxicant appearance will let you unfold the graceful makings all the time. How can&#8217;t you be moved?  Wearing the charming IDee jewelry, your mood will be bright everyday. The IDee jewelry is worth possessing!

---

