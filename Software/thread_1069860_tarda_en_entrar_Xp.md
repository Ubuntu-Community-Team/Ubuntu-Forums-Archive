---
title: "tarda en entrar Xp"
date: 2009-02-14
forum: Software
---

### Post by lucasfava on 2009-02-14
El problema es el siguiente, cuando quiero entrar a Xp(tengo particionado el disco), Xp reinicia un monton de veces hasta que entra, ha lo sumo tarda 10 minutos en entrar normalmente el S.O.
Supongo que puede ser que halla algún problema con el Grub de ubuntu.:confused:

Necesito ayuda para solucionar estó, sino me matan en casa :(

---

### Post by Hei Ku on 2009-02-14
Tambien podria ser que haya un problema con el XP. Es raro, nunca pasa, pero es una posibilidad. ;)

---

### Post by lucasfava on 2009-02-14
alguna sugerencia, pa solucionar el problema :confused:

---

### Post by Hei Ku on 2009-02-15
Reinstala el XP. Pasado el Grub, linux no tiene nada que ver. 
Si no levanta o tarda, ya es problema del XP.

---

### Post by c4d0rn4 on 2009-02-15
Sin ir a eso, reinstalar win, por ahí fijate con: [supergrub]("http://www.supergrubdisk.org/") o [hirens boot cd]("http://www.hiren.info/pages/bootcd").
También tengo entendido que si pones el cd de xp antes de que inicie te da la opción de reparar.

Con lo primero tendras la opción de bootear de otra manera xp. Igual es medio =S que sea el grub.

Con lo de reparar por ahí termina salvadonte las papas del horno. (antes hacer BACKUPS!!)


Y como última opción, si querés "reparar" el mbr de windows (lease mandar el grub a volar y que arranque windows de una como de fabrica); [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm) es una aplicación de win, lee bien lo que haces se baja de aca [http://www.sysint.no/Download/tabid/162/language/en-US/Default.aspx](http://www.sysint.no/Download/tabid/162/language/en-US/Default.aspx)

---

### Post by biale on 2009-02-15
Hay un procedimiento mas o menos standard para estos casos, que paso a detallar.

Los primero es serenarse, y en tu caso serenar a tus padres. "Todo lo que puede romperse se rompe". Y dudo que el grub tenga algo que ver, lo único que en principio hace es pasar control al arrancador de WXP y en tu caso WXP todavía arranca.

Pegale un vistazo a todas las temperaturas y voltajes de la PC. La mano contra el ventilador de fuente, lo que indique el bios, etc.

Arrancando con el CD de WXP urgente un "chkdsk C: /p /r" para despejar problemas en NTFS. No tan bueno como lo anterior, pero correr on-line un scandisk a "todo el disco" también puede servir. Anotate todo lo aparezca raro, el scandisk genera un suceso "winlogon" en el visor de eventos. ¡No defragmentar el disco!

Ademas mirar todos los rojos y amarillos en el visor de eventos de WXP.

Refrescar y correr el antivirus "a todo" el disco C. 

Usando el utilitario de Windows, backup de todo lo que consideres util y se encuentre en el disco "C".

En caso de duda, la última palabra en lo que refiere al disco rígido siempre la tienen los utilitarios de bajo nivel provistos por el fabricante del disco. Acordate que solo podes correr sin problemas los tests que NO destruyan los contenidos del disco, es decir los test "no destructivos".

Ahora vas a tener que decidir entre reparar a windows con el CD del MS o formatear y bajar backup, etc.

Saludos.

---

### Post by sajnox on 2009-02-15
Si XP Arranca, es decir ves la pantallita de XP cargando y asi como si nada se reinicia es muy dificil que haya sido algo provocado por Ubuntu (pero anda explicaselo a tus viejos, en mi casa es con mi mujer...y creeme que es peor)

Para dejar a todos tranquilos con el supergrubdisk podes reparar la mbr para hacer que Ubuntu no este ahi y ver que pasa. 

Y decile a tus viejos que agradezcan que tienen Ubuntu instalado, por que si lo que tienen es un virus con ubuntu te va a ser mucho mas facil rescatar archivos y reinstalar.

---

### Post by c4d0rn4 on 2009-02-15
> **sajnox said:**
> Si XP Arranca, es decir ves la pantallita de XP cargando y asi como si nada se reinicia es muy dificil que haya sido algo provocado por Ubuntu (pero anda explicaselo a tus viejos, en mi casa es con mi mujer...y creeme que es peor)

Yo lo hice sencillo, le arreglé la pc (según: rota en mis *experimentos*). Una vez andando les pregunté si andaba bien; dijeron que sí; y les contesté: buenisimo, porque yo no pienso tocar más esa P_ta Pc, arreglenselas.

Puedo decir que el resultado es satisfactorio, pero obvio eso se puede hacer si hay más de una pc.

(y lo mejor es después; cuando vienen con la cabeza gacha sabiendo que se daño por su culpa, y te piden con cariño que se las arregles JA-JA-JÁ!!)

---

### Post by lucasfava on 2009-03-12
Hace rato que no pasaba, voy a verificar como reparar el asunto ;).
Comento que reinstale el xp y al momento aparecio un problema con el archivo n....dll no me acuesdo el nombre ahora, intente reparar el archivo, pero todo sigue igual, se reinicia el xp. 

Otro tema, quise ver que pasaba si desinstalaba ubuntu desde windows y encuentro que el archivo de desinstalacion de ubuntu no responde, queria instalar la version server del 8.10 que me mandaron. Paso extremo seria formatear la particion de ubuntu, desde el bios, para poder hacer la nueva instalación.
O la extrema unsion (lease formateo totalmente el disco) a los dos S.O, y reinstalo denuevo

---

### Post by lucasfava on 2009-03-12
una idea que puede ser, que sea el disco rigido que tenga alguna zona desmagnetisada.

---

