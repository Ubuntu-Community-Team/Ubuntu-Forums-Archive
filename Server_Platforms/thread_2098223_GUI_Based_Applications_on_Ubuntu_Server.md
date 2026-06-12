---
title: "GUI Based Applications on Ubuntu Server"
date: 2012-12-26
forum: Server Platforms
---

### Post by Zythyr on 2012-12-26
I am interested in running a Ubuntu Server, however I have few questions in regards to it. 

At the moment I have the server running on Virtualbox so I can play around with it to see if it is suitable for my home server needs. 
**Note: My server is not headless... I do have a monitor directly  connected to the server... Thus I am NOT using Putty/SSH to access my  server. **

Is Ubuntu Server completely command line based? 
How would I install and run applications like Gparted, XBMC on Unutnu Server? 
I know CRTL + ALT + F1 to F6 will give me command line view, while CTRL + ALT + F7 will give me GUI view. 

But how do I run something like Gparted on my server and see the GUI? 

How do Install XBMC, set it up, and keep it running so my UPnP devices can access my media? 

I don't want to install ubuntu-desktop on my server, because that would defeat the purpose of having a server right?

---

### Post by 2F4U on 2012-12-26
> Is Ubuntu Server completely command line based? 

The default install comes without any GUI, but you can install what you want.

> But how do I run something like Gparted on my server and see the GUI? 

Those applications run under a desktop environment such as Unity, KDE, XFCE, etc., and you would need to install such a DE from the repositories.

Since you seem to need a desktop environment, why not install the default Ubuntu desktop version with Unity? It comes with the same support (5 years) as the server and can run the same software. It might save you some time to setup.

There are a couple of tutorials available to setup XBMC on Ubuntu. Here is just one of them:

[http://wiki.xbmc.org/index.php?title=How-to:Install_XBMC_on_Ubuntu](http://wiki.xbmc.org/index.php?title=How-to:Install_XBMC_on_Ubuntu)

---

### Post by d4rk0wl on 2012-12-26
Ubuntu Server is the same thing as standard Ubuntu but it has no GUI because on a server there really is no need. If you want a GUI with it, you can simply run 
```
sudo apt-get install ubuntu-desktop
```
A GUI will install on top of the server process. Or if you prefer KDE, XFDE, Openbox ect you can just substitute 'Ubuntu' with what flavor you want 'Kubuntu-desktop' 'xbuntu-desktop' and so forth.

Another thing that might be good to note is there are web based applications you can run on the server (Webmin, CPanel) that gives a GUI feel in assisting the setup and Maintenance of the server. It is good for some who like a GUI but me personally, I don't like the potential security risk involved. :P

---

### Post by ibjsb4 on 2012-12-26
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by CharlesA on 2012-12-26
X11 forwarding is handy for these sort of things as you don't need to run a full blown GUI.

---

### Post by JayKay3OOO on 2012-12-26
I always run Webmin for remote admin on the server because I like it.. Depends how secure you need it to be huh? Home? Not very.

It's best to run a light DE like XFCE if you need one, but you won't really live.

I often use a combination of webmin and SSH.

Alternative if you don't want a de is to run a live CD to do partitions although you can set this all up during the install.

If I were you I'd find a junk machine and get it running live because the VM can only take you so far. I find some things easier to do in Linux server (Ubuntu, fedora, whatever they all end up doing the same stuff) than in Windows server and I've had experience of both.

Don't forget about the Linux Terminal Server project if you want to have a multi user setup as that's easy as Easter to do.

Simples. Google is your local, friendly Ubuntu GOD. Use it. Or don't.

---

### Post by d4rk0wl on 2012-12-26
> **JayKay3OOO said:**
> I always run Webmin for remote admin on the server because I like it.. Depends how secure you need it to be huh? Home? Not very.

You have a good point there, if you just don't open it to the WAN I guess it would be perty secure :lol:

---

### Post by Zythyr on 2012-12-27
What are disadvantages of installing ubuntu-desktop on top of the server? I am guessing GNOME is a desktop environment. Is installing GNOME only sufficent or do I have to install ubuntu desktop? Is there a light weight version of ubuntu desktop which I can install on the server? 

What it mean for a product to have "5 year" support?

---

### Post by ibjsb4 on 2012-12-27
> **Zythyr said:**
> Is there a light weight version of ubuntu desktop which I can install on the server?

Gnome Classic without recommends.

```
sudo apt-get install lightdm gnome-terminal && sudo apt-get install --no-install-recommends gnome-session-fallback
```

---

### Post by CharlesA on 2012-12-27
> **ibjsb4 said:**
> Gnome Classic without recommends.

```
sudo apt get install lightdm gnome-terminal && sudo apt-get install --no-install-recommends gnome-session-fallback
```

+1, thought there are lighter DEs to run if you really need to run a DE.

---

### Post by ibjsb4 on 2012-12-27
> **ibjsb4 said:**
> Gnome Classic without recommends.

```
sudo apt-get install lightdm gnome-terminal && sudo apt-get install --no-install-recommends gnome-session-fallback
```

And I keep forgetting:

The Panels and gnome-terminal will be black on black.  To fix the panels; Alt + right click on panel and go to Properties>background.

For terminal go to Edit>Profile Preferences>Background

---

### Post by SeijiSensei on 2012-12-27
> **CharlesA said:**
> +1, thought there are lighter DEs to run if you really need to run a DE.

I like LXDE myself when I'm not running KDE.  The value of installing a desktop is to provide the X infrastructure to allow you to run GUI applications over an SSH connection.

---

### Post by CharlesA on 2012-12-27
> **SeijiSensei said:**
> I like LXDE myself when I'm not running KDE.  The value of installing a desktop is to provide the X infrastructure to allow you to run GUI applications over an SSH connection.
Indeed. I probably have a ton of KDE dependencies installed on my server cuz of VBox, but it's not running a full GUI.

---

