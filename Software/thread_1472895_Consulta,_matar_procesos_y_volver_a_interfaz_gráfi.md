---
title: "Consulta, matar procesos y volver a interfaz gráfica"
date: 2010-05-04
forum: Software
---

### Post by mano negra on 2010-05-04
Buenas,
  Les escribo por algo sencillo. Resulta que la máquina colgó (tengo el karmic instalado), asi que para seguir fui a modo consola y matar el proceso que originaba el problema: el inkscape. Como no estaba muy seguro, reinicié la máquina con reboot. Mi consulta es:
1. Para matar el proceso, ¿sigo los siguientes pasos?:
   * ps axu para ver los procesos que se está llevando a cabo.
   * kill -9 inkscape para matar el proceso del programa.
2. ¿Cómo hago para volver a tener la interfaz gráfica sin necesidad de reiniciar?

Salud!

---

### Post by quixote on 2010-05-05
I don't speak much Spanish, so this is mainly to bump this back into current questions for you.  

Just a couple of notes based on what I understand of your questions:  I'm not sure if it makes any difference, but I usually use "ps -e" to list processes.  Type "man ps" (without quotes) in a terminal for lots of info on the "ps" command.  "kill -9" followed by PID or package name should kill it.

Your last question implies you lose the GUI unless you reboot, is that right?  If inkscape takes all of X down with it, you can type "startx" at the command line to restart the GUI.  If it's the gnome desktop that goes down, there are ways to restart that too, but I think you're better off rebooting in that case because the system could become unstable.

---

### Post by clasificado on 2010-05-05
hay un método mas directo para matar procesos: el comando killall, que mata por nombre

por ejemplo, "killall inkscape" te deshace el inkscape de un plumazo. tambien se pueden usar asteriscos, por ejemplo "killall firefox*" deshace el firefox y el firefox-bin de un plumazo

Lo que no entendí es porqué decís lo de la interfaz gráfica: Si se cuelga el inkscape, matas el inkscape, no tendrias que perder nada mas que lo que estas haciendo en el inkscape. 

Si tenés problemas en todo el entorno gnome (o kde), ahi ya es bien diferente y la cosa pasa bien por otro lado.

para reiniciar el entorno gráfico podés hacerle un restart al desktop manager desde la consola

"sudo /etc/init.d/gdm restart" para gnome.
"sudo /etc/init.d/kdm restart" para kde.

clasificado

---

### Post by alfplayer on 2010-05-06
Lo que recomiendo es, si la aplicación sigue teniendo una ventana visible, ejecutar el comando "xkill", y después cliquear en la ventana que se quiere cerrar.

Y para ver el proceso que causa el problema se puede usar el Monitor de Sistema que se puede acceder desde el menú Sistema --> Adminsitración, ordenando por la columna *% CPU*.

---

### Post by juancarlospaco on 2010-05-07
**xkill**

---

### Post by jandry on 2010-05-07
Podrias explicar porque se cierra la interfaz grafica al matar el proceso? No deberia hacerlo, podes dar mas datos?
Abrazo ubuntero

---

