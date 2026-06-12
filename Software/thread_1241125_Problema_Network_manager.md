---
title: "Problema Network manager"
date: 2009-08-15
forum: Software
---

### Post by crynof on 2009-08-15
Hola como estan?
Tengo un problema bien raro.
Uso Ubuntu 9.04, y Kubuntu 9.04, con ambos me pasa igual.
Pasa que cuando quiero conectar a una red inalambrica, escribo la pass y empieza a conectar, pero despues se cae y dice fallo de conexion (pasa con todas las redes), y si reinicio el pc, despues dice que para las redes inalambricas el dispositivo no esta siendo gestionado.
Si voy a /etc/networks/interface, borro la config de interface, luego reinicio, ahi si me vuelve a detectar las rede, pero al conectar, sucede lo mismo, se cae y no conecta.
Osea no puedo usar el inet, parece q hay algun bug ahi, pero lo mas raro es que antes teniendo Ubuntu 9.04 instalado, nunca tuve problemas, hasta que formatee, lo reinstale, y no hay caso.
Alguien sabe por que sucede eso.
En kubuntu pasa igual, dice fallo de conexion.
No quiero usar wicd, nunca me ha funcionado bien, prefiero tener networkmanager por q tiene mas opcines.
Alguein sabe como solucionar el problema?
Ojala que peudan ayudarme
Saludos y muchas grax:P

---

### Post by Carlos C on 2009-08-16
Hola. Me parece que podríamos partir por ver qué te sale cuando escribes en el terminal:
```
iwconfig
```
También copia lo que aparece cuando escribes:
```
lspci
```
Saludos.

---

