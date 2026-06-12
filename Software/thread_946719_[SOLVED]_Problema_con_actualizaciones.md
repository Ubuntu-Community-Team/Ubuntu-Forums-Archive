---
title: "[SOLVED] Problema con actualizaciones"
date: 2008-10-13
forum: Software
---

### Post by Applelnx on 2008-10-13
Alguien me podria ayudar? Cuando abro el administrador de actualizaciones me tira el siguiente error:

> 
'E:Problem parsing dependency Depends, E:Ocurrió un error mientras se procesaba btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

---

### Post by luks911 on 2008-10-13
Perdón por lo escueto, pero mirate este hilo
[http://ubuntuforums.org/showthread.php?t=946062](http://ubuntuforums.org/showthread.php?t=946062)

está el problema y la solución. Algo con unos repositorios "fallados". Por lo que veo es
```
deb http://repoubuntusoftware.info harty all

```
Habría que cambiar "harty" por "hardy" y esperar que lo actualicen porque todavía falla. Si lo comentás en el sources.list se soluciona. 

Saludos

---

### Post by Applelnx on 2008-10-24
Gracias luks911, lo solucione editando el sources.list poniendo un # adelante de las lineas:


#deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

#deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

Saludos :)

---

### Post by luks911 on 2008-10-24
¡Genial!
Me alegroq ue haya servido.

Saludos

---

