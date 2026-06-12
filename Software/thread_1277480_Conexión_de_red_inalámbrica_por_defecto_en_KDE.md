---
title: "Conexión de red inalámbrica por defecto en KDE"
date: 2009-09-28
forum: Software
---

### Post by electronpositivo on 2009-09-28
Estoy probando en KDE 4.2.2 y no consigo configurar una red inalámbrica con wep para que se conecte automáticamente con cualquier usuario.

¿Es posible configurar la conexión para que conecte globalmente con cualquier usuario, incluso antes de loguearse?

---

### Post by Hei Ku on 2009-09-28
Tenés que usar el Wicd. Si estas usando el networkmanager de Kubuntu, no anda.
El wicd te reemplaza el networkmanager y anda muy bien, con algunas particularidades.

---

### Post by electronpositivo on 2009-09-28
Lo tengo! Gracias ;-)

---

### Post by Applelnx on 2009-09-28
Hola, instalo el wicd asi nomas? Tengo que desinstalaer el default network manager? 
Como es el tema de los drivers con este programa, vienen incluidos o los tengo que bajar/sacar de windows?

---

### Post by josecuervo86 on 2009-09-28
No se como sera el tema de los drivers, pero al instalar Wicd, automaticamente desinstala Network-manager

---

### Post by Hei Ku on 2009-09-28
Los drivers son independientes. Si te reconocia la placa wifi con el networkmanager, te la tendría que reconocer con el wicd.

Y sí, cuando instalas el WiCD te desinstala el networkmanager. Son mutuamente excluyentes.

---

### Post by Applelnx on 2009-09-29
Muchas gracias! :)

---

### Post by guillermolisi on 2009-09-29
> **Applelnx said:**
> Muchas gracias! :)
Anduvo ? Solucionado ?

---

### Post by Applelnx on 2009-09-30
> **guillermolisi said:**
> Anduvo ? Solucionado ?

Realmente yo no era el de la pregunta original. Mi pregunta era solo para informarme porque estaba pensando en cambiar el network manager (que me funciona) pero para probar el wicd.

---

### Post by guillermolisi on 2009-09-30
> **Applelnx said:**
> Realmente yo no era el de la pregunta original. Mi pregunta era solo para informarme porque estaba pensando en cambiar el network manager (que me funciona) pero para probar el wicd.
Ups, tenes razon. Me despisto el agradecimiento :)

Bueno, vale la pregunta para el que origino el thread con este tema.

---

### Post by josecuervo86 on 2009-09-30
> **electronpositivo said:**
> Lo tengo! Gracias ;-)

Ponele [SOLVED] nomás guille ;)

---

### Post by Applelnx on 2009-10-10
Desde el KPackit no me dejaba hacerlo.
Con la consola poniendo

```
sudo aptitude install wicd
```

se instala todo automaticamente.

Ahora, el wifi con wicd me funciona mal...
Con la red cableada todo bien, pero con el wifi se desconecta cada 2 segundos, no se por que. Alguno tuvo este mismo problema?

---

### Post by guillermolisi on 2009-10-10
> **Applelnx said:**
> Desde el KPackit no me dejaba hacerlo.
Con la consola poniendo

```
sudo aptitude install wicd
```se instala todo automaticamente.

Ahora, el wifi con wicd me funciona mal...
Con la red cableada todo bien, pero con el wifi se desconecta cada 2 segundos, no se por que. Alguno tuvo este mismo problema?
Recuerdo algunos threads aqui o en la lista de soporte de Ubuntu-ar que hablaban sobre conexiones inestables con sintomas similares al tuyo.

El Newtork Manager en Kubuntu 9.04 funciona mal por no decir que no funciona. Asi que fijate que no este interfiriendo intentado conectar via WiFi (se supone que cuando instalas Wicd desinstala NM).

Luego, dado que podriamos estar a nivel de drivers, creo que el tema da para abrir un thread nuevo especifico en la seccion Hardware. Si lo abris, de entrada nomas mostra la salida de "lspci" y "lsusb" ademas de "uname -s" asi tambien tenemos la version de kernel que estas usando. Todo esto siempre que no encuentres una solucion buscando con "Search this forum" y un patron que sea marca y/o modelo de tu interface wifi.

---

### Post by Applelnx on 2009-10-10
Hola, guillermo. El Network-manager aparece desinstalado, asi que buscare en el foro y de ultima abro un thread nuevo. Gracias!

EDIT: reinstale el network-manager sacando el wicd y volvio a la normalidad. Saludos :)

---

