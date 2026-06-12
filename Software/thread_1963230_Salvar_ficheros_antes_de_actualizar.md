---
title: "Salvar ficheros antes de actualizar"
date: 2012-04-22
forum: Software
---

### Post by Brath-ga on 2012-04-22
Hola a tod@s.

Tengo instalado Ubuntu 10.10 en mi equipo y lo tengo totalmente a mi gusto.
El caso es que al haber finalizado su vida útil, quiero instalar la versión 12.04.


Quiero hacer la nueva instalación desde cero, porque ya tengo tenido problemas con las actualizaciones de otras versiones de Ubuntu anteriores y al final tenía que instalar todo de nuevo.

El problema viene dado en que tengo, por ejemplo, amarok con una cantidad enorme de álbunes y utilizo mysql como base de datos.

Aunque los datos los tengo en una partición NTFS aparte y se que estos no tienen peligro, la base de datos amarokdb, no se donde se encuentra fisicamente y me dió mucho trabajo ponerla bien por lo cual no deseo perderla.

Podríais indicarme donde se encuentra amarokdb para poder salvarla a un disco externo?

Gracias

---

### Post by rojojuan on 2012-04-22
En consola podés usar el comando whereis seguido del nombe del programa o archivo.
Por ejemplo, para ver donde se encuentra instalado libreoffice: whereis libreoffice y te devuelve la ubicación.




> **Brath-ga said:**
> Hola a tod@s.

Tengo instalado Ubuntu 10.10 en mi equipo y lo tengo totalmente a mi gusto.
El caso es que al haber finalizado su vida útil, quiero instalar la versión 12.04.


Quiero hacer la nueva instalación desde cero, porque ya tengo tenido problemas con las actualizaciones de otras versiones de Ubuntu anteriores y al final tenía que instalar todo de nuevo.

El problema viene dado en que tengo, por ejemplo, amarok con una cantidad enorme de álbunes y utilizo mysql como base de datos.

Aunque los datos los tengo en una partición NTFS aparte y se que estos no tienen peligro, la base de datos amarokdb, no se donde se encuentra fisicamente y me dió mucho trabajo ponerla bien por lo cual no deseo perderla.

Podríais indicarme donde se encuentra amarokdb para poder salvarla a un disco externo?

Gracias

---

### Post by Brath-ga on 2012-04-22
Gracias por tu respuesta rojojuan, pero no me informa de donde está.

Me sale solo el nombre seguido de 2 puntos.
```

whereis amarokdb
amarokdb:


```

Mira que llevo buscado, pero no encuentro en donde guarda mysql las bases de datos.

---

### Post by rojojuan on 2012-04-23
Fijate si te sirve este link:

[http://amarok.kde.org/wiki/Installation_HowTo/es](http://amarok.kde.org/wiki/Installation_HowTo/es)




> **Brath-ga said:**
> Gracias por tu respuesta rojojuan, pero no me informa de donde está.

Me sale solo el nombre seguido de 2 puntos.
```

whereis amarokdb
amarokdb:


```

Mira que llevo buscado, pero no encuentro en donde guarda mysql las bases de datos.

---

### Post by guillermolisi on 2012-04-23
amarokdb es una base de datos dentro de MySQL y para hacer backup de la misma tenes que usar la herramienta de backup que posee MySQL para tal fin.

Si vas a hacer una instalacion fresca, nueva, te conviene, ademas, copiar los contenidos de los directorios /etc, /home/<tu_usuario> y /var (especialmente si utilizas MySQL, PostgreSQL, webserver, etc. y los instalaste en su ubicacion por defecto.

Te serviran de guia llegado el caso que necesites ajustar alguna configuracion o para restituir todo a la version anterior.

---

