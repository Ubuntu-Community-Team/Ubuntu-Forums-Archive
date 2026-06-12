---
title: "Restaurar la imagen cargando (boot splash)"
date: 2009-09-09
forum: Software
---

### Post by apohlo on 2009-09-09
Hola un saludo, mi problema es que la imagen cargando del Ubuntu 9.04 no aparece cuando arranca , me aparece solo texto pero luego si aparece la imagen de login y todo normal, esto ocurrio luego de que instale un tema y luego lo elimine y no se como restaurla o cambiarla el otro problema es que no tengo conexin a internet , no existira alguna forma manual para restaurarla...??
grax de antemano.

---

### Post by robertor on 2009-09-10
en el /boot/grub/menu.lst debieras tener una entrada como esta:
```

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            708fb8d5-013a-4bd0-8741-cbe22aa32bea
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=708fb8d5-013a-4bd0-8741-cbe22aa32bea ro **quiet splash**
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

```

Énfasis hago en lo que esta en negrita.
Eso es lo que hace en condiciones normales aparezca el splash de cargando.

Saludos!
Roberto

---

### Post by apohlo on 2009-09-11
gracias por tu ayuda te cuento que si he configurado el menu.lst para otras cosas, pero podrias ser mas especifico...??

---

### Post by Carlos C on 2009-09-11
robertor te está diciendo qué parámetro debe aparecer para que el splash se haga visible. ¿Qué es lo que no te parece específico? Creo que está bastante claro.

---

### Post by apohlo on 2009-09-11
Mira este es parte de mi menu.lst parece que esta igual...??
 
[html]title  Ubuntu 9.04, kernel 2.6.28-11-generic
uuid     35113046-2999-4d64-a420-c4677c71f2b7
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=35113046-2999-4d64-a420-c4677c71f2b7 ro quiet splash 
initrd   /boot/initrd.img-2.6.28-11-generic
quiet
[/html]

---

### Post by AlexDDR on 2009-09-11
podrias probar reinstalando los paquetes 

usplash
y usplash-theme-ubuntu

ya que yo he tenido esos problemas anteriormente, pero solo con la version de 32bit, pero no he podido restaurarlo 100% de hecho cuando lo generaba apagaba bien pero al encender, mostraba la carga de el logo por unos segundos, pero luego se iba a modo texto hasta la carga del GDM para el login del usuario, eso es lo que te ocurre??

se supodene que la instalacion de esos paquetes deberia hacer el initrd para regargar el splash, pero resulta que si no esta bien seteada la resolucion de inicio no va  a cargar.

Bueno trata reinstalando esos paquete y si no tendras que meter los comando a mano 

saludos

---

### Post by apohlo on 2009-09-11
grax por la respuesta, en ningun momento se carga ninguna imagen todo va al modo texto ,como digo al inicio todo andaba bien hasta que instale y quite un tema,.... mira es algo tribial pero el problema es que tengo que hacer una expo sobre ubuntu y es algo importante para mi que se observe el logo de ubuntu cargando.....

---

### Post by AlexDDR on 2009-09-11
y reinstalaste los paquete usplash y el otro en synaptic??


puedes probar tambien en synaptic desinstalar completamente y debpues volver a instalar. Y mientras se instalan axpandir la caja de consola con el triangulito y ver si dice algun problema, porque tambien los puedes instalar por consola con apt-get asi se puede ver mejor ya que puede ser un problema de resolucion tambien 

Si ves en synaptic tambien hay otors uplash themes esta el de debia, kubuntu etc , prueba instalando alguno de esos en vez de el clasico de ubuntu, por si hay alguna respuesta

saludos

---

### Post by nopersona on 2009-09-12
Creo que con starupmanager se puede restarurar el splash o dejarlo como verbose mode.

---

### Post by apohlo on 2009-09-14
grax pero no se logra cambiar, ya he tratado con ese y otro programas mas....alguien me da otra solución..?

---

### Post by kamus on 2009-09-14
> **apohlo said:**
> grax pero no se logra cambiar, ya he tratado con ese y otro programas mas....alguien me da otra solución..?

Después de instalar el tema ejecutaste sudo update-initramfs –u ?

Saludos

---

### Post by apohlo on 2009-09-15
no lo hice solo lo instale atraves de apariencia instalar.....

---

