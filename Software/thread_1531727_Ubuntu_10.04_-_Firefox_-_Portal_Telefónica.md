---
title: "Ubuntu 10.04 - Firefox - Portal Telefónica"
date: 2010-07-15
forum: Software
---

### Post by ppellet on 2010-07-15
Estimados Ubunteros

Tengo el siguiente problema: trabajo en una obra, donde para acceder  a internet usamos wifi vía Telefónica.

Cuando intento acceder a un link de una página cualquiera, ciertas veces no aparece la página a la que quiero ir sino que aparece el portal de Telefónica. Si intento otra forma, por ejemplo, buscando con google y desde ahí trato de acceder a la página que quiero, lo mismo.

Esta situación me tiene aburrido, ya que no he podido acceder a algunas páginas que requiero para realizar mi trabajo. Cuando llego a mi casa y me conecto por otra empresa a la página deseada no tengo el mismo problema.

¿Conocen alguna forma de bloquear el famoso portal?

Uso Ubuntu 10.04, Firefox.

Un saludo a todos y gracias por su ayuda.
:D

---

### Post by Patriciologico on 2010-07-17
Específicamente a que portal te refieres? ¿el de configuración del router o la pagina web de telefonica?

Te lo pregunto por que si es la web, a mi me paso hace un año y si mal no recuerdo lo arregle cambiando los dns por opendns.

---

### Post by ppellet on 2010-07-19
> **Patriciologico said:**
> Específicamente a que portal te refieres? ¿el de configuración del router o la pagina web de telefonica?

Te lo pregunto por que si es la web, a mi me paso hace un año y si mal no recuerdo lo arregle cambiando los dns por opendns.

Este es el portal que aparece cuando intento ingresar: [http://www.telefonicachile.cl/](http://www.telefonicachile.cl/) Por ejemplo, coloco [www.itau.cl]("http://www.itau.cl") y me envía al link anterior. Sin embargo, un colega sentado al lado mío pudo entrar a la página sin problema,  mientras que yo no (?).

No sé cambiar los DNS, en realidad, yo accedo como un funcionario más con mi laptop con wifi.


Saludos cordiales,

---

### Post by Carlos C on 2010-07-19
Para cambiar el DNS debes ir al icono de redes en el panel superior y acceder al menú contextual mediante el botón derecho de tu mouse. Luego escoge la opción "Editar las conexiones". Selecciona la pestaña "Inalámbrica". Editas la conexión de red que usas y seleccionas la pestaña "Ajustes de IPv4". Cambia el Método automático a "Sólo direcciones automáticas (DHCP)". En "Servidores DNS" anota los dns de opendns: 208.67.222.222, 208.67.220.220. Aplicas los cambios y reinicias el sistema. Puedes verificar que estás usando opendns si entras a [http://welcome.opendns.com](http://welcome.opendns.com)

---

### Post by ppellet on 2010-07-20
Carlos C

Acabo de realizar los pasos que me indicas y lo comprobé en la página que mencionas. Esta todo ok hasta el momento.

Ahora he intentado ingresar a la misma página que dió origen a este post (la del banco Itaú) y nada, de nuevo me muestra la famosa página de telefónica.

Sin embargo, para poder ingresar a mi cuenta (que es lo que me interesaba en un principio), he realizado un truco: le agregué información adicional, o sea, pasé de esto: [https://www.itau.cl/](https://www.itau.cl/)  a esto: [https://www.itau.cl/personas/process.asp](https://www.itau.cl/personas/process.asp)  y me funcionó.[I] [edito] probé nuevamente y ahora sí pude ingresar directamente, sin usar "trucos". Pero, todavía me queda ver si funciona con otras páginas cuando estoy trabajando. Lo informaré aquí mismo.
[/I]
De todas formas, no es la idea. No se trata de hacer "trucos" para ingresar a las páginas que uno quiere, se trata de ingresar libremente, sin que te pongan propaganda a cada rato y que más encima esa propaganda te bloqueé.

Sólo me restan un par de consultas, respecto de los DNS:
- ¿los puedo usar en cualquier otro caso, por ejemplo, en mi casa tengo conexión mediante VTR o cuando estoy en otros lugares (voy seguido a terreno con mi laptop)?
- ¿usando el mismo procedimiento?

Saludos desde Concepción terremoteado.

---

### Post by themasterdark on 2010-07-20
Si se puede realizar en todos los casos.

Saludos =)

---

### Post by Patriciologico on 2010-07-21
Cuando en una versión (hace tiempo) Firefox elimino la opción por defecto de cerrar pestañas con el botón central del mouse, lo que hacia era enviarte a una pagina guardada en cache (no estoy seguro si era a la ultima visitada, la mas frecuente o que) eso se cambiaba en about:config. A que voy con esto? que si los problemas no estan en los dns puede ser alguna extensión que lo este provocando o algún archivo que maneje cockies que no ande bien.

Para descartar eso podrías probar eliminando cockies y cache, iniciar firefox en modo aprueba de fallos o en modo privado (pruebalas todas) también puedes probar con otro navegador (esto para confirmar si son los dns)

```
firefox -safe-mode
```

---

### Post by ppellet on 2010-07-22
Patriciologico

Gracias por los datos. En cuanto tenga novedades les cuento, ya que mientras trabajo va ocurriendo este problema. De hecho, ya me volvió a ocurrir con las mismas páginas (busco la del banco y me aparece la de telefónica), sin embargo, la busqué por google y desde ahí la pude abrir.

Antes de seguir, debo aclarar que cargué desde cero el ubuntu 10.04 y agregué las aplicaciones que me interesaban. Es decir, no le he metido mano al sistema, cargando, borrando, etc. diferentes aplicaciones para probar (eso lo hacia antes para conocer).

Tengo el Konqueror para probar. Veremos que pasa. Trabajaré con él durante un par de días y postearé los resultados aquí mismo.

Un saludo a todos los ubunteros,

---

### Post by Carlos C on 2010-07-24
Yo también apostaría por lo que dice patriciologico: eliminar cookies y cache. Y también entiendo que, como dice themasterdark, se puede usar en todos los casos.

Saludos.

---

### Post by ppellet on 2010-08-26
Estimados:

Estuve probando con el **Konqueror**, pero no me sirve, ya que uso google apps y para leer emails me dice que es demasiado antiaguo (?). En general anda bien, pero funciono mejor con firefox, donde además tengo una serie de complementos que uso a diario (traductores, wikipedia, etc.).

Ahora pasé a **Chromium**... veremos que pasa.
*[140910]*
He trabajado con Chromium durante estas semanas y es el de mejor funcionamiento. Han sido muy pocas las veces que apareció el famoso mensaje de telefónica y, cuando lo hizo, vuelvo a escribir la dirección web que necesito y la muestra sin problemas (a diferencia de lo que ocurre usando Firefox).

Seguiré usando Chromium mientras trabajo fuera de casa y encuentro situaciones como la descrita.

Doy por terminado este asunto y agradezco a quienes me ayudaron.


Saludos,

---

