---
title: "question about software in wine"
date: 2009-06-29
forum: Wine
---

### Post by Mia1990 on 2009-06-29
My question i run Rosetta stone using wine and it runs better in wine then it ever did in windows but i have Cairo dock running and i would like to add Rosetta stone launcher to it but i drag it down to the dock and ther is arrows telling me to drop it but when i do there's nothing.
why?

thanks

---

### Post by fabounet on 2009-06-29
does it work with an "usual" launcher ?
try running "cairo-dock -l debug" in a terminal, do the operation, and post the result here.

---

### Post by Mia1990 on 2009-06-29
yes everything works great but i can't add a launcher to cairo dock that's my only problem
here is the output from the terminal

message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Computer/nautilus
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (nautilus)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 01google-picasa.desktop
 we will assume that its class is 'picasa'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Picasa/picasa
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (picasa)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 01truecrypt.desktop
 we will assume that its class is 'truecrypt'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;0;1
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + TrueCrypt/truecrypt
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (truecrypt)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 01gnome-terminal.desktop
 we will assume that its class is 'gnome-terminal'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:344)  
    on se base sur l'extension en desespoir de cause.
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Terminal/gnome-terminal
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (gnome-terminal)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 02evolution-mail.desktop
 we will assume that its class is 'evolution'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Evolution Mail/evolution
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (evolution)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 01brasero.desktop
 we will assume that its class is 'brasero'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Brasero Disc Burner/brasero
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (brasero)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 01rhythmbox.desktop
 we will assume that its class is 'rhythmbox'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Rhythmbox Music Player/rhythmbox
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (rhythmbox)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 03ekiga.desktop
 we will assume that its class is 'ekiga'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Ekiga Softphone/ekiga
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (ekiga)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 01transmission.desktop
 we will assume that its class is 'transmission'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Transmission BitTorrent Client/transmission
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (transmission)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 01gimp.desktop
 we will assume that its class is 'gimp-2.6'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:344)  
    on se base sur l'extension en desespoir de cause.
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + GIMP Image Editor/gimp-2.6
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (gimp-2.6)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 02pidgin.desktop
 we will assume that its class is 'pidgin'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 1;0;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Pidgin Internet Messenger/pidgin
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (pidgin)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:353)  
  no class defined for the launcher 02totem.desktop
 we will assume that its class is 'totem'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:344)  
    on se base sur l'extension en desespoir de cause.
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Movie Player/totem
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (totem)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:344)  
    on se base sur l'extension en desespoir de cause.
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:396)  
  + Firefox Web Browser/firefox
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:265)  
  cairo_dock_inhibate_class (firefox)
g_strsplit: assertion `string != NULL' failed
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:431)  
   + nouvelle icone d'appli (20971549)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:402)  
    cette fenetre est timide
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:431)  
   + nouvelle icone d'appli (56623311)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:511)  
  recuperation de 'question about software in wine - Ubuntu Forums - Mozilla Firefox' (bIsHidden : 0)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:519)  
    res_name : Navigator(9ebc350); res_class : Firefox(9b31820)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:551)  
  cairo_dock_create_surface_from_class (firefox)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:555)  
  bUseXIcon:0
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:564)  
    Firefox Web Browser
message :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:567)  
  Firefox Web Browser va fournir genereusement sa surface
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-class-manager.c:cairo_dock_add_appli_to_class:193)  
  cairo_dock_add_appli_to_class (firefox)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:431)  
   + nouvelle icone d'appli (58720260)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:511)  
  recuperation de 'me@me-laptop: ~' (bIsHidden : 0)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:519)  
    res_name : gnome-terminal(9e5366; res_class : Gnome-terminal(9e4d0f
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:551)  
  cairo_dock_create_surface_from_class (gnome-terminal)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:555)  
  bUseXIcon:0
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:564)  
    Terminal
message :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:567)  
  Terminal va fournir genereusement sa surface
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-class-manager.c:cairo_dock_add_appli_to_class:193)  
  cairo_dock_add_appli_to_class (gnome-terminal)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:431)  
   + nouvelle icone d'appli (18874411)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:431)  
   + nouvelle icone d'appli (18874371)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:402)  
    cette fenetre est timide
message :  (cairo-dock-modules.c:cairo_dock_activate_module:523)  
  cairo_dock_activate_module (dialog rendering)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1004)  
  cairo_dock_instanciate_module (/home/me/.config/cairo-dock/current_theme/plug-ins/dialog-rendering/dialog-rendering.conf)
message :  (applet-init.c:init:45)  
  init (/home/me/.config/cairo-dock/current_theme/plug-ins/dialog-rendering/dialog-rendering.conf)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_dialog_decorator:367)  
  cairo_dock_register_dialog_decorator (comics)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_dialog_decorator:367)  
  cairo_dock_register_dialog_decorator (modern)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_dialog_decorator:367)  
  cairo_dock_register_dialog_decorator (3Dplane)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_dialog_decorator:367)  
  cairo_dock_register_dialog_decorator (tooltip)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_dialog_decorator:367)  
  cairo_dock_register_dialog_decorator (curly)
message :  (cairo-dock-modules.c:cairo_dock_activate_module:523)  
  cairo_dock_activate_module (drop indicator)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1004)  
  cairo_dock_instanciate_module (/home/me/.config/cairo-dock/current_theme/plug-ins/drop_indicator/drop_indicator.conf)
message :  (applet-init.c:init:50)  
  init (/home/me/.config/cairo-dock/current_theme/plug-ins/drop_indicator/drop_indicator.conf)
message :  (applet-notifications.c:cd_drop_indicator_load_drop_indicator:265)  
  cd_drop_indicator_load_drop_indicator (/usr/share/cairo-dock/plug-ins/drop-indicator/default-drop-indicator.svg)

debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 1;0;0
message :  (cairo-dock-modules.c:cairo_dock_activate_module:523)  
  cairo_dock_activate_module (dock rendering)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1004)  
  cairo_dock_instanciate_module (/home/me/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:171)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:171)  
  Key file does not have key 'scroll accel'
message :  (cairo-dock-keyfile-utilities.c:cairo_dock_flush_conf_file_full:67)  
  cairo_dock_flush_conf_file_full (/usr/share/cairo-dock/plug-ins/rendering/rendering.conf)
cairo_dock_replace_values_in_conf_file (/home/me/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
cairo_dock_replace_key_values (0)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:33)  
  cairo_dock_write_keys_to_file (/home/me/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
message :  (rendering-init.c:init:11  
  init (/home/me/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:63)  
  cairo_dock_register_renderer (Caroussel)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:63)  
  cairo_dock_register_renderer (3D plane)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:63)  
  cairo_dock_register_renderer (Parabolic)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:63)  
  cairo_dock_register_renderer (Rainbow)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:63)  
  cairo_dock_register_renderer (Slide)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:63)  
  cairo_dock_register_renderer (Curve)
message :  (cairo-dock-modules.c:cairo_dock_activate_module:523)  
  cairo_dock_activate_module (Animated icons)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1004)  
  cairo_dock_instanciate_module (/home/me/.config/cairo-dock/current_theme/plug-ins/Animated-icons/Animated-icons.conf)
message :  (applet-init.c:init:30)  
  init (/home/me/.config/cairo-dock/current_theme/plug-ins/Animated-icons/Animated-icons.conf)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_animation:41  
  cairo_dock_register_animation (bounce)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_animation:41  
  cairo_dock_register_animation (rotate)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_animation:41  
  cairo_dock_register_animation (blink)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_animation:41  
  cairo_dock_register_animation (pulse)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_animation:41  
  cairo_dock_register_animation (wobbly)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_animation:41  
  cairo_dock_register_animation (wave)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_animation:41  
  cairo_dock_register_animation (spot)
message :  (cairo-dock-modules.c:cairo_dock_activate_module:523)  
  cairo_dock_activate_module (dustbin)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1004)  
  cairo_dock_instanciate_module (/home/me/.config/cairo-dock/current_theme/plug-ins/dustbin/dustbin.conf)
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:33  
  cairo_dock_fill_one_icon_buffer () -> 36.00x36.00
message :  (cairo-dock-themes-manager.c:cairo_dock_get_theme_path:824)  
  cairo_dock_get_theme_path (/usr/share/cairo-dock/plug-ins/dustbin/themes, /home/me/.config/cairo-dock/extras/dustbin, dustbin)
message :  (applet-init.c:init:145)  
  init (/home/me/.config/cairo-dock/current_theme/plug-ins/dustbin/dustbin.conf)
message :  (applet-init.c:_load_theme:62)  
    /home/me/.config/cairo-dock/extras/dustbin/Metal/trashcan_full.png

debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;1;0
message :  (applet-init.c:_load_theme:62)  
    /home/me/.config/cairo-dock/extras/dustbin/Metal/trashcan_empty.png

debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;1;0
message :  (applet-trashes-manager.c:cd_dustbin_add_one_dustbin:482)  
  cd_dustbin_add_one_dustbin (/home/me/.local/share/Trash/files)
message :  (applet-gvfs.c:vfs_backend_add_monitor:1094)  
  >>> moniteur ajoute sur /home/me/.local/share/Trash/files (9e4e960)
message :  (applet-trashes-manager.c:cd_dustbin_add_one_dustbin:493)  
    myConfig.iNbTrashes <- 0
message :  (applet-init.c:_cd_dusbin_start:110)  
    0 dechet(s) actuellement (1)
message :  (applet-draw.c:cd_dustbin_draw_quick_info:141)  
  cd_dustbin_draw_quick_info (0)
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (switcher, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (ram-meter, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (nVidia, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (Help, /home/me/.config/cairo-dock/current_theme/plug-ins/help/help.conf)
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (compiz-icon, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (showDesklets, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (keyboard indicator, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (stack, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (slider, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (Quick Browser, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (Toons, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (Cairo-Penguin, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (gnome integration, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (AlsaMixer, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (desklet rendering, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (shortcuts, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (Clipper, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (illusion, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (logout, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (weather, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (cpusage, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (Rhythmbox, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (showDesktop, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (wifi, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (clock, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (PowerManager, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (show mouse, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (systray, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (xmms, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (weblets, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (TomBoy, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (terminal, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (Dbus, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (GMenu, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (icon effects, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (netspeed, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (motion blur, (null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:570)  
  cairo_dock_deactivate_module (Xgamma, (null))
message :  (cairo-dock-renderer-manager.c:cairo_dock_set_renderer:22  
  cairo_dock_set_renderer ((null))
debug   :  (cairo-dock-dock-facility.c:cairo_dock_update_dock_size:95)  
    cairo_dock_update_dock_size (792 / 1024)
debug   :  (cairo-dock-X-utilities.c:cairo_dock_set_strut_partial:19  
  cairo_dock_set_strut_partial (0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
message :  (cairo-dock-dock-manager.c:cairo_dock_search_max_decorations_size:174)  
    decorations max : 792x35
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:33  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_update_background_decorations_if_necessary:747)  
    MaJ des decorations du fond -> 1584.00x35.00
debug   :  (cairo-dock-dock-facility.c:cairo_dock_place_root_dock:239)  
  cairo_dock_place_root_dock (0, 0, 1)
debug   :  (cairo-dock-dock-facility.c:cairo_dock_place_root_dock:252)  
   move to (200;68
message :  (cairo-dock-desklet.c:cairo_dock_reload_desklets_decorations:1400)  
  cairo_dock_reload_desklets_decorations (0)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (frame with scotch)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (personnal)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (none)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (scotch)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (dark)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (frame&reflects)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (clear)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (Starcraft2)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (CD box)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (default)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (frame with scotch)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (personnal)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (none)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (scotch)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (dark)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (frame&reflects)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (clear)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (Starcraft2)
debug   :  (cairo-dock-gui-factory.c:_cairo_dock_add_one_decoration_item:557)  
  _cairo_dock_add_one_decoration_item (CD box)
 

thank you

---

### Post by Ad88Ab99 on 2009-06-29
> **Mia1990 said:**
> My question i run Rosetta stone using wine and it runs better in wine then it ever did in windows but i have Cairo dock running and i would like to add Rosetta stone launcher to it but i drag it down to the dock and ther is arrows telling me to drop it but when i do there's nothing.
why?

thanks
point your mouse over the cairo-dock, right-click
choose    add a manual launcher
and create one as u normally do in ubuntu

---

### Post by andrea000 on 2009-06-30
you cant just drag and drop from wine to a dock software installed
using wine will not let you do that for some reason creating a manual launcher should do the trick for you

---

### Post by fabounet on 2009-06-30
so it is working for any launcher except a wine one ?
your debug output does not show the operation of inserting a launcher from the menu, did you do it ?
you don't need to paste all, only the part after the dock has loaded is useful.

---

### Post by Mia1990 on 2009-07-01
yes i can pull any software down and add it to the dock but not one installed in wine.I do not know how to make a manual launcher work i can just right click on the dock and add one but to launch the software i don't know how to do that.

---

### Post by fabounet on 2009-07-01
well I think the drag and drop should work.

launch the dock with "cairo-dock -l debug", wait until it's loaded, let some blank lines in the terminal, then try to add your launcher, and see if there are some new messages in the terminal.
If so, post them here to see if it's a bug.

---

