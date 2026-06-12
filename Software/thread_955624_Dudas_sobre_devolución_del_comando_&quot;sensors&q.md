---
title: "Dudas sobre devolución del comando &quot;sensors&quot;"
date: 2008-10-22
forum: Software
---

### Post by guisheca on 2008-10-22
Mi duda es con el tema de las temperaturas, tengo un procesador AMD athlon 64 X2 y no se porque aparecen 4 temperaturas tal como muestro mas abajo. Encima al final de la cita aparece una nueva lectura de CPU.
La pregunta es: ¿a que corresponde cada lectura? ¿a cual le tengo que prestar atención?
Esto esto viene a que ya empiezan las altas temperaturas típicas de la época y sobre todo de mi región (Chaco), por lo que siempre me mantengo alerta a las lecturas de temperaturas. Pero no quisiera poner 4 sensores en el escritorio, por lo tanto quiero saber cual de las 4 (ó 5) temperaturas son las que importan.
Saludos.

```
 _________________________________________
/ La ley es una telaraña que detiene a   \
| las moscas y deja pasar a los pájaros. |
|                                         |
\ -- Anacarsis.                           /
 -----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
guillermo@DeLorean:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +16.0°C                                    
Core0 Temp:   +7.0°C                                    
Core1 Temp:  +18.0°C                                    
Core1 Temp:   +5.0°C                                    

f71882fg-isa-0600
Adapter: ISA adapter
3.3V:        +3.42 V
Vcore:       +1.30 V  (max =  +2.04 V)   
Vdimm:       +2.26 V
Vchip:       +1.84 V
+5V:         +5.17 V
12V:        +10.37 V
5VSB:        +3.49 V
3VSB:        +3.44 V
Battery:     +3.31 V
CPU:        3080 RPM
System:        0 RPM  ALARM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +24.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
System:        FAULT  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

```

---

### Post by faktorqm on 2008-10-24
Bueno, yo le daria bola solo al que dice CPU abajo. Busqué por que, y obviamente sólo me topé con kilos y kilos de documentacion sobre lmsensors y sus amigos, la verdad que es una masa el programa ese.
La cosa es que requiere modulos, y configuraciones especiales si tu mother no esta soportada por la configuracion por defecto digamos. 
El programa lo que hace es preguntarle a los integrados (fisicos) de la mother que hacen, a que temperatura estan trabajando, a que tension, etc.
Acá en el faq responden por que ves tantas temperaturas si tenes un solo micro, [http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3), y mil cosas mas.
La documentacion esta en [http://www.lm-sensors.org/wiki/Documentation](http://www.lm-sensors.org/wiki/Documentation) y bueno, nada, te esperan un par de horas de lecturas, yo lo lei por que estaba bueno no mas jajaja. El sitio es [http://www.lm-sensors.org/](http://www.lm-sensors.org/) como ya te habras dado cuenta xD Salu2!!!

---

### Post by guisheca on 2008-10-24
Excelente lectura para el fin de semana jejejeje muchísimas gracias faktorqm.
Por cierto, gracias por los saludos a mi blog!! ayer recién lo leí porque askimet me tomo tu coment como spam (??) y ayer lo encontré

---

### Post by faktorqm on 2008-10-24
ahh grosso, no se por que no aparecia en el blog y pense que era por el opera, o por el blog q no andaba, o por algo. Salu2!!

---

### Post by luks911 on 2008-10-24
Aaaaaaahhhhhh, empiezo a entender por qué tengo dos temperaturas con un Sempron :lolflag:

---

### Post by faktorqm on 2008-10-25
Bien ahi! vos venis a la release party?

---

### Post by luks911 on 2008-10-26
Uuuuuuuuuyyyyyyyy me re colgué y no pasé por el hilo, perdón por si la pregunta era para mí. Supongo que sí porque Guisheca es de Chaco. No creo que pueda ir por el horario de mi laburo y porque vivo demasiado en el conurbano. Creo que me la vuelo a perder:icon_frown:

---

### Post by faktorqm on 2008-10-27
Si era para vos, el se va a ver a Ricardo... jajaja
Dale copate que nos vemos las caras dos veces al año no mas no seas ortiva!! todos nos tenemos que levantar temprano al otro dia... aparte los viernes... ¿quien labura? Salu2!

---

### Post by niko_3100 on 2008-10-27
luks911 porque tenes dos temperaturas con un sempron?? yo tengo un sempron 3600+ de una notebook y tambien me marca dos temperaturas, sabes por que es?? igual yo uso mas la temperatura que me marca el conky, aunque creo que la de sensors es mas real pero varian solo 2 o 3 grados entre ellas... pero no se porque me aparece otra temp.

---

### Post by luks911 on 2008-10-27
> **faktorqm said:**
> Si era para vos, el se va a ver a Ricardo... jajaja
Dale copate que nos vemos las caras dos veces al año no mas no seas ortiva!! todos nos tenemos que levantar temprano al otro dia... aparte los viernes... ¿quien labura? Salu2!

Es que salgo de laburar a las 22 y encima empezé a calcular horarios de subtes, trenes y demases, pero caí en la cuenta de que es el jueves y el viernes tengo un curso a la mañana y me levanto a las 6. ¡Me quiero matar! :mad:

> **niko_3100 said:**
> luks911 porque tenes dos temperaturas con un sempron?? yo tengo un sempron 3600+ de una notebook y tambien me marca dos temperaturas, sabes por que es?? igual yo uso mas la temperatura que me marca el conky, aunque creo que la de sensors es mas real pero varian solo 2 o 3 grados entre ellas... pero no se porque me aparece otra temp.

En realidad es una sola temperatura vista dos veces. No uso lm-sensors sino libsensors, aunque supongo que debe pasar lo mismo: la configuración de estos "medidores" está preparada por defecto para dos procesadores, entonces aunque tengamos uno nos da dos datos, en realidad, un dato duplicado. Al menos eso entendí de las FAQ de lm-sensors. De hecho, ambos dicen usar un archivo de configuración desde el que se podría cambiar eso (/etc/sensors.conf) pero no lo tengo :confused: En fin.

Con el sensors-applet, en las preferencias, desmarqué uno de los falsos procesadores y listo. 

Saludos

---

