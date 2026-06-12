---
title: "Wine + Firefox + Java"
date: 2009-07-20
forum: Wine
---

### Post by okelet on 2009-07-20
Hi

I am trying to install Firefox + Java with Wine in Ubuntu 9.04. These are the steps I follow:

```

sudo aptitude install wine cabextract

# Due to continous installations, remove all previous Wine settings
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

# With this, I install Firefox, Flash and Java
wget http://sunsite.rediris.es/mirror/firefox/latest/win32/es-ES/Firefox%20Setup%203.5.1.exe
wine Firefox\ Setup\ 3.5.1.exe
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player.exe
wine install_flash_player.exe
wget http://solosito.com/cybernet/download/jre-6u14-windows-i586-s.exe
wine jre-6u14-windows-i586-s.exe
rm Firefox\ Setup\ 3.5.1.exe install_flash_player.exe jre-6u14-windows-i586-s.exe

```

Now, when I run Firefox, flash movies run OK. If I go to [www.java.com](www.java.com) -> Do I have Java?, it says I have Java. Now I want to enter to a chat page that uses an applet: [http://www.ya.com/chats/](http://www.ya.com/chats/) -> Hispachat -> Spain -> Madrid -> Amistad, I enter my nick, and in the next page, where the applet should appear, there is only a white area.

Anybody can help me to make this work? Any tip is wellcome.

Thanks in advance.

---

### Post by yam.matt on 2009-07-21
Well, the question is why are you trying to run firefox and java through wine?:confused:. They are already available in the normal linux repositories. And Firefox cames preloaded with ubuntu. And if you want java you can easily install the sun-java6-jdk package through synaptic Package Manage, if you want the full JDK or if you just want the runtime then you can install the sun-java6-jre. Or there is another option too, you can also install the ubuntu-restricted-extras package through synaptic, it will install java 6 runtime as well as some other useful things like DVD playback, windows fonts, etc.
Hope I helped :)

---

### Post by dik23 on 2009-11-26
Because there's no Shockwave for Linux ?

How do you install Java for Windows FireFox using WINE ?

---

### Post by Ylon on 2009-11-26
From firefox check the andress:
about:plugins
to see if your plugins are correctly activated.


> Because there's no Shockwave for Linux ?

How do you install Java for Windows FireFox using WINE ?
You should able to install it (after firefox) just pressing Next > Yes > Yes > Next.....

JRE 1.6.x it's platinum for Wine.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6626](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6626)


Anyway, if you plan testing propouse I would suggest you to try virtualbox, with Windows 2000 to gain some performance.

---

