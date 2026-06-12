---
title: "problema con dpkg"
date: 2009-12-29
forum: Software
---

### Post by FB91 on 2009-12-29
cuando quiero instalar cualquier programa me sale este mensaje

> E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 

y cuando ejecuto **sudo dpkg --configure -a** se me queda la terminar en una linea que dice **Conectando a ftp.3drealms.com|74.208.171.241|:21...** y no pasa nada... se queda congelada ahí

que puede ser?

gracias !

---

### Post by FB91 on 2009-12-29
les muestro lo que me tira la consola 

> fb91@fb91-desktop:~$ sudo dpkg --configure -a
Configurando rott (1.1-3ubuntu0.1) ...
--2009-12-29 14:12:37--  [ftp://ftp.3drealms.com/share/1rott13.zip](ftp://ftp.3drealms.com/share/1rott13.zip)
           => `/usr/share/games/rott/1rott13.zip'
Resolviendo ftp.3drealms.com... 74.208.171.241
Conectando a ftp.3drealms.com|74.208.171.241|:21... ^Cdpkg: error al procesar rott (--configure):
 el subproceso script post-installation instalado fue terminado por la señal (Interrupción)
Se encontraron errores al procesar:
 rott

---

### Post by luks911 on 2009-12-29
Mirate este thread[0] que tiene la solución.

[0] [http://ubuntuforums.org/showthread.php?t=1254553](http://ubuntuforums.org/showthread.php?t=1254553)

---

### Post by FB91 on 2009-12-29
> **luks911 said:**
> Mirate este thread[0] que tiene la solución.

[0] [http://ubuntuforums.org/showthread.php?t=1254553](http://ubuntuforums.org/showthread.php?t=1254553)

gracias!! me funcionó perfecto

(la próxima busco mejor :P)

---

