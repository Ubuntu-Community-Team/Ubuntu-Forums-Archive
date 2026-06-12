---
title: "Problema con mouse"
date: 2008-08-13
forum: Software
---

### Post by kornykyano on 2008-08-13
La situación es así:
Después de instalar el paquete pppoe (Paquete para la conección modem) me salio un aviso de que preguntaba si quería conservar la configuración  o reemplazarla por otra que me decía. Me pareció que debía conservarla, entones le di aceptar. A partir de ese momento tengo problema con el mouse.Este se mueve muuuuy lento y si voy a preferencia del mouse al cambiarlo no se producen cambios.

Y además no funciona el teclado númerico

Pero cuando estoy en la pantalla de inicio (cuando se coloco el usuario y contraseña) este se mueve perfectamante

Yo creo que se modifico el /etc/X11/xorg.conf por eso lo pego abajo

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


algo esta mal?

---

### Post by kornykyano on 2008-08-13
Una solución temporaria para el mouse:
```
xset m N
```
donde n es la velocidad (entre 1 y 5) pero ahora es demasiado rapido ](*,)
y para habilitar el teclado numérico:
> 1. menú Sistema > preferencias > teclado
2. en la pestaña "Teclas del ratón" desactivamos la opción "Permitir controlar el puntero usando el teclado".

es lo que encontré pero funciona \\:D/

si alguien sugiere algo por favor me avisan

---

