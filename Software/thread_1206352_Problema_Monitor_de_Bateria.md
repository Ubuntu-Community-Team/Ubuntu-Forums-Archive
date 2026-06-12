---
title: "Problema Monitor de Bateria"
date: 2009-07-07
forum: Software
---

### Post by adux on 2009-07-07
Estimados,

Hace poco formatie mi laptop (HP 530), y tenia ubuntu 9.04 antes al igual que ahora. Pero al poco rato me di cuenta que el icono de bateria no se movia, despues de horas, seguia en 0%. Asique revisando por ahi, dijieron que lo apagara volviera a poner la bateria etc. Asi lo hice y la bateria marco 100%, pero cuando lo desenchufe, no bajo de 99%. y cuando reinicie marco 84% pero se pego en eso denuevo.

No tengo idea cual pueda ser el problema,

info:
cat /proc/acpi/battery/BAT0/info no me muestra nada

ahora, en ls /proc/acpi/battery me aparece C1AC

 cat /proc/acpi/battery/C1AC/info me muestra esto:

present:                 yes
design capacity:         2000 mAh
last full capacity:      2000 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 103 mAh
design capacity low:     21 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  100 mAh
model number:            Primary
serial number:           35527 2008/01/31
battery type:            LIon
OEM info:                Hewlett-Packard



y no se que otra info necesiten, pero ojala alguien me pueda ayudar!

Saludos :)!

---

