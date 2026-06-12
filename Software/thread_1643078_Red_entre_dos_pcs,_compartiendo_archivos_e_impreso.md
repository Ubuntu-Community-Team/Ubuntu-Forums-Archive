---
title: "Red entre dos pcs, compartiendo archivos e impresora"
date: 2010-12-11
forum: Software
---

### Post by c3959 on 2010-12-11
mi primer post despues de muchos años, usuario de linux desde pequeño =)

necesito su ayuda comunidad, me explico:
tengo en la oficina dos pcs actualmente con wxp, que trabajan en un red compartiendo archivos eh impresora...
voy a migrar a linux a esta distro. ubuntu, para lo cual estoy empezando a revisar la compatibilidad de las maquinas. lo puntual!, necesito que estos nuevos pcs con ubuntu cumplan estas fuciones de compartir tanto archivos como los documentos...

---

### Post by RafaelG on 2010-12-11
Hola C3959,

Por favor, la próxima vez que desees publicar una duda en el foro te pido que lo hagas en el subforo adecuado. Si no tienes muy clara la división que utilizamos puedes leer el siguiente post:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

También te pido que leas las normas que intentamos aplicar en el foro para que tu experiencia en el mismo sea más efectiva:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Por todo lo explicado anteriormente este Thread sera ubicado en el Sub-Foro adecuado.

Saludos cordiales,

---

### Post by RafaelG on 2010-12-11
> **c3959 said:**
> lo puntual!, necesito que estos nuevos pcs con ubuntu cumplan estas fuciones de compartir tanto archivos como los documentos...

C3959,

Creo que lo que necesitas es Samba una muy buena herramienta para administrar una red en Ubuntu. Samba trabaja muy bien entre Ubuntu y Windows si es que el dia de manana decides tener otros PC con Windows y compartir red con PC con Ubuntu.

Link Samba en Ubunto:
[http://www.guia-ubuntu.org/index.php?title=Samba](http://www.guia-ubuntu.org/index.php?title=Samba)

Hay mucho material de How To en google por lo que te recomiendo googlear y asi podras recavar mayor informacion como para despues tomar una decision.

Saludos!

---

### Post by c3959 on 2010-12-11
Rafael:

agradesco que me guiaras a leer las normas del foro, no las revise antes porque realmente no las vi y creí haber colocado el asunto en lugar correcto, pero no, y tu lo cambiaste como corresponde =)

al tema de la red, agradesco el link, ya lo habia revisado por ser info. oficial de guia respectos a samba que con lo poco revisar parece ser lo más utilizado... lo probaré durante la semana este soft. pero hoy me lleve la grata sorpresa que al tan solo probar ubuntu en los dos pcs, aparte de reconocer todo el hardware reconoció la red y la impresora, que al tenerlo conectado un pc a internet instalé su controlador y funcionaba impecable..

tengo la intención de dejar todo funcionando para el 01/01/2011, así que tengo unos 15 días aún, ante cualquier duda lo haré por este mismo canal


saludos a la comunidad!"

---

### Post by c3959 on 2011-01-04
alguien conoce una tutorial o guia bastante grafico sobre como lograr una coneccion entre dos pcs con ubuntu

---

### Post by Maciett on 2011-01-05
c3959 más que un tutorial, usa la interfaz gráfica para la configuración de samba, se llama gadmin-samba, búscalo en los repositorios. Yo con eso, y probando las opciones que trae, logré compartir la impresora y archivos desde un pc con ubuntu a uno con windows, pero sólo pude compartir la impresora luego de hacer que funcionara en ubuntu, así que hace eso primero. Si tienes alguna duda específica nos cuentas.

Saludos

---

### Post by asterix77 on 2011-01-05
Si en una red tienes equipos linux windows, lo mejor es usar samba. Ahora si tu red solo tiene linux, también puedes usar samba.

También existe NFS que se usa para compartir entre pc con solo linux. Tengo entendido que es un poco más rápido que samba. En forma personal no lo he probado.

En el siguiente link hay un tutorial de como hacerlo

[http://cayaoh.com/2010/11/02/compartir-archivos-en-linux-con-nfs/](http://cayaoh.com/2010/11/02/compartir-archivos-en-linux-con-nfs/)


Saludos

---

