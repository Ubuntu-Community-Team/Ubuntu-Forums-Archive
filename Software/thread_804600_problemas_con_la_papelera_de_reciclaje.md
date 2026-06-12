---
title: "problemas con la papelera de reciclaje"
date: 2008-05-23
forum: Software
---

### Post by jjoseluisdamico on 2008-05-23
Amigos, 
bajé el ubuntu 8.04 y tengo un problema que no tenía en versiones anteriores: no me permite enviar archivos o carpetas a la papelera de reciclaje, solamente me permite borrarlos definitivamente.
Esto sucede unicamente con archivos que están alojados en un disco master que está en formato ntfs. En cambio, en otro disco que tiene particiones fat32 y ext3 no tiene problemas.
Esto también me ocurre con Mint 5 beta (derivado de Ubuntu), lo cual me da a pensar que un problema de versión, porque antes no pasaba.
Por favor, necesito saber si a alguien le ha ocurrido y cómo resolverlo.
gracias

---

### Post by faktorqm on 2008-05-25
Hola, tenes que instalar el paquete ntfs-3g, por que el kernel solo tiene soporte para lectura en ntfs, no para escritura, vos cuando "borras" un archivo, lo sacas de la lista digamos, y lo mandas a la papelera de reciclaje, pero en realidad fisicamente nunca lo moviste. Para hacer eso necesitas escribir y no podes.

```
sudo apt-get install ntfs-3g
```

creo que es automatico, pero si te sigue pasando asegurate de que tu linux utilice el ntfs-3g para montar dicho tipo de particiones y no otro programa. Espero que te haya servido, Salu2!!

---

### Post by Mister X on 2008-05-26
> **faktorqm said:**
> Hola, tenes que instalar el paquete ntfs-3g, por que el kernel solo tiene soporte para lectura en ntfs, no para escritura, vos cuando "borras" un archivo, lo sacas de la lista digamos, y lo mandas a la papelera de reciclaje, pero en realidad fisicamente nunca lo moviste. Para hacer eso necesitas escribir y no podes.

```
sudo apt-get install ntfs-3g
```

creo que es automatico, pero si te sigue pasando asegurate de que tu linux utilice el ntfs-3g para montar dicho tipo de particiones y no otro programa. Espero que te haya servido, Salu2!!

Yo le estaba por contestar algo parecido, pero ya puede escribir en el ntfs, ya que puede eliminar los archivos, lo que no puede es mandarlos a la papelera.

---

