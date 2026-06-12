---
title: "Perdí botón de expulsar/desmontar en el navegador de archivos (GNOME)"
date: 2009-03-25
forum: Software
---

### Post by faustileon on 2009-03-25
Hola:
Tengo instalado Intrepid Ibex.  Como ustedes saben, una de sus novedades es (a esta altura "era") contar con un botón expulsar desmontar en el panel lateral del navegador de archivos, al estilo OSX. Instalé de GNOME-Look.org, un script para cambiar la apariencia a una muy similar al XP, un poco para matar el aburrimiento laboral, otro poco por las dudas tenga que hacerlo pasar por (en mi trabajo), o para instalarlo en casa y ayudar a vencer la muy femeninamente típica reacción al cambio de mi esposa.
El script es XpGnome, aunque ahora no encuentro el link.  Básicamente instala XPLuna, íconos y un GDM.  Pero, supongo que para aumentar el parecido con XP, le suprimió los botones susodichos, modificó la tipografía y también sacó los marcadores del panel lateral del navegador de archivos de Gnome.  Cuando me cansé, volví al tema Dust con íconos Hydroxygen, pero el Panel lateral quedó igual.  la tipogafía no me molesta, pero lo de los botones de expulsar y los marcadores (Documentos, Imágenes, Música y Videos) sí.  supongo que debe ser fácil, pero no encontré la forma en "Editar/preferencias" del Navegador de Archivos, ni usando el gconf-editor. Como info adicional, el script creó una carpeta "RestoreSettings_feb_23_2009,17-07-52" con un archivo Panel_Settings.xml pero no tengo ni la menor idea de qué hacer con él.
Si alguien sabe, por favor, que me oriente.
Muchísimas gracias por anticipado.
Santiago.

---

### Post by albandy on 2009-03-25
para descartar que el script te haya tocado archivos del sistema crea un nuevo usuario y prueba si funciona todo correctamente.

Normalmente este tipo de scripts usan un tipo de instalación make install por lo que es posible que tambien exista el make uninstall

---

### Post by faustileon on 2009-03-25
Muchas gracias por tu respuesta, qué digo rápida, rapidísima.  Me fijé en la carpeta Xp Gnome, la que salió de XpGnome.tar.gz, y tengo la carpeta que comenté antes, otra que se llama "files" que tiene los diferentes temas comprimidos y, suelto, el archivo InstallXpGnome.sh.
El texto de este .sh es:

#!/bin/sh
#
# XpGnome Script
# Written by PhrankDaChicken
# [http://ubunut.online02.com/xpgnome](http://ubunut.online02.com/xpgnome)
#
# Last Update: 12/25/08
#

DIR=$(pwd)

if ! $(zenity --question --no-wrap --title "XpGnome" --text "WARNING: This script will change your Gnome desktop to look like Windows XP! \n Continue?") ; then
	echo "no"
	exit 0
fi

(
echo "# Saving Settings..."

RESTOREDIR=$(date +%b_%d_%Y,%H-%M-%S)
RESTOREDIR="RestoreSettings_$RESTOREDIR"
mkdir $RESTOREDIR
echo "#!/bin/sh" > /tmp/Restore_Settings.sh
echo "gconftool-2 --set \"/desktop/gnome/interface/icon_theme\" --type string" \"$(gconftool-2 --get "/desktop/gnome/interface/icon_theme")\" >> /tmp/Restore_Settings.sh
echo "gconftool-2 --set \"/desktop/gnome/peripherals/mouse/cursor_theme\" --type string" \"$(gconftool-2 --get "/desktop/gnome/peripherals/mouse/cursor_theme")\" >> /tmp/Restore_Settings.sh
echo "gconftool-2 --set \"/desktop/gnome/interface/gtk_theme\" --type string" \"$(gconftool-2 --get "/desktop/gnome/interface/gtk_theme")\" >> /tmp/Restore_Settings.sh
echo "gconftool-2 --set \"/apps/metacity/general/theme\" --type string" \"$(gconftool-2 --get "/apps/metacity/general/theme")\" >> /tmp/Restore_Settings.sh
echo "gconftool-2 --set \"/desktop/gnome/interface/toolbar_style\" --type string" \"$(gconftool-2 --get "/desktop/gnome/interface/toolbar_style")\" >> /tmp/Restore_Settings.sh
echo "gconftool-2 --set \"/apps/nautilus/preferences/side_pane_view\" --type string" \"$(gconftool-2 --get "/apps/nautilus/preferences/side_pane_view")\" >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/nautilus/sidebar_panels/tree/show_only_directories\" --type bool" $(gconftool-2 --get "/apps/nautilus/sidebar_panels/tree/show_only_directories") >> /tmp/Restore_Settings.sh
echo "gconftool-2 --set \"/apps/nautilus/desktop/computer_icon_visible\" --type bool" $(gconftool-2 --get "/apps/nautilus/desktop/computer_icon_visible") >> /tmp/Restore_Settings.sh
echo "gconftool-2 --set \"/apps/nautilus/desktop/computer_icon_name\" --type string " \"$(gconftool-2 --get "/apps/nautilus/desktop/computer_icon_name")\" >> /tmp/Restore_Settings.sh  
echo "gconftool-2 --set \"/apps/nautilus/desktop/home_icon_visible\" --type bool" $(gconftool-2 --get "/apps/nautilus/desktop/home_icon_visible") >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/nautilus/desktop/home_icon_name\" --type string" \"$(gconftool-2 --get "/apps/nautilus/desktop/home_icon_name")\" >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/nautilus/desktop/network_icon_visible\" --type bool" $(gconftool-2 --get "/apps/nautilus/desktop/network_icon_visible") >> /tmp/Restore_Settings.sh  
echo "gconftool-2 --set \"/apps/nautilus/desktop/network_icon_name\" --type string" \"$(gconftool-2 --get "/apps/nautilus/desktop/network_icon_name")\" >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/nautilus/desktop/trash_icon_visible\" --type bool" $(gconftool-2 --get "/apps/nautilus/desktop/trash_icon_visible") >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/nautilus/desktop/trash_icon_name\" --type string" \"$(gconftool-2 --get "/apps/nautilus/desktop/trash_icon_name")\" >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/nautilus/desktop/volumes_visible\" --type bool" $(gconftool-2 --get "/apps/nautilus/desktop/volumes_visible") >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/gnome-session/options/show_splash_screen\" --type bool" $(gconftool-2 --get "/apps/gnome-session/options/show_splash_screen") >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/gnome-session/options/splash_image\" --type string" \"$(gconftool-2 --get "/apps/gnome-session/options/splash_image")\" >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/desktop/gnome/background/picture_filename\" --type string" \"$(gconftool-2 --get "/desktop/gnome/background/picture_filename")\" >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/desktop/gnome/background/picture_options\" --type string" \"$(gconftool-2 --get "/desktop/gnome/background/picture_options")\" >> /tmp/Restore_Settings.sh 
echo "gconftool-2 --set \"/apps/metacity/general/num_workspaces\" --type int" $(gconftool-2 --get "/apps/metacity/general/num_workspaces") >> /tmp/Restore_Settings.sh 
echo "rm -r $HOME/.icons/GnomeXP" >> /tmp/Restore_Settings.sh
echo "rm -r $HOME/.icons/xp" >> /tmp/Restore_Settings.sh
echo "rm -r $HOME/.themes/XPLuna" >> /tmp/Restore_Settings.sh
echo "gconftool-2 --load Panel_Settings.xml" >> /tmp/Restore_Settings.sh
echo "killall gnome-panel" >> /tmp/Restore_Settings.sh
echo "gksudo -m \"Enter your password to remove and change the XP GDM/Login theme\" \"rm -r /usr/share/gdm/themes/XP_Ubuntu\"" >> /tmp/Restore_Settings.sh
echo "gksudo gdmsetup" >> /tmp/Restore_Settings.sh
echo "zenity --info --no-wrap --title \"XpGnome\" --text \"Settings restored!" >> /tmp/Restore_Settings.sh
chmod a+x /tmp/Restore_Settings.sh
mv /tmp/Restore_Settings.sh $DIR/$RESTOREDIR/Restore_Settings.sh
gconftool-2 --dump /apps/panel > $DIR/$RESTOREDIR/Panel_Settings.xml 
#cp /etc/gdm/gdm.conf-custom $DIR/$RESTOREDIR/

echo "# Theming Desktop...."
mkdir $HOME/.themes
mkdir $HOME/.icons

# Icons
cp files/GnomeXP.tar.gz $HOME/.icons
cd $HOME/.icons
tar -xf GnomeXP.tar.gz
rm GnomeXP.tar.gz
gconftool-2 --set "/desktop/gnome/interface/icon_theme" --type string "GnomeXP"
cd $DIR

# Cursor
cp files/xp_cursor.tar.gz $HOME/.icons
cd $HOME/.icons
tar -xf xp_cursor.tar.gz
rm xp_cursor.tar.gz
gconftool-2 --set "/desktop/gnome/peripherals/mouse/cursor_theme" --type string "xp"
cd $DIR

# GTK Theme - XPLuna
cp files/XPLuna.tar.gz $HOME/.themes
cd $HOME/.themes
tar -xf XPLuna.tar.gz
rm XPLuna.tar.gz
gconftool-2 --set "/desktop/gnome/interface/gtk_theme" --type string "XPLuna"
cd $DIR

# Meacity Theme
gconftool-2 --set "/apps/metacity/general/theme" --type string "XPLuna"

# Toolbars - Icons Only
gconftool-2 --set "/desktop/gnome/interface/toolbar_style" --type string "icons"
# Nautilus Sidebar
gconftool-2 --set "/apps/nautilus/preferences/side_pane_view" --type string "NautilusTreeSidebar"
gconftool-2 --set "/apps/nautilus/sidebar_panels/tree/show_only_directories" --type bool TRUE

# Desktop Icons
gconftool-2 --set "/apps/nautilus/desktop/computer_icon_visible" --type bool TRUE
gconftool-2 --set "/apps/nautilus/desktop/computer_icon_name" --type string "My Computer"
gconftool-2 --set "/apps/nautilus/desktop/home_icon_visible" --type bool TRUE
gconftool-2 --set "/apps/nautilus/desktop/home_icon_name" --type string "My Documents"
gconftool-2 --set "/apps/nautilus/desktop/network_icon_visible" --type bool TRUE
gconftool-2 --set "/apps/nautilus/desktop/network_icon_name" --type string "My Network Places"
gconftool-2 --set "/apps/nautilus/desktop/trash_icon_visible" --type bool TRUE
gconftool-2 --set "/apps/nautilus/desktop/trash_icon_name" --type string "Recycle Bin"
gconftool-2 --set "/apps/nautilus/desktop/volumes_visible" --type bool FALSE

# Splash Screen
gconftool-2 --set "/apps/gnome-session/options/show_splash_screen" --type bool TRUE
gconftool-2 --set "/apps/gnome-session/options/splash_image" --type string "$HOME/.themes/XPLuna/windowslogin.png"

# Background
gconftool-2 --set "/desktop/gnome/background/picture_filename" --type string "$HOME/.themes/XPLuna/Bliss_XP.jpg"
gconftool-2 --set "/desktop/gnome/background/picture_options" --type string "stretched"

# Set One Workplace
gconftool-2 --set "/apps/metacity/general/num_workspaces" --type int 1

echo "# Creating Panels...."
## Panel Stuff
# Create New Panel
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/animation_speed" --type string "medium"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/auto_hide" --type bool FALSE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/auto_hide_size" --type int 6
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/enable_animations" --type bool TRUE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/enable_arrows" --type bool TRUE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/enable_buttons" --type bool FALSE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/expand" --type bool TRUE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/hide_delay" --type int 500
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/monitor" --type int 0
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/name" --type string "bottom_panel_0"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/orientation" --type string "bottom"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/screen" --type int 0
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/size" --type int 32
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/unhide_delay" --type int 500 
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/x" --type int 0
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/x_centered" --type bool FALSE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/x_right" --type int 
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/y" --type int 0
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/y_bottom" --type  int 
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/y_centered" --type bool FALSE

gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/background/color" --type string "#ffffff"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/background/fit" --type bool FALSE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/background/image" --type string ""
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/background/opacity" --type int 6000
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/background/rotate" --type bool FALSE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/background/stretch" --type bool FALSE
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_0/background/type" --type string "gtk"

# Start Menu
gconftool-2 --set "/apps/panel/objects/object_0/action_type" --type string "lock"
gconftool-2 --set "/apps/panel/objects/object_0/attached_toplevel_id" --type string ""
gconftool-2 --set "/apps/panel/objects/object_0/bonobo_iid" --type string ""
gconftool-2 --set "/apps/panel/objects/object_0/custom_icon" --type string "/home/"$USER"/.themes/XPLuna/start.png"
gconftool-2 --set "/apps/panel/objects/object_0/launcher_location" --type string ""
gconftool-2 --set "/apps/panel/objects/object_0/locked" --type bool TRUE
gconftool-2 --set "/apps/panel/objects/object_0/menu_path" --type string "applications:/"
gconftool-2 --set "/apps/panel/objects/object_0/object_type" --type string "menu-object"
gconftool-2 --set "/apps/panel/objects/object_0/panel_right_stick" --type bool FALSE
gconftool-2 --set "/apps/panel/objects/object_0/position" --type int 0
gconftool-2 --set "/apps/panel/objects/object_0/tooltip" --type string "Main Menu"
gconftool-2 --set "/apps/panel/objects/object_0/toplevel_id" --type string "bottom_panel_0"
gconftool-2 --set "/apps/panel/objects/object_0/use_custom_icon" --type bool TRUE
gconftool-2 --set "/apps/panel/objects/object_0/use_menu_path" --type bool FALSE

# Show Desktop
gconftool-2 --set "/apps/panel/applets/applet_0/action_type" --type string "lock"
gconftool-2 --set "/apps/panel/applets/applet_0/attached_toplevel_id" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_0/bonobo_iid" --type string "OAFIID:GNOME_ShowDesktopApplet"
gconftool-2 --set "/apps/panel/applets/applet_0/custom_icon" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_0/launcher_location" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_0/locked" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_0/menu_path" --type string "applications:/"
gconftool-2 --set "/apps/panel/applets/applet_0/object_type" --type string "bonobo-applet"
gconftool-2 --set "/apps/panel/applets/applet_0/panel_right_stick" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_0/position" --type int 1
gconftool-2 --set "/apps/panel/applets/applet_0/tooltip" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_0/toplevel_id" --type string "bottom_panel_0"
gconftool-2 --set "/apps/panel/applets/applet_0/use_custom_icon" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_0/use_menu_path" --type bool FALSE

# Window Switcher
gconftool-2 --set "/apps/panel/applets/applet_1/action_type" --type string "lock"
gconftool-2 --set "/apps/panel/applets/applet_1/attached_toplevel_id" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_1/bonobo_iid" --type string "OAFIID:GNOME_WindowListApplet"
gconftool-2 --set "/apps/panel/applets/applet_1/custom_icon" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_1/launcher_location" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_1/locked" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_1/menu_path" --type string "applications:/"
gconftool-2 --set "/apps/panel/applets/applet_1/object_type" --type string "bonobo-applet"
gconftool-2 --set "/apps/panel/applets/applet_1/panel_right_stick" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_1/position" --type int 2
gconftool-2 --set "/apps/panel/applets/applet_1/tooltip" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_1/toplevel_id" --type string "bottom_panel_0"
gconftool-2 --set "/apps/panel/applets/applet_1/use_custom_icon" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_1/use_menu_path" --type bool FALSE

gconftool-2 --set "/apps/panel/applets/applet_1/prefs/display_all_workspaces" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_1/prefs/group_windows" --type string "never"
gconftool-2 --set "/apps/panel/applets/applet_1/prefs/maximum_size" --type int 4096
gconftool-2 --set "/apps/panel/applets/applet_1/prefs/minimum_size" --type int 50
gconftool-2 --set "/apps/panel/applets/applet_1/prefs/move_unminimized_windows" --type bool TRUE

# Notification Area
gconftool-2 --set "/apps/panel/applets/applet_2/action_type" --type string "lock"
gconftool-2 --set "/apps/panel/applets/applet_2/attached_toplevel_id" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_2/bonobo_iid" --type string "OAFIID:GNOME_NotificationAreaApplet"
gconftool-2 --set "/apps/panel/applets/applet_2/custom_icon" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_2/launcher_location" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_2/locked" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_2/menu_path" --type string "applications:/"
gconftool-2 --set "/apps/panel/applets/applet_2/object_type" --type string "bonobo-applet"
gconftool-2 --set "/apps/panel/applets/applet_2/panel_right_stick" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_2/position" --type int 3
gconftool-2 --set "/apps/panel/applets/applet_2/tooltip" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_2/toplevel_id" --type string "bottom_panel_0"
gconftool-2 --set "/apps/panel/applets/applet_2/use_custom_icon" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_2/use_menu_path" --type bool FALSE

# Volume Control
gconftool-2 --set "/apps/panel/applets/applet_3/action_type" --type string "lock"
gconftool-2 --set "/apps/panel/applets/applet_3/attached_toplevel_id" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_3/bonobo_iid" --type string "OAFIID:GNOME_MixerApplet"
gconftool-2 --set "/apps/panel/applets/applet_3/custom_icon" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_3/launcher_location" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_3/locked" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_3/menu_path" --type string "applications:/"
gconftool-2 --set "/apps/panel/applets/applet_3/object_type" --type string "bonobo-applet"
gconftool-2 --set "/apps/panel/applets/applet_3/panel_right_stick" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_3/position" --type int 2
gconftool-2 --set "/apps/panel/applets/applet_3/tooltip" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_3/toplevel_id" --type string "bottom_panel_0"
gconftool-2 --set "/apps/panel/applets/applet_3/use_custom_icon" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_3/use_menu_path" --type bool FALSE

# Clock
gconftool-2 --set "/apps/panel/applets/applet_4/action_type" --type string "lock"
gconftool-2 --set "/apps/panel/applets/applet_4/attached_toplevel_id" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_4/bonobo_iid" --type string "OAFIID:GNOME_ClockApplet"
gconftool-2 --set "/apps/panel/applets/applet_4/custom_icon" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_4/launcher_location" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_4/locked" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_4/menu_path" --type string "applications:/"
gconftool-2 --set "/apps/panel/applets/applet_4/object_type" --type string "bonobo-applet"
gconftool-2 --set "/apps/panel/applets/applet_4/panel_right_stick" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_4/position" --type int 0
gconftool-2 --set "/apps/panel/applets/applet_4/tooltip" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_4/toplevel_id" --type string "bottom_panel_0"
gconftool-2 --set "/apps/panel/applets/applet_4/use_custom_icon" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/use_menu_path" --type bool FALSE

gconftool-2 --set "/apps/panel/applets/applet_4/prefs/config_tool" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/custom_format" --type string ""
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/expand_appointments" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/expand_birthdays" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/expand_tasks" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/expand_weather" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/format" --type string "12-hour"
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/gmt_time" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/hour_format" --type string "12"
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/internet_time" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/show_date" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/show_seconds" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/show_timezones" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/show_tooltip" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/show_week_numbers" --type bool TRUE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/unix_time" --type bool FALSE
gconftool-2 --set "/apps/panel/applets/applet_4/prefs/timezones/tz_id_list" --type list --list-type string "[]"

# Add Panels Items
gconftool-2 --set "/apps/panel/general/applet_id_list" --type list --list-type string "[applet_0,applet_1,applet_2,applet_3,applet_4]"
gconftool-2 --set "/apps/panel/general/object_id_list" --type list --list-type string "[object_0]"
gconftool-2 --set "/apps/panel/general/toplevel_id_list" --type list --list-type string "[bottom_panel_0]"
 
echo "# Setting up GDM theme..."
# GDM Theme
cp files/XP_Ubuntu.tar.gz /tmp
gksudo -m "Enter your (sudo/root) password to change the Login screen to a XP Style - Or click cancel if you do not wish to change it" files/GDMTheme.sh
rm /tmp/XP_Ubuntu.tar.gz

killall gnome-panel
echo "# Done! Your desktop is now fully XP themed. \nRun the Restore_Settings_$FILEDATE.sh script to revert to the previous settings."
) | zenity --progress --width 500 --height 300 --title "XpGnome" --text "Setting stuff up..." --pulsate

No me hixo un archivo Restore_Settings_$FILEDATE.sh, sino la carpeta antes mencionada con este .xml: (editado)

Bueno esto, más o menos. Voy a ver si puedo encontrar al autor y preguntarle. ¡Gracias!

Nota: lo edito y saco el texto del .xml porque es larguísimo.

---

### Post by faustileon on 2009-03-25
albandy:
Probé lo que me sugeriste, cree el usuario "invitado" y en esa sesión estaba todo bien. ¿A partir de esto tenés alguna otra sugerencia? Muchas gracias.

---

### Post by pablo.s on 2009-03-25
En cualquier ventana de Nautilus presiona F9.

---

### Post by faustileon on 2009-03-25
Gracias pablo.  Mañana en el trabajo, en cuya máquina es que tengo el temita, lo intento y les cuento.

---

### Post by Air23 on 2009-03-26
¿En la parte superior del panel lateral de nautilus te figura "arbol"? Si es asi cambialo por "lugares" a ver que pasa

---

### Post by faustileon on 2009-03-26
Solucionado, ¡gracias air23! Como decía en el primer post, debía ser algo muy simple, pero se me escapaba.  Hace dos años que uso Gnome, pero nunca me había fijado en la utilidad de ese menú deplegable.  Otra vez, gracias.
Pablo: muchas gracias también para vos.  Intenté lo que decías pero ese no era el problema, F9 oculta/muestra el panel lateral y el problema era EN el panel lateral.

---

### Post by Air23 on 2009-03-26
> **faustileon said:**
> Solucionado, ¡gracias air23! Como decía en el primer post, debía ser algo muy simple, pero se me escapaba.  Hace dos años que uso Gnome, pero nunca me había fijado en la utilidad de ese menú deplegable.  Otra vez, gracias.
De nada :)

---

