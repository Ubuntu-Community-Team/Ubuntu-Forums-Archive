---
title: "SPSS. No me funciona y no puedo desinstalarlo"
date: 2008-10-29
forum: Software
---

### Post by chulelinux on 2008-10-29
Hola, instale el spss para linux en hardy, no lo registre bien al principio por lo que quise desisntalarlo... y no puedo. Alguien sabe como hacerlo? Me tira el siguiente error cuando lo desistalo ejecutando el archivo uninstall en terminal: 

Errors occurred during the uninstallation.
An error occurred and product uninstallation failed. Look at the log file /opt/SPSSInc/SPSS16/log.txt for details.
An error occurred and product uninstallation failed. Look at the log file /opt/SPSSInc/SPSS16/log.txt for details.

The following warnings were generated:
Could not delete file /opt/SPSSInc/SPSS16/bin/Looks/Academic.stt
Could not delete file /opt/SPS..... (y una lista muy larga de esto...)

Y en log.txt me aparece esto:

(Oct 27, 2008 11:15:06 AM), Install, com.installshield.database.designtime.ISFrameDef, wrn, could not open resource for 1_background_en.gif
(Oct 28, 2008 12:20:11 PM), Uninstall, com.installshield.database.designtime.ISFrameDef, wrn, could not open resource for 1_background_en.gif
(Oct 29, 2008 9:26:49 AM), Install, com.installshield.database.designtime.ISFrameDef, wrn, could not open resource for 1_background_en.gif

Si alguien me puede ayudar agradecido ya que es uno de los pocos programas por los que todavía guardo una ventana en un lugarcito de mi pc...

Saludos

---

### Post by sebastianabate on 2008-10-29
El problema evidentemente es que está tratando de borrar un archivo que al instalarlo no lo pudo copiar. Fijate que la primer línea del 27/10 dice "Install" y falló al crear ese archivo, en la segunda del 28/10 falla al tratar de borrarlo, y en la tercera del 29/10 parece que trataste de instalarlo de vuelta y falló nuevamente.

La pregunta es, ¿por qué no borrás directamente el directorio /opt/SPSSInc? Generalmente los programas que se instalan en /opt no tocan ninguna otra configuración, salvo linkear algunos binarios a /usr/bin y crear las entradas del menú, pero esas cosas también las podés borrar sin problemas.

---

### Post by marianom on 2008-10-29
2 cosas 2:
 1- en /opt tu usuario no tiene permisos por defecto (en gral) salvo que hayas creado la carpeta y te hayas dado los permisos. Si la creaste/instalaste con sudo, el dueño es root y no te va a dejar borrar salvo que lo hagas con sudo. No decís nada al respecto así que es dificil saberlo desde aca.
 2- ¿sabés que en linux tenes [pspp]("http://www.gnu.org/software/pspp/")?

---

### Post by faktorqm on 2008-10-30
La instalacion la hizo con wine me parece, por que en un momento del log dice install shield. De ultima fijate de borrar algun directorio relacionado en ~/.wine/ Salu2!

---

### Post by chulelinux on 2008-10-30
Disculpen el silencio, volví a la red ... La instalación la hice arrastrando el archivo setup bin a la terminal, no lo instalé con wine, gracias Faktorqm. Igualmente si mal no recuerdo aparece la ventana de install shield...
También traté de desinstalarlo entrando como root...y como bien señala sebastian lo instale de nuevo y supuestamente todo bien pero ni andaba y ya no entraba ni hacía nada el spss. 
Que sepa o de cuenta el programa no sumo nada ni creo entradas de menú... No sabía que podía borrar directamente la carpeta sin mayores conflictos... intentaré eso y trataré de instalarlo de nuevo a ver que ocurre... 
Marianon, el pspp no lo probé pero vamos a hacerlo, es que más allá del uso individual este programa es una de las excusas para no usar linux en el instituto donde trabajo por ello también quiero usarlo para desdibujar la resistencia al mismo....

---

### Post by sebastianabate on 2008-10-30
Otra recomendación, fijate en tu home si no te creó una carpeta tipo /home/tu-usuario/.spss (no estoy seguro si este programa lo hace, pero la mayoría sí), porque si lo registraste mal seguramente la información del registro quedó guardada allí, y si lo volvés a instalar te va a levantar esa configuración.

---

### Post by chulelinux on 2008-11-01
Al final no lo desinstalé Sebastian porque pasé al intrepid y formateé todo... Cuando lo instale nuevamente comento como fue...
Saludos

---

