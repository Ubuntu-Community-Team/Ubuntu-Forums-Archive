---
title: "Problema en la Actualización"
date: 2009-11-08
forum: Software
---

### Post by pablotestori on 2009-11-08
Hola; utilizando el gestor de actualizaciones , intenté pasar del  9.04 JJ al 9.10 Karmic Koala; se descargaron los paquetes y comenzó a instalar la actualización reemplazando ficheros.El problema es que por un error que no tiene que ver con la instalación de dichos paquetes la maquina se me colgó y tuve que reiniciarla.Ahora no me permite entrar al sistema operativo con entorno gráfico, si como usuario root.

Como puedo hacer que continue la instalación de los paquetes de la actualización ya descargados?

Qué sudo puedo utilizar?

Al que me pueda ayudar se lo voy a agradecer ya que tengo documentos muy importantes que no puedo perder

---

### Post by josecuervo86 on 2009-11-08
Mira, si tenes el /home separado en una partición separada, lo mejor creo yo seria realizar una instalación limpia. Si no es asi, podes entrar con el LiveCD y "backapear" tus datos importantes ya sea en una partición nueva que podes crear con Gparted o en algún medio físico alternativo (CD, Pendrive) para poder realizar una instalación limpia.
De cualquier manera, espera a que otros respondan que tal vez le encuentren la vuelta por otro lado sin tener que reinstalar. 

Saludos!

---

### Post by pablotestori on 2009-11-08
> **josecuervo86 said:**
> Mira, si tenes el /home separado en una partición separada, lo mejor creo yo seria realizar una instalación limpia. Si no es asi, podes entrar con el LiveCD y "backapear" tus datos importantes ya sea en una partición nueva que podes crear con Gparted o en algún medio físico alternativo (CD, Pendrive) para poder realizar una instalación limpia.
De cualquier manera, espera a que otros respondan que tal vez le encuentren la vuelta por otro lado sin tener que reinstalar. 

Saludos!


Muchas gracias; el precio que uno tiene que pagar por la estupidez

---

### Post by Mauro22 on 2009-11-08
Primeros los datos. Una ve que tengas back up con un live cd. Reinstala, ya esta todo corrupto

---

### Post by josecuervo86 on 2009-11-08
> **pablotestori said:**
> Muchas gracias; el precio que uno tiene que pagar por la estupidez

Dicen que a los golpes se aprende. De cualquier manera, no hay mal que por bien no venga, si la solución es reinstalar ahora podras hacerlo con la partición /home separada, algo que es muy recomendable justamente por si pasan cosas como estas!

Igual, espera a ver que opinen otros usuarios!

---

### Post by pablotestori on 2009-11-08
> **Mauro22 said:**
> Primeros los datos. Una ve que tengas back up con un live cd. Reinstala, ya esta todo corrupto


Ahora el live cd que utilizo es el de la versión 9.10 o la 9.04 que tenía instalada?

---

### Post by pablo.s on 2009-11-08
> **pablotestori said:**
> Como puedo hacer que continue la instalación de los paquetes de la actualización ya descargados?

Qué sudo puedo utilizar?

Al que me pueda ayudar se lo voy a agradecer ya que tengo documentos muy importantes que no puedo perder

Antes de hacer algo, probá
desde la consola, si es que
tenés Internet, con hacer

```
sudo apt-get dist-upgrade
```

y ver si resume la actualización.

---

### Post by Mauro22 on 2009-11-08
A que tengas a mano. Mínimo que Levante los discos con los datos y algún lado para meterlos ( otro disco, pendrive, cd, etc )

---

