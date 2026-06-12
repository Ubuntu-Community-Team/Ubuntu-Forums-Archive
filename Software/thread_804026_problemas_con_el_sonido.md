---
title: "problemas con el sonido"
date: 2008-05-22
forum: Software
---

### Post by alcapone42 on 2008-05-22
Hola, a todos, buen mi primer post jejeje.
el problema es el siguiente: yo tengo unos auriculares plantronics dsp500 (ficha usb), los conecto y me los reconoce, entro en el sonido y pongo la opcion de los plantronics y la musica la escucho subo bajo el volumen, ahora el tema es cuando juego un warcraft 3 o veo algun video en youtube o cuando quiero ver la tele por internet , no tengo sonido, pero la imagen SI la tengo osea el plugin que necesita el firefox lo tengo, pero el sonido no me lo da = que en los juegos. alguien sabra porque???? alguna solucion?????(demas esta decir que todo esto en windows lo puedo hacer)

---

### Post by osensei on 2008-05-22
Tenés alguna otra placa de sonido en la máquina? Aunque sea onboard?

En ese caso... probaste a ver si se escucha en la otra placa?

---

### Post by alcapone42 on 2008-05-22
si tienen placa onboard, lo que pasa que los auriculares estos traen placa de sonido incorporada y NO tengo parlantes entonces cuando los auris se conectan automaticamente anulan la otra y andan los auris

---

### Post by osensei on 2008-05-22
> **alcapone42 said:**
> si tienen placa onboard, lo que pasa que los auriculares estos traen placa de sonido incorporada y NO tengo parlantes entonces cuando los auris se conectan automaticamente anulan la otra y andan los auris

Sería bueno que verifiques si cuando no lo escuchás, como por ejemplo en youtube o en los juegos, si no está saliendo por la otra placa. Si tenés unos auriculares comunes enchufalos en la onboard para ver si en ese caso está sonando por ahí.

Por otro lado probá de instalar el paquete libflashsupport, ya sea desde Synaptic Package Manager, o desde la consola con el siguiente comando

```
sudo apt-get install libflashsupport
```

Y fijate si se soluciona el sonido en el flash.

---

### Post by alcapone42 on 2008-05-22
instale ese programa por la terminal y listo, ya puedo escuchar del youtube, muchisimas gracias

---

### Post by osensei on 2008-05-22
Buenísimo!

En cuanto a lo de los juegos, probá de hacer lo siguiente. En la terminal escribí
```
asoundconf list
```

Ahí debería listarte las dos placas de sonido. Después de eso poné el siguiente comando reemplazando "placausb" por el nombre de la placa exactamente igual a como apareció en el listado.

```
asoundconf set-default-card placausb
```

Ahora fijate si te funciona, si no te funciona de una probá de cerrar y volver a iniciar sesión, pero no creo que sea necesario.

---

### Post by alcapone42 on 2008-05-22
listo ai puse : asoundconf list, me tiro,
 Names of available sound cards:
Intel
Headset
i ai puse: asoundconf set-default-card Headset
 ahora lo pruebo

---

### Post by osensei on 2008-05-22
Tengo curiosidad... funcionó?

---

### Post by alcapone42 on 2008-05-22
si, funciono xD

---

### Post by osensei on 2008-05-23
Buenísimo :)

---

### Post by Simbiosys on 2008-06-05
Pude solucionar el mismo problema con este post... gracias!!!

---

