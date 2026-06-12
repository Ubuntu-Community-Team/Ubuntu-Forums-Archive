---
title: "eclise 3.8, menu doesn't scroll"
date: 2013-12-12
forum: Ubuntu Application Development
---

### Post by philo_71 on 2013-12-12
hi,
i have intalled eclipse 3.8 and jboss 7 on ubuntu server 13.10.
i cannot to acces to menu !
i have intalled of course jdk and tomcat 7 which run normaly.
 > root@dct-zeus:~/Desktop# javac -version
javac 1.7.0_25
root@dct-zeus:~/Desktop# 


but my probleme is to menu of eclipe doesn't display !

see ya_
philippe

---

### Post by bluesky2210 on 2013-12-28
This problem is bug Ubuntu 13.10
You need create file eclipse.desktop in /usr/share/applications with contents:
> [Desktop Entry]Version=4.3.0
Name=Eclipse
Comment=IDE for all seasons
#Exec=/home/tuyennd/Downloads/eclipse/eclipse
Exec=env UBUNTU_MENUPROXY=0 /home/tuyennd/Downloads/eclipse/eclipse
Icon=/home/tuyennd/Downloads/eclipse/icon.xpm
Terminal=false
Type=Application
Categories=Utility;Application
Name[en_US]=eclipse.desktop

Change path Exec and Icon to your path.
Start eclipse.desktop and the menu is showing :)
This solution work for me :)

---

