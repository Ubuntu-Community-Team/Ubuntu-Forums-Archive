---
title: "[COMOs] Instalar Jdownloader"
date: 2009-05-24
forum: Software
---

### Post by NickCis on 2009-05-24
Bueno, dsp de usar la guia que esta en la pagina de Ubuntu-ar y ver que el Jdownloader no andaba correctamente, use el script que te sugiere la pagina de Jdownloader. Paso a explicar como se debe instalar.

Primero, Jdownlaoder requiere Java Runtime Enviroment (jre/jdk) 1.5 or superior. Lo instalamos con estos comandos en terminal:
```
sudo apt-get update
sudo apt-get -udV sun-java6-jre
sudo apt-get install sun-java6-jre
```

Despues descargamos el script de la pagina de JDownloader.
Link: [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh)
Si no vallan a la seccion de descargas del Jdownloader ( [http://jdownloader.org/download](http://jdownloader.org/download) ) y bajo la parte de linux esta el script.

Pueden abrir el script (con cualquier editor de textos), para modificar la carpeta donde lo instala. Por defecto lo va a instalar en  ~/.jd

Para ejecutar el script debemos agregarle permisos de ejecucion:
(estando en la carpeta donde bajaron el archivo)
```
sudo chmod +X jd.sh
```

Y despues ejecutan el archivo:
```
./jd.sh
```

Con esto instalara, actualizara al Jdownloader.
Si quieren agregarlo al menu, haganlo como dice el Como de Ubuntu-ar acerca de Jdownloader ( [http://ubuntu-ar.org/node/210](http://ubuntu-ar.org/node/210) ), pero en donde dice command o comando, pongan:
```
/carpeta/./jd.sh
```
Donde carpeta es la ruta donde esta el archivo que usaron para instalar el Jdownloader.

Saludos.

Edit: Si tienen Cablemodem, para usar el reconnect pueden usar esta guia: [http://taringa.net/posts/linux/1645302/Descargar-de-Rapidshare-y-Megaupload---Ubuntu.html](http://taringa.net/posts/linux/1645302/Descargar-de-Rapidshare-y-Megaupload---Ubuntu.html)
El problema que plantea esa guia es que como ejecuta el jdownloader el cambiador de Ip si no tiene derechos de administrador. La mejor solucion es hacer un script con el siguiente comando "gksudo cambiarip", y qe el jdownloader ejecute ese script como reconector de Ip. Siempre que se haga la primera reconneccion nos pedira la clave de administrador, pero para las demas no.

---

### Post by emiliano_raso on 2009-05-24
Y que hace la aplicacion? :-S

---

### Post by pablo.s on 2009-05-24
Descarga archivos de Rapidshare
y demás cuevas.

---

### Post by emiliano_raso on 2009-05-24
> **pablo.s said:**
> Descarga archivos de Rapidshare
y demás cuevas.

Pero eso lo bajas con los web browser... o baja mas rapido? o sea... evita las limitaciones de velocidad que te imponen?

---

### Post by pablo.s on 2009-05-24
Permite listas de bajadas.
Si por ejemplo encontrás
en algún antro la lista de
todos los episodios de la
primera temporada de Lost
en 720p en 400 pedazos
de 100 MB, es muy util.

---

### Post by emiliano_raso on 2009-05-24
> **pablo.s said:**
> Permite listas de bajadas.
Si por ejemplo encontrás
en algún antro la lista de
todos los episodios de la
primera temporada de Lost
en 720p en 400 pedazos
de 100 MB, es muy util.

Apa... interesante. Gracias che...

---

### Post by santiagoward2000 on 2009-05-24
Además tiene unas cuantas opciones bastante útiles.
[LIST=1]
[*]En páginas como Rapidshare normalmente te hacen esperar un rato después de cada bajada, dependiendo de tu IP. Este programa tiene una opción para desconectar y reconectarte a internet cuando termina una parte, cosa de que (si no tenés una conexión de IP fija), te cambie el IP y no tengas que esperar.
[*]Si son muchas partes en rar, las junta y descomprime automáticamente.
[*]Y como dijo Pablo, es más cómodo armar la lista que andar haciendo click uno por uno. Acá copias todas las direcciones juntas, las agregás y el programa se fija qué son y si los archivos siguen disponibles. Si está todo bien se arma la lista, y te podés ir tranquilo a hacer otra cosa
[/LIST]
Saludos!

---

### Post by pol666 on 2009-05-25
> **santiagoward2000 said:**
> Además tiene unas cuantas opciones bastante útiles.
[LIST=1]
[*]En páginas como Rapidshare normalmente te hacen esperar un rato después de cada bajada, dependiendo de tu IP. Este programa tiene una opción para desconectar y reconectarte a internet cuando termina una parte, cosa de que (si no tenés una conexión de IP fija), te cambie el IP y no tengas que esperar.
[*]Si son muchas partes en rar, las junta y descomprime automáticamente.
[*]Y como dijo Pablo, es más cómodo armar la lista que andar haciendo click uno por uno. Acá copias todas las direcciones juntas, las agregás y el programa se fija qué son y si los archivos siguen disponibles. Si está todo bien se arma la lista, y te podés ir tranquilo a hacer otra cosa
[/LIST]
Saludos!

Tambien baja galerias de fotos, videos de youtube, te plancha y te lleva los pibes al colegio.

---

### Post by NickCis on 2009-05-25
Sii,,, tambien le podes tirar los links con texto en el medio (a veces los encontras numerados o con fotos) y te los toma igual xD...

---

### Post by guillermon on 2009-07-21
Bien! Por fin lo pude volver a hacer funcionar! Con el comando java, etc no funcionaba.

   Gracias...

---

### Post by dnovai on 2009-08-13
Exelente post!

Por fin corre de maravilla JDownloader!

Gracias

---

### Post by erickelrojas on 2010-05-11
Hola acaban de salir los repositorios para Jdownloader, en mi web he echo un manual breve para instalar Jdownloader [http://www.elleonplateadodeojosrojos.es/blog/repositorios-internet/](http://www.elleonplateadodeojosrojos.es/blog/repositorios-internet/)
...y al ser desde repositorios se instala todo lo que hace falta y no falla, lo he probado tanto en 32 bits como 64 bits y va bien.

---

