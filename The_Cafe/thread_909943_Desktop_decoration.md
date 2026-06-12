---
title: "Desktop decoration"
date: 2008-09-04
forum: The Cafe
---

### Post by mailtwogopal on 2008-09-04
Hi all,

  I am having ubuntu hardy in my box. I am not sure whether am right to be here to ask you guys about how i can have my Desktop richer than one of my friend who owns windows vista. The idea is, apart from using background images to make the desktop richer, how to an extent i can customize my desktop. This question may be silly but it is due to the fact that i may not aware of using or customizing ubuntu hardy desktop. Please help me. Hope guys understand what i need.

---

### Post by Sealbhach on 2008-09-04
Hi,

You need to install the Compiz Configuration Settings Manager.

This will allow you to enable a whole load of amazing effects.

You can install it with Add/Remove programs - juat search for "compiz" and the first package you will see is "Advanced Desktop Effect Settings".

That's the one you want.


.

---

### Post by Trail on 2008-09-04
You might want to try screenlets as well, or avant-window-navigator. Which need compiz enabled, though.

(By the way, less is more. Simpler desktops are more productive, imo).

---

### Post by billgoldberg on 2008-09-04
> **mailtwogopal said:**
> Hi all,

  I am having ubuntu hardy in my box. I am not sure whether am right to be here to ask you guys about how i can have my Desktop richer than one of my friend who owns windows vista. The idea is, apart from using background images to make the desktop richer, how to an extent i can customize my desktop. This question may be silly but it is due to the fact that i may not aware of using or customizing ubuntu hardy desktop. Please help me. Hope guys understand what i need.

See link in my signature "Customizing Ubuntu".

---

### Post by Dutch70 on 2008-09-04
Here is a good site to help you get compiz set up...
[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

I didn't read this entire thread. But I will forewarn you about screenlets...although they are really awesome. If you decide you don't like them, or you have trouble with them, from what I understand, it takes a power user to uninstall them. So do some research before making that decision.

---

### Post by billgoldberg on 2008-09-04
> **Dutch70 said:**
> Here is a good site to help you get compiz set up...
[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

I didn't read this entire thread. But I will forewarn you about screenlets...although they are really awesome. If you decide you don't like them, or you have trouble with them, from what I understand, it takes a power user to uninstall them. So do some research before making that decision.

I don't know why you think that.

It's removed like any other app.

---

### Post by Dutch70 on 2008-09-04
> **billgoldberg said:**
> I don't know why you think that.

It's removed like any other app.

Well, I had read something to that effect, sorry I can't give you the source, but are you saying that screenlets can be added and removed easily. If so please enlighten me, because I would love to have them. But 3 months ago I didn't even know what linux was...lol. So I have to be very careful.

---

### Post by mailtwogopal on 2008-09-05
Hi guys,

  thanks a lot for ur replies. I ll try tonight and let u all know. Am in office at present. Also guys please tell me one thing that, **do i need NVIDIA graphics card and driver to work with compiz** since mine is not NVIDIA at present.

---

### Post by Saint Angeles on 2008-09-05
you dont even need advanced desktop effects (compiz) to make your desktop pretty!

take a look at my current setup. (i have anxiety problems and i change my theme about every 3 days)

---

### Post by mailtwogopal on 2008-09-05
Hi saint,

  Shall i follow the link "See what worked for me" in your signature area. Mine is also ATI only. Shall i try this?

---

### Post by mailtwogopal on 2008-09-05
Hi saint,

  Shall i follow the link "See what worked for me" in your signature area. Mine is also ATI only. Shall i try this?

---

### Post by Saint Angeles on 2008-09-05
> **mailtwogopal said:**
> Hi saint,

  Shall i follow the link "See what worked for me" in your signature area. Mine is also ATI only. Shall i try this?

yes sir!

i've helped a few people getting fglrx (the proprietary ATI driver) to work!

---

### Post by billgoldberg on 2008-09-05
> **Dutch70 said:**
> Well, I had read something to that effect, sorry I can't give you the source, but are you saying that screenlets can be added and removed easily. If so please enlighten me, because I would love to have them. But 3 months ago I didn't even know what linux was...lol. So I have to be very careful.

Sure.

I've installed the latest version , not the ancient version in the repos. So that could be why was easier for me.

Install instructions are copy/paste only.

Look here for them:
[http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/](http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/)

---

### Post by mailtwogopal on 2008-09-05
Ok guys i try tonight and let you know the results. :)

---

### Post by mailtwogopal on 2008-09-05
Hi saint,

  i have gone to [http://ati.amd.com/support/drivers/l...ux-radeon.html](http://ati.amd.com/support/drivers/l...ux-radeon.html) page, where the page is like the attachment here. i clicked on ATI driver installer link in that page and it downloaded to my desktop. As i typed "sudo sh ati[tab]" it said as below:

```


gopal@gopal-desktop:~$ sudo sh ati[tab]
sh: Can't open ati[tab]


```

What can i do further?

---

### Post by miggols99 on 2008-09-05
> **mailtwogopal said:**
> Hi saint,

  i have gone to [http://ati.amd.com/support/drivers/l...ux-radeon.html](http://ati.amd.com/support/drivers/l...ux-radeon.html) page, where the page is like the attachment here. i clicked on ATI driver installer link in that page and it downloaded to my desktop. As i typed "sudo sh ati[tab]" it said as below:

```


gopal@gopal-desktop:~$ sudo sh ati[tab]
sh: Can't open ati[tab]


```

What can i do further?
When it says [tab] it means to **press** tab. Not to type it..

---

### Post by mailtwogopal on 2008-09-05
hi miggols,

  i pressed tab after that but none happened. so i copy-pasted the full file name and still error as below:

```

gopal@gopal-desktop:~$ sudo sh ati-driver-installer-8-8-x86.x86_64.run
[sudo] password for gopal:
sh: Can't open ati-driver-installer-8-8-x86.x86_64.run

```

Please help.

---

### Post by MaxIBoy on 2008-09-05
Right click the .run file, go to "properties," then "permissions," and enable executing of the file as a program.

---

### Post by GrouchoMarx on 2008-09-05
If you saved it to your desktop then the file is in the "Desktop" folder in your home directory. You need to specify that in your path...

```
sudo sh Desktop/ati-driver-installer-8-8-x86.x86_64.run
```

---

### Post by mailtwogopal on 2008-09-05
Hi maxi,

  I did the same a pop up window appeared having options "Cancel", "Run" "Run on terminal". I chose run on terminal options and the result is as attached screen shot. please refer and help. In the screen shot any one can see a small window appeared having no message in window and in button. what is is upto?

---

### Post by miggols99 on 2008-09-05
Try running

```
sudo sh ./ati-driver-installer-8-8-x86.x86_64.run
```

---

### Post by mailtwogopal on 2008-09-06
Hi miggols,

Same error thrown. :(

```

gopal@gopal-desktop:~$ sudo sh ./ati-driver-installer-8-8-x86.x86_64.run
sh: Can't open ./ati-driver-installer-8-8-x86.x86_64.run

```

---

### Post by mailtwogopal on 2008-09-06
Hi billgold,

  I followed the link "customizing ubuntu". One of the thing dint work for me is setting window borders, menus transparent. I set all the steps it stated, but it dint work for me. Also can any one help with this?

---

### Post by zxscooby on 2008-09-06
A red stapler maybe, and some multi-colored post it notes.

---

### Post by Saint Angeles on 2008-09-06
> **mailtwogopal said:**
> Hi miggols,

Same error thrown. :(

```

gopal@gopal-desktop:~$ sudo sh ./ati-driver-installer-8-8-x86.x86_64.run
sh: Can't open ./ati-driver-installer-8-8-x86.x86_64.run

```

dude... navigate to your desktop first (cd Desktop) then run the sh ati... command

---

### Post by mailtwogopal on 2008-09-06
Hi saint,

  Am posting the result of using command cd desktop below:

```

gopal@gopal-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory

```

---

### Post by jespdj on 2008-09-06
**D**esktop, not **d**esktop. Filenames are case sensitive.
```
cd Desktop
```

---

### Post by mailtwogopal on 2008-09-06
Hi jespdj,

  Ya i tried that option, it worked. So i was following all the steps from [here]("http://ubuntuforums.org/showpost.php?p=4749740&postcount=12"). At the end as suggested i restarted my PC. All of a sudden after booting, i got a screen which has colours splashing here and there, in which i can do nothing. Only my mouse works. i restarted and tried again, even then i landed to same screen (Probably its a login screen which looks so) as above in which i can do nothing. Then i restarted again and in grub boot loader i booted thru recovery mode and chose the option to "repair broken package" and checked "Xorg" one time and resumed to normal boot. Now it is working fine. But i am not sure what the change may happened because i can't feel it. any way i executed command "lspci" and the result is below:

```

gopal@gopal-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Why i pasted the above code is to check with you guys whether the graphics card what i have suits to it or not. Thats why. Expecting replies.

---

### Post by Saint Angeles on 2008-09-06
what does ```
glxinfo | grep direct
``` give ya?

(i'm really really sorry if i didn't say that politely)

---

### Post by mailtwogopal on 2008-09-06
Hi saint,

 here is the result:

```

gopal@gopal-desktop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

What is it for basically?

---

### Post by Saint Angeles on 2008-09-07
> **mailtwogopal said:**
> Hi saint,

 here is the result:

```

gopal@gopal-desktop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```What is it for basically?

basically, the command i gave ya will take the output of "glxinfo" and search for a line containing the word "direct" and spit it out.

this tells you that you ARE NOT getting direct hardware rendering with your card right now. i am going through this same mess because i stupidly upgraded to intrepid last night without checking to see if fglrx works with it yet (it doesn't).

what this means is that you wont get the cool 3d features you want. you can still watch videos and get a good resolution... but we need to figure out whats wrong with your driver.

---

### Post by mailtwogopal on 2008-09-08
Hi saint,

  Sorry for delay in reply. My monitor got into  power problem and am  not getting power from CPU. Today it ll be solved. So what can be done on this. do i need to send any further details about my hardware etc?

---

### Post by mailtwogopal on 2008-09-08
hi saint,

  Am at home now. My monitor power problem got resolved. i will search some stuff regarding this and post u if i get any solution. expecting replies from experts in this forum.

---

### Post by Saint Angeles on 2008-09-15
what resolution is the best for your monitor...

for example: my monitor is a samsung 941bw that likes 1440x900. its a widescreen LCD monitor. most people have a normal aspect ratio monitor... so you probably want either 1024x768 or 1280x1024.

make sure that is setup in your xorg.conf file.. can you post your xorg.conf file for us?

its located at /etc/X11/xorg.conf

open it with ```
sudo gedit /etc/X11/xorg.conf
``` then save it as a different file on your desktop. (file->save as) i choose xorg.txt so its easy to upload onto this site.

now what you might wanna do, before editing your xorg.conf file with all those extra things in my tutorial, is run the aticonfig thing first...

```
sudo aticonfig --initial
``` go through the steps answering as much as possible. after its done, go through with the xorg.conf steps of my tutorial once again.

lemme know if you run into any hiccups or require aditional explanation.

---

### Post by mailtwogopal on 2008-09-15
Hi saint,

 i hereby uploaded my xorg file which is saved in text format. Also out of fear i ask you one thing is that if i do again the steps etc will i be landed to a screen which splashes color like anything as before with which i cannot do anything. Will it lead to any problem? Also my monitor is the Samsung Syncmaster 594MG a CRT monitor with best resolution of 1024*768. Also i dint find anything as resolution size in xorg file.

 And now at first i installed ati driver in pc and in thru terminal window. finally i got the screen as attached and in that window i could read nothing, Also please look into it. i did nothing in that screen. i hope two options are there and two buttons too. i just closed that window.

---

### Post by cardinals_fan on 2008-09-15
> **mailtwogopal said:**
> Hi all,

  I am having ubuntu hardy in my box. I am not sure whether am right to be here to ask you guys about how i can have my Desktop richer than one of my friend who owns windows vista. The idea is, apart from using background images to make the desktop richer, how to an extent i can customize my desktop. This question may be silly but it is due to the fact that i may not aware of using or customizing ubuntu hardy desktop. Please help me. Hope guys understand what i need.
That depends on your definition of "richer".  I would personally recommend installing/configuring a lightweight WM such as Openbox for a clean, minimal style.  If you want shiny things, try out Gdesklets, Wbar, and tweak your Compiz with CCSM.

---

### Post by kingbilly on 2008-09-15
> **Saint Angeles said:**
> you dont even need advanced desktop effects (compiz) to make your desktop pretty!

take a look at my current setup. (i have anxiety problems and i change my theme about every 3 days)


We share the same symptoms :)

---

