---
title: "Ayuda por favor con puertos y Firestarter"
date: 2009-01-11
forum: Software
---

### Post by guillermon on 2009-01-11
Hola:
     La verdad que me ha ido muy pero muy mal con el tema de los puertos, descargas p2p, etc (Transmission me anda muy lento; Ares no se conecta nunca, amule siempre idbaja). He leído mucho... y ya sé que no poseo los conocimientos; y estoy algo desahuciado con esto (y desgraciadamente todo esto funciona bien en Win$, el cual estaba a punto de formatear definitivamente). Las preguntas específicas:
- No puedo abrir puertos; he instalado el Firestarter, y me dice que no puede arrancar el cortafuegos, pues no está disponible el dispositivo (aviso, internet funciona bien). Esta situación fue un revés durísimo...

- Ares no se conecta nunca, aún emulando como win ME, bajando la velocidad, reistalando wine y el mismo ares...

- Amule me informa que tengo una versión antigua... y no sé cómo se actualiza...

     Notas pertinentes: Tengo Ubuntu 8.04, 64 bits; no tengo router; conexión cablemodem, sin compartir internet (antes tuve un router). 

     Cualquier ayuda es bienvenida, aún sea una palmada, un hombro... ji. Saludos, desde ya gracias

---

### Post by sergiom99 on 2009-01-11
te cuento que en un Xubuntu 8.04, firestarter tambien me daba un mensaje de que no puede iniciarse. Lo solucione reiniciando la red (*sudo /etc/init.d/networking restart*) y ahi levantaba. Finalmente lo saque.
Con respecto al amule, tengo andando perfecto la version amule SVN que esta en los repos de hardy.

---

### Post by guillermon on 2009-01-13
Hola Sergio, muchas gracias. He probado lo que comentas y funciona; también a partir de tu comentario encontré que cambiandoun acento, se soluciona definitivamente el bug. Ahora bien, sigo si poder abrir los puertos, pues voy a Normativa, en la parte Normativa para el tráfico entrante, añado una regla en Permitir Servicio, no le pongo ningún nombre, le asigno un número, por ejemplo 55000, aplico, y nada... Reinicio Xwin y nada... ¿qué estoy haciendo mal?
   Además observo que a los segundos, el símbolo de Firestarted pasa de estar azul a rojito con un rayo.
   De paso otra preguntita: porqué ahora (pues antes andaba bien) cuando uso el comando sudo shutdown 10 (10 min por ejem), no se apaga, sino que se cierra y da un menú?
   Muchas gracias desde ya, saludos... 
Guillermo

---

### Post by Hei Ku on 2009-01-14
Ademas de agregar la regla, apretaste en Aplicar regla? Si no, la agrega, pero no la pone a funcionar.

---

### Post by sergiom99 on 2009-01-14
de nada.

por las dudas reinicia la PC asi levanta todo de nuevo, si o si.

---

### Post by guillermon on 2009-01-16
> **Hei Ku said:**
> Ademas de agregar la regla, apretaste en Aplicar regla? Si no, la agrega, pero no la pone a funcionar.

   Bueno, tenía en Preferencias la opción de que se apliquen los cambios inmediatamente... Lo desactivé, e hice como sugerís (reinicié toda la pc inclusive) y nada... Pruebo los puertos en 
```
http://www.amule.org/testport.php
```
   Continúa poniénndose rojo el símbolo... Otra idea...?

Muchas gracias!

---

### Post by Hei Ku on 2009-01-18
Fijate en la parte de eventos de Firestarter, cuando haces la comprobacion de puertos, por qué puertos intenta entrar, porque los debes tener todavia cerrados.

---

### Post by guillermon on 2009-01-19
> **Hei Ku said:**
> Fijate en la parte de eventos de Firestarter, cuando haces la comprobacion de puertos, por qué puertos intenta entrar, porque los debes tener todavia cerrados.

  Bueno, fuí donde me dices, y no entiendo nada... Te agradezco la ayuda... Desde mi sentido común pienso que en algunas metidas de patas algo quedó mal; porque no puede ser que a otros funcione bien de toque... estoy valorando la posibilidad de hacer una instalación limpia... Si tienes otra idea... gracias!

  Saludos...:confused:

---

### Post by guillermolisi on 2009-01-19
> **guillermon said:**
> Bueno, fuí donde me dices, y no entiendo nada... Te agradezco la ayuda... Desde mi sentido común pienso que en algunas metidas de patas algo quedó mal; porque no puede ser que a otros funcione bien de toque... estoy valorando la posibilidad de hacer una instalación limpia... Si tienes otra idea... gracias!

  Saludos...:confused:

Toma screenshots de las reglas que definiste en Firestarter y adjuntalas a un mensaje asi podemos verlas y aconsejarte mejor y mas certeramente.

---

### Post by guillermon on 2009-01-21
> **guillermolisi said:**
> Toma screenshots de las reglas que definiste en Firestarter y adjuntalas a un mensaje asi podemos verlas y aconsejarte mejor y mas certeramente.

   Hola Tocayo, he intentado anteriormente subir un screenshots, pero lo había intentado con Insertar Imagen, y no he podido. Ahora que leo que dices Adjuntar, supongo que se podrá... Aquí subo entonces, desde ya gracias... espero los consejos... Salu2...
Guillermo

PD: normalmente, el Firestarter en el &#347;imbolo se pone en forma de un rayito; no como se lo vé en la imágen...

---

### Post by guillermolisi on 2009-01-25
> **guillermon said:**
> Hola Tocayo, he intentado anteriormente subir un screenshots, pero lo había intentado con Insertar Imagen, y no he podido. Ahora que leo que dices Adjuntar, supongo que se podrá... Aquí subo entonces, desde ya gracias... espero los consejos... Salu2...
Guillermo

PD: normalmente, el Firestarter en el &#347;imbolo se pone en forma de un rayito; no como se lo vé en la imágen...
Te adjunto un screenshot de mi firestarter para que veas como lo configure para el aMule que me anda perfecto.

Los ports que le puse los saque de las sugerencias que dan en su website (antes lo suaba bajo Windows ya que tome los archivos de configuracion que tenia en ese entorno y los copie en Ubuntu para no configurar todo de nuevo).

Los parametros que vas a ver en el grafico corresponden a Inbound Traffic Policy del Firestarter. Para Outbound Traffic Policy no configure nada ya que si tengo un programa que requiere enviar algo a Internet es porque lo active yo (o sea, que salga todo lo que tenga que salir).

---

### Post by guillermon on 2009-01-27
> **guillermolisi said:**
> Te adjunto un screenshot de mi firestarter para que veas como lo configure para el aMule que me anda perfecto.

Los ports que le puse los saque de las sugerencias que dan en su website (antes lo suaba bajo Windows ya que tome los archivos de configuracion que tenia en ese entorno y los copie en Ubuntu para no configurar todo de nuevo).

Los parametros que vas a ver en el grafico corresponden a Inbound Traffic Policy del Firestarter. Para Outbound Traffic Policy no configure nada ya que si tengo un programa que requiere enviar algo a Internet es porque lo active yo (o sea, que salga todo lo que tenga que salir).

   Guillermo, de nuevo... pues no consigo dar un paso (desde hace tiempo), pero no desisto. Te adjunto un nuevo pantallazo, donde se ve que he intentado configurar aquellos de amule como los tienes vos; si te fijas en la página de  atrás verás que haciendo la comprobación del puerto desde amule lo da cerrado, y me figura siempre el logo rojo de Firestarter, y titilando... Alguna idea?
  Aclaro que he reiniciado, tanto toda la pc, como el modo gráfico...

Desde ya gracias, nuevamente...

---

### Post by guillermolisi on 2009-01-27
> **guillermon said:**
> Guillermo, de nuevo... pues no consigo dar un paso (desde hace tiempo), pero no desisto. Te adjunto un nuevo pantallazo, donde se ve que he intentado configurar aquellos de amule como los tienes vos; si te fijas en la página de  atrás verás que haciendo la comprobación del puerto desde amule lo da cerrado, y me figura siempre el logo rojo de Firestarter, y titilando... Alguna idea?
  Aclaro que he reiniciado, tanto toda la pc, como el modo gráfico...

Desde ya gracias, nuevamente...

Primero, ingresa en una consola el comando ```
ifconfig
``` y pega en un nuevo mensaje su salida. Esto en la PC que oficia de gateway a Internet (donde esta el Firestarter).

Luego, fijate en el ejemplo grafico que envie que omitiste configurar la seccion Forward Services (la seccion inferior de mi screenshot).

Luego, asi no va a funcionar porque dudo muchisimo que tu LAN use IPs del bloque 90.0.0.0, asi que esas reglas como estan es lo mismo que nada (por eso te pido que pongas la salida del ifconfig, asi sabemos que IPs usas en tu LAN).

El icono de Firestarter normalmente se pone en rojo porque indica que bloqueo un acceso no autorizado por algunas de las reglas definidas.

---

### Post by guillermon on 2009-01-27
> **guillermolisi said:**
> Primero, ingresa en una consola el comando ```
ifconfig
``` y pega en un nuevo mensaje su salida. Esto en la PC que oficia de gateway a Internet (donde esta el Firestarter).

Luego, fijate en el ejemplo grafico que envie que omitiste configurar la seccion Forward Services (la seccion inferior de mi screenshot).

Luego, asi no va a funcionar porque dudo muchisimo que tu LAN use IPs del bloque 90.0.0.0, asi que esas reglas como estan es lo mismo que nada (por eso te pido que pongas la salida del ifconfig, asi sabemos que IPs usas en tu LAN).

El icono de Firestarter normalmente se pone en rojo porque indica que bloqueo un acceso no autorizado por algunas de las reglas definidas.

    Hola Guillermo, aquí de nuevo. Copio lo que deviene del comando:
guillermo@guille-desktop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:e0:4d:26:43:eb  
          inet dirección:200.127.233.229  Difusión:255.255.255.255  Máscara:255.255.255.0
          dirección inet6: fe80::2e0:4dff:fe26:43eb/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:594146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55363 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:144554028 (137.8 MB)  TX bytes:5466450 (5.2 MB)
          Interrupción:252 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:2664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2664 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:113102 (110.4 KB)  TX bytes:113102 (110.4 KB)

guillermo@guille-desktop:~$ 

   Respecto de que no he configurado la seccion Forward Services, que en castellano entiendo que es Reenviar servicio, tienes razón; ocurre que no se puede, allí no se puede añadir regla...
   Bueno, qué mas decirte, espero tu ayuda. Mil gracias... Hasta pronto

Guillermo

---

### Post by guillermolisi on 2009-01-27
> **guillermon said:**
> Hola Guillermo, aquí de nuevo. Copio lo que deviene del comando:
guillermo@guille-desktop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:e0:4d:26:43:eb  
          inet dirección:200.127.233.229  Difusión:255.255.255.255  Máscara:255.255.255.0
          dirección inet6: fe80::2e0:4dff:fe26:43eb/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:594146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55363 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:144554028 (137.8 MB)  TX bytes:5466450 (5.2 MB)
          Interrupción:252 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:2664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2664 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:113102 (110.4 KB)  TX bytes:113102 (110.4 KB)

guillermo@guille-desktop:~$ 

   Respecto de que no he configurado la seccion Forward Services, que en castellano entiendo que es Reenviar servicio, tienes razón; ocurre que no se puede, allí no se puede añadir regla...
   Bueno, qué mas decirte, espero tu ayuda. Mil gracias... Hasta pronto

Guillermo
Claro, no se puede porque en esa maquina, por lo menos de la que pasaste la salida del ifconfig, tiene una sola placa de red, eth0. Fijate y vas a ver que no figura otra que eth0 y 'lo' que es la misma placa.

El forwarding de servicios se puede hacer si tenes dos placas de red, una conectada a Internet y la otra a la LAN. Como vos tenes una sola placa, no es necesario ningun forwarding.

Ademas, tengo que reconocer que estaba convencido que tenias dos placas de red, my fault.

Bueno, siendo asi el tema cambia.

Primero, te adjunto un screenshot de mi FIrestarter para que verifiques que el trafico de salida de tu PC hacia Internet no esta restringido por el firewall.

Luego deberias modificar las reglas que pusiste en "Allow service" para que los ports de aMule se abran a Everyone (lo que pusiste estaba en la seccion Forward service de mi Firestarter, es decir, no van donde las pusiste). De esta forma quienes quieran acceder a los compartidos y demas servicios de aMule en tu maquina podran hacerlo sin trabas.

Fijate y comenta como te fue.

---

### Post by guillermon on 2009-01-28
> **guillermolisi said:**
> Claro, no se puede porque en esa maquina, por lo menos de la que pasaste la salida del ifconfig, tiene una sola placa de red, eth0. Fijate y vas a ver que no figura otra que eth0 y 'lo' que es la misma placa.

El forwarding de servicios se puede hacer si tenes dos placas de red, una conectada a Internet y la otra a la LAN. Como vos tenes una sola placa, no es necesario ningun forwarding.

Ademas, tengo que reconocer que estaba convencido que tenias dos placas de red, my fault.

Bueno, siendo asi el tema cambia.

Primero, te adjunto un screenshot de mi FIrestarter para que verifiques que el trafico de salida de tu PC hacia Internet no esta restringido por el firewall.

Luego deberias modificar las reglas que pusiste en "Allow service" para que los ports de aMule se abran a Everyone (lo que pusiste estaba en la seccion Forward service de mi Firestarter, es decir, no van donde las pusiste). De esta forma quienes quieran acceder a los compartidos y demas servicios de aMule en tu maquina podran hacerlo sin trabas.

Fijate y comenta como te fue.

    Bueno, he aquí nuevamente... El tráfico de salida está así como sugieres. He cambiado como lo sugieres (adjunto captura) y nada... que es como había intentado por primera vez, desde mi sentido común...
    Otra idea?? Nuevamente gracias...
Guillermo

---

### Post by guillermolisi on 2009-01-28
> **guillermon said:**
> Bueno, he aquí nuevamente... El tráfico de salida está así como sugieres. He cambiado como lo sugieres (adjunto captura) y nada... que es como había intentado por primera vez, desde mi sentido común...
    Otra idea?? Nuevamente gracias...
Guillermo
Por favor, verifica que los ports a usar que indica el programa aMule instalado coincidan con los que abris en el firewall via Firestarter.

En el ejemplo que te pase, los que figuran son los que tiene configurados mi instalacion de aMule pero no necesariamente tiene que ser igual en todas las maquinas.

Por otra parte, el firestarter reconocio eth0 como la placa de red conectada a Internet, cierto ?

---

### Post by guillermon on 2009-01-29
> **guillermolisi said:**
> Por favor, verifica que los ports a usar que indica el programa aMule instalado coincidan con los que abris en el firewall via Firestarter.

En el ejemplo que te pase, los que figuran son los que tiene configurados mi instalacion de aMule pero no necesariamente tiene que ser igual en todas las maquinas.

Por otra parte, el firestarter reconocio eth0 como la placa de red conectada a Internet, cierto ?

    Hola. Los puertos coinciden, y he verificado que el firestarter reconoche eth0 como placa red. Como también tengo Win$ en esta pc, he hecho todo el proceso en este sistema, y pasa el mismo problema, por lo cual vuelvo a una hipótesis que tuve en algún momento, y es que desde mi proveedor de internet me los están bloquendo. Hoy llamé dos veces, y me juran que no es así... En Win$, habiendo desactivado el firewall, antivirus, etc... y todo lo que hemos hecho desde Ubuntu... estoy convencido! (por favor alertarme de si puede ser otra cosa). 
      Estoy bastante indignado, pues sé que es algo que suelen hacer, y no creo que tengan algún prurito en hacérmelo a mi. He dejado una queja; y si lo compruebo, me cambiaré a algún proveedor que sepa que no lo hace (pido asesoramiento en esto también de llegar el caso). Para completar la información, cuento que tengo Internet cablemodem, con Flash o Ciudad Internet, en la ciudad de Cba.
      Espero comentarios, gracias!
Guillermo

---

### Post by guillermolisi on 2009-01-29
> **guillermon said:**
> Hola. Los puertos coinciden, y he verificado que el firestarter reconoche eth0 como placa red. Como también tengo Win$ en esta pc, he hecho todo el proceso en este sistema, y pasa el mismo problema, por lo cual vuelvo a una hipótesis que tuve en algún momento, y es que desde mi proveedor de internet me los están bloquendo. Hoy llamé dos veces, y me juran que no es así... En Win$, habiendo desactivado el firewall, antivirus, etc... y todo lo que hemos hecho desde Ubuntu... estoy convencido! (por favor alertarme de si puede ser otra cosa). 
      Estoy bastante indignado, pues sé que es algo que suelen hacer, y no creo que tengan algún prurito en hacérmelo a mi. He dejado una queja; y si lo compruebo, me cambiaré a algún proveedor que sepa que no lo hace (pido asesoramiento en esto también de llegar el caso). Para completar la información, cuento que tengo Internet cablemodem, con Flash o Ciudad Internet, en la ciudad de Cba.
      Espero comentarios, gracias!
Guillermo
Mira, en este pais todo puede ser :)

Yo tambien tengo Fibertel y se, porque me lo han dicho tecnicos que laburaron y/o laburan ahi, que no bloquean pero si dropean paquetes que identifican corresponden a una conexion P2P/eMule.

El dropeo de paquetes hace que de descarten una buena cantidad recibida obligando a las maquinas a reenviar lo que ya habian enviado, entonces de cada x cantidad del mismo paquete enviado pasa uno solo, el ultimo de la serie, desechando los anteriores. Esto hace que la velocidad de transferencia sea pauperrima.

Que hice ? Opte por usar Torrents, con Ktorrent, y encriptar las conexiones para que el ISP no sepa de que tipo son y no dropee paquetes.

Hasta aqui, me esta dando excelentes resultados.

Volviendo al tema, la verdad que no veo razon alguna para que aMule te asigne lowID. Por lo que pude ver hasta aqui, deberia funcionar con HighID a menos que te este conectando a un server cuyo port no este dentro de los que tenes abiertos en el firewall (ojo con esto porque no es algo menor).

---

