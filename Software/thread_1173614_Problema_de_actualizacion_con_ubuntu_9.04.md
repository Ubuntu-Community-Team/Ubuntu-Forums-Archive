---
title: "Problema de actualizacion con ubuntu 9.04"
date: 2009-05-29
forum: Software
---

### Post by killer22 on 2009-05-29
Hola, estaba tratando de actualizar ubuntu y me salio este error:

[B][I]Imposible obtener [http://ppa.launchpad.net/flam3/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/flam3/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/I][/B]

Y no se como solucionarlo por lo tanto no se me actualiza ubuntu hace rato.
busque una solucion pero solo encontre para la vercion 8.10 de ubuntu.

Gracias de todas formas. ;)

---

### Post by pablo.s on 2009-05-29
No está más activo ese [PPA]("https://launchpad.net/%7Eflam3/+archive/ppa").
(La parte de Jaunty, digo,
sin embargo aparecen
Intrepid y Hardy)
¿Por qué no se te actualiza 
más Ubuntu?

---

### Post by killer22 on 2009-05-29
Si este ya no funciona no sabes por cual lo remplazo....
si el de Jaunty ya no aparece y yo nececito ese

---

### Post by pablo.s on 2009-05-29
Podés usar el de Intrepid.
Alguna razón tuvo para
retirar los paquetes de
Jaunty. En la linea del
PPA podés reemplazar
"jaunty" por "intrepid"
y funciona.

---

### Post by killer22 on 2009-05-29
Probe lo eso y me tiro esto:

[B][I]Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 91DAE98F32FFB679.

Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/I][/B]
y ahi ni idea.
gracias por responder hasta ahora.

---

### Post by pablo.s on 2009-05-29
El tema de las firmas es
muy simple:

1) Andá a [esta página]("https://launchpad.net/%7Eflam3/+archive/ppa").

2)Hacé click donde dice:
"This repository is signed
bla bla.." pero en la clave
1024R/32FF que está en
color azul.

3) Te abre una página
que dice "Search results..."
y otra vez hacés click en
la clave 32FFB679

4) Abre un archivo de texto
que dice "Public key server"
y COPIAS seleccionando
todo el texto menos lo que
está en letra grande, pero
si la letra chica.

5) Abris Gedit y PEGAS lo
que copiaste antes. Guardás
el documento como "clave.txt"

6)Vas al menú Sistema -
Administración y elegís
Fuentes de Software ( o
algo asi, no lo tengo en 
castellano)

7) En la solapa que dice
Autenticación vas adonde
dice "Importar clave" y
elegís el archivito que ya
habias guardado como
"clave.txt"

Eso es todo.

---

