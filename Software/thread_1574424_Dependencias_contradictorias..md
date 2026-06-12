---
title: "Dependencias contradictorias."
date: 2010-09-14
forum: Software
---

### Post by Cacique1 on 2010-09-14
Hola. Hace poco instale Ubuntu 10.04 y le he agregado varios programas. Sin embargo, cuando quise instalar Opendict me salio un mensaje diciendo que faltaba la dependencia *python-wkgtk2.6*. La descargué y cuando quise instalarla salió un mensaje diciendo que faltaba la dependencia *python-wxversion*. También la descargué y cuando quise instalarla me salió un mensaje diciendo que faltaba la dependencia *python-wkgtk2.6*. 
  O sea que un paquete es dependencia del otro, por lo tanto no puedo instalar ninguno de los dos paquetes. Y hasta que no los instale no puedo instalar Opendict. ¿Alguien sabe como se puede arreglar este lío de dependencias?.
  Desde ya, agradezco cualquier respuesta.

---

### Post by juancarlospaco on 2010-09-14
Aplicaciones--->Accesorios--->Terminal, copia, pega y dale Enter:

**sudo apt-get update ; sudo apt-get install opendict**

O

[Click aca.]("apt:/opendict?refresh=yes")

---

### Post by Cacique1 on 2010-09-20
Muchas gracias por tu respuesta. El problema es que me olvidé de aclarar que mi PC no posee conexión a Internet. Todos los paquetes que descargo lo hago desde un Ciber a mi pendrive. ¿Hay alguna manera de instalarlo de forma offline?.

---

### Post by juancarlospaco on 2010-09-20
el proyecto [Keryx]("http://keryxproject.org/wiki/index.php?title=Tutorial_de_Keryx_(espa%C3%B1ol)")...

---

