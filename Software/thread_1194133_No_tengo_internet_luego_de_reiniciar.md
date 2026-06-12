---
title: "No tengo internet luego de reiniciar"
date: 2009-06-22
forum: Software
---

### Post by Tenisfan on 2009-06-22
Bueno, el motivo de este post es el siguiente: Tengo instalado Jaunty 9.04 de 64 bits sobre una laptop Toshiba A215-S5822, y funciona más que aceptablemente, aunque tengo un problema cuando la pongo en modo suspensión (y en hibernación también). 
El problema es que cuando el sistema se reanuda, se conecta de nuevo a la red wifi sin problemas, pero ya no puedo acceder a internet, y no me queda otra que reiniciar el sistema, razón por la cual ya directamente la apago cuando sé que voy a estar ausente un tiempo largo. Obviamente es un garrón cerrar todo para apagar, en el sistema win la tengo configurada para que suspenda cuando cierro la tapa, y es mucho mas cómodo. ¿Hay alguna solución a este problema o es un bug del sistema? 
Como siempre, gracias por la ayuda a toda la comunidad
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by Hei Ku on 2009-06-22
Proba con:

sudo /etc/init.d/networking restart

Por otro lado, que usas para conectarte? NetworkManager? Probaste con darle para reconectar manualmente?

---

### Post by Tenisfan on 2009-06-22
> **Hei Ku said:**
> Proba con:

sudo /etc/init.d/networking restart

Por otro lado, que usas para conectarte? NetworkManager? Probaste con darle para reconectar manualmente?
Mira, uso el programa que viene por defecto en Jaunty, creo que si es ese. Tambien probé reconectar haciendo click sobre el ícono del minigestor (el q tiene las barritas de intensidad de señal) pero no puedo recuperar la conexión a internet (repito que si se reconecta a mi red casera, pero no a internet)
Voy a probar con el comando que me diste y despues te cuento como me fue
**EDIT:** Sigo teniendo el mismo problema, probé y no funciona tu sugerencia
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by Tenisfan on 2009-06-24
Alguna otra sugerencia?
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by Hei Ku on 2009-06-24
Postea el resultado de ifconfig antes y despues de hibernar.

---

