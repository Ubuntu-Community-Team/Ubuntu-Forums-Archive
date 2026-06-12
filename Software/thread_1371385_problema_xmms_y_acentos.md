---
title: "problema xmms y acentos"
date: 2010-01-03
forum: Software
---

### Post by radixs on 2010-01-03
Hola a todos, la verdad que hace bastante tiempo que no pasaba por estos lados :D.

Bueno les comento encontré un repositorios para instalar xmms en ubuntu 9.10. Solo tengo un pequeño detalle con xmms, este no reconoce los acentos, ojo no el de los temas (mp3), si no que los acentos del menu, para que me entiendan les dejo una captura.

[http://i46.tinypic.com/69hnid.png]("http://i46.tinypic.com/69hnid.png")

PD: no tengo problemas con los acentos del sistema.

---

### Post by CdK1 on 2010-01-03
Setea la variable de entorno relacionada con el idioma LANG_ALL, LANGUAGE etc y correlo desde la terminal...

También haz:

sudo dpkg-reconfigure locales 
marcas la opcion es_ES.iso-8859-15 

También puedes retocar /etc/environment
nano /etc/environment y le añades:

LC_ALL=es_ES@euro
LANG=”es_ES.UTF-8&#8243;
LANGUAGE=”es_ES:es:en_GB:en”
LC_TYPE=es_ES@euro

---

### Post by bichopro on 2010-01-03
Te recomiendo que pruebes audacious, es igual al winamp 2.9, con muchos plugins y esta en desarrollo no como xmms que esta bastante abandonado.

---

### Post by radixs on 2010-01-03
> **bichopro said:**
> Te recomiendo que pruebes audacious, es igual al winamp 2.9, con muchos plugins y esta en desarrollo no como xmms que esta bastante abandonado.

Pues déjame decirte que eh probado Audacious2 desde hace bastante tiempo a tras, la verdad encuentro que suena mucho mas despacio que propio sonido del sistema (ojo también configurando el plugins de salida alsa, haciendo lo mismo con xmms me va mucho mejor, Ademas el skins que se ve en la captura es una edición que hice yo mismo y no funciona con Audacious2. Aunque Xmms no este en desarrollo me gusta mucho mas que Audacious2.

PD: En gusto no hay nada escrito :P

---

### Post by moreback on 2010-01-04
No me acuerdo como era soporte de UTF-8 en las bibliotecas GKT+ 1.2, pero parce que había algunos problemillas, por eso es mejor usar las aplicaciones más modernas basadas en GTK+ 2.0.

Ahora yo creo que que tendrías que retocar tus locales como dice CdK1, pero dejando todo con UTF-8, ya que los catálogos de idiomas deben venir todos en UTF-8.

Saludos.

---

### Post by radixs on 2010-01-05
La configuraciones las probé y adivinen cuec, no funciono ninguna, entube viendo con cdk1 el tema y pues no funciono nada de lo que vivimos.

Ahora si logro encontrar la solución obviamente la pondré aqui ;)

---

