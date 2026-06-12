---
title: "No puedo iniciar con Ubuntu"
date: 2008-10-15
forum: Software
---

### Post by Pessimiste_x on 2008-10-15
Mi problema no se que tan senciloo o complicado sea. El punto es que hace poco me entro un virus en la maquina (tenia windows) y tuve que formatear (no lo pude sacar con el antivirus porque no me lo dejaba usar al igual que un monton de aplicaciones que me habia anulado, supongo, el virus). Bueno, en fin, el tema es que formatee la maquina en la casa de un amigo y despues de pelearnos un poco de que si instalaba o no linux (porque yo decia que era una ****** y que me dejara el windows pero el decia que era mejor entonces le dije que si para probarlo y me instalo los dos) instale ubuntu junto con windows (en particiones diferentes) despues estuve un tiempo usando linux pero resulta que el virus estaba en mi mp4 y windows se me volvio a cagar (aparte no habia instalado antivirus jeje), entonces formatee la particion de windows e instale windows de nuevo pero ahora me aparecia para elegir entre dos windows XP (y tenia uno solo, y me dio bronca eso tambien), pero la pantalla de eleccion de OS (grub si no me equivoco) no aparece, cuando tendria aparecer antes de la eleccion de windows... La hice re re re larga ¿no?

Bueno... lo que yo quiero hacer es que me aparezca el grub asi puedo arrancar el ubuntu. porque ensima hay carpetas a las que desde windows no puedo entrar y no se porque

La verdad es que ahora le doy la razon a mi amigo de que ubuntu es mejor, y me molesta un poco el windows porque ya ni lo usaba (exepto para jugar al sims :D) y quiero volver a usar linux, espero alguien me pueda ayudar, desde ya muchas gracias

---

### Post by SLA_leandrin on 2008-10-15
Bueno primero que nada no te preocupes. Es un error típico de alguien que recién comienza en esto de linux. Segundo, te diría que antes de postear busques porque por suerte, este foro funciona de primera, y siempre hay respuestas que podes obtener con mas rapidez a dudas que uno tiene.

Lo que te voy a explicar lo saqué de aqui ([fuente]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")).

Primero que nada, tenes que bootear nuevamente del live cd de ubuntu. Una vez que ha arrancado, y el sistema está funcionando, inicias la consola (APLICACIONES --> ACCESORIOS --> TERMINAL)

Una vez allí tipeas

```
sudo grub
```

Entonces te va a salir un signo "grub>"

ahora;

```
find /boot/grub/stage1
```

Esto te va a dar como resultado una ubicación donde está el grub, por ejemplo, hd0,1

ahora;
```
root (hd?,?)
```

en donde tenés que reemplazar hd?,? por lo que te haya devuelto el comando anterior.

ahora vamos a reinsalar el grub;
```
setup (hd0)
``` 

Y listo, estamos a un solo paso,

```
quit
```

Salis de la consola y reinicias la máquina, deberías tener el grub funcionando.

Avisa si te ayudó.

Saludos.

---

### Post by victor_nesta on 2008-10-16
Agrego un detalle mas por si lo necesitas. o porcino
Acordate que por ejemplo
**(hd0) es igual a (hda)**
La nomenclatura empieza en 0
En mi caso **(hd1,4)** es el segundo disco, 5 particion o **(hdb,5)**
y la diferencia de hda y sda, es si el disco es Pata o Sata.

---

### Post by Pessimiste_x on 2008-10-23
Bien... intente hacer lo que me dijeron pero despues de bajarme ubuntu y grabarlo en un cd y de ponerlo en mi computadora antes de reiniciar la maquina y despues de reiniciar la maquina, me paso que no boteaba del cd, por lo tanto me hizo instalar algo desde windows para que, cuando me aparece para elegir que windows quiero usar, me de la opcion de elegir ubuntu. entonces pude arrancar el live cd, pero no podia hacer lo que me aconsejaron porque me decia ''error ?? file not found'' (?? = algun numero que no recuerdo). Bueno en fin, formatee e instale ubuntu de nuevo pero JA!, no tengo internet en mi casa y no se como descargar los drivers. intente usar el buscador del foro pero no me tiraba nada.

La pregunta es entonces: ¿De donde puedo descargar drivers para ubuntu?. y tambien necesito los codecs tales como mp3, mp4, wma, wmv, avi, etc, etc, etc.

Ah por cierto, gracias por la ayuda

---

### Post by faktorqm on 2008-10-24
No tenes internet en tu casa simplemente por que no tenes o por que no la supiste/pudiste configurar en ubuntu? De ser la segunda opcion, deci que conexion tenes y te ayudamos. 
Si no tenes internet en tu casa, te cuento que no es tan asi como en windows de bajar un archivo y ejecutarlo. Es asi por ejemplo en caso de nvidia o de ati (creo) pero lo que hacen la mayoria de los programas es, que pongas que marca de placa de video (por ejemplo, o de placa wireless) tenes y te lo bajan automaticamente sin que vos hagas nada. Algunas veces anda, otras no, pero decinos mas o menos que dispositivos te estan faltando y lo vamos viendo. Salu2!

---

### Post by Pessimiste_x on 2008-10-25
No, no tengo internet en mi casa, me baje los paquetes en un ciber, uno es ubuntu restricted (.deb creo) me baje el de nVIDIA de la pagina oficial de la placa pero, no se como instalarlos.

---

### Post by faktorqm on 2008-10-27
Es que no vas a poder... No tenes ningun amigo con internet? es mas facil llevar un dia la pc a la casa y hacer todo que ver todo el tema este sin internet... ¿Alguno conoce otra alternativa? Lo que pasa es que si te bajas el dvd es lo mismo, a menos que lo consigas... el tema drivers suele ponerse puntiagudo sin internet... Salu2!

---

