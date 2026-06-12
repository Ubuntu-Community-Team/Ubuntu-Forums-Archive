---
title: "Paquete roto por instalación forzada"
date: 2010-09-28
forum: Software
---

### Post by kornykyano on 2010-09-28
Hola gente, nunca he realizado una instalación forzada hasta hoy...y bue así me fue. Quise probar impressive y keyjnote (sirve para hacer presentaciones de un pdf). Descargue el .deb y como no podía instalarse solo porque dependía de python-support, los obligue a los dos con! como habia visto en otros thread:

```
sudo dpkg -i --force-all keyjnote_0.10.3~WIP+svn31-1_all.deb
sudo dpkg -i --force-all impressive_0.10.3~WIP+svn31-1_all.deb
```

pero resulta que después ya no pude actualizar el sistema (no me acuerdo el mensaje que decía. Por lo tanto intente desinstalar (no se porque lo hice desde synaptic) a los dos anteriores, del cual impressive no me deja desde synaptic o con la terminal, vean los resultados:

```
XXX@XXX:~$ sudo apt-get install -f
[sudo] password for XXX: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Los siguientes paquetes se ELIMINARÁN:
  impressive
0 actualizados, 0 se instalarán, 1 para eliminar y 3 no actualizados.
1 no instalados del todo o eliminados.
Se liberarán 410kB después de desempaquetar.
¿Desea continuar [S/n]? 
(Leyendo la base de datos ...  
269690 ficheros y directorios instalados actualmente.)
Desinstalando impressive ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/impressive.private is not a directory
dpkg: error al procesar impressive (--remove):
 el subproceso pre-removal script devolvió el código de salida de error 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/impressive.private is not a directory
dpkg: error al reorganizar:
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 impressive
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Ademas haciendo:

```
XXX@XXX:~$ sudo apt-get upgrade
[sudo] password for XXX: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar `apt-get -f install' para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
  impressive: Depende: python-support (>= 0.90.0) pero 0.7.5ubuntu1 está instalado
E: Dependencias incumplidas. Pruebe de nuevo usando -f.
```

Quiero deshacerme de impressive y como ya no se que hacer acudo a la sabiduría de ustedes  ... :(

PD:tengo ubuntu 8.04.4

---

### Post by juancarlospaco on 2010-09-28
Peroooo si le pones apt-get purge que te dice?

---

### Post by kornykyano on 2010-09-29
> **juancarlospaco said:**
> Peroooo si le pones apt-get purge que te dice?

Lo mismo que: **sudo apt-get install -f** o **sudo apt-get -f install**

---

### Post by kornykyano on 2010-09-29
Tengo una solución parcial:

1. dpkg --listfiles <nombre del paquete>

    Buscar cada fichero que se instaló y a continuación buscarlos y eliminarlos. 

2. Editar el archivo /var/lib/dpkg/status

    Eliminar la sección del paquete seriamente dañado (Hacer una copia de seguridad antes de editar el archivo) 

3. Editar el archivo /var/lib/dpkg/available

    Eliminar la sección del paquete seriamente dañado (Hacer una copia de seguridad antes de editar el archivo) 

[http://www.mepis.org/docs/es/Reparar_la_base_de_datos_de_apt-get]("http://www.mepis.org/docs/es/Reparar_la_base_de_datos_de_apt-get")

---

