---
title: "Problema fecha y Hora cambiante"
date: 2009-10-26
forum: Software
---

### Post by fachamix on 2009-10-26
**Español**
Tengo un problema, estoy casi seguro que es algo simple pero como soy nuevo en linux no logro saber como solucionarlo
Tengo un servidor con Ubuntu Desktop 9.04, qu trabaja pura y exclusivamente como servidor de archivos
Nadie usa esta computadora de manera loca, solamente funciona como servidor remoto de archivos.
 
Cuando lo instale por primera vez, tuve que cambiar la fecha y hora del sistema ... como corresponde.
A veces tengo la necsidad de reiniciar el servidor, cuando esto sucede, la fecha y hora (especialmente la hora), cambian !!!!
Estoy segur que algo sucede cuando Ubuntu esta arrancando, el cable de red esta SIEMPRE CONECTADO. Creo que se sincroniza por internet o algo, y modifica la hora. 
 
Quiero que esto deje de suceder, quiero que no busque la fecha y hora AFUERA, que quede con la configuracion manual
 
alguna sugerencia ?
Muchas Gracias
 
**English:**
I have a problem, I presume its something really simple but I am new in linux.
 
I have a server with Ubuntu 9.04, it works as a File Share Server.
Nobody uses it ( I mean , with mouse, and keyboard .... locally), Its just a File Server.
 
So I change the date and time manually, and I leave it on my Server Room
 
Sometimes I have ti Restart the server, and every time I do that, the date and Time is modify.
 
I am pretty sure that something happends when UBUNTU is booting up the OS, and my network cable is ALWAYS pluging up, so something is going on during boot time on my network that modifyies my datetime settings.
 
 
any suggestions ?
 
thanks a lot

---

### Post by Fak89 on 2009-10-26
> **fachamix said:**
> **Español**
Tengo un problema, estoy casi seguro que es algo simple pero como soy nuevo en linux no logro saber como solucionarlo
Tengo un servidor con Ubuntu Desktop 9.04, qu trabaja pura y exclusivamente como servidor de archivos
Nadie usa esta computadora de manera loca, solamente funciona como servidor remoto de archivos.
 
Cuando lo instale por primera vez, tuve que cambiar la fecha y hora del sistema ... como corresponde.
A veces tengo la necsidad de reiniciar el servidor, cuando esto sucede, la fecha y hora (especialmente la hora), cambian !!!!
Estoy segur que algo sucede cuando Ubuntu esta arrancando, el cable de red esta SIEMPRE CONECTADO. Creo que se sincroniza por internet o algo, y modifica la hora. 
 
Quiero que esto deje de suceder, quiero que no busque la fecha y hora AFUERA, que quede con la configuracion manual
 
alguna sugerencia ?
Muchas Gracias
 

Puede ser que este mal configurado el área y cuando sincroniza en internet te cambie la hora y te ponga la de un lugar que no es.
Si no es eso, fijate si la bios te marca bien la hora. Si no marca bien, arreglala.. Y si se vuelve a desconfigurar, cambiale la pila al mother.

Es lo unico que se me ocurre por ahora, fijate y contanos que pasa.
Saludos!

Pd. Esto iva a software :)

---

### Post by guillermolisi on 2009-10-26
Todo esto siempre y cuando no tengas problemas en la pila de la motherboard y que a raiz de que esta desgastada tengas ese problema de la hora como sintoma cada vez que la encedes.

Tenes escritorio grafico en ese server o solo consola ?

---

### Post by anarko on 2009-10-26
Yo me tiraria por el tema del uso horario y que este mal configurado el tzdata ya que si la pila del bios esta agotada, no se pierde la hora con un reinicio solamente, solo se pierde con un apagado completo del equipo.
Proba hacer un reconfigure del tzdata.
```
anarko@AnArKa:~$ sudo dpkg-reconfigure tzdata

Current default timezone: 'America/Argentina/Buenos_Aires'
Local time is now:      Mon Oct 26 23:27:26 ART 2009.
Universal Time is now:  Tue Oct 27 02:27:26 UTC 2009.
```

Cuando hacer el dpkg-reconfigure te pregunta continente, pais y ciudad para configurar el uso horario correcto. 
Tambien esta el problema de que este años K no nos cambio la hora, y no se si ubuntu saco un patch para el tzdata, yo use uno de debian que largaron en la facultad de ingenieria de la UBA.

---

### Post by ALEXEX on 2009-10-27
Como comentan anteriomente es un problema con la pila que esta en la motherboard, dices que al reiniciar te cambia la hora y la fecha, pero si es muy comun que al estar ya desgastada la pila suceda que te cambie la hora.
Dudo que sea problema de sincronizacion.

---

### Post by fachamix on 2009-10-27
MIL GRACIAS POR CONTESTAR!!!!!!!!!
 
la pila anda perfecto, mi zona horaria esta bien configurada.
 
lo que sucede , y esto ya lo se, es que cuando reinicia toma la hora de mi zona horaria , en ves de la hora de la BIOS.
 
vivo en argentina, y a mis benditos gobernantes se les antoja atrazar (o adelantar no me acuerdo bien ) 1 hora del reloj para "ahorrar energia en verano"
 
cuando reinicio la pc con el cable de red puesto, busca mi zona horaria y me pone la HORA VERDADERA, no la hora pactada para el pais.
 
por eso queria saber si puedo desactivar esta funcion, que deje de buscar por internet la hora, y se base en la hora de la BIOS solamente.

---

### Post by anarko on 2009-10-28
Muchachos desmitifiquemos un poco, la hora se pierde solamente si se le corta la energia TOTALMETE al mother, ya sea por un apagado total o por desenchufarla de la pared cuando la pila esta defectuosa o agotada. Con la pila agotada podes apretar el boton reset o mandar a reiniciar por soft las veces que quieran que la hora y la conf. del BIOS se mantiene.

Fachamix : Si no queres que te cambie la hora en base al horario de verano instala el siguiente paquete 

[http://www.marga.com.ar/~marga/debian/tzdata/tzdata_2009g-0etch1.1_all.deb](http://www.marga.com.ar/~marga/debian/tzdata/tzdata_2009g-0etch1.1_all.deb)

Que tiene la correccion del tzdata para el horario nuevo de argentina ( sin cambios porque el ahorro de energia no fue el esperado ), es para debian, pero yo lo probe en Ubuntu 8.04 y 9.04 anda de 10. 
El link proviene del grupo de usuarios de linux de la facultad de ingenieria de la UBA.

---

### Post by leosr on 2009-10-28
Hola. Yo lo arreglé sacando la actualización automática.
Creo que ya hay un parche en los repos.

Saludos.

---

### Post by fachamix on 2009-10-28
gracias a todos por las respuestas.
 
[[SIZE=5][COLOR=#000000]anarko[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=571810")  , exelente el patch, solucione el problema de la hora "erronea" con el paquete que has propuetso, y tambien probe un paquete que se encuentra en las actualizaciones de ubuntu, con un nombre parecido , pero es el tzdata.
 
 
de todas maneras, creo, que aunque ya solucione el problema, la pregunta sigue en pie.
 
Como hacer para que Ubuntu siempre tome la hora de la BIOS , y no de mi zona horaria sin desconectar de la red. 
Es decir, si yo reinicio mi PC sin el cable de red puesto, ... MANTIENE LA HORA DE LA BIOS, pero reinicio con el cable de red puesto ..... toma de la zona horaria !!!!
 
 
saludos ...
 
(debe ser un proceso , un demonio, algo es , pero , yo no se )

---

### Post by mama21mama on 2009-10-28
En terminal
> apt-cache show tzdata


Description: time zone and daylight-saving time data
 This package contains data required for the implementation of
 standard local time for many representative locations around the
 globe. It is updated periodically to reflect changes made by
 political bodies to time zone boundaries, UTC offsets, and
 daylight-saving rules.

Traducion:	
zona horaria y el horario de verano de datos
  Este paquete contiene los datos necesarios para la aplicación de la
  hora local estándar para muchos lugares representativos de todo el
  mundo. Se actualiza periódicamente para reflejar los cambios realizados por
  los órganos políticos al tiempo límites de la zona, la compensación de UTC, y la
  horario de verano normas.

Como que si removes el **tzdata** la hora del ubuntu la tomara del bios.

---

### Post by anarko on 2009-10-28
a pero yo 6 años usando debian y me desayono ahora que el apt tiene una descripcion extendida, si sere bestia :)

---

### Post by fachamix on 2009-10-29
no lo habia pensado asi, soy nuevo en ubuntu.


voy a probar !!!!!!!


saludos


pruebo y cuento despues

---

