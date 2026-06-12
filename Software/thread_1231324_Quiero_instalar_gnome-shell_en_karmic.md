---
title: "Quiero instalar gnome-shell en karmic"
date: 2009-08-04
forum: Software
---

### Post by guisheca on 2009-08-04
Perdonen si me he vuelto loco, pero no encuentro la forma de hacerlo en karmic. Y se supone que viene en los repositorios no?
De todas formas busque en google y no encuentro nada :confused: solo opciones para jaunty e intrepid.
Alguien me puede decir como lograrlo? instalé karmic alpha 3 en una máquina virtual sólo para probar gnome-shell :(
Saludos y gracias.

---

### Post by rubioo on 2009-08-04
Por ahí te sirve esto [http://live.gnome.org/GnomeShell]("http://live.gnome.org/GnomeShell")

 PD: si logras instalar gnome-shell pone screenshots jaj

         Saludos

---

### Post by pablo.s on 2009-08-04
> **guisheca said:**
> Alguien me puede decir como lograrlo?

Está en un desarrollo constante,
lo que ves hoy puede cambiar
mañana, asi que vas a tener que
bajar el código fuente y compilar.
Aca te adjunto un script que encontré
en este foro (en la parte en inglés, digo)
para compilar.[ATTACH]123588[/ATTACH]

---

### Post by rubioo on 2009-08-04
Te dejo otro link, por ahí te sirve :)

 [https://launchpad.net/ubuntu/karmic/+source/gnome-shell/0.0.1~git20090715-0ubuntu1]("https://launchpad.net/ubuntu/karmic/+source/gnome-shell/0.0.1~git20090715-0ubuntu1")

---

### Post by guisheca on 2009-08-04
Gracias gracias!! estoy poniendo manos a la obra a ver que sale.
(puse a correr el script que me paso pablo.s, creo que la opción mas práctica. Gracias pablo.s!)

---

### Post by pablo.s on 2009-08-04
Guarda que ahi no explica el
modo de uso. Primero corrés
el script. Si no tenés las 
dependencias te va a decir que
las bajes.
Luego lo ejecutás y arma dos
carpetas en tu /home que se
llaman /Source y /bin.
Entrás a /bin y ejecutás

```
./jhbuild build
```y luego hay que esperar a que 
baje todo lo que precisa de git
y compile.

Una vez que compila todo,
ejecutás lo siguiente:

```
cd ~/gnome-shell/source/gnome-shell/src
./gnome-shell --replace
```A mi, que no estoy acostumbrado 
a Compiz, me dió la misma sensación
que cuando miro por la ventanilla
del avión. Por eso siempre pido pasillo
al lado de la salida de emergencia.

Unas capturas simples:
[ATTACH]123598[/ATTACH]
[ATTACH]123599[/ATTACH]

---

### Post by guisheca on 2009-08-04
> **pablo.s said:**
> Guarda que ahi no explica el
modo de uso. Primero corrés
el script. Si no tenés las 
dependencias te va a decir que
las bajes.
Luego lo ejecutás y arma dos
carpetas en tu /home que se
llaman /Source y /bin.
Entrás a /bin y ejecutás

```
./jhbuild build
```y luego hay que esperar a que 
baje todo lo que precisa de git
y compile.

Una vez que compila todo,
ejecutás lo siguiente:

```
cd ~/gnome-shell/source/gnome-shell/src
./gnome-shell --replace
```A mi, que no estoy acostumbrado 
a Compiz, me dió la misma sensación
que cuando miro por la ventanilla
del avión. Por eso siempre pido pasillo
al lado de la salida de emergencia.

Unas capturas simples:
[ATTACH]123598[/ATTACH]
[ATTACH]123599[/ATTACH]

Muchas gracias pablo.s! logre instalarlo pero desafortunadamente tiene serios problemas de refresco (o renderizado, no se como sería el termino técnico, la cosa es que se ven patrones de rayas en las ventanas), supongo que debe ser porque esta desde una máquina virtual.

En fin, el objetivo era instalarlo y probarlo y se cumplió. Y mas alla de los problemas en la visual pude apreciar las innovaciones en cuanto a usabilidad, y son muy interesantes la verdad. No se si será mejor o peor, pero es distinto y eso me gusta.
Gracias a todos por la ayuda.

---

