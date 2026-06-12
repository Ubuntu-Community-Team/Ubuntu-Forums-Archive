---
title: "Raid sobre particion con datos"
date: 2009-07-13
forum: Software
---

### Post by jpmorelli on 2009-07-13
Buenas, alguien sabe si puedo crear un RAID agregando un disco a mi server sin necesidad de formatear y manteniendo los datos que ya existen en las particiones ?
La utilidad a usar es mdadm obvio. Ya lo utlizé antes pero arrancando desde cero. Se podrá crear sin perder la info que ya existe ? Gracias.

---

### Post by clasificado on 2009-07-13
Que yo sepa: no :)

Lo que se puede hacer es lvm sobre medio disco y copiar las cosas de la mitad no-raid a la mitad raid (sea lvm o raid por hardware)

clasificado

---

### Post by jpmorelli on 2009-07-13
Ok, muchas gracias. Estaba casi seguro de que solo podía hacer eso pero quería confirmarlo con alguien más. 
Gracias clasificado !

---

