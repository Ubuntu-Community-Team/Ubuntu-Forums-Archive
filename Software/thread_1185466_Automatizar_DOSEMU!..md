---
title: "Automatizar DOSEMU!."
date: 2009-06-12
forum: Software
---

### Post by zeroadrenaline on 2009-06-12
Ya se que me van a decir que haga un script que lo haga, o que lo busque en google.
Para la primera opcion no estoy muy en el tema, intente algunas cosas basicas, pero no le agarre la onda, y creeanme que busque en google.
La onda es que tengo una aplicacion que corre en MS-DOS y la estoy ejecutando con dosemu, ya edite autoexec.bat para que monte mi disco, ya lo tengo todo casi cocinado, pero lo que me lima es que para ejecutar mi aplicacion, tengo que:
1_ Abrir dosemu
2_ Ir con comandos de DOS hasta el directorio en cuestion
3_ Ejecutar la aplicacion.

Y me gustaria poder tener una manera de que al hacer un click sobre un iconito, me abra directamente mi aplicacion, dentro de dosemu.

SI alguien lo hace, hiso, o sabe como hacerlo y me comenta como hacerlo, va a hacer muy feliz a varias personas en una empresa de la republica de Caseros.

---

### Post by Mauro22 on 2009-06-12
probaste la ayuda de dosemu?

man dosemu

Fijate si tiene el parámetro para cargar un path directamente. 





Saludos!

---

### Post by gmunioz on 2009-06-12
Hola zer.....:

1- Crea un archivo para que DosEmu sea detectado por los menús de

entornos gráficos, llamado dosemu.desktop en el directorio 
```
/usr/share/applications
```

Que contenga esta información:

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Name=DOSEMU
GenericName=Emulador
Comment=Emulador de MSDOS
Exec=/usr/local/bin/xdosemu
TryExec=/usr/local/bin/xdosemu
Icon=dosemu.xpm
Categories=Application;System;Emulator

```

2 - Copia el archivo a:

/home/usuario/escritorio/

Y agrégale esta línea al comienzo:

```
#!/usr/bin/env xdg-open
```

3- Dale permisos de ejecución

Una vez que constates que DosEmu inicia bien, le agregas

al lanzador del escritorio, en el comando los parámetros

necesarios para que inicie la aplicación.

---

### Post by sebastianabate on 2009-06-12
Si usás dosemu para correr una sola aplicación podés agregar el comando de arranque al final del autoexec.bat y se va a ejecutar siempre que uses dosemu.

Si tenés varias aplicaciones distintas podés crearte scripts que arranquen dosemu con el comando como modificador; ej:

```
dosemu /home/usuario/.dosemu/drive_c/aplicacion/ejecutable.exe
```para que esto funcione tenés que agregar al autoexec.bat una línea que diga

```
unix -e
```[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

