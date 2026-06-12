---
title: "Error al iniciar Ubuntu Intrepid"
date: 2008-11-16
forum: Software
---

### Post by leosr on 2008-11-16
Hola a todos.

Instalé Intrepid desde los repositorios, aparentemente sin problemas. El tema es que cuando arranca aparece la clásica pantalla con la barra de progreso antes de llegar la final me aparece un texto q dice algo así como "change ownership.... ./var/... read only file system" varias veces con distintos archivos en esa carpeta y se queda estancado ahí. Sólo puedo entrar en el "recovery mode"

Aclaro que soy novato.

Gracias.

---

### Post by WanderingKnight on 2008-11-17
Aparentemente están chiflados los permisos de /var o algún subdirectorio. /var es donde se guardan los logs y mensajes varios del sistema para depuración de errores y ese tipo de cosas, y necesariamente tenés que tener permisos para escribir ahí. Fijate el path exacto que te tira así podemos ver exactamente qué directorio está teniendo problemas.

---

### Post by leosr on 2008-11-17
Esto es lo que aparece al iniciar:

---

### Post by guillermolisi on 2008-11-17
Por lo que dice la imagen es tema de permisos.

Para poder revisar el asunto habria que poner ese disco en otra maquina, como secundario, montarlo y revisar todos los permisos de /var de ese disco. 

Puede que solo este mal el directorio de mayor nivel y los subdirectorios esten bien como que esten todos mal.

La pregunta que se me ocurre, como llego a suceder esto ?

---

### Post by sergiom99 on 2008-11-17
> **guillermolisi said:**
> 
Para poder revisar el asunto habria que poner ese disco en otra maquina, como secundario, montarlo y revisar todos los permisos de /var de ese disco. 

se puede hacer esto mismo con un LiveCD?

[PS OT: Lisi, respondeme el mail de los backups!]

---

### Post by guillermolisi on 2008-11-17
Entiendo que si, que se puede hacer lo mismo iniciando con un LiveCD (yo recupere Grub de un HD iniciando la PC con un Live CD y para eso lo tuve que montar).

PS [OT]: Uhh ... perdoname, es que desde la RP de II se me acumularon quichicientos mensajes sin leer aun en mi inbox. Ya lo leo y respondo.

---

### Post by leosr on 2008-11-17
Probé lo de iniciar con el live cd (de Hardy) y ejecuté Nautilus como Root, propiedades, permisos. Ahi aparece "Acceso a archivo: ---", lo cambio a "Lectura y escritura" y lo cierro. Luego si lo abro está como antes.
Tendría que hacerlo desde la consola? Cómo lo hago?

No tengo posibilidad de de cambiar el disco a otra máquina.

Saludos.

---

### Post by leosr on 2008-11-17
Probé lo de iniciar con el live cd (de Hardy) y ejecuté Nautilus como Root, propiedades, permisos. Ahi aparece "Acceso a archivo: ---", lo cambio a "Lectura y escritura" y lo cierro. Luego si lo abro está como antes.
Tendría que hacerlo desde la consola? Cómo lo hago?
Cuando la re-inicio vuelve a quedarse en ese lugar.

No tengo posibilidad de de cambiar el disco a otra máquina.

Saludos.

---

### Post by hictio on 2008-11-17
El disco en si no tiene problemas verdad? Digo, problemas fisicos, vos lo estabas usando sin ningun inconveniente?
Es una laptop o un desktop?

Esos errores que indican que el file system esta "solo de lectura" los vi una sola vez con 8.04, y por un problema con el atajo de teclado que lo activa; es decir, que pone todo el HDD como 'read only', pero 
es necesario tipear: "Alt + SysRQ + u", y al rebootear el problema se arregla, no es persistente.

Podes bootear la maquina en modo "kernel recovery"? En modo mono usuario, y ver los logs de '/var/log/messages' de los intentos de booteo normal?

---

### Post by WanderingKnight on 2008-11-17
> Probé lo de iniciar con el live cd (de Hardy) y ejecuté Nautilus como Root, propiedades, permisos. Ahi aparece "Acceso a archivo: ---", lo cambio a "Lectura y escritura" y lo cierro. Luego si lo abro está como antes.

O podés hacerlo a lo bestia y hacer lo siguiente (AVISO, PUEDE LLEGAR A ROMPER EL SISTEMA):

1) Montás el Live CD.

2) Abrís una terminal.

3) Hacés

```
sudo -s
```

para tener permisos de root.

4) Creás directorio:

```
mkdir mountpoint
```

5) Montás el disco:

```
mount /dev/sd(*) mountpoint
```

En (*) va el número de disco (a, b, c) y el número de partición. Para saber cuál es, podés hacer fdisk -l.

6) Le das a lo bestia:

```
chmod -R 777 mountpoint/var
```

Eso le cambia todos los permisos al mínimo a todos los archivos de /var... aunque es probable que rompa más cosas de las que arregle. Por lo que estoy viendo /var tiene permisos muy variados en distintos archivos. Pero puede ser un punto de partida, por lo menos para verificar que no se trate un problema de disco o de filesystem.

---

### Post by leosr on 2008-11-18
> **hictio said:**
> El disco en si no tiene problemas verdad? Digo, problemas fisicos, vos lo estabas usando sin ningun inconveniente?
Es una laptop o un desktop?

Esos errores que indican que el file system esta "solo de lectura" los vi una sola vez con 8.04, y por un problema con el atajo de teclado que lo activa; es decir, que pone todo el HDD como 'read only', pero 
es necesario tipear: "Alt + SysRQ + u", y al rebootear el problema se arregla, no es persistente.

Podes bootear la maquina en modo "kernel recovery"? En modo mono usuario, y ver los logs de '/var/log/messages' de los intentos de booteo normal?

Hola.
Es una PC de escritorio. El HD funcionaba sin problemas hasta la actualización y esta fue normal hasta el momento de re-iniciar.

Probé tipeando "Alt + SysRQ + u" cuando aparece la pantalla dode se bloquea y no pasó nada. Con "SysRQ" te referís a la tecla "impr pant/PetSis" del teclado?

Puedo ingresar usando el "Recovery Mode" del menú de Grub, te referís a ese?. Es normal que me aparezca en ese menú el Hardy con 2 versiones del kernel, Win XP, Intrepid con la versión 2.6.27-7-generic y otra anterior?

---

### Post by leosr on 2008-11-18
> **hictio said:**
> El disco en si no tiene problemas verdad? Digo, problemas fisicos, vos lo estabas usando sin ningun inconveniente?
Es una laptop o un desktop?

Esos errores que indican que el file system esta "solo de lectura" los vi una sola vez con 8.04, y por un problema con el atajo de teclado que lo activa; es decir, que pone todo el HDD como 'read only', pero 
es necesario tipear: "Alt + SysRQ + u", y al rebootear el problema se arregla, no es persistente.

Podes bootear la maquina en modo "kernel recovery"? En modo mono usuario, y ver los logs de '/var/log/messages' de los intentos de booteo normal?
No puedo postear el contenido del archivo "messages" xq es muy largo, si no diganme cómo.

---

### Post by hictio on 2008-11-18
> **leosr said:**
> Hola.
Es una PC de escritorio. El HD funcionaba sin problemas hasta la actualización y esta fue normal hasta el momento de re-iniciar.

Probé tipeando "Alt + SysRQ + u" cuando aparece la pantalla dode se bloquea y no pasó nada. Con "SysRQ" te referís a la tecla "impr pant/PetSis" del teclado?

Puedo ingresar usando el "Recovery Mode" del menú de Grub, te referís a ese?. Es normal que me aparezca en ese menú el Hardy con 2 versiones del kernel, Win XP, Intrepid con la versión 2.6.27-7-generic y otra anterior?

Si, ese es el boton.
Pero el shortcut no lo tenes que usar, ese shortcut activa el paso de todo el file system a read only.


Si, ese es el recovery mode, podrias probar de bootear, entrar, y ver los logs.
En mi caso, cuando vi ese error en un Ubuntu, en el log '/var/log/messages' tenia es entrada:

```

Oct 14 00:09:16 tango kernel: [682988.488445] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks

```

Pero como te digo, con un reboot, fue suficiente. De hecho, el sistema seguia funcionando correctamente, solo daba problemas cuando habia que hacer un cambio, por ejemplo, transferir archivos de otra maquina a esta.

La solucion de WanderingKnight puede que camine, pero vas a mandar al demonio todos los permisos de ese directorio.

La instalacion la hiciste desde cero, o hiciste un upgrade de 8.04 a 8.10?

---

### Post by leosr on 2008-11-18
> **hictio said:**
> Si, ese es el boton.
Pero el shortcut no lo tenes que usar, ese shortcut activa el paso de todo el file system a read only.


Si, ese es el recovery mode, podrias probar de bootear, entrar, y ver los logs.
En mi caso, cuando vi ese error en un Ubuntu, en el log '/var/log/messages' tenia es entrada:

```

Oct 14 00:09:16 tango kernel: [682988.488445] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks

```

Pero como te digo, con un reboot, fue suficiente. De hecho, el sistema seguia funcionando correctamente, solo daba problemas cuando habia que hacer un cambio, por ejemplo, transferir archivos de otra maquina a esta.

La solucion de WanderingKnight puede que camine, pero vas a mandar al demonio todos los permisos de ese directorio.

La instalacion la hiciste desde cero, o hiciste un upgrade de 8.04 a 8.10?
Hice un upgrade desde Hardy.

Busqué en el archivo algo de lo que te apareció y no hay nada.

Voy a esperar hasta el fin de semana y si no encuentro solución formateo la partición e instalo todo de nuevo (tengo el /home en otra partición).
Me conviene instalar Hardy y luego hacer el upgrade o me bajo el live cd?

Saludos.

---

### Post by guillermolisi on 2008-11-18
Si queres verificar que la actualizacion fue lo que rompio los permisos de /var, instala 8.04 y luego actualiza.

Si no te importa saber cual fue la causa, dale para adelante con el LiveCD y listo.

Si vas a instalar la 8.04 que sea 8.04.1 asi no tenes que actualizar tantos paquetes hasta poder llevarla a la 8.10 (salvo que no te importe esperar un poco mas por eso).
La 8.04.1 ya trae una buena cantidad de paquetes actualizados.

---

### Post by leosr on 2008-11-18
> **guillermolisi said:**
> Si queres verificar que la actualizacion fue lo que rompio los permisos de /var, instala 8.04 y luego actualiza.

Si no te importa saber cual fue la causa, dale para adelante con el LiveCD y listo.

Si vas a instalar la 8.04 que sea 8.04.1 asi no tenes que actualizar tantos paquetes hasta poder llevarla a la 8.10 (salvo que no te importe esperar un poco mas por eso).
La 8.04.1 ya trae una buena cantidad de paquetes actualizados.

Una semana antes de que salga Intrepid actualizé desde los repositorios y no tuve problemas, salvo por VirtualBox que no era compatible. Por eso reinstalé Hardy.
Ahora estoy bajando el livecd de Intrepid y este finde lo instalo para ver que pasa.

Saludos.

---

