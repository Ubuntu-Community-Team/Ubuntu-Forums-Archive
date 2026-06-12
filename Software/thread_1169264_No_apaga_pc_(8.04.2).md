---
title: "No apaga pc (8.04.2)"
date: 2009-05-25
forum: Software
---

### Post by hernan blau on 2009-05-25
Amigos: Desde el otro día, aparentemente después de una actualización, no puedo apagar la pc. La pantalla se oscurece pero la cpu no apaga. Uso Ubuntu 8.04.2, kernel 2.6.24-24-generic. Les agradecería algún consejo. Cordialmente, HB.

---

### Post by emiliano_raso on 2009-05-25
Si la apagas por consola que pasa?

```
sudo poweroff
```

---

### Post by hernan blau on 2009-05-25
Aún haciendo eso ocurre lo mismo.  Gracias. HB.

---

### Post by staar on 2009-05-25
se actualizó el kernel? en el grub podés elegir el kernel anterior? es una pc o una laptop?

saludos

---

### Post by emiliano_raso on 2009-05-25
A un amigo le pasa exactamente lo mismo pero con Windows. La solucion fue formatear.
No buscamos mucho tampoco xD Pero si no tenes nada que perder formateá y listo xD

---

### Post by staar on 2009-05-25
je, el otro día me trajeron un pc con windos para arreglar, por el mismo tema, la cosa era el winlogon.exe (o algo así), Restaurar Sistema, y listo (creo que es la única feature importante de XP que funciona decentemente, aunque muchos digan lo contrario)

bueno, basta de off, emiliano, en GNU/Linux formatear es algo extremo, acá las cosas tienen solución, y si no le damos tiempo de encontrarla y repararla, perdemos todos, él, porque pierde tiempo, datos, etc, y los demás, porque si viene alguien con el mismo problema, no podemos ayudarlo...

mejor démosle tiempo a contestar y a aumentar la información, para así poder intentar resolver su problema, sin guiarnos por los cuestionables 'métodos' del Ventanas...

saludos

EDIT: hay distintas formas de apagar por consola ```

sudo halt
sudo shutdown -h now
sudo init 0
``` probá a ver si alguna funciona para ir descartando posibles fuentes del problema

---

### Post by juancarlospaco on 2009-05-25
**sudo shutdown now**

---

### Post by josecuervo86 on 2009-05-25
Capaz que esto te sirve: [http://www.espaciolinux.com/foros-tema-t15404.html]("http://www.espaciolinux.com/foros-tema-t15404.html")

---

### Post by hernan blau on 2009-05-25
Gracias por las respuestas. Opino que reformatear debería ser un recurso extremo. Probé muchas cosas. Hace un par de años me pasó lo mismo y luego de buscar mucho usé esta fórmula: en /etc/modules agregué apm power_off=1. En /boot/grub/menu.lst en el renglón de Kernel que menciona splash agregué acpi=off apm=power_off. Además reinicié en modo recovery y pasé el dpkg para restaurar. Luego de todo eso reinicié y la pc de escritorio apagó normalmente. Cordialmente, HB.

---

### Post by emiliano_raso on 2009-05-25
Pero sea como sea por mas que apague por consola, el boton en el menú no le funciona cuando le hace click y mi pregunta es: Al clickear los botones "reiniciar" "apagar" etc, lo que hace es ejecutar estos mismos comandos?
Por lo tanto, en algun lado tiene que estar, en algun archivo escrito, que hace cada boton y ahi modificar que es lo que hace el de apagar.

O me equivoco? porque siempre busqué cual era ese archivo y nunca lo encontre :-P

---

### Post by hernan blau on 2009-05-25
No sé. No soy informático y hago lo que encuentro en la red. Prueba y error. Pero ahora, cuando le hago click al botón de apagar, funciona y se apaga. Cordialmente, HB.

---

