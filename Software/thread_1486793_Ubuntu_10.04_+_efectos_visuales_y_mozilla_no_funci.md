---
title: "Ubuntu 10.04 + efectos visuales y mozilla no funciona correctamente"
date: 2010-05-18
forum: Software
---

### Post by eliux on 2010-05-18
Hola a todos, tengo un problema muy particular:
 Cuando activo los efectos visuales de la apariencia de Ubuntu 10.04 mozilla empieza a tener problemas con la carga de videos y aplicaciones en flash, en cambio chrome no me da estos problemas.

 Ejemplo. con los efectos visuales de Ubuntu DESACTIVADOS, entro a alguna pagina para ver un video online y carga todo perfecto  (ejemplo los videos de megavideo) pero en cuanto activo los efectos visuales y entro a ver el mismo video le doy al play, el boton hace su respeciva animacion cuando lo pulsan pero no reproduce el video sino que el boton vuelve a su estado anterior. Solo me pasa en mozilla firefox (lo mismo me pasa con videos de youtube, si tengo los efectos visuales activos no puedo pausarlos ni interactuar con las opciones como adelantar, pantalla completa etc. clic y no pasa nada)

Desactivo efectos visuales y mozilla funciona de maravilla!

Tengo una placa de video geforce 8600 de XFX y ubuntu 10.04, todo actualizado y con los driver recomendados de ubuntu habilitados.

Espero que alguien pueda ayudarme! =D

---

### Post by eliux on 2010-05-18
Bueno me auto respondo:
 
 La solucion no la prove aun, apenas llegue a mi casa lo intento, busque y busque y encontre algo:
 
 
 Problema: flash player no funcionan botones de las animaciones cuando activo los efectos visuales de ubuntu
 
 El problema radica que ubuntu 64bit baja el flash player de 32 o algo asi y anda como el traste, lo que hay que hacer es desinstalar todo lo referente a flash player y para ello hacemos lo siguiente:
 
desde un terminal
sudo apt-get remove flashplugin-nonfree nspluginwrapper 

esto desisntala el flash
 
luego bajamos desde [COLOR=red][AQUI]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")[/COLOR] la version 64
DESCOMPRIMIMOS
y lo copiamos al siguiente directorio con el siguiente comando
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

 
si funciona posteo los resultados
 
FUENTE: [http://www.ubuntu-es.org/?q=node/127056](http://www.ubuntu-es.org/?q=node/127056)

---

### Post by eliux on 2010-05-19
Si funciono de maravilla, el problema esta en flash y ubuntu de 64 bit.


Una recomendacion, si estan por instalar una desktop con ubuntu y no saben si 64 o 32, por el momento recomiendo 32 bit funca mucho mas rapido y no tiene tantos problemas, las versiones 64 para DESKTOP estan un poco verdes!

---

