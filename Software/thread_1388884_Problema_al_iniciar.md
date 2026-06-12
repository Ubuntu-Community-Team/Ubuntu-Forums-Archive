---
title: "Problema al iniciar"
date: 2010-01-23
forum: Software
---

### Post by Tosh78 on 2010-01-23
Buenas gente! Les cuento que tengo un pequenio problemita. No puedo acceder a la interfaz grafica cuando inicia mi Ubuntu. Supongo que la causa pueden ser unas actualizaciones que instale hoy o el haber instalado tint2. Realmente no lo se porque hoy lo estuve usando perfectamente pero despues apague, al rato volvi a iniciar y nada. Se queda la pantalla negra despues del grub. 
Lo loco es que si inicio en Recovery Mode, arranca todo perfecto. O al menos eso creo. Pueden darme una mano? Porque mis conocimientos de comandos son muy muy escasos y no se me ocurre como podria solucionar esto.

Gracias!

---

### Post by qZweWfYjaz on 2010-01-23
a mi me paso lo mismo que a vos, tendrán algo que ver los drivers ATI???

---

### Post by mama21mama on 2010-01-23
si no te arrancan las X puedes hacer lo siguiente... Arranca ubuntu en modo (Recovery mode) y le dices que te mande a una consola root, luego ejecutas el comando

> dpkg-reconfigure -phigh xserver-xorg

[Fuente]("http://mamalibre.eshost.com.ar/?q=node/30")

---

### Post by qZweWfYjaz on 2010-01-23
yo desinstale los drivers de ATI y me anduvo
> cd /usr/share/ati
sudo ./fglrx-uninstall.sh
Despues los instale de nuevo desde controladores de hardware de Ubuntu.

---

### Post by Tosh78 on 2010-01-23
Gracias a los dos!
Reinstale los driver ATI y todo volvio a la normalidad. Mil gracias!

---

