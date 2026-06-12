---
title: "Virus de linux (impresora)"
date: 2009-08-05
forum: Software
---

### Post by armagedonc on 2009-08-05
Hola, tengo un problema con la impresora, es una stylus color 440 muy vieja, funcionaba bien hasta que empezaron a llegar trabajos de impresion cada 20 minutos. 

Ya probe borrar los trabajos desde localhost:631
tambien lprm - y lpmr nombre_de_usuario

al usar lp :lp /etc/profile
request id is Stylus-COLOR-440-26 (1 file(s))

y con lp -p: lpstat -p
printer ML-1640-Series disabled since Wed 22 Jul 2009 12:28:06 CLT -
	Unplugged or turned off
printer Stylus-COLOR-440 is idle.  enabled since Wed 05 Aug 2009 02:12:39 CLT
	Printing page 1, 33%


probe reinstalando el paquete donde viene lp pero nada, al borrar los trabajos de impresion de cualquier forma al segundo aparece uno nuevo con el mismo titulo **Printing page 1, 33%**.

ALgunas veces el comando lp: printer ML-1640-Series disabled since Wed 22 Jul 2009 12:28:06 CLT -
	Unplugged or turned off
printer Stylus-COLOR-440 is idle.  enabled since Wed 05 Aug 2009 01:49:00 CLT
 
idle pero al encenderla aparecen trabajos de impresion. 
Va en el trabajo 26, pero se acumulan y sigue subiendo si no los borro .


Supongo que es un virus. 

Saludos

---

### Post by Carlos C on 2009-08-05
Difícil que sea un virus. Hay pocos virus en linux y no tienen las mismas características que en windows. Antes que salten otros poniendo el grito en el cielo te recomiendo que leas la información que sale acá:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

