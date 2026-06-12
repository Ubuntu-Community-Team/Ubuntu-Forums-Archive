---
title: "archivos .swf?"
date: 2010-08-24
forum: Software
---

### Post by Sargento_Loco on 2010-08-24
Tengo un problema: no logro abrir los archivos .swf, cuando intento abrirlos me los muestra como videos y mas que videos son presentaciones de un paso a paso de la facultad. ademas no logro bajar el flash de adobe porque el gestor no lo abre..... si alguien me puede decir que es lo que tengo que hacer... 
desde ya gracias.-

---

### Post by sartrejp on 2010-08-25
En mi caso, para jugar unos juegos, los incrusté en una página web. 
```
<html>
<head>
<title>Titulo que le quieras poner</title>
</head>
<body>
<object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"
codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,29,0"
width="532" height="532">
 <param name="movie" value="archivo.swf" />
 <param name="quality" value="high" />
 <embed src="TU_ARCHIVO.swf" quality="high"
pluginspage="http://www.macromedia.com/go/getflashplayer"
type="application/x-shockwave-flash" width="432" height="432"></embed>
</object>
</body>
</html>
```

Lo guardás con cualquier nombre.html y lo abrís con el navegador.
Cambiando width y height controlás el tamaño.
Espero que te sirva.

---

### Post by josecuervo86 on 2010-08-25
Intentaste abrirlos con swfdec? esta en los repositorios, cuando bajo alguno de esos juegos los abre re bien. El paquete esta en synaptic, se llama **swfdec-gnome**

---

