---
title: "ubuntu no deja que wine haga su trabajo con algunos .exe y lanza error"
date: 2010-05-22
forum: Software
---

### Post by zhelo on 2010-05-22
Bueno resulta que tengo la version beta de wine, que viene en los repositorios, es asunto es que cuando ejecuto un .exe que obtuve de un foro (ese .exe es para jugar warcraft 3 desde su servidor), al ejecutar con wine me sale una ventana con este error

_**The file '/home/zhelo/.wine/dosdevices/c:/Archivos de programa/Warcraft III/w3l.exe' is not marked as executable. If this was downloaded or copied form an untrusted source, it may be dangerous to run. For more details, read about the executable bit**_

el asunto es que en ubuntu 9.10 no me tiraba niun error y entraba tranquilamente al juego y yo jugaba sin dramas, ahora no puedo jugar

me ayudan?
otros datos: tengo ubuntu 10.04 con wine 1.1.42

---

### Post by nechus on 2010-05-25
¿Has probado a seguir las instrucciones de ese mensaje y "mark the file as executable", o sea, "marcar el archivo como ejecutable"?  Hazle clic derecho al ícono rebelde, ve a Propiedades y marca el casillero "Permitir ejecutar el archivo como un programa". Ojalá funcione.

---

### Post by Seldaiendil on 2010-10-23
Lo de marcar el fichero como ejecutable funciona siempre que tengas permisos de escritura sobre el archivo.

Que pasa si el .exe que intentas ejecutar está en un CD?

---

