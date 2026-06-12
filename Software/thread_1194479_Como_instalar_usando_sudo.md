---
title: "Como instalar usando sudo?"
date: 2009-06-22
forum: Software
---

### Post by ParamDaya on 2009-06-22
[FONT=Georgia][SIZE=2][B]Estimados

Alguien por favor me podria ensennar a instalar programas utilizando el sudo para asi instalar teniendo todos los permisos?

Estoy instalando un software que me pide crear una carpeta, pero no me deja porque no tengo los permisos, entonces pense en hacerlo con sudo, pero no se como instalar programas usando sudo.

El programa no es de la lista de Aplicaciones de Ubuntu. El programa es de un tercero.

Muchas gracias....[/B][/SIZE][/FONT]

---

### Post by CdK1 on 2009-06-22
Lo único que tienes que hacer es anteponer "sudo" a los comandos, ejemplo:

sudo apt-get install emesene
sudo make && sudo make install

Etc....

---

### Post by ParamDaya on 2009-06-22
> **CdK1 said:**
> Lo único que tienes que hacer es anteponer "sudo" a los comandos, ejemplo:

sudo apt-get install emesene
sudo make && sudo make install

Etc....

[FONT=Georgia][SIZE=2][B]Gracias pero probe con apt-get y no me funciono, me dice que no encuentra el paquete. Acaso debo dar la direccion exacta de donde se encuentra el archivo? El instalar es un .bin, afecta en algo eso?

Respecto de la otra opcion que pusiste, no tengo idea que hace, soy nuevo en Ubuntu y Linux, asi que me dejaste igual..... 

Gracias por la informacion, pero me gustaria que fuera mas detallada y explicada.[/B][/SIZE][/FONT]

---

### Post by CdK1 on 2009-06-22
sudo sh archivo.bin

---

### Post by radixs on 2009-06-22
> **ParamDaya said:**
> [FONT=Georgia][SIZE=2][B]
Gracias por la informacion, pero me gustaria que fuera mas detallada y explicada.[/B][/SIZE][/FONT]

Para eso se creo la documentacion de ubuntu un poco de lectura o google siempre es bueno para aprender

---

### Post by moreback on 2009-06-22
> **ParamDaya said:**
> [FONT=Georgia][SIZE=2][B]Gracias pero probe con apt-get y no me funciono, me dice que no encuentra el paquete. Acaso debo dar la direccion exacta de donde se encuentra el archivo? El instalar es un .bin, afecta en algo eso?

Respecto de la otra opcion que pusiste, no tengo idea que hace, soy nuevo en Ubuntu y Linux, asi que me dejaste igual..... 

Gracias por la informacion, pero me gustaria que fuera mas detallada y explicada.[/B][/SIZE][/FONT]
Generalmente cuando bajas algo, como que trae un archivo README o un INSTALL, el cual tiene bastante información acerca de qué bajaste y cómo lo puedes instalar.

Saludos.

PD: no le tengas miedo a leer.

---

### Post by Carlos C on 2009-06-23
> **ParamDaya said:**
> [FONT=Georgia][SIZE=2][B]Gracias pero probe con apt-get y no me funciono, me dice que no encuentra el paquete. Acaso debo dar la direccion exacta de donde se encuentra el archivo? El instalar es un .bin, afecta en algo eso?

Respecto de la otra opcion que pusiste, no tengo idea que hace, soy nuevo en Ubuntu y Linux, asi que me dejaste igual..... 

Gracias por la informacion, pero me gustaria que fuera mas detallada y explicada.[/B][/SIZE][/FONT]

Parece que tienes varias confusiones. Si vas a instalar un paquete de un tercero y deseas permisos de administrador hay varias formas de hacerlo. Lo que te sugiero es que aprendas para qué sirve sudo y cómo se usa:

[http://www.guia-ubuntu.org/index.php?title=Sudo](http://www.guia-ubuntu.org/index.php?title=Sudo)

Luego deberías aprender a instalar programas:

[http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones](http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones)

Por último quiero señalarte que pedirle a la gente que colabora en el foro información más detallada sin haber hecho el esfuerzo de investigar primero me parece un poco cómodo de tu parte. Recuerda que quienes responden en el foro lo hacen sólo por el agrado de ayudar, no están obligados a hacerlo.
Saludos.

---

