---
title: "instalacion de tipos de letras"
date: 2010-09-25
forum: Software
---

### Post by andrestester on 2010-09-25
hola que tal.

hay alguna menera de instalar tipos de letras de windos en ubuntu.

saludos...

---

### Post by bichopro on 2010-09-25
Prueba primero instalando ttf-mscorefonts-installer y microsoft core fonts estos paquetes instalan varias.

---

### Post by 3nG3ndR0 on 2010-09-25
> **andrestester said:**
> hola que tal.

hay alguna menera de instalar tipos de letras de windos en ubuntu.

saludos...

* Andale Mono
* Arial Black
* Arial (Bold, Italic, Bold Italic)
* Comic Sans MS (Bold)
* Courier New (Bold, Italic, Bold Italic)
* Georgia (Bold, Italic, Bold Italic)
* Impact
* Times New Roman (Bold, Italic, Bold Italic)
* Trebuchet (Bold, Italic, Bold Italic)
* Verdana (Bold, Italic, Bold Italic)
* Webdings

Ejecutamos:

```
$ sudo apt-get install msttcorefonts
```

y despues

```
$ sudo fc-cache
```

para reiniciar la cache de fuentes del sistema.

---

### Post by andrestester on 2010-09-26
gracias por responder

pero si tengo los tipos de letras en un cd. como los pasaria directo a ubuntu


salu2.

---

### Post by themasterdark on 2010-09-26
Es facil solo debes copiarlas al directorio

/usr/share/fonts/truetype

Saludos =)

---

### Post by andrestester on 2010-09-26
gracias por responder 

instalando fuentes .


salu2.

---

### Post by moreback on 2010-09-26
También sirve copiarlas a tu directorio /home/usuario/.fonts

---

### Post by themasterdark on 2010-09-27
aa verdad,y en ese caso no necesitas permisos de root para instalarlas, claro que si tienes mas de un usuario solo el que instalo las fuentes podra tenerlas en los programas que use.

Saludos =)

---

