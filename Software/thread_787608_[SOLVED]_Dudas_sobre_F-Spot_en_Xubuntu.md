---
title: "[SOLVED] Dudas sobre F-Spot en Xubuntu"
date: 2008-05-09
forum: Software
---

### Post by santiagoward2000 on 2008-05-09
Hola!
Ahora que instalé Hardy se me dio por probar usar F-Spot en lugar de Picasa. La verdad que me está gustando, aunque todavía no probé todo. Pero tengo algunas dudas.
[LIST=1]
[*]**dbus-launch**
Empecemos por el principio. Cuando quiero abrirlo desde el menú Applications, me tira este error:
> **F-Spot Encountered a Fatal Error**
F-Spot cannot find the Dbus session bus. Make sure dbus is configured properly or start a new session for f-spot using "dbus-launch f-spot"
Si lo abro con el "dbus-launch f-spot" anda bien. Por ahora puse un ícono con ese comando para abrirlo. ¿Alguien me podría explicar por qué necesito el "dbus-launch"?


[*]**Mandar por mail**
Este es el problema más "serio" que tengo. Quise mandar unas fotos por mail para probarlo, pero cuando pongo "Send by Mail", me aparece una ventana para cambiar el tamaño de las fotos, aparece una barrita y después no pasa nada. Lo abrí desde una terminal para ver si había algún error, y me tira:
> GLib.GException: There was an error launching the default action command associated with this location.
  at Gnome.Url.Show (System.String url) [0x00000] 
  at FSpot.Utils.GnomeUtil.Show () [0x00000] 


[*]**Fechas de algunas fotos**
Esto no es tan importante, pero es medio molesto y no encontré cómo arreglarlo. Algunas de mis fotos figuran con cualquier fecha. Unas fotos que me mandaron el año pasado unos amigos del día que nevó en Bs.As. figuran que son del 19/4/2097, y unas que saqué ayer con mi celu del patio de casa tapado en cenizas figuran del 1/1/1980. Las abrí con Picasa en Windows y las fechas están bien. ¿Será que F-Spot tampoco cree que haya nevado en Bs.As. o que haya ceniza acá? Jeje ¿Hay alguna forma de cambiarlas?[/LIST]

Gracias!

---

### Post by Alejandro Vidal on 2008-05-09
Hola Santiago.
También estoy usando f-spot en xubuntu Hardy y me tira exactamente el mismo error.
En lo que respecta a enviar por mail nunca lo intenté pero esta noche voy a probarlo.
Lo que si te puedo confirmar es que la opción de enviar las fotos a un album web funciona a la perfección al menos con Picasa web albums. Ese es el motivo por el cual nunca envío una foto por mail.
Simplemente las subo al álbum web y luego las comparto con mis amigos y conocidos sin necesidad de llenarles la casilla con kbs.
El tema de las fechas siempre me resultó algo confuso pero el F-spot te permite corregirlo de a una o bien en bloque. Creo que en algunos casos depende de la fecha que tiene o no tiene configurada la máquina con la que se sacó la foto. Las que me envía mi papá tienen todas fecha 01/01/2005.
En relación al primer punto acabo de encontrar esto:
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/185752]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/185752")
Hablan del mismo tema y proponen algunas soluciones.
Esta noche lo pruebo en casa y te cuento.

Saludos.

---

### Post by santiagoward2000 on 2008-05-09
Hola Alejandro.
Gracias por el link de launchpad. No probé la opción de crear el archivo /etc/X11/Xsession.d/15dbus. ¿Sabés si puede crear algún conflicto como dicen?
Sobre lo de cambiar la fecha, no lo encuentro :confused: ¿Me podés decir dónde está?
Y por lo del mail, supongo que podría mandar la dirección de Picasa Web Albums. Igual me gustaría saber por qué no puedo mandarlo.
Gracias!

_EDIT:_
Ya encontré la opción para cambiar la fecha! :D Estaba en Editar, pero no lo veía. JAJA! (Tendría que ir derecho a las preguntontas!)

---

### Post by santiagoward2000 on 2008-05-12
Encontré cómo poder mandar los mails! \\:D/
Como explica este [thread]("http://ubuntuforums.org/showthread.php?t=501990"), el problema es que hay que elegir el programa que queremos usar (Thunderbird en este caso) como el programa por defecto de Gnome (aunque use Xfce). Para eso instalé el **gconf-editor** y en *Desktop>Gnome>url-handlers>mailto* puse **thunderbird %s** como comando.
Ahora sólo me falta ver por qué tengo que usar el **dbus-launch** para abrirlo. Lo único que encontré es de un [wiki de Gentoo]("http://gentoo-wiki.com/HOWTO_f-spot"), que dice que es por no usar Gnome.
Bueno, por lo menos puedo mandar mails y pude cambiar las fechas! :)
Saludos

PS: Me mata este nuevo foro. ¿Como lo marco Solved?

---

### Post by Alejandro Vidal on 2008-05-12
Me alegra que lo hayas resuelto.
Yo tuve un fin de semana imposible y ni siquiera puede ponerlo a prueba.
Saludos.
Alejandro.

---

### Post by _kAz_ on 2008-06-15
Revivo esto porque ando con un problemita con el f-spot en Ubuntu.

Se me dió por subir las pocas fotos que tengo a Picasa, pero no me gusta andar con aplicaciones Wine (salvo que sean juegos, siempre hay opciones nativas). 

Leí que F-Spot podía subirlas a la web, así que mortal, peeeeeeeroooooooo, como ya estoy acostumbrado, siempre algun obstáculo.

La cosa fue así: seleccione una foto, me fui a exportar>picasaweb, pude introducir la dirección, la contraseña y además tuve que abrir el anillo de contraseñas. 

Pasados unos segundos se cerró completamente el F-Spot; esto mismo sucede cada vez que quiero exportar (ya ni siquiera me aparece el cuadro donde me pedia el usuario). Cómo puedo detectar el problema?

Esto me dice desde la consola cuando lo abro:

```
Starting new FSpot server
Reloading
item changed
error checking orientation
System.IO.FileNotFoundException: Could not find uri "file:///home/ljd/Imagenes/100_0272.jpg".
  at Gnome.Vfs.VfsStream..ctor (System.String text_uri, FileMode mode, Boolean async) [0x00000] 
  at Gnome.Vfs.VfsStream..ctor (System.String uri, FileMode mode) [0x00000] 
  at (wrapper remoting-invoke-with-check) Gnome.Vfs.VfsStream:.ctor (string,System.IO.FileMode)
  at FSpot.ImageFile.Open () [0x00000] 
  at FSpot.ImageFile.PixbufStream () [0x00000] 
  at FSpot.AsyncPixbufLoader.Load (System.Uri uri) [0x00000] 
  at FSpot.PhotoImageView.PhotoItemChanged (FSpot.BrowsablePointer item, FSpot.BrowsablePointerChangedArgs args) [0x00000] 

(f-spot:6856): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
System.IO.FileNotFoundException: Could not find uri "file:///home/ljd/Imagenes/100_0272.jpg".
  at Gnome.Vfs.VfsStream..ctor (System.String text_uri, FileMode mode, Boolean async) [0x00000] 
  at Gnome.Vfs.VfsStream..ctor (System.String uri, FileMode mode) [0x00000] 
  at (wrapper remoting-invoke-with-check) Gnome.Vfs.VfsStream:.ctor (string,System.IO.FileMode)
  at FSpot.ImageFile.Open () [0x00000] 
  at FSpot.JpegFile.get_Header () [0x00000] 
  at FSpot.JpegFile.Select (StatementSink sink) [0x00000] 
  at InfoBox+ImageInfo..ctor (FSpot.ImageFile img) [0x00000] 
  at InfoBox.Update () [0x00000] 
```

Y cuando quiero exportar:
```
GoogleAccount.Connect()
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentOutOfRangeException: Index is less than 0 or more than or equal to the list count.
Parameter name: index
0
  at System.Collections.ArrayList.get_Item (Int32 index) [0x00000] 
  at System.Collections.Specialized.NameObjectCollectionBase.BaseGet (Int32 index) [0x00000] 
  at Mono.Google.Picasa.PicasaAlbumCollection.get_Item (Int32 index) [0x00000] 
  at FSpotGoogleExport.GoogleExport.HandleAlbumOptionMenuChanged (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.OptionMenu.gtk_option_menu_set_menu(IntPtr , IntPtr )
   at Gtk.OptionMenu.gtk_option_menu_set_menu(IntPtr , IntPtr )
   at Gtk.OptionMenu.set_Menu(Gtk.Widget value)
   at FSpotGoogleExport.GoogleExport.PopulateAlbumOptionMenu(Mono.Google.Picasa.PicasaWeb picasa)
   at FSpotGoogleExport.GoogleExport.Connect(FSpotGoogleExport.GoogleAccount selected, System.String token, System.String text)
   at FSpotGoogleExport.GoogleExport.Connect(FSpotGoogleExport.GoogleAccount selected)
   at FSpotGoogleExport.GoogleExport.Connect()
   at FSpotGoogleExport.GoogleExport.Run(IBrowsableCollection selection)
   at FSpot.Extensions.ExportMenuItemNode.OnActivated(System.Object o, System.EventArgs e)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)
```

---

### Post by santiagoward2000 on 2008-07-10
Hola!
Revivo este thread porque me aparecio otra duda con el F-Spot (no esta relacionada solamente con Xubuntu, pero para no abrir otro). Hoy modifique una foto un par de veces, entonces podia elegir si queria ver la foto original o alguna de las 2 modificaciones. Quise borrar las modificadas, entonces fui a la carpeta donde tengo todas las fotos y las borre. El tema es que cuando abro el F-Spot, todavia puedo ver las modificadas. ¿Alguien sabe si se guardan en algun otro lado?
Saludos!

---

### Post by Hei Ku on 2008-07-10
seguramente guarda un cache de las imagenes. Fijate que debe tener una opcion para actualizar la colección, como el Amarok.

---

### Post by santiagoward2000 on 2008-07-10
> **Hei Ku said:**
> seguramente guarda un cache de las imagenes. Fijate que debe tener una opcion para actualizar la colección, como el Amarok.

Hei Ku, gracias por la idea. La verdad que no encontré la opción para actualizarla (si alguien sabe si existe que me avise :)), pero saqué esa foto de la colección, la volví a agregar y ya no estaban.
Gracias!

---

### Post by www.rzr.online.fr on 2008-10-22
hola,

excuse me if I speak in english, but how did you fix this error :
"FSpot.Utils.GnomeUtil.Show"

-- 
[http://rzr.online.fr/q/smil](http://rzr.online.fr/q/smil)

---

### Post by santiagoward2000 on 2009-01-01
Hola gente!
Parece que este thread no quiere darse por muerto :D
Bue, nuevo problema: recién quería mandar todas las fotos de año nuevo por mail. Les cambié el tamaño con F-Spot, se abre el Thunderbird... hasta ahí todo bien. El tema es que, estuve un rato agregando gente a la lista, y cuando voy a mandar el mail, me salta un cartel que dice: > Sending of message failed.
Unable to open the temporary file /tmp/tmp49dc8bd6.tmp/DSC00640.JPG. Check your 'Temporary Directory' setting.
Terminé "solucionándolo" armando un grupo en el Thunderbird con las direcciones antes de abrir el F-Spot, pero ¿se puede aumentar el tiempo que tarda antes de vaciarse la carpeta temporal?
Gracias y FELIZ AÑO NUEVO! [IMG]http://www.gifmania.ec/bebidas/champagne/Wine-01.gif[/IMG]

---

### Post by Hei Ku on 2009-01-01
Cual es el problema? El F-Spot tiene un limite, o el espacio del tmp estaba lleno?

---

### Post by Hei Ku on 2009-01-01
Cual es el problema? El F-Spot tiene un limite, o el espacio del tmp estaba lleno?

---

### Post by santiagoward2000 on 2009-01-01
> **Hei Ku said:**
> Cual es el problema? El F-Spot tiene un limite, o el espacio del tmp estaba lleno?

Me parece que el problema es que las imágenes redimencionadas se guardan en el /tmp, pero se vacía muy rápido. Probé varias veces, y si estoy un rato antes de mandarlas, me pone el cartel y la carpeta /tmp está vacía, pero si lo hago más rápido puedo mandar sin problemas. No sé si está relacionado con el F-Spot.

---

### Post by Hei Ku on 2009-01-01
Fijate este thread, me parece que es tu problema:

[http://ubuntuforums.org/showthread.php?t=501990](http://ubuntuforums.org/showthread.php?t=501990)

---

### Post by santiagoward2000 on 2009-01-01
> **Hei Ku said:**
> Fijate este thread, me parece que es tu problema:

[http://ubuntuforums.org/showthread.php?t=501990](http://ubuntuforums.org/showthread.php?t=501990)

Ese es mi problema! :D
Pero ahora tengo otra duda. En gconf no me aparece ese **delete_timeout_seconds** como para editarlo. ¿Está bien si lo agrego yo?

_EDIT:_
Al final lo agregué yo, le metí un valor de 2000 segundos y listo. Probé de nuevo y ahora parece que puedo esperar un tiempo razonable sin que se borren :P
Gracias Hei Ku! Feliz año!!

---

### Post by Hei Ku on 2009-01-01
Me alegro! Lo damos por resuelto nomas?

Feliz Año!

---

