---
title: "[SOLVED] No puedo instalar un .deb"
date: 2009-07-03
forum: Software
---

### Post by kornykyano on 2009-07-03
Hola gente:

Quiero instalar un .deb pero sale diciendo que me falta **libjson-glib-1.0-0**. El tema es que no esta disponible para Hardy Heron. Alguna idea?

Saludos

---

### Post by guillermolisi on 2009-07-03
> **kornykyano said:**
> Hola gente:

Quiero instalar un .deb pero sale diciendo que me falta **libjson-glib-1.0-0**. El tema es que no esta disponible para Hardy Heron. Alguna idea?

Saludos
Bueno, ya sabemos que usas HH. Faltaria que nos cuentes que paquete .deb queres instalar y como lo estas queriendo instalar, asi nos vamos poniendo en ambiente para ayudarte.

En los repos de HH solo encontre libjson-ruby ....

---

### Post by juancarlospaco on 2009-07-03
[B]./configure
make
sudo checkinstall[/B]

---

### Post by pablo.s on 2009-07-03
> **juancarlospaco said:**
> [B]./configure
make
sudo checkinstall[/B]

Aha. Y las dependencias?

---

### Post by kornykyano on 2009-07-04
YA! está

Lo encontre en [http://repository.maemo.org/extras-devel/pool/diablo/free/j/json-glib/](http://repository.maemo.org/extras-devel/pool/diablo/free/j/json-glib/) , era para instalar el plugin de facebook para Pidgin. No se si es confiable la fuente [-o<, pero hasta ahora funciona de 10 :)

PD: espero que no me genera algún conflicto con otra cosa, aunque HH se la re-banca

PD: compliar ni idea, debería tomar algún cursito :-\"

Saludos

---

### Post by juancarlospaco on 2009-07-05
> **pablo.s said:**
> Aha. Y las dependencias?

**sudo apt-get build-dep NombrePaquete && sudo apt-get check NombrePaquete**

:p

---

### Post by GGsalas on 2009-09-14
> **kornykyano said:**
> YA! está

Lo encontre en [http://repository.maemo.org/extras-devel/pool/diablo/free/j/json-glib/](http://repository.maemo.org/extras-devel/pool/diablo/free/j/json-glib/) , era para instalar el plugin de facebook para Pidgin. 

Acabo de instalarlo. Parece que la version que descargue (1.61) es para Karmic y yo uso Jaunty.

Lo que hice fue instalar el .deb:

```
sudo dpkg -i pidgin-facebookchat-1.61.deb
```

Luego da error. Entonces instalo la dependencia:

```
sudo aptitude install libjson-glib-1.0-0
```

Da error porque pide una version más reciente, propone solucionarlo desinstalando el plugin para pidgin

Le digo que no y encuentra una segunda solucion que es instalar una version del plugin para pidgin más vieja...

Acepto y lo instala :D

No se como hizo aptitude para instalar una version más vieja ¿estara en repositorios este plugin?

Saludos

libjson-glib-1.0-0

---

### Post by GGsalas on 2009-09-14
La manerq que expliqué no me permitia conectarme. Logré solucionarlo instalando el ejecutable que bajé y la dependencia que bajé de acá: [http://mirrors.kernel.org/ubuntu/pool/main/j/json-glib/](http://mirrors.kernel.org/ubuntu/pool/main/j/json-glib/)

Saludos

---

