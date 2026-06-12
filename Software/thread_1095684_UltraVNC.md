---
title: "UltraVNC"
date: 2009-03-14
forum: Software
---

### Post by erdosain9 on 2009-03-14
existe algún programa similar para Ubuntu??? es posible hacer este tipo de "intrusión" entre ubuntu y windows... es decir... servicio técnico entre ubuntu y windows???
O sea tengo ubuntu... vos windows... entro por algún programa como este (o alguna página) y arreglo la carcaza???
Existe??
Muchas gracias

---

### Post by Hei Ku on 2009-03-14
y si, tenes vnc, tenes freeNX, etc. Depende que tengas en las 2 PCs. Pero si vas a usar vnc, no hay problema.
El vnc se creo para Unix originalmente. A windows llego despues.

---

### Post by sergiom99 on 2009-03-14
yo uso el paquete xvnc4viewer para casi todas las conexiones, pero no sirve en los casos en que tenes un servidor VNC que usa para autenticarse los usuarios de windows. (ie: w2k, w2k2, w2k3 Servers) asi que para esos casos uso el Uvncviewer.exe con wine y problema solucionado.
suerte! Sergio

---

### Post by erdosain9 on 2009-03-14
Muchas gracias a ambos.  Podrían explicarme paso a paso cómo se instala alguno de esos programas y cómo hago para entrar a determinada máquina?? soy nuevo en linux...

Un saludo

---

### Post by Hei Ku on 2009-03-14
Depende de cuál instales.
El xvnc4viewer lo instalas por Synaptic y lo usas igual que el vnc para windows, o el ultravnc.

El UltraVNC, tenes que instalar primero wine, y despues en wine lo instalas igual que en Windows.

---

### Post by erdosain9 on 2009-03-14
No me gusta usar wine... de hecho ya no lo tengo instalado.  Así que prefiero xvnc4viewer si es la otra opción.  Bueno, lo instalo por synaptic... yo quiero tener acceso a una máquina que tiene windows... qué hago?

Saludos

---

### Post by erdosain9 on 2009-03-14
Veo que hace falta instalar un "servidor VNC" cómo se hace esto en un windows??? qué hay que bajar??
gracias

---

### Post by josecuervo86 on 2009-03-14
Podes Googlear primero[0] y si te trabas en algo haces la consulta específica 

[0][www.google.com.ar]("http://www.google.com.ar") ;)

---

### Post by erdosain9 on 2009-03-14
jejejejej.. bueno, está bien...... disculpen la forma chat.

---

### Post by erdosain9 on 2009-03-14
Ahora sí!! ayuda por favor!!! Bueno, resulta que ya instalé en un windows el realvnc y lo puse en server... y está encendido, etc.  Pues bueno, ahí si pongo el mouse sobre el ícono inferior me tira dos números ¿?¿?¿? cuál de ellos es¿¿¿ los dos tienen pinta ip...

Desde la de ubuntu escribo en consola "xvnc4viewer" le doy enter... me pide un server... escribo un número.  Primero probé con el primer número y me dice "unable to connect to host: no route to host (113)"
Qué pasa???

Si pongo el otro número se queda tildado??? qué onda??? luego de un tiempo me dice: unable to connect to hos: connection timed out(110)

SAludos y gracias

---

### Post by erdosain9 on 2009-03-14
HOla! ya lo logré! resulta que había que configurar el firewall... como no estaba en la casa simplemente pedí que lo desactivaran... y entré con el segundo número... no sé que será el primero.
Un saludo 

p.D.: por cierto... para entrar a un windows vista es igual no???

---

### Post by Mauro22 on 2009-03-14
Si mal no recuerdo el VNC en Windows te tira las dos IP, la interna en el rango 192.xxx.xxx.xxx y la externa.


Dependiendo si queres ingresar desde intranet o internet vas a tenes que usar una o la otra.

---

