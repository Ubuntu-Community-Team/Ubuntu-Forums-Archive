---
title: "consulta de sonido karmic"
date: 2009-11-13
forum: Software
---

### Post by granjero on 2009-11-13
buenas gente, acá yo nuevamente con preguntas...

ahora lo que me aqueja es lo siguiente...

tengo roto el gestor de actualizaciones en jaunty y como no estoy pudiendo solucionar el tema, me quemé un CD cd karmic para ver que onda...

cuando corro el live session anda todo bárbaro menos una cuestión con el sonido... antes de empezar a reproducir algo hace como una explosión sonora... 

abrí el rhythmbox, fui a jamengo o algo así y puse play en lo primero que encontré. justo antes de empezar a reproducir escuché un [SIZE="7"]PUM[/SIZE] muy fuerte y después empezó a reproducir normalmente. Lo probé varias veces, parece ser que la primera vez que quiere reproducir algo explota. El sonido aficano de inicio lo reproduce bien sin sobresaltos.

a alguien le sucede algo similar?

la placa de sonido es una onboard:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

---

### Post by guillermolisi on 2009-11-13
Hay por lo menos un par de threads sobre el tema.

[http://ubuntuforums.org/showthread.php?t=1320861](http://ubuntuforums.org/showthread.php?t=1320861)
[http://ubuntuforums.org/showthread.php?t=1306815](http://ubuntuforums.org/showthread.php?t=1306815)

---

### Post by granjero on 2009-11-13
creo que mi problema no es el mismo que se trata en esos hilos guillermolisi!

yo sí tengo sonido...  desde el inicio... pero cuando arranca explota y después anda todo ok! la explosiñon es más bien molesta... pero siempre desde el live CD... cuando instale veré si sigue el problema.

por ahora como ando sin tiempo seguiré con mi jaunty cachuzo!

salud!

---

### Post by guillermolisi on 2009-11-13
Dale una leida a [este otro thread]("http://ubuntuforums.org/showpost.php?p=8275036&postcount=25"). Si bien el tema se inicio por un problema con el microfono la solucion vino por un problema (entiendo) similar al tuyo de alguien que participa en la lista de soporte via e-mail de este LoCo Team. Esa persona hasta comentaba lo del bump al iniciar el sonido y luego le desaparecio.

---

### Post by granjero on 2009-11-14
ok. muchas gracias! voy a ver si instalo KK a ver que pasa...

salud!

---

### Post by granjero on 2009-11-30
bueno finalmente actualicé a KK

el problema de las explosiones cuando algún programa engancha el audio persiste....

estuve viendo las soluciones y nada...

instale linux-backports-modules-alsa-karmic-generic y no hubo cambios...

salud!

---

### Post by alfplayer on 2009-11-30
Puede ser este problema: [http://www.ubuntu-es.org/?q=node/120587](http://www.ubuntu-es.org/?q=node/120587)

---

### Post by granjero on 2009-12-01
gracias alfplayer por el aporte. 

el problema que describen ese post pareciera ser el mismo problema que tengo yo.

hice lo que recomiendan y comenté las líneas del archivo:

```
/etc/modprobe.d/alsa-base.conf
```

quedando así!

```
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N
```

pero lamentablemente el problema persiste!

salud!

---

### Post by granjero on 2009-12-02
como eso no funcionó probé con:

```
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=0 power_save_controller=N
```

```
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10000000000000000000000000000000 power_save_controller=N
```

y lamentablemente el problema persiste.

un dato más es que antes del sonido de los tamborcitos del gdm también hace ese mismo ruido.... 

salud!

---

### Post by alfplayer on 2009-12-03
> **granjero said:**
> como eso no funcionó probé con:

```
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=0 power_save_controller=N
``````
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10000000000000000000000000000000 power_save_controller=N
```y lamentablemente el problema persiste.

un dato más es que antes del sonido de los tamborcitos del gdm también hace ese mismo ruido.... 

salud!

Mmm... Hay un valor que puede estar demasiado alto.

---

### Post by granjero on 2009-12-03
no entiendo alplayer a que te referís?

salud!

---

### Post by anarko on 2009-12-03
Hace lo que dicen en el post que mencionaron antes, pero en vez de cambiar el valor por 10000000000000000000000000000000000 directamente comenta las lineas en cuestion poniendoles un # adelante asi son omitidas de la conf. y el coso no apaga la placa de sonido.
Ami me pasa lo mismo esta noche lo pruebo en casa, aca en la oficina no tengo parlantes.

Saluttes.

---

### Post by alfplayer on 2009-12-03
> **anarko said:**
> Hace lo que dicen en el post que mencionaron antes, pero en vez de cambiar el valor por 10000000000000000000000000000000000 directamente comenta las lineas en cuestion poniendoles un # adelante asi son omitidas de la conf. y el coso no apaga la placa de sonido.
Ami me pasa lo mismo esta noche lo pruebo en casa, aca en la oficina no tengo parlantes.

Saluttes.

No fue lo que hizo primero?

Lo que quiero decir ese valor con tantos ceros puede ser demasiado alto. A alguien le funcionó con el valor 5000000 en el link anterior de ubuntu-es, se podría probar con ese valor. Aunque si no se resuelve con estas recomendaciones el problema puede ser de otro tipo.

Es necesario que se actualize la configuración después de editar el archivo. Una forma de estar seguro de que los cambios entren en efecto es reiniciar ubuntu (después de editar el archivo).

---

### Post by granjero on 2009-12-03
ya hice la prueba con todas las opciones con 5000000, con las dos lineas comentadas, con valor 0, todas las opciones que comentan el post ese...


el problema persiste y es medio molesto, sobre todo cuando el volumen está medio alto.


salud!

---

### Post by Gundizalv on 2009-12-04
Hola amigos! yo tenía el mísmo problema en mi NB una HP dv2625la en la que estoy corriendo Ubuntu9.10 ayer hice lo que dice el post de granjero de descomentar la linea del alsa-base.conf y ahora el sonido desapareció.

Saludos.

---

### Post by granjero on 2009-12-05
Gundizalv, me alegra que se halla solucionado tu tema... el mío sigue pendiente de solución...  estuve googleando pero no encontré otras soluciones....


salud!

---

### Post by granjero on 2009-12-14
bump...

;)

---

### Post by alfplayer on 2009-12-14
granjero, si es útil lei que este problema de explosiones si no se resuelve con la solución que se comenta anteriormente puede estar causado por problemas de drivers de sonido. Si es asi se resolvería con versiones actualizadas de los drivers que causan el problema en el caso que estén disponibles.

---

### Post by granjero on 2009-12-14
hoy buscando y buscando encontré este hilo:

[http://ubuntuforums.org/showthread.php?t=1312690&highlight=loud+noise](http://ubuntuforums.org/showthread.php?t=1312690&highlight=loud+noise)

y ejecuté este comando

```
sudo alsa force-reload
```

la respuesta fue esta:

```
jm@pcjm:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
Terminating processes: 4406lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
 4553lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer.
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timerWARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bakup, it will be ignored in a future release.
.

```

ese archivo es el bakup que hice antes de modificar la linea.... 

lo borre y listo el pollo!

```
jm@pcjm:~$ sudo rm /etc/modprobe.d/alsa-base.conf-bakup 
jm@pcjm:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
Terminating processes: 4764lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jm/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-pcm snd-page-alloc snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-pcm snd-page-alloc snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```


igual queda ahí un WARNING que no se que es....


salud!

---

