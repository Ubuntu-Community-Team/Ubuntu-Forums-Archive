---
title: "[SOLVED] Como cambiar ip?"
date: 2008-08-14
forum: Software
---

### Post by victor_nesta on 2008-08-14
simple en guindows usaba este scrip para cambia mi ip.
> 
ipconfig
ipconfig /release "local"
netsh interface ip set address name="local" source=static addr=126.0.0.11 mask=255.0.0.0 
netsh interface ip set address name="local" source=dhcp
ipconfig
ipconfig /renew "local" 
pause

como se hace en linux?

Aclaro antes que me puteen. hice man ipconfig. Pero termino desorientado :S

---

### Post by faktorqm on 2008-08-14
por consola: ```
ifconfig eth0 IP netmask MASCARA up
```
(no se si va con sudo adelante)
graficamente: sistema -> administracion -> red

---

### Post by victor_nesta on 2008-08-15
Gracias! así de fácil es?
pensé que se complicaba mas y me dio cuiqui tocar. Puedo probar lo que sea menos la conexión, ya que si esta me quedo en bo .
Gracias!

---

