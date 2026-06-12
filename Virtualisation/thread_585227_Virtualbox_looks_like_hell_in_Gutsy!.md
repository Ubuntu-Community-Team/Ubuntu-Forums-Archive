---
title: "Virtualbox looks like hell in Gutsy!"
date: 2007-10-21
forum: Virtualisation
---

### Post by derekaug on 2007-10-21
So just got Gutsy going and all set up like I like... and not I find that Virtualbox looks like crap, see photo attached for what I'm talking about. Any ideas at what the problem could be?

BTW, I am using the nvidia driver.

---

### Post by bodhi.zazen on 2007-10-21
LOL, that is certainly a matter of opinion. What is wrong with it ?

You could always give feedback to innotek

---

### Post by anonymous_x on 2007-10-21
I'm yet to try it out .. . hope it works fine for  moi!

---

### Post by UbuWu on 2007-10-21
Install qt3-qtconfig and change the font settings to whatever you like to make it look better.

---

### Post by Chazall1 on 2007-10-21
My Virtual Box on Gusty looks like its running at a different resolution? Its all oversized. Its works, but is difficult to using the Virt Manager, and configuring-because of the size issue.

---

### Post by Jose Catre-Vandis on 2007-10-21
> **derekaug said:**
> So just got Gutsy going and all set up like I like... and not I find that Virtualbox looks like crap, see photo attached for what I'm talking about. Any ideas at what the problem could be?

BTW, I am using the nvidia driver.

I have the same problem, on an ATI card, and seamless is acting a bit odd too. (no desktop effects enabled, although it behaved the same with them on.) Accept it has something to do with QT, but what?

---

### Post by sloggerkhan on 2007-10-21
It looks like it's missing some some qt- stuff. Scribus looks that ugly (or worse) on my machine.

---

### Post by Jose Catre-Vandis on 2007-10-21
OK, it can be sorted out by doing what UbuWu said.

Install as follows:
```
sudo apt-get install qt3-qtconfig
```
then in a terminal
```
qtconfig
```
Click on the fonts tab
Change font to your preference (I used verdana) and set font size to 10
(or leave on F500 and change font size to 10)
File > Exit
Start up Vbox, and it should look a lot better :)

---

### Post by jsully1 on 2007-10-22
Dear lord thank you - I was hit with this as well.

---

### Post by Ralphie on 2007-10-22
But thats not the only thing that is wrong with VirtualBox, I am having problems beyond it looking terrible.

It seems to work somewhat fine, but i am having problems installing Adobe CS3 now. this was not a problem when i was using ubuntu 7.04.

I get the same error that i would if i were trying to install CS3 without Service Pack 2 installed. something about it cant find the installer or something. 

If anyone has info on possible fixes to get this program running as it should again, please respond.

thanks!

---

### Post by Jose Catre-Vandis on 2007-10-23
> **Ralphie said:**
> But thats not the only thing that is wrong with VirtualBox, I am having problems beyond it looking terrible.

It seems to work somewhat fine, but i am having problems installing Adobe CS3 now. this was not a problem when i was using ubuntu 7.04.

I get the same error that i would if i were trying to install CS3 without Service Pack 2 installed. something about it cant find the installer or something. 

If anyone has info on possible fixes to get this program running as it should again, please respond.

thanks!

Is it looking for the eula.dll ?Yuou can find this file pretty easily on the net, donwload it and place it in your home or install directory. Worked for me with CS2

---

### Post by Ralphie on 2007-10-23
> **Jose Catre-Vandis said:**
> Is it looking for the eula.dll ?Yuou can find this file pretty easily on the net, donwload it and place it in your home or install directory. Worked for me with CS2

thank you for the reply, i will download that file when i get home, where should it be placed? the system32? 

I'm not sure if the problem is the same as yours but i will try it.

this is the exact message I get while trying to install:

[I]"Setup has encountered an error and cannot continue. Contact Adobe Customer Support for assistance.

The Windows Installer Service could not be accessed. This can occur if you are running Windows in safe mode, or if the Windows Installer is not correctly installed. Contact your support personnel for assistance."[/I]

I looked on some windows forums, and they had help for people with this problem, and i tried what they said, but i feel like it has more to do with the way VB works under ubuntu 7.10, because none of the tutorials helped.

---

### Post by Jose Catre-Vandis on 2007-10-23
If memory serves me right, I had to unpack the ISO, copy all the files over onto the VM and start it up from there. You could try copying the ISO to your hard drive and mounting iton the VM?

---

### Post by mikeytag on 2007-10-24
Hey everyone. I had the same problem and have expounded on the fix outlined above. If you want to get your qt windows (virtualbox, hp, etc.) do the following:

```
sudo apt-get install polymer qt3-qtconfig
```

Then from a terminal run

```
qtconfig
```

In the resulting window choose Polymer as your theme, then click the Fonts tab and set your Family to Sans Serif and the Point Size to 9.

Close the window and click Yes to save your changes.

Then simply quit and reopen any of your qt apps. Mine look darn close to the way they did in Feisty. :) Polymer was the ticket on this one, the description in Synaptic for it says the following:

> Port of the KDE style "Plastik" depending on Qt only
Polymer (formerly known as Plastique) is a port of the KDE style
"Plastik", which does not depend on any KDE libraries. This means, that
you only need Qt 3.x to make your Qt applications look as if you had KDE
installed.

Currently only the multi-threaded version of the Qt library is supported.

---

### Post by Jose Catre-Vandis on 2007-10-24
Nice work Mikeytag - polymer does the job well

---

### Post by jespdj on 2007-10-25
> **Ralphie said:**
> It seems to work somewhat fine, but i am having problems installing Adobe CS3 now. this was not a problem when i was using ubuntu 7.04.

I get the same error that i would if i were trying to install CS3 without Service Pack 2 installed. something about it cant find the installer or something.
So you are using Ubuntu 7.10 as the host OS, but what's your guest OS? Win XP SP2, or Vista?

I have just installed Photoshop CS3 in a virtual machine running Win XP SP2 as the guest OS. No problems.

How much main memory and video do you have assigned to the guest OS? I've set it to 1024 MB / 64 MB. CS3 needs a minimum amount of 512 MB main and 64 MB video RAM, so you need to set the memory settings of your VM to at least those numbers.

I'm using VirtualBox 1.5.2.

---

### Post by Ralphie on 2007-10-26
> **jespdj said:**
> So you are using Ubuntu 7.10 as the host OS, but what's your guest OS? Win XP SP2, or Vista?

I have just installed Photoshop CS3 in a virtual machine running Win XP SP2 as the guest OS. No problems.

How much main memory and video do you have assigned to the guest OS? I've set it to 1024 MB / 64 MB. CS3 needs a minimum amount of 512 MB main and 64 MB video RAM, so you need to set the memory settings of your VM to at least those numbers.

I'm using VirtualBox 1.5.2.

Thank you so much for the reply, both here, and I assume also on the VirtualBox forums (as Gomez).

After your suggestion, I took a look and saw that I only had 40MB of Video RAM dedicated to the VM. After bumping it up I had no problem installing CS3. 

I guess it was just by luck the first time around that I set the RAM beyond Adobes minimum :D 

well thanks again, I am busy updating every post I made about the issue on different forums with your tip for anyone else who may run into the problem.

---

### Post by kasulstyls on 2007-10-26
Thanks for the fix with the look of Virtualbox!

---

### Post by pointone on 2007-10-29
Agreed. This should be a sticky somewhere...

Thanks bunches!

---

### Post by Cochise on 2007-10-29
thanks for the fix did the job nicely

---

### Post by Twintop on 2007-10-29
Fixed my display issues too. Thanks!

---

### Post by david.rahrer on 2007-10-30
Very nice solution, thanks!

---

### Post by VON_CAPO on 2007-11-01
> **mikeytag said:**
> Hey everyone. I had the same problem and have expounded on the fix outlined above. If you want to get your qt windows (virtualbox, hp, etc.) do the following:

```
sudo apt-get install polymer qt3-qtconfig
```

Then from a terminal run

```
qtconfig
```

In the resulting window choose Polymer as your theme, then click the Fonts tab and set your Family to Sans Serif and the Point Size to 9 
Superb fix.

Thanks a lot. :)

=D>

By the way, this thread should be marked as **[SOLVED]**

---

### Post by vexorian on 2007-11-01
I hope ubuntu devs learn from this and follow this blueprint: [https://blueprints.launchpad.net/ubuntu/+spec/human-theme-for-qt-and-kde/](https://blueprints.launchpad.net/ubuntu/+spec/human-theme-for-qt-and-kde/)

---

### Post by KOld Iron on 2007-11-01
Thank you, too. Basically a minor issue, but in a way annoying, when you have Compiz running and then you are faced with such an interface of an application :???:

---

### Post by sloggerkhan on 2007-11-02
Thank you.

---

### Post by freackout on 2008-06-18
> **sloggerkhan said:**
> Thank you.

i'm stuggling to get broadcom 4318 up in virtual box though it works fine on the lappy, dont have connection for broadcom 4318 but other cards are displayed for some reason. though i'm not sure if it was ok in 1.6 not 1.6.2

---

