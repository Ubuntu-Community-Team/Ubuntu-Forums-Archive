---
title: "No tengo acceso de red a mi desktop desde mi laptop"
date: 2009-08-03
forum: Software
---

### Post by obedlink on 2009-08-03
hola

hace como 3 semanas ubuntu 9.04 se actualizo, trayendo con esto dos problemas.

1. Bracero no quema CD/DVD, el proceso de grabación transcurre sin problemas, pero cuando insertas de CD/DVD para comprobarlo, no hay nada grado en el, lo extraño es que bracero nunca da un mensaje d error en el proceso de grabado.

2. Para acceder a las carpetas compartidas que estan en mi computadora de escritorio, simplemente navegava hasta ella a traves de Nautilus sin utilizar contraseña ya que la otra PC (usando windows Vista) la tengo configurada para entrar libremente a ella desde otra PC. despues de la actualización, me sale una ventana donde tengo que poner el "grupo de trabajo", "usuario" y "contraseña".

lo que mas me interesa solucionar es lo de la red.

saludos espero su ayuda

---

### Post by guillermolisi on 2009-08-03
Mostranos el contenido de /etc/samba/smb.conf para saber como esta configurado. Tambien decinos a que grupo de trabajo pertenece/esta definida la otra PC (la desktop).

Respecto de Brasero, inicialo desde una terminal/consola y fijate que mensajes te da.

---

### Post by obedlink on 2009-08-03
aqui tengo adjunto el fichero smb.conf

---

### Post by guillermolisi on 2009-08-03
> **obedlink said:**
> aqui tengo adjunto el fichero smb.conf
Pareceria que el archivo esta sin configrar/personalizar. Esta como viene originalmente cuando bajas/actualizas e instalas el paquete por primera vez.

El grupo de red al que apunta es:
```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
```Fijate si coincide con el de la otra PC. Si no coincide nunca se veran en el mismo grupo.

Luego, tenes algunos pocos recursos compartidos, a saber:
```
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
```Y nada mas ....

Fijate en /etc/samba si te quedo una copia de tu smb.conf anterior, como para que veas las diferencias.

Logicamente, ambas maquinas deben utilizar IPs que esten en la misma red/bloque, sino tampoco se veran.

---

### Post by obedlink on 2009-08-03
pues el workgroup esta bien, de hecho de windows 7 a ubuntu puedo acceder, pero no al contrario, samba lo instale hace mucho, fecha exactano no puedo decirte, pero si que fue hace como 3 semanas.

---

### Post by guillermolisi on 2009-08-03
Si de Win7 podes ver Ubuntu y al reves no, entonces revisa el firewall del System7 para verificar que no este jugando en contra en este problema de conexion.

---

