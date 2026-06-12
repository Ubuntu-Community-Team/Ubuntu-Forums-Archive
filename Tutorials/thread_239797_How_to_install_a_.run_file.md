---
title: "How to install a .run file"
date: 2006-08-19
forum: Tutorials
---

### Post by fatsheep on 2006-08-19
For those of you that have been using Ubuntu for a while, you probably already know this.  I'm posting this for the newbies that download a game installer in .run format and have no idea what to do with it.

**How to Install a .run File:**

For this How To I am going to be using the dummy name "example.run".   You should replace this with the name of the file you are trying to install.

1.  Open a terminal.  In Gnome the terminal is found in Applications>Accessories>Terminal.
2.  Navigate to the directory of the .run file.  For this example, I have mine on the desktop so I would  type in "cd ~/Desktop" and press enter.
3.  Type "chmod +x example.run" (press enter).
4.  Now type "./example.run", press enter, and the installer will run.

---

### Post by professorTHC on 2007-11-06
Thanks! =D

---

### Post by WaySensei on 2008-01-22
What about uninstalling these? I have UFO: Alien Invasion installed on my box, but I want to remove it. Is it enough to delete the directory it's located in, or is there another, better method?

---

### Post by erfahren on 2008-01-22
this page is a good reference (although I don't think .run installers are there): [How to install *ANYTHING* in Ubuntu!](http://monkeyblog.org/ubuntu/installing/)

those programs often put an uninstaller script in their main directory, in the directory do: 
"sudo ./uninstaller_script_name" (whatever the name of it is) - or - "sudo  /*path_to_it*/uninstaller_script_name" of course.

there is a great little application that comes in handy for stuff like that - called "nautilus-open-terminal" (available in Synaptic - or "sudo apt-get install nautilus-open-terminal") - it puts a selection in the right-click context menu to open a directory in the terminal. (Xubuntu 7.10 has something like that included).

---

### Post by WaySensei on 2008-01-22
There is an uninstall script in the /usr/local/games/ufoai directory that I wish to uninstall, but when I try to run the uninstaller script by typing: 
```
./uninstall
```, there is an error that: ```
Could not find a usable uninstall program. Aborting.
``` I think it must be a bug with the uninstall script for ufoai. I am thinking of simply trashing the directory in order to remove the program and clear the space, but would like other thoughts on the matter before I do.

---

### Post by tim15856 on 2008-01-23
> **WaySensei said:**
> What about uninstalling these? I have UFO: Alien Invasion installed on my box, but I want to remove it. Is it enough to delete the directory it's located in, or is there another, better method?


Since I'm getting ready to install this game I wanted to know why you want to uninstall it. Don't like it? Did you play XCOM? How does it compare?

---

### Post by WaySensei on 2008-01-23
The game itself is fine. When I installed from a .run file, however, the game would not start. I then installed it from a .deb package from getdeb.net, and it worked fine. However, now I have two installs on my computer and want to get rid of one of them.

---

### Post by tim15856 on 2008-01-24
Yeah, I'm having troubles getting it to work too. I'm not on my Ubuntu system, so I don't have the error code in front of me, but it is missing something. I found one post that said to fix that problem, I need to create a link. But the link command he used didn't work. The file wasn't in the directory his command showed. This problem appears to show up in the 64 bit version. I'll try again later, if it continues to give me a hard time, I'll try the deb.

---

### Post by erfahren on 2008-01-24
> **tim15856 said:**
> Yeah, I'm having troubles getting it to work too. I'm not on my Ubuntu system, so I don't have the error code in front of me, but it is missing something. I found one post that said to fix that problem, I need to create a link. But the link command he used didn't work. The file wasn't in the directory his command showed. This problem appears to show up in the 64 bit version. I'll try again later, if it continues to give me a hard time, I'll try the deb.
search for the file you need like:
```

sudo find / -name *name-of-file*

```
then to make a symlink make it *from* the file *to* where it goes 

it might be possible that you don't have the library package (or other dependency) installed that the file is a part of (you probably thought of that already I guess)

---

### Post by zeus thunder on 2008-01-29
[SIZE="3"]i have tried the samething to install .run file of america's army.
but i still get ">"  after pressing enter after "./example.run"[/SIZE]:

[SIZE="3"]Thanks in advance[/SIZE]

---

### Post by eram on 2008-07-26
Ok, so I followed your instructions to install a .run file. every thing went fine until after I did the last step: (sudo ./example.run) I got an error message: "Your appear to be running an X server; please exit X before installing."

Can anyone help with this?
Thanks!

---

### Post by ice60 on 2008-07-26
> **eram said:**
> Ok, so I followed your instructions to install a .run file. every thing went fine until after I did the last step: (sudo ./example.run) I got an error message: "Your appear to be running an X server; please exit X before installing."

Can anyone help with this?
Thanks!
are you trying to install a graphics driver? you'd be better off finding a tutorial for it if you are. it's telling you to kill all the GUI stuff and just use a terminal.

---

### Post by eram on 2008-07-26
Yes, I am installing a graphics card driver. They only provide a README for Suse installation. I don't mind killing the GUI, I have a lot of experience in terminal. But I have never yet encountered a .run file, so I don't know what to do.

---

### Post by PinkFloyd102489 on 2008-07-26
You can still sh a run file. I do this all the time with the Nvidia drivers.

```
sh whatever.run
```

---

### Post by eram on 2008-07-26
> **PinkFloyd102489 said:**
> You can still sh a run file. I do this all the time with the Nvidia drivers.

```
sh whatever.run
```

No, it says I need to do it as root.
I do ```
sudo sh N*.run
``` but it tells me to exit X.

---

### Post by ice60 on 2008-07-26
you run this -
```
ctrl-alt-F1
```
that will get rid of your desktop, so save anything first. then run this -
```
init 3
```
then -
```
gdm stop
```
then login, that bit might be earlier, it's says login, or something like that. then, if the nvidia driver is on your desktop cd to your desktop and run it like this -
```
cd ~/Desktop <enter>
sudo sh NVIDIA-Linux-xxxx.run
```
replace the xxxx with what the driver is called. at some point you might get an error about /tmp/.X0-lock, or something like that, you can remove it like this -
```
sudo rm /tmp/.X0-lock
```

you can reboot like this -
```
sudo reboot
```
OR incase that doesn't work for some reason
```
sudo shutdown -r now
```

i've never installed a graphics driver like that in ubuntu, that's just from old notes i made for installing the nvidia driver on linux. i don't think anyone installs the driver like that on ubuntu.

---

### Post by eram on 2008-08-02
> **ice60 said:**
> you run this -
```
ctrl-alt-F1
```
that will get rid of your desktop, so save anything first. then run this -
```
init 3
```
then -
```
gdm stop
```
then login, that bit might be earlier, it's says login, or something like that. then, if the nvidia driver is on your desktop cd to your desktop and run it like this -
```
cd ~/Desktop <enter>
sudo sh NVIDIA-Linux-xxxx.run
```
replace the xxxx with what the driver is called. at some point you might get an error about /tmp/.X0-lock, or something like that, you can remove it like this -
```
sudo rm /tmp/.X0-lock
```

you can reboot like this -
```
sudo reboot
```
OR incase that doesn't work for some reason
```
sudo shutdown -r now
```

i've never installed a graphics driver like that in ubuntu, that's just from old notes i made for installing the nvidia driver on linux. i don't think anyone installs the driver like that on ubuntu.

Thanks! It worked! I ended up uninstalling the driver again because it did not solve my graphics problem. But I was able to solve my problem a different way: It was a simple matter of editing the xorg.conf file.
Thanks again!8)

---

### Post by coolest30 on 2008-08-02
as regards step 4 once i have press enter it comes up with permission denied can any one help?

thanks in advance.

---

### Post by Dfairlite on 2008-10-13
works great!

---

### Post by flower199 on 2009-01-03
Thank you, very useful!

---

### Post by kevincolorado on 2009-05-23
This is what terminal says:
"================================================= =
ATI Technologies Linux Driver Installer/Packager
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.dSEiPN
kevin@kevin-desktop:~/Desktop$ "

What happened?

---

### Post by Brandaho on 2009-06-11
> **kevincolorado said:**
> This is what terminal says:
"================================================= =
ATI Technologies Linux Driver Installer/Packager
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.dSEiPN
kevin@kevin-desktop:~/Desktop$ "

What happened?


When I went to ATI's website, I chose Linux 86_64 because I have a 64 bit system. It works with Ubuntu 9 thats for sure. So it might be your version, or the incorrect file. Just a guess, but the first post helped me get it completely installed.

---

### Post by ironhorse99 on 2009-06-17
> **fatsheep said:**
> For those of you that have been using Ubuntu for a while, you probably already know this.  I'm posting this for the newbies that download a game installer in .run format and have no idea what to do with it.

**How to Install a .run File:**

For this How To I am going to be using the dummy name "example.run".   You should replace this with the name of the file you are trying to install.

1.  Open a terminal.  In Gnome the terminal is found in Applications>Accessories>Terminal.
2.  Navigate to the directory of the .run file.  For this example, I have mine on the desktop so I would  type in "cd ~/Desktop" and press enter.
3.  Type "chmod +x example.run" (press enter).
4.  Now type "./example.run", press enter, and the installer will run.

I have tried this everywhichway I can & it always says "  No such file or directory"
I have it on my desktop. What am I doing wrong.

---

### Post by ironhorse99 on 2009-06-17
> **ice60 said:**
> you run this -
```
ctrl-alt-F1
```
that will get rid of your desktop, so save anything first. then run this -
```
init 3
```
then -
```
gdm stop
```
then login, that bit might be earlier, it's says login, or something like that. then, if the nvidia driver is on your desktop cd to your desktop and run it like this -
```
cd ~/Desktop <enter>
sudo sh NVIDIA-Linux-xxxx.run
```
replace the xxxx with what the driver is called. at some point you might get an error about /tmp/.X0-lock, or something like that, you can remove it like this -
```
sudo rm /tmp/.X0-lock
```

you can reboot like this -
```
sudo reboot
```
OR incase that doesn't work for some reason
```
sudo shutdown -r now
```

i've never installed a graphics driver like that in ubuntu, that's just from old notes i made for installing the nvidia driver on linux. i don't think anyone installs the driver like that on ubuntu.

I did everything line by line & it says "that it appears I'm runing X-server".
I've exited the GUI by ctrl-alt-F1. Now I type everything in.....still a no/go.
What does happen is the driver starts to uncompress & then I get that message.....whats going on??????

---

### Post by TattooCharlie on 2009-08-31
that was easy. thanks alot for the how to man :)

---

### Post by F. B. I. Guy on 2009-11-23
when i tryed to run the gmd stop command i got this: ** (gdm-binary:2233): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.70" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

please help with this,
and thank you in advance

---

### Post by bhavana on 2009-12-09
Thank You. This was very helpful.

---

### Post by doris orange on 2010-01-07
cheers from noobville!

---

### Post by AMadDog on 2010-01-30
I know this doesn't have a lot to do with this thread but i want to run a .exe file of a cd how do I do that? I have tried just clicking on it but it goes to the archive manager and then says there is an error please help
cheers

---

### Post by E7uber on 2010-02-18
Hi,

Noob here. I want to play America's Army. I downloaded a .run file except I have what I think are security issues on install. It says write access denied. I'm very new to Ubuntu.

Thanks in advance.):P

---

### Post by jamesrfla on 2010-02-18
Try typing sudo before the command you run. Then enter your password and that should work. Only use sudo when you have to.

---

### Post by Uberche on 2010-02-20
I am trying to install A Tale In the Desert which is a .run file. I navigate to Downloads which is where it is and I type 

chmod -x eClient-linux-i686.run 

and hit enter and it does nothing, just back to the prompt 

ethan@ubuntu:~Downloads$ chmod -x eClient-linux-i686.run
ethan@ubuntu:~Downloads$

is what I end up with... any thoughts of what stupidity I'm doing here? 

Thanks as I'm new to Linux, liking it... just a bit of a learning curve.

---

### Post by Uberche on 2010-02-21
1) Right Click - Properties - Permissions - Allow executing as a program 

2) Double Click

3) Feel like idiot.

---

### Post by Thonyv on 2010-03-25
> **ice60 said:**
> you run this -
```
ctrl-alt-F1
```
that will get rid of your desktop, so save anything first. then run this -
```
init 3
```
then -
```
gdm stop
```
then login, that bit might be earlier, it's says login, or something like that. then, if the nvidia driver is on your desktop cd to your desktop and run it like this -
```
cd ~/Desktop <enter>
sudo sh NVIDIA-Linux-xxxx.run
```
replace the xxxx with what the driver is called. at some point you might get an error about /tmp/.X0-lock, or something like that, you can remove it like this -
```
sudo rm /tmp/.X0-lock
```

you can reboot like this -
```
sudo reboot
```
OR incase that doesn't work for some reason
```
sudo shutdown -r now
```

i've never installed a graphics driver like that in ubuntu, that's just from old notes i made for installing the nvidia driver on linux. i don't think anyone installs the driver like that on ubuntu.

I am attempting to use this method to install the new nvidia graphics driver and all goes well until I try to stop the GDM. I get an error message saying to cannot acquire name. I ran the gdm stop command with sudo but it still didn't work. I tried to install the driver anyway and it said the X server was stil running, so I assume that I have to stop it somehow. The instructions in nvidia's readme file aren't clear on how to stop the X server either.

Any help is greatly appreciated

**I dug a little deeper and found that I had to use 

$ sudo /etc/init.d/gdm stop

Driver is now installed and working great. Thanks all for the information

---

### Post by dakkar9999 on 2010-05-08
Thanks!  Worked perfectly!

---

### Post by groundwire123 on 2011-02-09
> **fatsheep said:**
> For those of you that have been using Ubuntu for a while, you probably already know this.  I'm posting this for the newbies that download a game installer in .run format and have no idea what to do with it.

**How to Install a .run File:**

For this How To I am going to be using the dummy name "example.run".   You should replace this with the name of the file you are trying to install.

1.  Open a terminal.  In Gnome the terminal is found in Applications>Accessories>Terminal.
2.  Navigate to the directory of the .run file.  For this example, I have mine on the desktop so I would  type in "cd ~/Desktop" and press enter.
3.  Type "chmod +x example.run" (press enter).
4.  Now type "./example.run", press enter, and the installer will run.
______________________________________________________________

Thank you much. I have been pulling hair out of my head!!! by the way, my new 11.1 ati drivers and hd radion 5870 thank you to.

---

### Post by FreymanX on 2011-06-12
Hello how do you run it as a Admin this is what i get

VirtualBox Version 4.0.8 r71778 (2011-05-16T16:58:14Z) installer
This program must be run with administrator privileges.  Aborting

---

### Post by Slasher The Great! on 2011-06-22
thanks

---

### Post by geazzy on 2011-06-24
nice tutorial :)

---

### Post by mujahied on 2011-07-10
thanks very usefull

---

### Post by lukas_adler on 2011-07-13
Thank you for this yet simple
but yet very helpful tutorial. *lolthnx*

---

### Post by Sebastian-Li on 2011-07-22
Thanks!!!

---

### Post by Darryl_Gittins on 2011-09-16
If this is for "newbs" then it should explain how to open a terminal, and how to  navigate. 

IT shouldn't be rocket science to install a driver in Ubuntu. You shouldn't need to type esoteric commands. In Windows, you double click thie driver to install it. This is why people prefer Windows.

---

### Post by derekhammer on 2011-11-20
Hello, when I get to step four and type ./whatever.run , it says permission denied. what do i have to do? thanks Derek

---

### Post by john.williams43 on 2013-02-06
Perfect, thanks for this

---

### Post by CodeSunil on 2013-02-15
thanx :)

---

### Post by Vegeto Tr7 on 2013-06-30
thanks a lot mate!

---

### Post by ayberkoktay on 2014-02-28
Thanks

---

### Post by umithaz on 2014-02-28
This is summary of Linux :) install and uninstall, good examples. Thanks!

---

### Post by edde2 on 2014-05-26
Thanks!
But if you get a error that says "Alredy Exists!" or some thing add " --force" at the end of the last command. ;)

---

### Post by edde2 on 2014-05-26
?

---

### Post by edde2 on 2014-05-26
:lolflag:

---

