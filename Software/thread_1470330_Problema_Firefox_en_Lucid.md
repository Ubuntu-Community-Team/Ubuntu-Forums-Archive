---
title: "Problema Firefox en Lucid"
date: 2010-05-02
forum: Software
---

### Post by aledruetta on 2010-05-02
No entiendo qué pasa con Firefox en Lucid. Mantengo una página web y ahora que actualicé a Lucid la veo toda despelotada. Bueno, pensé que yo estaba con algún problema en el código, entonces instalé Opera, Chrome y Chromium. Ahí anda todo bien. Y en Karmic también, el problema es en la versión 3.6.3 de Lucid, creo.

Concretamente, las div se ven fuera de lugar se pierde buena parte del estilo css cuando comprimo con gzip.

¿A alguien le está pasando algo parecido?

---

### Post by hictio on 2010-05-02
Qué fuente estás usando?
Tenés activada la opción en el Firefox que "permite que las páginas usen sus propias fuentes", en lugar de las fuentes que vos usás?

---

### Post by aledruetta on 2010-05-02
Estoy usando font-family: "lucida grande", "lucida sans", verdana, sans-serif;

Y sí, esa opción que vos decís está activada por defecto.

Ahora ¿eso puede afectar tanto al layout de la página?

Por ejemplo, una div con una imagen y nada de texto, aparecer completamente desplazada a la derecha, casi fuera de la pantalla.

Y por otro lado, el problema con la hoja de estilo comprimida en formato gzip.

¿será?

---

### Post by hictio on 2010-05-02
Qué página en particular es?
Podrías postear un screenshot?

---

### Post by aledruetta on 2010-05-02
> **hictio said:**
> Qué página en particular es?
Podrías postear un screenshot?

Bueno, ahí subí a un subdominio de prueba la hoja de estilo comprimida con gzip y la home para que veas cómo queda. En el dominio principal está sin compresión y más parecida a cómo debería verse.

[URL="http://www.bancodeprova.epyks.com.br/"]
[/URL]

---

### Post by alfplayer on 2010-05-03
Se me ve igual a la segunda captura con Fedora 13 con Firefox 3.6.3. Probablemente es un problema de la página.

---

### Post by aledruetta on 2010-05-03
> **alfplayer said:**
> Se me ve igual a la segunda captura con Fedora 13 con Firefox 3.6.3. Probablemente es un problema de la página.

Gracias Alfplayer,
¿Probaste con otro navegador o con otra versión de Firefox?

---

### Post by sitiomatic on 2010-05-03
Parece un problema de css y no de firefox.
Yo tambien me dedico a hacer sitios y uso firefox 3.6.3 en ubuntu todo el dia y no veo grandes problemas.
En esa pagina que mandaste, hice un par de toques con firebug y se ve bien con esos arreglos en firefox.
En chrome directamente no carga el css.

---

### Post by aledruetta on 2010-05-03
> **sitiomatic said:**
> Parece un problema de css y no de firefox.
Yo tambien me dedico a hacer sitios y uso firefox 3.6.3 en ubuntu todo el dia y no veo grandes problemas.
En esa pagina que mandaste, hice un par de toques con firebug y se ve bien con esos arreglos en firefox.
En chrome directamente no carga el css.

Bueno, gracias muchachos. Voy a buscar por el lado del host a ver qué pasa con la compresión. Debe ser eso, no sé. Pensé que podía ser firefox, porque todo comenzó después de la actualización de ubuntu. Debe ser casualidad.
Gracias de nuevo.

---

### Post by aledruetta on 2010-05-03
Evidentemente hay un problema con el servicio de hosting, porque ahora está totalmente caído.

---

### Post by sitiomatic on 2010-05-03
> **aledruetta said:**
> Evidentemente hay un problema con el servicio de hosting, porque ahora está totalmente caído.

Es un tema conseguir host confiable, accesible y con buen soporte. Yo hace años que hosteo en USA y Canada.

---

### Post by aledruetta on 2010-05-03
> **sitiomatic said:**
> Es un tema conseguir host confiable, accesible y con buen soporte. Yo hace años que hosteo en USA y Canada.

Es un gran problema, sí. 

Y haciendo host en USA o Canadá ¿no aumenta el tiempo de acceso a la página?

PD: Los moderadores nos van a retar, esto no tiene nada que ver con Ubuntu :(

---

### Post by hictio on 2010-05-03
> **aledruetta said:**
> Es un gran problema, sí. 

Y haciendo host en USA o Canadá ¿no aumenta el tiempo de acceso a la página?

PD: Los moderadores nos van a retar, esto no tiene nada que ver con Ubuntu :(

Para nada, depende del ancho de banda, en realidad, y es difícil que encuentres algo peor que lo podés encontrar en Argentina.

En el trabajo usamos estos dos hace ya años:

[www.vaultnetworks.com](www.vaultnetworks.com)
[www.hostway.com](www.hostway.com)

Son caros, si, pero muy, muy confiables, especialmente Hostway.

(Aclaro, no trabajo para ellos, ni gano nada con la recomendación)

La única ventaja que se me ocurre en hostear tu página en un servidor/ data center nacional es que necesites por alguna razón conectarte a la infraestructura nacional (red telefónica, por ejemplo) o todos los visitantes lo hagan desde dentro de la Argentina.

---

### Post by guillermolisi on 2010-05-03
Si el tema esta solucionado, por favor marquenlo como Solved.

Si no lo esta, pueden seguir con la charla OT pero en otro ambito, un nuevo thread en Comunidad por ejemplo.

Nada personal, es parte del trabajo :)

---

