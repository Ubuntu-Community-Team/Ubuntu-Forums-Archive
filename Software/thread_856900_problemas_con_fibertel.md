---
title: "problemas con fibertel?"
date: 2008-07-11
forum: Software
---

### Post by eldragon on 2008-07-11
buenas, se que no es un tema relacionado al SO, pero queria saber si habia alguno de uds que estuvo teniendo problemas de coneccion con fibertel?

mi problema es que durante el dia, cada 15 minutos, aunque el modem funciona como la gente, el router funciona como la gente, (LAN), se pierde coneccion, no con ips ya conectados (ejemplo, msn), sino, que el intentar acceder a cualquier web / DNS, la coneccion hace time out. esperas 5 minutos y arranca de nuevo.... 


alguno tuvo una experiencia similar? como lo soluciono.

---

### Post by InsektO on 2008-07-12
No sé, a mí particularmente lo que me sucede se lo atribuyo a los pésimos servidores DNS de FiberTel. Por momentos no resuelven algunas cosas como [www.google.com.ar](www.google.com.ar) o páginas muy comunes. Creo que vienen teniendo problemas con eso últimamente. En mi pc tengo un servidor de TeamSpeak y el otro día cayó del servidor todo el mundo salvo la gente que tenía FiberTel :S.

Por cierto, el otro día se descubrió una vulnerabilidad en los servidores DNS o algo por el estilo (y también se bajó tanto en Debian como en Ubuntu una actualización de algo de DNS). Casualmente Speedy también tuvo problemas por esos días con sus servidores DNS, así que yo estimo que tal vez en algo está relacionado...

Como alternativa, siempre se pueden usar los de [www.opendns.com](www.opendns.com).

Saludos

---

### Post by eldragon on 2008-07-12
gracias por el dato, precisamente por ese motivo les mande un mail ***********. por los servidores dns que no funcionan como la gente.

me huele a mi a que no dan a basto, por eso de noche todo anda pipi cucu. mientras que de dia, responden a la mitad de los pedidos...

voy a probar con los de opendns.

gracias de nuevo por el dato

---

### Post by eldragon on 2008-07-13
justo aparecio un articulo en slashdot donde mucha gente opina que los routers ******** que tenemos en casa luego de algunos dias tienen problemas con DNS, soluciones propuestas incluyen instalar un DNS server en una pc en casa. algo que voy a hacer si los servidores de opendns no funcionan. (despues de todo, tengo mi server encendido 24/7).

---

### Post by sergiom99 on 2008-07-13
o proba de cambiarle el firmware al router por uno mejor :-P
Yo tengo un Linksys WRT54g y le puse el firmware open-source de dd-wrt.com y anda perfecto, jamas tuve problemas con DNS y tengo fiber.

Si el problemas es de ellos ya es otro tema...

---

### Post by marianom on 2008-07-13
¿La resignación es una solución? :D

---

### Post by eldragon on 2008-07-13
mi router es v6 y no se banca el dd-wrt, no se puede instalar. es mas, tengo 2 routers linksys v6, asi que si ladrillo uno de ellos no me preocupo...pero dice explicitamente que no funciona. tengo que conseguir un router viejo, y la verdad no me siento con ganas de tratar de encontrarlo.

si cae a mis manos, bien, sino tambien.


EDIT
parezco un jodido posteando como loco, pero un estudio un poco mas desesperado (opendns no soluciono del todo) hizo que encuente como flashear el firmware y bueno, ahor estoy con un router con linux, muchas opciones para tocar, en cuanto tenga mas tiempo voy a mirarlo mas detenidamente, pero ya tengo para rato con esto.

gracias por responder a todos

---

### Post by sergiom99 on 2008-07-13
si no entiendo mal, el v6 en la lista dice que esta soportado. Yo tengo un v8.
[http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Linksys_.28all_the_rest_that_is_not_re-engineered_til_today.29](http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Linksys_.28all_the_rest_that_is_not_re-engineered_til_today.29)

---

### Post by eldragon on 2008-07-13
> **sergiom99 said:**
> si no entiendo mal, el v6 en la lista dice que esta soportado. Yo tengo un v8.
[http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Linksys_.28all_the_rest_that_is_not_re-engineered_til_today.29](http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Linksys_.28all_the_rest_that_is_not_re-engineered_til_today.29)

si, ya reemplaze el firmware, y ahora estoy buscando esquematicos para ampliarle la memoria flash con una sdram que tengo dando vueltas por aca....

---

### Post by eldragon on 2008-07-13
recien cayo mi cuñado con un linksys v8 que se le cuelga dia por medio, se acaba de ir con un v8 con dd-wrt....

---

