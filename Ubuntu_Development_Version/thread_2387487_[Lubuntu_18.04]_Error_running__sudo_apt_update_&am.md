---
title: "[Lubuntu 18.04] Error running : sudo apt update &amp;&amp; sudo apt upgrade"
date: 2018-03-19
forum: Ubuntu Development Version
---

### Post by learnspeakthink on 2018-03-19
I'm used to updating and upgrading with sudo apt update && sudo apt upgrade ,every day .Today when I run it this was showed in LXTerminal :

```
tyuio@tyuio-h:~$ sudo apt update && sudo apt upgrade
[sudo] password for tyuio:
Obj:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
Obj:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Obj:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Obj:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
Obj:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Todos los paquetes están actualizados.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
4 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Configurando lxterminal (0.3.1-2ubuntu1) ...
/var/lib/dpkg/info/lxterminal.postinst: 26: /var/lib/dpkg/info/lxterminal.postinst: Syntax error: Unterminated quoted string
dpkg: error al procesar el paquete lxterminal (--configure):
instalado lxterminal paquete post-installation guión el subproceso devolvió un error con estado de salida 2
dpkg: problemas de dependencias impiden la configuración de lubuntu-gtk-core:
lubuntu-gtk-core depende de lxterminal; sin embargo:
El paquete `lxterminal' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-gtk-core (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de lubuntu-gtk-desktop:
lubuntu-gtk-desktop depende de lubuntu-gtk-core; sin embargo:
El paquete `lubuntu-gtk-core' no está configurado todavía.
lubuntu-gtk-desktop depende de lxterminal; sin embargo:
El paquete `lxterminal' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-gtk-desktop (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de lubuntu-desktop:
lubuntu-desktop depende de lubuntu-gtk-core; sin embargo:
El paquete `lubuntu-gtk-core' no está configurado todavía.
lubuntu-desktopNo se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
depende de lubuntu-gtk-desktop; sin embargo:
El paquete `lubuntu-gtk-desktop' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-desktop (--configure):
problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
lxterminal
lubuntu-gtk-core
lubuntu-gtk-desktop
lubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
_______________________________________________________________________________________________________________________

Any comment will be a great help .Thanks in advance .

---

### Post by Bashing-om on 2018-03-19
learnspeakthink; Hello'

Configuration issue .
Try this:
```

sudo apt clean
sudo apt autoclean
sudo apt -f install

```
Then run:
```

sudo dpkg --configure -a

```
Then run this again:
```

sudo apt -f install

```

still with errors. - post them and we see what else is to be done.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by learnspeakthink on 2018-03-19
> **Bashing-om said:**
> learnspeakthink; Hello'

Configuration issue .
Try this:
```

sudo apt clean
sudo apt autoclean
sudo apt -f install

```
Then run:
```

sudo dpkg --configure -a

```
Then run this again:
```

sudo apt -f install

```

still with errors. - post them and we see what else is to be done.[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]
[/INDENT]


Thank you so much ,you give me some steps to fix my own lubuntu 18.04 .I'll give the answer of this problem if someone have the same issue :

Firstly ,I do what Bashing-om have said .The ---LXterminal--- show the same .I'm not an expert in Linux ,but according to the error message Lxterminal -->must be fixed .

So I repeat the first two steps of Bashing-om ,and add sudo apt update && sudo apt upgrade ,thinking it'd be clean at all .And that was right and Lxterminal was saved .

```
tyuio@tyuio-h:~$ sudo apt clean
[sudo] password for tyuio: 
tyuio@tyuio-h:~$ sudo apt autoclean
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
tyuio@tyuio-h:~$ sudo apt -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
4 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
Configurando lxterminal (0.3.1-2ubuntu1) ...
/var/lib/dpkg/info/lxterminal.postinst: 26: /var/lib/dpkg/info/lxterminal.postinst: Syntax error: Unterminated quoted string
dpkg: error al procesar el paquete lxterminal (--configure):
 instalado lxterminal paquete post-installation guión el subproceso devolvió un error con estado de salida 2
dpkg: problemas de dependencias impiden la configuración de lubuntu-gtk-core:
 lubuntu-gtk-core depende de lxterminal; sin embargo:
 El paquete `lxterminal' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-gtk-core (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           dpkg: problemas de dependencias impiden la configuración de lubuntu-gtk-desktop:
 lubuntu-gtk-desktop depende de lubuntu-gtk-core; sin embargo:
 El paquete `lubuntu-gtk-core' no está configurado todavía.
 lubuntu-gtk-desktop depende de lxterminal; sin embargo:
 El paquete `lxterminal' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-gtk-desktop (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           dpkg: problemas de dependencias impiden la configuración de lubuntu-desktop:
 lubuntu-desktop depende de lubuntu-gtk-core; sin embargo:
 El paquete `lubuntu-gtk-core' no está configurado todavía.
 lubuntu-desktop depende de lubuntu-gtk-desktop; sin embargo:
 El paquete `lubuntu-gtk-desktop' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-desktop (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         Se encontraron errores al procesar:
 lxterminal
 lubuntu-gtk-core
 lubuntu-gtk-desktop
 lubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
tyuio@tyuio-h:~$ sudo dpkg --configure -a
Configurando lxterminal (0.3.1-2ubuntu1) ...
/var/lib/dpkg/info/lxterminal.postinst: 26: /var/lib/dpkg/info/lxterminal.postinst: Syntax error: Unterminated quoted string
dpkg: error al procesar el paquete lxterminal (--configure):
 instalado lxterminal paquete post-installation guión el subproceso devolvió un error con estado de salida 2
dpkg: problemas de dependencias impiden la configuración de lubuntu-gtk-core:
 lubuntu-gtk-core depende de lxterminal; sin embargo:
 El paquete `lxterminal' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-gtk-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de lubuntu-gtk-desktop:
 lubuntu-gtk-desktop depende de lubuntu-gtk-core; sin embargo:
 El paquete `lubuntu-gtk-core' no está configurado todavía.
 lubuntu-gtk-desktop depende de lxterminal; sin embargo:
 El paquete `lxterminal' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-gtk-desktop (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de lubuntu-desktop:
 lubuntu-desktop depende de lubuntu-gtk-core; sin embargo:
 El paquete `lubuntu-gtk-core' no está configurado todavía.
 lubuntu-desktop depende de lubuntu-gtk-desktop; sin embargo:
 El paquete `lubuntu-gtk-desktop' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-desktop (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 lxterminal
 lubuntu-gtk-core
 lubuntu-gtk-desktop
 lubuntu-desktop
tyuio@tyuio-h:~$ sudo apt -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
4 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
Configurando lxterminal (0.3.1-2ubuntu1) ...
/var/lib/dpkg/info/lxterminal.postinst: 26: /var/lib/dpkg/info/lxterminal.postinst: Syntax error: Unterminated quoted string
dpkg: error al procesar el paquete lxterminal (--configure):
 instalado lxterminal paquete post-installation guión el subproceso devolvió un error con estado de salida 2
dpkg: problemas de dependencias impiden la configuración de lubuntu-gtk-core:
 lubuntu-gtk-core depende de lxterminal; sin embargo:
 El paquete `lxterminal' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-gtk-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de lubuntu-gtk-desktop:
 lubuntu-gtk-desktop depende de lubuntu-gtk-core; sin embargo:
 El paquete `lubuntu-gtk-core' no está configurado todavía.
 lubuntu-gtk-desktop depende de lxterminal; sin embargo:
 El paquete `lxterminal' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-gtk-desktop (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de lubuntu-desktop:
 lubuntu-desktop depende de lubuntu-gtk-core; sin embargo:
 El paquete `lubuntu-gtk-core' no está configurado todavía.
 lubuntu-desktopNo se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                                           No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                      No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                depende de lubuntu-gtk-desktop; sin embargo:
 El paquete `lubuntu-gtk-desktop' no está configurado todavía.

dpkg: error al procesar el paquete lubuntu-desktop (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 lxterminal
 lubuntu-gtk-core
 lubuntu-gtk-desktop
 lubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
tyuio@tyuio-h:~$ sudo apt clean
tyuio@tyuio-h:~$ sudo apt autoclean
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
tyuio@tyuio-h:~$ sudo apt update && sudo apt upgrade
Obj:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
Des:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease [235 kB]
Obj:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Obj:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
Obj:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease
Des:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main amd64 Packages [1.017 kB]
Des:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main i386 Packages [1.008 kB]    
Des:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main amd64 DEP-11 Metadata [446 kB]
Des:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main DEP-11 64x64 Icons [245 kB] 
Des:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe i386 Packages [8.468 kB]
Des:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages [8.504 kB]
Des:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe Translation-en [4.944 kB]
Des:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 DEP-11 Metadata [3.031 kB]
Des:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe DEP-11 64x64 Icons [8.162 kB]
Des:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/multiverse amd64 DEP-11 Metadata [40,5 kB]
Des:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/multiverse DEP-11 64x64 Icons [209 kB]
Descargados 36,3 MB en 3min 15s (186 kB/s)                                     
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se puede actualizar 1 paquete. Ejecute «apt list --upgradable» para verlo.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
Se actualizarán los siguientes paquetes:
  lxterminal
1 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
4 no instalados del todo o eliminados.
Se necesita descargar 89,2 kB de archivos.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Des:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 lxterminal amd64 0.3.1-2ubuntu2 [89,2 kB]
Descargados 89,2 kB en 1s (68,2 kB/s) 
(Leyendo la base de datos ... 192141 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../lxterminal_0.3.1-2ubuntu2_amd64.deb ...
Desempaquetando lxterminal (0.3.1-2ubuntu2) sobre (0.3.1-2ubuntu1) ...
Procesando disparadores para mime-support (3.60ubuntu1) ...
Procesando disparadores para desktop-file-utils (0.23-1ubuntu3) ...
Configurando lxterminal (0.3.1-2ubuntu2) ...
update-alternatives: utilizando /usr/bin/lxterminal para proveer /usr/bin/x-terminal-emulator (x-terminal-emulator) en modo automático
Procesando disparadores para man-db (2.8.2-1) ...
Procesando disparadores para hicolor-icon-theme (0.17-2) ...
Configurando lubuntu-gtk-core (0.93) ...
Configurando lubuntu-gtk-desktop (0.93) ...
Configurando lubuntu-desktop (0.93) ...
```

Again thank you so much Bashing-om .

---

### Post by Bashing-om on 2018-03-19
learnspeakthink; Great !

You do good work :)

If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]together we do
[/INDENT][/INDENT]

---

### Post by coffeecat on 2018-03-19
*Thread moved to **Ubuntu Development Version**.*

---

