---
title: "Horario de invierno en Thunderbird!"
date: 2016-05-24
forum: Software
---

### Post by donmatas on 2016-05-24
Un problema muy chileno. Uso el calendario de Thunderbird sincronizado con gmail y con el calendario institucional de mi pega (con ligthening). EL problema es que cuando agrego un evento de gmail desde thunderbird o desde gmail, lo agenda una hora más tarde. Creo que el problema es producto de los jugosos del MInisterio de Energía y sus constantes y geniales cambios de zona horaria. Estuve rebuscando por ahí y encontré el archivo "zones.json" aqui: /home/usuario/.thunderbird/qbfgl38o.default/extensions/{e2fda1a4-762b-4020-b5ad-a41df1933103}/timezones

Ahí encontré lo que parece ser el problema:

```
"America/Santiago": {
      "ics": "BEGIN:VTIMEZONE\r\nTZID:America/Santiago\r\nBEGIN:STANDARD\r\nTZOFFSETFROM:**-0300**\r\nTZOFFSETTO:**-0300**\r\nTZNAME:CLT\r\nDTSTART:19700101T000000\r\nEND:STANDARD\r\nEND:VTIMEZONE",
      "latitude": "-0332700",
      "longitude": "-0704000"
    },
```

Se me ocurrió cambiar los valores -0300 por -0400. Luego cerré el thunderbird desde el terminal

```
$ killall thunderbird 
```

Lo volví a abrir, pero el problema persiste.

¿alguna sugerencia?

gracias
M

---

### Post by donmatas on 2016-05-24
Muchachos. Problema resuelto. Era cosa de reiniciar la máquina completa y no sólo el thundebird.

Advierto al público que lo más probable es que cuando volvamos a la zona horaria de Brasil (-3, ¡genios!), habrá que revertir el cambio.

salud!
M

---

### Post by rthelmofp on 2016-10-10
Gracias por la ayuda, hace mucho que no ocupo el calendario de Thunderbird con Lightnig, pero si lo llego a requerir me servirá mucho esta solución.
Saludos.

---

