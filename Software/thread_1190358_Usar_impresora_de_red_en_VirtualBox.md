---
title: "Usar impresora de red en VirtualBox"
date: 2009-06-17
forum: Software
---

### Post by leosr on 2009-06-17
Hola.
Tengo en la PC Ubuntu Jaunty y uso VirtualBox con WinXP... la idea es que desde la VM pueda ver la red (conectada por un router ADSL) y poder usar impresoras conectadas vía ethernet. Tengo una impresora Oki C5200n, la cual no es soportado por Ubuntu, con interfaz usb y ethernet. Conectada vía usb funciona sin problamas desde el Win virtualizado, pero si conecto la impresora por ethernet directamente no la registra. La idea es que pueda usar esta impresora y en un futuro una fotocopiadora Ricoh con conexión ethernet/postcrip. 
Estuve googleando pero lo que encontré resultó muy técnico para mis conocimientos de redes. Si alguien sabe como hacer que el Win virtualizado tenga acceso a la red, por favor que me lo explique paso a paso...

Aclaración: la VM tiene acceso a internet vía NAT. Uso VirtualBox 2.2.4, no la versión de los repos (versión OSE).

Gracias!

---

### Post by guillermolisi on 2009-06-17
> **leosr said:**
> Hola.
Tengo en la PC Ubuntu Jaunty y uso VirtualBox con WinXP... la idea es que desde la VM pueda ver la red (conectada por un router ADSL) y poder usar impresoras conectadas vía ethernet. Tengo una impresora Oki C5200n, la cual no es soportado por Ubuntu, con interfaz usb y ethernet. Conectada vía usb funciona sin problamas desde el Win virtualizado, pero si conecto la impresora por ethernet directamente no la registra. La idea es que pueda usar esta impresora y en un futuro una fotocopiadora Ricoh con conexión ethernet/postcrip. 
Estuve googleando pero lo que encontré resultó muy técnico para mis conocimientos de redes. Si alguien sabe como hacer que el Win virtualizado tenga acceso a la red, por favor que me lo explique paso a paso...

Aclaración: la VM tiene acceso a internet vía NAT. Uso VirtualBox 2.2.4, no la versión de los repos (versión OSE).

Gracias!
Si la impresora tiene interface Ethernet, entonces podes asignarle una IP.

Si esto es asi, asignale una direccion IP que este en la misma red que la maquina virtual y el host, asi la deberias poder usar desde Win y desde Ubuntu (aqui tengo mis reparos por lo que comentaste antes sore la falta de soporte para esta impresora en Linux).

Tambien tenes que asignarle la misma mascara de red que tienen las otras maquinas.

Con esos datos deberias poder configurarla desde Win.

---

### Post by leosr on 2009-06-18
> **guillermolisi said:**
> Si la impresora tiene interface Ethernet, entonces podes asignarle una IP.

Si esto es asi, asignale una direccion IP que este en la misma red que la maquina virtual y el host, asi la deberias poder usar desde Win y desde Ubuntu (aqui tengo mis reparos por lo que comentaste antes sore la falta de soporte para esta impresora en Linux).

Tambien tenes que asignarle la misma mascara de red que tienen las otras maquinas.

Con esos datos deberias poder configurarla desde Win.

Hola. Te muestro en un pantallazo los datos de red del Win virtulizado y Ubuntu. Qué ip tendría que asignar a la impresora?

---

