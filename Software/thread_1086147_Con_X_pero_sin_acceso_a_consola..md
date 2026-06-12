---
title: "Con X pero sin acceso a consola."
date: 2009-03-03
forum: Software
---

### Post by zeroadrenaline on 2009-03-03
Cortito y al pie, el tema es asi:
Booteo todo hermoso, pantalla de login 10 puntos, entra impecable, y cuando tiro ctrl + alt + F# sale una manito de la compactera que me dice "que queres pibe?" Se rie un segundo y se vuelve a meter por la compactera.
No mentira, simplemente no tengo consola, o para ser mas preciso, no tengo SALIDA a consola, porque cuando bootea se ve que al final queda con el login ahi esperando.
Si a alguien se le ocurre algo, buenisimo.

---

### Post by clasificado on 2009-03-04
Yo tengo una idea!

Sacale una foto con tu celular y mostranos como se ve :P Que no me llego a dar una idea

¿responde al hotkey pero queda en negro?
¿responde al hotkey, muestra el login y no responde al teclado?


Si es X el que está intercediendo, ¿tenés algún módulo propietario cargado? (Tipo nvidia o ati). Podés probar sacarlo y poner el equivalente opensource, o el vesa estándar y probar de nuevo, para descartar el módulo.

por último, sería ver si las consolas efectivamente estan encendidas, terminan siendo procesos tty* que podes ver en el ps -a, top, ksysmanager o lo que uses. Aunque si cuando booteas ves el login supongo que se da por asumido

bah, digo nomás

clasificado

---

