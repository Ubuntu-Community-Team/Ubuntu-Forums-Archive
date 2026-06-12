---
title: "Whoops I did it again ..."
date: 2017-08-15
forum: The Cafe
---

### Post by shantiq on 2017-08-15
Hhmmm   so not a Britney appreciation post but a summary of the aleatories of playing with your Linux distros ...  I have some holiday time so I think time to try new distros  ...   I have an old Packard Bell PC from 2005 and I load it up with Slackware and Manjaro ...   I also have a 2005 MacBook with 10.6.8 installed also with Ubuntu 16.04 using rEFIt to load it and added BodhiLinux for good measure even tried [https://en.wikipedia.org/wiki/Astra_Linux](https://en.wikipedia.org/wiki/Astra_Linux) designed by the Russian military.... my main and current Acer PC has 16.04 and I intend to leave it out of my experimentation of course ....

I have all 3 machines running concurrently and merely move from one to the next trying this and that ... what can I do here which does not work there and why? kind of playful balletic Linuxing ...   it is summer let's have fun ...

[Manjaro]("https://manjaro.org/") it turns out is amazing ...   everything is there ...   it is so easy to install a ten-year-old could do it ...    everything works ...  Iphone is picked up OOTB ...   I play for a while then move away as I want things to think about ...   you're Linux users you understand .

PS If anyone says to you "I'd like to try Linux but fear it is too hard too involved ; may I suggest you point them in the Manjaro direction"

OK so I carry on ...   much use of Live SuperGrub2 and Gparted to partition and reorganize my space; but at one point on my main machine Unetbootin goes grey and nothing shows up anymore, so I think no worries let us remove all of that and start again
I use Locate and find all the files are in /usr/share/unetbootin so I use sudo rm -rf * once in /usr/share/unetbootin or so I think  [I found sudo apt remove --purge sometimes leaves bits and pieces behind] but I forgot to write "unetbootin" so busy was I hopping from one machine to the next so my entire share folder has gone and really so has my 16.04 install and ALL MY FILES! :] Whoops I did it again .....

Fortunately much backed up elsewhere so not too bad but still ....    sobering  ...    and reinstall

On the Slackware never managed to create a user that was accepted [something to do with .serverauth not being found read around it and then left it]so I had stayed in root and still do  ...    the wiping of my share folder showed me that really the minute you use a terminal and mostly that means sudo you are in the same boat as a root slackware user so I shall remain root there ...   it means you can damage your system but hey terminal opens the door to that ....   maybe it is just me [but I doubt that]

Playing around is interesting ...   iphone is picked up OOTB by Manjaro and Slackware!?! but not by Ubuntu which required

```
sudo apt-add-repository ppa:ingo/ios7support
sudo apt-get update
sudo apt-get upgrade

then run:

sudo mkdir /var/lib/lockdown
sudo chmod 777 /var/lib/lockdown
```

Some things are smoother in one distro and not in the next ...  been a Ubuntu user since 2009 but I now love Slackware too especially with the sbopkg package manager which again could be used by a ten-year-old ...    Slackware usta be seen as "scary" Linux;   well it really no longer is ...    if I can use it  ..iso burnt to usb then install and make a beeline for sbopkg ...    anyone can   ...   and it is sooo stable so pared down .

And there are now incredibly easy Distros like Manjaro   ...    there are probably others too

So in 2017 Linux is still free mostly virus-free too and has so much variety that really ANYONE can and should have a go
No need to make The Great Vaccinator richer ....   The future is bright for PC/laptop users ...    the future is Linux ... we hope

---

### Post by Perfect Storm on 2017-08-15
...and here I thought a Britney gathering at last :P :P :P

It haven't been easier than now to install linux is my conclusion. I would say it as easy as windows. Some would ague it's easier to install linux than windows. I would say they are just different.

---

