---
title: "antivirus"
date: 2009-04-07
forum: Software
---

### Post by marcelob_012 on 2009-04-07
Hola gente...tengo una duda existencial. yo tengo un disco con 2 particiones en donde la 1ª particion tengo windows xp y en el otro ubuntu. y en ubuntu instale el avast para poder chequear de virus la particion de xp. pero cuando me dispongo a elegir que carpetas quiero analizar me aparecen nada mas las de ubuntu y no la otra particion de xp. La pregunta como hago para analizar la otra particion de xp, porque en la carpeta mnt no me aparece nada los dispositivos montados..
Gracias

---

### Post by josecuervo86 on 2009-04-07
Una pregunta: porque pusiste el antivirus en Ubuntu en vez de Window$??

---

### Post by marcelob_012 on 2009-04-07
porque asi le reviso si tiene virus. en windows si tiene el antivirus pero para revisarlo es mejor hacerlo desde afuera. por eso mismo

---

### Post by josecuervo86 on 2009-04-07
Podrias explicarte un poco mejor? A que te referis con mejor?

---

### Post by guillermolisi on 2009-04-07
> **marcelob_012 said:**
> porque asi le reviso si tiene virus. en windows si tiene el antivirus pero para revisarlo es mejor hacerlo desde afuera. por eso mismo

Coincido con el fundamento.

Para revisar una maquina posiblemente infectada nada mejor que iniciarla con Linux y pasarle uno o mas antivirus. De esa forma los bichos que se camuflan, autoprotegen, mutan, etc. quedan totalmente desprotegidos porque no estan en un entorno operativo para el cual fueron hechos.

Normalmente utilizo el Trinity Rescue Kit que es una Linux con scripts que corren hasta cinco antivirus y que se actualiza antes de correrlos (via Internet). Lo uso iniciando desde CD o desde pendrive y hasta aqui me ha dado excelentes resultados, Confiker incluido.

Si les interesa lo pueden bajar de [http://trinityhome.org/](http://trinityhome.org/)

---

### Post by Mauro22 on 2009-04-07
En ubuntu los discos se montan en /media y no en /mnt...


Si no te aparecen, verifica tu fstab o monta la particion a mano!


Saludos!

---

### Post by marcelob_012 on 2009-04-07
gracias amigos tenian razon era en la carpeta media donde se cargaban los demas modulos. gracias. y por ende otra pregunta para que sirve la carpeta mnt????

---

### Post by Mauro22 on 2009-04-07
No se jaja, todo lo que se monta va a parar a Media... pero al parecer solo ocurre en Ubuntu, por lo que las demas usan mnt como punto de montaje

---

### Post by guillermolisi on 2009-04-07
> **marcelob_012 said:**
> gracias amigos tenian razon era en la carpeta media donde se cargaban los demas modulos. gracias. y por ende otra pregunta para que sirve la carpeta mnt????

Para mantener cierta compatibilidad historica con Unix, se me ocurre, ya que en realidad podrias montar en ese punto lo que quisieras (al igual que sucede con /media por defecto).

---

### Post by faktorqm on 2009-04-08
/mnt aparte de lo que dijo Guillermo sirve para montar cosas temporalmente, como si fuera una especie de carpeta temporal de montado. Entonces, te permite montar una particion que ya tenes montada en otro lado (sorprendido? :P) o montar en /mnt alguna particion que no sabes bien que onda para que no te tire abajo el sistema o de prueba, o para mover el /home de ubicacion por ejemplo. Saludos!

---

