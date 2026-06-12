---
title: "[SOLVED] Error al compilar en Ubuntu jaunty"
date: 2009-08-20
forum: Software
---

### Post by astalavista2000 on 2009-08-20
Hi! I have installed Ubuntu 9.04 on a 4G eee Asus Netbook. In fact, I hace installed it on a micro SD card. Everything works just fine, but I have an issue with compiling apps from source code. I installed the build-essential package, downloaded the source code of an application and when I run the configure script something goes wrong. I' have attached a notepad file with the console output. Hope you can help me. Thanks!

******************************************

<<EDITADO>>
Hola! Instalé Ubuntu 9.04 en una netbook Asus eee 4G. La instalación la hice en una memoria micro SD. Anda de maravillas, pero tengo un problema para compilar código fuente. Instalé el paquete build-essential y descargué el código del programa y cuando ejecuto el script de configuración me devuelve un error. En el archivo adjunto esta la salida que obtengo. Espero que me puedan ayudar. Saludos.

---

### Post by josecuervo86 on 2009-08-20
Hi, this is the argentine forum,  maybe you'll find more help in some english speaking forum. However, this may be help you.

```
apt-get install libncurses5-dev
```

---

### Post by astalavista2000 on 2009-08-20
> **josecuervo86 said:**
> Hi, this is the argentine forum,  maybe you'll find more help in some english speaking forum. However, this may be help you.

```
apt-get install libncurses5-dev
```

Pido perdón, es la costumbre de escribir en los foros en ingles. Transcribo el mensaje inicial al castellano. Voy a probar instalando el paquete que me indicas. Muchas gracias.

---

### Post by astalavista2000 on 2009-08-20
> **josecuervo86 said:**
> Hi, this is the argentine forum,  maybe you'll find more help in some english speaking forum. However, this may be help you.

```
apt-get install libncurses5-dev
```

Estimado josecuervo86, instale el paquete libncurses5-dev y pude compilar sin problemas. Muchas gracias por tu ayuda! Saludos

---

### Post by josecuervo86 on 2009-08-20
Saludos astalavista! Y volve cuando quieras! Suerte

---

