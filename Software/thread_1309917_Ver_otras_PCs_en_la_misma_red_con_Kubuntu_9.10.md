---
title: "Ver otras PCs en la misma red con Kubuntu 9.10"
date: 2009-11-01
forum: Software
---

### Post by FB91 on 2009-11-01
no me deja ver los archivos de las otras PC en red.

Ingreso a Red -> Comparticiones Samba y ahi dentro se vé el grupo de trabajo (que se llama CASA) pero adentro no se vé nada

---

### Post by FB91 on 2009-11-01
me dí cuenta que desde Dolphin, entrando a "Comparticiones Samba" y luego en la barra de direcciones escribiendo la IP de la PC que quiero entrar lo hace perfectamente. El problema es que cuando entro al ícono "Comparticiones Samba" no me muestra las 2 PCs que están en red

---

### Post by guillermolisi on 2009-11-01
> **FB91 said:**
> me dí cuenta que desde Dolphin, entrando a "Comparticiones Samba" y luego en la barra de direcciones escribiendo la IP de la PC que quiero entrar lo hace perfectamente. El problema es que cuando entro al ícono "Comparticiones Samba" no me muestra las 2 PCs que están en red
Eso es porque no puede resolver los nombres de las maquinas.

Si son pocas maquinas podes utilizar el archivo /etc/hosts para que se resuelvan los nombres en lugar de tener que ingresar directamente las IPS.

---

### Post by FB91 on 2009-11-02
colocando

192.168.0.1 PC1

en el archivo host.conf me tendría que llevar a esa ip cuando escriba PC1 en la barra de direcciones del Dolphin? porque probé con eso y no vá

---

### Post by guillermolisi on 2009-11-02
> **FB91 said:**
> colocando

192.168.0.1 PC1

en el archivo host.conf me tendría que llevar a esa ip cuando escriba PC1 en la barra de direcciones del Dolphin? porque probé con eso y no vá
El archivo que tenes que editar es /etc/hosts (no lleva ningun .conf) y si, con una entrada como la que decis deberia funcionar bien.

---

### Post by FB91 on 2009-11-02
perfecto, me funcionó.

muchas gracias!!

Solved!

---

