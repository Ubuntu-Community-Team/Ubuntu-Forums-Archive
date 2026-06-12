---
title: "Instalas Xampp o similar en Ubuntu 64"
date: 2008-08-12
forum: Software
---

### Post by gabyrsh on 2008-08-12
Hola chicos, he instalado Xampp en mi Ubuntu 8.04 - Hardy Heron de 64 bits. Ahora bien cuando quiero iniciar el servicio me dice:

```
XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.

```

Calculo que no arranca porque no es compatible con mi version. 
Entonces, me dicen algun software similar al Xampp para instalar y que me funcione???
Necesito Apache, Php5, Mysql y Phpmyadmin.

Disculpen, soy muy nuevo en esto. :(
Desde ya, un abrazo.

---

### Post by sergiom99 on 2008-08-12
si probas de instalarlo por separado?

---

### Post by facundocorradini on 2008-08-15
Hola gabyrsh, 

El problema es justamente tratar de usar XAMPP.  Es mucho más facil instalar todo desde synaptic: 

Sistema -->administración --> gestor de paquetes synaptic

ahí vas a Editar --> "marcar paquetes por tarea" y eliges "LAMP Server". 

Eso te instala y configura Apache, PHP y MySQL. Tal vez lo único que te haga falta después es phpmyadmin y algún editor de código (te recomiendo geany, Bluefish y/o Quanta) los buscas e instalas desde synaptic y listo. 

saludos!

---

### Post by jules82 on 2011-03-15
podrias usar mediante consola sudo apt-get install lamp^

---

