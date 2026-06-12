---
title: "usar google earth a través de un proxy"
date: 2011-12-02
forum: Software
---

### Post by asterix77 on 2011-12-02
Estimados:

Tengo lucid instalado en mi notebook, y como indico en el título no puedo conectarme a través de un proxy, ya que mayoritariamente google earth lo uso en mi trabajo. En herramientas ----> opciones no me aparece nada relacionado con alguna configuración de red o proxy.

En mi hogar no tengo ningún problema.

Mi versión de google earth es la 6.0.3.2197

 p, li { white-space: pre-wrap; }Desde ya agradezco cualquier ayuda

Saludos

---

### Post by guillermolisi on 2011-12-02
La configuracion no dependera de la configuracion de red del sistema y por eso no hay opciones particulares dentro de GEarth ?

Supongo que habras probado definiendo un proxy a nivel del sistema. Si no lo hiciste, proba y comenta que resultados obtenes.

Es importante conocer las caracteristicas de ese proxy para poder definirlo adecuadamente.

---

### Post by asterix77 on 2011-12-05
Agradezco el comentario, como la consulta la hice el viernes, solo hoy pude acceder a google earth en mi lugar de trabajo.

La verdad no se me había ocurrido establecer el proxy a nivel de sistema, supongo que será la ruta Sistema ----->Preferencias ------>Proxy de la red y aquí configurar las opciones correctas. Pues bien no me ha resultado.

El acceso a internet y a mi correo a través del proxy, está bien configurado, así es que el problema al parecer es de google earth.

Y no es un asunto de restricción de acceso del proxy, ya que los demás compañeros lo usan sin ninguna restricción. Incluso yo al arrancar con windows en el mismo notebook, puedo acceder a google earth sin problemas.

Saludos

---

### Post by guillermolisi on 2011-12-05
Si te arreglas leyendo en Ingles, [aqui]("https://groups.google.com/group/earth-linux/browse_thread/thread/cdd7ed6f2417b161?pli=1") hay un caso de exito usando Fedora Core 6 con proxy.

La solucion esta en el ultimo punto. Lo anterior es el relato de la situacion y las pruebas que esa persona llevo a cabo hasta llegar a resolver el tema.

---

### Post by asterix77 on 2011-12-06
:P
Excelente,me ha funcionado. La verdad es que ya lo había hecho, lo había leido en algún post. Pero al parecer había un error, ya que después del signo = digité directamente la ip y puerto. Ahora con agregar el http:// más la ip y puerto me ha funcionado a la perfección, en caso de querer usarlo sin proxy, me imagino que la solución será comentar la linea del archivo y listo.

Estas son las cosas que me gustan de ubuntu y linux en general, siempre hay alguna forma de hacer funcionar las cosas, y de paso se parende.

Saludos y gracias

---

