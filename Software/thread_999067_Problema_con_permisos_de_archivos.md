---
title: "Problema con permisos de archivos"
date: 2008-12-01
forum: Software
---

### Post by benjamin_linux on 2008-12-01
Hola,

quise instalar Virtual Forbidden City, es un tour 3d de la Ciudad Prohibida de Beijing, hecha por el gobierno de China junto a IBM, con el motor de Second Life. Tiene versión para Linux, un .rpm.

Para pasarlo a .deb, primero intenté con 

```
seretur@dendro:~$ sudo alien -k VirtualForbiddenCity.rpm
```

y me creó carpetas con la información correspondiente pero ningún .deb, me tiró un error y recomendó que usara --scripts. Ahí funcionó.

```
seretur@dendro:~$ sudo alien -k --scripts VirtualForbiddenCity.rpm
virtualforbiddencity_6.0-1_i386.deb generated
seretur@dendro:~$
```

Instalo el deb... y el problema es que cuando quiero correr el tour me dice "Ha ocurrido un error al ejecutar el proceso hijo 'vfc' (Permiso denegado)". Me pasa lo mismo si intento ejecutarlo desde la consola, aunque lo haga como root y también lo mismo me pasa cuando quiero borrar el directorio que había creado antes. Y no me deja cambiar los permisos de ningún archivo (aunque esté logueado como root) porque me dice que no soy el "propietario".

Cómo puedo hacer??

---

### Post by Mauro22 on 2008-12-01
[B]Podes instalarlo sin pasarlo a .deb

```
sudo alien -i paquete.rpm

```

o, pasarlo:
[COLOR=Black]
[/COLOR]```
alien -d paquete.rpm
```[I][B][COLOR=Black]
[/COLOR][COLOR=Black]
e instalarlo:[/COLOR][COLOR=Black]

[/COLOR][/B][/I]```
dpkg -i paquete.deb
```[/B]

---

### Post by sajnox on 2008-12-01
Para generar el .deb uso el comando alien con la opcion -v (verbose) para que me tire donde hay un error (si es que lo hay)

```
sudo alien -v "nombre del archivo"
```

---

### Post by benjamin_linux on 2008-12-01
Gracias por la ayuda, pero el problema no lo tengo para hacer el deb, con alien lo pude hacer en el segundo intento, la cuestión es que no me permite ni ejecutar el programa ya instalado ni borrar los archivos (de cuando lo intenté por primera vez, generándome una carpeta con la info en lugar del deb), todo esto por "no tener los permisos" para hacerlo, ni logueándome como root

---

### Post by benjamin_linux on 2008-12-02
Finalmente, haciendo

```
root@dendro:/home/seretur/Escritorio# chmod a=rw VirtualForbiddenCity-6.0
root@dendro:/home/seretur/Escritorio# ls -l
total 4
drw-rw-rw- 5 root seretur 4096 2008-11-27 14:55 VirtualForbiddenCity-6.0
```


he podido borrar el directorio. pero sólo me dejó enviarlo a la papelera y no puedo sacarlo de ahí ahora...

Y el problema sigue siendo el tour ya instalado, tiene toda una carpeta en /opt y luego archivos en /usr/bin y /usr/share, tengo que hacer lo mismo con estos archivos/carpetas? Calculo que sí... denme el ok please :)

---

