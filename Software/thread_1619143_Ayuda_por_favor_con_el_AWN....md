---
title: "Ayuda por favor con el AWN..."
date: 2010-11-11
forum: Software
---

### Post by juakel on 2010-11-11
[B][SIZE=3]que tal gente de esta comunidad...? bueno antes que nada me presento en esta comunidad ya que soy nuevo y decidi independizarme del horroroso windows de una vez por todas...
Esta mañana instale la ultima version del ubuntu la 10.10, la instale y anda de maravilla, me encanto, luego empece a hacerle unos retoques en la apariencia, mientras iba leyendo algunos tutoriales. Hasta ahi todo perfecto, hasta que instale el dock AWN, al principio andaba bien, luego lei unos tips que habia por ahi para actualizarlo y descargar e instalar unos themes para el AWN. Bueno resulta que despues cuando quise instalar Compiz mediante el centro de sofware de ubuntu no podia y no puedo instalar ni eliminar nada, porque cada vez que entro al centro de sofware me dice:[/SIZE][/B]

[SIZE=3][COLOR=Red][COLOR=Blue]LOS ELEMENTOS NO SE PUEDEN INSTALAR O ELIMINAR HASTA QUE EL CATALOGO DE PAQUETES NO ESTE REPARADO ¿QUIERE REPARARLO AHORA?[/COLOR]
[/COLOR][/SIZE]
[SIZE=3][COLOR=Black]le doy en reparar y me dice:[/COLOR][/SIZE]

[SIZE=3][COLOR=Blue]FALLO LA OPERACION CON EL PAQUETE[/COLOR][/SIZE]

[SIZE=3][COLOR=Black]le doy en detalles y dice:[/COLOR][/SIZE]

[SIZE=2][COLOR=Blue]installArchives() failed: (Leyendo la base de datos ...  (Leyendo la base de datos ... 5% (Leyendo la base de datos ... 10% (Leyendo la base de datos ... 15% (Leyendo la base de datos ... 20% (Leyendo la base de datos ... 25% (Leyendo la base de datos ... 30% (Leyendo la base de datos ... 35% (Leyendo la base de datos ... 40% (Leyendo la base de datos ... 45% (Leyendo la base de datos ... 50% (Leyendo la base de datos ... 55% (Leyendo la base de datos ... 60% (Leyendo la base de datos ... 65% (Leyendo la base de datos ... 70% (Leyendo la base de datos ... 75% (Leyendo la base de datos ... 80% (Leyendo la base de datos ... 85% (Leyendo la base de datos ... 90% (Leyendo la base de datos ... 95% (Leyendo la base de datos ... 100% (Leyendo la base de datos ...   
124252 ficheros y directorios instalados actualmente.) 
Desempaquetando awn-applets-common-trunk (de .../awn-applets-common-trunk_0.4.1~bzr1476+201011032003~maverick1_i386.deb) ... 
dpkg: error al procesar /var/cache/apt/archives/awn-applets-common-trunk_0.4.1~bzr1476+201011032003~maverick1_i386.deb (--unpack): 
 intentando sobreescribir «/usr/share/locale/cs/LC_MESSAGES/awn-extras.mo», que está también en el paquete awn-applets-common 0.4.0+bzr1372-0ubuntu3 
dpkg-deb: el subproceso pegar fue terminado por la señal (Tubería rota) 
Se encontraron errores al procesar: 
 /var/cache/apt/archives/awn-applets-common-trunk_0.4.1~bzr1476+201011032003~maverick1_i386.deb 
dpkg: problemas de dependencias impiden la configuración de python-awn-extras-trunk: 
 python-awn-extras-trunk depende de awn-applets-common-trunk; sin embargo: 
  El paquete `awn-applets-common-trunk' no está instalado. 
dpkg: error al procesar python-awn-extras-trunk (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de awn-applets-c-extras-trunk: 
 awn-applets-c-extras-trunk depende de awn-applets-common-trunk; sin embargo: 
  El paquete `awn-applets-common-trunk' no está instalado. 
dpkg: error al procesar awn-applets-c-extras-trunk (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de awn-applets-c-core-trunk: 
 awn-applets-c-core-trunk depende de awn-applets-common-trunk; sin embargo: 
  El paquete `awn-applets-common-trunk' no está instalado. 
dpkg: error al procesar awn-applets-c-core-trunk (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de awn-applets-python-extras-trunk: 
 awn-applets-python-extras-trunk depende de awn-applets-common-trunk; sin embargo: 
  El paquete `awn-applets-common-trunk' no está instalado. 
 awn-applets-python-extras-trunk depende de python-awn-extras-trunk (>= 0.3.8); sin embargo: 
 El paquete `python-awn-extras-trunk' no está configurado todavía. 
dpkg: error al procesar awn-applets-python-extras-trunk (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de awn-applets-python-core-trunk: 
 awn-applets-python-core-trunk depende de awn-applets-common-trunk; sin embargo: 
  El paquete `awn-applets-common-trunk' no está instalado. 
 awn-applets-python-core-trunk depende de python-awn-extras-trunk (>= 0.3.8); sin embargo: 
 El paquete `python-awn-extras-trunk' no está configurado todavía. 
dpkg: error al procesar awn-applets-python-core-trunk (--configure): 
 problemas de dependencias - se deja sin configurar 
Se encontraron errores al procesar: 
 python-awn-extras-trunk 
 awn-applets-c-extras-trunk 
 awn-applets-c-core-trunk 
 awn-applets-python-extras-trunk[/COLOR][/SIZE]

[SIZE=3][COLOR=Black]y ese error no me deja desintalar ni instalar nada, si abro la terminal y le pongo que desisntale el awn me sale:[/COLOR][/SIZE]

[SIZE=2][COLOR=Blue]sudo apt-get remove avant-window-navigator
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete avant-window-navigator no esta instalado, no se eliminará
Tal vez quiera ejecutar 'apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 awn-applets-c-core-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
 awn-applets-c-extras-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
 awn-applets-python-core-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
 awn-applets-python-extras-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
 python-awn-extras-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especifique una solución).[/COLOR][/SIZE]

[SIZE=3][COLOR=Black]si le doy para que lo vuelva a instalar me sale:[/COLOR][/SIZE]

[SIZE=2][COLOR=Blue]sudo apt-get install avant-window-navigator
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar 'apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 avant-window-navigator : Depende: libawn1 (>= 0.4.0) pero no va a instalarse
                          Depende: avant-window-navigator-data (>= 0.4.0-2ubuntu1) pero no va a instalarse
                          Recomienda: awn-applets-python-core pero no va a instalarse
                          Recomienda: awn-applets-c-core pero no va a instalarse
                          Recomienda: awn-settings (>= 0.4.0-2ubuntu1) pero no va a instalarse
 avant-window-navigator-trunk : Entra en conflicto: avant-window-navigator pero 0.4.0-2ubuntu1 va a ser instalado
 awn-applets-c-core-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
 awn-applets-c-extras-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
 awn-applets-python-core-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
 awn-applets-python-extras-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
 python-awn-extras-trunk : Depende: awn-applets-common-trunk pero no va a instalarse
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especifique una solución).
[/COLOR][/SIZE]

[SIZE=3][COLOR=Black]pareciera que hay un problema con el awn trunk que no se lo que es...
bueno si alguien sabe que se puede hacer, le pediria que me explique, y desde ya muchas gracias por su tiempo...[/COLOR][/SIZE]

---

### Post by Wiredfixer on 2010-11-11
ya hiciste esto?

El paquete avant-window-navigator no esta instalado, no se eliminará
Tal vez quiera ejecutar 'apt-get -f install' para corregirlo:

Ahi te lo pide... deberias tratar con eso.

---

### Post by juakel on 2010-11-13
si ya probe con el sudo apt-get -f install, pero logre solucionarlo en sistema>administracion> gestor de paquetes synaptic con eso se soluciono, haba unos paquetes rotos del awn...

ya esta solucionado, igual muchas gracias...

---

