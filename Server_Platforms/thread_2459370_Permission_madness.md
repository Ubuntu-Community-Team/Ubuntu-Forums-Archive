---
title: "Permission madness"
date: 2021-03-17
forum: Server Platforms
---

### Post by josedb on 2021-03-17
i have setted the owner, group , and mod to a folder and files inside. But, i can read some of them and some cannot. I have never seen this before.


```
rbackup@dul:~$ ls -l /home/Graficos/
total 252
drwxrwxr-x+ 12 jose jose 4096 nov 17 01:59 'Banco de Fotos (Solo Productos)'
drwxrwxr-x+ 43 jose jose 4096 mar 16  2020  Cafeteros
drwxrwxr-x+  4 jose jose 4096 ene 15 14:04  CIMES
drwxrwxr-x+  2 jose jose 4096 mar 16  2020 'Codigos 13 y 14'
drwxrwxr-x+  3 jose jose 4096 ene 15 15:51 'Corproacion del Bosque'
drwxrwxr-x+ 15 jose jose 4096 ene 15 16:23  Cremuccino
drwxrwxr-x+ 12 jose jose 4096 ene 15 15:04 'Della Tazza'
drwxrwxr-x+  8 jose jose 4096 ene 15 15:05  DLK
drwxrwxr-x+ 18 jose jose 4096 ene 15 15:55  Dulkre
drwxrwxr-x+ 11 jose jose 4096 ene 15 15:06 'Ever Cream'
drwxrwxr-x+  9 jose jose 4096 ene 15 15:07 'Ever Sweet'
drwxrwxr-x+ 11 jose jose 4096 mar 16  2020 'Fichas tecnicas y Carpetas de presentacion'
drwxrwxr-x+  5 jose jose 4096 mar 16  2020  Folletos
drwxrwxr-x+  5 jose jose 4096 nov 24 14:54 'Fotos Trabajo'
drwxrwxr-x+  6 jose jose 4096 nov 24 15:44  Fuentes
drwxrwxr-x+  5 jose jose 4096 mar 16  2020 'Golden Seed'
drwxrwxr-x+  3 jose jose 4096 mar 16  2020 'In The Cup'
drwxrwxr-x+  5 jose jose 4096 mar 16  2020  Krucor
drwxrwxr-x+ 11 jose jose 4096 ene 15 15:13  Logos
drwxrwxr-x+  9 jose jose 4096 ene 15 15:13 'Manjares del Sur'
drwxrwxr-x+  3 jose jose 4096 mar 16  2020  Marolio
drwxrwxr-x+  2 jose jose 4096 mar 16  2020  Mascaras
drwxrwxr-x+ 10 jose jose 4096 ene 15 16:14  Ordenar
drwxrwxr-x+  3 jose jose 4096 mar 16  2020  Panama
drwxrwxr-x+  2 jose jose 4096 mar 16  2020  Polimeros
drwxrwxr-x+  3 jose jose 4096 mar 16  2020  Publicidades
-rwxrwxr-x+  1 jose jose    0 ene 11 21:17  Readme.md
drwxrwxr-x+  8 jose jose 4096 nov 24 15:34  Renders
drwxrwxr-x+  8 jose jose 4096 ene 15 15:07  Salkré
drwxrwxr-x+  3 jose jose 4096 ene 15 15:07  Segafredo
drwxrwxr-x+  7 jose jose 4096 ene 15 15:10  Supermercados
drwxrwxr-x+  9 jose jose 4096 ene 15 16:11  Ubot
rbackup@dul:~$ ls -l /home/Graficos/CIMES
total 11340
-rwxrwxr-x+ 1 jose jose 11588235 sep  5  2019 cimes3.pdf
drwxrwxr-x+ 2 jose jose     4096 ene 15 14:04 Etiqueta
drwxrwxr-x+ 4 jose jose     4096 ene 15 14:04 Folleto
rbackup@dul:~$ ls -l /home/Graficos/Fuentes
ls: cannot open directory '/home/Graficos/Fuentes': Permission denied
rbackup@dul:~$

```

i have absolutly no idea where to start...

i can read files with user "jose" , and can read all files with user "rbackup" if i change the owner to itself.

---

### Post by TheFu on 2021-03-17
See the '+' at the end of each permissions.  That means someone is using ACLs which hide the true permissions.  The only way I know to see the true permissions with ACLs are used is using the **getfacl** command.  In almost 30 yrs on Unix systems, I've only needed to use ACLs 2 times for 2 directories, 10 yrs apart.

With ACLs it is easy to prevent the owner from having any access.

My suggestion is to _**remove all ACLs**_ and learn to use standard permissions as controlled by chmod, chgrp and chown.  You'll need to use the **setfacl** command.

---

