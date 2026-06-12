---
title: "[SOLVED] undev.conf"
date: 2008-08-12
forum: Software
---

### Post by Tosh78 on 2008-08-12
Buenas! Les cuento que anoche instale unas actualizaciones del sistema y unas de Amarok Nightly que estoy probando, apague y me fui a dormir. Hoy a la mañana, cuando prendo la computadora me encuentro con que primero tarda muchisimo mas en aparecerme el cartelito de ubuntu que te muestra la barra que va cargando, y segundo, cuando termina de cargar me dice que que el archivo undev.conf es invalido y me deja ahi nomas. Me dice que escriba HELP para ver los comandos y listo, queda en modo consola. La cuestion es que no se casi nada de consola, un par de cosas basicas, pero nada mas, y quiero solucionar esto. Me pueden dar una mano?

---

### Post by sdennie on 2008-08-12
Podés entrar con otro kernel?  Fijate en grub, si tenés un kernel viejo y si anda.  Si no, probá con un kernel "recovery mode" que te da mas información.  Por defecto udev.conf no tiene casi nada y puedo borrarlo en una máquina virtual y la máquina inicia sin problema.

---

### Post by Tosh78 on 2008-08-12
No tengo un kernel viejo :(
Para entrar en recovery aprieto esc cuando esta haciendo la cuenta regresiva?

---

### Post by sdennie on 2008-08-12
> **Tosh78 said:**
> No tengo un kernel viejo :(
Para entrar en recovery aprieto esc cuando esta haciendo la cuenta regresiva?

Si.  Y desde alla vas a tener "recovery mode" y a veces un kernel viejo.

---

### Post by Tosh78 on 2008-08-12
Bueno, probe de entrar en recovery mode y me tiro lo siguiente:

Begin: Running /scripts/init-premount
udevd[1141] Parde-config_file: can't open'/etc/udev/udev.conf' as a config file: invalid argument
udevd[1143] Parde-config_file: can't open'/etc/udev/udev.conf' as a config file: invalid argument
Done.
Begin: mounting root file system
Begin: running /scripts/local-top
Done.
Begin: waiting for root system
[    16.190972] atbkd.c: spurious NAK on isa0060/serio0 some program might be trying access hardware directly
[    16.390439] atbkd.c: spurious NAK on isa0060/serio0 some program might be trying access hardware directly

Despues, entre con otro kernel (si, al final si tenia uno) y entre de lo mas bien. Solo...que recien despues de un rato (hable de al menos 3 minutos) de que entre se habilitaron algunas cosas como AWN, screenlets y fundamentalmente la red. Con lo cual...que puedo hacer? que puede estar pasando? Por favor, denme una mano.

---

### Post by faktorqm on 2008-08-13
Hola, malas noticias... es un bug del kernel!

- Que version tenes? (uname -r) 
- tenes una notebook no? 

empeza por probar esto para ahorrar tiempo: bootea con un kernel viejo, y abri una consola

```
sudo gedit /boot/grub/menu.lst
```

y ahi te abre el archivo de configuracion del grub. En la linea del kernel (la ultima version que te esta trayendo problemas) la vas a ver algo asi como (parecida, no igual):

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5430a0a1-0ca4-4304-b2b5-d682a2ff0f43 ro quiet nosplash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

y le tenemos que agregar esta linea: i8042.panicblink=0

asi que te tiene que quedar:

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5430a0a1-0ca4-4304-b2b5-d682a2ff0f43 ro i8042.panicblink=0 quiet nosplash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

y ahi grabas y salis. reinicias y arrancas normalmente, si te sigue tirando el error lo vemos. Salu2!!

te paso las paginas que visite para ver el problema:

bug en launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/34501/comments/18](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/34501/comments/18)
bug en kernel.org: [http://bugzilla.kernel.org/show_bug.cgi?id=8140](http://bugzilla.kernel.org/show_bug.cgi?id=8140)
solucion en kerneltrap: [http://kerneltrap.org/node/5898](http://kerneltrap.org/node/5898)
[http://www.linuxquestions.org/questions/linux-newbie-8/kernel-panic-atkbd.c-spurios-ack-on-isa0060-after-installing-2.6.19.1-512839/](http://www.linuxquestions.org/questions/linux-newbie-8/kernel-panic-atkbd.c-spurios-ack-on-isa0060-after-installing-2.6.19.1-512839/)
[http://www.linuxquestions.org/questions/linux-general-1/kernel-panicatkbd.c-spurious-ack-on-isa0060serio0-507224/](http://www.linuxquestions.org/questions/linux-general-1/kernel-panicatkbd.c-spurious-ack-on-isa0060serio0-507224/)

---

### Post by Tosh78 on 2008-08-13
Muchisimas gracias Faktorqm!! Si, tengo una notebook! Voy a probar la solucion que me decis.
Otra cosa que me parecio muy rara, aun arrancando con un kernel anterior, es que cuando quiero apagar, aprieto el botoncito en el panel de arriba (el que te muestra la pantalla de cerrar sesion y demas) y no solo no aparece el menu, sino que ademas desaparecer el panel!! tengo que apgar haciendo "sudo shutdown now" y aun asi a veces se queda tildada y no apaga. Habra alguna relacion con esto? Esto me empezo a pasar al mismo tiempo que lo del kernel. Si saben de algo, me pueden avisar?

---

### Post by faktorqm on 2008-08-13
Si tiene todo que ver, lo que pasa es que te trastorna la kbza el kernel jajajaj tambien podes probar de poner "acpi=off" en las opciones que te pase antes, para arrancar el kernel sin eso. es mas, quiza con eso te salva todos los errores... acordate de postear uname -r. salu2!!

---

### Post by Tosh78 on 2008-08-13
Hola! Probe lo que me dijiste pero naranjas, sigue todo igual.
Por cierto, la version del kernel es 2.6.24-19-generic
Ahora voy a probar lo del ACPI...alguna otra idea?
Tambien probe editando el archivo udev.conf y comentandole la linea que decia:
udev_log="err"

Esto es lo que dice este archivo: 
# udev.conf

# The initial syslog(3) priority: "err", "info", "debug" or its
# numerical equivalent. For runtime debugging, the daemons internal
# state can be changed with: "udevcontrol log_priority=<value>".
udev_log="err"

---

### Post by Tosh78 on 2008-08-13
Bueno, finalmente lo resolvi. Lei por ahi googleando sobre el tema, que el udev podia ser reinstalado desde Synaptic y entonces decidi probar eso. Para mi sorpresa, funciono bien, asi que. Lei que a algunos usuarios mas les habia pasado lo mismo que a mi: instalaron unas actualizaciones y les empezo a tirar el error de udev. No se por que puede darse esto, pero bueno, si a alguno le llega a pasar, esta es la solucion.

---

