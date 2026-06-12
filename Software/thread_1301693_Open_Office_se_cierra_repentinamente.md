---
title: "Open Office se cierra repentinamente"
date: 2009-10-26
forum: Software
---

### Post by asterix77 on 2009-10-26
Tal como dice el título, mi versión de open office (3.1.0), se cierra en forma repentina. Esto me sucede hasta el momento, solo cuando quiero copiar textos desde una página web al procesador de texto. Me explico mejor, busco temas e internet, y si algo quiero, lo copio y lo voy agregando  a mi texto; llevo ya como 40 páginas. Al copiar algo, me dá un tiempo suficiente como para guardar el documento y se cierra. A veces cuando consulto dicho documento, igual se cierra por lo que es molesto.

Espero que alguien me pueda ayudar, he tratado de abrir open office mediante terminal para ver si me arroja un error, pero solo lo llama y listo. De igual forma he tratado de buscar algún log de error, pero nada, por lo que si alguien sabe como hacerlo se lo agradecería.

Saludos

---

### Post by AlexDDR on 2009-10-26
como consejo, y no tiene nada que ver con el bug, yo paso todos los textos copiados a writer o word (depende del caso) por el block de notas, en ubuntu gedit (editor de texto plano) para asi eliminar el formateo html que puede generar muchos dolores de cabeza para cuando uno tiene que presentar un trabjo con presentacion excelente


debe haber un repositorio de openoffice en el que se actualice a la siguiente version de openoffice, solo s cosa de esperar


saludos

---

### Post by moreback on 2009-10-26
> **AlexDDR said:**
> como consejo, y no tiene nada que ver con el bug, yo paso todos los textos copiados a writer o word (depende del caso) por el block de notas, en ubuntu gedit (editor de texto plano) para asi eliminar el formateo html que puede generar muchos dolores de cabeza para cuando uno tiene que presentar un trabjo con presentacion excelente


debe haber un repositorio de openoffice en el que se actualice a la siguiente version de openoffice, solo s cosa de esperar


saludos

Para no usar el Gedit, podrías usar la combinación de teclas Shift+Ctrl+V para usar el Pegado especial, ahí podrás elegir el formato que quieras, como texto plano, rtf, etc.

---

### Post by maxmoraga on 2009-10-27
intenta iniciar openoffice desde la terminal y repite los pasos para reproducir el bug, debiera mostrar algun stacktrace del error. luego pega el error aqui para ver si es quizas un error en tu pc o quizas debiese ser reportado como bug a los desarrolladores de openoffice. 

Saludos.

---

### Post by asterix77 on 2009-10-27
En primer lugar, gracias por sus respuestas.

Maxmoraga, ya intenté iniciarlo desde el terminal, pero solo lo abre y me devuelve al promp, aunque trabaje y guarde algún documento. Es por eso que consultaba si es que alguien sabe donde open office guarda sus log para ver el funcionamiento y errores de este.

En la terminal ecribo

$ ooffice -writer %F                         ...y una vez abierto, me devuelve al promp esperando por otro comando
$                          

Voy a intentar hacerlo con el pegado especial, y si no me resulta, lo haré con gedit. Aunque con gedit no creo que se copien algunos archivos de imágenes. 


Saludos y gracias una vez más

---

### Post by maxmoraga on 2009-10-27
lamentablemente ahora estoy en la oficina con windows, pero openoffice es una aplicación java y debe haber alguna manera de iniciarlo con java en modo debug. revisa si existe alguna linea en el script de inicio de openoffice que ejecute un archivo *.jar. Debiera ser alguna linea como $java openoffice.jar o algo así, si es así cambia ese java por javaw y así iniciara en modo debug. yo supongo que debe haber algo asi en openoffice pero no lo puedo comprobar ahora ya que no estoy usando linux en este momento.

:p

---

### Post by Patriciologico on 2009-10-27
> **maxmoraga said:**
> lamentablemente ahora estoy en la oficina con windows, pero openoffice es una aplicación java y debe haber alguna manera de iniciarlo con java en modo debug. 

Hola Max, entiendo que OO.org, esta escrito en C++, no en Java, aunque tiene dependencias java, pero no se cuales.

Saludos!

---

### Post by maxmoraga on 2009-10-29
> **Patriciologico said:**
> Hola Max, entiendo que OO.org, esta escrito en C++, no en Java, aunque tiene dependencias java, pero no se cuales.

Saludos!

Tienes razón, no se donde escuche que era java o quizás las primeras versiones de staroffice fueron en java.

---

### Post by rauls66 on 2009-12-23
Bueno, a mí me pasa lo mismo. Cuando intento pegar un texto html se cierra sólo. Ahora, si hago la copia <shift><ctrl><v> como se comenta por ahí arriba, entonces esto no pasa.
Si alguien encuentra la solución, aquí estamos.
Saludos.

---

### Post by moreback on 2009-12-23
... y dale con copiar de la wikipedia para los trabajos del colegio jajaja

Saludos a todos!

---

