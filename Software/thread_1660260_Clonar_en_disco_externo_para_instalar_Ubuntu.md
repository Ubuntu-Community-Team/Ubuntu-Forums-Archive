---
title: "Clonar en disco externo para instalar Ubuntu"
date: 2011-01-05
forum: Software
---

### Post by kabeza on 2011-01-05
Hola
Tengo una maquina con un disco de 320gb con Windows XP
Quiero conseguir un disco externo de 1tb y hacer lo siguiente:

- Clonar de alguna forma (rápida) el disco interno al externo
- Formatear el disco de 320
- Instalar Ubuntu en el disco interno
- Leer y copiar desde el externo cualquier carpeta o archivo que me haga falta (mp3, docs, laburo)

Mi consulta principal seria:
**En que formato debería clonar el disco interno en el externo, para que luego pueda leerlo fácilmente con Ubuntu sin tener que descomprimir o copiar de nuevo?**

Espero me hayan entendido la consulta. Gracias!!

---

### Post by mama21mama on 2011-01-05
Mira este [articulo]("http://doc.ubuntu-es.org/Clonar_discos_duros")

Saludos

---

### Post by kabeza on 2011-01-06
> **mama21mama said:**
> Mira este [articulo]("http://doc.ubuntu-es.org/Clonar_discos_duros")

Saludos

Gracias por el dato y permitime por favor hacerte un par de consultas

1) Dado que tengo windows en el disco interno, supongo que deberé hacer esos comandos desde el CD booteable de Ubuntu, no?

2) Una vez hecho **sudo dd if=/dev/hda of=/dev/hdb bs=1M** el disco externo tendra el mismo filesystem, las mismas particiones, carpetas y archivos que mi disco interno, no? sin importar la cantidad y tipo de particiones que tenga, no?

Gracias nuevamente

---

### Post by biale on 2011-01-06
Tendría que clonar el disco completo, incluido el MBR.

Las particiones van a quedar con UUID duplicadas. No es crítico si luego vas formatear el disco original de 320.

Para correr el comando dd cualquier arranque live con nucleo actualizado te sirve. Ojo no vayas a clonar "al reves" (alguna vez me paso).

---

### Post by kabeza on 2011-01-07
gracias biale por el dato

---

