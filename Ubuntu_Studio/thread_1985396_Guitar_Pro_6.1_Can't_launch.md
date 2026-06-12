---
title: "Guitar Pro 6.1 Can't launch"
date: 2012-05-23
forum: Ubuntu Studio
---

### Post by ZliS on 2012-05-23
Ubuntu Studio 12.04 x86
I have an error and crash of the Guitar pro 6.1
```
Object::connect: No such signal PlaySettingsWidget::tuningChanged() in /home/build-linux/BuildMachine/workspace/gp/Sources/GuitarPro/widgets/UniverseSubWidget.cpp:133
Object::connect: No such signal BankListWidget::tuningChanged() in /home/build-linux/BuildMachine/workspace/gp/Sources/GuitarPro/widgets/UniverseSubWidget.cpp:133
Object::connect:  (sender name:   'SearchTreeWidget')
Object::connect: No such signal QWidget::tuningChanged() in /home/build-linux/BuildMachine/workspace/gp/Sources/GuitarPro/widgets/UniverseSubWidget.cpp:133
Object::connect:  (sender name:   'TrackMidiProperties')

(process:14128): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.1/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:14128): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.1/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:14128): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(process:14128): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:14128): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:14128): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:14128): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; &#1089;&#1077;&#1075;&#1084;&#1077;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1103; (core dumped)

```
Does anybody know anything about that?

---

### Post by Finn bjerke on 2012-05-31
I Dont know about studio, GP6 works well in Ubuntu 12.04, however there are 2 serious flaws:

1) It can not print it seems, also the "supportteam" are not supportive at all, they call themselves "getsatisfaction" 
2) Preview Print does not work in 100% scaled, however in 200% it looks OK. [http://gratisupload.dk/vis_billede/680146/](http://gratisupload.dk/vis_billede/680146/)

The GP6 people blame canonical (off course) 
[http://getsatisfaction.guitar-pro.com/arobas_music/topics/cannot_print_in_ubuntu_12_04?utm_medium=email&utm_source=new_topic&from_gsfn=true](http://getsatisfaction.guitar-pro.com/arobas_music/topics/cannot_print_in_ubuntu_12_04?utm_medium=email&utm_source=new_topic&from_gsfn=true)

  [IMG]http://gratisupload.dk/vis_billede/680146/[/IMG]

---

