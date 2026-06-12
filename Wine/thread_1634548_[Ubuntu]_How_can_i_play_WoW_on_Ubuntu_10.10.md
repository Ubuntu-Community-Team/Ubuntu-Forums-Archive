---
title: "[Ubuntu] How can i play WoW on Ubuntu 10.10 ?"
date: 2010-11-30
forum: Wine
---

### Post by AlexThayer on 2010-11-30
Hello,

I understand that there are a lot of compatability issues with linux derivatives but how can i play World of warcraft on ubuntu? (Its 32-bit Ubuntu on a 32-bit machine). 

I havent downloaded WoW yet because i want to make sure i know what i need before i do this..

-thanks for help.

---

### Post by jmwinter1991 on 2010-11-30
What I did was I downloaded Wine in the Terminal. The command line should be "sudo apt-get install wine" and then after that, I went to the downloaded file of WOW and right clicked it and went to the Permission tab and clicked the box that says something about allowing it to be executable. (bare with me, i haven't used Ubuntu for a while and right now I am on Windows) Anyway, than I right clicked it and ran it under Wine. It installed and updated and everything but I did not check to see if all the graphics worked because I didn't have an account and the gf was mad at me being on the computer too long. You could try that. If not, just google it and find one that works. If you find a site that helped you, it would be awesome if you posted the site here so other users can be helped by you if they are having issues. Sorry if I am no help! Good luck.

---

### Post by efikkan on 2010-11-30
First, install Wine in the software center or in terminal using ```
sudo apt-get install wine1.2
``` or ```
sudo apt-get install wine
```

Then right-click on the installer for WoW and click run in wine.

WoW is one of the games wich works very well in Ubuntu, but if you need more tips check [Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549").

---

### Post by Firem4nJoe on 2011-03-12
I'm interested in trying this, anyone know of any mirrors or torrents they trust for downloading WoW (and/or the expansion packs) ???

P.S. For those not comfortable using the command line terminal, Wine is listed in the Synaptic Package Manager in Ubuntu 10.10 
System > Administration > Synaptic Package Manager
Then just type Wine in the quick search. :)

---

### Post by cwwilson721 on 2011-03-12
> **Firem4nJoe said:**
> I'm interested in trying this, anyone know of any mirrors or torrents they trust for downloading WoW (and/or the expansion packs) ???

Go to [www.worldofwarcraft.com](www.worldofwarcraft.com). If you don't want to, Google for "wow mirror"

To AlexThayer:

[COLOR="Red"][SIZE="4"]SEARCH THE FORUM. [/SIZE][/COLOR]

If you would already have, you would know there is a VERY detailed HOWTO.

---

### Post by shz1 on 2011-03-12
after installing wine through the package manager, the wow install and patching works out of the box for me

---

### Post by Firem4nJoe on 2011-03-12
Thanks, I've just been out of the WoW loop for ages now and I prefer to play on private servers because technically it is still legal to do so and also I am cheap and I don't want to pay for subscription - I'm wondering if this is still a simple edit of the realmlist.txt or have Blizzard made it harder in my absence?

P.S. Sorry for side tracking from the original issue.

---

### Post by Dlambert on 2011-03-12
> **Firem4nJoe said:**
> Thanks, I've just been out of the WoW loop for ages now and I prefer to play on private servers because technically it is still legal to do so and also I am cheap and I don't want to pay for subscription - I'm wondering if this is still a simple edit of the realmlist.txt or have Blizzard made it harder in my absence?

P.S. Sorry for side tracking from the original issue.

Nope, still the same method. I would upgrade Wine to latest release 1.3.15, but thats just me.

---

