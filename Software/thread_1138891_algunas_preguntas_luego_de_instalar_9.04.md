---
title: "algunas preguntas luego de instalar 9.04"
date: 2009-04-26
forum: Software
---

### Post by joseluis on 2009-04-26
Hola..la instalación de ubuntu 9.04 fue de maravillas y el sistema anda mejor que nunca.
Me quedaron algunos problemas que espero me puedan ayudar a resolver.
1- no anda opción de Alt-Ctrl-Retroceso para reiniciar las x. ¿alguien sabe cómo se arregla?

2- al instalar me daba la opción de que luego de ser instalado puediera entrar al sistema sin necesidad de logearse, es decir, entrar directamente. No habilité esa opción y ahora quisiera habilitarla. Es decir, no tener necesidad de poner mi nombre de usuario y contraseña porque el unico que usa la maquina soy yo y no habrá otro usuario.

Espero puedan ayudarme.
gracias

---

### Post by pablo.s on 2009-04-26
> **joseluis said:**
> 1- no anda opción de Alt-Ctrl-Retroceso para reiniciar las x. ¿alguien sabe cómo se arregla?

Hay que descomentar en xorg.conf 
una linea.

> **joseluis said:**
> 2- al instalar me daba la opción de que luego de ser instalado puediera entrar al sistema sin necesidad de logearse, es decir, entrar directamente. No habilité esa opción y ahora quisiera habilitarla. 

Eso se soluciona yendo al menú
Sistema - Administración - Ventana
de Entrada (si no aparece asi es similar)
en la solapa Seguridad y tildar "Habilitar
ingreso automatico" eligiendo a la vez
tu usuario.

---

### Post by joseluis on 2009-04-26
bien...lo de acceder automáticamente lo arreglé..GRACIAS
que linea hay que descomentar para el Atl-Crtl-Retroceso? 
¿como accedo al xorg?

gracias de nuevo

---

### Post by dox_drum on 2009-04-26
> **joseluis said:**
> bien...lo de acceder automáticamente lo arreglé..GRACIAS
que linea hay que descomentar para el Atl-Crtl-Retroceso? 
¿como accedo al xorg?

gracias de nuevo

```
sudo gedit /etc/X11/xorg.conf
```

Asi se accede.

---

### Post by lega on 2009-04-26
Ctrl+Alt+retroceso se arregla o mejor dicho se habilita, de la siguiente manera
Instalas dontzap

```
sudo aptitude install dontzap -y
```

y luego habilitas la conbinación de teclas

```
sudo dontzap  --disable
```

Saludos

---

### Post by pablo.s on 2009-04-26
[COLOR=Green][B]sudo aptitude install dontzap -y

[/B][COLOR=Black]y luego[/COLOR][B]

sudo dontzap -d[/B][/COLOR]

---

### Post by joseluis on 2009-04-26
MUCHAS GRACIAS AMIGOS!!!!!!!!!!!!!

ahora. ¿por qué deshabilitaron esa función? dicen que era por seguridad, que se evitaba así que uno lo haga por error? es cierto eso?

---

