---
title: "Ubuntu, Kubuntu or Edubuntu?"
date: 2005-12-06
forum: The Cafe
---

### Post by rocp on 2005-12-06
Hi All,

I'm a newbie here, and I would like to say hello to everyone and apologize if I write or do anything stupid. I must say also that english is not my native tongue, so you may see some mispelling or miswriting here. Not a great start, uh?

Here is the deal:

I'm the CIO for a health care institution in Brazil, and we just got some funds to apply in a computer laboratory for the patients. We already decided for linux, and Ubuntu is now our most probable distro choice. But I'm facing a doubt that maybe someone can help me to clarify: should we use Ubuntu, Kubuntu or Edubuntu?

The laboratory will be used to introduce computer and internet to very poor patients (who never or almost never had access to a computer), providing them a new professional carreer option/tool (most of them just can't attend to a regular fixed time job due to their illness). A considerable part of the patients are children (we plan to have distinct groups/classes).

Any opinion or consideration will be appreciated. We are also looking for teaching material, if anyone can tip me about it.

Please forgive me if this is not the apropriate thread for this... just point me the way.

TIA,

rocp
----------
BH - Brazil

---

### Post by erikpiper on 2005-12-06
Edubuntu is for little kiddies (Think games with what is 2+2?) so it is out
Kubuntu is ubuntu with KDE
Ubuntu is with gnome.

I say ubuntu because gnome runs better on slower computers.
Do you know how to use linux?

---

### Post by UbuWu on 2005-12-07
Edubuntu can be used to easily set up terminal servers.

---

### Post by rocp on 2005-12-07
[QUOTE=erikpiper]Edubuntu is for little kiddies (Think games with what is 2+2?) so it is out
Kubuntu is ubuntu with KDE
Ubuntu is with gnome.

I say ubuntu because gnome runs better on slower computers.
Do you know how to use linux?[/QUOTE]

Hi,

Thanks for your comment:) 

I'm not sure if I would discard Edubuntu, cause we have patients that are little kiddies. Would it be possible to set different environments according to the class?

We plan to have celeron d computers with 512 Mb RAM. Would that be too short for Kubuntu?

Answering your question, I'm no linux expert, but I can use it. And I have a linux expert in the staff.

I'm full of doubts:confused:

---

### Post by rocp on 2005-12-07
[QUOTE=UbuWu]Edubuntu can be used to easily set up terminal servers.[/QUOTE]

Hi,

Thanks for your reply :) 

The idea of terminal servers is very interesting for class purposes:KS . What would I need (in hardware) for a server to hold like 10 student computers?

---

### Post by Rinzwind on 2005-12-07
Those pc's are a bit slow. There's also xubuntu btw. Very slick and doesn't take up as much of your resources as a window manager as KDE or gnome would. ;) 

Btw, you can always install the edubuntu games on kubuntu or ubuntu. They are just not installed from scratch. kubuntu comes with KDE, ubuntu comes with gnome etc but if you (for instance) use firefox you only install it 1 time: both gnome and kde use the same program. And this goes for games and almost anything else  :) 

It's all the same ubuntu, it's just that they install different apps from scratch. 
My kUbuntu (uses KDE) also has gnome installed with all it's packages. 

So don't get too confused cuz it's fairly simple  ;)

Oh and do check the WIKI on top of this page cuz it's got several pages on all the flavours.

[https://wiki.ubuntu.com/Kubuntu?highlight=%28kubuntu%29](https://wiki.ubuntu.com/Kubuntu?highlight=%28kubuntu%29)
[https://wiki.ubuntu.com/Xubuntu?highlight=%28xubuntu%29](https://wiki.ubuntu.com/Xubuntu?highlight=%28xubuntu%29)
[http://www.edubuntu.org](http://www.edubuntu.org)

---

### Post by rocp on 2005-12-07
[QUOTE=Rinzwind]Those pc's are a bit slow. There's also xubuntu btw. Very slick and doesn't take up as much of your resources as a window manager as KDE or gnome would. ;) 
[/QUOTE]

Hi,

Thanks for your comments and tips :) 

Already reading about Xubuntu (not much to read thoug)

I'm a bit surprised 512 Mb won't be enough. So what would be the recommended hardware for Ubuntu or Edubuntu?

---

### Post by ssam on 2005-12-07
512mb is fine for ubuntu/kubuntu.

it may be possible to customise a edubuntu install so that you get the benifits of  terminal servers and your own choise of packages.

all the ubuntu varients are basically the same, they just have a slightly different default set of applications and desktop evnironment.

you can install the kubuntu-desktop and xubuntu-desktop package on an ubuntu install to get all three sets of packages.

---

### Post by Rinzwind on 2005-12-07
Hmm it's not the 512 Mb. It's the board: celeron. It'll work. No doubt but don't expect to have the more serious apps to work as well.

The question to answer is: will these PC's be more toward kids or toward grown ups? If it's the 1st get Edubuntu and then install the apps it doesn't install at startup. Like have a cd player, dvd player, openoffice.org or whatever you feel you need. If it's more towards grown ups install either x/k or ubuntu and add the games from Edubuntu.

Oh and you could ALSO do a mix: do some with edu, some with x/k/ubuntu and see what the people that use it use the most.

To explain the difference between k and ubuntu:
If you use ubuntu sudo apt-get install kubuntu-desktop adds KDE.
If you use kubuntu sudo apt-get install ubuntu-desktop adds gnome.
It's THAT simple. And I can't imagine xubuntu and edubuntu will be any different. 

Whatever you take you can always end up with another window manager. That's the cool thing about Linux :) :)

---

### Post by erikpiper on 2005-12-07
512 is plenty!

If you have a spare PC install ubuntu, then type into a console
sudo apt-get install kubuntu-desktop

Then try out both gnome/kde to see which you like better!

---

### Post by CompShrink on 2005-12-08
I am not an expert in the difference between Edubuntu and the other two, but hopefully this post will be of some use.

You may want to read this: [wiki.ubuntu.com/ThinClientHowto]("https://wiki.ubuntu.com/ThinClientHowto")

As well as: [http://wiki.ubuntu.com/LTSPHowTo]("http://wiki.ubuntu.com/LTSPHowTo")

Those are two guides on setting up so called thin clients. 


As for the Celeron Ds, unless you are getting a special deal on them, AthlonXP2600+ would give you better performance for around the same price according to most of the reviews I've seen.

From [this]("http://www.ubuntuforums.org/showthread.php?t=96883) thread;
> I also set up LTSP labs for schools and have had a lot of success. One lab has a 1800+ Athlon and 768 MB RAM and runs 15 client PCS (100-250MHz / 64MB and no hdd) with KDE/OOo/FFox/Gimp/etc. Takes a minute to boot, but works awesome. No complaints from kids or teachers. (and they love having THEIR desktop no matter where they log in).

So if you haven't already paid for the computers, thin clients might be a good way to afford more computers in total. Buy old used computers that should be really cheap. 

I would suggest giving a little more power to each computer than he suggested, so you don't have to upgrade too soon. Maybe an AMD AthlonXP2600+ or above, with 768mb or 1gb of ram per 10 thin clients, each with at least a 250Mhz processor and 128 mb ram.

Also, you should (in theory) be able to upgrade just the server PC when you start feeling that they're getting too old, running too slow for modern software.

Personally, I say try them all out. EDUbuntu's supposed to be a simplified Ubuntu, with added games, right? A simplified version might be good for adults new to computers as well, and it comes with LTSP preinstalled.

Hope that helps. Do your homework and it'll work out I'm sure. Good luck!

---

### Post by UbuWu on 2005-12-08
[QUOTE=rocp] What would I need (in hardware) for a server to hold like 10 student computers?[/QUOTE]

Ram is most important. A rough guideline (minimum):
Total Ram = 256mb + ( 50mb * number_of_terminals )

So for 10 clients:
Total Ram = 256 + ( 50 * 10 ) = 256 + 500 = 756mb

See this page for more information: [http://wiki.ltsp.org/twiki/bin/view/Ltsp/ServerSizing](http://wiki.ltsp.org/twiki/bin/view/Ltsp/ServerSizing)

---

