---
title: "Matlab"
date: 2011-03-22
forum: Software
---

### Post by zaret on 2011-03-22
Hola he utilizado ubuntu desde la versión 8.10 y actualmente me he downgradeado de la 10.10 por algunos problemas.
mi consulta es si alguien sabe que es lo que le pasa a matlab en linux que muchas veces cuando gestiona nuevas ventanas se cae el decorador de ventanas (aunque el problema es intermitente no ocurre siempre) y se pegan las nuevas ventanas generadas por matlab(uso el 2009a), teniendo como consecuencia recargar el gestor de ventanas y el decorador utilizando el Fusion-icon. ademas consultando con algunos amigos de la universidad, tienen los mismos problemas que yo con otras versiones de matlab(2009b 2010a 2010b).
Bueno pense que podria ser problema de java puesto que matlab corre en java pero no es asi puesto que he probado el open jre como el de sun, y los problemas continuan.
si tiene alguna sugerencia se agradece su ayuda puesto que google no me a arrojado nada bueno.
saludos

---

### Post by silex89 on 2011-05-10
Hola!, no sé si ya resolviste tu problema instalando la nueva versión de Ubuntu, puede que eso te haya ayudado, pero en caso de que no, lo que te sugeriría es que utilices GNU Octave. Yo lo estuve utilizando para "plotear" unas funciones que me dieron para integrar en lRn, y va de maravillas (se instala nativamente en Ubuntu desde Synaptic). Dependiendo del fin con el que uses MatLab, Octave podría ser más o menos útil....

Ahora si no te quieres desligar del MatLab te sugiero que inicies sesión sin efectos de escritorio (sin Compiz que ahora viene por defecto instalado y corriendo en Ubuntu), y deja la gestión y decoración de ventanas a GNOME (asumo que sabes cómo se hace).


Espero que sea de ayuda :)


Saludos

---

### Post by dnovai on 2011-05-18
Hola, yo soy usuario Matlab R2011a en Ubuntu 9.10 y 11.04

Te sugiero que intentes quitando todos los efectos de Ubuntu (usar sin efectos), puede ser que sea un problema de tu GPU o CPU al correr matlab estes usando muchas recursos de CPU y tu GPU no te respalda.
Cuentanos como te ha ido o si lograste reparar el error.

Saludos!

---

### Post by tommpogg on 2011-07-04
Yo también te sugiero que quites los efectos gráficos antes de iniciar Matlab.
De todas formas, la gestión de los aspectos gráficos de Matlab no es muy estable (en ninguna versión de Matlab y Ubuntu).

---

### Post by zaret on 2011-07-13
se me soluciono utilizando matlab2010b y ubuntu 10.04 y desactivando el decorador emerald. hasta el momento no he tenido problemas con las graficas.
saludo

---

