---
title: "No puedo crear directorio"
date: 2011-05-17
forum: Software
---

### Post by dnovai on 2011-05-17
Estimados, no puedo crear un directorio desde el terminal o consola


```

dnovai@AGACHADIZA:~$ sudo mkdir ~/.matlab/bin
mkdir: cannot create directory `/home/dnovai/.matlab/bin': No such file or directory

```

Al hacerlo como root me entrega el mismo mesaje :S

Alguna idea o ayuda?

Saludos!

---

### Post by papibe on 2011-05-17
Lo más probable es que el directorio .matlab no exista. Tienes 2 alternativas:

Lo creas en 2 pasos:
```
$ mkdir ~/.matlab
$ mkdir ~/.matlab/bin
```
O, usas la opción -p que crea los directorios necesarios si no existen:
```
$ mkdir -p ~/.matlab/bin
```
Espero que te sirva.
Saludos.

---

### Post by dnovai on 2011-05-18
Gracias, me sirvio tu ayuda, pero tengo dudas.
Estaba intentando hacer los pasos de este link para configurar el compilador de matlab [https://help.ubuntu.com/community/MATLAB]("https://help.ubuntu.com/community/MATLAB"), pero en algunos comandos como crear el directorio o crear el link tuve que forzar usando sudo,lo que no habia hecho veces anteriores. Ahora, para arrancar matlab tb debo usar sudo o me arroja un error y se cierra matlab (antes lo habia instalado en otras ocasiones sin usar comando sudo para arrancar matlab). Bueno, me llama la atención pq el sistema se comporta ahora así que ni para crear un directorio tuve problemas antes. Tienes alguna idea?

Gracias de todos modos pq igual resolvi el problema, pero no me gusta quedar con dudas :P.
=)

---

