---
title: "No se puede abrir PDF con Firefox"
date: 2009-05-05
forum: Software
---

### Post by Einfachlacm on 2009-05-05
Hola,

Estoy tratando de abrir un archivo PDF sin tener que guardarlo en el HD para luego abrilo con Evince.

El archivo que quiero abrir especificamente es este:

[http://librairie.territorial.fr/PAR_TPL_IDENTIFIANT/633/TPL_CODE/TPL_OUVR_NUM_FICHE/PAG_TITLE/R%E9ussir+son+plan+de+communication/42-librairie-des-professionnels-territoriaux.htm](http://librairie.territorial.fr/PAR_TPL_IDENTIFIANT/633/TPL_CODE/TPL_OUVR_NUM_FICHE/PAG_TITLE/R%E9ussir+son+plan+de+communication/42-librairie-des-professionnels-territoriaux.htm)

Donde dice: >> Téléchargez le sommaire  (format pdf, 292.97 Ko)

Doy click y me aparece la ventana de Firefox: "Abriendo Reussir-son-plan-de-communication.pdf" y me pregunta si lo quiero guardar o abrir con "Visor de documentos (predeterminada)".
Solo tengo como opciones "Visor de documentos (predeterminada)", "firefox-3.0.10" y "Otro". Doy click en cualquiera de los dos y me aparece el mensaje: "/tmp/Reussir-son-plan-de-communication.pdf no se puede abrir, porque la aplicacion asociada no existe. Cambie la asociacion en sus preferencias."

Quiero asociarlo a Evince, pero no se como. Alguna sugerencia?

Gracias de antemano.

---

### Post by pablo.s on 2009-05-05
En Editar -- Preferencias -- Aplicaciones
está la lista de archivos y sus
respectivas aplicaciones para
ser conectados entre si.

---

### Post by Einfachlacm on 2009-05-05
Claro, el tema es que solo aparece "Siempre preguntar", "Guardar archivo", "Usar", "Usar otra", "Detalles de la aplicacion" (si selecciono esto solo esta "firefox"). No se como agregar Evince, ni en que parte del sistema lo puedo encontrar.

Saludos.

---

### Post by josecuervo86 on 2009-05-05
Apreta donde dice "Usar otra", despues anda a sistema de archivos > usr > bin > y ahi busca evince ;)

---

### Post by marianom on 2009-05-05
Otra forma posible es editar el archivo del mailcap
Te vas a la terminal y abrís o creas .mailcap
Dentro ponés con que programa se tiene que abrir que extensión.
Te doy como ejemplo el mío (que lo uso para mutt, por eso está el lynx):

```

text/html;                      lynx -assume_charset=%{charset} %s; nametemplate=%s.html
text/html;                      lynx -assume_charset=%{charset} -dump %s; nametemplate=%s.html; copiousoutput
application/msword;             abiword %s
application/vnd.ms-excel;       gnumeric %s
application/msexcel;            gnumeric %s
application/pdf;                evince %s
image/png;                      eog %s
image/jpg;                      eog %s
image/jpeg;                     eog %s
application/x-gzip;             file-roller %s
application/x-rar;              file-roller %s
application/zip;                file-roller %s
application/rar;                file-roller %s


```

Luego te vas a about:config en tu navegador, buscás helpers.private_mailcap_file y te asegurás que apunte al archivo creado.
Listo (opcionalmente si no anda podes crear el ~/.mime.types que es esencialmente lo mismo (mirá el /etc/.mime.types para más datos).

---

### Post by pablo.s on 2009-05-05
> **marianom said:**
> Otra forma posible es editar el archivo del mailcap
Te vas a la terminal y abrís o creas .mailcap
Dentro ponés con que programa se tiene que abrir que extensión.

Pero los mimetypes de Firefox no 
los gestiona internamente? Que pasa
si por ejemplo yo quiero que nautilus
abra los PDF con Adobe Reader y desde
Firefox los abra con Evince?

> **marianom said:**
> Te doy como ejemplo el mío (que lo uso para mutt, por eso está el lynx):

Sos grosso, Mariano. Yo uso alpine.

---

### Post by marianom on 2009-05-05
> **pablo.s said:**
> Pero los mimetypes de Firefox no 
los gestiona internamente? Que pasa
si por ejemplo yo quiero que nautilus
abra los PDF con Adobe Reader y desde
Firefox los abra con Evince?

¿Hay un adobe para linux? mira lo que me vengo a enterar... de todos modos, estoy contento con evince, de aca no me muevo.
Con respecto a tu pregunta, es posible que Firefox lo haga, realmente no debería y sería mal comportado que no siga las configuraciones por defecto. Haciendo una prueba rápida, si intento abrir un .doc desde firefox lo intenta hacer con abiword, como lo tengo en mi .mailcap (cuando para una instalación por defecto de gnome como tengo yo, lo debería intentar con OO). No puedo confirmarte que hace con el pdf (ya que posiblemente lo trate diferencial) pero parece respetar lo que le digo con respecto a los docs.


> **pablo.s said:**
> 
Sos grosso, Mariano. Yo uso alpine.

"Somos" grosos, sabelo :)
Son un vicio estos clientes de mails

---

### Post by pablo.s on 2009-05-05
> **marianom said:**
> ¿Hay un adobe para linux? mira lo que me vengo a enterar... de todos modos, estoy contento con evince, de aca no me muevo.

Si, hay una versión nativa de Adobe,
peeeeeero, usa unos miseros 300 MB
en disco para el manejo de PDFs, a mi
me rompe soberanamente las castañas
y por eso estoy utilizando otra vez Evince.

> **marianom said:**
> "Somos" grosos, sabelo 
Son un vicio estos clientes de mails

Ah! Pensé que se venia la gastada de
"alpine is for wimps, use mutt instead"

---

### Post by Einfachlacm on 2009-05-05
> **josecuervo86 said:**
> Apreta donde dice "Usar otra", despues anda a sistema de archivos > usr > bin > y ahi busca evince ;)

Muchas gracias a todos por las respuestas. 

Simple y al grano. ;)

---

### Post by juancarlospaco on 2009-05-05
Che... pasen por Medibuntu, hay un paqueton llamado: "Mozilla-acroread"

---

### Post by Einfachlacm on 2009-05-05
No, en realidad queria configurarlo con Evince, que es liviano y libre.

El Reader de Adobe es pesado y lento, ademas privativo.

---

