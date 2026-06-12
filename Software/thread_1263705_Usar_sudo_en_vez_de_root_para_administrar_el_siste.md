---
title: "Usar sudo en vez de root para administrar el sistema."
date: 2009-09-10
forum: Software
---

### Post by moreback on 2009-09-10
Editado por Carlos C: viene de [http://ubuntuforums.org/showthread.php?p=7927997#post7927997](http://ubuntuforums.org/showthread.php?p=7927997#post7927997)



> **Maciett said:**
> _[[IMG]http://img525.imageshack.us/img525/8099/pantallazobl.th.png[/IMG]]("http://img525.imageshack.us/i/pantallazobl.png/")_[IMG]http://img525.imageshack.us/i/pantallazobl.png/[/IMG]

A pesar de los colores rosados, Ud. es una dama que le gusta el peligro...



... lo digo por esa consola logueada como root que muestra :P

---

### Post by Maciett on 2009-09-10
> **moreback said:**
> A pesar de los colores rosados, Ud. es una dama que le gusta el peligro...



... lo digo por esa consola logueada como root que muestra :P

hahaha, es que no soporto que me diga que no tengo permiso para hacer cualquier cosa =x

Y sobre el peligro...no le tengo miedo, total ya me eche una distribución anterior por desconfigurarle la intefaz gráfica, pero me sirvió para limpiar el pc e instalar una nueva... y llegar a acá y conocer gente interesante...

Saludos

---

### Post by moreback on 2009-09-10
> **Maciett said:**
> hahaha, es que no soporto que me diga que no tengo permiso para hacer cualquier cosa =x

Cuando trabajas en la consola como usuario normal y haces una operación que se te niega, debes anteponer el comando **sudo** ([http://es.wikipedia.org/wiki/Sudo](http://es.wikipedia.org/wiki/Sudo)).

_Por seguridad_, yo siempre trabajo como usuario normal y si quiero modificar archivos del sistema uso este comando.

Saludos.

---

### Post by Maciett on 2009-09-10
Esta bien, Moreback te haré caso, así aprovecho de aprender que es lo que puede hacer un usuario normal.
[[IMG]http://img6.imageshack.us/img6/9799/pantallazo2a.th.png[/IMG]]("http://img6.imageshack.us/i/pantallazo2a.png/")

Agrego mi intento de conky x3!

---

### Post by AlexDDR on 2009-09-10
> hahaha, es que no soporto que me diga que no tengo permiso para hacer cualquier cosa =x

Y sobre el peligro...no le tengo miedo, total ya me eche una distribución anterior por desconfigurarle la intefaz gráfica, pero me sirvió para limpiar el pc e instalar una nueva... y llegar a acá y conocer gente interesante...

Lo que debes saber es que el peligro no viene solo  por lo que tu puedas hacer logueada como root, sino de por ejecutar programas como root permite que un atacante externo (de internet or ejemplo) o un programa (troyano)  que tu misma instales o un script que ejecutes pueda generar destrozos en todo el sistema sin siquiera que tu te enteres. Y además de internet tambien hay ataque con acceso fisico a la maquina y ufff muchas cosas mas.

en cambio logueado como usuario, si un programa bueno o malicioso quiere escribir en el sistema se te pedira que confirme ese acceso, no no se lo das solo podra acceder a tu carpeta de usuario pero no podrá compremeter el sistema completo, bueno es harto mas compejo de mi propia comprension lo de la seguridad informatica, pero solo hay que seguir los csabios consejos que se nos dan.



saludos

---

### Post by nopersona on 2009-09-10
Creo que estos 3 últimos post dan para un tema aparte :popcorn: que ya nos bifurcamos de compartir el escritorio.

---

### Post by Carlos C on 2009-09-11
> **nopersona said:**
> Creo que estos 3 últimos post dan para un tema aparte :popcorn: que ya nos bifurcamos de compartir el escritorio.

Toda la razón. Los moví a un thread aparte para que se mantenga el orden. 

Como dato sugiero ver lo que dice la Guía Ubuntu sobre el comando sudo:

[http://www.guia-ubuntu.org/index.php?title=Sudo](http://www.guia-ubuntu.org/index.php?title=Sudo)

Saludos.

---

