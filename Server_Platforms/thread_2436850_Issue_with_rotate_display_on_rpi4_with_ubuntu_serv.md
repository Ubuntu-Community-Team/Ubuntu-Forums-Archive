---
title: "Issue with rotate display on rpi4 with ubuntu server 19.10"
date: 2020-02-14
forum: Server Platforms
---

### Post by elconcombritos on 2020-02-14
[COLOR=#242729][FONT=Arial]i need to rotate the display on a rpi4 using ubuntu 19.10. I tried by adding some stuff in usercfg.txt, which seems to be the new config file on this version but i don't manage to make this work.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here is what i put in usercfg :[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]disable_overscan=1[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]display_rotate=1[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]dtoverlay=vc4-fkms-v3d[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]With this configuration, the screen is rotated for the boot screen, but when it's done, the desktop appear in the background and the boot code stay in front of everything in a weird way.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I also tried xrandr but it split the screen in two part like this : [https://zupimages.net/viewer.php?id=20/07/uvvq.jpg](https://zupimages.net/viewer.php?id=20/07/uvvq.jpg)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How can i achieve to rotate the display and put in portrait mode ?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks

(PS:Sorry if it's the wrong forum. If it's the case, can someone tell me where i could find some help ?)[/FONT][/COLOR]

---

