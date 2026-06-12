---
title: "Problemas con GDM y X"
date: 2009-04-05
forum: Software
---

### Post by bolchevique on 2009-04-05
Tengo una maquina en la que instale Ubuntu 9.04. Todo muy bien, hasta anoche que dejo de arrancar la X


me aparece el login, pongo usuario y contraseña. se queda un segundo y me muestra una pantalla con un error que dice

"Ya existe un servidor X en ejecución en la pantalla :0. Desea intentar otro número de pantalla? Si responde no, GDM volvera a intentar iniciar el servidor en :0 otra vez. (puede intercambiar consolas pulsando contro...."   bla bla bueno ahi me explica como cambiar de consola


Cualquiera de las alternativas da error. El otro problema que me parece raro es que si voy a tty1 ingreso el usuario y la pass. NO INICIA... me vuelve a pedir usuario y pass.. y así siempre.......


La única manera de ingresar a la consola fue en "safe mode" (ahi me deja ejecutar la consola como root).
También ahí hice pruebas de checkear el disco, reconfigurar x-server, liberar espacio (hay como 5 gigas libres en realidad). También intente iniciar con startx pero apenas arranca me da un error y se tilda.

ah.. también probe con dpkg-reconfigure gdm y nada...

A alguien le pasó?? en internet vi varios con el mismo problema en LENNY. Pero no veo soluciones a ese problema.

Habilite al usuario ROOT y me da el mismo error.

También es preocupante que no puedo loguearme en la consola con el usuario por defecto. Ingreso las credenciales y me vuelve a pedir login. si las ingreso mal. me dice login incorrecto, pero si las ingreso bien, me vuelve a pedir login :S

---

### Post by clasificado on 2009-04-05
Siempre que tuve un problema raro fue porque se me había acabado el espacio en disco (maldito bittorrent)

fijate co un ```
df
```

clasificado

---

### Post by bolchevique on 2009-04-06
> **bolchevique said:**
>  liberar espacio (hay como 5 gigas libres en realidad). 

lo controle a eso, y hay suficiente espacio libre..


La verdad no logre encontrar solución alguna... esta noche lo reinstalo :) 


si resguardo el /home; instalo nuevamente, instalo los programas y reemplazo el /home por el que tenia antes. 

Funciona todo?

---

