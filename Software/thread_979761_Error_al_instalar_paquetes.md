---
title: "Error al instalar paquetes"
date: 2008-11-12
forum: Software
---

### Post by undiaperfecto on 2008-11-12
Hola genios!!! Tengo una duda no muy complicada.
Cada vez que instalo algo desde sinaptyc, luego de instalar todo, me sale un error, como que se instala todo bien, pero esto pareciera estar trabado y nunca termina de instalarse bien, al menos eso es lo que interpreto yo.
La verdad no me afecta en lo mas minimo en el funcionamiento ni en la instalacion de paquetes, pero me tiene intrigado que será.
Este es el mensaje que sale en el terminal.


> dpkg: error al procesar cups (--configure) :
el paquete cups no esta listo para configurarse
no se puede configurar (estado actual `triggers-awaited`)
Se encontraron errores al procesar:
cups
E: Sub-process /usr/bin/dpkg returned an error code (1)
No se ha podido instalar un paquete. Intentando recuperarse

---

### Post by faktorqm on 2008-11-12
Proba 

```
sudo apt-get install -f
```

Para reparar paquetes rotos. O desde el synaptic lo mismo graficamente. salu2!!

---

### Post by guillermolisi on 2008-11-12
Proba lo que te aconseja Faktor y comenta que resultados tuviste.

---

### Post by undiaperfecto on 2008-11-13
Creo que no se arreglo :(
Despues de hacer eso, use el actualizador, se instalaron dos paquetes y cuando termina el update me volvio a aparecer el mensaje de error

> minotauro@minotauro-desktop:~$ sudo apt-get install -f

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 3 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
dpkg: error al procesar cups (--configure):
 el paquete cups no está listo para configurarse
 no se puede configurar (estado actual `triggers-awaited')
Se encontraron errores al procesar:
 cups
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by faktorqm on 2008-11-13
y... primero tendrias que desinstalarlo entonces. lo haces con 

```
sudo apt-get remove cups --purge
```

o lo que creo es lo mismo

```
sudo apt-get purge cups
```

Salu2!!

---

### Post by undiaperfecto on 2008-11-14
ahora parece que funciono, porque actualice unas pavadas y anduvo todo bien.
lo que si tal vez necesite reinstalar cups si me compro una impresora no?
igualmente no esta en mis planes

mil gracias nuevamente

---

### Post by Hei Ku on 2008-11-14
No, no tenes que actualizar nada al cambiar de impresora, salvo que sea de las que no traen drivers para linux.

---

