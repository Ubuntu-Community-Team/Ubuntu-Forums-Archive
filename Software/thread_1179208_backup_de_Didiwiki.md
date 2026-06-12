---
title: "backup de Didiwiki"
date: 2009-06-05
forum: Software
---

### Post by papa canaria on 2009-06-05
Hola buenas, he tenido que reinstalar mi ubuntu a la nueva version (porque me dio la gana, porque funcionaba de maravilla ;) ) y como tuve que hacer un backup de didiwiki (una plataforma que me gusta mucho de wikis) y busqué por la web y no encontré mucho me animé ha hacer un super-cutre howto que espero que le sirva a los que se encuentren en misma situación.

Deciros que lo hice a base de ensayo y error, y que problablemente (o no) haya un método más civilizado y común (yo no lo encontré)

En primer lugar (por si alguien no lo sabe) didiwiki se instala con un simple:
 *sudo aptitude install didiwiki*

Una vez instalado las páginas que vayamos creando se crearan en el directorio:
 */var/lib/didiwiki*  (y no en ~/.didiwiki como lei en muchos sitios, aunque se puede cambiar)

Si queremos cambiar donde se guardarán las páginas editaremos el archivo:
* sudo /etc/init.d/didiwiki*
y sustituiremos siempre que encontremos la cadena (son 2 veces en este archivo):
 [I]start-stop-daemon --start -b -m -c didiwiki --quiet --pidfile \
            /var/run/$NAME.pid --exec $DAEMON -- --home=[COLOR=Red]/el_directorio_que_queramos_poner[/COLOR][/I]

Bueno, evidentemente si queremos hacer un backup del contenido de didiwiki debemos de copiar la carpeta donde se encuentren las páginas, recordad, por defecto en:
 */var/lib/didiwiki*
Lo podemos hacer de la siguiente manera:
*sudo cp -R /var/lib/didiwiki /directorio/a/copiar*

Ahora ya tenemos un backup de nuestro contenido. Después de cualquier tragedia, formateo o algo, lo único que debemos hacer es copiar el contenido de esta carpeta al directorio por defecto de las páginas o cambiar nuestro directorio de didiwiki (como hicimos antes).
Lo único, deciros que para que didiwiki pueda escribir en las páginas (ya a mi me pasó), la carpeta donde pongamos el home de didiwiki y las páginas creadas tienen que ser propiedad del usuario didiwiki
*sudo chown -R didiwiki:didiwiki /carpeta/a/cambiar/propietario*

Saludos a todos!!

---

