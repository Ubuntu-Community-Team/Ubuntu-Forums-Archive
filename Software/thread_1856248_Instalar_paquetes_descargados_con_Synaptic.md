---
title: "Instalar paquetes descargados con Synaptic"
date: 2011-10-07
forum: Software
---

### Post by negrotuxero on 2011-10-07
Hola que tal.. hacia mucho tiempo que no me daba una vuelta por acá xD

Bueno mi problema es que instale ubuntu 11.04 en la pc de mi novia que tiene una conexión 3G de movistar(super lenta como sabrán), para instalar programas la verdad que estaba dificil..Asi que abri synaptic marque todos los programas que quería instalar hice el script de descarga y lo guarde en una carpeta.. corrí el script desde consola y espere que bajara todos los paquetes.. verifique que descargara todos y hoy cuando abrí los paquetes desde el gestor Synaptic quiso descargarlos desde Internet así que retire el modem y procedí a intentarlo una ves mas.. supuestamente había instalado todo, el problema fue que al revisar el menú.. estaban instalados 2 o 3 programas, de los demás ni noticias..

---

### Post by euzkoarima on 2011-10-08
Por lo que contás, da la impresión que no bajaron todos los paquetes cuando corriste el script. Por eso al instalar, synaptic volvió a intentar conectarse.
Al cortarle la conexión, solo instaló lo que había logrado bajar.

Una prueba que podés hacer es generar el script y correrlo en otra pc que tenga buena conexión (y la capacidad de correr el script, obviamente)

Saludos,
Eduardo

---

### Post by negrotuxero on 2011-10-10
Corrí el script 3 veces y comprobó que descargo todos los paquetes.. es mas los conté.. mi conexión es de 6 megas.. estoy seguro que eso no fue.. y también me asegure que bajara las dependencias..

---

### Post by euzkoarima on 2011-10-10
Entonces, si tiene todo bajado, no se porque synaptic vuelve a tratar de conectarse.

Revisá en synaptic como aparece los paquetes que bajaste (deberían figurar todos como instalados). Si es así hay que ver porque no te aparecen en el menú (supongo que a eso te referías con "estaban instalados 2 o 3 programas, de los demás ni noticias").
Las raras veces que instalé un programa y no quedó disponible en el menú, fué porque había un error en el paquete y no creaba el item de menú, pero el programa lo podía lanzar desde consola. Con lo cuál, luego agregaba la entrada de menú a mano.

Saludos,
Eduardo

---

### Post by guillermolisi on 2011-10-10
Como estas aplicando en Synaptic los paquetes que bajaste con el script ?

Si tenes uno o varios paquetes para ser aplicados al sistema, habiendolos bajado fuera del proceso corriente que lleva a cabo Synaptic, deberias utilizar la opcion "File - Add Downloaded Packages". El tip que aparece si posas el cursor sobre esa opcion del menu dice > Add packages downloaded with the 'Generate package download script" feature to the system

---

### Post by EnriqueK on 2011-10-11
Leete este link en donde  se detalla el uso del Script en windows y además la forma de instalar los paquetes descargados.
[http://www.ubuntu-es.org/node/67349](http://www.ubuntu-es.org/node/67349)

---

### Post by negrotuxero on 2011-10-11
exactamente desde synaptic y con la opcion de instalar paquetes descargados es como los instale.. en este momento me estoy bajando los repositorios enteros ya casi termino.. luego voy a quemarlo con aptoncd y subire el archivo y el script que utilice ...

---

### Post by euzkoarima on 2011-10-11
> **negrotuxero said:**
> exactamente desde synaptic y con la opcion de instalar paquetes descargados es como los instale.. en este momento me estoy bajando los repositorios enteros ya casi termino.. luego voy a quemarlo con aptoncd y subire el archivo y el script que utilice ...

Ja!! no te andas con chiquitas !!
Bueno, mientras que funcione, en buena hora. Suerte !!

Saludos,
Eduardo

---

### Post by negrotuxero on 2011-10-18
Bueno sigo con un problemon... baje repositorios enteros.. genere un Packages.gz con los paquetes instalables.. agregue la carpeta como repositorio... tod joya hasta aca .. aparecen los paquetes que baje en la lista y todo.. al momento de instalar cualquier programa me salen errores de dependencias.. paquetes rotos.. paquetes no instalables.. y nunca instala nada.. alguna idea??

---

### Post by euzkoarima on 2011-10-19
Raro, la verdad ni idea.
Si podes copianos los mensajes de error para ver si con eso llegamos a darnos cuenta que pasa.

Saludos,
Eduardo

---

