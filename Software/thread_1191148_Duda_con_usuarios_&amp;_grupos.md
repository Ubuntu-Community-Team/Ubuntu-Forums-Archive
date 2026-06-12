---
title: "Duda con usuarios &amp; grupos"
date: 2009-06-18
forum: Software
---

### Post by Mauro22 on 2009-06-18
Hola!!


Ayer actualicé el soft del ipod mediante xp en virtualbox... Lamentablemente en el medio del proceso, virtualbox dejó de "reconocer" los usb (nota: Uso la version PUEL que anda joya con los USB). Terminé el proceso en vista y me puse a investigar que pacho con los USB...


1) Desde ese momento no andan... Aparecen como "No Disponible" :S
2) En la imagen a continuacion... no deberia estar yo (o sea mi usuario) ??? porque no se si viene de ahi el problema de virtualbox...


[IMG]http://s3.subirimagenes.com:81/otros/previo/thump_2745806usuarios.jpg[/IMG]


PD: Instale 9.04 manteniendo mi /home y en la instalacion puse el mismo nombre para que me reconozca esa particion. No hubo problemas hasta que se me dio por fijarme.


Gracias totales!

---

### Post by WanderingKnight on 2009-06-18
No entiendo, no está tu usuario en el listado?

---

### Post by guillermolisi on 2009-06-18
Fijate si tu user pertenece al grupo Virtualbox (o vbox).

---

### Post by Mauro22 on 2009-06-19
El problema es que mi usuario no aparece en la lista. Como pueden ver aparece solo root. 

Para usar VB normalmente, meti a root dentro del grupo de VB y me deja usar los puertos USB.  


Que hago? creo un usuario nuevo? o le pongo el mismo nombre que ahora ? Me reemplaza el home?



Gracias por las respuestas!!

---

### Post by gmunioz on 2009-06-19
Hola mau.....:

Visita esta página:

```
http://www.linuxtotal.com.mx/index.php?cont=info_admon_008
```

---

### Post by guillermolisi on 2009-06-19
> **Mauro22 said:**
> El problema es que mi usuario no aparece en la lista. Como pueden ver aparece solo root. 

Para usar VB normalmente, meti a root dentro del grupo de VB y me deja usar los puertos USB.  


Que hago? creo un usuario nuevo? o le pongo el mismo nombre que ahora ? Me reemplaza el home?



Gracias por las respuestas!!
No aparece porque posiblemente no forma parte del grupoVBox. Por eso te decia que verifiques eso.

Antes de crear uno nuevo empeza revisando el que estabas usando.

---

### Post by Mister X on 2009-06-19
los usuarios y contraseñas del sistema se guardan en /etc/passwd y /etc/shadow, fijate ahi, no creo que te haya borrado tu usuario

---

### Post by Mauro22 on 2009-06-19
Hola!!

Tomen gracias por sus respuestas!


Cuando llego a casa pruebo bien el link que me dejaron y lo de /etc/...


Lo mas curioso es que me puedo logear, hacer todo normalmente. Pero cuando voy a grupos aparece solo root y en el grupo de VirtualBox aparece solo root para marcar...

):P

---

### Post by Mauro22 on 2009-06-19
> **gmunioz said:**
> Hola mau.....:

Visita esta página:

```
http://www.linuxtotal.com.mx/index.php?cont=info_admon_008
```


Gracias por la info!!



[quote=Mister X]los usuarios y contraseñas del sistema se guardan en /etc/passwd y /etc/shadow, fijate ahi, no creo que te haya borrado tu usuario[/quote]

Me fije y sí, aparezco en ambos.


[quote=guillermolisi]No aparece porque posiblemente no forma parte del grupoVBox. Por eso te decia que verifiques eso.

Antes de crear uno nuevo empeza revisando el que estabas usando.[/quote]

No aparece porque ni siquiera me lo reconoce ubuntu. En la imagen tiene que aparecer root y mauro... solo aparece root, como pueden apreciar.


Agregado:

Si agrego un usuario nuevo, y pongo "mauro" como nombre, me dice que ya existe! :S y no me deja crearlo... (existe pero no en la lista, con lo cual no me puedo agregar al VBgroup).



Hasta ahora la que se me ocurre es crear un usuario distinto y migrar mi home.


Gracias otra vez a todos!

---

### Post by guillermolisi on 2009-06-19
Cuando vas a la administracion de usuarios no aparece ni siquiera oculto o con algun atributo especial ?

Te fijaste en una terminal/consola si hubo alguna alteracion en los permisos, owner, group del directorio /home/mauro ?

---

### Post by Mauro22 on 2009-06-19
> **guillermolisi said:**
> Cuando vas a la administracion de usuarios no aparece ni siquiera oculto o con algun atributo especial ?


Nop, nada, solo root. Y ahora de curiosidad me fije los atributos de este root y solo tiene previlegio para usar VirtualBox... :mad:

> **guillermolisi said:**
> 
Te fijaste en una terminal/consola si hubo alguna alteracion en los permisos, owner, group del directorio /home/mauro ?




Check.

Todo me pertenece.

```
drwxr-xr-x 89 mauro mauro   12288 2009-06-19 19:15 mauro
```



Aca hay gato encerrado, o me cambiaron de caballo a mitad del rio...

---

### Post by guillermolisi on 2009-06-19
Y si normalizas los atributos de root antes de toquetear lo demas ?

Posiblemente por eso no te lee el resto de las cuentas de usuarios de la maquina (mira que hay mas que root y mauro)

---

### Post by Mister X on 2009-06-20
> **Mauro22 said:**
> 

Hasta ahora la que se me ocurre es crear un usuario distinto y migrar mi home.



Ni lo pienses!!!! jaja

tenes dos alternativas: 
editas a mano /etc/group y le agregas el grupo a tu usuario al final de la linea

o en la consola:
```
sudo usermod -a -G vboxusers <usuario>
```

saludos

---

### Post by Mauro22 on 2009-06-20
> **guillermolisi said:**
> Y si normalizas los atributos de root antes de toquetear lo demas ?

Posiblemente por eso no te lee el resto de las cuentas de usuarios de la maquina (mira que hay mas que root y mauro)

Lo hice, y sigue aparenciendo root unicamente. Gracias!!



> **Mister X said:**
> Ni lo pienses!!!! jaja

tenes dos alternativas: 
editas a mano /etc/group y le agregas el grupo a tu usuario al final de la linea

o en la consola:
```
sudo usermod -a -G vboxusers <usuario>
```

saludos


Lo hice por consola y chequeé por gedit y lo agregó pero no hizo efecto en el VirtualBox...  Leer EDIT



EDIT: Cerre sesión y ahora me deja usar los usb en VB :D Gracias!!!
EDIT2: Aun sigue apareciendo root como unico usuario del sistema. Pero el 50% del problema esta!!


Gracias!!

---

