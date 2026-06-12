---
title: "Problema Kernel Panic al actualizar a Ubuntu 8.10"
date: 2009-03-27
forum: Software
---

### Post by gatoyfelpudo on 2009-03-27
Ayer decidí actualizar mi Ubuntu de la Hardy Heron 8.04 a Intrepid Ibex 8.10, así que dejé a la noche haciéndose la actualización. Cuando, a la mañana, trate de prender la máquina (donde convive aún con Vista), me encontré con este error, apenas booteando: "**kernel panic - not syncing: VFS: Unable to mount root fs on unknow -block (0,0)**".
La verdad es que estuve toda la tarde tratando de arreglar el problema, y como me costó bastante (y la mayoría de las referencias de Google no funcionaron), ahora que finalmente lo solucioné, decidí compartirlo, por si otro anda con el mismo problema.
Después de probar varias cosas, decidí instalarlo desde el LiveCD, así que lo bajé, quemé un cd y probé. Nada: cuando llegaba al particionado, no reconocía nada. Boteé desde el LiveCD y ahí arrancó, pero cuando le corrí el gparted me indicaba como si el disco no tuviera ninguna partición (ni lógica ni física) y todo el espacio estaba "sin asignar". A todo esto, Vista seguía andando.
En fin, que después de varias horas, [este post del Blog de Max Horvath]("http://www.maxhorvath.com/2008/11/problems-when-upgrading-to-ubuntu-810-kernel-panic-unable-to-mount-root-fs.html") me dio la pista.

Pero le tuve que hace algunos toques. En el post explican que (supongo que no en todos los casos), Intrepid Ibex no agrega en el script del Grub la línea que indica el initrd.
En mi caso esto era así, pero cuando se la agregué me daba otro error. Buscando en el directorio /boot, resulta que el initrd-img-XXXX que correspodía al kernel que supuestamente había cargado el Ibex, no estaba.
Modifiqué el script para que cargue el kernel anterior (supongo que era el último que había actualizado Hardy Heron) y ¡voilá! pude arrancar mi Ubuntu.
Un detalle: a la primera no me reconoció el wi-fi, y ya estaba bastante embolado, pero cuando reinicié anduvo todo bien.

Si a alguno le pasa algo parecido, lo que hice -resumido- es lo siguiente:

1) Iniciar desde el LiveCD
2) Abrir una consola y ahí

```
# sudo mount /dev/sdaXY /mnt
```

Aclaro que yo me acordaba el número de la partición donde estaba ubuntu (en mi caso sda7), si no la verdad es que no sé cómo habría que hacer para averiguarlo

4) Fijarse en el directorio /mnt/boot cuál es el último kernel completo (los archivos vmlinuz e initrd con la misma versión): en mi caso tenía el vmlinuz-2.6.27-14 pero el último initrd que tenía era el 2.6.24-24

3) Editar el script del Grub

# sudo nano /mnt/boot/grub/menu.lst

Ahí busqué las líneas correspondientes, que eran algo así:

   ```
1. ...  
   2. title           Ubuntu 8.10, kernel 2.6.27-14-generic  
   3. root            (hd0,4)  
   4. kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=********-****-****-****-************
   5. quiet
   6. ...  
```

y las sustituí por 

  ```
 1. ...  
   2. title           Ubuntu 8.10, kernel 2.6.24-24-generic  
   3. root            (hd0,4)  
   4. kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=********-****-****-****-************ ro  
   5. initrd          /boot/initrd.img-2.6.24-24-generic  
   6. quiet  
   7. ...  

```

Agregando la última (la que empieza con "initrd"). Fíjense que hay que poner el UUID que corresponde a la partición, pero eso ya debe estar bien.

Y listo, reiniciar desde el HD, y cruzar los dedos

---

