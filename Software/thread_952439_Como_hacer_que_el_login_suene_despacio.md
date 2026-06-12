---
title: "Como hacer que el login suene despacio"
date: 2008-10-19
forum: Software
---

### Post by victor_nesta on 2008-10-19
La cuestión es la siguiente, tomen lápiz y papel:
Cuando uno inicia Ubuntu y sale el cartelito del Login, suena ese especie de redoblante, cuando nos logeamos suenan los bombos y demás cosas que todos conocemos haciéndonos saber que entramos en ubuntu.

Muy bien, prendí la maquina a las 5 de la tarde, escuche musica al palo y cuando se hizo la noche, tranquilito sin hacer ruido seguí trabajando, reinicio el sistema y... Me olvido de bajar el volumen de los parlantes (que estaban al palo desde las 5 de la tarde), ¿y que paso? El vecino salio con la escopeta pensando que el redoblante era un chorro que se le había colado en el techo.

En fin, luego de esta hermosisima historia que os acabo de contar, pregunto.

¿Se puede configurar el volumen de los sonidos del login?

Saludos y Gracias.

---

### Post by Mauro22 on 2008-10-19
Es muy temprano, y lo unico que se me ocurre es editar el archivo y bajarle un par de dB.


O en su defecto sacarlo.

---

### Post by luks911 on 2008-10-19
> **victor_nesta said:**
> La cuestión es la siguiente, tomen lápiz y papel:
Cuando uno inicia Ubuntu y sale el cartelito del Login, suena ese especie de redoblante, cuando nos logeamos suenan los bombos y demás cosas que todos conocemos haciéndonos saber que entramos en ubuntu.

Muy bien, prendí la maquina a las 5 de la tarde, escuche musica al palo y cuando se hizo la noche, tranquilito sin hacer ruido seguí trabajando, reinicio el sistema y... Me olvido de bajar el volumen de los parlantes (que estaban al palo desde las 5 de la tarde), ¿y que paso? El vecino salio con la escopeta pensando que el redoblante era un chorro que se le había colado en el techo.

En fin, luego de esta hermosisima historia que os acabo de contar, pregunto.

¿Se puede configurar el volumen de los sonidos del login?

Saludos y Gracias.

Estoy en la misma desde hace tiempo. Pero no afecta sólo el sonido del inicio sino el volumen en general. Como dice Mauro, opté por sacarlo. Y para el resto de los sonidos agregué
```
alsactl restore
```
para que se ejecute al inicio desde Sesiones. No sé si es lo mejor, pero funciona. Claro que no para el sonido de login, que es previo a eso. En fin.

---

### Post by MeduZa on 2009-01-06
podrias probar con amixer de alsatools desde linea de comandos, ponerlo en algun archivo de arranque del sistema uqe baje el volumen antes de entrar y si queres despues del login que lo suba de nuevo (a gusto y piachere)

y la otra es matar al vecino (?)

---

### Post by staar on 2009-01-06
[desvirtuar] jaja, killall vecino :P [/desvirtuar]

q algun mod borre esto, por favor :oops:

---

### Post by M_NUS on 2009-01-06
desactivarlo seria la opcion mas coherente 

off: tus parlantes deben medir como la puerta de tu alcoba y tenes 5 o tu vecino tiene las orejas de superman o utiliza algun prototipo de los de sprayette ajajjjaaj

---

### Post by MeduZa on 2009-01-07
> **M_NUS said:**
> desactivarlo seria la opcion mas coherente 

off: tus parlantes deben medir como la puerta de tu alcoba y tenes 5 o tu vecino tiene las orejas de superman o utiliza algun prototipo de los de sprayette ajajjjaaj

es ned flanders

---

