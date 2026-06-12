---
title: "Webcam con emesene"
date: 2009-10-28
forum: Software
---

### Post by anarko on 2009-10-28
> **luks911 said:**
> Fijate que más arriba la cámara fue probada con gstreamer-properties y funciona. El problema es con el emesene.

Hay Hay Hay tenes razon,mil perdones, sabes que lei todo el Th viendo si habia logrado probar la camarita y lo pase por alto, = ami me gusta mas el cheese porque despues me cuelgo con los efectos :)

Je Je Ya que estamos me prendo a ver si me explican como hacer andar la camarita con el emesene, ya tengo instalado libmimic la camarita andando ( probada con cheese :p ) en las opciones del emesene la puedo seleciconar y me aparece el preview, pero despues cuando la quiero usar, osea enviar video desde el emesene no hace nada, vuelvo a las propiedades y no esta seleccionada la camarita.
Osea cuando un contaco requiere ver mi camara aparece la ventanita de preview, pero sin imagen y la otra persona no ve nada le dice que no se peude conectar.

Desde ya muchas gracias.

---

### Post by luks911 on 2009-10-28
Todo bien.
La verdad es que teniendo libmic0 y python-libmimic instalados debería funcionar. Todavía no lo probé. Prometo hacerlo ni bien pueda.
Para sumar otro dato, ¿qué versión de emesene tenés? La última es la 1.5, disponible en repositorios "oficiales" desde Karmic y en Jaunty agregando este[0].

[0] [https://launchpad.net/~bjfs/+archive/ppa](https://launchpad.net/~bjfs/+archive/ppa)

---

### Post by anarko on 2009-10-28
emesene 1.5.1 - awesome, bajado del svn, actualizado hace 1h, version obtenida : 2002

---

### Post by luks911 on 2009-10-30
Perdón por la demora. 
Finalmente pude probarlo y funciona. Tengo la versión 1.5 de los repositorios de Karmic (instalada en Ubuntu en 9.10, claro), con el paquete python-libmimic instalado. Probé enviar mi cámara, incluso estando como no conectado, a una máquina con Jaunty y aMSN, y recibió el video sin problemas.

---

### Post by Leandro17 on 2009-11-02
> **luks911 said:**
> Perdón por la demora. 
Finalmente pude probarlo y funciona. Tengo la versión 1.5 de los repositorios de Karmic (instalada en Ubuntu en 9.10, claro), con el paquete python-libmimic instalado. Probé enviar mi cámara, incluso estando como no conectado, a una máquina con Jaunty y aMSN, y recibió el video sin problemas.

Yo tengo instalado el paquete python-libmimic pero no funciona la camara, en cheese se ve bien, pero para usarlo en el emesene me pasa lo mismo que lo habian escrito arriba pero la luz indicadora no se prende cuando pongo para usar la cam en el chat, pero si en cheese...

tengo ubuntu kk, y el emesene 1.5... la notebook es una compaq presario cq50 111la, nose cual es el modelo de la camara

---

### Post by luks911 on 2009-11-02
> **Leandro17 said:**
> Yo tengo instalado el paquete python-libmimic pero no funciona la camara, en cheese se ve bien, pero para usarlo en el emesene me pasa lo mismo que lo habian escrito arriba pero la luz indicadora no se prende cuando pongo para usar la cam en el chat, pero si en cheese...

tengo ubuntu kk, y el emesene 1.5... la notebook es una compaq presario cq50 111la, nose cual es el modelo de la camara

Si funciona en Cheese, no es problema de la cámara.
En el Emesene andá a Options > Preferencias y con las flechas de arriba movete hacia la derecha hasta la última pestaña, que es Webcam. Ahí hay un menú desplegable para seleccionar la cámara, al elegirla debería encenderse. Si hacés eso, ¿qué pasa?

---

### Post by Leandro17 on 2009-11-02
La selecciono pero en el preview que esta en preferencias no muestra nada

---

### Post by luks911 on 2009-11-02
Qué raro. Si la cámara funciona y tenés instalados los paquetes necesarios, debería funcionar. No se me ocurre qué pueda ser.
Sé que no es la idea, pero también podés probar el aMSN, que tiene la misma función.

---

