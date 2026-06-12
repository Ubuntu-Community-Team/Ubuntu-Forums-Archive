---
title: "consulta técnica al hacer apt-get"
date: 2009-12-24
forum: Software
---

### Post by asterix77 on 2009-12-24
Cuando quiero instalar algo vía apt-get aparece lo siguiente en consola:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  liblash2 libsad2 libfluidsynth1 libftgl2 libglew1.5 libcddb2 libprojectm2
  libaudutil1 libprojectm-data libbinio1ldbl libaudclient2
  libresid-builder0c2a libmowgli1 libaudcore1 libsidplay2 libmcs1
  libaudid3tag2
Utilice «apt-get autoremove» para eliminarlos.
Se instalarán los siguientes paquetes NUEVOS:


Mis consultas: esos paquetes "no necesarios"


[LIST=1]
[*]¿Se instalan todos en forma manual (por la terminal con apt-get), o no necesariamente?
[*]¿quedan cuando se desinstala algún programa?. Por que si es así ¿no se supone que al eliminar un programa también se desinstalan sus dependencias?
[*]¿puedo removerlos como sugiere apt-get en forma segura (apt-get autoremove), sin tener complicaciones en algún otro programa.
[/LIST]

Saludos

---

### Post by moreback on 2009-12-24
1. No necesariamente, pero en general son automáticos como dependencias de otros programas.

2. Son dependencias de otros programas, por lo que se instalan automáticamente, pero al desinstalar el programa original ya no son necesarios. El sistema no los desinstala automaticamente porque pueden existir otros programas que dependean de ellos.

3. Sí, no deberías tener problemas, a menos que sean dependencias de algún programa que compilaste e instalaste manualmente (./configure; make; make install), saltándote el sistema de dpkg.

Saludos.

---

