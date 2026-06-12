---
title: "Problema arrancado desde LiveCD 9.04, el monitor se apaga"
date: 2009-06-27
forum: Software
---

### Post by Axel-Maze on 2009-06-27
Resulta que hace unas semanas por fin me llegó mi copia de Ubuntu Jackalope y me dispuse a probar desde el LiveCD. 

Todo iba bastante bien durante la pantalla de inicio pero después de la pantalla de la barra de progreso y justo cuando va a mostrarse la pantalla de bienvenida (supongo, porque aquí es donde esta el problema) mi monitor se apaga, aunque se sigue cargando el SO porque se puede escuchar la múscia de bienvenida.

Estoy 99% seguro que es algún problema de configuración de la resolución/frecuencia de refresco de mi monitor, porque en Windows (mi actual SO) algunas combinaciones me provocan el mismo problema.

Les dejo los datos de mi PC en cuestión:
- HP Brio, Pentium Celeron (Coppermine) 600 MHz
- 368 MB de RAM
- Audio VIA AC'97 (WDM)
- Chipset VIA
- S3 Graphics ProSavage PM 133 (gráfcos integrados)
- Monitor CTR 14" HP (la resolución/refresco optima: 800*600 @60 Hercios)
- BIOS Award IO.07.06

Sí, es un equipo viejo :P, sin embargo ya lo he probado con Mandriva (ver. 2007) y no tuve ningún impedimento (y eso que dicen que Mandriva es más robusto, etc.)

Espero que me puedan ayudar, pues es una lástima que tenga una copia de Ubuntu y no la pueda usar más allá de la pantalla de inicio :(.

---

### Post by guillermolisi on 2009-06-27
> **Axel-Maze said:**
> Resulta que hace unas semanas por fin me llegó mi copia de Ubuntu Jackalope y me dispuse a probar desde el LiveCD. 

Todo iba bastante bien durante la pantalla de inicio pero después de la pantalla de la barra de progreso y justo cuando va a mostrarse la pantalla de bienvenida (supongo, porque aquí es donde esta el problema) mi monitor se apaga, aunque se sigue cargando el SO porque se puede escuchar la múscia de bienvenida.

Estoy 99% seguro que es algún problema de configuración de la resolución/frecuencia de refresco de mi monitor, porque en Windows (mi actual SO) algunas combinaciones me provocan el mismo problema.

Les dejo los datos de mi PC en cuestión:
- HP Brio, Pentium Celeron (Coppermine) 600 MHz
- 368 MB de RAM
- Audio VIA AC'97 (WDM)
- Chipset VIA
- S3 Graphics ProSavage PM 133 (gráfcos integrados)
- Monitor CTR 14" HP (la resolución/refresco optima: 800*600 @60 Hercios)
- BIOS Award IO.07.06

Sí, es un equipo viejo :P, sin embargo ya lo he probado con Mandriva (ver. 2007) y no tuve ningún impedimento (y eso que dicen que Mandriva es más robusto, etc.)

Espero que me puedan ayudar, pues es una lástima que tenga una copia de Ubuntu y no la pueda usar más allá de la pantalla de inicio :(.
Probaste iniciando desde el CD en modo VGA (opcion que podes elegir presionando una de las teclas de funcion cuando te aparece el menu con las opciones de Inicio en modo Live, Instalar, etc.) ?

Creo que era F6 ... :)

---

### Post by Axel-Maze on 2009-06-27
> **guillermolisi said:**
> Probaste iniciando desde el CD en modo VGA (opcion que podes elegir presionando una de las teclas de funcion cuando te aparece el menu con las opciones de Inicio en modo Live, Instalar, etc.) ?

Creo que era F6 ... :)

Este es un detalle muy extraño, pues este problema lo vengo arrastrando desde la versión 6.06 y, efectivamente, usaba la opción para iniciar en VGA con F6 pero eso solo me cambiaba la resolución en la pantalla de la barra de progreso y al terminar mi monitor nuevamente se apagaba.

También he notado que esta opción ya no esta disponible en la pantalla de inicio (o no la encuentro) en la versión 9.04. Voy a probar de nuevo y luego posteo que sucedió.

Gracias por tu respuesta ):P

---

### Post by Axel-Maze on 2009-07-03
Soy yo de nuevo. Efectivamente la opción de iniciar en modo VGA ya no esta disponible en la versión 9.04, ahora la config. de las teclas esta así:

F1=Ayuda, F2=Idioma, F3=Teclado, F4=Modos (normal; Disco de actualización de controladores), F5=Accesibilidad, **F6=Otras opciones (acpi=off; noapic; nolapic; Solo software libre)**.

Como ven ya no esta la opción de iniciar en VGA y aún así como explique en mi post anterior, esto no me solucionaba el problema :(

¿Alguien tiene alguna idea? :confused:

---

### Post by guillermolisi on 2009-07-03
Como para ver si enteindo correctamente el sintoma, cuando decis "el monitor se apaga" significa que desconecta su conexion de video y queda el led de encendido como si estuviera sin señal, titilando o con un color diferente al de encendido y en operacion normal ?

Si es asi, se me ocurre que se "apaga" por que la placa de video, como consecuencia de lo que el X server le envia, quiere trabajar a frecuencias vertical y horizontal fuera de rango para el monitor. Entonces, para protegerse y no quemarse, se desconecta de la placa de video y queda sin señal.

Tenes la posibilidad de probar con otro monitor, algo mas moderno si fuera posible ?

---

### Post by Axel-Maze on 2009-07-03
> **guillermolisi said:**
> Como para ver si enteindo correctamente el sintoma, cuando decis "el monitor se apaga" significa que desconecta su conexion de video y queda el led de encendido como si estuviera sin señal, titilando o con un color diferente al de encendido y en operacion normal ?

Sí, exactamente eso sucede. Gracias por tu explicación ):P

>  Tenes la posibilidad de probar con otro monitor, algo mas moderno si fuera posible ?Pues sí, posiblemente en algún cibercafé podría intentarlo. Pero si en el otro equipo si funciona ¿eso quiere decir que mi PC ya esta muy "pasada" para Ubuntu o qué? :confused:

---

