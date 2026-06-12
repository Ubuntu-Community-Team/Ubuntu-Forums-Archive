---
title: "ayuda con dvd doble capa"
date: 2009-06-19
forum: Software
---

### Post by methastasis on 2009-06-19
alguien sabe como montar una imagen de un dvd doble capa ? porque estoy intentando instalar los sims 3 en ubuntu 9.04 y ubuntu no me la cargar y cuando me la cargar no funciona ya lo intente todo esttoy a punto de hacer esto ](*,) gracias

---

### Post by pablo.s on 2009-06-19
Suponemos que es una imagen
de respaldo del original,
es asi?

---

### Post by methastasis on 2009-06-19
sip como la monto

---

### Post by Mauro22 on 2009-06-19
Para montar iso yo en gnome tengo:

Click derecho -> Abrir con <<Montador de archivo>>


Sino, desde la consola:

```
sudo mount -o loop archivodeimagen /carpetadestino
```

o graficamente con:

```
sudo apt-get install gmountiso && gmountiso
```


):P

---

### Post by methastasis on 2009-06-19
no me funciono

---

### Post by Mauro22 on 2009-06-19
A ver A ver...


Vamos a separar los porotos, asi es mas facil contar..


1) No te funcion que?

a) Montar la Imagen

b) La imagen en si

2) El juego que mencionas, corre en linux pero necesita de wine y de accelaracion grafica. Tienes ambos correctamente instalados??


):P

---

### Post by methastasis on 2009-06-19
a) montar la imagen 
no me aparece ningun archivo

---

### Post by Mauro22 on 2009-06-19
La imagen en que formato es?? (ISO, NGR, etc)

Con que programa la hiciste?? 

Usas la imagen porque no tenes lectora?? sino podes quemarla en un dvd virgen y usarlo de ahi.

---

### Post by methastasis on 2009-06-19
es iso
y me la paso un amigo y la uso para no comprar un dvd doble capa

---

### Post by Mauro22 on 2009-06-19
Ok...

peeroo:

haciendo este en consola:

sudo mount -o loop archivodeimagen /carpetadestino

en archivodeimagen pone el nombre y donde esta.. por ejemplo /home/usuario/miimagen.iso

en /carpeta de destino pone /tmp

sudo mount -o loop /home/usuario/miimagen.iso /tmp

le das enter, te pide tu contraseña y si todo sale OK (lease, no hay error) en /tmp tiene que estar la imagen montada y fijate que tenes que ejecutar....


Postea el comando ese y el resultado.

---

### Post by methastasis on 2009-06-19
che muchas gracias me re sirvio

---

### Post by aledruetta on 2009-06-20
Yo uso Gmount-iso que me funciona bien, porque al montador estándard de gnome no conseguí hacerlo funcionar.

Saludos,
Alejandro.

---

