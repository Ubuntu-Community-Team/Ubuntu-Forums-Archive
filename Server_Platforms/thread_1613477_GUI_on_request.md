---
title: "GUI on request"
date: 2010-11-04
forum: Server Platforms
---

### Post by Gheter on 2010-11-04
Okay. This is my first post so please forgive any mistakes.

I installed Ubuntu Server 10.04 and then GNOME GUI. Now what I want is that when the system starts it boots into the command line and only goes to GNOME when the specific command is typed

Please help me with this

Thank You

---

### Post by arrrghhh on 2010-11-04
> **Gheter said:**
> Okay. This is my first post so please forgive any mistakes.

I installed Ubuntu Server 10.04 and then GNOME GUI. Now what I want is that when the system starts it boots into the command line and only goes to GNOME when the specific command is typed

Please help me with this

Thank You

Remove gdm from init.d ```
sudo update-rc.d gdm remove
```  Now gdm won't start on its own - simply do a ```
sudo service gdm start
``` if you want to start it.

With that said, why are you running a GUI on a server?  It's usually easier to just install ubuntu-desktop, not -server.  You can run all the same services on ubuntu-desktop that you can on -server...

---

### Post by david.garceau on 2010-11-04
the reason i found was setting up raids more easily. his may be different though, just throwing in my two cents :)

---

### Post by minaev on 2010-11-04
Even so, it would be more reasonable to use X tunneling from a workstation with GUI.

---

### Post by arrrghhh on 2010-11-04
> **minaev said:**
> Even so, it would be more reasonable to use X tunneling from a workstation with GUI.

+1.  Tunneling SSH over X to just setup one application is much better than installing GNOME just for that :p

Webmin is a great tool to configure things remotely with a GUI as well.

---

### Post by Gheter on 2010-11-05
Thank you [COLOR=Black]arrrghhh.
I was running a server os because i wanted to learn how to use it.
I added a gui because I find it much easier to update Ubuntu that way

Thanks
[/COLOR]

---

### Post by Gheter on 2010-11-05
[COLOR=Black]Thank you for your reply again arrrghhh but after doing it Ubuntu still booted into GNOME.

Any other solution?

Thank you
[/COLOR]

---

### Post by arrrghhh on 2010-11-05
> **Gheter said:**
> Thank you [COLOR=Black]arrrghhh.
I was running a server os because i wanted to learn how to use it.
I added a gui because I find it much easier to update Ubuntu that way

Thanks
[/COLOR]

You can use the console on the -desktop edition of ubuntu as well... CTRL-ALT-F1.

Also, what's hard about sudo apt-get update?  ...

I'm pretty sure that's all it is.  I don't have a DE on my server.  I'm also not sure what you installed.  Did you install the full ubuntu-desktop?  Just x11...?

---

### Post by sisco311 on 2010-11-05
> **Gheter said:**
> [COLOR=Black]Thank you for your reply again arrrghhh but after doing it Ubuntu still booted into GNOME.

Any other solution?

Thank you
[/COLOR]

Edit the /etc/default/grub file and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then generate a new grub2 config file:
```
sudo update-grub
```

---

### Post by arrrghhh on 2010-11-05
> **sisco311 said:**
> Edit the /etc/default/grub file and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then generate a new grub2 config file:
```
sudo update-grub
```

O____o I thought that just disabled the splash screen.  I didn't realize that disabled GDM from starting too... Thanks!  Gheter let us know how this works.

Gheter, if it doesn't try [this](http://www.uluga.ubuntuforums.org/showpost.php?p=9691917&postcount=2).

---

### Post by sisco311 on 2010-11-05
If the text, -s, s, S or single kernel parameter is present, then GDM's [Upstart]("http://upstart.ubuntu.com/") job (/etc/init/gdm.conf) does not start the display manager.

---

### Post by Gheter on 2010-11-05
sisco311 thank you.
Your method worked perfectly
Everyone thank you for all your help.

---

