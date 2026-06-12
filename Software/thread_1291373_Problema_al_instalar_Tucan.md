---
title: "Problema al instalar Tucan"
date: 2009-10-14
forum: Software
---

### Post by ferlz on 2009-10-14
Bueno queria instalar este programa para descargar cosas de internet (el programa se llama Tucan) y resulta que segui lo que decia en una web y me salto un error en el terminal y ahora cuando abro el Gestor de Paquetes Synaptic me salta esto:

[HTML]E: Tipo '“deb' desconocido en la línea 1 de lista de fuentes /etc/apt/sources.list.d/tucan.list
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.
E: _cache->open() failed, please report.[/HTML]

Y busque por inet y por todos lados pero no tengo idea que hacer para que ande de vuelta :S

---

### Post by SLA_leandrin on 2009-10-14
Podés postear completo que es lo que hiciste, como querés instalar tucán?

De todos modos te recomiendo fuertemente instalar Jdownloader en cambio. Es en java eso sí, pero anda mejor como gestor de descarga y acepta (casi) todos los sitios de descarga.

[URL="http://jdownloader.org/download"]http://jdownloader.org/download
[/URL]

Saludos.

---

### Post by guillermolisi on 2009-10-14
Podrias mostrarnos el contenido del archivo /etc/apt/sources.list.d/tucan.list ?

---

### Post by gmunioz on 2009-10-14
Hola fer...:

1- Carga nautilus con permisos temporarios de administrador:

Ejecuta en consola Aplicaciones - Accesorios - Terminal:

```
sudo nautilus
```

Navega hasta el directorio (carpeta)

/etc/apt/sources.list.d/

Y borra el archivo tucan.list

Navega hasta /etc/apt/

Pulsa el boton derecho sobre el archivo

sources.list

Elige editar

Borra las líneas que hagan referencia a tucan

Guarda el archivo.

Cierra gedit

Ejecuta:

```
sudo apt-get update

sudo apt-get upgrade
```

2- Si el problema se solucionó, respecto de tucan

es un excelente programa para descargar multiples

archivos en forma desatendida de sitios de alojamiento

tipo mediafire, rapidshare, etc.

Ve a este sitio:

[http://www.getdeb.net/](http://www.getdeb.net/)

Descarga el archivo de tu distribución y

arquitectura, con nautilus navega hasta el 

y pulsa doble click izquierdo para instalarlo

con gdebi

---

### Post by ferlz on 2009-10-14
Gracias a todos gente, hice lo que me dijo [gmunioz]("http://ubuntuforums.org/member.php?u=252237") y andubo de 10 todo, muchas gracias.

---

