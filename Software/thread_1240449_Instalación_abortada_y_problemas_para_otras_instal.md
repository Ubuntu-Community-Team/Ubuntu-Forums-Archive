---
title: "Instalación abortada y problemas para otras instalaciones"
date: 2009-08-14
forum: Software
---

### Post by GerryEastwood on 2009-08-14
Hola.

Tras la instalación de Ubuntu Studio decidí instalar software adicional.
Entre otras cosas que encontré disponibles, el OpenOffice. El problema es que durante la instalación se quedó colgado en un punto (merge nosécuánto) y tuve que resetear. Ahora no puedo instalar nada más porque siempre quiere terminar ese. Me manda a escribir en la terminal,
```
sudo dpkg --configure -a
```
con lo que retoma y no termina nunca.

¿Hay alguna forma de solucionar esto?

Gracias.

---

### Post by guillermolisi on 2009-08-14
No me queda claro si corriste esa linea de comando en una consola/terminal.

Si no lo hiciste, hacelo y si seguis con problemas en los repositorios o para instalar paquetes, vamos viendo como evoluciona.

Si lo hiciste, podrias mostrar que mensaje te devuelve ?

---

### Post by GerryEastwood on 2009-08-14
Sí, lo hice y trata de continuar, pero se queda en eso y no me deja hacer nada más en la máquina (si pruebo ahora no te voy a poder responder).

Voy a hacerlo y en todo caso te lo digo después de resetear.

EDITADO: Finalmente tuve que resetar porque se queda haciendo eso:

```
adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...
```

Y allí se queda horas. ¿Hay algo parecido al ctrl+c o ctrl+break o ctrl+alt+supr de DOS/Windows?

Gracias

---

### Post by GerryEastwood on 2009-08-15
Por favor, que no puedo instalar nada :(

Gracias.

---

### Post by Hei Ku on 2009-08-15
El ctrl+c deberia funcionar.
De todas maneras, eso deberia funcionar.

Podes postear lo que te aparece cuando hacer: sudo dpkg --configure -a

---

### Post by GerryEastwood on 2009-08-15
Me pudrí de los cuelgues y reinstalé Ubuntu Studio.

Gracias.

---

