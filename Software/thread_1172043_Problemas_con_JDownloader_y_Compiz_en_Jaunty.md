---
title: "Problemas con JDownloader y Compiz en Jaunty"
date: 2009-05-28
forum: Software
---

### Post by santiagoward2000 on 2009-05-28
Hola gente.
Nuevo problema. Desde que instalé Jaunty, casi siempre que abro el JDownloader con Compiz activado, Compiz deja de funcionar, la pantalla empieza a titilar y todo empieza a andar re lento por un rato. Después, todo empieza a andar mejor, pero se ve con errores.
Me pasaba con la versión vieja, y hoy bajé la nueva a ver si se solucionaba, pero parece que no. ¿A alguien más le pasa? ¿Se puede hacer algo (aparte de apagar compiz cada vez que quiero usar JDownloader)?
Saludos!

---

### Post by staar on 2009-05-28
te pasa solo con JDownloader?, o también con otros programas java?

saludos

PD: para reemplazar JDownloader por algo más livianito y evitar java, podés probar Tucan, que es GTK, no tiene tooodas las cosas que tiene JDownloader, pero anda bien...

---

### Post by jorgea.garciav on 2009-05-28
Les cuento que tengo el mismo problema en Intrepid Ibex y JDownloader.  Al final se desactiva el Compiz.  Estos problemas surgieron después de la última actualización que hice de JDownloader, antes de eso todo funcionaba sin problemas.

---

### Post by santiagoward2000 on 2009-05-28
> **staar said:**
> te pasa solo con JDownloader?, o también con otros programas java?

saludos

PD: para reemplazar JDownloader por algo más livianito y evitar java, podés probar Tucan, que es GTK, no tiene tooodas las cosas que tiene JDownloader, pero anda bien...

Ahora no estoy usando ningún otro programa con Java, pero voy a probar ese Tucan. Supongo que ese debe ser el problema.
Gracias!

---

### Post by santiagoward2000 on 2009-06-09
> **staar said:**
> te pasa solo con JDownloader?, o también con otros programas java?

Después de que en otro thread se moncionara el BlueMarine (hecho en java) como alternativa para el F-Spot, lo estuve probando, y no me hizo nada raro con Compiz. Revisé entonces el script que usa para correrlo, me acuerdo que en algún momento usé eso para correr programas Java con Compiz, pero que después lo había arreglado y no hacía falta. ¿Tendrá algo que ver?

> **staar said:**
> para reemplazar JDownloader por algo más livianito y evitar java, podés probar Tucan, que es GTK, no tiene tooodas las cosas que tiene JDownloader, pero anda bien...

Lo estuve probando, y está bastante bueno. Le falta la opción de reconectar, y soporte para otras páginas (como youtube), pero me gusta. Por lo menos tengo una alternativa si no puedo hacer andar el JDownloader.
Saludos!

---

### Post by Mister X on 2009-06-09
con que JRE estas usando JDownloader?, con la de Sun o con la abierta, yo con la abierta no tengo problemas

---

### Post by guisheca on 2009-06-09
Yo tengo kubuntu jaunty (KDE 4.2.4) de 64 bits y con el java que te instala cuando le das al ubuntu-restricted-extras. Mas allá de que kde tiene kwin y que se yo, corro compiz en él. Y tengo el último jdownloader instalado mediante el script jd.sh.
To esto corre perfectamente bien todo junto, ni problemas de rendimiento, ni sobrecargas ni nada por el estilo.

---

### Post by santiagoward2000 on 2009-06-09
> **Mister X said:**
> con que JRE estas usando JDownloader?, con la de Sun o con la abierta, yo con la abierta no tengo problemas

Estoy usando la de Sun. Lo más raro es que lo probé en mi laptop, que tiene Xubuntu pero con Compiz, y ahí anda perfecto. Las dos placas de video son NVidia, ¿tendrá algo que ver con el modelo de placa? (nVidia Corporation GeForce 8400 GS)

---

### Post by NickCis on 2009-06-09
Que es eso de la vercion libre de java?.
Debe ser un bug del compiz con el java, en Ubuntu 8.04, yo no podia usar el menu de configuracion con el compiz activado.

Saludos.

---

### Post by pablo.s on 2009-06-09
La version [libre]("http://openjdk.java.net/") de Java.

---

### Post by NickCis on 2009-06-09
Perdonen por el Offtopic:
Y que ventajas / desventajas (en funcionalidad, no las ya obvias por ser libre) con respecto al java de sun?.

---

### Post by pablo.s on 2009-06-09
Supuestamente ofrece la misma
performance que la versión
cerrada. Sun está haciendo una
transición hacia el código abierto
porque la beneficia en calidad,
no en dinero. Además quiere
conservar a los desarrolladores
para que no se vayan detrás de
otros lenguajes.

---

### Post by NickCis on 2009-06-09
Es recomendable usar la vercion abierta?.
Se instala dsd los repositorios?.

---

### Post by pablo.s on 2009-06-09
> **NickCis said:**
> Es recomendable usar la vercion abierta?.
Se instala dsd los repositorios?.

Yo recomiendo usar lo que
uno le sirva. A mi me sirve
cualquiera de las dos 
versiones pero por una 
posición ideologica elijo
la de código abierto (Si
puedo elegir, claro está)

Se puede instalar de los 
repositorios, está en main.

[COLOR="DarkGreen"]**sudo apt-get install open-jdk-6-jre**[/COLOR]

---

### Post by Mister X on 2009-06-10
> **NickCis said:**
> Que es eso de la vercion libre de java?.
Debe ser un bug del compiz con el java, en Ubuntu 8.04, yo no podia usar el menu de configuracion con el compiz activado.

Saludos.

yo hace un tiempo tenia el problema con un programa en java de que me mostraba las ventanas en blanco cuando estaba compiza activado, pero con la version libre de la JRE me andaba correctamente (o con la de Sun, honestamente no me acuerdo), la cuestion es que con una andaba bien y con la otra mal...

ahora anda bien con las 2

pero uso la libre:D

---

### Post by Xion19 on 2009-06-16
tenia exactamente el mismo problema lo acabo de solucionar instalando la version libre de java ahora anda sin ningun problema.
si no sabes como googlea un toque que dice por todos lados como instalarla.
saludos! espero que te  sirva va en realidad me sirvio a mi porque ya me estaba poniendo mal con que no me andaba el jdownloader

---

### Post by metaladicto1 on 2009-07-16
Perdón si el post es antiguo.

A mi también me pasaba lo mismo, por mas q bajase la versión compilada o con el jd.sh, compiz se descontrolaba y terminaba por des-configurarse totalmente y no veia ninguna forma de repararlo x mas q desisntalara completamenet compiz ............ y unica solucion, instalar todo de nuevo para recuperar compiz.

Una alternativa q se me ocurrio fue desactivar compiz desde compiz fusion icon seleccionando Metacity en el menu select windows manager, y luego de ello jdownloader corrio normal, luego de ello desactive todos los complementos inutiles del jdowloader [visuales] y todo arreglado , volvi a activar compiz y todo funciona de maravilla.

Aclarando que no es un problema de java, pues realizo programas en java y este en jaunty no me ocasiona ningun proble, y a mi parecer el problema se origina en compiz al no soportar sus efectos visuales.

Unas capturas para verificar que funciona correctamente:

[http://www.fotazas.com/Jdowloader-en-jaunty-1606](http://www.fotazas.com/Jdowloader-en-jaunty-1606)

[[IMG]http://www.fotazas.com/fotos/t/711571247747966.png[/IMG]]("http://www.fotazas.com/Jdowloader-en-jaunty-1606")

[http://www.fotazas.com/Jdowloader-en-jaunty-1614](http://www.fotazas.com/Jdowloader-en-jaunty-1614)

[[IMG]http://www.fotazas.com/fotos/t/552651247757818.png[/IMG]](http://www.fotazas.com/Jdowloader-en-jaunty-1614)

---

