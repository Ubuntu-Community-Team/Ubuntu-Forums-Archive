---
title: "Eliminar historial en Unity!"
date: 2012-02-05
forum: Software
---

### Post by z37a on 2012-02-05
Acá les dejo un link a mi blog donde puse un articulo sobre como eliminar el historial en forma automática con cada inicio de sesión!

[http://zele.biz/?p=827](http://zele.biz/?p=827)

Igualmente resumo un poquito el tema:

1º Crear un script en el /usr/bin llamado clearhist (o como quieran) con el siguiente contenido:

```
#!/bin/sh
rm -R ~/.local/share/zeitgeist
rm ~/.local/share/recently-used.xbe*
```

PD: Para ello ejecutar "sudo gedit /usr/bin/clearhist"

2º Darle permisos de ejecucion (sudo chmod a+x /usr/bin/clearhist)

3º Ir al engranaje superior derecho en Unity y seleccionar aplicaciones al inicio, y agregar dicho script.

Con esto cada vez que inicien se borrara el historial que a muchos nos molesta!

---

