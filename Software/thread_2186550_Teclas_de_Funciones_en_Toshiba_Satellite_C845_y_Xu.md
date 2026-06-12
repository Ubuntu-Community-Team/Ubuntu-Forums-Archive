---
title: "Teclas de Funciones en Toshiba Satellite C845 y Xubuntu 13.04"
date: 2013-11-07
forum: Software
---

### Post by Pablo_D._Kromn on 2013-11-07
Hola gente, tengo una Notebook Toshiba Satellite C845, se que esta marca tiene problemas de reconocimiento con el tema de las teclas función (Fn) y con algunas otras cosas mas (Tarjeta Inalambrica (Rtl8188)). Mi problema es que arranco la maquina y no me funcionan las teclas Fn + F2, F3, F4, F5, F12; supe solucionar el tema del brillo asignándole a la tecla Win + F2 y F3 la función para que incremente (xbacklight -inc 10%) y decremente (xbacklight -dec 10%) el brillo; el tema es que hay veces que empieza a funcionar las teclas de función que no me funcionaban, o sea anda por completo Fn + F1 a F12.
Busque por todos los logs, googlee y no encuentro el cambio.
Si me pueden decir donde puedo ver ese cambio, o que archivos o comandos ver, les agradecería mucho!

Saludos

---

### Post by Pablo_D._Kromn on 2013-11-15
Solucionado el problema, instale Ubuntu 13.10, luego de instalar agregue en /etc/default/grub dentro de las comillas de la linea 
GRUB_CMDLINE_LINUX="" 


lo siguiente 
"acpi_osi=Linux acpi_backlight=vendor" 


quedando 
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"


Reinicie y no funcionaba, luego probe agregando a
/etc/modprobe.d/blacklist.conf


la linea
blacklist toshiba_acpi


Reinicio y empezaron a andar las teclas de funcion, me queda por instalar Xubuntu 13.10 y probar lo mismo que hice.


Tambien estuve viendo y probando que Ubuntu 13.10 la placa de red rtl8188 funciona bien.


Saludos

---

### Post by ezakto on 2014-05-20
Me registré solamente para decirte que sos un grande! Tengo una Satellite L840, y tenía un problema casi idéntico. El blacklist toshiba_acpi arregló todo! No encontraba la solución en ningún lugar!
Gracias!

---

### Post by noid2 on 2014-05-24
Tenia el mismo problema en Manjaro y lo de blacklist tochiba_acpi fue lo unico que lo arregló. No existe en ningun otro lado la solución.

Mil gracias! Sos groso. Sabelo.=d>=d>

---

