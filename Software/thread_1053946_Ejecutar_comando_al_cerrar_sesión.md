---
title: "Ejecutar comando al cerrar sesión"
date: 2009-01-29
forum: Software
---

### Post by electronpositivo on 2009-01-29
Buenas,

Existe una forma de ejecutar un programa al iniciar la sesión gráfica en Ubuntu. Sistema->Preferencias->Sesiones->Programas de inicio (o copiar en el directorio .config/autostart/ dentro del home del usuario).

El problema que intento resolver es poder hacer esto mismo pero cuando se cierre la sesión; la idea es sincronizar varios directorios con el programa unison en el momento del cierre de la sesión. El script ya lo tengo a punto, pero no sé dónde ponerlo.

¿Se puede hacer esto? [-o<
Gracias

---

### Post by Mauro22 on 2009-01-30
Lo unico que se me ocurre es que agregues el comando para apagar, al script que tenes hecho.


Sino tendrias que buscar algo que intercepte la señal de apagado y todo eso, pero es mas sencilla la opcion anterior.

---

### Post by electronpositivo on 2009-02-01
¿Y no es posible hacerlo al cerrar la sesión un usuario?

---

### Post by electronpositivo on 2009-09-24
El fenónemo Kei Ku respondió perfectamente: [http://ubuntuforums.org/showpost.php?p=8000700&postcount=22]("http://ubuntuforums.org/showpost.php?p=8000700&postcount=22")

---

### Post by BoneZZZ on 2010-01-22
Estoy intentando lo mismo. Manualmente, desde la consola o con la versión GTK no tengo problemas, pero al modificar el script Default en /etc/gdm/PostSession, obtengo un error en Unison.log:
Uncaught exception End_of_file

¿cómo lo hicieste tú?

---

### Post by splig on 2010-10-09
> **electronpositivo said:**
> ¿Y no es posible hacerlo al cerrar la sesión un usuario?
Hay otra forma de hacerlo.
Si miras en la carpeta /etc/rc0.d/ todo son links a scripts que se ejecutan (empiezan por S) o se matan (empiezan por K) al apagar el PC.
Mete tu script en /etc/init.d (hecha un vistazo como estan programados, programalos igual, que tenga el paso de parametro stop, que es lo que se pasa por defecto).

Una vez lo tengas ahi utiliza el comando update-rc.d para que te cree esos links automaticamente.

Echa un vistazo al man, pero si lo que quieres es ejecutarlo al apagar el pc seria algo del estilo:

update-rc.d nombre_script stop 99 0 .

Espero te ayude, aunque tarde...

---

### Post by alfplayer on 2010-10-11
> **splig said:**
> Hay otra forma de hacerlo.
Si miras en la carpeta /etc/rc0.d/ todo son links a scripts que se ejecutan (empiezan por S) o se matan (empiezan por K) al apagar el PC.
Mete tu script en /etc/init.d (hecha un vistazo como estan programados, programalos igual, que tenga el paso de parametro stop, que es lo que se pasa por defecto).

Una vez lo tengas ahi utiliza el comando update-rc.d para que te cree esos links automaticamente.

Echa un vistazo al man, pero si lo que quieres es ejecutarlo al apagar el pc seria algo del estilo:

update-rc.d nombre_script stop 99 0 .

Espero te ayude, aunque tarde...

También habría que agregarlo a los runlevels 1 y 6 (especialmente al 6 que es reboot). El comando quedaría:

```
update-rc.d nombre_script stop 99 0 1 6 .
```

Esto es para que se ejecute cuando se cierra el sistema, después que se cierra el escritorio.

---

