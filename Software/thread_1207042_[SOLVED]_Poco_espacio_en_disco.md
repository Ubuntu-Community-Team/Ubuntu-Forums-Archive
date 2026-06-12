---
title: "[SOLVED] Poco espacio en disco"
date: 2009-07-07
forum: Software
---

### Post by VictorDi on 2009-07-07
Acabo de instalar Ubuntu en una pc de escritorio con un solo rígido de 160 y conservando el WXP que tenía previamente instalado. Usé la herramienta de instalación por defecto, y me creó una partición de 2,5 gigas. Ubuntu anda perfecto, pero no me permite actualizar nada ni agregar nada por falta de espacio. Como hago para aumentar el espacio de la partición, ó en su defecto como hago para desinstalarlo y corregirlo en una reinstalación? Gracias

---

### Post by joseluis on 2009-07-07
Con un live CD accedes a Gparted (el programa de particionado de GNU/Linux y que viene con muchas distros linux).
En Gparted borras la partición de linux. Te quedará una de windows grande y otra sin formato de 2,5 gigas.
Reducis la partición de xp y bien extendes esa particion que te queda sin formato. Dale mas o menos unos 10 o 15 gigas, si vas a usar los documentos que tenes en win, sino dale mas para usar mas espacio para guardar documentos, etc. A esa particion dale formato, te recomiendo ext4.
Luego, cuando instalas, elegis la opcion particionado manual y decis a ubuntu que te instale en esa particion. No te alarmes, te lo muestra graficamente.
Y seguis los pasos que hiciste antes, igual que cuando lo instalaste la primera vez.

---

### Post by VictorDi on 2009-07-08
Gracias Joseluis, con tus instrucciones pude solucionar el problema.

---

