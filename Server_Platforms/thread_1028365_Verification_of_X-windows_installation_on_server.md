---
title: "Verification of X-windows installation on server"
date: 2009-01-02
forum: Server Platforms
---

### Post by ndnd on 2009-01-02
Hi,
I am new to Linux environment (have had experience with other O.S OpenVMS ). 

I have setup a Ubuntu server the latest version without any problems. 

I need to install a software that requires x-server capabilities. I have looked in the forum and there are several posts. Based on this 

My objective: To minimize usage of resources have therefore have the bare minimum X-server installation to be able to run the software (I have seen it working on of our lab's systems), emacs, (It's okay if the mozilla browser doesn't work-not important). 


I need to do: 

OPTION 1:
> 
sudo apt-get update
sudo apt-get install x-window-system-core gdm synaptic icewm menu
reboot(ctrl+alt+delete)



OPTION 2:
>  
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg
Gdm is what handles your x system starting automatically instead of entering start x at the command line each time you boot. The reconfigure runs the xserver setup so you can configure your system monitor, video card etc.


My concerns:
1) 
GDM should not be installed in my case. This way when I login I start at the terminal and only when I start the application it will start X-server

2) In option 2: Would Desktop installation result in installation of too many additional packages that may be unnecessary ? 

Please let me know if which should be the order of steps (as I mentioned I am new so I would need some details)

If you need more info from my end please let me know. 

Thanks in advance.

---

### Post by cdenley on 2009-01-02
1. You can always disable GDM. I would go with option 1, except skip synaptic, then disable gdm. Technically, All you need is xserver-xorg, but most applications aren't meant to be used without some sort of window manager.
```

sudo apt-get install gdm xserver-xorg icewm
sudo update-rc.d -f gdm remove

```
Then, when you need a GUI:
```

sudo /etc/init.d/gdm start

```

2. Installing the ubuntu-desktop package will install many packages you don't need, even if you skip the recommended ones. It will also install gnome, which is certainly not want you want to run a single application on a server.

---

