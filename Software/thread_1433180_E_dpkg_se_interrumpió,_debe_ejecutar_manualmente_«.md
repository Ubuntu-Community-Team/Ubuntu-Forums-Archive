---
title: "E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para cor"
date: 2010-03-18
forum: Software
---

### Post by sol03 on 2010-03-18
Hola,

Soy nueva con Ubuntu 9.10 y cuando trato de instalar paquetes y/o ingrsar a Gestor e paquetes Synaptic me da este error:



E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
E: _cache->open() failed, please report.

Gracias de antemano por su apoyo,

Sol

---

### Post by lisati on 2010-03-18
> **sol03 said:**
> Hola,

Soy nueva con Ubuntu 9.10 y cuando trato de instalar paquetes y/o ingrsar a Gestor e paquetes Synaptic me da este error:



E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
E: _cache->open() failed, please report.

Gracias de antemano por su apoyo,

Sol

Arrepentido para la traducción hecha por [www.freetranslation.com](www.freetranslation.com) - yo no sé mucho español. ¿Ha tratado usted hacer lo que el mensaje de error dijo hacer? (Haciendo la misma pregunta más de una vez le conseguirá atención que usted no quizás quiera)

---

### Post by guillermolisi on 2010-03-18
En una consola/terminal ingresa ```
sudo dpkg --configure -a
```le das Enter y esperas que termine. Despues volve a instalar paquetes actualizando previamente el cache de repositorios.

Esto es, si usas apt-get en una consola/terminal ```
sudo apt-get update
```Si usas Aptitude (tambien en consola/terminal) busca la opcion de Update/Actualizar cache en el menu principal de Aptitude o ejecuta ```
sudo aptitude update
```Si usas Synaptic, presiona el boton de Recarga/Reload.

Contanos como te fue.

---

### Post by CristianGR on 2010-04-26
> **guillermolisi said:**
> En una consola/terminal ingresa ```
sudo dpkg --configure -a
```le das Enter y esperas que termine. Despues volve a instalar paquetes actualizando previamente el cache de repositorios.

Esto es, si usas apt-get en una consola/terminal ```
sudo apt-get update
```Si usas Aptitude (tambien en consola/terminal) busca la opcion de Update/Actualizar cache en el menu principal de Aptitude o ejecuta ```
sudo aptitude update
```Si usas Synaptic, presiona el boton de Recarga/Reload.

Contanos como te fue.

Hola Guillermo, 
Yo tambien soy nuevo con Ubuntu 9.10. Y tambien tengo el mismo problema que Sol. Como vos bien decis, seguí las instrucciones; en la terminal ingreso " sudo dpkp --configure -a". Se reinicia el sistema y veo el escritorio totalmente congelado, solo lo saco de ese estado reiniciando la maquina. ¿Tendré que reinstalar el SO?
¡Gracias por ayudarnos a sumarnos a la comunidad!

---

### Post by guillermolisi on 2010-04-26
> **CristianGR said:**
> Hola Guillermo, 
Yo tambien soy nuevo con Ubuntu 9.10. Y tambien tengo el mismo problema que Sol. Como vos bien decis, seguí las instrucciones; en la terminal ingreso " sudo dpkp --configure -a". Se reinicia el sistema y veo el escritorio totalmente congelado, solo lo saco de ese estado reiniciando la maquina. ¿Tendré que reinstalar el SO?
¡Gracias por ayudarnos a sumarnos a la comunidad!
Ese comportamiento no lo habia visto nunca !

Habra que investigar buscando casos similares. Si encuentro algo te aviso.

Aclaracion: es "dpk[COLOR=Red]**g**[/COLOR]"

---

### Post by CristianGR on 2010-04-28
> **guillermolisi said:**
> Ese comportamiento no lo habia visto nunca !

Habra que investigar buscando casos similares. Si encuentro algo te aviso.

Aclaracion: es "dpk[COLOR=Red]**g**[/COLOR]"

Muchas Gracias!
Realmente este problema me tiene atado de manos. No puedo instalar ningún programa nuevo, ni plugings. Intente realizarlo con Synaptic, con Instalar y Quitar aplicaciones y de manera manual. 

PD: Gracias por la aclaración. 

Saludos.

---

### Post by guillermolisi on 2010-04-28
> **lisati said:**
> Arrepentido para la traducción hecha por [www.freetranslation.com]("http://www.freetranslation.com") - yo no sé mucho español. ¿Ha tratado usted hacer lo que el mensaje de error dijo hacer? (Haciendo la misma pregunta más de una vez le conseguirá atención que usted no quizás quiera)
Hey Lisati !

Thanks for your message !

---

### Post by guillermolisi on 2010-04-28
Algo me dice que el cache local de paquetes esta tan corrupto que hace que el sistema se reinicie.
Algo que habria que probar es borrar/limpiar totalmente esa estructura para que se regenere pero antes de ello cambiar el server/mirror del cual se toman los repositorios ya que los de Argentina estan funcionando mal desde hace un tiempo a la fecha. Es recomendable usar los de Brasil.

De confirmar mi sospecha les paso como poner a cero el cache de paquetes, si alguien aun no lo ha hecho antes, para que lo puedan regenerar (bajando los paquetes nuevamente).

Esto se puede hacer con Aptitude ya que posee una opcion en su menu al efecto pero no se si han podido probar Aptitude con exito (sin que vuelva a aparecer el mensaje sugiriendo recomponer el cache local con dpkg etc., etc.)

---

### Post by DrKenobi on 2010-04-30
cuando apenas empece a usar linux, con 8.10, me paso lo mismo porque se me colgo (maquina viejita) cuando estaba instalando unos paquetes

yo me volvi loco buscado respuestas, y nada

como recien lo intslaba, lo reinstale y listo. Yo en su momento no encontre nada, ni en español ni en ingles

asi que el reinstalar es una opcion....

suerte!

---

