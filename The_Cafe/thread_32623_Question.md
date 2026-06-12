---
title: "Question"
date: 2005-05-08
forum: The Cafe
---

### Post by granite230 on 2005-05-08
Ubuntu gets a new release every 6 months right?
Warty Warthog was the first, Hoary Hedgehog the second.
But what if I install Warty and keep updating/upgrading. Will this automatically bring me from Warty to Hoary or do I have to reinstall Ubuntu to go from Warty to Hoary? 

I also read that every release will be supported for 18 months, does that mean I have to install a different version of Ubuntu every 18 months to keep my system up to date?

---

### Post by bored2k on 2005-05-08
1. In order to upgrade, you will need to change your download repositories. So for every version, you'll change these and yeah, get upgraded. Cool huh ;-]

2. Yes. If you stay with Warty, after 18 months you'll receive no more support for it. It's a good deal, considering you can just --dist-upgrade to the newest. *edit - * By yes I mean you can --dist-upgrade

---

### Post by poofyhairguy on 2005-05-08
[QUOTE=granite230]
I also read that every release will be supported for 18 months, does that mean I have to install a different version of Ubuntu every 18 months to keep my system up to date?[/QUOTE]


Nope, you just have to upgrade. Its really painless....

---

### Post by granite230 on 2005-05-13
Hm, I'm still not sure. I think I'll stick to Warty until the Breezy release.

I changed a lot of things in my Warty installation. For example I modified my Firefox logo, will this still be the modified version if I upgrade to another Ubuntu-release or another version of Firefox?
There are realy tons of things I changed/fine-tuned until I was happy. Not everything is working the way I want it to work yet but I'm still learning stuff. I don't want a dist-upgrade to mess up my settings and modifications.

I also have no idea (yet) how to change these download repositories... never did that before. I don't realy understand how all that stuff realy works (yet). I'm still learning ;)

---

### Post by bored2k on 2005-05-13
[QUOTE=granite230]Hm, I'm still not sure. I think I'll stick to Warty until the Breezy release.

I changed a lot of things in my Warty installation. For example I modified my Firefox logo, will this still be the modified version if I upgrade to another Ubuntu-release or another version of Firefox?
There are realy tons of things I changed/fine-tuned until I was happy. Not everything is working the way I want it to work yet but I'm still learning stuff. I don't want a dist-upgrade to mess up my settings and modifications.

I also have no idea (yet) how to change these download repositories... never did that before. I don't realy understand how all that stuff realy works (yet). I'm still learning ;)[/QUOTE]
 You can upgrade to hoary without the configs getting lost. YOur configs are saved in ~/. manner and will be used by the upgraded applications. So there is no need to stay with warty. Plus, you won't get super duper sweet apps with it.

---

### Post by granite230 on 2005-05-13
Okay, I'll give it a try!

I read a few threads and I understand that I have to do the following:

- open /etc/apt/sources.list and edit all Warty to Hoary
- get out of the GUI
- type apt-get dist-upgrade
- reboot, and enjoy Hoary

Is this correct? Please be specific on the details... I'm only a newbie :P
I'm sorry if I'm  a little over-worried and making a big deal out of this.
Can't be too careful ;)

Thanx for your help!

---

### Post by bored2k on 2005-05-13
[QUOTE=granite230]Okay, I'll give it a try!

I read a few threads and I understand that I have to do the following:

- open /etc/apt/sources.list and edit all Warty to Hoary
- get out of the GUI
- type apt-get dist-upgrade
- reboot, and enjoy Hoary

Is this correct? Please be specific on the details... I'm only a newbie :P
I'm sorry if I'm  a little over-worried and making a big deal out of this.
Can't be too careful ;)

Thanx for your help![/QUOTE]
 1) That is correct. It's hoary not Hoary by the way. More information read the official wiki. [http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

2) No need to. After you sudo aot-get dist-upgrade reboot your *machina* for the full !shabang!

3) I just covered that lol.

It's ok to be worried. We were/are all newbies at a certain point.

---

### Post by granite230 on 2005-05-13
So I just upgraded Warty to Hoary! 

The upgrade was a succes, everything looks cool but there were a few small things that I didn't like:

- Some menu items I deleted in Warty have returned after my upgrade to Hoary. Even when I use Smeg I can't delete any items. How can I delete Menu-items?
- In Open Office (Spreadsheet) I say: print selected sheet only, and usually it remembers this but now everytime I print a spreadsheet I have to set this option again because it won't remember it any longer. :? 
- I turned Num Lock ON by default but now it's OFF by default.

You see... this is why I hate dist-upgrades :|

---

### Post by bored2k on 2005-05-13
[QUOTE=granite230]So I just upgraded Warty to Hoary! 

The upgrade was a succes, everything looks cool but there were a few small things that I didn't like:

- My Firefox logo is gone! -fixed that already ;)
- Some menu items I deleted in Warty have returned after my upgrade to Hoary.
- My Unreal Tournament shortcut is still in the menu but America's Army is not.
- In Open Office (Spreadsheet) I say: print selected sheet only, and usually it remembers this but now everytime I print a spreadsheet I have to set this option again because it won't remember it any longer. :? 
- XMMS freezes when I want to play a song!! :? I cant even log out decently after that.
- My MPlayer shortcut is gone!! :?[/QUOTE]
 - Edit your menus using SMEG. [http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/)

- Did you edit xmms preferences so it uses eSound or alsa or whatever you use ? Personally I  recommend [this](http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd) method.

---

### Post by granite230 on 2005-05-13
I get this message all day!!

This time after sudo apt-get install libesd-alsa0

W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

What is it?

Thanx for your help! Smeg worked! Now I need to get my sound back! Anyone knows why I get this message?

---

### Post by Stormy Eyes on 2005-05-13
I think the backports site is down again.

---

### Post by granite230 on 2005-05-13
I think this is the problem, I found this at: [http://backports.ubuntuforums.org/:](http://backports.ubuntuforums.org/:)

Getting 403 Forbidden Errors? You must be using the old ubuntu-bp.sourceforge.net repository. Please update with [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports)

In the errors I get I see this:

W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)

So lets see what happens if I change [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) to [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) in my sources.list

Now when I say: sudo apt-get update I don't get the errors anymore but now it says this:

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=granite230]
Now when I say: sudo apt-get update I don't get the errors anymore but now it says this:

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems[/QUOTE]

Tell it yes anyway. The backport repo has not been "signed" because its too hard to do and it would mess everything up.

---

### Post by granite230 on 2005-05-13
How can I tell it yes anyway? 

I can't choose Yes/No and I tried sudo apt-get update -f but that gave me the exact same errors,

---

### Post by bored2k on 2005-05-13
[QUOTE=granite230]How can I tell it yes anyway? 

I can't choose Yes/No and I tried sudo apt-get update -f but that gave me the exact same errors,[/QUOTE]
 Just go ahead and install whatever you were going to. It will work.

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=granite230]How can I tell it yes anyway? 

I can't choose Yes/No and I tried sudo apt-get update -f but that gave me the exact same errors,[/QUOTE]


just install the program. It will say "these are not signed" tell it to install anyway (basically "shut up apt-get).

---

### Post by granite230 on 2005-05-13
Okay thanx for your help!

There are actually three more things that are not working since after the dist-upgrade:

- Some menu items I deleted in Warty have returned after my upgrade to Hoary. Even when I use Smeg I can't delete any items. How can I delete Menu-items?

- In Open Office (Spreadsheet) I say: print selected sheet only, and usually it remembers this but now everytime I print a spreadsheet I have to set this option again because it won't remember it any longer.

- I turned Num Lock ON by default but now it's OFF by default. Applications > Run Application > NumLockx works, but in Warty NumLock automatically turned on when I booted Linux. This is no big deal for me but my father doesn't know the first thing about computers.

Hoary is cool though! I also learned some new things thanks to this upgrade and this thread :)

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=granite230]
- Some menu items I deleted in Warty have returned after my upgrade to Hoary. Even when I use Smeg I can't delete any items. How can I delete Menu-items?[/QUOTE]

Use the other menu editor. Instructions are found of the Ubuntu Guide. Its what I use:

[www.ubuntuguide.org](www.ubuntuguide.org)

[QUOTE=granite230]- In Open Office (Spreadsheet) I say: print selected sheet only, and usually it remembers this but now everytime I print a spreadsheet I have to set this option again because it won't remember it any longer.[/QUOTE]

I would try installing the OpenOffice2 from the universe and see if it fixes it. If not, some googling will have to take place (very specific problem it is).


[QUOTE=granite230]- I turned Num Lock ON by default but now it's OFF by default. Applications > Run Application > NumLockx works, but in Warty NumLock automatically turned on when I booted Linux. This is no big deal for me but my father doesn't know the first thing about computers.
[/QUOTE]

uninstall numlockx then reinstall it.

---

