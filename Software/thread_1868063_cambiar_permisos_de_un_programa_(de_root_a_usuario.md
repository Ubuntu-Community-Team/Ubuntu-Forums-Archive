---
title: "cambiar permisos de un programa (de root a usuario comun)"
date: 2011-10-23
forum: Software
---

### Post by drazhe on 2011-10-23
Hola, hace unos días me pasaron un .deb con un emulador de PSX, y todo funcionó bien, hasta que descubrí que el programa se instaló como root y cada vez que necesito arrancarlo, me pide la contraseña para elevar los permisos... 

Existe alguna manera de cambiar esas características?, que el programa siga funcionando sin tener que poner el pass cada vez que lo arranco, con el riesgo propio de dicha acción...

---

### Post by euzkoarima on 2011-10-24
Una manera sería darle permiso de lectura y ejecución a otros. Fijate en /usr/bin que los programas se suelen instalar como pertencientes al root pero con esos permisos.

Sin embargo creo que corres el riesgo de dejar algunos permisos sin cambiar, por ejemplo en algún archivo de configuración.

Por lo tanto me parece más sano que desinstales el programa y lo vuelvas a instalar con tu usuario.

Saludos,
Eduardo

---

### Post by drazhe on 2011-10-24
> **euzkoarima said:**
> Una manera sería darle permiso de lectura y ejecución a otros. Fijate en /usr/bin que los programas se suelen instalar como pertencientes al root pero con esos permisos.

Sin embargo creo que corres el riesgo de dejar algunos permisos sin cambiar, por ejemplo en algún archivo de configuración.

Por lo tanto me parece más sano que desinstales el programa y lo vuelvas a instalar con tu usuario.

Saludos,
Eduardo

eso hice, y varias veces, y siempre se me instala como root, cada vez que inicio el programa me vuelve a pedir la contraseña y si no la cargo el programa no arranca... y cargar la contraseña de root es un riesgo a la hora de usar un programa...

---

### Post by euzkoarima on 2011-10-24
Raro !!
Seré curioso, como se llama el programa ?
A ver si con ese dato podemos encontrar a alguno que le haya pasado algo similar.

Saludos,
Eduardo

---

### Post by drazhe on 2011-10-25
> **euzkoarima said:**
> Raro !!
Seré curioso, como se llama el programa ?
A ver si con ese dato podemos encontrar a alguno que le haya pasado algo similar.

Saludos,
Eduardo

lo dije en la primera entrada, pero es un emulador de playstation 1, se llama **psx** me lo pasó un amigo en un **.deb** y él no tuve ningún problema para instalarlo como corresponde...

---

### Post by guillermolisi on 2011-10-25
> **drazhe said:**
> lo dije en la primera entrada, pero es un emulador de playstation 1, se llama **psx** me lo pasó un amigo en un **.deb** y él no tuve ningún problema para instalarlo como corresponde...

El nombre correcto del paquete es pcsxr y esta en los repositorios de Ubuntu (por lo menos en los de la 11.10).

> PCSX is an advanced PlayStation (PSX) emulator, which uses a plugin architecture to provide full support for all components of the PSX. It has full emulation support for gamepads, videos, sound, memory cards, and other important PSX components, and is able to play many games without problems.

This package contains PCSX-Reloaded, which is based on PCSX-df 1.9 which is in turn based on the original PCSX.



Removeria completamente esa instalacion que hiciste y volveria a instalar desde los repositorios, a ver que pasa.

---

### Post by drazhe on 2011-10-26
> **guillermolisi said:**
> El nombre correcto del paquete es pcsxr y esta en los repositorios de Ubuntu (por lo menos en los de la 11.10).

Removeria completamente esa instalacion que hiciste y volveria a instalar desde los repositorios, a ver que pasa.

bueh.. una pena, no pude soportar la nueva versión 11.10 de Ubuntu y reinstale la ultima LTS... en sus repositorios no aparece nada, mas que las librerías-dependencias que se suponen hacen falta para hacer funcionar dicho emulador... 
pero no importa.. sería mas grave que fuera un programa útil...

---

### Post by drazhe on 2011-10-26
otra que pensé es instalarlo a mano, pero ahí se me complica...

[http://psxemulator.gazaxian.com/]("http://psxemulator.gazaxian.com/")
Al parecer esa es la página oficial del proyecto... 

y dan varias opciones de descarga, entra las ultimas versiones par Linux, se encuentra: 

[http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2]("http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2")

pero es un archivo comprimido sin un instalador y hay que hacerlo por consola... y ya tanto no me acuerdo... jejeje

---

### Post by euzkoarima on 2011-10-26
Efectivamente los paquetes del repositorio son de 11.10 en adelante, pero si estás corriendo 10.04 este post [0] dice como instalar en esa versión

[0] [http://ubuntuforums.org/showthread.php?t=1704649]("http://ubuntuforums.org/showthread.php?t=1704649")

Saludos,
Eduardo

---

