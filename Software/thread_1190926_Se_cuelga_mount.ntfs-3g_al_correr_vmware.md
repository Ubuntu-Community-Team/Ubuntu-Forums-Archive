---
title: "Se cuelga mount.ntfs-3g al correr vmware"
date: 2009-06-18
forum: Software
---

### Post by matuu! on 2009-06-18
Hola gente. Este es mi primer post en el foro, espero que puedan darme una mano con esto. Utilizo maquinas virtuales con vmware server 2. El problema surge cuando tengo encendida alguna maquina que esta alojada en una partición ntfs. No se si el problema es de vmware o de mount.ntfs-3g. La maquina no se cuelga, pero anda muy lento. Me fije con htop y mount.ntfs-3g ocupa el 97% o 98% del procesador. Esto empezo a pasar hace poco, no recuerdo si fue antes o después a la actualización a la version JJ.
Bueno, espero alguien pueda darme una mano..

---

### Post by guillermolisi on 2009-06-18
> **matuu! said:**
> Hola gente. Este es mi primer post en el foro, espero que puedan darme una mano con esto. Utilizo maquinas virtuales con vmware server 2. El problema surge cuando tengo encendida alguna maquina que esta alojada en una partición ntfs. No se si el problema es de vmware o de mount.ntfs-3g. La maquina no se cuelga, pero anda muy lento. Me fije con htop y mount.ntfs-3g ocupa el 97% o 98% del procesador. Esto empezo a pasar hace poco, no recuerdo si fue antes o después a la actualización a la version JJ.
Bueno, espero alguien pueda darme una mano..
Por que guardar la imagen de una VM en una particion NTFS cuando lo podes hacer en una ext3 que es muchisimo mas segura, confiable, libre de mantenimiento y no necesita de un programa intermedio para interactuar entre un entorno operativo y otro ?

Que sistemas operativos corres en esas VMs ?

---

### Post by staar on 2009-06-18
solución temporal: desfragmentar la partición NTFS (si querés hacerlo rápìdo y bien, usa [Jkdefrag]("http://www.kessels.com/Jkdefrag/"))

solución definitiva: trasladar la VM a un sistema de archivos como la gente (llámese ext3, ext4, reiserfs o el que más te guste)

saludos

---

### Post by matuu! on 2009-06-18
> Por que guardar la imagen de una VM en una particion NTFS cuando lo podes hacer en una ext3 que es muchisimo mas segura, confiable, libre de mantenimiento y no necesita de un programa intermedio para interactuar entre un entorno operativo y otro ?

Que sistemas operativos corres en esas VMs ?     Tenés toda la razón, pero me quede sin espacio en el /home y la tuve que poner en esa partición.. Me paso instalando un Debian Lenny en la VM, de hecho lo he querido instalar ya varias veces, pero antes de terminar la instalación se colgaba mal..

> solución temporal: desfragmentar la partición NTFS (si querés hacerlo rápìdo y bien, usa [Jkdefrag]("http://www.kessels.com/Jkdefrag/"))Lo voy a probar, a ver como anda..
Bueno, gracias a los dos.. Voy a mover la vm a alguna ext3 y tratar de instalar el debian..
Thank!

---

