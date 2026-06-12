---
title: "Removing KDE 4 Kickoff Kubuntu.org Link"
date: 2013-08-21
forum: Ubuntu Dev Link Forum
---

### Post by joseph5 on 2013-08-21
Hello, I am hoping my question will be answered here I have spent the past 4 days searching and talking to people and no one has an answer with direction just keeps telling me to try to contact ubuntu package developer....so my question I am sure is simple to someone, how do I remove the kubuntu.org image and link from the KDE 4 Kickoff menu? Even changing it would be okay, I just really do not want the bulging logo to be part of my start menu. Can someone please help?

---

### Post by monkeybrain20122 on 2013-08-21
You can right click it and a menu would show up where you can choose your icon. Sorry can't give more details since I am not logged in to kde right now.

---

### Post by joseph5 on 2013-08-21
Not that, here is an image of it [IMG]http://i.troll.ws/4faceec3.png[/IMG]

---

### Post by joseph5 on 2013-08-21
notice the kubuntu logo in the bottom right? It is also a link to kubuntu.org I would like to remove it.

---

### Post by joseph5 on 2013-08-22
Pretty sad to see no movement. I just thought that I should let people know I discovered how to do it by googling around a bit out of the box questions. Follow these helpful links and you will be fine if you need to do this as well.

Step 1.
[http://askubuntu.com/questions/126965/how-to-personalize-kde-menu](http://askubuntu.com/questions/126965/how-to-personalize-kde-menu)

Step 2.
[http://forum.kde.org/viewtopic.php?f=66&t=110064](http://forum.kde.org/viewtopic.php?f=66&t=110064)

Step 3.
[http://ubuntuforums.org/showthread.php?t=2020676](http://ubuntuforums.org/showthread.php?t=2020676)

If you do all those in that order you will be okay and everything should change, the image and link...of course you could completly null the image and link as well if that is what you are looking to do as well.

---

### Post by ivaylo-va on 2013-09-14
I have managed to change the default [www.kubuntu.org]("http://www.kubuntu.org") link in the kickoff menu launcher (and display logo) only after renaming or deleting these files
/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps/desktoptheme/default/widgets/branding.svgz
/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps/desktoptheme/oxygen/widgets/branding.svgz

adding
[Branding]
homepage=http://www.example.org/
in /usr/share/kde4/apps/desktoptheme/oxygen/metadata.desktop , /usr/share/kde4/apps/desktoptheme/default/metadata.desktop , ~/.kde/share/apps/desktoptheme/default/metadata.desktop and

replacing /usr/share/kde4/apps/desktoptheme/default/widgets/branding.svgz and /usr/share/kde4/apps/desktoptheme/oxygen/widgets/branding.svgz
with logo of my own choice.

---

