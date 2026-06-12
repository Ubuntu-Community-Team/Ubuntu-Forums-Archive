---
title: "Problema con el Mouse... con el cursos específicamente"
date: 2010-10-26
forum: Software
---

### Post by baila0 on 2010-10-26
Hola a todos, tengo un problema, me ocurre en 10.04 LTS y en 10.10

El cursos de mi ratón se queda pegado a ratos, es un "pegado" de 1 segundo, sin embargo es muy desagradable. Me ocurre tanto usando el trackpad como un mouse.

Ojala me puedan ayudar.
Gracias

---

### Post by bichopro on 2010-10-26
sobre el panel superior en un lugar vacio, dale click derecho "añadir al panel" agrega el monitor de sistema, verza que te muestra graficamente el uso del cpu. Si cuando se te pega el mouse coincide con un pico de uso en la cpu es por que el problema es execivo uso del procesador. Espero te sirva para diagnosticar

---

### Post by baila0 on 2010-10-27
Tenias toda la razon Bichopro

El CPU se manda unos "mini" peaks (especificamente el CPU1), que llegan a 20% aproximadamente, que coinciden jusamente con el momento en que se pega el cursor.

Por lo que vi, va en ciclos de aproximadamente 10 segundos... (Me pasó con la versión de 32 y 64 bits.

Igual encuentro que 20% no deberia provocar algo así

Ahora como puedo proceder??
Gracias

---

### Post by Carlos C on 2010-10-27
Trata de identificar el proceso que está consumiendo tu cpu. Entra a la pestaña "Procesos" y ordena por %CPU.

Saludos.

---

### Post by baila0 on 2010-10-27
> **Carlos C said:**
> Trata de identificar el proceso que está consumiendo tu cpu. Entra a la pestaña "Procesos" y ordena por %CPU.

Saludos.

El único proceso que me aparece que está consumiendo "algo" es el gnome-system-monitor, todos los demás salen en 0... sin embargo no tiene nada que ver con los ciclos en los cuales se pega el cursor

Saludos

---

### Post by moreback on 2010-10-28
Revisa los logs del sistema con **Sistema -> Administración -> Visor de archivos de sucesos** y busca errores de tu mouse USB, puede ser que esté pronto a morirse :S

Saludos.

PD: el mío presenta los síntomas que describes y en los logs aparecen como desconexiones y conexiones del mouse.

---

### Post by baila0 on 2010-10-28
> **moreback said:**
> Revisa los logs del sistema con **Sistema -> Administración -> Visor de archivos de sucesos** y busca errores de tu mouse USB, puede ser que esté pronto a morirse :S

Saludos.

PD: el mío presenta los síntomas que describes y en los logs aparecen como desconexiones y conexiones del mouse.

Gracias, sin embargo, me ocurre también al usar el Trackpad, no sólamente con el mouse.

---

### Post by moreback on 2010-10-30
> **baila0 said:**
> Gracias, sin embargo, me ocurre también al usar el Trackpad, no sólamente con el mouse.

¿Había o no algún mensaje de error en tus logs?

---

