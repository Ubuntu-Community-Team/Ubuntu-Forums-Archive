---
title: "Applet de geogebra en firefox"
date: 2012-05-22
forum: Uruguay Team
---

### Post by francomariani on 2012-05-22
Hola para todos. Estoy armando un blog, donde quiero colgar applets de  geogebra. Los hago sin problemas pero al momento de verlos en firefox los abre por primera vez y luego, si cierro la pestaña donde se encuentra el applet y abro otra para ver otro (o el mismo) ya no lo puedo ver bien, es decir, queda un recuadro de fondo gris pero no puedo  visualizarlos. 
Tengo entendido que para visualizarlos correctamente tengo que tener instalado java. Escribo *java -version* en la terminal y me sale esto: 
[B]java version "1.6.0_24" 
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu3) 
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)[/B]

Yo lo instalé mediante: sudo apt-get install ubuntu-restricted-extras creo.. Y además metiendo mano sin saber instalé OpenJDK Java 7 Runtime desde el centro de software de ubuntu. O sea que me quedaron las versiones 6 y 7 instaladas, por lo menos eso veo desde el centro de software. Igual, el problema lo tengo desde antes de instalar la versión 7..
Bueno espero alguna solución. 
Saludos, 
Franco.

---

### Post by francomariani on 2012-06-15
[U][B]Solución:

[/B][/U]Primeramente corroborar que estén instalados los siguientes paquetes: 
> ttf-mscorefonts-installer 
libmysql-javaLuego, abrir una terminal y esciribir: 

```
franco@franco-HP-Pavilion-dm4-Notebook-PC:~$ sudo update-alternatives --config java [sudo] password for franco:  Existen 4 opcioens para la alternativa java (que provee /usr/bin/java).    Selección   Ruta                                            Prioridad  Estado ------------------------------------------------------------   0            /usr/lib/jvm/java-7-oracle/bin/java              1064      modo automático   1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      modo manual * 2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      modo manual   3            /usr/lib/jvm/java-7-oracle/bin/java              1064      modo manual   4            /usr/lib/jvm/java-7-oracle/jre/bin/java          1064      modo manual  Pulse <Intro> para mantener el valor por omisión 
[*] o pulse un número de selección:
```

Seleccionar cualquier número que tenga openjdk (ya sea en su versión 6 o  7). Por supuesto que hay que instalarlo previamente (desde el centro de  software de ubuntu, por ejemplo). 
Y tema solucionado, los applets de geogebra en firefox se ven perfectamente. 
Saludos, 
Franco.

---

