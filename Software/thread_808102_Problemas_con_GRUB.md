---
title: "Problemas con GRUB"
date: 2008-05-26
forum: Software
---

### Post by fedescha on 2008-05-26
Cuando instale Hardy aproveche para reparticionar el disco y crear un espacio para XP (fat32). El problema es que cuando instale XP en su particion aparece el sist. de inicio de windows y no GRUB y me pregunta si quiero iniciar windows o un sist operativo que se encuentra en la particion c:, cosa que no hace.
Inicie la maquina con el disco de arranque de hardy y estan las tres particiones como discos: Disk 1: XP, Disk 2: /home y Disk 3: /
Quise re instalar hardy pero no puedo distinguir la particion / ya que cuando lo hago manualmente estan/dev/dva1, 3, 4, 6.
siendo 1 y 4 ext32 y 3 fat32.

Como puedo hacer para reinstalar en / o como puedo hacer para que la maquina se inicie con GRUB.
Saludos,

---

### Post by sajnox on 2008-05-26
Si ya instalaste Hardy y despues instalaste windows no hace falta que reinstales (hardy por lo menos), el tema es que cuando instalas windows te borra el MBR (master boot record).

Para recuperarlo podes seguir esta guia: [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

---

