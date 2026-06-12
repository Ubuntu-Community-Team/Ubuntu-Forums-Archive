---
title: "Actualizaciones automaticas"
date: 2009-11-27
forum: Software
---

### Post by emiliano_raso on 2009-11-27
Alguien sabe porqué las actualizaciones automaticas de aplicaciones no aparecen mas en el update-notifier???
Se que es un cambio de la version 9.10, pero quiero saber las razones.
O al menos si me pueden pasar un link con información les agradezco.

Me llama la atención porque es re poco user-friendly upgradear por terminal. Para los usuarios nuevos seria molesto y poco practico, por lo cual tendrian un sistema desactualizado, teniendo en cuenta que las actualizaciones automaticas y gratuitas son uno de los aspectos mas importantes de Ubuntu y GNU/Linux (o al menos para mi.)

Saludos.

EDIT: Me parece que esto tendria que ir en COMUNIDAD porque se entiende mejor despues de una cerveza, pero tambien tendria que ir a Software porque sólo se puede insultar...
> **Hei Ku said:**
> 
Como regla general:
- Si se puede patear, va a hardware. Los drivers estan incluidos.
- Si sólo se puede insultar, va a software.
- Si la discusion se entiende mejor despues de una cerveza, va a Comunidad. ;)

---

### Post by Mauro22 on 2009-11-27
El cambio es que Karmic sólo avisa de los updates importantes. Para todo lo demas, tenes que darle al boton "comprobar" vos mismo... Lo unico que se instala sólo es lo que 'Ubuntu' considera necesario.

La consola y Gestor de actualizaciones no tiene diferencias. Hacen lo mismo.

---

### Post by emiliano_raso on 2010-06-15
Para actualizar, tiren en consola el siguiente comando asi les actualiza todo (excepto a una nueva version de Ubuntu):

```
sudo aptitude update && sudo aptitude full-upgrade
```

---

