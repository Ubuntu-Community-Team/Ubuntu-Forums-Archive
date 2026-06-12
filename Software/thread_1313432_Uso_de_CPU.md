---
title: "Uso de CPU"
date: 2009-11-03
forum: Software
---

### Post by Nym Niko on 2009-11-03
Hola, me llamo Nicolás y soy nuevo aquí al igual que en Ubuntu, llevo 3 o 4 días usándolo y me resalta una duda, ¿que tanto es el uso de CPU de este sistema operativo?
Tenga esta duda porque mi CPU esta siempre al 40-60~% de uso (según el monitor del sistema). El pc no se alenta, ni anda mal, ni nada por el estilo, es solo una duda.
Bueno, no tenía muy claro donde postear esto, pero si me equivoque por favor muevanlo y me avisan :P

---

### Post by bichopro on 2009-11-03
Eso es por que esta en modo ondemand.
Si agregas en el panel el applet Monitor de frecuencia de la CPU podras cambiarlo.

---

### Post by Carlos C on 2009-11-03
40% de uso constante es mucho. Podrías partir diciéndonos el tipo de hardware de tu equipo. También debes identificar el proceso que usa tanto cpu. Escribe en el terminal el siguiente comando:
```
top
```
te va a mostrar una lista de procesos que se están ejecutando. Trata de identificar aquellos que usen más cpu.

Saludos.

---

### Post by Nym Niko on 2009-11-03
Ahora entendí, donde estaba ondemand (1 Ghz), el monitor me mostraba que usaba 60% pero al ponerlo al máximo (2.7ghz) me mostraba que usaba solo el 15%. Gracias.

---

### Post by Carlos C on 2009-11-04
Resuelto el problema entonces.

---

