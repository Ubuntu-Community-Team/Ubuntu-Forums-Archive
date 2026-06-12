---
title: "cairo-dock and others"
date: 2008-10-19
forum: Software
---

### Post by tsueseres on 2008-10-19
tenia cairo-dock pero lo desinstale y luego quise volver a instalarlo,pero ya no corre, lo intente abrir desde una terminal y me sale esto:

warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/share/cairo-dock/plug-in/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio)
warning :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:248)  
  Attention : El archivo clave no tiene la clave «modules_0» en el grupo «Applets»
cairo_dock_update_conf_file_with_list: assertion `cOldComment != NULL' failed
warning :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:248)  
  Attention : El archivo clave no tiene la clave «modules_1» en el grupo «Applets»
cairo_dock_update_conf_file_with_list: assertion `cOldComment != NULL' failed
warning :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:248)  
  Attention : El archivo clave no tiene la clave «modules_2» en el grupo «Applets»
cairo_dock_update_conf_file_with_list: assertion `cOldComment != NULL' failed
warning :  (cairo-dock-config.c:cairo_dock_get_integer_key_value:242)  
  Attention : El archivo clave contiene la clave «screen border» en el grupo «Position» que tiene un valor que no puede ser interpretado.
warning :  (cairo-dock-config.c:cairo_dock_get_boolean_key_value:191)  
  Attention : El archivo clave no tiene la clave «auto-hide»

  Attention : El archivo clave no tiene la clave «string color»
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:293)  
  Attention : El archivo clave no tiene la clave «alpha at rest»

warning :  (cairo-dock-config.c:cairo_dock_get_string_key_value:344)  
  Attention : El archivo clave no tiene el grupo «Dialogs»
warning :  (cairo-dock-config.c:cairo_dock_get_string_key_value:344)  
  Attention : El archivo clave no tiene la clave «button_cancel image»
warning :  (cairo-dock-config.c:cairo_dock_get_integer_key_value:242)  
  Attention : El archivo clave no tiene la clave «button width»
warning :  (cairo-dock-config.c:cairo_dock_get_integer_key_value:242)  
  Attention : El archivo clave no tiene la clave «button height»
warning :  (cairo-dock-config.c:cairo_dock_get_double_list_key_value:478)  
  Attention : El archivo clave no tiene la clave «background color»
warning :  (cairo-dock-config.c:cairo_dock_get_integer_key_value:242)  
  Attention : El archivo clave no tiene la clave «icon size»
warning :  (cairo-dock-config.c:cairo_dock_get_boolean_key_value:191)  
  Attention : El archivo clave no tiene la clave «homogeneous text»
warning :  (cairo-dock-config.c:cairo_dock_get_double_list_key_value:478)  
  Attention : El archivo clave no tiene la clave «text color»
warning :  (cairo-dock-config.c:cairo_dock_get_double_list_key_value:478)  
  Attention : El archivo clave no tiene el grupo «Desklets»
warning :  (cairo-dock-config.c:cairo_dock_get_double_list_key_value:478)  
  Attention : El archivo clave no tiene la clave «background color inside»
warning :  (cairo-dock-config.c:cairo_dock_get_integer_key_value:242)  
  Attention : El archivo clave no tiene la clave «sort files»
warning :  (cairo-dock-config.c:cairo_dock_get_boolean_key_value:191)  
  Attention : El archivo clave no tiene la clave «show hidden files»
warning :  (cairo-dock-config.c:cairo_dock_get_string_key_value:344)  
  Attention : El archivo clave no tiene la clave «raise shortcut»
warning :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:185)  
  Attention : while trying to load 11gnome-system-monitor.desktop : Permiso denegado
cairo_dock_create_icon_from_desktop_file: assertion `icon->acDesktopFileName != NULL' failed
Fallo de segmentación


posdata: en otra cuenta de usuario si funciona, pero no se como hacerle para que vuelva a funcionar en esta, ya lo he desinstañado y vuelto a instalar varias veces

---

### Post by guisheca on 2008-10-20
Probá eliminando toda la config acerca del programa. Para hacerlo abrí nautilus en tu home, apretá ctrl+H (para ver archivos ocultos) y buscá la carpeta .cairo-dock, cuando la encuentres borrala por completo. Esto lo que hace es reiniciar todas las configuraciones del cairo-dock. Asumo que si te anda con otro user con esto se tiene que arreglar.
Saludos.

---

### Post by tsueseres on 2008-10-20
> **guisheca said:**
> Probá eliminando toda la config acerca del programa. Para hacerlo abrí nautilus en tu home, apretá ctrl+H (para ver archivos ocultos) y buscá la carpeta .cairo-dock, cuando la encuentres borrala por completo. Esto lo que hace es reiniciar todas las configuraciones del cairo-dock. Asumo que si te anda con otro user con esto se tiene que arreglar.
Saludos.

ok ya la encontre la carpeta pero no me deja borrarla dice permiso denegado

---

### Post by pol666 on 2008-10-20
¿? en /home te dice permiso denegado?

Fijate dandole permisos en propiedades. de ultima abri una terminal, pone sudo nautilus y ahi fijate

---

### Post by tsueseres on 2008-10-20
> **pol666 said:**
> ¿? en /home te dice permiso denegado?

Fijate dandole permisos en propiedades. de ultima abri una terminal, pone sudo nautilus y ahi fijate

gracias ya pude

---

