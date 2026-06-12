---
title: "comando netstat"
date: 2008-11-22
forum: Software
---

### Post by ramiro_md on 2008-11-22
Gente tengo un problema con el comando netsat, cuando ejecuto netstat -n además de mostrarme las Conexiones activas de Internet me muestra una serie de líneas como esta:
```
unix  3      [ ]         FLUJO      CONECTADO     (un número)   

```
qué son ? como hago para que netstat discrimine y solo me muetre las conexiones activas a internet sin las lineas que mencioné anteriormente ?.

---

### Post by guillermolisi on 2008-11-22
> **ramiro_md said:**
>  como hago para que netstat discrimine y solo me muetre las conexiones activas a internet sin las lineas que mencioné anteriormente ?.
Ejecuta
```
netstat <ip_publica_de_tu_maquina>
```Y te devuelve todos los ports activos de la conexion.

Para solo tener los ports/sockets a Internet. podes usar
```
netstat <ip_publica_de_tu_maquina> |grep tcp
```Mas info en detalle
```
man netstat
```

---

### Post by sdennie on 2008-11-26
Hay muchas cosas que hablan por "sockets" como un red y estas viendo esas cosas.  Lo mas probable es que querés usar:

```

netstat -tu

```

---

