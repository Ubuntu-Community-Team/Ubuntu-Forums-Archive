---
title: "No Puedo Usar Sudo"
date: 2010-08-24
forum: Software
---

### Post by asterix77 on 2010-08-24
Les comento que hoy he querido hacer una acción usando sudo y me aparece lo siguiente:

asterix@asterix-laptop:~$ sudo nautilus
[sudo] password for asterix: 
asterix is not in the sudoers file.  This incident will be reported.
asterix@asterix-laptop:~$ 

Al parecer algo pasó con el archivo sudoers, el problema es que al no  tener privilegios de root, no puedo editarlo. Ubuntu tiene creado un  usuario root, pero al invocarlo pide una pass, que por razones obvias de  la instalación de ubuntu, no la sé. (¿sería tal vez bueno crearla??????  Creo que no estaría demás).

¿Se habrá generado el problema ayer al ejecutar estos comandos?

#sudo /usr/sbin/usermod -G dialout asterix
#id -nG asterix

Bueno, el tema es que quiero ingresar a la consola de recuperación para poder seguir esta posible solución. 

[http://alufis35.uv.es/~laura/spip/spip.php?article172]("http://alufis35.uv.es/%7Elaura/spip/spip.php?article172")

El problema es que en mi notebook, tengo el ingreso en forma automática hacia ubuntu,  (que está solo con ubuntu lucid), ni siquiera me muestra el grub, o  algún tipo de acción (ni siquiera me tengo que logear).

¿Alguien sabe cual es la combinación para ingresar a la consola de recuperación en lucid?.

No tengo a mano un livecd, tal vez se podría editar de esta forma ¿se podría?.

Saludos

---

### Post by spjackson on 2010-08-24
Me disculpo por mi español débil/pobre - soy ingles.

> 
```

#sudo /usr/sbin/usermod -G dialout asterix

```Gran problema. Ya el usuario 'asterix' no es miembro del grupo 'admin', entonces no puede usar 'sudo'.

Se necesitan otros grupos tambien, pero 'admin' es le grupo para 'sudo'.

Comando correcto:
```

#sudo /usr/sbin/usermod -a -G dialout asterix

```Se necesita una linea en /etc/group contiendo
```

admin:x:119:asterix

```Creo que si mantenga la tecla de mayúsculas durante el 'boot', el grub se muestra. Si no es posible, se necesita un livecd.

---

### Post by asterix77 on 2010-08-25
Perfecto, he arreglado mi problema finalmente usando un liveCD y editando los archivos correspondientes.

Mil gracias por tu ayuda spjackson.

Saludos

---

