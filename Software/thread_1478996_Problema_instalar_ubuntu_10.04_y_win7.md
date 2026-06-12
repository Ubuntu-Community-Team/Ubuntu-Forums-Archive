---
title: "Problema instalar ubuntu 10.04 y win7"
date: 2010-05-10
forum: Software
---

### Post by sp33d3rs on 2010-05-10
Tengo un problema para instalar Ubuntu 10.04 junto a windows 7. Primero, antes de comenzar la instalación el cd me tira un error
incorregible, y me dice que pruebe instalar con la version live, en ese momento ya me pasa a la version live.
Realizo la instalación como siempre, con el particionado manual y cuando reinicia PUM!.. iniciando windows 7.. Y EL GRUB?!

En sintesis, el grub no se instala bien, o algo parecido, ya que cuando vuelvo a iniciar el live cd figura part de win y part ubuntu 10.04 lts.

_Lo que ya hice_
Grabar otra imagen del cd :(
Verificar la integridad del disco :(
particionar manual o automático :(

tengo entendido que antes de sacar la versión oficial (la que tengo) habían tenido problemas con el grub, pero el problema era que solo figuraba ubuntu y dejaba los demás SO sin visualizar.. ahora, no es lo que me pasa a mi, además, se supone que ese error lo habían corregido.

---

### Post by anarko on 2010-05-10
Si mal no recuerdo en la versión 8.04 pasaba algo parecido. En su momento era problema del instalador que corría al grubinstall después de la instalación. Se solucionaba haciendo en el ultimo paso de la instalación donde pregunta donde queremos instalar el grub poner modificar elegir el disco ( aunque sea el mismo que esta por default ) y poniendo aceptar. Desde esa version que hago eso siempre por las dudas, proba con eso.

---

### Post by sp33d3rs on 2010-05-10
> **anarko said:**
> Se solucionaba haciendo en el ultimo paso de la instalación donde pregunta donde queremos instalar el grub poner modificar elegir el disco ( aunque sea el mismo que esta por default ) y poniendo aceptar.

Me marie... no recuerdo ese paso...
lenguaje
ubicación
partición
datos personales
resumen
instalación
y reset..
no?

o se hace por consola?

---

### Post by anarko on 2010-05-10
Es en esta pantalla, ahi en advanced tenes las opciones que te digo de donde instlar el grub. 
[IMG]http://n00bsonubuntu.com/system/files/image/Screenshot-11.png[/IMG]

---

### Post by sp33d3rs on 2010-05-12
**Funciono!!!...**
Muchas gracias

---

