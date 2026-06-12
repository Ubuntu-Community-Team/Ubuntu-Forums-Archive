---
title: "Problemas con Transmission"
date: 2009-06-03
forum: Software
---

### Post by dcorrea on 2009-06-03
Hola a todos...
Me ha pasado ya dos veces que cuando incio una descarga de un archivo torrents con Transmission 1.51 en ubuntu 9.4 lo hace con normalidad.
Pero cuando apago el PC e inicio Transmission nuevamente, se pierde todo lo que habia descargado con anterioridad y la descarga se inicia en 0%.

Se agredece su ayuda.

Nota: Siempre antes de apagar el PC me aseguro de cerrar Transmission previamente.

---

### Post by Carlos C on 2009-06-03
Hola. Te voy a dar una respuesta que no es muy buena en realidad, pero puede servir. No sé como resolver tu problema, se me ocurre que el archivo se corrompe por alguna razón y el programa no es capaz de resumir la descarga correctamente. Existen otras alternativas para torrent que te pueden dar mejores resultados. He usado ktorrent y deluge y ambos son muy buenos. Ahora uso deluge porque es muy fácil de configurar para que quede corriendo como daemon y así puedes controlar tus descargas con cualquier navegador web que este conectado a internet.

Saludos.

---

### Post by radixs on 2009-06-03
Deluge es una mejor alternativa.

Ahora continuando con tu problema, ¿las descargas de los torrent que estas realizando las tienes en una partición aparte? Ej: *“NTFS”* o estas descargando directamente en el directorio /home?

Si el problema fuese que estas descargando en una partición *"NTFS"*, seria que no tienes montada la partición, esa seria la razon por la cual no retoma la descarga.

---

### Post by dcorrea on 2009-06-03
gracias una ves más por sus respuestas...
voy a darle una opotunidad mas a transmission...
y descarge los archivos en mi /home.

Duda adicional; puede ver el archivo /home desde windows XP?...
al parecer no, porque tiene u formato de archivos distintos...ext3 (en mi caso)
o se podrá de alguna manera?

---

### Post by Patriciologico on 2009-06-04
> **dcorrea said:**
> Duda adicional; puede ver el archivo /home desde windows XP?...
al parecer no, porque tiene u formato de archivos distintos...ext3 (en mi caso)
o se podrá de alguna manera?

Ver particiones ext3 desde Windows, merece que habrás un nuevo tema, para que sea fácilmente encontrado por otros necesitados de lo mismo.

Te anticipo que si se puede instalando un programa en Windows.

Saludos!

---

### Post by nopersona on 2009-06-04
+1 para Deluge. Sobre tu consulta, creo que podría ser que la partición donde guardas los torrents no esté montada cuando reinicias y el programa quiere descargar, o tiene errores en los permisos.

---

### Post by Eddy_Kine on 2009-06-06
A la pregunta, por su facilidad de configuración, te recomiendo Deluge, la velocidad de descarga en mi caso ha llegado a los 904 kb con internet de 8 mb. es excelente ;)

---

