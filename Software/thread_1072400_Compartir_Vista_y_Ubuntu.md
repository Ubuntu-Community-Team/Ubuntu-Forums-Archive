---
title: "Compartir Vista y Ubuntu"
date: 2009-02-17
forum: Software
---

### Post by h9005 on 2009-02-17
Buenas a todos tengo instalado Vista original pero me gstaria instalar tambien ubuntu amd 64. No encuentro el tutorial para compartir el disco con los dos so. Se que habia que hacer al menos cinco particiones, pero no recuerdo como achicar la ntfs sin tocar el vista.

---

### Post by Mauro22 on 2009-02-17
Te digo mi caso.

Yo en la notebook me vino vista original y dos particiones 'ACER' y 'DATA'.

Yo use la 2da (DATA) e instale Ubuntu mediante Wubi, porque todavia esta en garantia y todo eso.


hasta ahora 0 problemas. Ademas II ya esta tan probado que es muy estable y no se nota que trabaja sobre ntfs y nada de eso.

---

### Post by h9005 on 2009-02-17
Siempre he usado ubuntu compartido con windows y no he tenido problemas. Solo que las veces anteriores formateaba de cero. Ahora no quiero tocar la particion de Vista original.

---

### Post by guillermolisi on 2009-02-17
> **h9005 said:**
> Buenas a todos tengo instalado Vista original pero me gstaria instalar tambien ubuntu amd 64. No encuentro el tutorial para compartir el disco con los dos so. Se que habia que hacer al menos cinco particiones, pero no recuerdo como achicar la ntfs sin tocar el vista.
Estamos hablando de acceder a una particion NTFS desde Ubuntu ?
De Dual Boot ?

---

### Post by h9005 on 2009-02-17
Sí todo eso. Iniciar con el grub, elegir SO, etc.

---

### Post by guillermolisi on 2009-02-17
> **h9005 said:**
> Sí todo eso. Iniciar con el grub, elegir SO, etc.
Hasta no hace mucho (Octubre/Noviembre del 2008) recomendaba no usar dual boot con Vista (y no era el unico que hacia esta recomendacion) ya que los casos conocidos hasta ese momento presentaron problemas. El Grub que maneja Vista sobreescribia la informacion que registraba su equivalente de Ubuntu en forma no regular, es decir sin un patron aparente, y te dejaba sin el doble arranque. Por esa razon recomendaba hacer dual boot con XP.

Ahora Mauro22 dice que habiendolo instalado con Wubi le funciona, asi que puede ser que Wubi juegue un papel importante en este tema (las otras instalaciones no usaron Wubi).

Para modificar el tamaño de la particion donde queres hacer lugar, con el administrador de discos del Vista no podes remarcarla para liberar espacio ?

Wubi no hace este trabajo por vos ? (nunca use Wubi a la fecha)

---

### Post by h9005 on 2009-02-17
Instale ubuntu, el grub arranca y todo me muestra las opciones pero al elegir vista no carga, dice que probablemente debido a cambios de hard. habia un programa que recuperaba los arranques...

---

### Post by sergiom99 on 2009-02-17
el mejor tutorial lo encontre aca:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Yo lo use dos veces ya, pero ambas con XP y quedo perfecto. En mi laptop hace tanto que no entro a XP que creo que todavia debe estar ahi ;-)

---

### Post by sajnox on 2009-02-17
> **guillermolisi said:**
> Ahora Mauro22 dice que habiendolo instalado con Wubi le funciona, asi que puede ser que Wubi juegue un papel importante en este tema (las otras instalaciones no usaron Wubi).

Wubi: hace la instalacion sobre ntfs por lo que no necesitas particionar ni redimensionar, ni nada.

Ademas no usa el grub sino que trabaja sobre el gestor de arranque de windows.

Si bien no es la opcion mas "purista" que conozco las veces que lo probe no note ninguna caida en el rendimiento del equipo, seguramente si se hace un benchmark dara algo de perdida, pero hasta ahora no escuche de nadie que se haya suicidado por ese tema

---

### Post by Mauro22 on 2009-02-18
> **sajnox said:**
> ...seguramente si se hace un benchmark dara algo de perdida, pero hasta ahora no escuche de nadie que se haya suicidado por ese tema


Busque sobre benchmark y encontre en los repositorios a 'hardinfo' que genera una especie de 'benchmark' (medio corto):

Benchmarks


CPU ZLib

This Machine	10683,416
PowerPC 740/750 (280.00MHz)	2150.597408
Intel(R) Celeron(R) M processor 1.50GHz	8761.604561


CPU Fibonacci

This Machine	4,425
Intel(R) Celeron(R) M processor 1.50GHz	8.1375674
PowerPC 740/750 (280.00MHz)	58.07682


CPU MD5

This Machine	65,714
PowerPC 740/750 (280.00MHz)	7.115258
Intel(R) Celeron(R) M processor 1.50GHz	38.6607998


CPU SHA1

This Machine	75,690
PowerPC 740/750 (280.00MHz)	6.761451
Intel(R) Celeron(R) M processor 1.50GHz	49.6752776

CPU Blowfish

This Machine	16,666
Intel(R) Celeron(R) M processor 1.50GHz	26.1876862
PowerPC 740/750 (280.00MHz)	172.816713

FPU Raytracing

This Machine	22,385
Intel(R) Celeron(R) M processor 1.50GHz	40.8816714
PowerPC 740/750 (280.00MHz)	161.312647


Siendo 'This Machine' mi pc:
+ Intel Pentium DualCore T3200 2.0ghz
+ 2GB


Usando wubi, a ver si alguien con pc parecida lo hace desde la instalacion "normal".

---

### Post by h9005 on 2009-02-18
Solucionado chicos, redmiensione las particiones con Parted Magic (gparted), arme 2 ext3, una swap y una dos ntfs.
Reinicié, instale ubuntu 8.10 64, andaba todo menos vista. Con el disco de recuperacion/instalacion de vista elegi reparar, y MILAGROSAMENTE encontro solamente un problema en el arranque. Lo reparó y al reiniciar ya funcionaba vista. Gracias por la ayuda chicos. No me animé a formatear en ext4.

---

