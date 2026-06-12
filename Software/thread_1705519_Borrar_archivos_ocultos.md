---
title: "Borrar archivos ocultos"
date: 2011-03-12
forum: Software
---

### Post by EnriqueK on 2011-03-12
Estoy preparando un script para hacer mantenimiento del sistema, entre los comando que requiero está el de borrar el contenido de las diferentes papeleras, por ejemplo para vaciar la de todos los usuarios ejecuto
sudo rm -rf /home/*/.local/share/Trash/*/*
el problema está en no elimina los archivos ocultos, por lo que para eliminar a estos, debo poner
sudo rm -rf /home/*/.local/share/Trash/*/.*
En definitiva lo que busco es la manera de emplear un solo comando y de preferencia que haga uso adecado de comodines cono ser * :: etc



















el problema está en no eliniba los archivos ocultos, por lo que para eliminar a estos, debo poner
# rm -rf /home/*/.local/share/Trash/*/.*
En definitiva lo que busco es la manera de emplear un solo comando

---

### Post by juancarlospaco on 2011-03-13
Borra la carpeta Trash entera...   cuando el usuario la vuelva a usar esta se creara automaticamente...

---

### Post by EnriqueK on 2011-03-13
Si lo se, el tema es que quiero tener en claro el por que los archivos ocultos tienen que tener un tratamiento especial o diferente al de los otros archivos.
Doy el tema por solucionado dado que encontré la expresión que estaba bucando
**sudo rm -rf /home/*/.local/share/Trash/*/{*,.*}**

---

