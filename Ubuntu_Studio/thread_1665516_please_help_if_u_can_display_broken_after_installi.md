---
title: "please help if u can: display broken after installing Ubuntu Studio Maverick"
date: 2011-01-12
forum: Ubuntu Studio
---

### Post by youWho on 2011-01-12
*Fortunately* I decided to install  Ubuntu Studio Maverick onto a separate  partition, so as to be able to  keep the (working) Ubuntu Studio Lucid install I have. I say  "fortunately" because after installing Maverick I've had quite some  difficulties. The first, and actually a minor thing, was getting to the internet. It would seem that  Ubuntu Studio doesn't include network-manager by default and for those  of us who are new to Ubuntu Studio understanding what's wrong can be frustrating  (I'm not a total noob, though I'm new to GNU/Linux and not a  programmer). For those who have this problem, (briefly) it was solved by: adding the DVD to the repositories  used by Synaptic; inserting the DVD; installing the network-manager (to  which was automatically added network-manager-gnome plus others);  getting that configured, reset and working... Al fin internet.

Next I ran System->Administration->Update Manager to bring the OS up to date. All went well.

*** But here's the main thing: ***
After a restart I tried System->Administration->Hardware Drivers  to "activate" the proprietary nvidia driver for the Sony Vaio  VPCF116FX (NVIDIA GeForce GT 330M)---this is what had eventually gotten the display working  properly in the Lucid case. But after doing that and restarting I  now have a totally dead display, and am at the moment stumped. *Any help  would be appreciated.* The symptom is that the computer boots, but in  the last stages of the boot I get a blank  light purple screen, and that's all. (Ctl-)Alt-F1, 2, etc. don't do anything; the only way I can get to a terminal-like situation is to select in the grub menu  at startup to go to a recovery mode, then to choose a failsafe  (display) mode. Doing that I could finally run "sudo nvidia-xconfig", in  the hope that that might fix it, but no go.

Like I say, if any of you kind folks has any tips I'd appreciate it  (thanks in advance). I've been searching high and low but haven't found  any solutions, I think at least partly because I don't know what the  problem is ("blank purple screen"???)

---

### Post by Strayfolk on 2011-01-13
Thankfully some smart people with Vaio F series laptops have gathered all the info you need into this magnificient page:
[B]
[http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)[/B]

The problem for me with 10.10 was the Nvidia v260 something. They've fixed it now I think. You might want to try to manually install the v256 and edit the xorg.conf as described in this link:

[http://ubuntuforums.org/showthread.php?t=1470822](http://ubuntuforums.org/showthread.php?t=1470822) (Scroll down to #7)

I use 256.52 with the xorg.conf entry above. I need to do this every time I update kernels. Boot screens are displayed incorrectly. There are fixes, but I don't care anymore, sorry.

Much luck, 
Strayfolk (Using a Vaio F12S1E + NVIDIA GeForce GT 330M)

---

### Post by youWho on 2011-01-18
Thanks Strayfolk for your nice comments. Actually I didn't see them, but found a solution. I then kinda spontaneously posted this info to a different thread, just because I had found some extremely useful advice there; then after doing that I thought to paste it here too in case it's useful to somebody. Here's how I did it; first I saw this and found it very helpful:

                     Originally Posted by **vmforno**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9996039#post9996039")                 
                 [I]If you wanna use the nVidia proprietary driver with 10.10 x64, you should use version 256.53
 
The current version 260.19.12 (Oct 2010) will leave you on a blank screen.

The current steps, I've taken on my laptop Sony CW27FX (i5, 4 GB RAM, nvidia GeForce GT 330M):

     Code:
     sudo apt-get --purge remove nvidia*
sudo apt-get install binutils gcc
sh NVIDIA-Linux-x86_64-256.53.run 
The first command uninstalled every nvidia package installed with your distro (nvidia-96, nvidia-173, etc). 
Explanation: if you try the nVidia installer it will halt with a error  message because there is a small piece of code (script) one some of  these packages.

The 2nd will install binutils and gcc. 
Explanation: They are required by the nVidia installer

The 3rd. will install the driver.

Regards,
vm[/I]

[Then wrote this:]

> **youWho said:**
> Thank you so much for the tip. That worked.

If it helps though I should note a few things here that seemed to be  necessary in my case (a Sony Vaio VPCF116FX with an nvidia GT 330M,  Ubuntu Studio Maverick freshly installed from DVD to a clean partition).  The problem I had was that when I installed Ubuntu Studio, and then  used the System->Administration->Additional Drivers menu item to  install the current nvidia driver, when I rebooted all I ever got was a  blank light purple screen, sometimes preceded by a sort of old fashioned  looking Ubuntu logo and a row of dots, but always no working display no  matter what I tried.

First I should say that I think many of us noobs don't know that in the  grub menu at boot you can choose a "recovery" mode, after which you'll  have the opportunity to boot into a "failsafe" display mode, which means  you'll at least have a working if wrong and low res display.

Anyway, based on the tips here I went to nvidia's web site, found the  downloads section for my computer, but didn't download the latest  driver, instead I got the version mentioned above, version 256.53. I  first uninstalled the nvidia drivers using  System->Administration->Additional Drivers, just in case it might  help. Then I also followed vmforno's advice for uninstalling from the  command line. At the next command it turned out that I already had  binutils and gcc, so no worries there. But then when trying to do sudo  sh NVIDIA-Linux-x86_64-256.53.run the installer complained that I had to  quit X and also to be in a different run level. To be honest I didn't  take mental notes, so I'm not sure of the exact sequence, but  essentially what I next did was to first follow the advice on nvidia's  web site about  how to install---the main thing being that in order to  disable nouveau I first created a small text file containing only the  lines:

blacklist nouveau
options nouveau modeset=0

saving it as disable-nouveau.conf, then did chown for it to be owned by  root:root, then moved it to /etc/modprobe.d/ (that is, you end up with  /etc/modprobe.d/disable-nouveau.conf)

After that I think I basically restarted and got into a console style of login, where I ran 

sudo sh NVIDIA-Linux-x86_64-256.53.run

which worked. The display seems all good.

Thanks again everybody here.


That might be confusing. Just trying to copy the post from the other thread... But you get the gist of it.

I'll go now to check the links you suggested Strayfolk.


[Edit:] I just remembered that I had done one more thing before the above sequence of steps that ultimately got the display working. When I was getting the blank screen I rebooted and chose the recovery option in the grub menu, then chose the failsafe mode, then when the boot was finished I tried from the command line:

sudo nvidia-xconfig

in the hope that it might fix the display problem. It didn't, so I edited the xorg.conf file that nvidia-xcconfig generates:

sudo gedit /etc/X11/xorg.conf

adding these lines (many posts talk about how the nvidia driver needs help in getting the size and shape of some screens right, though that was only part of the problem I was having) in the "Device" section of that file:

    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0:/etc/X11/SonyEDID.raw"

Restarting, it turned out that this hadn't solved the problem, so I then did the above mentioned things---uninstalling the nvidia driver, blacklisting nouveau, etc. I notice that I still have this file though, and perhaps it still figures into the solution---for example it might be why the display now has the right size and shape. I dunno, but you might find that you need to do sudo nvidia-xconfig and then to edit the xorg.conf file before everything works.

---

