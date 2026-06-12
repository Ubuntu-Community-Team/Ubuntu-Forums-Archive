---
title: "Partición de ubuntu llena"
date: 2011-03-17
forum: Software
---

### Post by nahuel_89p on 2011-03-17
Buenas gente, les comento... cada vez que prendo la pc me salta el cartel que dice que me quedan varios pocos cientos de mb libres. Esta partición es de 16GB en total. Para la última vez que instalé Ubuntu, hace poco más de un año, había leído que no eran necesarios más de 15GB puesto que, si tenes otra partición u otro disco duro donde guardar musica, peliculas, archivos, etc (como ocurre en mi caso), con 15GB iba a bastar para el sistema operativo.
Cuando entro al directorio raíz, y le doy click derecho para averiguar el tamaño de todas las carpetas (no hay ocultos), me da 8,4GB. Es decir, hay otros 6GB que no puedo explicar. Ya borré los kernels viejos (o algo así) con el ubuntu tweak, pero no ha sido de graan ayuda. La papelera de reciclaje esta vacía, y la única cuenta que uso es la de mi usuario, y no hay otras cuentas.
No quisiera aumentar el tamaño de la partición, quiero creer que 16GB son suficientes para las necesidades del S.O, ya que el resto de mis documentos los guardo en otra partición o en un disco duro externo.

Escucho sus sugerencias.

---

### Post by EnriqueK on 2011-03-17
Ejecuta los siguientes comandos
 sudo -i
 rm -Rf /home/*/.local/share/Trash/*/{*,.*}
 rm -Rf /root/.local/share/Trash/*/{*,.*}
 rm -Rf /media/*/.Trash*/*/{*,.*}
 rm -Rf /.Trash*/*/{*,.*}
 rm -Rf /home/*/.thumbnails/*/*
 rm -Rf /home/*/.wine/dosdevices/c:/windows/temp/*
 rm -Rf /home/*/.macromedia/Flash_Player/#SharedObjects/*

---

### Post by juancarlospaco on 2011-03-17
Usa el Bleachbit...

---

