---
title: "no puedo instalar windows teniendo ubuntu"
date: 2009-05-30
forum: Software
---

### Post by naranjosk8 on 2009-05-30
buenas.
les cuento, resultake instale ubuntu 9.04en mi recien comprado notebook toshiba borrando disco duro y todo osealo deje solamente con ubuntu. el cual me corria perfectamente hasta ke tube un error cuatiko e intente instalar todo denuevo.
esta vez keria windows y ubuntu por los distintas dificultades ke tenia al tener solo ubuntu.
bueno lo ke paso es ke intente instalar windows y no me lo peska. me tira un error al instalar xp o vista y desde los cds originales. ahora solo puedo instalar ubuntu.

mi pregunta es si ustedes saben si desde ubuntu yo pudiera solucionar este problema.

los problemas ke me arroja al intentar instalar windows son estos.

en xp: 0X0000007b (0XF7A8A524,0xC0000034,0X00000000,0X00000000)

y en vista: 0X800703EE

estos errores son al bootear los cds.

por fa he buscado y no he encontrado nada.

desde ya gracias.

---

### Post by AlvaroV on 2009-05-30
Deberías considerar dos cosas antes de pedir lo que estas pidiendo:

1.- Este es un Foro para soporte de Ubuntu Linux, no de Windows.

2.- Si la versión de Window que traía originalmente tu PC era legal, deberías poder pedir soporte a Microsoft.

Te propongo que señales porque necesitas tener instalado Windows junto a Ubuntu y cual han sido los errores de Ubuntu para ver si te podemos ayudar.

saludos

---

### Post by Carlos C on 2009-05-30
naranjosk8, lamentablemente no podemos ayudarte con los errores de xp, tendrás que buscar ayuda en otro lugar, como ya se te respondió.

Por favor, evita escribir con "k" y preocupate de hacerlo de la manera más neutra posible, en este foro entran personas de diferentes países, muchos de los cuales no tienen el castellano como idioma nativo. Te sugiero que mires [**acá**]("http://ubuntuforums.org/showthread.php?t=1162750") antes de publicar nuevamente en el foro.

Saludos!

---

### Post by mocoloco on 2009-05-30
Una posible solución, usando un disco de Ubuntu (o cualquiere LiveCD) creale una partición a Windows primero, de tipo NTFS. Tal vez así le guste.

---

### Post by guillermolisi on 2009-06-01
EL procedimiento correcto para contar con ambos sistemas operativos funcionales es primero instalar Windows y despues Ubuntu.

Esto es asi porque el Boot Manager de Windows no se fija en el contenido del Grub que genera Ubuntu y lo pisa regrabando informacion nueva referida solamente a WinXP dejando sin posibilidades de inicio a Ubuntu.

Por otra parte, deberias dejar algo de espacio en el disco rigido para instalar cada uno. Posiblemente el problema que estas experimentando con XP es que no encuentra una particion con espacio libre, sin formatear o con formato reconocible por Windows, para hacer la instalacion.

PS: El asunto de escribir adecuadamente permite que cualquier persona que inicie una consulta en el foro encuentre lo que busca a partir de una o varias palabras bien escritas. Si algun mensaje hace referencia al tema buscado pero con la palabra requerida mal escrita, no obtendra resultado y se perdera parte de la potencia de las herramientas de UbuntuForums (y el que busca se quedara con la duda).

---

