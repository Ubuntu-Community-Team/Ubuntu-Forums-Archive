---
title: "Ayuda con instalación de Tor y Privoxi"
date: 2009-07-01
forum: Software
---

### Post by pablo3821 on 2009-07-01
Hola!
Estoy intentando instalar Tor y Privoxy ya que necesito mandar datos confidenciales y no me basta con encriptarlos pero cuando en la terminal le doy 

$sudo apt-get install -y tor

me sale el siguiente error y no se que hacer

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  tor: Depende: libc6 (> 2.9) pero 2.7-10ubuntu4 va a ser instalado
       Entra en conflicto: libssl0.9.8 (< 0.9.8g-9) pero 0.9.8g-4ubuntu3.7 va a ser instalado
E: Paquetes rotos

Cualquier sugerencia es bienvenida
Gracias

---

### Post by guillermolisi on 2009-07-01
> **pablo3821 said:**
> Hola!
Estoy intentando instalar Tor y Privoxy ya que necesito mandar datos confidenciales y no me basta con encriptarlos pero cuando en la terminal le doy 

$sudo apt-get install -y tor

me sale el siguiente error y no se que hacer

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  tor: Depende: libc6 (> 2.9) pero 2.7-10ubuntu4 va a ser instalado
       Entra en conflicto: libssl0.9.8 (< 0.9.8g-9) pero 0.9.8g-4ubuntu3.7 va a ser instalado
E: Paquetes rotos

Cualquier sugerencia es bienvenida
Gracias

Antes de la instalacion, hiciste un apt-get update ?

Por que instalas con la opcion -y ?
Probaste de hacerlo sin esa opcion para ver si te pregunta algo ?

Que version de Tor estas usando ?
Que version de Ubuntu ?

---

