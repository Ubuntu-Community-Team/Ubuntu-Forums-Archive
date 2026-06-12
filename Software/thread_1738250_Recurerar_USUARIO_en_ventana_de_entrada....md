---
title: "Recurerar USUARIO en ventana de entrada..."
date: 2011-04-24
forum: Software
---

### Post by CarlosRuiz on 2011-04-24
Holap:

Cometí una tremenda estupidez:

Cambié la "Ventana de entrada" de mi Ubuntu 8.04, pero no recuerdo el USUARIO...
La ventada de entrada anterior tenía la opción de seleccionar el usuario con un click, pero esta nueva ventana no la tiene, por lo que recuerdo la clave y no el usuario... :(

Qué puedo hacer para volver a entrar a Ubuntu?

Help Plisss... :confused:

Saludooos :(

---

### Post by Patriciologico on 2011-04-24
Entra como root en modo recovery o con un live cd y revisa el fichero /etc/passwd mas facil con el comando

```
less /etc/passwd
```

El primer usuario creado (donde debe estar el tuyo imagino) empieza con el numero 1000, luego 1001 y asi sucesivamente (los anteriores son reservados para el sistema)

Saludos

---

### Post by CarlosRuiz on 2011-04-24
Holap:

Excelenteeee!!!
Funcionó a la perfección lo de buscar en /etc/passwd, encontré al usuario de inmediato... :cool:

Gracias por todooo... O:)

Saludooos :P

---

