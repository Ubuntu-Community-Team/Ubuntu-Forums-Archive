---
title: "Couple of questions about ubuntu."
date: 2007-06-19
forum: The Cafe
---

### Post by Arkiel on 2007-06-19
Hello everyone i have a couple of questions that i wanted to see if i could get some answers to. These forums seem friendly enough and after using the search function i still feel unknowing so maybe someone can give it a go :)

Firstly I want to install ubuntu on my HP ZD8000 laptop its my primary comp. and it has an ati x600 mobility radeon in it and was curious do i need to install a driver for it or are ati drivers already in ubuntu. (prolly not but figured i would ask) and if not how do i go about installing them.

Secondly to run windows like apps such as games do i need wine or does ubuntu have it covered? If i have to use wine is it easy to set up? 

Also as far as playing audio/video files such as wma,divx,mp3 etc can i install divx or an mp3 player? or codecs like for the file types?

Thats about it for now as you can tell im new to linux coming from windows and I've been doing as much reading as i can. Just some questions have me left wanting >.<

Any help is appreciated so thanks to anyone who gives it a shot!

---

### Post by FuturePilot on 2007-06-20
Hi and welcome. When you install Ubuntu you will already have a driver for your graphics card in use. It's the open source "ati" driver. However, it's not too good with 3D stuff so you may need to install the FGLRX proprietary driver to get better performance out of your card. The latest Ubuntu (Feisty) has made this task pretty simple.

Some Windows only programs will work find using Wine. However there's usually a Linux equivalent to most Windows apps. MS Office=Open Office, Photoshop=GIMP But if you need a certain program that's only available for Windows, Wine should do the trick.

For codecs and stuff, have a look here.
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
That explains on how to install just about every codec you could ever need.

---

### Post by Celegorm on 2007-06-20
You need wine or some other software to run windows applications in ubuntu. It depends which applications you want to run whether it will be easy to set up. I suggest poking through wine's app database to see if the applications you want are known to work or not: [http://appdb.winehq.org/]("http://appdb.winehq.org/") If there is some windows application that you absolutely cannot do without, that either does not have a linux equivalent or that might not work with wine, I'd suggest setting up a dual boot system with Ubuntu and Windows.

There are quite a variety of media players available for Ubuntu, and there's a thread here about getting codecs and multimedia working: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by Arkiel on 2007-06-20
Thanks for the tidbits and the link im gonna read that in a sec that kinda calms my nerves about using ubuntu :)

I just really want to get away from windows and its clutters that and about every 6 months i have to reinstall cause something inevitably screws something else up >.<

thanks again for the help though :)

---

### Post by scrooge_74 on 2007-06-20
Hi welcome.

For your first question on the ATI drivers, Ubuntu comes with open source drivers, but those drivers leave out lots of the capabilities of your card (ATI is not well supported anyway thanks to ATI policies) latest version of Ubuntu will help you install the correct close source drivers for it.

For Wine you should check winehq.org for each of the games or apps you want to use, some work, some dont, some go half way.  you can find pretty good and interesting games for Linux also.

For codecs a few months back it was a little more complicated, but things are getting easier every day, there are tools and howtos for it, check the documentation provided [here]("https://help.ubuntu.com/community/UserDocumentation")  it should get you going pretty 
soon.

Keep reading and learning, I learn something new every day and it is a lot of fun to discover new things (plus been able to work without worrying about viruses and spyware)

Have fun

---

### Post by Arkiel on 2007-06-20
> **Celegorm said:**
> You need wine or some other software to run windows applications in ubuntu. It depends which applications you want to run whether it will be easy to set up. I suggest poking through wine's app database to see if the applications you want are known to work or not: [http://appdb.winehq.org/]("http://appdb.winehq.org/") If there is some windows application that you absolutely cannot do without, that either does not have a linux equivalent or that might not work with wine, I'd suggest setting up a dual boot system with Ubuntu and Windows.

There are quite a variety of media players available for Ubuntu, and there's a thread here about getting codecs and multimedia working: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Well another search revealed the results i was looking for the programs in general are just games like World of warcraft ut2k3 and games of the like

---

### Post by Iarwain ben-adar on 2007-06-20
Hiya,

If your games are not supported (yet :D ) by wine, try dualbooting.

I formatted my pc, made my partitions (via Live CD) and then installed Windows first, then Kubuntu.
Only using Windows for gaming, it never crashes or gives me strange quirks. For all the rest i'm using Kubuntu.

Perhaps it's better first trying a dualboot before really jumping in?


Iarwain

---

