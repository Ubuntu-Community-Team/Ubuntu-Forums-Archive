---
title: "Run windows software from Linux"
date: 2009-01-15
forum: Wine
---

### Post by hberaldi on 2009-01-15
Hi guys,

I am totally lost here. Is there a way to access and run Windows XP-based software without leaving Ubuntu?

The specific software I am concerned about are GraphPad (Prism 5) and Minitab v. 15. I have not found anything like it on Linux, but I wonder if there is a way by which Ubuntu can 'create' a windows environment where to run those applications without having to reboot the computer on Windows...

Please help. Many thanks.

---

### Post by blazemore on 2009-01-15
Yes it's very straightforward.
Run the following commands from the Terminal:
```
sudo su
```
enter your password and press Enter.

Then run
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | apt-key add -
```

Then,
```
wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list && apt-get update
```

Now install the program called Wine:

```
apt-get install wine
```

Now you can run .exe programs by right-clicking and choosing "Wine Windows Program Launcher", or by running from the Terminal:
```
wine /path/to/programname.exe
```

---

### Post by 2hot6ft2 on 2009-01-15
There you go /\

It's called wine. Look in Applications>Wine
Plenty of info for it at [http://appdb.winehq.org/](http://appdb.winehq.org/)

If you don't already have it which would surprise me then install it either thru Applications>Add/Remove or synaptic
System>Administration>Synaptic Package Manager
By simply searching for it and installing it.

I don't use it myself so beyond that I can't help you.

---

### Post by HyperHacker on 2009-01-15
sudo apt-get install wine

Wine is a compatibility layer that lets most Windows programs run on Linux (on PC only) without having to do any emulation or actually have a copy of Windows. You can double-click an EXE to run it just like Windows. It's not very polished though; it's slow and has some graphic bugs, and it won't pop up an error message if the program can't run (it prints to the console, but if you're just clicking the icon, nothing happens).

You can also set up Virtualbox, which is like a virtual computer, and install Windows on it. That's a bit slower and less convenient, but anything that doesn't need hardware acceleration should work. (IIRC, Vista deliberately refuses to run or refuses to enable something. XP works fine.)

[edit] Beat me to it. Just a warning, if you do all of these in one go:

> **blazemore said:**
> Yes it's very straightforward.
Run the following commands from the Terminal:
```
sudo su
```
enter your password and press Enter.

Then run
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | apt-key add -
```

Then,
```
wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list && apt-get update
```

Now install the program called Wine:

```
apt-get install wine
```
**Run "exit" here** before continuing to log out of the root account and go back to normal user mode. Running Windows apps as root is a bad idea.

---

### Post by blazemore on 2009-01-15
The reason the first few steps are important, is it will ensure your system gets updates for Wine with its normal system updates. This ensures the best compatibility and performance with Windows applications.

However, you don't have to use them. There's a slightly older version of Wine in the repos already.

---

### Post by stchman on 2009-01-15
> **hberaldi said:**
> Hi guys,

I am totally lost here. Is there a way to access and run Windows XP-based software without leaving Ubuntu?

The specific software I am concerned about are GraphPad (Prism 5) and Minitab v. 15. I have not found anything like it on Linux, but I wonder if there is a way by which Ubuntu can 'create' a windows environment where to run those applications without having to reboot the computer on Windows...

Please help. Many thanks.

Yes WINE is in the repositories since Gutsy.

```
sudo apt-get install wine
```

The reason to run Linux is to run....Linux.  Not to run Windows programs under Linux.  TO this date I run all my programs native under Linux.  I am amazed all the time when there is a program in the repos that fits the bill.

Now if you need to run a Windows program using WINE please do not be one of those folks that judge Ubuntu 100% on how well it runs Windows programs.  Too many times there are folks that try Linux thinking it is a free Windows when it is not.  They may have somewhat similar looking GUIs but under the hood is VERY different.

---

### Post by 2hot6ft2 on 2009-01-15
> **hberaldi said:**
> Minitab v. 15. I have not found anything like it on Linux, 
Nothing found for GraphPad but here's a linux alternative for Minitab
[http://linuxappfinder.com/package/r-recommended](http://linuxappfinder.com/package/r-recommended)
Scroll down to your version of ubuntu to get the appropriate one.

---

### Post by blazemore on 2009-01-15
2hot, you beat me to it :P
But it's nice to use your favourite apps, like me, I use utorrent.
ps has anyone found the guide to integrating Wine apps with your linux theme? It had a side by side comparison of the names of different parts so you could colour-pick your way to integration bliss.

---

### Post by 2hot6ft2 on 2009-01-15
> **blazemore said:**
> 2hot, you beat me to it :P
But it's nice to use your favourite apps, like me, I use utorrent.
ps has anyone found the guide to integrating Wine apps with your linux theme? It had a side by side comparison of the names of different parts so you could colour-pick your way to integration bliss.
Didn't know we were racing...:P You were explaining wine meanwhile I did a search for them. The OP may want these for any other linux  alternatives
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.gimpshop.com/](http://www.gimpshop.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

---

### Post by hberaldi on 2009-01-15
Wine is a compatibility layer that lets most Windows programs run on Linux (on PC only) without having to do any emulation or actually have a copy of Windows. 

So I do not even need to have WXP installed on a different partition?

---

### Post by albinootje on 2009-01-15
> **hberaldi said:**
>  So I do not even need to have WXP installed on a different partition?

Correct. 
With Wine on Linux you don't need a license for MS-Windows.

For your information, there's also commercial options for Wine :
[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)
[http://en.wikipedia.org/wiki/Cedega](http://en.wikipedia.org/wiki/Cedega)

Another option is using VirtualBox with MS-Windows as guest VM on it. 
If you want to try that, don't forget to install the Guest Additions :
[http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

---

### Post by scouser73 on 2009-01-15
Virtualbox, as described in this blog. [http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/]("http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/")

---

### Post by blazemore on 2009-01-16
Wine first, virtualbox is a completely different kettle of fish.

---

### Post by hberaldi on 2009-01-18
Thank you all for your input. 

I installed both, Wine and VirtualBox, but never got the result I expected. Small programs (e.g. PhotoEd, Notepad, Calculator, etc.) work flawlessly, but more complex ones (e.g. Corel Draw, Photoshop, Minitab) do not work properly.

I tested several different options and concluded that, if you need windows software, to trust that your work will be done under safe and reliable conditions, you should run those within windows, and not from linux.

Thanks again.

HB

---

### Post by SunnyRabbiera on 2009-01-18
> **hberaldi said:**
> Thank you all for your input. 

I installed both, Wine and VirtualBox, but never got the result I expected. Small programs (e.g. PhotoEd, Notepad, Calculator, etc.) work flawlessly, but more complex ones (e.g. Corel Draw, Photoshop, Minitab) do not work properly.

I tested several different options and concluded that, if you need windows software, to trust that your work will be done under safe and reliable conditions, you should run those within windows, and not from linux.

Thanks again.

HB

well it depends, like with photoshop it depends on the version.
If you need a more commercial approach that might work better for you there is always crossover office.
[http://www.codeweavers.com/](http://www.codeweavers.com/)

Its not free but its development goes out to wine.

---

