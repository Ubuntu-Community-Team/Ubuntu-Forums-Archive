---
title: "Problema con wine"
date: 2008-07-09
forum: Software
---

### Post by nicolab10 on 2008-07-09
Mi problema es el siguiente, hace un poco mas de un mes que estoy utilizando ubuntu y me dio ganas de instalar un juego, busque y econtre que la solucion era Wine, el tema es que ya probe con varios juegos y el problema con el que me encuentro ahora es que los juegos se ejecutan pero al ratito se cierran. Estoy utilizando ubuntu Hardy Heron y Wine 1.10 y tambien probe con la version 0.9 pero hace el mismo error.

Saludos y espero soluciones.

---

### Post by SLA_leandrin on 2008-07-09
HOLA.

Primero que nada, decinos que juegos instalaste, y que errores te tira.

Para eso ejecutalos en la consola, con el comando;

```
wine "nombre del archivo.exe"
```

En el directorio que esté instalado.

Posteá los errores aquí y te ayudamos.

---

### Post by nicolab10 on 2008-07-10
wine: could not load L"C:\\windows\\system32\\gta.exe": Module not found

Me aparece este error, ni idea que es pero no creo que tenga que ver con mi problema anterior, debe ser que estoy haciendo algo mal.

---

### Post by juanman on 2008-07-12
Cada juego es un mundo con wine.
Para ese error q te salta parece q tenes q copiar el archivo gta.exe (debe estar en Archivos de Programa/Rockstar Games/GTA algo) a C:\\windows\\system32\\
El C: q simula wine esta ubicado en ~/.wine/drive_c/ (~ es tu home)

Siempre para estos juegos complejos, buscá un tutorial o howto q te diga q hay q hacer para q funcione (si funciona). La [appdb de wine]("http://appdb.winehq.com") es la biblia para esto.
Ahí buscas el programa de windows y te dice la compatibilidad q tiene, y suelen venir howtos (en ingles) para hacerlo funcionar. Por ej, [este]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780") es el de GTA San Andreas. Parece q funciona bien excepto los videos y el joystick.
Tambien hay algunos programas q ayudan en estos casos, como [winedoors]("http://www.winedoors.org") o [PlayOnLinux]("http://www.playonlinux.com"), q traen una lista de soft para instalar y configurar facilmente, al estilo windows... PlayOnLinux trae los GTA...

Saludos

---

