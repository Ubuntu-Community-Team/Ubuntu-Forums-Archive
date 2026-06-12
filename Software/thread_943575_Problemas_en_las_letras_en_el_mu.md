---
title: "Problemas en las letras en el mu"
date: 2008-10-10
forum: Software
---

### Post by xXEddXx on 2008-10-10
hola a todos, bueno, yo ya vengo usando linux desde hace un tiempo y todo, pero tengo un problema con uno de los juegos.

es el mu online, 

el tema en particular es, que se ven mal las letras, se ven muy borrosas y hasta casi no se distinge que se dice, 

si hasta probe poniendo una C y una G (vean la imagen) juntas y nada, no se entiende -.-

[[IMG]http://img516.imageshack.us/img516/5624/letrasfj1.th.png[/IMG]](http://img516.imageshack.us/my.php?image=letrasfj1.png)

espero que si alguien sabe alguna solucion me la pueda dar, ya que es el unico juego que me hace estoy y es mi juego preferido.

gracias por todo.l

---

### Post by User21 on 2008-10-10
Aunque este no es el lugar para dar soporte a UN JUEGO que nada tiene que ver con Ubuntu, supongo que como lo corres con Wine, todavía puedo tirarte un hueso :P 
Es un problema de fuentes, aparentemente: El MU requiere CIERTA FUENTE que no tenés instalada! Debe estar usando alguna otra que no es la correcta y da problemas de visualización. Que podes probar? Instalar algunas fuentes que tengan similares características:
```
sudo apt-get install ttf-liberation
```
o instalar las mismas fuentes que usa otro conocido sistema operativo.
```
sudo apt-get install msttcorefonts
``` lo cual requiere que tengas activos los repositorios de **Software  restringido por copyright  o cuestiones legales (multiverse). **

Si con esto no se soluciona, yo trataría de probar con la resolución elegida para ejecutar el juego. Solo una idea....

---

### Post by xXEddXx on 2008-10-10
oks, muchas gracias, y si, uso wine, por eso posteo aca. ya que en la ***** del sistema me anda bien,

voy a probar, y disculpenme que no sea el lugar indicado, sino es el indicado, por favor diganme bien, o si un mod me lo muebe o directamente me lo borra, no me enojaria.

gracias

edito, no, no se soluciono, y estoy usando la resolucion que pide el juego, hasta la subi a 1028 x 7xx (no me acuerdo ahora xD) y nadap.

voy a seguir, por que en algun lado tiene que aver algo -.-

gracias igual.

---

### Post by User21 on 2008-10-10
Deberías probar si hay algún cambio en la **RESOLUCIÓN DE PANTALLA**, en la configuración de Wine, dentro de la pestaña Gráficos. Proba con 96 DPI y después andá aumentándolas paulatinamente a ver que sucede. La config de Wine debería aparecer en tu menu de Wine, o desde consola: **winecfg** .

---

