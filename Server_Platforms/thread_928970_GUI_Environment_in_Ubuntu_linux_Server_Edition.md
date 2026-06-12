---
title: "GUI Environment in Ubuntu linux Server Edition"
date: 2008-09-24
forum: Server Platforms
---

### Post by 802.1x on 2008-09-24
Can I use a GUI environment in Ubuntu Server Edition? If so, how can I enable that?

Thanks

-Reza

---

### Post by alastair on 2008-09-24
Yes. 

You can just install the desktop stuff in the usual way (apt-get, aptitude etc.). Perhaps try installing "ubuntu-desktop" - this will probably pull in a lot of dependencies though.

Alastair

---

### Post by lazyart on 2008-09-24
sudo tasksel

---

### Post by 802.1x on 2008-09-24
Thanks for your replies.

I am new in Linux, so...

Anyway; when the server comes up, I issue the "startx" command to start the server in GUI environment. Using this command is allowed in Ubuntu?

When I issue the "startx" command, the output this is display is:

The program 'startx' is currently not installed. You can install it by typing:

```
sudo apt-get install xinit
-bash: startx: command not found
```

Now when I execute the "sudo apt-get install xinit" command, the following output appears:

```
Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package xinit
```

How can I solve this problem?

Thanks again;

-Reza

---

### Post by Dragonbite on 2008-09-24
I think you need to subscribe to a few repositories which include the traditional GUI stuff.  I am sorry, I am not in front of my Ubuntu right now to see what the repositories are. Perhaps somebody has that information at their fingertips.

Actually, I htink there is a config file with the list of repositories installed as part of apt, and the GUI (base) ones are commented out.  Find that, uncomment them and run ```
apt-get update
```should do the trick.

Sorry I can't be more specific right now.

---

### Post by Dr Small on 2008-09-24
I think all you need to do is,
```
sudo apt-get install xorg
```

But servers are not intended for burdening GUI. Set everything up from the command line, install OpenSSH-Server, and then move to another computer and administrate the system.

---

### Post by hyper_ch on 2008-09-24
why do you want a gui on a server or what makes you think that you need one?

---

### Post by TomB19 on 2008-09-24
I like having a GUI on my firewall.  It is extremely convenient and productive to have a alarm window, log files, firewall config, and other windows open, all at the same time.

For ftp/web/samba/ntp/dhcp/smtp, etc., I don't see any advantage to a GUI at all.

Anyway, run what you want.  That's a big part of what makes Linux so great.

I'm a big fan of KDE so I run KDE on my firewall and desktop systems.  If you get the Ubuntu desktop, you will end up with Gnome (also a very good GUI environment).  If you want to stay small and light, there are tons of options all the way down to the diminutive FluxBox.

Get yourself some x.org and a window manager and enjoy.

---

### Post by cariboo on 2008-09-24
You really don't need a full gui to do what you want, just install the gui apps you think you'll need without installing X, then just use X forwarding to run the app on the local computer. the commands should look something like this:

```
ssh -X username@server
```

Then to run synaptic for example:

```
sudo synaptic
```

Jim

---

### Post by brad8266 on 2008-09-24
Everyone is going to tell you not to bother running a GUI on a server because it can easily all be administered remotely and even use a GUI remotely without installing any desktop components. Webmin can configure the Linux firewall also in addition to a lot of other tasks.

If you really want to install the desktop:
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install ubuntu-desktop


Its that easy. It will eat up some memory and such and really is not optimum in a server.

I use putty for a remote CLI and I use Webmin for almost all of my other server tasks. Webmin really is pretty high speed and you can do all your admin tasks between Webmin and putty. You really have no need for a server desktop.

---

