---
title: "No me deja actualizar a Opera 10"
date: 2009-09-05
forum: Software
---

### Post by GerryEastwood on 2009-09-05
Uso Opera como navgador de internet. Instalé sin problemas el 9.64 pero ahora bajo la versión 10 y no puedo instalarla.

Ya la bajé varias veces (sea GDebi Package Installer o Install package (dpkg)) y cuando trata d instalarla me da error:

```
Error: Breaks exisiting package 'opera-static' conflict: opera ( )
```

:confused:

Gracias.

---

### Post by pablo.s on 2009-09-05
Lo que tenés que hacer es 
desinstalar la versión vieja
de Opera 9.algo

```
sudo apt-get remove opera
```

y después te va a dejar hacer
la instalación de la versión 10.

---

### Post by GerryEastwood on 2009-09-05
¡Ah! Era eso. Supuse que podría ser.

Gracias.

---

### Post by GerryEastwood on 2009-09-05
Funcionó, gracias.

---

