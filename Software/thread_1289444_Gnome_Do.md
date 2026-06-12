---
title: "Gnome Do"
date: 2009-10-12
forum: Software
---

### Post by RafaelG on 2009-10-12
Hola a todos los companeros Ubunteros, bueno Tuve el Siguiente problema con Gnome Do al momento de mover algunas preferencias especificamente en Plugings la aplicacion desaparecio y cuando intento volver abrir la aplicacion aparece pero desaparece rapidamente. Mi OS es Karmic Beta.

Me despido coordialmente de todos agradeciendo ante mano su ayuda o comentarios para solucionar mi Thread.

---

### Post by moreback on 2009-10-12
¿Intentaste ejecutar gnome-do en una consola para ver qué error está tirando?

---

### Post by RafaelG on 2009-10-12
> **moreback said:**
> ¿Intentaste ejecutar gnome-do en una consola para ver qué error está tirando?

Aqui esta lo que arroja la consola

[B]eligonzalez@ergg:~$ gnome-do

(Do:2795): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Could not locate Tomboy on D-Bus. Perhaps it's not running?
[Debug 20:04:51.116] Acquiring org.freedesktop.DBus session instance
[Debug 20:04:51.126] Starting org.bansheeproject.CollectionIndexer
[Error 20:04:51.124] Could not read Epiphany Bookmarks file /home/eligonzalez/.gnome2/epiphany/bookmarks.rdf: Could not find a part of the path "/home/eligonzalez/.gnome2/epiphany/bookmarks.rdf".

Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bansheeproject.CollectionIndexer was not provided by any .service files
  at IBusProxy.StartServiceByName (System.String flags, UInt32 ) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name, UInt32 flags) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name) [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.IndexerClient.Start () [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.SimpleIndexerClient.Start () [0x00000] 
[/B]

---

### Post by moreback on 2009-10-13
Por el error que te da creo que tienes problemas con el plugin de Banshee, ¿Seguro que tienes instalado Banshee?

La verdad es que no sé como desactivar los plugins del gnome-do, pero podrías intentar borrar los siguientes directorios (si es que instalando Banshee no se resuelve):

$HOME/.local/share/gnome-do
$HOME/.config/gnome-do

Saludos.

---

### Post by RafaelG on 2009-10-14
> **moreback said:**
> Por el error que te da creo que tienes problemas con el plugin de Banshee, ¿Seguro que tienes instalado Banshee?

Hola Moreback gracias por los Comentarios, bueno descarge Banshee y ahora Gnome Do trabaja sin problema muchas gracias por los comentarios hasta la proxima...

---

