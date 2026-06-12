---
title: "Problemas con reproductores de video en ubuntu"
date: 2008-12-28
forum: Software
---

### Post by lsp on 2008-12-28
Soy absolutamente nuevo con este sistema operativo y no se pa donde agarrar. Todo me resulta complicado (microsoft se encarga de eso) y por hábito hasta quiero volver a lo viejo. Pero no, espero acostumbrarme y solucionar mis problemas. Cada vez que pongo un dvd a reproducir,ya sea totem, gxine, xine, ogle, vlc, mplayer y no recuerdo cual mas, se congela en algun momento la imagen y luego sigue reproduciendo normalmente hasta que vuelve a pasar lo mismo. Estuve averiguando y vi que hay mucha gente con problemas de reproducción, ¿puedo solucionarlo?, ¿cómo? Les agradecería mucho una mano

---

### Post by guillermolisi on 2008-12-28
> **lsp said:**
> Soy absolutamente nuevo con este sistema operativo y no se pa donde agarrar. Todo me resulta complicado (microsoft se encarga de eso) y por hábito hasta quiero volver a lo viejo. Pero no, espero acostumbrarme y solucionar mis problemas. Cada vez que pongo un dvd a reproducir,ya sea totem, gxine, xine, ogle, vlc, mplayer y no recuerdo cual mas, se congela en algun momento la imagen y luego sigue reproduciendo normalmente hasta que vuelve a pasar lo mismo. Estuve averiguando y vi que hay mucha gente con problemas de reproducción, ¿puedo solucionarlo?, ¿cómo? Les agradecería mucho una mano
Que version de Ubuntu estas usando ?

Que marca y modelo de placa de sonido tenes ?

Cuanta memoria RAM posee la maquina ?

Que procesador tiene ?

---

### Post by lsp on 2008-12-28
Acá te paso los datos que me pediste. Estoy dudando si puede ser un problema de la placa de video porque antes de tener ubuntu, con windows me estaba pasando lo mismo, se congelaba la imagen en reproducción. Además sucede lo mismo sea un dvd o un archivo de video guardado en mi computadora. En fin, estos son los datos:
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 79
model name	: AMD Sempron(tm) Processor 3200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy
bogomips	: 2009.01
clflush size	: 64
power management: ts fid vid ttp tm stc

Mi versión de ubuntu es la 8.10 intrepid ibex, mi memoria ram de 1.4 g, mi placa de video  nVidia Corporation GeForce 6100 nForce 405 (rev a2) y la de sonido  MCP61 High Definition Audio. Espero poder solucionarlo y muchas gracias. 
Cualquier irregularidad en el uso del foro por favor señálenmela, es la primera vez que participo en uno.

---

### Post by faktorqm on 2008-12-29
Hola, tenes compiz fusion activado? Intentaste desactivarlo a ver que pasa?
Instalaste los drivers de nvidia? los libres o los privativos?
Parece ser un problema exclusivo de la compu, si en otro sistema operativo tambien pasa lo mismo... pero con esa compu no deberias tener problemas. Salu2!

---

### Post by lsp on 2008-12-29
Muchas gracias viejo, desinstalé el compiz fusion y probé una película durante veinte minutos y no se me congeló la imagen. Voy a probar de ver una par y te confirmo finalmente si no me surge el mismo problema. Igual muchísimas gracias.

Lisandro

---

### Post by lsp on 2008-12-30
Probé con una película entera y se congeló la imagen en menor cantidad de veces y la duración de la imágen congelada fu menor. Ya saqué el compiz y el compiz fusion (plugins estras y plugins main) y parece ser que por ahí va la cosa, si quito otros compiz ¿esto puede alterar el funcionamiento y la resolución de las ventanas y no modificar mi problema con la reproducción de videos?
Muchas gracias.

---

### Post by faktorqm on 2008-12-30
Puede ser, lo segundo que probaria yo es dejar un solo motor, vos tenes el motor xine y el gstreamer. Agarra todos los paquetes del reproductor que uses que digan xine e instalalos y desinstala todos los que digan gstreamer, o al reves, por ejemplo, tenes totem-xine y totem-gstreamer entonces tenes que elegir. NO ES LO MISMO QUE DESINSTALAR LOS CODECS GSTREAMER, son dos cosas distintas, la cosa es el reproductor o programa que uses para ver, los codecs dejalos como estan.
Yo particularmente no uso compiz fusion y tengo todo en xine y uso vlc y nunca un drama. Tengo los codecs gstreamer instalados y todo marcha viento en popa.
Conta como te fue, salu2!

---

### Post by lsp on 2009-01-05
Cómo hago para desinstalar el paquete xine o gstreamer del reproductor vlc? Por terminal, por el gestor sinaptyc, por añadir y quitar? No sé cómo hacerlo y no me aparecen paquetes xine o gstreamer  cuando busco en el vlc. Qué hago?
Gracias

---

### Post by Hei Ku on 2009-01-05
A través de Synaptic

---

### Post by ramiro_md on 2009-01-07
Nooo, para no desinstales nada !! :S ami me pasa lo mismo, desactiva compiz cuando veas la pelicula, deja mateacity. Creo que desde consola es: metacity --replace. A mi me sirvió así. Un saludo y suerte.

---

### Post by lsp on 2009-01-09
El compiz fusion ya lo había sacado antes y parecía mejorar la cosa pero sólo un poco. Vos decís que saque todos los compiz desde sinaptyc? Probé lo de metacity --replace desde terminal y no me funcionó. 
Estoy empezando a creer que puede ser un problema de la configuración de la placa de video porque las ventanas cuando las abro y a veces mientras las uso se ven con errores. Agradezco las opiniones.

---

### Post by ramiro_md on 2009-01-09
Lsp tarta de volver a instalar compiz y dejalo todo como estaba antes, e instala fusion-icon:
```
 sudo aptitude install fusion-icon 
``` 
y desde fusion-icon cambiar el gestor de ventanas. Te digo xq tenés mi misma placa de video =) yo lo solucioné de ese modo (a la hora de ver pelis cambio a metacity) haceme caso. Un saludo y suerte

---

### Post by lsp on 2009-01-10
Volví a instalar el compiz fusion como antes e instalé el fusion icon. Cuando vea la peli voy al fusion icon a donde dice select window manager y elijo metacity? Creo que así me dijiste; si da resultado te aviso. Muchas gracias che.

---

### Post by ramiro_md on 2009-01-10
Claro, ni más ni menos que así. A mi me funciona, esperemos que  te pase lo mismo je. Un saluudo.

---

### Post by lsp on 2009-01-12
Sigo con el mismo problema. Capaz que se sobrecalienta la placa de video y con un ventilador lo resuelvo; así resolví un problema de reinicio constante que tenía. Muchas gracias igual Ramiro.

---

### Post by ramiro_md on 2009-01-12
Que extraño, bueno intenta eso que decis, espero que tengas suerte. Un saludo.

---

