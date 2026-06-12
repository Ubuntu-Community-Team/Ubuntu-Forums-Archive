---
title: "Problemas con Brasero"
date: 2009-12-05
forum: Software
---

### Post by ramiro_md on 2009-12-05
Buenas tardes ente, resulta que le hurté a mi hermano su grabadora de dvd y la conecté en mi pc. Ubuntu la reconoció de toque sin más problemas.
EL tema es que cuando quize grabar un dvd de video, abro Brasero busco la opción "dvd de datos" e inserto las carpetas "audio_ts" y "video_ts" en el proyecto.
El dvd se comienza a grabar, pero cuando está finalizando la grabación Brasero tira un error, acá dejo el log del error:
> BraseroGrowisofs Finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Preparing to checksum (type 4 .checksum.md5) (brasero_burn_record_session brasero-burn.c:2364)
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Found file 0x8c04fc8
BraseroChecksumFiles Cannot open checksum file
BraseroChecksumFiles Ended with an error
BraseroChecksumFiles called brasero_job_error
BraseroChecksumFiles finished with an error
BraseroChecksumFiles asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroChecksumFiles stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

Además también probé con k3b pero me tiraba un error como que no tenia permisos para usar la unidad o algo así.

EStoy desesperado por grabar ese dvd de mierrrr, espero que alguien me pueda dar una mano.
Desde ya muchas gracias.

---

### Post by Mauro22 on 2009-12-05
Hola!!


Probá:


1) Menos velocidad

2) Tildá "Simular grabación"



Por lo que entiendo es que arrastraste dos carpetas y de diste grabar, no?

Que error preciso te da K3b ??

---

### Post by ramiro_md on 2009-12-05
Mauro gracias por la respuesta, estuve grabando en 8x voy a probar en la mínima. Pasa que me voy a conseguir algún regrabable porque ya tire 3 dvds :S. No recuerdo que me decia bien k3b pero cuando tenga el dvd regrabable pruebo de nuevo.

---

### Post by ramiro_md on 2009-12-05
Problema resuelto gente, se ve que era algo aleatorio porque grabé un par de cds de música y un dvd regrabable y salió andando todo.
Bueno, un saludo !

---

