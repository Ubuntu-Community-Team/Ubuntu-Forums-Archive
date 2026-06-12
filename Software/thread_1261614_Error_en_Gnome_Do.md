---
title: "Error en Gnome Do"
date: 2009-09-08
forum: Software
---

### Post by Fisaulerod on 2009-09-08
Hola, uso Gnome Do como docky. A veces cuando por ejemplo me hablan en emesene y sale una ventana nueva, gnome do se cierra. Luego lo abro pero se vuelve a cerrar (no vuelve a funcionar bien hasta que reinicio). Si lo ejecuto desde la terminal luego de que se cierra sale esto:

```
/home/felipe/.themes/MurrinaChrome/gtk-2.0/gtkrc:83: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/felipe/.themes/MurrinaChrome/gtk-2.0/gtkrc:84: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentOutOfRangeException: StartIndex can not be less than zero
Parameter name: startIndex
  at System.String.Remove (Int32 startIndex) [0x00000] 
  at Do.Interface.IconProvider.IconFromTheme (System.String name, Int32 size, Gtk.IconTheme theme) [0x00000] 
  at Do.Interface.IconProvider.PixbufFromIconName (System.String name, Int32 size, Gdk.Pixbuf& pixbuf) [0x00000] 
  at Docky.Interface.ApplicationDockItem.GetSurfacePixbuf (Int32 size) [0x00000] 
  at Docky.Interface.AbstractDockItem.MakeIconSurface (Cairo.Surface similar, Int32 size) [0x00000] 
  at Docky.Interface.AbstractDockItem.GetIconSurface (Cairo.Surface similar, Int32 targetSize, System.Int32& actualSize) [0x00000] 
  at Docky.Interface.DockArea.DrawIcon (Cairo.Context cr, Int32 icon) [0x00000] 
  at Docky.Interface.DockArea.DrawIcons (Cairo.Context cr) [0x00000] 
  at Docky.Interface.DockArea.DrawDrock (Cairo.Context cr) [0x00000] 
  at Docky.Interface.DockArea.OnExposeEvent (Gdk.EventExpose evnt) [0x00000] 
  at Gtk.Widget.exposeevent_cb (IntPtr widget, IntPtr evnt) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.exposeevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Do.Do.Main(System.String[] args)
Cairo.Context: called from finalization thread, programmer is missing a call to Dispose
Cairo.Context: called from finalization thread, programmer is missing a call to Dispose

```

Eso, gracias de antemano :P.

---

### Post by moreback on 2009-09-09
Viendo la traza que deja el programa creo que el error se da cuando Docky intenta crear el ícono para la ventana que está apareciendo (que según indicas sería el emesene). No sé si tendrá que ver con el tema de íconos que estés usando, pero prueba cambiando de tema y trata de reproducir nuevamente el error.

Si no hay solución intenta buscar algún bug en el sitio oficial de gnome-do y si no lo encuentras entonces publica uno nuevo.

Saludos.

---

### Post by Fisaulerod on 2009-09-09
Efectivamente al cambiar el tema y abrir una ventana de dialogo de emesene el docky no se cierra...¿Qué puedo hacer? Porque no quiero cambiar el tema de iconos, además los otros que me gustan hacen que el panel se vea muy grande siendo muy incomodo...
Lo otro, ¿porque antes no pasaba?
eso, gracias de antemano.

P.D: disculpen por el doble post, aprete quote sin querer.

P.D.2: comprobé que con otros temas tampoco funciona...es que a veces funciona bien, pero desde cierto momento que abro una ventana de conversacion funciona mal...de hecho ejecutando gnome do en la terminal he probado que se cierra siempre que tenga una ventana de conversacion de alguien conectado abierta...si no tengo emesene abierto, incluso despues de cerrarse, puedo abrirlo sin problemas....eso, gracias de antemano

---

### Post by moreback on 2009-09-10
Creo que puede ser un problema con el ícono que le asigna el tema a las ventanas del emesene. A lo mejor si lo cambias manualmente sólo para esa aplicación, puedas conseguir que no se caiga. Puede ser que el archivo del ícono pueda estar corrupto o tener algo que hace que se caiga el gnome-do.

Saludos.

---

### Post by Fisaulerod on 2009-09-12
Sí, supongo que puede ser eso...lo raro es que por un rato funciona bien, pero desde cierto momento la cosa se cierra, y el error sólo sale si abro una ventana nueva a alguien conectado. Por ejemplo, si abro una ventana con alguien no conectado (luego del error) funciona bien, pero si abro con alguien conectado se cierra :/.

---

