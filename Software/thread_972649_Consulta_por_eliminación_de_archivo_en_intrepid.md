---
title: "Consulta por eliminación de archivo en intrepid"
date: 2008-11-06
forum: Software
---

### Post by chulelinux on 2008-11-06
Hola gente... tratando de instalar algunas cosas eliminé el archivo o directorio rcS.d en /etc/init.d/ sin posibilidad de recuperar. Por lo que leí sin entender mucho parece importante aunque no noté ningún mal funcionamiento... ¿Alquien me puede decir si es importante o no y si lo puedo recuperar o crear de algún modo?

Saludos

---

### Post by guillermolisi on 2008-11-07
> **chulelinux said:**
> Hola gente... tratando de instalar algunas cosas eliminé el archivo o directorio rcS.d en /etc/init.d/ sin posibilidad de recuperar. Por lo que leí sin entender mucho parece importante aunque no noté ningún mal funcionamiento... ¿Alquien me puede decir si es importante o no y si lo puedo recuperar o crear de algún modo?

Saludos

En mi /etc/init.d tengo solamente rcS (sin el .d que mencionas en tu mensaje).

El contenido del mismo es el siguiente:
```

#! /bin/sh
#
# rcS
#
# Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
#

exec /etc/init.d/rc S
```Para tu informacion estoy usando 8.04 y KDE 3.5.10 que no creo influya enelcontenido de ese archivo, pero lo menciono por las dudas.

Si alguien mas confirma que no hay tal rcS.d y que el contenido del rcS es el mismo, con copiar y pegar lo que te puse como codigo te permitira recuperarlo.

Ese archivo es del user root, grupo root con permisos 755 (rwxr-xr-x)

Con un editor tipo vim, vi, o uno equivalente grafico (kate si usas KDE) es suficiente.

---

### Post by hictio on 2008-11-07
En Intrepid, en /etc/init.d/, estos son los archivos 'rc*' son:
```

esteban@tango:/etc/init.d$ ls rc*
rc  rc.local  rcS

```

Son todos archivos de texto, y el contenido de 'rcS' es exactamente igual en Intrepid al que posteo guillermolisi de su Hardy.
Por curiosidad, como te volaste ese archivo?

---

### Post by chulelinux on 2008-11-07
Gracias por la data. El rcS lo tengo, también tenía uno .d que no se bien para que era y por las dudas consultaba. Este lo eliminé implementando varias veces un tuto ( [http://lihuen.linti.unlp.edu.ar/index.php/Configuraci%C3%B3n_de_placa_sintonizadora_de_tv_encore_enltv-fm_pci](http://lihuen.linti.unlp.edu.ar/index.php/Configuraci%C3%B3n_de_placa_sintonizadora_de_tv_encore_enltv-fm_pci) ) para tratar de hacer andar el remoto de la sinto encore. Y entre tanto probar y borrar lo que iba haciendo volé el archivo... Lamentablemente el control remoto nunca funcionó....

---

