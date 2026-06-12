---
title: "Problema con repositorios"
date: 2009-03-11
forum: Software
---

### Post by josecuervo86 on 2009-03-11
Como andan? Yo medio perdido. Pasa que desde que quise ponerle un plugin a pidgin para ver lo que estoy escuchando me empezaron a andar mal los repositorios. O sea, cuando pongo el gestor de actualizaciones busca en los repositorios pero me tira que no puede acceder. 
No creo que sea problema de repositorios, y problema de conxion tampoco porque puedo entrar a internet tranquilamente. 
Alguien me tira un cable?

---

### Post by josecuervo86 on 2009-03-11
Listo chicos, se soluciono solo. Ahora entiendo cuando dicen que se recomienda instalar por synaptic, se me hizo un lio de dependencias barabaro, pero nada que un
```
sudo apt-get remove
```
no pueda solucionar

---

### Post by santiagoward2000 on 2009-03-11
Que raro. ¿De dónde instalaste el plugin? Me parece raro que te haya roto algo en los repositorios. Lo más probable es que se haya caído alguno temporalmente.

---

### Post by josecuervo86 on 2009-03-11
Caida de repos no creo, por que es bastante improbable que tooooooooodos los repos se caigan al mismo tiempo. O sea, cuando puse que me buscara el mejor repositorio (porque pensaba que se habia caido el brasilero, que es de donde bajo yo) no me encontro ninguno.
Entonces baje desde getdeb.com la ultima versión de pidgin y ahí empezo la ecatombe. El mismo instalador me dijo que habia un conflicto de dependencias, Igual ahora se soluciono todo. Gracias a FSM por el bendito APT!!

---

