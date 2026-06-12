---
title: "Virtual Box error made worse via noob"
date: 2008-07-30
forum: Virtualisation
---

### Post by Ebritno on 2008-07-30
Earlier today I installed Virtualbox (ose). I, then proceded to install windows on a vm, but as it began i recieved an error messgae telling me that i needed to install a virtualbox-ose-modules package

I preceeded with this in the terminal:
```
sudo apt-get install virtual-ose-modules package
```

Upon this I was informed of a number of packages containing the neccisary files for me to install (or so i had interprided it.. you see in my noobish stroke of stupidity i had not know exactly which one to install (virtualbox-ose-modules generic)but had thought they were all aplicable to my problem. i preceeded to run: 

```
sudo apt-get install virtual-ose-modules-2.6.24-19-virtual\24.0.4
``` 

This however did not work and so i searched it in google and downloaded a .deb version of the file. and have since been unable to acces the internet or use my mouse on my ubuntu machine.

So my question.. Does anyone know how i might come about uninstalling the package? It is only by a stroke of stupidity and unsaintly-miracle that i have made it this far in screwing up and i am now stuck as i have been unable to find a solution on google or the forums. (forums did tell me the [package i should have installed... the irony)

Thank you very much for your time. 

p.s if u think you need more for a diagnosis i will try to get it to you a.s.a.p

---

### Post by Pro-reason on 2008-07-30
Surely what you need is this: ```
sudo apt-get install **virtualbox-ose-modules-2.6.24-19-generic**
```

---

### Post by Ebritno on 2008-07-30
> **Pro-reason said:**
> Surely what you need is this: ```
sudo apt-get install **virtualbox-ose-modules-2.6.24-19-generic**
```
i tried that just now.. i recieved 

E: Couldn't find package virtual-ose-modules-2.6.24-19-generic

I've also tried 

```
sudo dpkg -r virtual-ose-modules-2.6.24-19-virtual_24.0.4_i386.deb
```

---

### Post by Pro-reason on 2008-07-30
> **Ebritno said:**
> i tried that just now.. i recieved 

E: Couldn't find package virtual-ose-modules-2.6.24-19-generic

I don't see how you could get that message from that command.  The package mentioned is different.

Are you 100% sure you're doing this right?

Copy and paste the command into the terminal.

---

### Post by Ebritno on 2008-07-30
yes i am sure. Do i need an internet connection for the command to work? im troubleshooting on wixp, while ubuntu sits there with no connection or mouse (mouse pad works fine though) 

I tried saveing a .deb package of the file you gave me and transfered it via my external harddrive, but it refused to run.

---

### Post by Pro-reason on 2008-07-30
> **Ebritno said:**
> yes i am sure. Do i need an internet connection for the command to work? im troubleshooting on wixp, while ubuntu sits there with no connection or mouse (mouse pad works fine though) 

I tried saveing a .deb package of the file you gave me and transfered it via my external harddrive, but it refused to run.

Yes, apt-get fetches the package from the internet (or from /var/cache/apt/archives/ if you've installed it before).

When you say that the locally saved .deb package failed to run, what do you mean?  What output did you get?

---

### Post by Ebritno on 2008-07-30
i got an eror message stating that it could not install becuase of the previous (wrong) package i installed earlier (or something to the effect.
______

I have spent all day trouble shooting multiple errors on 3 diffrent cpu's in my house and i dont think i can take another tonight. im taking a small break... and if i happen to run a fresh install during the break... life just might be easier 
(i had nothing but a desktop and internet configuration on ubuntu that was not backed up so no loss in data was truly made... just making up time... i could have had a fresh in stall by now had i done it in the beginning)

with my reasearch it didnt look like their was a fix (that i could comprehend at my level that was quicker and less complex than a reinstallation anyways) for my problem of installing and screwing up the kernel along  with other drivers on my machine by using the wrong package.

i guess im just gonna have to learn to: 
---READ messages THROUGHLY 
---Smacking the keyboard like a chimp might work on windows but but not with sophisticated operating systems like ubuntu.

Well anyways thanks for your help!!! 

p.s i have a vm on another system i can use to run and recreate the error if someone thinks they might have the fix for it-- so that this may open up an alternative to reinstalling for a web surfer without the time... or the means of backing up data.

once again thanks (and my ubuntu just finished as i finished this message:))

---

### Post by Pro-reason on 2008-07-31
> **Ebritno said:**
> i got an eror message stating that it could not install becuase of the previous (wrong) package i installed earlier (or something to the effect.

Without an exact error message, I can't tell you what to do to fix it.  :-(

---

### Post by overdrank on 2008-07-31
Moved :)

---

### Post by jimv on 2008-07-31
Run this:

sudo apt-get remove --purge virtualbox*

Then reboot and see if your internets are back.

Then go here: [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

And download this version of VirtualBox...it's not open source, but it's still free, and it includes USB and SATA support.  And you don't have to install any modules, it's all in one package.

---

