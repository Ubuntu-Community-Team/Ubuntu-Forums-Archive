---
title: "Qcad, plano con dibujos a diferentes escalas"
date: 2008-11-17
forum: Software
---

### Post by GGsalas on 2008-11-17
Hola, estoy investigando el cad libre QCAD. Cuesta acostumbrarse, pero creo que si logro solucionar un obstáclo, este programa me permitirá crear y administrar toda la documentación de una obra, que es para lo cual lo necesito.

Para hacer planos AutoCAD crea los llamados "espacios papel" donde se van insertando ventanas a diferentes escalas y con diferentes capas activadas. De esta manera cualquier modificación en el "modelo" se refleja en los planos, sean 5 o 500, da igual. 

[B]En Qcad probé crear un bloque para cada dibujo, escalarlo, y con eso crear el plano que necesito. Luego con capas podré ir mostrando u ocultando los planos de la obra.

El problema es que las cotas que coloco dentro del bloque, cuando lo escalo, miden mal al objeto. [/B]

[Esta pregunta la hice en el foro de Qcad ]("http://www.ribbonsoft.com/forum/viewtopic.php?t=475&highlight=&sid=ae2cc38b44805ca8bea4ee4d87e633b6")y me contestaron que era un problema simple, pero realmente no se como solucionarlo.
[B][CENTER]
[Dejo esta imágen que explica el problema]("http://www.flickr.com/photos/28171665@N00/3024026587/")[/CENTER][/B]

[COLOR="DimGray"]¿alguien del foro colabora con este proyecto? Creo que es el CAD Libre más avanzado, aunque le faltan muy pocas cosas para ser 100% utilizable, puedo mencionar:

[LIST]
[*] Cotas acumuladas (supongo que debe haber alguna manera de simularlas, no lo he investigado, pero deberían estar tan a la vista como las parciales)

[*] Una manera de crear MUCHOS PLANOS, con DIBUJOS, cada Dibujo con su escala. (Como digo, cada dibujo puede ser un bloque, y cada bloque puede estar dentro del plano o ser planos separados)

[*] Nada más, creo que de esta manera es una herramienta de trabajo para arquitectos e ingenieros, no creo que falte nada más, a pesar de que Autocad tenga otras opciones no las considero sustanciales para el 90% de los proyectos.
[/LIST][/COLOR]

Bueno, nada más, disculpen la extensión de este mensaje, pero hace casi 2 años que estoy buscando una solución para migrar 100% al software libre y todavía no lo logré.

Gracias, saludos

---

### Post by Kittukahier on 2008-12-04
En el manual en línea en la explicación de **escalar** ponen:
*"Se mostrará el cuadro de diálogo que se observa en la figura 28.4. Para escalar las entidades sin mantener las originales, seleccione "Eliminar Original", para copiar elija _"Conservar Original"_. Por último, puede crear múltiples copias de una sola vez seleccionando "Copias Múltiples" copias" e introduciendo el número deseado en la línea de texto inferior. Tenga en cuenta que '9' creará 9 copias de la original - el valor por defecto es 10. _Las copias tendrán los mismos atributos y estarán en la misma capa que la entidad original. Para cambiar esto, puede activar las opciones "Usar atributos actuales" o "Usar capa actual"_."*

Ojalá sea de ayuda!

---

### Post by GGsalas on 2008-12-05
> **Kittukahier said:**
> En el manual en línea en la explicación de **escalar** ponen:
*"Se mostrará el cuadro de diálogo que se observa en la figura 28.4. Para escalar las entidades sin mantener las originales, seleccione "Eliminar Original", para copiar elija _"Conservar Original"_. Por último, puede crear múltiples copias de una sola vez seleccionando "Copias Múltiples" copias" e introduciendo el número deseado en la línea de texto inferior. Tenga en cuenta que '9' creará 9 copias de la original - el valor por defecto es 10. _Las copias tendrán los mismos atributos y estarán en la misma capa que la entidad original. Para cambiar esto, puede activar las opciones "Usar atributos actuales" o "Usar capa actual"_."*
Ojalá sea de ayuda!

Gracias. Lo que explica esa parte del maual es la utilización de la herramienta "escala". No dice cómo hacer para que las cotas midan la medida original de un bloque.

Saludos.

---

