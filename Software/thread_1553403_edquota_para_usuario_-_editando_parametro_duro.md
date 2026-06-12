---
title: "edquota para usuario - editando parametro duro"
date: 2010-08-15
forum: Software
---

### Post by mama21mama on 2010-08-15
Hola,

tengo un inconveniente a la hora de usar este comando

en la practica e creado un usuario con el nombre de test
```
sudo edquota test
```

> Cuotas de disco para user test (uid 1005):
  Sistema de archivos          bloques      blando     duro     inodos     blando   duro
  /dev/sda1                     63816          0      64000        281        0        0



el valor que intento modificar es **duro 64000**, pero no le doy con el valor justo que pretendo yo.

o sea, ando probando de dar un máximo de uso de disco rígido de 129mb pero me perdí en la forma correcta que poner ese valor.

con el valor **duro 64000** puedo meter un archivo de 129,5 MiB y cuando copio el mismo el quote me crea otro de 60,4 MiB.

o sea que el usuario test con el valor **duro 64000** puede ocupar de espacio en disco rígido total 129,5 MiB + 60,4 MiB.

:s

si alguien me explica como usar correctamente ese valor le estaré agradecido.

Saludos

---

