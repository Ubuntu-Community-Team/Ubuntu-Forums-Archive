---
title: "Administrador de paquetes confiable y seguro?"
date: 2019-01-31
forum: Software
---

### Post by Daniel TL on 2019-01-31
Buenas noches

Estoy usando Lubuntu 18.04 y estoy muy contento y sin inconveniente alguno.
Pero tengo una duda: **¿Qué administrador de paquetes (en línea de comandos) se sugiere usar actualmente o, al menos, con esta versión?**

Hace muchos años comencé a usar Debian Woody, y allí usaba _apt-get_. Después de un tiempo (ya no recuerdo en qué versión), desde Debian sugirieron que _aptitude_ era más adecuado para mantener el sistema, así que dejé de usar apt-get y comencé a usar aptitude.

Después de Debian me pasé a _Ubuntu (6.06) y siempre usé aptitude_. Usé Ubuntu hasta la 16.04, siempre con aptitude y sin problema alguno.

Luego, por mi trabajo comencé a usar **Huayra** (una distribución educativa hecha en Argentina, basada en Debian) y también usé siempre _aptitude_.

Hasta que compré esta portátil HP y le he instalado Lubuntu 18.04 Y con él me enteré de la herramienta **apt** (así, a secas). De todas maneras continué usando aptitude, por costumbre.
Pero comencé a tener problemas... Algunos paquetes no se instalan, a veces falla el proceso de actualización e inconvenientes así._ Y siempre los he resuelto usando apt..._

Así que esa es mi pregunta: **Actualmente conviene usar apt y ya no aptitude? Qué ha cambiado?**

Les agradezco alguna sugerencia, alguna indicación al respecto.

Muchas gracias!!

---

### Post by TheFu on 2019-02-02
In order of preference:
1) apt # a wrapper around apt-get
2) apt-get
3) aptitude # it resolves some dependency issues better than the others, but has some issues.

99% of the time, it shouldn't matter which you use. They all used dpkg and the APT database on the back end.

---

