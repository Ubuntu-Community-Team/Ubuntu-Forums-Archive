---
title: "[SOLVED] Chibitracker 1.2 - problemas de compilación"
date: 2008-08-27
forum: Software
---

### Post by faktorqm on 2008-08-27
Hola gente, les vengo con un problema de compilación de un tracker que tenía ganas de hacer andar a ver si componía algo con software libre y bueno, no me anda! :( 
El chibitracker es un clon libre del viejo y queridisimo Impulse Tracker 2.14, lider de trackers.
La cosa es que parece que esta hecho en python, y para compilarse necesita de algo llamado scons que segun lo que averigue vendria a ser como el make de C, pero la verdad que yo no le veo la simplicidad del mismo. 
Acá intenté compilarlo y les dejo la salida para ver si se les ocurre algo:

```
faktorqm@the-edge:~$ cd chibitracker-1.2/
faktorqm@the-edge:~/chibitracker-1.2$ ls
AUTHORS    drivers  gui        mixer           player      skins  todo.txt
ChangeLog  fileio   INSTALL    NEWS            program     song   tracker
COPYING    globals  interface  pigui_todo.txt  SConstruct  TODO
faktorqm@the-edge:~/chibitracker-1.2$ sudo scons install
scons: Reading SConscript files ...
1.2.12
libSDL Detected
1
scons: done reading SConscript files.
scons: Building targets ...
o program/chibitracker.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL program/chibitracker.cpp
sh: o: not found
o interface/playback_button.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/playback_button.cpp
sh: o: not found
o interface/pattern_editor.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/pattern_editor.cpp
sh: o: not found
o interface/pattern_screen.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/pattern_screen.cpp
sh: o: not found
o interface/sample_screen.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_screen.cpp
sh: o: not found
o interface/instrument_screen.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/instrument_screen.cpp
sh: o: not found
o interface/variables_screen.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/variables_screen.cpp
sh: o: not found
o interface/sample_instrument_table.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_instrument_table.cpp
sh: o: not found
o interface/ctskin.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/ctskin.cpp
sh: o: not found
o interface/interface.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/interface.cpp
sh: o: not found
o interface/orderlist_editor.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/orderlist_editor.cpp
sh: o: not found
o interface/pattern_editor_top.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/pattern_editor_top.cpp
sh: o: not found
o interface/pattern_editor_mask.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/pattern_editor_mask.cpp
sh: o: not found
o interface/pattern_editor_rows.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/pattern_editor_rows.cpp
sh: o: not found
o interface/sample_editor.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_editor.cpp
sh: o: not found
o interface/sample_editor_clipboard.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_editor_clipboard.cpp
sh: o: not found
o interface/sample_editor_effects.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_editor_effects.cpp
sh: o: not found
o interface/sample_editor_format.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_editor_format.cpp
sh: o: not found
o interface/sample_viewer.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_viewer.cpp
sh: o: not found
o interface/sample_viewer_zoom.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_viewer_zoom.cpp
sh: o: not found
o interface/envelope_editor.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/envelope_editor.cpp
sh: o: not found
o interface/envelope_point_editor.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/envelope_point_editor.cpp
sh: o: not found
o interface/theme_dialog.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/theme_dialog.cpp
sh: o: not found
o interface/sound_driver_dialog.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sound_driver_dialog.cpp
sh: o: not found
o interface/keyboard_dialog.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/keyboard_dialog.cpp
sh: o: not found
o interface/sample_viewer_positions.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_viewer_positions.cpp
sh: o: not found
o interface/sample_status_list.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_status_list.cpp
sh: o: not found
o interface/pattern_editor_oscs.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/pattern_editor_oscs.cpp
sh: o: not found
o interface/reverb.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/reverb.cpp
sh: o: not found
o interface/mixer_dialog.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/mixer_dialog.cpp
sh: o: not found
o interface/sample_file_dialog.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/sample_file_dialog.cpp
sh: o: not found
o interface/config_api.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/config_api.cpp
sh: o: not found
o interface/config_file.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/config_file.cpp
sh: o: not found
o interface/interface_settings_dialog.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/interface_settings_dialog.cpp
sh: o: not found
o interface/theme_loader.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/theme_loader.cpp
sh: o: not found
o interface/interface_help.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/interface_help.cpp
sh: o: not found
o interface/wav_saver_dialog.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/wav_saver_dialog.cpp
sh: o: not found
o interface/main_vu.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/main_vu.cpp
sh: o: not found
o interface/pattern_transpose.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/pattern_transpose.cpp
sh: o: not found
o interface/paths_dialog.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/paths_dialog.cpp
sh: o: not found
o interface/default_paths.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/default_paths.cpp
sh: o: not found
o interface/interface_mini.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/interface_mini.cpp
sh: o: not found
o interface/mini_theme.o -c -O2 -ffast-math -DANSIC_LIBS_ENABLED -DPOSIX_ENABLED -DSDL_ENABLED -fno-exceptions -D_GNU_SOURCE=1 -D_REENTRANT -Iglobals -Igui -I. -I/usr/include/SDL interface/mini_theme.cpp
sh: o: not found
ar rc interface/libinterface.a interface/playback_button.o interface/pattern_editor.o interface/pattern_screen.o interface/sample_screen.o interface/instrument_screen.o interface/variables_screen.o interface/sample_instrument_table.o interface/ctskin.o interface/interface.o interface/orderlist_editor.o interface/pattern_editor_top.o interface/pattern_editor_mask.o interface/pattern_editor_rows.o interface/interface.o interface/sample_editor.o interface/sample_editor_clipboard.o interface/sample_editor_effects.o interface/sample_editor_format.o interface/sample_viewer.o interface/sample_viewer_zoom.o interface/envelope_editor.o interface/envelope_point_editor.o interface/theme_dialog.o interface/sound_driver_dialog.o interface/keyboard_dialog.o interface/sample_viewer_positions.o interface/sample_status_list.o interface/pattern_editor_oscs.o interface/reverb.o interface/mixer_dialog.o interface/keyboard_dialog.o interface/sample_file_dialog.o interface/config_api.o interface/config_file.o interface/interface_settings_dialog.o interface/theme_loader.o interface/interface_help.o interface/wav_saver_dialog.o interface/main_vu.o interface/pattern_transpose.o interface/paths_dialog.o interface/default_paths.o interface/interface_mini.o interface/mini_theme.o
ar: interface/playback_button.o: No such file or directory
scons: *** [interface/libinterface.a] Error 1
scons: building terminated because of errors.
faktorqm@the-edge:~/chibitracker-1.2$
```

Bueno, lo que a mi me parece segun las lineas de arriba es que esta mal la ruta de los directorios de include para las bibliotecas, por ejemplo: -I/usr/include/SDL interface/main_vu.cpp pero ese directorio obviamente no existe, tambien esta -I. que punto es el directorio actual... pero tampoco existe una carpeta con ese nombre. no compila, no se que pasa.
Aclaro que instale un par de bibliotecas de SDL que me faltaban por que antes ni esta salida me tiraba, pero ahora ya no se como seguir.
Agradeceria cualquier tipo de ayuda, y gracias por leer. Salu2!!

---

### Post by faktorqm on 2008-08-28
Bueno, ya lo solucioné. Encontré un .deb de la misma versión que había sido compilada y empaquetada por un programador asi que estoy muy muy contento, mis conocimientos no daban para tanto. Acá obviamente les dejo el .deb para todos aquellos que lo deseen instalar este programa. 
Salu2!!

---

