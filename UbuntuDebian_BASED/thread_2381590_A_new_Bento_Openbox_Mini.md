---
title: "A new Bento Openbox Mini"
date: 2018-01-02
forum: Ubuntu/Debian BASED
---

### Post by Melodie on 2018-01-02
Hello,

I have been away for several months from the remixing of Ubuntu Openbox Remix versions, but back I am now! Here is a post with some screenshots: [http://forum.linuxvillage.org/index.php/topic,750.msg4251.html#msg4251](http://forum.linuxvillage.org/index.php/topic,750.msg4251.html#msg4251)

The very latest is an Ubuntu Openbox with the usual additions to Openbox which makes it easy to use for all people (openbox-menu makes automatically generated menus, obsession is a fork from lxde-logout, free from depends).

The Bento Sushi versions are small, come without applications or almost. In the latest there is Midori 5.11 to surf the web, Leafpad as editor, and also mc, (a formidable tool! the Swiss knife which needs to be known!). It also has htop to check the processes, kill some, renice, etc.

Here they are: [http://downloads.linuxvillage.org/?C=M;O=D](http://downloads.linuxvillage.org/?C=M;O=D) (the latest on the top). Feel free to test, bring feedback, ask questions and ask for more! :D

Best regards, and Happy GNU Year! :-)
Mélodie

---

### Post by cruzer001 on 2018-01-02
Hello

What display manager are you using and is that the lxpanel I see in the pic?  Maybe you have a list of all installed packages somewhere.

I just want to compare it to say a LXDE install.

Thanks

---

### Post by Melodie on 2018-01-02
Hello,

here is the filesystem.manifest: [http://pastebin.fr/52746](http://pastebin.fr/52746)
and here is the filesystem.manifest-remove: (the packages which are removed at the end of the installation): [http://pastebin.fr/52747](http://pastebin.fr/52747)

I can't take time to write a better presentation yet.

the session manager is lightdm, the window manager is Openbox, the menus are generated thanks to openbox-menu, and the logout/reboot/shutdown/sleep/hibernate is done with obsession which is a fork of lxde-logout (no depends).

What is a display manager? The background can be shown using pcmanfm, or hsetroot&#8230; among others, with this minimalistic version you will need to have a look in /home/user/.config/autostart/* (the directory) and in /home/user/.config/openbox/autostart (the file, which is a link to the "lang" subdirectory). If you choose pcmanfm it will also display the icons. If not, there are other means to display icons&#8230; but not so easy.

At first boot, you will get an openbox right-click menu, from there you can keep English, or select French or German. The austostart symlink in the /home/user/.config/openbox/ will point to either or autostart-fr/de/en file in the "lang" subdir (it will be easier to see it with the directories in front of you).

I suggest once installed you open the console, do a "sudo apt update && sudo apt dist-upgrade && sudo apt install synaptic", for a start.

The top panel is tint2. If you like better lxpanel or any other, you can install it. Lxpanel and Tint2 already have a default configuration under /home/user/.config/ which you can customize as you like best.

---

### Post by cruzer001 on 2018-01-02
Thank you for your time.

LightDM is the display manager, you just calling it the session manager.  Probably what everyone calls it on your side of the pond :D

Anyhow thanks again

---

### Post by Melodie on 2018-01-02
> **cruzer001 said:**
> Thank you for your time.

LightDM is the display manager, you just calling it the session manager.  Probably what everyone calls it on your side of the pond :D

Anyhow thanks again

You are welcome, and please provide feeback, and stay tuned, the x86_64 for the Sushi mini version is on it's way, and hopefully I'll be able to have the bigger ones following very soon. :D

(I like the image of a pond between two continents, LOL!)

---

