---
title: "VirtualBox...va super lento..!!"
date: 2009-05-31
forum: Software
---

### Post by prostata on 2009-05-31
Gracias a vuestros aportes, al fin ya ando con virtualbox, bufff, la de reseteos que me ahorro, la cuestión de hoy es la siguiente:

En la configuración general de virtual marca por defecto los siguiente parámetros:
Memoria base= 681 MB (1)
Memoria video 73 Mb (2)

Soy gran aficionado a la fotografia digital y para hacer HDR's uso un programa que me gusta más que QTPFsgui, me da muchas más opciones y de ahí que cambie a virtual, para realizar dicho proceso, pero no solo con ese programa la máquina va lenta, sino con el mismo openoffice, por ejemplo, en fin si me podéis dar alguna solución para hacer correr más la máquina os lo agradeceré...
He mirado dentro del XP la configuración de la memoria SAWP y no me permite cambiar los valores..

Saludos

(1) yo dispongo de 2 Gb
(2) aquí dispongo de 256 Mb

---

### Post by pablo.s on 2009-05-31
Bueno, hasta cierto punto
se puede elevar la memoria
de VirtualBox, pero no hay
que olvidar que el sistema
anfitrión también necesita
de recursos. Por ejemplo
con 2 GB de memoria RAM
lo máximo que te recomendaría
es 1 GB para VirtualBox y
1 GB para Ubuntu.
¿Cómo se llama el programa
que utilizas para HDR?

---

### Post by prostata on 2009-06-01
> **pablo.s said:**
> Bueno, hasta cierto punto
se puede elevar la memoria
de VirtualBox, pero no hay
que olvidar que el sistema
anfitrión también necesita
de recursos. Por ejemplo
con 2 GB de memoria RAM
lo máximo que te recomendaría
es 1 GB para VirtualBox y
1 GB para Ubuntu.
¿Cómo se llama el programa
que utilizas para HDR?


Gracias por consejo, uso dos programas indistintamente Photomatix y Dynamicphoto HDR, aunque más este último, me permite hacer más cosas, y las hago directamente del .RAW  ¿los conocías??

Saludos

---

### Post by pablo.s on 2009-06-01
> **prostata said:**
> ¿los conocías??
Saludos

No los conocía... Interesante
tu aporte. Gracias.

---

### Post by Hei Ku on 2009-06-01
Probaste con Krita. Según recuerdo, tenía posibilidad de editar archivos RAW.

---

### Post by pablo.s on 2009-06-01
El método HDR en fotografía
consiste en combinar tres
tomas de una misma escena
para ecualizar las zonas altas,
medias y bajas. Es un tratamiento
digital que hace parecer a la
toma como si fuera perfecta
(en términos de contraste) pero
al ojo de un fotógrafo pasa
como muy artificial. Si bien
se suele utilizar formatos de
tipo RAW o DNG, no es sólo
eso. Krita es muy buen programa,
pero me temo que todavía no
está implementado de forma
nativa. Tampoco en GIMP.

---

### Post by prostata on 2009-06-01
> **pablo.s said:**
> El método HDR en fotografía
consiste en combinar tres
tomas de una misma escena
para ecualizar las zonas altas,
medias y bajas. Es un tratamiento
digital que hace parecer a la
toma como si fuera perfecta
(en términos de contraste) pero
al ojo de un fotógrafo pasa
como muy artificial. Si bien
se suele utilizar formatos de
tipo RAW o DNG, no es sólo
eso. Krita es muy buen programa,
pero me temo que todavía no
está implementado de forma
nativa. Tampoco en GIMP.

Desconozco Krita, pero de momento para editar formatos RAW en GNU y concretamente en Ubuntu hay un par de ellos  o más muy buenos, Fspot phtoshow y alguno más, para positivar RAW uso indistintamente Rawstudio, Rawtherapee, o UfraW.

Sobre la técnica HDR, decirte como supongo sabes, que puede hacerse una HDR solo, con el Raw y a partir de ahí con los programas nombrados con anterioridad, en el otro post, parametrizas los valores que más se ajusten a tus personal gusto...por otro lado, para hacer una HDR, se necesitan mínimo tres tomas, pero ojo..cada toma debe pasar por ejemplo a modo de concepto por: una bastante sub expuesta por ejemplo EV -3, otra toma normal y otra tercera sobre expuesta osea EV *3, esas exposiciones hacen que se capte todo el rango dinamico, el más expuesto, el normal y el menos expuesto...se pueden hacer con más de tres tomas, pero entonces las EV de subexposición y sobreexposición debera&#324; seguir una progresión igual, en internet hay muchas paginas que explican esto más ampliamente. Se me olvidaba, es muy recomendable que el sujeto a fotografiar sea estático, pues al hacer los alineamientos pertinentes de todas la imagenes si hay movimiento en los sujetos el alineamiento hara aparecer fuertes halos de movimiento en el resultado final

Saludos

Edito: información interesante acerca de Krita  [http://neotux.wordpress.com/2009/05/31/krita-%C2%BFel-clon-de-gimp/](http://neotux.wordpress.com/2009/05/31/krita-%C2%BFel-clon-de-gimp/)  a lo que se ve, ya no compite con Gimp programa este último más que bueno, bonito y barato

---

### Post by mhoyos on 2009-06-01
> **prostata said:**
> 

Soy gran aficionado a la fotografia digital y para hacer HDR's uso un programa que me gusta más que QTPFsgui, me da muchas más opciones y de ahí que cambie a virtual, para realizar dicho proceso, pero no solo con ese programa la máquina va lenta, sino con el mismo openoffice, por ejemplo, en fin si me podéis dar alguna solución para hacer correr más la máquina os lo agradeceré...




hola:

yo tambien soy aficionado a la fotografia y linuxero "cuasi" avanzado.. :P

por lo que vi en otros posts, decis que usas o trabajas en imagenes en RAW.. por lo que te recomiendo (para probar en linux):

- ufraw
- rawstudio
- dcraw
- plugins para gimp: gimp-dcraw y gimp-ufraw
- RawTherapee >> [http://www.rawtherapee.com/](http://www.rawtherapee.com/)

yo estoy cursando fotografia digital , pero solo la parte de fotografia, ya que la digital la dictan con el fotoyop.. jejeje

y la tecnica de HDR, la haces desde RAW ?? :P 


por el lado del virtualbox, te recomiendo:

- le asignes 1 gb de memoria.
- la memoria de video, la "resta" de la fisica, no la de hard del host.
- no decis si tu equipo es dual core o de 64 bits.
- buscale la manera de optimizar el rendimiento del OS alojado, para que trabaje lo mejor posible, a pesar de ser una VM..


espero te sirva..

salu2

---

### Post by pablo.s on 2009-06-01
> **mhoyos said:**
> yo estoy cursando fotografia digital , pero solo la parte de fotografia, ya que la digital la dictan con el fotoyop.. jejeje

Dale Marco, lo mismo que
aprendés en PS lo podés
aplicar en GIMP, che!

---

