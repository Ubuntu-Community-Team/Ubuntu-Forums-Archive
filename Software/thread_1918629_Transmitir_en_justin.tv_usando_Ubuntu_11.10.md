---
title: "Transmitir en justin.tv usando Ubuntu 11.10"
date: 2012-02-01
forum: Software
---

### Post by ogonzaleslara on 2012-02-01
Hola ...les comento que recién hace unas semanas instalé Ubuntu 11.10 en mi laptop. 
 
El problema es que al loguearme a la pagina de justin.tv... y darle clic al botòn "Transmite en vivo!"... lo que debería aparecer es la pantalla para darle "permitir"...y pues luego configurar el video y el audio. Pero esta pantalla no aparece...sólo me aparece el mensaje "You can't start until you click allow below."..pero ningún botón para cliquear el "permitir" .
 
Pensé que era un problema del Adobe Flash Player...pero no tengo problemas para ver video en youtube ni nada parecido.
 
Las características de mi laptop son las siguientes: Toshiba Satellite C645-SP4135L Memoria RAM: 3GB, Procesador: Intel Core i3-2310M 2.10GHz x 4 Disco duro: 320GB
 
Gracias te antemano por la ayuda.
Saludos!! Orlando

---

### Post by granjero on 2012-02-01
hola, yo tuve muchos problemas para transmitir por ustream.tv y el problema fue el flash aunque se veían videos perfectamente por youtube, vimeo etc. no lograba transmitir...

Fijate que [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html) en esta página hay versiones viejas de flash. Creo que con la versión 10.2.152 me funcionó.

Desisntalé por completo flash-plugin-installer y flash-nonfree desde synaptic.

Descomprimí el archivo flashplayer.so y lo copié a /usr/lib/mozilla/plugins y listo.

Ojalá te sirva.

Salud.

---

### Post by mama21mama on 2012-02-01
Puedes transmitir desde la terminal

[Con este metodo.]("http://blog.mamalibre.com.ar/content/stream-nativo-en-linux-con-justin-y-vlc")

---

