---
title: "problema con el make"
date: 2011-05-12
forum: Software
---

### Post by ryu_hunter on 2011-05-12
hola, estaba compilando con make y me salio esta salida en la terminal:

jimmy@jimmy-EasyNote-MX45:~/ipwraw-ng$ make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.35-28-generic/build M=/home/jimmy/ipwraw-ng modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-2.6.35-28-generic»

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/jimmy/ipwraw-ng/ipwraw.o
/home/jimmy/ipwraw-ng/ipwraw.c:43: fatal error: net/ieee80211.h: No existe el fichero o el directorio
compilation terminated.
make[2]: *** [/home/jimmy/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/jimmy/ipwraw-ng] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-2.6.35-28-generic»
make: *** [modules] Error 2

que es este error??? como puedo repararlo, o como puedo terminar de compilar lo que quiero?????
gracias

---

### Post by silex89 on 2011-05-14
Te falta una librería para hacer la compilación.


Has instalado el compilador para Ubuntu?, puede que eso sea lo que te falte.

El compilador es una serie de librerías que te permiten convertir el código de fuente en ejecutables (programas usables). En Ubuntu se instala poniendo en la terminal:

```
sudo apt-get install build-essential
```


Infórmanos cómo evoluciona el problema ;)

---

### Post by ryu_hunter on 2011-05-15
gracias por responder!!!

y bueno, si instale el essencials.........

aun no consigo solucionar mi problema...

---

