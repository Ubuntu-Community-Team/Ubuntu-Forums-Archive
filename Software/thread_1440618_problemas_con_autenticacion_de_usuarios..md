---
title: "problemas con autenticacion de usuarios."
date: 2010-03-27
forum: Software
---

### Post by mama21mama on 2010-03-27
Hola,

somos 3 usuarios en mi ubuntu, antes cada uno tenia su clave para asi
tener cada cual sus cosas. Pero... ahora algo se averio en karmic y las
claves no sirven, ahora con un simple «enter» entran los usuarios. :s

Lo que paso es que se apago la pc sola.
Luego al iniciarse de nuevo me tiro error en el filesystem, le tire sin
saber mucho el $fsck y al aparecer «fix» marque con (y).

Creo que la embarre pero quiero corregir los que los usuarios tengan
claves de autenticación al inicio.

en el irc me tiraron 3 posibilidades 

1º upgradear
2º reinstalar 
3º o reinstalar forzadamente pam.d
/etc/pam.d
no se que hacer :s

Saludos

---

### Post by juancarlospaco on 2010-03-28
Ponerle clave desde sistema--->administracion--->usuarios *(?)*

---

### Post by mama21mama on 2010-03-28
Ya intente con $ passwd y desde donde me indicas y nada de nada. :s

---

### Post by juancarlospaco on 2010-03-29
borra los user y crealos de nuevo *(?)*
muy extraño... :s

---

### Post by mama21mama on 2010-03-29
Ya probé eso y nada.
solo el problema es en el menú del grub que no me acepta entrar en modo recovery y también en la pantalla del gdm donde están los usuarios que con marcarlos y presionar enter inician sesión.
No pasa lo mismo si quiero iniciar sesión en las tty con esos usuario si le pongo enter a la clave no entra. Muy raro lo que provoco el error en filesystem.

---

