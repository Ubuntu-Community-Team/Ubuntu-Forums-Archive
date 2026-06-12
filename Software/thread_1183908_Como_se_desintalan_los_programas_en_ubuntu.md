---
title: "Como se desintalan los programas en ubuntu?"
date: 2009-06-10
forum: Software
---

### Post by zhelo on 2009-06-10
sorry cacbros, soy super pregunaton y ademas y novato....
quiero desintalar unos programas que instale y no se como, trato en agregar o quitar poer no aparece la opcion de quitar

como lo hago a traves de sudo??
ya que no fio del synaptic por que los programas instalados tenian paquetes rotos y al deseintalar me procuduce error

---

### Post by Iced_R on 2009-06-10
sudo apt-get remove (o autoremove) programa_en_cuestión

Saludos.

---

### Post by moreback on 2009-06-10
En **Agregar o quitar** solamente tienes que quitarle el tic a la aplicación.

Confía en Synaptic, si te dio problemas es porque le pusiste algunas fuentes mal formadas o interrumpiste la descarga o mataste la aplicación a la mala.

Saludos.

---

### Post by Carlos C on 2009-06-10
Yo también recomiendo Synaptic, sobre todo para el que está empezando, es más intuitivo para buscar el nombre de los paquetes y ver las dependencias. Por lo mismo me parece más fácil a la hora de desinstalar algo. Es una muy buena herramienta. Ahora, instalar y desinstalar se puede hacer desde la consola con apt-get (como ya se te dijo) y con aptitude. Más información la puedes buscar acá:

[http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones](http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones)

---

### Post by nopersona on 2009-06-11
> **Carlos C said:**
> Yo también recomiendo Synaptic, sobre todo para el que está empezando, es más intuitivo para buscar el nombre de los paquetes y ver las dependencias. Por lo mismo me parece más fácil a la hora de desinstalar algo. Es una muy buena herramienta. Ahora, instalar y desinstalar se puede hacer desde la consola con apt-get (como ya se te dijo) y con aptitude. Más información la puedes buscar acá:

[http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones](http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones)


+1 para Synaptic, sobre todo si eres novato. Cuando tengas más recorrido verás qué fácil y cómodo es instalar, desintalar, compilar y un largo etc mediante la terminal.

Información extra sobre aptitude y apt-get, nunca está de más :p

[http://www.debian.org/international/spanish/contrib/apt-get-mini-COMO.html](http://www.debian.org/international/spanish/contrib/apt-get-mini-COMO.html)

[http://es.wikipedia.org/wiki/Aptitude](http://es.wikipedia.org/wiki/Aptitude)

[http://banyut.obolog.com/apt-get-vs-aptitude-106918](http://banyut.obolog.com/apt-get-vs-aptitude-106918)

---

### Post by rodrigovb-cl on 2009-06-11
> **zhelo said:**
> sorry cacbros, soy super pregunaton y ademas y novato....
quiero desintalar unos programas que instale y no se como, trato en agregar o quitar poer no aparece la opcion de quitar

como lo hago a traves de sudo??
ya que no fio del synaptic por que los programas instalados tenian paquetes rotos y al deseintalar me procuduce error

Ya se te contestó la pregunta pero quiero recomendarte algo, al parecer eres nuevo en estas lides por lo que te voy a recomendar lectura, más temprano que tarde te darás cuenta que lo más importante para el nuevo usuario de linux es "aprender a leer", al grano:

[https://wiki.ubuntu.com/ChileanTeam/ManualUbuntero/PrimerosPasos](https://wiki.ubuntu.com/ChileanTeam/ManualUbuntero/PrimerosPasos)

Cuando hayas leido la mitad de los documentos que están ahí, ya no nos necesitarás ;)

---

### Post by CdK1 on 2009-06-11
Acostumbrate temprano a usar la lìnea de òrdenes, puede que no tengas Synaptic o similares algún día -como yo- asi que apt-get autoremove es excelente ;)

---

