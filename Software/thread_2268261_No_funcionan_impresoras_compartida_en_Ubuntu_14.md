---
title: "No funcionan impresoras compartida en Ubuntu 14"
date: 2015-03-07
forum: Software
---

### Post by evilside2 on 2015-03-07
Estimados

Les comparto un descubrimiento, uso Ubuntu 14 LTE en varios computadores, varios de estos tienen conectadas impresoras por USB que luego comparten para imprimir desde otros computadores con Windows y/o Ubuntu.

El asunto es que sólo funciona la primera impresión desde otros computadores, luego no imprime más. Lo más extraño es que los logs de Cups muestran que recibieron la solicitud de impresión y que la página salió correctamente.

Bueno, la solución es agregar esta linea al archivo /etc/lightdm/lightdm.conf

session-setup-script = /etc/init.d/cups restart

Con esto el servicio se reinicia cada vez que un usuario inicia sesión y mágicamente las impresiones ya salen.

---

