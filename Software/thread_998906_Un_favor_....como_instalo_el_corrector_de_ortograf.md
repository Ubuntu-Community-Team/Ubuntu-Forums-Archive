---
title: "Un favor ....como instalo el corrector de ortografia"
date: 2008-12-01
forum: Software
---

### Post by EDGAR MORENO on 2008-12-01
Saludos amigos de ubuntu , espero que este diciembre este lleno de gratas sorpresas para todas y todos los compañeros del foro,

 :confused::confused::confused::confused:les pido el favor de quien sepa como   activar (spellcheck) el corrector de ortografia en español , en el programa de openOffice.org Writer ,en mi computadora esta desactivado , me pueda guiar , gracias de antemano por esta informacion tan util :lolflag::confused:

---

### Post by opscure on 2008-12-01
"File -> Wizards -> Install new dictionaries"

Spanish dictionary:
[http://wiki.services.openoffice.org/wiki/Dictionaries#Spanish_.28Spain.2C_....29]("http://wiki.services.openoffice.org/wiki/Dictionaries#Spanish_.28Spain.2C_....29")

---

### Post by rojojuan on 2008-12-01
Si tenés problema con el asistente (te deja ver una ventana muy chica con la que no podés operar), es un bug que tiene Openoffice con Compiz. 
Tenés que desactivar Compiz (Sistema, Preferencias, Apariencia, Efectos Visuales, Normal), entonces la ventana se ve bien y podés instalar el diccionario. 
Después volver a setear Compiz.

---

### Post by EDGAR MORENO on 2008-12-02
estoy en este paso pero no se como hacerlo 
DicOOo 
Versión 1.8

DicOOo es un mago que permite instalar diccionarios faltantes. 

Pulse el botón para ejecutar el asistente de DicOOo:




Cuando termine, salga de OpenOffice.org y el Inicio rápido de OpenOffice.org. Reinicie OpenOffice.org y vaya al cuadro de diálogo del menú Herramientas>Opciones>Configuración del Idioma>Lingüística y seleccione los nuevos diccionarios.

See installation details

Este asistente está disponible bajo los términos de la licencia LGPL, que se puede ver aquí: 
[http://www.opensource.org/licenses/lgpl-license.php](http://www.opensource.org/licenses/lgpl-license.php)
Autor: Laurent Godard &#8211; © 2003-2007 &#8211; [email]LaurentGodard@openoffice.org[/email]


Nota para losdetalles 18:01 usuarios


La instalación en Modo Administrador necesita permiso de escritura en el directorio:
	<OOo>/share/dict/ooo
y en el fichero:
	<OOo>/share/dict/ooo/dictionary.lst

*NO TENGO LA MENOR IDEA DE COMO HACER LO ANTERIO ,¿DONDE SE EJECUTA ESE PERMISO? QUE VENTANA ABRO? *
Si actualiza la versión del asistente DicOOo, puede que tenga que cerrar el fichero del asistente y volver a abrirlo para que funcione.
MacOs X: la utilidad del sistema unzip debe estar disponible (gracias a Riccardo losselli)
Debian GNU/Linux: (gracias a Claude)
Si está usando una versión de OOo empaquetada por Debian (.deb), por favor, dése cuenta de que para usar el asistente, tiene que borrar primero el enlace simbólico @dictionary.lst en el directorio:
	/usr/lib/openoffice/share/dict/ooo
y copiar en su lugar el fichero dictionary.lst ya existente que está en :
	/etc/openoffice
Para hacer esto, necesita ser root.
También necesita dar permisos de escritura en el fichero dictionary.lst, si quiere que los usuarios puedan instalar diccionarios:
	chmod go+w dictionary.lst
También, si los usuarios pertencen al grupo « users »:
	chown root.users dictionary.lst
También puede iniciar el asistente como root, si no quiere que los usuarios puedan añadir diccionarios.

---

### Post by chalito on 2008-12-02
probaste hacer:
sudo apt-get install openoffice.org-l10n-es

 ?

---

### Post by EDGAR MORENO on 2008-12-02
> **chalito said:**
> probaste hacer:
sudo apt-get install openoffice.org-l10n-es

 ?
estimado amigo Chalito, tengo que contarte que soy un completo ignorante en este asunto, mi generacion no recibio ninguna enseñanza al respecto (estudie bachillerato con regla de calculo, ni siquiera habia calculadoras de bolsillo) y ahora que tengo esta maravilla de tecnologia , estoy apenas comenzando a usarla , por ello no te entiendo lo que me quieres decir, por ejemplo, no se que es lo que que me tratas de decir , por ello te pido que tengas paciencia conmigo y me digas paso a paso de que se trata, gracias por la comprension a mi ignorancia ,pero con la ayuda de uds, espero poder hacer funcionar esto de la ortografia 

saludos

---

### Post by EDGAR MORENO on 2008-12-02
muchas gracias amigos ya pude instalar el sistema ,muchas gracias a los que me ayudaron 

saludos a proposito hago caricaturas y los invito a ver mis dibujos este es mi blog 
[http://caricaturasedgar.blogspot.com/](http://caricaturasedgar.blogspot.com/)

saludos

---

