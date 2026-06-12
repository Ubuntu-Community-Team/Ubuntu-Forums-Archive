---
title: "Ubuntu 11.10 - Añadir impresora de red - &quot;FirewallD no está en ejecución&quot;"
date: 2011-10-12
forum: Software
---

### Post by marohds on 2011-10-12
Hola amigos,

Ayer instalé Ubuntu 11.10 Oneiric Ocelot y me surgió la siguiente cuestión:

Cuando quiero instalar una impresora de red a través del menú

Configuración del Sistema -> Impresoras ->Añadir Impresora nueva -> Selecciono "De red"

me aparece el mensaje:

*"FirewallD no está en ejecución. La detección de impresoras de red necesita que los servicios  mdns, ipp, ipp-client y samba-client estén activados en el cortafuegos."*

Sé que el mensaje está bastante clarito, pero... cómo lo configuro? no encontré nada de info en internet (o busqué mal).

Les agradezco cualquier ayuda.

Abrazo!

---

### Post by juancarlospaco on 2011-10-13
Instalaste TODAS las actualizaciones ...?, no hay que olvidar que no era Final Release... (todavia)

---

### Post by marohds on 2011-10-13
Si, instalé todas las actualizaciones...

De todos modos, seguí buscando y, de manera alternativa, pude instalar la impresora a través de CUPS con [http://localhost:631](http://localhost:631).

Sin embargo, acabo de intentar nuevamente realizar la misma acción a través de la herramienta de Gnome pero no va... sigue igual...

No se si marcar el thread como "Solved" ya que el problema aún persiste...

---

### Post by maceiras on 2012-06-04
Lee mi post al respecto: [http://wp.me/p12q95-1v](http://wp.me/p12q95-1v)
En primer lugar, no le preste la más mínima atención al mensaje &#8220;FirewallD no está en ejecución. La detección de impresoras de red necesita que los servicios  mdns, ipp, ipp-client y samba-client estén activados en el cortafuegos.&#8220; No pierda tiempo alguno con el Firewall o Cortafuegos, Firestarter ni nada de ello.

---

