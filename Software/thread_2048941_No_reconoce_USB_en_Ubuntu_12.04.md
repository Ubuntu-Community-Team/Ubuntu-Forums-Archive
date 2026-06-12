---
title: "No reconoce USB en Ubuntu 12.04"
date: 2012-08-27
forum: Software
---

### Post by Leeen on 2012-08-27
Acabo de instalar 
Cuando corro lsusb en una terminal me aparece esto:

Ubuntu 12.04 y no me reconoce los puertos USB.root@lautaro-Aspire-5100:/home/lautaro# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Probe con distintos pendrives y con un ipod y nada. no reconoce nada

Agradezco alguna ayuda por favor

---

### Post by ercherramon on 2012-09-01
hola. prueba insertando un pendrive por favoy y has un:

dmesg

pon las ultimas 6 lineas de la respuesta del informe que te da. para ver que error te está dando los puertos.

hace algún tiempo me dio problema una Acer Aspire con los puertos USB, la destapé, la limpié bien, revisé el cableado y las soldaduras de los puertos y casualmente después de intentarlo todo me tocó actualizar el BIOS, crucé los dedos y los Puertos volvieron a la vida. No digo que sea una solución a tu problema pero es posible que sea una de las tantas fallas que tienen estas Notebooks y así se han corregido con una actualización.

---

