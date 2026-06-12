---
title: "Actualizar Dropbox a la version 1.0.10 Stable"
date: 2010-12-18
forum: Software
---

### Post by Pan0ramix on 2010-12-18
Para aquellos que utilizan Dropbox como sincronización de archivos via internet.

No hay necesidad de descargar paquetes desde el sitio ([www.dropbox.com]("http://www.dropbox.com")). Aqui los pasos a seguir para una actualización suave:

Sólo abran un Terminal y detengan el proceso de dropbox ejecutando:

$ dropbox stop

El proceso Dropbox no debería estar corriendo, confirmen con: 

$ status

debería leerse: "Dropbox is not running"

Entonces le dan este otro comando:

$ rm -r ~/.dropbox-dist/

y luego

$ dropbox start -i 

El proceso comenzará por descargar los archivos necesarios para llevar a cabo la actualización. El proceso de Dropbox se reanudará nuevamente. alli podrán volver a configurar el servicio.
¿qué tienen de nuevo?
Pues dos cosas importantes, entre otros trabajos del motor de sincronización:

1. Consume un 25% menos de memoria RAM que su versión anterior.

2. Aparece la opción de sincronizar carpetas seleccionadas para mantener sólo aquellas que nos interesen, sin necesidad de descargar todas aquellas que no serán utilizadas en el ámbito de la computadora que se encuentre asociada al servicio.

Esto último es muy útil cuando trabajamos en diferentes ambientes: Win/Linux/Mac y usamos dropbox en todos ellos para mantener sincronizados distintos tipos de archivos. Muy útil y recomendable esta aplicación. 

Y tiene hasta 2 GB gratis de sincronización.

And that's it! Enjoy

---

