---
title: "Avisar a las teminales del apagado del servidor"
date: 2010-11-03
forum: Software
---

### Post by Brath-ga on 2010-11-03
Hola a tod@s.
Tengo una red compuesta por un servidor en Linux y tres terminales con XP.
He programado el apagado del servidor con "cron" y el comando: shutdown -h +2 "Servidor apagándose", para dar tiempo a los terminales a cerrar sus programas.
El caso es que me gustaría que en los terminales se abriese una ventanita tipo pop-up avisando del tiempo que falta para que se desconecte, al igual que el aviso que me sale en la consola del servidor donde se ejecuta el shutdown.
Alguien sabe como puedo conseguir esto?
Gracias anticipadas.

---

### Post by alfplayer on 2010-11-04
Se puede sincronizar los tiempos de las terminales con el tiempo del servidor, y programar una tarea en los windows con algún comando que permita abrir un pop-up con el aviso.

---

### Post by juancarlospaco on 2010-11-04
```
net rpc shutdown -U [COLOR="Blue"]administrador[/COLOR] -I [COLOR="blue"]172.16.0.256[/COLOR] -t [COLOR="blue"]120[/COLOR] -f -C [COLOR="blue"]Vas_a_ser_desconectado_de_la_Matrix[/COLOR]
```

Lo que esta en Azul varia segun tus necesidades...

-U es usuario con privilegios, -I es la IP, -t es tiempo del Pop-Up en Segundos,
-C es el mensaje del Pop-Up, podes agregar -r si queres que reinicie en vez de apagar.

Esto es Samba basicamente.

---

### Post by alfplayer on 2010-11-04
Brath-ga: Hay que apagar los terminales también?

---

### Post by juancarlospaco on 2010-11-04
ah..., yo interprete que los queria apagar, bueno, eso apaga o reinicia, 
que es lo que necesita hacer?, bajar las interfaces de red? o que?

---

### Post by alfplayer on 2010-11-04
> **juancarlospaco said:**
> ah..., yo interprete que los queria apagar, bueno, eso apaga o reinicia, 
que es lo que necesita hacer?, bajar las interfaces de red? o que?

Yo estaba pensando en cortar las conexiones entra aplicaciones, como OO.org con Samba (como para grabar documentos) u otras cliente/servidor. Mejor que lo aclare.

---

### Post by Brath-ga on 2010-11-05
Gracias por vuestras respuestas.
Veo que no me expliqué correctamente.
Tengo programado el apagado del servidor, pero solo el servidor, para una hora determinada.
Pretendo que cuando se vaya a apagar se abra en cada terminal activo un pop-up con el aviso de que el servidor se va a apagar.

La orden que tengo en el crontab es esta:
```
30 22 * * *  shutdown -h +2  "Servidor apagándose"
```

---

### Post by alfplayer on 2010-11-05
Mi sugerencia anterior es una posibilidad. Si el período de espera es de varios minutos no habría necesidad de sincronizar los tiempos. También se podría hacer por red con algún sistema como winexe.

---

### Post by juancarlospaco on 2010-11-05
Es que..., toda red local seria conveniente que este sincronizada con un NTP server, digo...

Podes usar LinPopUp, se comunica via WinPopUp *(servicio de Mensajeria de windows)*

---

### Post by alfplayer on 2010-11-05
> **juancarlospaco said:**
> Es que..., toda red local seria conveniente que este sincronizada con un NTP server, digo...

Si las aplicaciones y los usuarios no necesitan precisión... aunque es fácil de configurar y no causa problemas.

---

### Post by Brath-ga on 2010-11-05
Estoy intentando bajarme linpopup y veo que no está en los repositorios.
Leí googleando que no es compatible con la 9.10 y si con la 9.04, pero yo estoy con la 10.04 y me da errores de dependencias.
Tendré que bajarme las depedencias a pelo como antiguamente o existe algun .deb completo?
Alguien me puede asegurar que funciona en Ubuntu 10.04?
Gracias de nuevo por vuestra ayuda.

---

### Post by Brath-ga on 2010-11-06
Imposible instalar linpopup.
Al aumentarle a la 10.04 los repositorios de Jaunty, casca la sources.list.

---

