---
title: "Concrete reasons why I love Ubuntu more"
date: 2007-08-17
forum: Testimonials &amp; Experiences
---

### Post by slamdunk12 on 2007-08-17
I put reasons over emotions so usually before I voice out my opinion I will test it out first for a period of time. And my experiment has proved that Ubuntu is more usable to me then any versions of Windows.

**_Introduction_**
I am a Software Engineer who worked on midrange to large projects for government and private sector. I used commercial and open source solutions bundled with proprietary applications to solve numerous problems for my client, and normally I'll use .Net or Java to build those applications.

**_My Experiment _**
I have a high-end desktop computer in my house and a comparable desktop in my cubicle both running Microsoft Windows XP, I also have an old laptop which is about 3 years old just sitting around gathering dust. So I've decided to install Ubuntu Feisty on it and see whether I can live with Ubuntu for as long as I can without using Windows XP, unless it is absolutely necessary.

**_The Results_**
The result really shocked me quite a bit, I've used Ubuntu for more then 3 months in a row without any major hiccups. Below is my findings:

[LIST=1]
[*]I've used Java to build my applications, so far there is no major problems that is unsolvable with a little bit of time and knowledge. Ubuntu Linux is a totally different operating system compared to Microsoft Windows, so I know it'll take me a little time to get used to the Linux way of doing things.
[*]I don't know whether it is possible to run Microsoft Visual Studio .Net on Ubuntu because so far I don't need to use it yet, but if it can't then there is still a reason for me to keep my Window partition around.
[*]Having thousands of open-source (Free) applications under my finger tips (Thanks Synaptic and apt) is absolutely great! I can find everything I need there so far. Plus I've also found three very useful apps for me, which is KOrganiser, Kdissert and Eqonomize!. I bet it'll cost me a hundreds of dollars to buy the commercially equivalent apps on Windows. 
[*]The flexibility and the customizations of Ubuntu Linux is astonishing, when I've successfully installed Beryl on my laptop it absolutely blew me away. Plus I can change my windows manager with just 2 clicks!
[*]The terminal is the most productive piece of application I've ever used in my life, and the irony is it doesn't even have a graphical user interface.
[*]Since most open-source applications are build with the community, it is very well supported, I can find almost all of the solutions to my problems .
[*]There is one criticisms though, installing my D-Link USB Wireless Stick is a great pain. But I think in the near future the Ubuntu Developers will sort it out in the next release.
[/LIST]

**_Conclusion_**
Overall it is a great OS for me, and it has open up great opportunity for me to learn more about Linux. The thought that it can be customized without limit is great. Thanks to all the hard working developers who has created such a great operating system for the masses, kudos to you.

I have joined The Force (Ubuntu Linux), goodbye Dark Side (Microsof t Windows) :KS

---

### Post by leathco on 2007-08-17
Glad to see another user realize there's other options than being forced to follow the empire.

---

### Post by steveneddy on 2007-08-17
> **slamdunk12 said:**
> Plus I can change my windows manager with just 2 clicks!


I can tell you how to change the WM in one click and one click to go back.

First use this script by copying it and putting it in your home folder. Name it whatever you like. Mine is names fission. I use it to launch Compiz-Fusion, but you could use it to launch Beryl if you change the line to read Beryl --replace instead of Compiz.

```


#!/bin/sh

# click to start, click to stop

if pidof compiz.real | grep [0-9] > /dev/null
then
 exec metacity --replace
else
# exec compiz --replace -c emerald
  exec compiz --indirect-rendering --replace -c emerald
fi


```

Then make a launcher that has in the command section the path to this script.

You could use any icon, but if you use Beryl, just point it to the Beryl icon.

There you go. WM changing with one click on one icon on your taskbar.

---

### Post by slamdunk12 on 2007-08-18
Thanks steveneddy for your tip, it worked wonderfully on my Ubuntu... Another great example of Ubuntu's flexibility ;-)

---

### Post by steveneddy on 2007-08-18
You are very welcome - pass on the tip I just sent you so many others can have this capibility.

---

### Post by ukripper on 2007-08-20
> **slamdunk12 said:**
> There is one criticisms though, installing my D-Link USB Wireless Stick is a great pain. But I think in the near future the Ubuntu Developers will sort it out in the next release.:KS

I know wirelessusb sticks   are always pain in the a*** so I got rid of them and put pci wirless card instead which works great for me and also cheap paid about 12 quid for it.:guitar:

---

