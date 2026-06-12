---
title: "Actualizar un Ubuntu 11.10 instalado con Wubi en una netbook con win7"
date: 2012-04-13
forum: Software
---

### Post by techapu on 2012-04-13
Necesito un consejo! En una netbook Asus Eee con Win7 instalé el Ubuntu 11.10 pero desde Wubi. Y ahora descargué la beta2 del 12.04 y quiero actualizar. Como procederían Uds?
Entre a Win y no encuentro una aplicación Wubi con que administrar la nueva versión que tengo en el pendrive.
Cuando corro el Wubi desde el pendrive dentro de Win, como lo instalé la vez pasada, me aparece la opción de probar el livecd e instalar desde ahí, reiniciando, pero no la opción de instalarlo desde dentro de Win.
Cuando reinicio, me entra como para probar el sistema, le doy a la opción instalar Ubuntu y me da tres posibilidades, ninguna de ellas es actualizar. No me reconoce que esté instalado el Ubuntu 11.10 en la net. La opción más posible, instalar junto con el otro OS, me pone un botón que dice "salir" y al lado otro "reiniciar para instalar". Pero sólo está habilitado el botón que dice salir! 
Cuando reinicio desde el panel, reinicia, pero no como parte de un proceso de instalación: empieza todo de cero.
Así que pensé en actualizar con el update-manager -d, desde Ubuntu, y ahí hacer apt-get dist-upgrade porque ahí sí me da la opción de actualizar al 12.04. Pero tiene que descargar todos los datos de nuevo! No hay una forma de usar los datos de la iso que tengo en el pendrive?
O Uds. actualizarian de otra manera?
O me conviene desinstalar el Ubuntu 11.10 desde Win7, y hacer una instalación pura? Si lo hago, nunca voy a aprender si podría haber actualizado el SO instalado desde Wubi. Gracias. 
Gracias.

---

### Post by bcbc on 2012-04-13
1. You cannot upgrade a Wubi install from Windows. You can only replace a Wubi install in this way.
2. Wubi installs from a CD have been [disabled in 12.04]("https://bugs.launchpad.net/wubi/+bug/975251")
3. You can't upgrade from the Desktop CD. Only from the [Alternate CD]("https://help.ubuntu.com/community/PreciseUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD").
4. You have to upgrade from Ubuntu, not from Windows.

If you upgrade the Wubi install, be aware that this has not been fully tested. To make it safer:
1. backup your \ubuntu\disks directory first
2. if it fails, you can copy it back.

Google translate:

1. No es posible actualizar una instalación Wubi desde Windows. Sólo se puede sustituir una instalación Wubi de esta manera.
2. Wubi se instala desde un CD se han desactivado en 12,04
3. No se puede actualizar desde el CD Desktop. Sólo desde el CD Alternate.
4. Usted tiene que actualizar de Ubuntu, no desde Windows.

Si se actualiza la instalación de Wubi, tenga en cuenta que esto no ha sido plenamente probado. Para que sea más seguro:
1. una copia de seguridad \ ubuntu \ discos directorio de primera
2. si no, se puede copiar de nuevo.

---

