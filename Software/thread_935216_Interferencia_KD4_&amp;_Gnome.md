---
title: "Interferencia KD4 &amp; Gnome ?"
date: 2008-10-01
forum: Software
---

### Post by ramiro_md on 2008-10-01
Gente ayer por la tarde instalé kde 4 depués de algunos bardos lo pude sacar andando sin más probemas. La cuestión es que me molesta que inicien los screenlets, que tengo en gnome, en la sesión de kde. No se si será un problema de mi pc, o qué es así en todos los casos.
Por otra parte la cairo dock me inicia 2 veces :confused: teniendo que cerrar una.

Esos son mis dos únicos problemas pendientes en kde 4. Esperop que algún kdeero me puda ayudar :D
Un saludo.

---

### Post by guisheca on 2008-10-01
Si siempre pasa eso, que los programas que se inician con gnome también lo hacen en kde. La verdad que no tengo ahora kde y gnome juntos (lo tengo en particiones separadas), pero en kde hay dos formas de iniciar sesión: una "automatica" (creo que se llama así) y otra "manual". La "automática" recuerda los programas que estaban abiertos cuando se cerró sesión anteriormente, y la manual se rige por los programas que el indique el directorio /home/tuusuario/.kde4/autostart.
Probá activando esta última opción a ver que pasa, es lo único que se me ocurre decirte. Para cambiar eso, no recuerdo bien donde hay que ir, pero supongo que tiene que ser en "configuración del sistema" y después tiene que haber un apartado que se llame "sesiones".
Espero haberte sido de ayuda.
Saludos.

---

### Post by ramiro_md on 2008-10-01
Me interesa lo del directorio "autostart". Cómo hago para agregar programas al inicio en esa carpeta ? porque la tengo vacia. Hay que poner scripts ?. Gracias guisheca. Un saludo.

---

### Post by guisheca on 2008-10-01
Tenes dos formas de poner programas al inicio de kde. Una es poniendo un script tipo

```
#!/bin/bash
yakuake & 
```

No te olvides de darle permisos de ejecución porque si no lo que va a hacer es abrirte el script en kate XD. Otra cosa, tiene que ser un script por cada programa, no vale algo del tipo

```
#!/bin/bash
yakuake & 
compiz --replace &
```

La otra es simplemente colocando un enlace simbólico en la carpeta. Lo pedés hacer buscando el programa en el menú, ahí creo que con botón derecho podés elegir que te ponga el enlace en el escritorio, lo copias a la carpeta en cuestión y listo.
Saludos.

---

### Post by ramiro_md on 2008-10-01
Ok. Muchas gracias. Lo voy a probar.

---

