---
title: "Libre Office"
date: 2010-10-28
forum: Software
---

### Post by gmunioz on 2010-10-28
A partir de las dudas que genera la continuidad de OpenOffice
por la compra de toda la tecnología de Sun Microsystem (MySQL,
OpenOffice, OpenSolaris, etc)por parte Oracle y su conocida 
politica hacia las aplicaciones de código abierto (OpenSolaris
ya ha sido descartada) algunos desarrolladores de OpenOffice 
se reunieron y dieron vida a The Document Foundation.

Esta organización trabaja en el proyecto LibreOffice.
LibreOffice es una nueva suite ofimática basada en el código libre de OpenOffice.org.
The Document Foundation ya ha recibido el apoyo de Google,
Canonical,Red Hat y Novell, ha sido dejada de lado por Oracle
que no aceptó la invitación de colaborar en su desarrollo, al
que además perjudicial para sus intereses.
Entre los planes a corto plazo se espera que la próxima versión
de Ubuntu pueda incluir esta nueva suite ofimática Open Source.
Por lo pronto Go Open Office que es una redistribución de Open
Office que mejora muchos aspectos del mismo, compatible con 
Windows, Mac y Linux y de donde provienen los paquetes de 
Ubuntu, Debian, OpenSuse, ha decidido discontinuar este
proyecto para continuar con el desarrollo de Libre Office. 

Para quién se interese en descargarla para ir probándola, 
ya está disponible su versión Beta 2 en [www.documentfoundation.org](www.documentfoundation.org)

Sitio de la suite:
[http://download.documentfoundation.org/](http://download.documentfoundation.org/)

Paquetes a descargar para Ubuntu de 32

[http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb/x86/](http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb/x86/)
LibO_3.3.0_beta2_Linux_x86_install-deb_en-US.tar.gz

[http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb/x86/](http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb/x86/)
LibO_3.3.0_beta2_Linux_x86_langpack-deb_es.tar.gz

Disponibles también para arquitectura de 64, otros idiomas, Windows y MAC

Descargados los archivos .tar.gz con los paquetes deb en su
interior, se descomprimen, simplemente pulsando con el mouse desde Nautilus
Una vez descomprimidos en el directorio (carpeta) en-US/DEBSm
desde una consola se cambia a ese directorio y se ejecuta la
orden

sudo dpkg -i *.deb

Cambiando luego al directorio (carpeta) desktop-integration 
y ejecutando la orden (comando)

sudo dpkg -i *.deb

El mismo procedimiento se utiliza para los paquetes de idiomas

Luego de esto en Aplicaciones -- Oficina junto con los de OpenOffice se encontraran 
los accesos a LibreOffice.

Decidido su uso exclusivo se desinstala Openoffice con la 
orden en consola

sudo apt-get remove --purge openoffice*.*

Para poder separar silabas y buscar sinónimos.
Ir al sitio de extensiones de OpenOffice:

[http://extensions.services.openoffice.org/project/es_ANY-HyphThes](http://extensions.services.openoffice.org/project/es_ANY-HyphThes)

Guardar el archivo en un directorio e instalarlo como una extensión de LbreOffice:

Herramientas -- Administrador de extensiones -- Añadir

Se localiza el archivo en el directorio donde se escargó/guardó
se pulsa el botón Abrir y listo, ya se debería poder buscar sinónimos y poner guiones.

Fuente:[http://www.ubuntu-es.org/node/143190](http://www.ubuntu-es.org/node/143190)

---

