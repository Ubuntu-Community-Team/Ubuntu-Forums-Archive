---
title: "mdb viewer no abre archivos mdb"
date: 2009-05-19
forum: Software
---

### Post by el_burgues on 2009-05-19
Descargué el mdb viewer desde los repositorios sin embargo se cierra automáticamente al intentar abrir cualquier archivo mdb. ¿Baja el programa incompleto de los repositorios?

---

### Post by guillermolisi on 2009-05-19
Busque en los repos y solo encontre "mdbtools" que sirve para trabajar con bases de datos Jet de MS.

No pude dar con "MDB Viewer" (lo mas parecido en nombre fue "iMDBTools" pero es para otra cosa, nada que ver con bases de datos MDB).

Salvo que tengas algun repositorio especial incluido en tu sistema, en los tradicionalmente usados no lo encontre (los que vienen "de fabrica" mas Medibuntu, Wine, VirtualBox y ppa de KDE4.2)

---

### Post by mauriciog on 2009-05-19
Buenas noches estimados.
Desde OpenOffice (Base) no los podes abrir? Cual es especificamente tu necesidad?
Exitos!

---

### Post by el_burgues on 2009-05-22
> **guillermolisi said:**
> Busque en los repos y solo encontre "mdbtools" que sirve para trabajar con bases de datos Jet de MS.

No pude dar con "MDB Viewer" (lo mas parecido en nombre fue "iMDBTools" pero es para otra cosa, nada que ver con bases de datos MDB).

Salvo que tengas algun repositorio especial incluido en tu sistema, en los tradicionalmente usados no lo encontre (los que vienen "de fabrica" mas Medibuntu, Wine, VirtualBox y ppa de KDE4.2)


En los repositorios figura como "visor mdb", luego, una vez instalado, aparece el icono del programa   como "mdb viewer en: aplicaciones, oficina.

---

### Post by el_burgues on 2009-05-22
> **mauriciog said:**
> Buenas noches estimados.
Desde OpenOffice (Base) no los podes abrir? Cual es especificamente tu necesidad?
Exitos!

hice varias bases de datos en el trabajo y quiero abrirlas en casa para analizar y discutir los datos registrados con mi esposa. Me interesa que se vean las pantallas para que entienda como los usuarios ingresan los datos.

---

### Post by guillermolisi on 2009-05-22
> **el_burgues said:**
> En los repositorios figura como "visor mdb", luego, una vez instalado, aparece el icono del programa   como "mdb viewer en: aplicaciones, oficina.
A que repositorio pertence este paquete ?
A universe, a multiverse , otro ?

No sera que lo estas viendo en la opcion de "Intstalar/agregar programas" ?

Los nombres de los paquetes en los repositorios estan en Ingles, generalmente.

Busque por "mdb" y  "viewer y en ningun caso me trajo algo parecido a los que mencionas, usando Synaptic.

No se si el uso de un viewer te permitira hacer lo que pretendes ya que, generalmente, cuando se habla de un visor de base de datos se esta haciendo referencia a ver su estructura y contenidos pero no a ver sus interfaces/formularios de ingreso y consulta de datos.

---

### Post by el_burgues on 2009-05-23
> **guillermolisi said:**
> A que repositorio pertence este paquete ?
A universe, a multiverse , otro ?

No sera que lo estas viendo en la opcion de "Intstalar/agregar programas" ?

Los nombres de los paquetes en los repositorios estan en Ingles, generalmente.

Busque por "mdb" y  "viewer y en ningun caso me trajo algo parecido a los que mencionas, usando Synaptic.

No se si el uso de un viewer te permitira hacer lo que pretendes ya que, generalmente, cuando se habla de un visor de base de datos se esta haciendo referencia a ver su estructura y contenidos pero no a ver sus interfaces/formularios de ingreso y consulta de datos.

Es cierto, no usé Synaptic, usé la opción añadir y quitar aplicaciones. La cuestión es que ni siquiera puedo ver los datos que contiene la base.

---

### Post by guillermolisi on 2009-05-23
> **el_burgues said:**
> Es cierto, no usé Synaptic, usé la opción añadir y quitar aplicaciones. La cuestión es que ni siquiera puedo ver los datos que contiene la base.
Entonces el nombre real de esa herramienta es otro y posiblemente sea alguno de los que mencione oportunamente (mdbtools por ejemplo).

Igual considera lo que dije antes respecto que esas herramientas no estan , en general, preparadas para usar un desarrollo con formularios, tal como haces en la otra maquina, sino para trabajar la estructura de datos y su contenido (algo mas crudo que lo que creo necesitas hacer.

Si la aplicacion corre en Windows y esta hecha con Access, por mencionar una alternativa, probaria de correrla bajo Wine.

Otra posibilidad es virtualizar un WinXP y ahi corres la aplicacion en forma nativa.

---

### Post by jipz2005 on 2009-06-25
Tengo el mismo problema y ya no se que hacer.

---

### Post by jdmonto0 on 2009-06-26
Hola gente, yo también tengo el mismo problema, necesito abrir unos mdb para exportarlos a postreSQL y cuando trato con mdb viewer, este se cierra automáticamente, por synaptic se encuentra como mdbtools-gmdb, o si alguien conoce otra manera de llevar un mdb a posgreSQL, me dicen por favor.

Saludos

---

### Post by jdmonto0 on 2009-06-26
se me olvidaba, el mdb que tengo es una geodatabase

---

### Post by guillermolisi on 2009-06-27
> **jdmonto0 said:**
> Hola gente, yo también tengo el mismo problema, necesito abrir unos mdb para exportarlos a postreSQL y cuando trato con mdb viewer, este se cierra automáticamente, por synaptic se encuentra como mdbtools-gmdb, o si alguien conoce otra manera de llevar un mdb a posgreSQL, me dicen por favor.

Saludos
Y ... una forma "clasica" seria exportar/descargar el contenido de las tablas de la base mdb a archivos tipo texto y luego crear las tablas con el mismo diseño que las originales y generarlas con esos archivos de texto en la nueva base en Posgre o la que sea.

Para esta operacion hay que prestar especial cuidado a las compatibilidades/equivalencias de tipos de datos para no tener interrupciones en la generacion de las tablas.

---

