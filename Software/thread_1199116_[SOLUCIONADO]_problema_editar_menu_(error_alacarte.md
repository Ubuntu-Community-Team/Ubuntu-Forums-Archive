---
title: "[SOLUCIONADO] problema editar menu (error alacarte)"
date: 2009-06-28
forum: Software
---

### Post by palbornoz on 2009-06-28
Estimad@s, les escribo para saber si me pueden ayudar, he tratado de editar el menu pero no puedo hacerlo :( lo he tratado por consola y sale el siguiente error:

```

:~$ alacarte 
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permiso denegado: '/home/usuario/.config/menus/applications.menu'

```

Agradeciendo de antemano su pronta respuesta.

Saludos!

---

### Post by palbornoz on 2009-06-28
La verdad que encontré la solución es simplemente:
```

:~$ cd .config/
:~/.config$ sudo chown usuario *.*
:~/.config$ chmod 644 applications.menu

```

Listo! pueden editar el menu con botón derecho o directamente en Sistema->Menú principal

Saludos!

> **palbornoz said:**
> Estimad@s, les escribo para saber si me pueden ayudar, he tratado de editar el menu pero no puedo hacerlo :( lo he tratado por consola y sale el siguiente error:

```

:~$ alacarte 
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permiso denegado: '/home/usuario/.config/menus/applications.menu'

```

Agradeciendo de antemano su pronta respuesta.

Saludos!

---

### Post by Carlos C on 2009-06-28
Movido al subforo "Software".

---

