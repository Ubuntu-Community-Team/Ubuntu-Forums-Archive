---
title: "Problema con Amarok al iniciar"
date: 2013-08-31
forum: Uruguay Team
---

### Post by Pablo_Mederos on 2013-08-31
Hola, muy buen foro, luego de tanto leer por aquí me animé a hacer una pregunta de la que no he tenido respuesta.

Tengo Kubuntu 12.04
Resulta que al intentar iniciar amarok este simplemente no inicia.
Intenté desinstalarlo, y volver a instalarlo pero no hubo solución.
Esto ocurrió tras un problema con la base de datos, por lo que procedí a añadirle una base de datos externa mediante mysql, luego de esto amarok no inicia. lo único que hice fue crear la base de datos y añadirla la configuración de amarok.

al iniciarlo en Konsole Me pone:

> 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
"/org/freedesktop/UDisks2/drives/ZTE_MMC_Storage_P671A2CLAD010000" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/ZTE_MMC_Storage_P671A2CLAD010000" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/Floppy_Drive" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/Floppy_Drive" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/MAXTOR_STM3250310AS_6RY586XM" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/MAXTOR_STM3250310AS_6RY586XM" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/ZTE_MMC_Storage_P671A2CLAD010000" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/Floppy_Drive" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/MAXTOR_STM3250310AS_6RY586XM" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/MAXTOR_STM3250310AS_6RY586XM" : property "Table" does not exist 
"/org/freedesktop/UDisks2/drives/Floppy_Drive" : property "Table" does not exist 
QWidget::insertAction: Attempt to insert null action
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 7 (X_ReparentWindow)
  Resource id:  0xe001cc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 7 (X_ReparentWindow)
  Resource id:  0xe001cc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 7 (X_ReparentWindow)
  Resource id:  0xe001cc
X Error: RenderBadPicture (invalid Picture parameter) 160
  Extension:    148 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0xaf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 10 (X_UnmapWindow)
  Resource id:  0xe000d9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 7 (X_ReparentWindow)
  Resource id:  0xe000d9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe000d9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 4 (X_DestroyWindow)
  Resource id:  0xe000d9
X Error: RenderBadPicture (invalid Picture parameter) 160
  Extension:    148 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0xe000d9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 10 (X_UnmapWindow)
  Resource id:  0xe000db
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 7 (X_ReparentWindow)
  Resource id:  0xe000db
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe000db
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 4 (X_DestroyWindow)
  Resource id:  0xe000db
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 10 (X_UnmapWindow)
  Resource id:  0xe000dd
X Error: RenderBadPicture (invalid Picture parameter) 160
  Extension:    148 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0xe000dd
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 10 (X_UnmapWindow)
  Resource id:  0xe000dd
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 7 (X_ReparentWindow)
  Resource id:  0xe000dd
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 7 (X_ReparentWindow)
  Resource id:  0xe000e1
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe000dd
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 4 (X_DestroyWindow)
  Resource id:  0xe000dd
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 12 (X_ConfigureWindow)
  Resource id:  0xe000e1
Could not parse stylesheet of widget 0x8940150
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 12 (X_ConfigureWindow)
  Resource id:  0xe000e1
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 12 (X_ConfigureWindow)
  Resource id:  0xe000e1
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 12 (X_ConfigureWindow)
  Resource id:  0xe000e1
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    136 (Uknown extension)
  Minor opcode: 3 (Unknown request)
  Resource id:  0xe000e1
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    136 (Uknown extension)
  Minor opcode: 12 (Unknown request)
  Resource id:  0xe000e1
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    136 (Uknown extension)
  Minor opcode: 7 (Unknown request)
  Resource id:  0xe000e1
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 8 (X_MapWindow)
  Resource id:  0xe000e1
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 12 (X_ConfigureWindow)
  Resource id:  0xe000e1
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    136 (Uknown extension)
  Minor opcode: 7 (Unknown request)
  Resource id:  0xe000e1
amarok: swrast/s_renderbuffer.c:588: map_attachment: La declaración `srb->Map' no se cumple.
unnamed app(8834): Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 

pablomederos@pablomederos-G31-M7-TE:~$ KCrash: Application 'amarok' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/pablomederos/.kde/socket-pablomederos-G31-M7-TE/kdeinit4__0
QSocketNotifier: Invalid socket 57 and type 'Read', disabling...
QSocketNotifier: Invalid socket 46 and type 'Read', disabling...



Alguna idea?

Muchas gracias!

---

### Post by Pablo_Mederos on 2013-09-01
A fin de cuentas pude solucionar el problema de amarok añadiendo una excepción en el panel de Oxygen-transparent, lo que no he logrado es entender cómo es que todo funcionaba sin problemas hasta ahora, y de repente este bug. Espero que lo solucionen, y se agradece el trabajo del foro.

---

