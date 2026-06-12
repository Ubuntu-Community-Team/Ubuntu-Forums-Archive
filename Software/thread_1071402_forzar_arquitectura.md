---
title: "forzar arquitectura?"
date: 2009-02-16
forum: Software
---

### Post by sirkurt on 2009-02-16
bueno la cosa es asi, 
leyendo en internet vi que se podian emular los juegos de windows sin ningun problema con el Cedega y Wine.
el problema es el siguiente tengo ubuntu 8.04 para amd64 entonces no logro isntalar cedega, segui leyendo y vi algo de una aplicacion que forza la arquitectura de instaladores como los de cdega y se puede instalar sin ningun problema.

  dpkg force architecture creo que se llamaba si no me equivoco.

bueno alguien sabe como conseguirlo o alguna solucion al cedega en si?


gracias

---

### Post by marianom on 2009-02-16
Vos mismo lo dijiste:

```
sudo dpkg -i *package.deb* --force-architecture
```

Tiende a no ser buena idea pero no lo probé con ese programa en particular. Te sugiero busques con ahínco algún post, blog, mensaje donde alguien lo haya intentando para que veas como le fue.

Siempre podes correrlo con dry-run para que lo instale de mentirita a ver si te da algún mensaje que debas considerar:

```
sudo dpkg --dry-run -i *package.deb* --force-architecture
```

---

### Post by sirkurt on 2009-02-16
me tira un error cuando intento pegar el codigo que dejaste aca te lo muestro
dpkg: error al procesar package.deb (--install):
 no se puede acceder al archivo: No existe el fichero ó directorio
dpkg: error al procesar --force-architecture (--install):
 no se puede acceder al archivo: No existe el fichero ó directorio
Se encontraron errores al procesar:
 package.deb
 --force-architecture

soy nuevo lo que estoy haciendo es pegar el codigo que dejaste nomas, si hay que hacerlo de otra forma indicame como 

y he leido en un blog que esta aplicacion es conveniente aveces

---

### Post by marianom on 2009-02-16
package.deb es el nombre del paquete que vos querés instalar, lo tenés que reemplazar con el nombre correcto en la ruta correcta.
Si el paquete se llama cedega-0.1.deb
tenés que hacer:

```
sudo dpkg -i cedega-0.1.deb --force-architecture
```

y así.

---

### Post by sirkurt on 2009-02-16
bueno este es el codigo exacto que intente usar para ejecutarlo
```
sudo dpkg -i /home/metal/Escritorio/Cedega/cedega-small_5.2_i386.deb --force-architecture
```

y este es el error que me tiro la consola 

```
dpkg: error al procesar /home/metal/Escritorio/Cedega/cedega-small_5.2_i386.deb (--install):
 la arquitectura del paquete (i386) no corresponde con la del sistema (amd64)
dpkg: error al procesar --force-architecture (--install):
 no se puede acceder al archivo: No existe el fichero ó directorio
Se encontraron errores al procesar:
 /home/metal/Escritorio/Cedega/cedega-small_5.2_i386.deb
 --force-architecture

```

---

### Post by marianom on 2009-02-16
¿Será al revés entonces? (Sorry, hago las cosas de memoria)

```
sudo dpkg --force-architecture -i package.deb
```

---

### Post by guillermolisi on 2009-02-16
> **marianom said:**
> ¿Será al revés entonces? (Sorry, hago las cosas de memoria)

```
sudo dpkg --force-architecture -i package.deb
```
Si, este es el orden correcto segun lo que surge de la lectura del manual on line sobre dpkg
```
man dpkg
```

---

### Post by sirkurt on 2009-02-16
este es el orden correcto 

```
sudo dpkg -iinstall --force-architecture  package.deb
```

jejej bueno lo termine de sacar con un poco de logica leyendo lo que me tiraba la consola 

ahora lo pude instalar y abrir correctamente pero me surgio otro problema, pero es en la ejecucion del juego en si.

asi que lo voy a poner en otro topic

---

