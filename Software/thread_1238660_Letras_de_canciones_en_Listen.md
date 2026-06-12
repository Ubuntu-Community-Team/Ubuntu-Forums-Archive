---
title: "Letras de canciones en Listen"
date: 2009-08-12
forum: Software
---

### Post by xc36e on 2009-08-12
Hola. Queria hacerles una pregunta.
EStoy usando (y con muy buenos resultados) el reproductor Listen.
Pero la verdad me es sumamente incapaz de encontrarme la mayoria de las letras de las canciones. Por mas que cambie de servidores, ninguno tiene la cancion (y aclaro que tampoco es nada de otro mundo, estoy hablando de la renga por ejemplo, alguna banda internacional, etc) 

No saben si hay forma de agregar distintos servidores? y cual se podria agregar. 

Gracias

---

### Post by pablo.s on 2009-08-12
Te paso los servidores que
aparecen en el plugin de letras
de Rhythmbox:

Astraweb: astraweb.com
Lyrc: lyrc.com.ar
Leo's Lyrics: leoslyrics.com
LyricWiki: lyricwiki.org

---

### Post by josecuervo86 on 2009-08-12
Las del plugin de songbird son estas:

[http://lyricplugin.com](http://lyricplugin.com)
[http://lyricwiki.org](http://lyricwiki.org)

La busqueda la hace asi (por las dudas)
```

var req = new XMLHttpRequest();

  if (lm_webLoc == "LWIKI"){
    var url = "http://lyricwiki.org/api.php?artist=" + escape(artist) + "&song=" + escape(track) + "&fmt=text";
           }

  if (lm_webLoc == "LPLUGIN"){
    var url = "http://www.lyricsplugin.com/plugin/?title=" + escape(track) + "&artist=" + escape(artist);
           }
```

---

### Post by matias_tati on 2009-08-12
> **josecuervo86 said:**
> Las del plugin de songbird son estas:

[http://lyricplugin.com](http://lyricplugin.com)
[http://lyricwiki.org](http://lyricwiki.org)

La busqueda la hace asi (por las dudas)
```

var req = new XMLHttpRequest();

  if (lm_webLoc == "LWIKI"){
    var url = "http://lyricwiki.org/api.php?artist=" + escape(artist) + "&song=" + escape(track) + "&fmt=text";
           }

  if (lm_webLoc == "LPLUGIN"){
    var url = "http://www.lyricsplugin.com/plugin/?title=" + escape(track) + "&artist=" + escape(artist);
           }
```

Disculpa se que no tiene nada que ver con el tema pero como hago para que el Songbird muestre las caratulas automaticamente, por ej. en winamp nombraba el archivo jpg con el nombre del album y me lo detectaba, en rythimbox le ponia de nombre cover. Pero en songbird? Gracias....

---

### Post by guillermolisi on 2009-08-12
> **matias_tati said:**
> Disculpa se que no tiene nada que ver con el tema pero como hago para que el Songbird muestre las caratulas automaticamente, por ej. en winamp nombraba el archivo jpg con el nombre del album y me lo detectaba, en rythimbox le ponia de nombre cover. Pero en songbird? Gracias....
Matias

Como bien dijiste, no tiene nada que ver con el asunto de este hilo/thread, asi que te pido por favor que abras uno nuevo con tu consulta, si es que ya no fue resuelta con anterioridad.

---

### Post by josecuervo86 on 2009-08-12
En songbird podes poner que te las busque en last.fm. Despues voy a ver si reviso el codigo y encuentro como las obtiene, de paso me desburro un poco.

Pd: guille, no alcance a ver tu post, my bad

---

### Post by xc36e on 2009-08-14
Gracias por las respuestas.
Pero la verdad nose como agregar los servidores a la lista.
Si alguien ah usado Listen se dara cuenta q al escuchar una cancion, si en un servidor no la encuentra puede buscar en los otros. Cosa que muchas veces funciona, pero se que hay mejores servidores donde nunca hay problema.

Ademas hay algo que no entiendo:
Al encontrar la letra de la cancion Listen la guarda en una carpeta llamada Lyrics. PERO nunca la levanta desde ahí. sino q siempre la busca desde el servidor, asi q no le encuentro funcionalidad a descargar la letra para no usarla. ES más, existe una opcion que se llama "MODO DESCONECTADO". Lo logico seria que al buscar la letra primero la levante desde el rigido, pero no es así, sino que (elijas el servidor que elijas) te pone la inscripcion "MODO DESCONECTADO" y nada mas..
Esta bien, entiendo que sirve para otras cosas pero lo veo algo inutil en ese sentido..

Retomando un poco el tema:
¿alguien sabe si se le pueden agregar plugins a Listen? Porque solo puedo usar los que hay en la lista y nada mas.. 
¿En donde estan los archivos de listen? nose donde esta guardado.. o como hago para fijarme?

Bueno gente un saludo y espero no agobiarlos demaciado :P

---

### Post by josecuervo86 on 2009-08-14
La verdad, no se como funcionara listen, pero si hay una opción para guardar las letras, debe haber otra para cargarlas.

En cuanto a los archivos de listen, seguramente estan en tu Home, pero ocultos. Anda a tu carpeta personal y apreta

```
**Ctrl** + **H**
```

Eso te va a mostrar los archivos ocultos.La carpeta seguramente se llama **.Listen**

---

