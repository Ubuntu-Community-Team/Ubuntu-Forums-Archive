---
title: "Ubuntu 9 entra en Google solamente"
date: 2009-05-26
forum: Software
---

### Post by flakojaime on 2009-05-26
Hola.

Bueno, intente solucionar el detalle con San Google y no funciono.

Les cuento.

Por medio de conexiones inalambricas, la internet funciona en firefox y en el sistema para bajar paquetes y todo. Ni un problema.

Por medio de una conexion adsl ethernet (telefonica chile) de 4 Mb, firefox solo entra a google.

El amsn tampoco conecta.

No habia probado la conexion adsl. Configure una conexion nueva donde ingrese usuario y contraseña. 

Uso Ubuntu 9.04 Actualizado
Tarjeta Ethernet Bradcom Nextreme BCM5754M PCI express.
Notebook Dell XPS m1730

Gracias.

---

### Post by felipeleven on 2009-05-26
> **flakojaime said:**
> Hola.

Bueno, intente solucionar el detalle con San Google y no funciono.

Les cuento.

Por medio de conexiones inalambricas, la internet funciona en firefox y en el sistema para bajar paquetes y todo. Ni un problema.

Por medio de una conexion adsl ethernet (telefonica chile) de 4 Mb, firefox solo entra a google.

El amsn tampoco conecta.

No habia probado la conexion adsl. Configure una conexion nueva donde ingrese usuario y contraseña. 

Uso Ubuntu 9.04 Actualizado
Tarjeta Ethernet Bradcom Nextreme BCM5754M PCI express.
Notebook Dell XPS m1730

Gracias.

En una de esas, la conexión por adsl no funciona, puede que firefox guarde en caché la página de google y sin conexión esta abra, eso me "tinca", al menos que me digas que puedes hacer búsquedas por google a través del adsl.

También puedes detallar cual fue el procedimiento que utilizaste para crear la conexión adsl, si por network-manager o por consola, etc, mejor si lo explicas paso a paso.

Saludos

---

### Post by Carlos C on 2009-05-26
¿cuando buscas algo en google, obtienes resultados?

---

### Post by flakojaime on 2009-05-26
Hola

> **Carlos C said:**
> ¿cuando buscas algo en google, obtienes resultados?

Cuando hago consultas por google, si me las da. Cualquier consulta me da los resultados.

Configure adsl por medio de NM.

1.- Abri NM

2.- pestaña DSL y AÑADIR.

3.- Pestaña DLS: Puse usuario, contraseña y servicio (le puse terra). Marque conectar automaticamente, mostrar la contraseña y disponible para todos los usuarios.

4.-Pestaña CABLEADA, no modifique nada. No hay nada escrito en direccion MAC y **MTU automatico**.

5.- Pestaña AJUSTES PPP no modifique nada. Esta marcado:
   * Permitir compresion de datos punto a punto.
   * Permitir compresion de datos deflate.
   * Usar compresion de cabeceras TCP.
No esta marcado:
* Usar cifrado punto a punto.
* Enviar paquetes echo PPP
Atentificacion metodos esta marcado: EAP, PAP, CHAP, MSCHAPv2, MSCHAP

6.- Pestaña AJUSTES IPv4, no modifique nada. Metodo automatico (PPPoE)
*En rutas IPv4 no hay nada escrito y esta desmarcado: **Ignorar rutas obtenidas automaticamente** y **Usar esta conexion solo para recursos en su red**.

Eso.

Saludos

---

### Post by Carlos C on 2009-05-26
es posible que tengas problemas con tu DNS. Te recomiendo que uses los dns de opendns. En este hilo expliqué cómo hacerlo:

[http://ubuntuforums.org/showpost.php?p=7316309&postcount=3](http://ubuntuforums.org/showpost.php?p=7316309&postcount=3)

Aun cuando en ese caso era lo contrario, no podía acceder a google, de todas maneras creo que tienes problemas con tu dns. Espero que sirva de algo.

---

### Post by flakojaime on 2009-05-27
Ok, gracias.

Pruebo y retroalimento.

---

### Post by felipeleven on 2009-05-27
Raro :(, yo uso conexión adsl de telefónica y tengo la misma configuración que tu y no sufro de ese problema.

Prueba poniendo en barra de dirección las siguientes páginas (en forma de IP) (sonó repetido XD):

[http://66.102.11.99/](http://66.102.11.99/)  (la de google españa)

[http://209.191.93.52/](http://209.191.93.52/)   (la de yahoo)

En caso de que te abra la página, sobre todo la de yahoo, es un problema de DNS.

---

### Post by felipeleven on 2009-05-27
se me adelantaron XDDD,

bueno pero de todas formas lo puedes diagnosticar de la forma que te puse.

Saludos y disculpas.

---

### Post by flakojaime on 2009-05-27
Ok, gracias.

Pruebo y retroalimento.

---

### Post by flakojaime on 2009-05-27
Yap.

Probe ingresando DNS en la conexion adsl:

208.67.222.222
208.67.220.220

Reinicie el pc y ahora no me deja ver ninguna pagina, ni google.

Voy a probar con las direcciones ip.

Saludos

---

