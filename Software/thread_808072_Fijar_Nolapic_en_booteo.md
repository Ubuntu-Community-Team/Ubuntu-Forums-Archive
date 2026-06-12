---
title: "Fijar Nolapic en booteo"
date: 2008-05-26
forum: Software
---

### Post by athnea on 2008-05-26
¡Hola!

Ayer instalé Ubuntu 8.04. Al principio no podía ejecutar el Live CD, pero tanteando toqué la opción NOLAPIC en el F6 y funcionó. Instalé. Cuando la PC reinició y seleccioné Ubuntu, se quedó colgada en "starting up". Busqué por Internet sobre el asunto y encontré la recomendación de modificar el kernel y cambiar el  "quiet splash" por "nolapic" (esto, cuando carga el grub y tocando e). Funcionó y pude entrar.

El problema es: ¿cómo hago para dejar fijo el entrar con nolapic y no tener que modificar siempre el kernel en el inicio?

¡Gracias!

---

### Post by faktorqm on 2008-05-26
Hola, edita el archivo del grub con:

```
sudo gedit /boot/grub/menu.lst
```

y en la parte que dice algo parecido a esto:

```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5430a0a1-0ca4-4304-b2b5-d682a2ff0f43 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

```

Debe quedar:

```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5430a0a1-0ca4-4304-b2b5-d682a2ff0f43 ro quiet splash [COLOR="Red"]apic=nolapic[/COLOR]
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

```

Te lo puse en color para que veas la diferencia. Suerte y salu2!!

p.d.: En el foro hay mil cosas sobre grub, si te interesa, podes buscarlas adentro de este mismo sub foro y vas a ver muchos threads al respecto. Salu2!

---

### Post by athnea on 2008-05-26
Muchas gracias :)
¡Ahora entra directo! Mi nuevo problema es la conexión a Internet, jiji. [http://ubuntuforums.org/showthread.php?t=808768](http://ubuntuforums.org/showthread.php?t=808768)

:confused:

---

