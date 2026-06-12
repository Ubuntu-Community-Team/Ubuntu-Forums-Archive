---
title: "Ubuntu no me pidio cantidad memoria particiones"
date: 2011-08-22
forum: Software
---

### Post by Yvoty on 2011-08-22
Hola a todos, acabo de instalar Ubuntu y es mi primer Linux!! Soy super inexperta.

Habia leido en foros como instalar Ubuntu 10.4 y estaba preparada para asignar cantidad de memoria para las particiones Raiz, Swap y Home, pero en ningun momento me pidio eso. Estoy en duda que paso, si puedo cambiarlo ahora o al menos chequear que se haya asignado de forma conveniente.

Gracias a todos, estoy feliz de haberme pasado a Linux al fin!!!!

Saludos
Yvoty

---

### Post by dave01945 on 2011-08-22
> Hello everyone, I just installed Ubuntu Linux and it's my first! I'm super inexperienced.

I had read on forums how to install Ubuntu 10.4 and was prepared to allocate much memory for the root partition, swap and home, but at no time asked me that. I doubt that happened, if I can change it now or at least check that has been conveniently assigned.

Thank you all, I'm glad I happened to Linux at last!!

regards
Yvoty

this may help you get more response most people here are english speakers it's a good idea to translate first



esto puede ayudarle a obtener más respuesta mayoría de la gente aquí son de habla Inglés es una buena idea para traducir primero

---

### Post by Yvoty on 2011-08-22
Gracias Dave!!!

Thanks Dave!!!

---

### Post by gmunioz on 2011-08-23
Si estas decidida a realizar una instalación personalizada, estableciendo la cantidad de espacio en disco a asignar a cada partición, deberçías reinstalar.
Cuando llegues a particionamiento, debes elegir manual, entonces podrás borrar las particiones ya creadas por Ubuntu en forma automática y crear en el espacio, ahora liberado, las particiones como más te agraden.

---

### Post by Yvoty on 2011-08-23
Gracias Gabriel, parece andar bien asi, si no es imprescindible preferiria no reinstalar. ¿Cómo hago para ver las particiones que tengo y cuanta memoria tiene cada una? Asi les consulto si esta bien.

Gracias, saludos

---

### Post by samigina on 2011-08-23
Ubuntu incluye un programa llamado "Utilidad de Discos", lo puedes encontrar en el menu Sistema o Administración; con el puedes ver los detalles de tu disco y particiones.

Tambíen puedes instalar otro llamado Gparted, este te permite editar las particiones, pero si quieres cambiar algo, mejor reinstala.

---

### Post by asterix77 on 2011-08-23
Los live cd vienen con gparted incluido, es muy intuitivo de usarlo; en cambio si ya instalastes ubuntu al disco duro, este no se instala y debes hacerlo.

Abres una terminal y escribes lo siguiente:

$sudo apt-get install gparted

y les das enter.... y eso es todo.

luego lo ejecutas y eliges el disco duro a editar. 

En mi caso al instalar, primero accedo con el live cd, abro gparted, y realizo tres particiones:

a) La partición "raiz" / (formateada en ext4, 20 gigas creo que más que suficiente)
b) La partición "home" /home (resto del disco duro)
c) Y finalmente la partición swap (2 a 4 gigas).

Luego procedo con la instalación, colocando lo que que corresponde, en cada partición según corresponda.


Saludos

---

### Post by Yvoty on 2011-08-24
Hola chicos, entre a Utilidad de Discos y dice lo siguiente:

Disco duro ATA 165 GB

/dev/sda1
164 GB
164 GB ext4

/dev/sd2
extendido 468 MB

/dev/sd5
Area Inter
468 MB

Esto es poco? Si es asi reinstalo y trato de hacer lo que dicen (no entiendo bien!!)

Gracias, saludos

---

### Post by alfplayer on 2011-08-24
La opción por defecto de Ubuntu cuando se elige instalar en todo un disco es tener los datos en dos particiones: root y swap. Así, home queda contenida en root. Para tu caso sería así: sda1 es root y sda5 es swap. sda2 no contiene datos directamente sino que contiene sda5 (por eso sda2 y sda5 aparecen con el mismo tamaño).

El tamaño de swap puede ser muy bajo. Se recomienda que el tamaño sea mayor que el tamaño de la RAM así se puede hibernar. En cualquier caso, la computadora funciona.

La instalación estaría completa y no habría más para ocuparse de este tema.

---

### Post by Yvoty on 2011-08-24
Gracias!! Me quedo tranquila entonces....me re gusta Linux!!!

---

