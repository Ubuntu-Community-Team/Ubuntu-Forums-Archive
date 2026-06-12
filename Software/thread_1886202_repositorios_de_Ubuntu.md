---
title: "repositorios de Ubuntu"
date: 2011-11-24
forum: Software
---

### Post by jandry on 2011-11-24
Amig@s del foro: comence a enseñar cocina en un Centro de Formacion Profesional de la Municipalidad de la Ciudad de Buenos Aires y como siempre me acerque a los profes de informatica para ver la posibilidad de hablar del SL con los alumnos, encontre uno que simpatiza con Ubuntu y me pidio cds de versiones anteriores de Ubuntu para instalar en compus con pocos recursos, despues de instalar 9.04 me avisa que los repositorios estan caidos, reviso mi netbook con Karmic y me pasa lo mismo, no puedo actualizar nada por estar caidos los repositorios. Pregunta: esto es porque las versiones ya no tienen soporte? Si es asi que debo hacer para solucionarlo? en la mia hace un timepo instale Squeezy y anduvo bien pero la idea es aprovechar los pocos recursos de las compus y presentar a los chicos una distro super practica como es Ubuntu..
Cualquier soga que me tiren sera agradecida.
Abrazo Ubuntero

---

### Post by BC59 on 2011-11-24
Tienes razón, Karmic no tiene soporte por consiguiente los repositorios no funcionan.

No existe solución fácil.

Pero podrías utilizar las nuevas versiones del Ubuntu que son muchísimo mejores que Karmic y con menos incompatibilidades.

---

### Post by tersogar on 2011-11-24
Dado que necesitas actualizar podrías tratar xubuntu.

---

### Post by guillermolisi on 2011-11-24
Tambien podes probar Lubuntu 11.10 (XFCE + LXDE + OpenBox como WinManager)
Fijate los requerimientos minimos antes de sugerir alternativas. Si las PCs no llegan a esos minimos entonces mi recomendacion pasa por otra distribucion mas ajustada a las posibilidades (Puppy basado en Ubuntu, ArchBang (basado en Arch), CrunchBang (como ArchBang - OpenBox + XFCE - pero basado en Debian).

Probe las tres y todas me han parecido muy buenas distribuciones. Primero las probe en VMs y luego en maquinas reales y no me decepcionaron. De hecho tengo una PC con Athlon 950 Mhz y 512Mb RAM corriendo ArchBang y funciona muy pero muy bien.

---

### Post by EnriqueK on 2011-11-24
Cambia tu sources.list .Ejecuta en un terminal
sudo gedit /etc/apt/sources.list
Borra todo el contenido  y lo reeplazas por el siguiente

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) karmic-security main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) karmic-security main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse 

Luego
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install paquete

---

