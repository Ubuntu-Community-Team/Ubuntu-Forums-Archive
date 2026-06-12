---
title: "Xampp en Linux"
date: 2009-01-08
forum: Software
---

### Post by lucasfava on 2009-01-08
Alguien tiene instalado este servidor en ubuntu:)

---

### Post by Hei Ku on 2009-01-08
Hubo un thread en el foro de Software hace un tiempo por el xampp.

---

### Post by z37a on 2009-01-10
Yo lo probe hace un tiempo, peor la verdad no conviene, o sea simplemente podes hacer una linea en el terminal y tenes instalado lo mismo, con actualizaciones de tu sistema.

Hace esto:

```
sudo apt-get install apache2 mysql-server php5 phpmyadmin
```

con solo eso tenes instalado lo mismo pero en ubuntu, cada vez que salga un update te va a avisar bajas y mantenes al dia.

---

### Post by Hei Ku on 2009-01-10
Hmmm, el preguntaba por Xammp, que es para armar un home theater, y tu respuesta es para instalar un LAMP (Linux, Apache, MySQL, PHP) :D

---

### Post by lucasfava on 2009-01-10
El Xampp es un servidor Php, viene todo junto apache, Php y Mysql, por eso lo preguntaba. 
Voy a instalar LAMP entonces. :)

---

### Post by z37a on 2009-01-10
> **lucasfava said:**
> El Xampp es un servidor Php, viene todo junto apache, Php y Mysql, por eso lo preguntaba. 
Voy a instalar LAMP entonces. :)


No te conviene bajar e instalar un paquet aislado asi, como te dije lo que te conviene es instalar los paquetes que vienen en la distribucion, con esa linea tenes todo lo que trae el xampp o lamp, o sea Apache+PHP+Mysql, aun asi en synaptip podes instalar el grupo de webserver que te incluye todo esto, con xampp o lamp tenes que esperar a una actualizacion en general del paquete, con esta forma que te comente si se actualiza apache solo ya tenes disponible la actualizacion, y asi mantenes al dia los update(fundamental en un servido en internet)

---

### Post by lucasfava on 2009-01-10
> **z37a said:**
> No te conviene bajar e instalar un paquet aislado asi, como te dije lo que te conviene es instalar los paquetes que vienen en la distribucion, con esa linea tenes todo lo que trae el xampp o lamp, o sea Apache+PHP+Mysql, aun asi en synaptip podes instalar el grupo de webserver que te incluye todo esto, con xampp o lamp tenes que esperar a una actualizacion en general del paquete, con esta forma que te comente si se actualiza apache solo ya tenes disponible la actualizacion, y asi mantenes al dia los update(fundamental en un servido en internet)

Lamp son todos los paquetes desde apache a mysql, instalados en distros Linux. Igual ya te entendi 	:lolflag:

---

