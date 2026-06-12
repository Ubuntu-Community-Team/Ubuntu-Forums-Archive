---
title: "nesecito ayuda en ubuntu hardy heron!!!"
date: 2008-08-09
forum: Software
---

### Post by darkarcangel_sam on 2008-08-09
miren tengo el siguiente problema en ubuntu hardy heron 8.04.1 :


 " No se ha podido inicializar la información de los paquetes

 Ha ocurrido un problema imposible de corregir cuando se inicializaba la    información de los paquetes.

 Por favor, informe de ésto como un fallo en el paquete «update-manager» e  incluya el siguiente mensaje de error:

'E:Tipo 'universe' desconocido en la línea 16 de lista de fuentes /etc/apt/sources.list, E:No se pudieron leer las listas de fuentes.'

alguien me puede decir que puedo hacer??
 de antemano gracias

---

### Post by pol666 on 2008-08-10
agregaste repositorios?

---

### Post by [P]oli on 2008-08-10
Tenés que editar el **/etc/apt/sources.list** y mostrarnos los que dice en la línea 16, para editarlo 
```
sudo gedit /etc/apt/sources.list
```
Si esa línea la agregaste vos, borrala y después hacé un 
```
sudo apt-get update
```
Seguro se arregla

---

### Post by darkarcangel_sam on 2008-08-10
muchas gracias me sirvio tu consejo poli

pero ahora cuando quiero instalar algo me sale el siguiente mensage :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


aver si me pueden ayudar y disculpen las molestias , es q apenas llevo 2 dias probando ubuntu

de antemano gracias

---

### Post by darkarcangel_sam on 2008-08-10
c me olvidaba , y cuando le doy ese comando me dice q no tengo los permisos nesesarios xq no soy superusuario o algo asi

---

### Post by faktorqm on 2008-08-10
el comando es: ```
sudo dpkg --configure -a
```

comentario al margen: Alguien de aca iba a hacer el tutorial sobre como buscar en el foro nuestro, incluidas las palabras clave... que paso con eso? parece que hay MUCHA gente que lo necesita! si nadie lo hizo lo voy a tener que hacer yo....

---

### Post by darkarcangel_sam on 2008-08-10
si , ese comando ya lo escribi , pero me dice q no tengo los pernmisos suficientes para modificarlo
 q nesecito ser superusuario o algo asi , nesecito solucinarlo , xq no puedo instalar nada
 de antemano gracias , y disculpen las molestias

---

### Post by faktorqm on 2008-08-10
PRESTA ATENCION FLACO! copia y pega ese comando en la consola y mete la contraseña que metes cuando prendes la compu.

---

### Post by darkarcangel_sam on 2008-08-10
gracias x la ayuda , me sirvio tu clave  faktorqm, es q la estaba escribiendo mal o algo , 
peo ya funciono 

Gracias

---

### Post by darkarcangel_sam on 2008-08-10
jajajaja , pero ahora tengo otra cosa , cmo puedo instalar las actualizaciones , 
xq cuando le doy instalar actualizaciones nomas c queda ahi y la ventana c pone color gris , pero ps ni instala nada

quisiera saber si me pueden decir como , 
tengo una coneccion de 56 k/s
Gateway 545 mx
prosesador intel p 4
tecnologia ht
memoria ram de 1.5 Gb

usuario ubuntu 60563
dede hace 2 dias

---

### Post by [P]oli on 2008-08-10
probaste reiniciando?

---

### Post by faktorqm on 2008-08-10
mmm me parece que tu tema es la conexión, que como es de 56 kbps capaz se corta, o sufre cortes mientras va bien, o sea, no por que tu conexión sea mala, sino por que a veces los paquetes se pierden y demas y tenes que reenviarlos, y se pierden los reenvios, y asi. 
Lo que podes hacer es bajarte en lo de algun amigo/conocido o quien sea que tenga ubuntu los paquetes y mandarlos a un cd mediante la instalacion de un programa que se llama "apt on cd" (en realidad no se si se sigue desarrollando, si no que alguien le diga como es el "nuevo metodo" :P)
salu2!

---

### Post by victor_nesta on 2008-08-11
De paso cañazo pregunto. 
Y si hoy bajara el DVD de Hardy por Torrent. 
No incluiría tanto los aplicativos como las actualizaciones?
Si es para putearme no lo hagan ponga !#@ y listo :)

---

### Post by Hei Ku on 2008-08-11
No te va a incluir las ultimas actualizaciones. La version que debe estar es la 8.04.1, que es bastante cercana, pero no tiene lo último.

---

### Post by faktorqm on 2008-08-11
y aparte bajarse un dvd por torrent con 56 kbps? cuando lo termine de bajar ya va a ser "jardy jeron" jajajaja como se va a llamar la version de despues de II alguien sabe? tiene que ser algo con "JJ" salu2!

---

### Post by sajnox on 2008-08-12
JJ, se que venia con un Jaguar pero no sabria como adjetivarlo

---

