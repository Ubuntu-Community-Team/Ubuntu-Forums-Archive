---
title: "Firestart y wlan0"
date: 2009-06-09
forum: Software
---

### Post by DrKenobi on 2009-06-09
Hola. Instale Firestart para poder compartir la coneccion a internet.
Yo recibo la internet por Wi-Fi y quiero compartirla con otra PC via ethernet.

Instale el Firestart y no logro arrancar el firewall.
El primer error que me tiro fue:

> The device eth0 is not ready

Esto lo logre solucionar, pero ahora me tira otro error:

> The device wlan0 is not ready

Este ya no lo pude corregir y no se que hacer. Intente solucionarlo con algo similar a como corregi el primer error pero no tuve existo.

Alguna idea?

---

### Post by guillermolisi on 2009-06-09
> **DrKenobi said:**
> Hola. Instale Firestart para poder compartir la coneccion a internet.
Yo recibo la internet por Wi-Fi y quiero compartirla con otra PC via ethernet.

Instale el Firestart y no logro arrancar el firewall.
El primer error que me tiro fue:



Esto lo logre solucionar, pero ahora me tira otro error:



Este ya no lo pude corregir y no se que hacer. Intente solucionarlo con algo similar a como corregi el primer error pero no tuve existo.

Alguna idea?
El Firestarter no es ni inicia el firewall.

El firewall esta siempre activo, tenga o no reglas definidas porque es parte del kernel.

Firestarter es una interfaz grafica para configurarlo.

Para poder compartir el acceso a Internet deberias contar con dos placas de red. Una conectada a Internet, con IP publica, y la otra conectada a la otra PC o a un switch, formando una LAN.

La otra PC debe estar en la misma red que la que oficia de gateway/pasarela. Si no, nunca se va a conectar.

Antes de empezar a configurar Firestarter deberias tenes el tema red resuelto. Firestarter no lo hace por vos, solo permite definir reglas iptables.

---

### Post by DrKenobi on 2009-06-09
ok, voy a armar primero a red interna entonces

gracias!

---

