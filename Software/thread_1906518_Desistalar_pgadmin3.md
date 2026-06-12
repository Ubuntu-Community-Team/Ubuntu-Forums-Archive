---
title: "Desistalar pgadmin3"
date: 2012-01-09
forum: Software
---

### Post by akiestudio on 2012-01-09
Hola no consigo desistalar pgadmin3, con terminal hago un 
apt-get remove pgadmin3....y parece que desistala, pero cuando hago pgadmin arranca de nuevo y si pongo apt-get remove pgadmin3 ,me dice que no esta instalado , como puedo quitarlo del todo.
Un saludo

---

### Post by euzkoarima on 2012-01-09
Raro, no ?
Lo instalaste de los repositorios ? (y no de un paquete bajado de otro lado)

Si lo instalastes de los respositorios, yo probaría con 
```
sudo apt-get purge pgadmin3
```
Pero si ya te lo marca como no instalado, lo lógico sería que de error. En cuyo caso, volvería a instalar para poder hacer luego el purge.

Saludos,
Eduardo

---

