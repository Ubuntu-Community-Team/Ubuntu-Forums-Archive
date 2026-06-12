---
title: "Cambiar gnome por kde 4.3 / habilitar GDM"
date: 2009-10-07
forum: Software
---

### Post by sitiomatic on 2009-10-07
Hoy estaba aburrido y se me ocurrio bajar le beta de kubuntu 9.10 y me encanto kde...estuve jugando un rato y como chico que vio juguete nuevo, lo quiero YA!! (ojo, tengo 50 pirulos) :)
Ya tengo un tutorial para instalar kde 4.3 o desinstalarlo si va mal.
El tema es que en otras distros que he usado, al iniciar tenia la ventana de login y ahi podia elegir el entorno que queria usar y ahora no lo tengo. Al iniciar el sistema no hay login.
Como habilito eso? <--------- ya encontre solucion
Lei por ahi que es mejor usar aptitude (y no apt) para instalar y aptitude --purge para desinstalar. Es correcto?
Alguna recomendacion importante a tener en cuenta?

---

### Post by emiliano_raso on 2009-10-09
Seguramente se te desinstaló.
Iniciá sesión como te aparece en modo consola y despues:

```
sudo aptitude install gdm
``` Para instalar el de Gnome
```
sudo aptitude install kdm
``` Para instalar el de KDE

---

### Post by guillermolisi on 2009-10-09
ANtes de desinstalar e instalar o viceversa, verifica que aun tengas gdm en tu maquina.

Inicias la sesion de KDE, vas a una consola con Ctrl-Alt-F1, por ejemplo, login e ingresa
```
sudo /etc/init.d/kdm stop
```
Luego, en la misma sesion de consola, ingresa
```
sudo /etc/init.d/gdm start
```
Si te dice que ya esa corriendo (cosa que dudo), podes probar con
```
sudo /etc/init.d/gdm restart
```

Si te dice que no encuentra/puede iniciar gdm entonces se ha desinstalado efectivamente.

Contanos como te fue con esto

---

