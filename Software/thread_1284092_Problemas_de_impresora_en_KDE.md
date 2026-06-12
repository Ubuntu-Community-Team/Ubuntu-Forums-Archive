---
title: "Problemas de impresora en KDE"
date: 2009-10-06
forum: Software
---

### Post by SLA_leandrin on 2009-10-06
Hola muchachos.

Vengo arrastrando un problema en KDE, no se exactamente desde que versión pero seguro al menos desde la 4.3 (Ahora en 4.3.2)
No puedo configurar impresoras, no puedo ni siquiera entrar al panel de configuración.

Les dejo una captura de pantalla.

[[img]http://xs344.xs.to/xs344/09412/printer768.jpeg.xs.jpg[/img]](http://xs.to/xs.php?h=xs344&d=09412&f=printer768.jpeg)

La instalación de todos los paquetes salió bien, sin novedades... no sé que camino tomar, una ayuda por favor!

Gracias, saludos.

---

### Post by SLA_leandrin on 2009-10-07
Extraño a Hei Ku...

Bump!

---

### Post by guillermolisi on 2009-10-07
> **SLA_leandrin said:**
> Hola muchachos.

Vengo arrastrando un problema en KDE, no se exactamente desde que versión pero seguro al menos desde la 4.3 (Ahora en 4.3.2)
No puedo configurar impresoras, no puedo ni siquiera entrar al panel de configuración.

Les dejo una captura de pantalla.

[[IMG]http://xs344.xs.to/xs344/09412/printer768.jpeg.xs.jpg[/IMG]]("http://xs.to/xs.php?h=xs344&d=09412&f=printer768.jpeg")

La instalación de todos los paquetes salió bien, sin novedades... no sé que camino tomar, una ayuda por favor!

Gracias, saludos.
Instalaste los ultimos paquetes de actualizacion de KDE 4.3.2 ? Hay un paquete especifico para el manejo de impresoras y el applet que aparece cuando envias un trabajo de impresion. (esto aparecio hoy como novedad).

Antes de pasar a KDE 4.3.2 funcionaba bien ? Instalaste algo especifico para impresoras como ser software de HP, por ejemplo ?

Tengo Kubuntu con KDE 4.3.2 al dia y no tengo ese problema en ninguna de las dos maquinas exactamente iguales que uso.

---

### Post by SLA_leandrin on 2009-10-07
Sip instalé 4.3.2 ayer.
No me salió ningún problema, ya no funcionaba desde antes (al menos desde 4.3). Tengo todo actualizado y al día.

No tengo instalado ningún soft extra como el HPtoobox, pero estoy pensando en instalarlo, de todos modos las impresoras que uso en el trabajo son todas HP. tendré algún conflicto?


Slds.

Gracias,
Leandro.

---

### Post by guillermolisi on 2009-10-07
> **SLA_leandrin said:**
> Sip instalé 4.3.2 ayer.
No me salió ningún problema, ya no funcionaba desde antes (al menos desde 4.3). Tengo todo actualizado y al día.

No tengo instalado ningún soft extra como el HPtoobox, pero estoy pensando en instalarlo, de todos modos las impresoras que uso en el trabajo son todas HP. tendré algún conflicto?


Slds.

Gracias,
Leandro.
No te habra quedado desde antes algun paquete de actualizacion, Python por ejemplo, roto o pendiente de aplicar que por alguna razon dio algun inconveniente ? Es que me llama mucho el mensaje que aparece en la imagen haciendo referencia a un modulo hecho en Python y el error que muestra.

---

### Post by SLA_leandrin on 2009-10-07
Aparentemente no hay nada roto.

apt-get install -f no devuelve nada.

---

### Post by guillermolisi on 2009-10-07
> **SLA_leandrin said:**
> Aparentemente no hay nada roto.

apt-get install -f no devuelve nada.
Y si hay una dependencia mal resuelta, una instalacion forzada te la resuelve ? (el primer mensaje en el bloque de las posibles causas en el screenshot que pasaste)

---

### Post by SLA_leandrin on 2009-10-07
> **guillermolisi said:**
> Y si hay una dependencia mal resuelta, una instalacion forzada te la resuelve ? (el primer mensaje en el bloque de las posibles causas en el screenshot que pasaste)

No es eso lo que hago con el apt-get -f? pensé que era eso. De todos modos, donde busco si tengo dependencias rotas? al hacer upgrade no me sale nada extraño...

```
leandro@Leandro-Laptop:~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```

---

### Post by guillermolisi on 2009-10-07
> **SLA_leandrin said:**
> No es eso lo que hago con el apt-get -f? pensé que era eso. De todos modos, donde busco si tengo dependencias rotas? al hacer upgrade no me sale nada extraño...

```
leandro@Leandro-Laptop:~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```
Para actualizar las versiones que ya tenes es update, para pasar de una version mas nueva de paquetes es upgrade.

Proba con sudo apt-get check> 
check
           check is a diagnostic tool; it updates the package cache and checks for
           broken dependencies.

---

### Post by SLA_leandrin on 2009-10-07
> **guillermolisi said:**
> Para actualizar las versiones que ya tenes es update, para pasar de una version mas nueva de paquetes es upgrade.

sip, sabia, gracias igual... el check no lo conocía

```
leandro@Leandro-Laptop:~$ sudo apt-get check
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho

```

Cosa 'e mandinga no?

---

### Post by guillermolisi on 2009-10-07
> **SLA_leandrin said:**
> sip, sabia, gracias igual... el check no lo conocía

```
leandro@Leandro-Laptop:~$ sudo apt-get check
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho

```Cosa 'e mandinga no?
Sep. la verdad que es bien raro.

Sera cosa de buscar en otros foros, google, etc. pero de alguna forma se debe poder arreglar.

---

### Post by staar on 2009-10-07
no creo que sea un problema de dependencias, porque tengo el mismo problema en archlinux, creo que es un bug en KDE, temporalmente los solucioné configurando CUPS desde su interfaz http (en [http://localhost:631](http://localhost:631))

saludos

---

### Post by guillermolisi on 2009-10-07
> **staar said:**
> no creo que sea un problema de dependencias, porque tengo el mismo problema en archlinux, creo que es un bug en KDE, temporalmente los solucioné configurando CUPS desde su interfaz http (en [http://localhost:631](http://localhost:631))

saludos
Yo tampoco creo que se de dependencias sino SLA_Leandrin se hubiera dado cuenta, pero por las dudas y en funcion de los mensajes que recibio, mejor asegurarse que esta todo lo que tiene que estar y esta bien todo lo que esta. Como para empezar sobre una base solida.

La pregunta es, porque el tiene ese problema y otros, como yo, con la misma version no ?
Si fuera un bug lo seria para todos (con las observaciones del caso ya que cada instalacion es un mundo aparte).

Las librerias de HP no generaran conflicto ?

---

### Post by SLA_leandrin on 2009-10-07
OK gracias muchachos.. será cups o HPtoolbox entonces lo que usaré.

Saludos.
LS

---

### Post by staar on 2009-10-07
> **guillermolisi said:**
> Las librerias de HP no generaran conflicto ?
no las tengo instaladas (mi impresora es epson)

googleando un poco encontré el bug reportado en [debian]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=542650") y en [ubuntu]("https://bugs.launchpad.net/ubuntu/+source/kdeadmin/+bug/383517"), y en teoría tendría que estar solucionado con una de las últimas actualizaciones del paquete system-config-printer-common, pero sigue sin andar...

saludos

---

