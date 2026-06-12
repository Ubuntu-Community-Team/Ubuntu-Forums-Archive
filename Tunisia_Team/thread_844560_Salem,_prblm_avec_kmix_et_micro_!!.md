---
title: "Salem, prblm avec kmix et micro !!"
date: 2008-06-29
forum: Tunisia Team
---

### Post by tunifun on 2008-06-29
Voila j'ai migré vers kubuntu depuis quelques semaines (etfouuuuuuuh microzeft :D )
par contre mon micro ne marche pas depuis et quand j'ai essayé de toucher la config j'ai désactivé la sortie principale de ma carte son mouch bel3ani et j'utilise actuellement la sorte de headphone :(

[IMG]http://img112.imageshack.us/img112/6397/kmix1rb2.png[/IMG]
[IMG]http://img115.imageshack.us/img115/9910/kmix2be3.png[/IMG]
[IMG]http://img111.imageshack.us/my.php?image=kmix3uy2.png[/IMG]


sinon aussi en lspci -v

> 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Unknown device 0199
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at ec00 [size=256]
        I/O ports at e8c0 [size=64]
        Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
        Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2


alors quelqu'un pourra me sauver ??

---

### Post by pytheas22 on 2008-06-29
Pour résoudre le problème avec la sortie principale, essayez:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install kdm kubuntu-desktop
```

je ne sais pas si ça vous aidera mais selon cette [discussion]("http://ubuntuforums.org/showthread.php?t=205449"), c'est possible.

Pour le problème avec le micro:
```

sudo -s
echo 'options snd-hda-intel model=ref' >> /etc/modprobe.d/alsa-base
```

et rédemarrez.  De bons résultats?

Au fait vous utilisez quelle version de Kubuntu?

---

### Post by tunifun on 2008-06-30
Merci pour la réponse actuellement je suis au boulot donc je ne pourrai faire ces manips je m'en occuperai dès que je rentre et je vous tiendrai au courant.

Sinon pour rajouter j'utilise kubuntu 7.10 Gutsy
Et pour le probleme de la sortie principale il a eu lieu juste après que j'aurai touché Alsamixer pour régler le micro comme j'ai lu dans quelques topics du forum ubuntu-fr

---

