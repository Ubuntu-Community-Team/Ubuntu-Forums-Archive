---
title: "compiz plugin"
date: 2008-11-06
forum: Software
---

### Post by tsueseres on 2008-11-06
estoy intentando instalar el plugin de snow que viene en un script de elements  de esta pagina  [http://www.elementsplugin.com/downloads/](http://www.elementsplugin.com/downloads/)

pero cuando se esta instalando me sale esto

```
build/elements_options.c:1335: aviso: declaración externa anidada de ‘freeDisplayPrivateIndex’
build/elements_options.c: En el nivel principal:
build/elements_options.c:1346: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/elements_options.lo] Error 1
Checking for Xgl: not present. 
luis@umi:~/Escritorio$ Detected PCI ID for VGA: 01:00.0 0300: 10de:01d3 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

busque y encontre problemas parecidos pero no pude resolverlo

---

### Post by PatrickFisher on 2008-11-10
Sorry about the delay.

The script has now been updated for Intrepid. It's available here:

[http://www.elementsplugin.com/downloads/elementsinstall.sh](http://www.elementsplugin.com/downloads/elementsinstall.sh)

---

