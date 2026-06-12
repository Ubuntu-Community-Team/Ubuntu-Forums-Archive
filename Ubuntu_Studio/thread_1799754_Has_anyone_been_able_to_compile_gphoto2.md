---
title: "Has anyone been able to compile gphoto2?"
date: 2011-07-08
forum: Ubuntu Studio
---

### Post by wrybread on 2011-07-08
I'm trying to install gphoto2 from source since its a newer version than is in the apt repository (as of typing this, apt-get has version 2.4.10-1, while the [gphoto website]("http://sourceforge.net/projects/gphoto/files/gphoto/2.4.11/") has version 2.4.11-1).

Here are my steps to install:

```
wget http://sourceforge.net/projects/gphoto/files/gphoto/2.4.11/gphoto2-2.4.11.tar.gz
tar -xvvf gphoto2-2.4.11.tar.gz
cd gphoto2-2.4.11
./configure
make
make install

```

To get past ./configure I had to also run:

```
apt-get install libpopt-dev
```

I may have also needed these:

```
apt-get install libusb-dev
apt-get install libtool

```

make fails with the following:

```
make  all-recursive
make[1]: Entering directory `/home/wrybread/gphoto2-2.4.11'
Making all in m4m
make[2]: Entering directory `/home/wrybread/gphoto2-2.4.11/m4m'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/wrybread/gphoto2-2.4.11/m4m'
Making all in contrib
make[2]: Entering directory `/home/wrybread/gphoto2-2.4.11/contrib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/wrybread/gphoto2-2.4.11/contrib'
Making all in doc
make[2]: Entering directory `/home/wrybread/gphoto2-2.4.11/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/wrybread/gphoto2-2.4.11/doc'
Making all in gphoto2
make[2]: Entering directory `/home/wrybread/gphoto2-2.4.11/gphoto2'
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../gphoto2 -DLOCALEDIR=\"/usr/local/share/locale\" -Wall -Wmissing-declarations -Wmissing-prototypes -g -D_GPHOTO2_INTERNAL_CODE       -I/usr/include -g -O2 -Wall -g  -o gphoto2   gphoto2-actions.o gphoto2-foreach.o gphoto2-gp-params.o gphoto2-spawnve.o gphoto2-main.o gphoto2-version.o gphoto2-range.o gphoto2-shell.o    -lpthread     -L/usr/lib64 -lpopt 
libtool: link: gcc -I.. -I../gphoto2 -DLOCALEDIR=\"/usr/local/share/locale\" -Wall -Wmissing-declarations -Wmissing-prototypes -g -D_GPHOTO2_INTERNAL_CODE -I/usr/include -g -O2 -Wall -g -o gphoto2 gphoto2-actions.o gphoto2-foreach.o gphoto2-gp-params.o gphoto2-spawnve.o gphoto2-main.o gphoto2-version.o gphoto2-range.o gphoto2-shell.o  -lpthread -L/usr/lib64 /usr/lib/libpopt.so
gphoto2-actions.o: In function `display_widgets':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1361: undefined reference to `gp_widget_get_label'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1363: undefined reference to `gp_widget_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1365: undefined reference to `gp_widget_get_type'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1372: undefined reference to `gp_widget_count_children'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1384: undefined reference to `gp_widget_get_child'
gphoto2-actions.o: In function `_find_widget_by_name':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1409: undefined reference to `gp_camera_get_config'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1411: undefined reference to `gp_widget_get_child_by_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1413: undefined reference to `gp_widget_get_child_by_label'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1431: undefined reference to `gp_widget_get_child_by_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1433: undefined reference to `gp_widget_get_child_by_label'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1444: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1446: undefined reference to `gp_widget_free'
gphoto2-actions.o: In function `delete_all_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:65: undefined reference to `gp_camera_folder_delete_all'
gphoto2-actions.o: In function `action_camera_upload_file':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:74: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:76: undefined reference to `gp_file_new_from_fd'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:77: undefined reference to `gp_file_open'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:85: undefined reference to `gp_file_set_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:91: undefined reference to `gp_camera_folder_put_file'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:93: undefined reference to `gp_file_unref'
gphoto2-actions.o: In function `action_camera_upload_metadata':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:103: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:105: undefined reference to `gp_file_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:106: undefined reference to `gp_file_open'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:114: undefined reference to `gp_file_set_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:126: undefined reference to `gp_file_set_type'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:128: undefined reference to `gp_camera_folder_put_file'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:130: undefined reference to `gp_file_unref'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:120: undefined reference to `gp_file_set_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:122: undefined reference to `gp_file_unref'
gphoto2-actions.o: In function `num_files_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:140: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:141: undefined reference to `gp_camera_folder_list_files'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:143: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:154: undefined reference to `gp_camera_file_get_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:153: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:153: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:164: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:143: undefined reference to `gp_list_free'
gphoto2-actions.o: In function `list_folders_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:182: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:184: undefined reference to `gp_camera_folder_list_folders'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:186: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:193: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:193: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:196: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:186: undefined reference to `gp_list_free'
gphoto2-actions.o: In function `print_info_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:249: undefined reference to `gp_camera_file_get_info'
gphoto2-actions.o: In function `print_file_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:341: undefined reference to `gp_camera_file_get_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:328: undefined reference to `gp_camera_file_get_info'
gphoto2-actions.o: In function `list_files_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:208: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:209: undefined reference to `gp_camera_folder_list_files'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:211: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:218: undefined reference to `gp_camera_file_get_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:217: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:238: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:237: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:209: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:240: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:211: undefined reference to `gp_list_free'
gphoto2-actions.o: In function `delete_file_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:424: undefined reference to `gp_camera_file_get_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:430: undefined reference to `gp_camera_file_delete'
gphoto2-actions.o: In function `print_exif_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:528: undefined reference to `gp_context_error'
gphoto2-actions.o: In function `list_cameras_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:540: undefined reference to `gp_abilities_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:551: undefined reference to `gp_abilities_list_get_abilities'
gphoto2-actions.o: In function `_get_portinfo_list':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:584: undefined reference to `gp_port_info_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:586: undefined reference to `gp_port_info_list_load'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:591: undefined reference to `gp_port_info_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:593: undefined reference to `gp_port_info_list_free'
gphoto2-actions.o: In function `list_ports_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:607: undefined reference to `gp_port_info_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:619: undefined reference to `gp_port_info_list_get_info'
gphoto2-actions.o: In function `auto_detect_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:636: undefined reference to `gp_port_info_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:638: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:639: undefined reference to `gp_abilities_list_detect'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:641: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:647: undefined reference to `gp_list_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:646: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:647: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:650: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:641: undefined reference to `gp_list_free'
gphoto2-actions.o: In function `action_camera_show_abilities':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:661: undefined reference to `gp_camera_get_abilities'
gphoto2-actions.o: In function `action_camera_set_port':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:750: undefined reference to `gp_port_info_list_lookup_path'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:767: undefined reference to `gp_port_info_list_get_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:772: undefined reference to `gp_camera_set_port_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:775: undefined reference to `gp_setting_set'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:720: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:740: undefined reference to `gp_log'
gphoto2-actions.o: In function `action_camera_about':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:784: undefined reference to `gp_camera_get_about'
gphoto2-actions.o: In function `action_camera_summary':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:797: undefined reference to `gp_camera_get_summary'
gphoto2-actions.o: In function `action_camera_manual':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:810: undefined reference to `gp_camera_get_manual'
gphoto2-actions.o: In function `action_camera_set_speed':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:824: undefined reference to `gp_camera_get_port_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:834: undefined reference to `gp_camera_set_port_speed'
gphoto2-actions.o: In function `action_camera_set_model':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:843: undefined reference to `gp_abilities_list_lookup_model'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:844: undefined reference to `gp_abilities_list_get_abilities'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:845: undefined reference to `gp_camera_set_abilities'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:846: undefined reference to `gp_setting_set'
gphoto2-actions.o: In function `action_camera_capture_preview':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:932: undefined reference to `gp_file_new_from_fd'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:944: undefined reference to `gp_camera_capture_preview'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:954: undefined reference to `gp_file_unref'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:929: undefined reference to `gp_file_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:947: undefined reference to `gp_file_unref'
gphoto2-actions.o: In function `action_camera_capture_movie':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1000: undefined reference to `gp_file_new_from_fd'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1003: undefined reference to `gp_camera_capture_preview'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1008: undefined reference to `gp_file_get_mime_type'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1029: undefined reference to `gp_file_unref'
gphoto2-actions.o: In function `action_camera_wait_event':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1070: undefined reference to `gp_camera_wait_for_event'
gphoto2-actions.o: In function `print_storage_info':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1141: undefined reference to `gp_camera_get_storageinfo'
gphoto2-actions.o: In function `override_usbids_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1232: undefined reference to `gp_abilities_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1238: undefined reference to `gp_abilities_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1254: undefined reference to `gp_abilities_list_append'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1240: undefined reference to `gp_abilities_list_get_abilities'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1246: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1257: undefined reference to `gp_abilities_list_free'
gphoto2-actions.o: In function `debug_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1310: undefined reference to `gp_log_add_func'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1311: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1325: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1326: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1328: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1338: undefined reference to `gp_log'
gphoto2-actions.o:/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1344: more undefined references to `gp_log' follow
gphoto2-actions.o: In function `list_config_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1398: undefined reference to `gp_camera_get_config'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1401: undefined reference to `gp_widget_free'
gphoto2-actions.o: In function `get_config_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1483: undefined reference to `gp_widget_get_type'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1488: undefined reference to `gp_widget_get_label'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1511: undefined reference to `gp_widget_get_range'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1575: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1586: undefined reference to `gp_widget_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1561: undefined reference to `gp_widget_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1563: undefined reference to `gp_widget_count_choices'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1571: undefined reference to `gp_widget_get_choice'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1528: undefined reference to `gp_widget_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1543: undefined reference to `gp_widget_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1499: undefined reference to `gp_widget_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1513: undefined reference to `gp_widget_get_value'
gphoto2-actions.o: In function `set_config_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1600: undefined reference to `gp_widget_get_readonly'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1610: undefined reference to `gp_widget_get_type'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1748: undefined reference to `gp_camera_set_config'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1752: undefined reference to `gp_widget_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1750: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1696: undefined reference to `gp_widget_count_choices'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1705: undefined reference to `gp_widget_get_choice'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1666: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1618: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1688: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1743: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1686: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1626: undefined reference to `gp_widget_get_range'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1635: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1709: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1606: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1607: undefined reference to `gp_widget_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1732: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1735: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1639: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1641: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1724: undefined reference to `gp_widget_get_choice'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1726: undefined reference to `gp_widget_set_value'
gphoto2-actions.o: In function `set_config_index_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1767: undefined reference to `gp_widget_get_type'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1772: undefined reference to `gp_widget_get_label'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1783: undefined reference to `gp_widget_count_choices'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1793: undefined reference to `gp_widget_get_choice'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1795: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1820: undefined reference to `gp_widget_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1811: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1816: undefined reference to `gp_camera_set_config'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1818: undefined reference to `gp_context_error'
gphoto2-actions.o: In function `set_config_value_action':
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1835: undefined reference to `gp_widget_get_type'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1956: undefined reference to `gp_camera_set_config'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1960: undefined reference to `gp_widget_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1958: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1920: undefined reference to `gp_widget_count_choices'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1929: undefined reference to `gp_widget_get_choice'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1891: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1851: undefined reference to `gp_widget_get_range'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1860: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1843: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1913: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1951: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1911: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1933: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1941: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1943: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1864: undefined reference to `gp_widget_set_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/actions.c:1866: undefined reference to `gp_context_error'
gphoto2-foreach.o: In function `get_path_for_id_rec':
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:199: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:200: undefined reference to `gp_camera_folder_list_files'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:202: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:206: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:207: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:209: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:213: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:215: undefined reference to `gp_camera_folder_list_folders'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:215: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:217: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:219: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:230: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:234: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:217: undefined reference to `gp_list_free'
gphoto2-foreach.o: In function `get_path_for_id':
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:269: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:271: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:272: undefined reference to `gp_camera_folder_list_files'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:274: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:278: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:281: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:303: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:305: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:274: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:292: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:292: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:299: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:284: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:289: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:254: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:303: undefined reference to `gp_list_free'
gphoto2-foreach.o: In function `for_each_folder':
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:66: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:75: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:77: undefined reference to `gp_camera_folder_list_folders'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:79: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:102: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:102: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:82: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:82: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:121: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:118: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:108: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:79: undefined reference to `gp_list_free'
gphoto2-foreach.o: In function `for_each_file':
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:133: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:135: undefined reference to `gp_camera_folder_list_files'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:137: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:145: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:161: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:140: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:157: undefined reference to `gp_camera_folder_list_folders'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:159: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:161: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:179: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:167: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:177: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:159: undefined reference to `gp_list_free'
gphoto2-foreach.o: In function `for_each_file_in_range':
/home/wrybread/gphoto2-2.4.11/gphoto2/foreach.c:342: undefined reference to `gp_log'
gphoto2-gp-params.o: In function `gp_params_init':
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:280: undefined reference to `gp_camera_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:286: undefined reference to `gp_context_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:287: undefined reference to `gp_context_set_cancel_func'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:288: undefined reference to `gp_context_set_error_func'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:289: undefined reference to `gp_context_set_status_func'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:290: undefined reference to `gp_context_set_message_func'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:292: undefined reference to `gp_context_set_progress_funcs'
gphoto2-gp-params.o: In function `gp_params_abilities_list':
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:310: undefined reference to `gp_abilities_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:311: undefined reference to `gp_abilities_list_load'
gphoto2-gp-params.o: In function `gp_params_exit':
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:324: undefined reference to `gp_abilities_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:326: undefined reference to `gp_camera_unref'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:332: undefined reference to `gp_context_unref'
/home/wrybread/gphoto2-2.4.11/gphoto2/gp-params.c:336: undefined reference to `gp_port_info_list_free'
gphoto2-main.o: In function `report_failure':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1587: undefined reference to `gp_result_as_string'
gphoto2-main.o: In function `signal_exit':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1034: undefined reference to `gp_camera_unref'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1036: undefined reference to `gp_context_unref'
gphoto2-main.o: In function `save_camera_file_to_file':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:373: undefined reference to `gp_file_get_type'
gphoto2-main.o: In function `get_path_for_file':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:175: undefined reference to `gp_file_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:176: undefined reference to `gp_file_get_mtime'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:332: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:188: undefined reference to `gp_file_get_type'
gphoto2-main.o: In function `save_camera_file_to_file':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:383: undefined reference to `gp_system_is_file'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:420: undefined reference to `gp_system_is_dir'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:421: undefined reference to `gp_system_mkdir'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:434: undefined reference to `gp_file_get_mtime'
gphoto2-main.o: In function `get_path_for_file':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:244: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:277: undefined reference to `gp_context_error'
gphoto2-main.o: In function `camera_file_exists':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:449: undefined reference to `gp_camera_file_get_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:462: undefined reference to `gp_context_error'
gphoto2-main.o: In function `save_file_to_file':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:479: undefined reference to `gp_camera_file_get_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:513: undefined reference to `gp_file_new_from_fd'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:521: undefined reference to `gp_camera_file_get'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:533: undefined reference to `gp_file_get_data_and_size'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:538: undefined reference to `gp_file_unref'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:510: undefined reference to `gp_file_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:543: undefined reference to `gp_file_unref'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:524: undefined reference to `gp_file_unref'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:507: undefined reference to `gp_context_error'
gphoto2-main.o: In function `get_file_common':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:557: undefined reference to `gp_log'
gphoto2-main.o: In function `wait_and_handle_event':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:683: undefined reference to `gp_camera_wait_for_event'
gphoto2-main.o: In function `capture_generic':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:731: undefined reference to `gp_camera_get_abilities'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:808: undefined reference to `gp_camera_capture'
gphoto2-main.o: In function `cb_arg_preinit':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1179: undefined reference to `gp_log'
gphoto2-main.o: In function `cb_arg_init':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1240: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1235: undefined reference to `gp_log'
gphoto2-main.o: In function `cb_arg_run':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1418: undefined reference to `gp_camera_folder_make_dir'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1411: undefined reference to `gp_camera_folder_remove_dir'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1341: undefined reference to `gp_context_error'
gphoto2-main.o: In function `main':
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1930: undefined reference to `gp_camera_set_timeout_funcs'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1972: undefined reference to `gp_camera_get_abilities'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1973: undefined reference to `gp_camera_get_port_info'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2023: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2028: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2029: undefined reference to `gp_abilities_list_detect'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2032: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2131: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2132: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2133: undefined reference to `gp_list_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2138: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2067: undefined reference to `gp_setting_get'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2069: undefined reference to `gp_setting_get'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2071: undefined reference to `gp_camera_init'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1945: undefined reference to `gp_setting_get'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:1951: undefined reference to `gp_setting_get'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2081: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2082: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2083: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2084: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2088: undefined reference to `gp_list_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2090: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2093: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2035: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2036: undefined reference to `gp_list_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2105: undefined reference to `gp_log'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2110: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2111: undefined reference to `gp_abilities_list_lookup_model'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2113: undefined reference to `gp_abilities_list_get_abilities'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2121: undefined reference to `gp_list_get_value'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2041: undefined reference to `gp_abilities_list_lookup_model'
/home/wrybread/gphoto2-2.4.11/gphoto2/main.c:2044: undefined reference to `gp_abilities_list_get_abilities'
gphoto2-version.o:(.rodata+0xc): undefined reference to `gp_library_version'
gphoto2-version.o:(.rodata+0x14): undefined reference to `gp_port_library_version'
gphoto2-range.o: In function `parse_range_rec':
/home/wrybread/gphoto2-2.4.11/gphoto2/range.c:180: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/range.c:164: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/range.c:140: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/range.c:126: undefined reference to `gp_context_error'
/home/wrybread/gphoto2-2.4.11/gphoto2/range.c:158: undefined reference to `gp_context_error'
gphoto2-range.o:/home/wrybread/gphoto2-2.4.11/gphoto2/range.c:204: more undefined references to `gp_context_error' follow
gphoto2-shell.o: In function `shell_rmdir':
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:814: undefined reference to `gp_camera_folder_remove_dir'
gphoto2-shell.o: In function `shell_mkdir':
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:794: undefined reference to `gp_camera_folder_make_dir'
gphoto2-shell.o: In function `shell_ls':
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:658: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:659: undefined reference to `gp_camera_folder_list_folders'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:665: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:666: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:696: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:677: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:677: undefined reference to `gp_camera_folder_list_files'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:683: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:684: undefined reference to `gp_list_get_name'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:663: undefined reference to `gp_list_count'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:681: undefined reference to `gp_list_count'
gphoto2-shell.o: In function `shell_cd':
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:628: undefined reference to `gp_list_new'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:630: undefined reference to `gp_camera_folder_list_folders'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:630: undefined reference to `gp_list_free'
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:632: undefined reference to `gp_list_free'
gphoto2-shell.o: In function `shell_prompt':
/home/wrybread/gphoto2-2.4.11/gphoto2/shell.c:496: undefined reference to `gp_result_as_string'
collect2: ld returned 1 exit status
make[2]: *** [gphoto2] Error 1
make[2]: Leaving directory `/home/wrybread/gphoto2-2.4.11/gphoto2'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/wrybread/gphoto2-2.4.11'
make: *** [all] Error 2

```

---

### Post by magnuan on 2011-07-28
Think I got it to work

Installed devel libs for:
libltdl-dev, libaa1-dev, libjpeg8-dev, libreadline-dev, libcdk5-dev, libpopt-dev and libexif-dev
Don't know if really I need them, but 2.4.10 from repo was compiled with them, so...


Then downloaded and installed libgphoto2-2.4.11 from sourceforge
```

./configure
make all
sudo make install all
sudo ldconfig

```
And then the same for gphoto2-2.4.11 from sourceforge.

Checking the version now returns.

```

>gphoto2 -v
gphoto2 2.4.11

Copyright (c) 2000-2011 Lutz Mueller and others

gphoto2 comes with NO WARRANTY, to the extent permitted by law. You may
redistribute copies of gphoto2 under the terms of the GNU General Public
License. For more information about these matters, see the files named COPYING.

This version of gphoto2 is using the following software versions and options:
gphoto2         2.4.11         gcc, popt(m), exif, cdk, aa, jpeg, readline
libgphoto2      2.4.11         gcc, ltdl, EXIF
libgphoto2_port 0.8.0          gcc, ltdl, USB, serial without locking

```

---

### Post by lambermo on 2011-08-14
Thanks for posting. This also works for -HEAD :

gphoto2 -v
gphoto2 2.4.99.2

Copyright (c) 2000-2011 Lutz Mueller and others

gphoto2 comes with NO WARRANTY, to the extent permitted by law. You may
redistribute copies of gphoto2 under the terms of the GNU General Public
License. For more information about these matters, see the files named COPYING.

This version of gphoto2 is using the following software versions and options:
gphoto2         2.4.99.2       gcc, popt(m), exif, cdk, no aa, jpeg, readline
libgphoto2      2.4.99.7       all camlibs, gcc, ltdl, no EXIF
libgphoto2_port 0.10.0         gcc, ltdl, USB, serial without locking

(I see I have to recompile libgphoto2 , no EXIF support in there yet)

---

