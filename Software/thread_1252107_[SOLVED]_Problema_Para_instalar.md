---
title: "[SOLVED] Problema Para instalar"
date: 2009-08-28
forum: Software
---

### Post by Mustaine666 on 2009-08-28
Bueno.. despues de mucho pensarlo me decidi a probar linux en mi pc..

me recomendaron el ubuntu 9.04..la ultima version.. si mis pensamientos no me fallan..

 el problema ocurre cuando intento actualizar con el gestor de actualizaciones.. y ocurre

esto..

  [[IMG]http://img46.imagevenue.com/loc126/th_75488_error_122_126lo.JPG[/IMG]]("http://img46.imagevenue.com/img.php?loc=loc126&image=75488_error_122_126lo.JPG")
cuando abro la consola y pongo lo q me dice.. no se q hacer..
 [IMG]http://img46.imagevenue.com/img.php?image=75488_error_122_126lo.JPG[/IMG] [[IMG]http://img206.imagevenue.com/loc48/th_75491_Pantallazo-2_122_48lo.JPG[/IMG]]("http://img206.imagevenue.com/img.php?loc=loc48&image=75491_Pantallazo-2_122_48lo.JPG")
[IMG]http://img206.imagevenue.com/img.php?image=75491_Pantallazo-2_122_48lo.JPG#[/IMG]

 

Y para cualquiero cosa q intento instalar.. me aparece el mismo error.

Me sale el mismo error cuando intento instalar Flash Player para firefox en linux.. no puedo entrar al foro..

hay alguna solucion algo por el estilo.. desde ya muchas gracias.. aviso.. estoy con windows ahora.. para poder armar el post!

quiero usar linux..  no quiero volver a windows.. pero los plugins para la musica de Rythmbox.. tampoco los puedo descargar..

---

### Post by staar on 2009-08-28
el comando correcto es ```
sudo dpkg --configure -a
``` fijate que no hay espacio entre los dos guiones y el configure...

para que estés precavido, este error aparece cuando la instalación de algún paquete fue interrumpida indebidamente, asegurate de dejar que apt (el manejador de paquetes, la base de 'Añadir y quitar aplicaciones', Synaptic, aptitude y/o apt-get, etc) termine de correr una vez que lo iniciaste, para eso esperá a que el programa te avise que terminó...

saludos

---

### Post by Mustaine666 on 2009-08-28
el problema es q no se que hacer... con eso..por q no me deja instalar nada..

---

### Post by staar on 2009-08-28
corré ese comando, dejá que termine de configurar los paquetes que le faltaron, y después vas a poder instalar normalmente...

saludos

---

### Post by Mustaine666 on 2009-08-28
ahora pruebo.. y aviso como me fue..

---

### Post by Mustaine666 on 2009-08-28
> **staar said:**
> corré ese comando, dejá que termine de configurar los paquetes que le faltaron, y después vas a poder instalar normalmente...

saludos


perdona si soy muy pesado.. o muy ignorante.. pero no sale.. que comando tengo q elegir despues de ejecutar "sudo dpkg --configure -a" ... 

gracias..

---

### Post by staar on 2009-08-28
nada, ningún comando, corré ESE comando (pero asegurate de escribirlo bien), poné tu contraseña, esperá que termine de correr y listo, después intentá instalar algo y ya vas a poder...

saludos

---

### Post by pablo.s on 2009-08-28
Lo que tienes que hacer
es abrir una terminal y
escribir el comando, luego
pulsar la tecla que dice Enter
y esperar que te devuelva el
prompt.

Una vez realizado esto,
escribes en esa misma 
terminal lo siguiente:

```
sudo apt-get update
```

---

### Post by Mustaine666 on 2009-08-28
> **staar said:**
> nada, ningún comando, corré ESE comando (pero asegurate de escribirlo bien), poné tu contraseña, esperá que termine de correr y listo, después intentá instalar algo y ya vas a poder...

saludos

> **pablo.s said:**
> Lo que tienes que hacer
es abrir una terminal y
escribir el comando, luego
pulsar la tecla que dice Enter
y esperar que te devuelva el
prompt.

Una vez realizado esto,
escribes en esa misma 
terminal lo siguiente:

```
sudo apt-get update
```


estaba poniendo mal el comando al principio.. ahora lo puse bien.. y anda.. 

son unos groso.. 

aca la prueba.. [[IMG]http://a.imagehost.org/t/0154/Pantallazo-2.jpg[/IMG]]("http://a.imagehost.org/view/0154/Pantallazo-2") 

....

acabo de terminar de actualizar todo.. muchisimas gracias!

---

