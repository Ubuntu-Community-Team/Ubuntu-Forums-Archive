---
title: "Pantalla de Login Muy grande!"
date: 2008-07-20
forum: Software
---

### Post by wanchan on 2008-07-20
Hola que tal, hace rato que tengo la pantalla de inicio de sesion con resolucion bastante grande, pero por lo menos puedo logearme, pero esta bastante grande.
 Me fije en el xorg.conf pero no le encuentro que tiene mal. Aca dejo una copia de la seccion Screen:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"800x600@85"	"800x600@60"	"800x600@75"	"832x624@75"	"800x600@72"	"1024x768@60"	"800x600@56"	"1024x768@43"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Virtual	1024	768 me parece que esta bien, ademas uso resolucion 1024x768 a 55 Hz. Pero aparece con una resolucion mas alta, eso es lo que creo.

---

### Post by rojojuan on 2008-07-21
> **wanchan said:**
> Hola que tal, hace rato que tengo la pantalla de inicio de sesion con resolucion bastante grande, pero por lo menos puedo logearme, pero esta bastante grande.
 Me fije en el xorg.conf pero no le encuentro que tiene mal. Aca dejo una copia de la seccion Screen:



Virtual	1024	768 me parece que esta bien, ademas uso resolucion 1024x768 a 55 Hz. Pero aparece con una resolucion mas alta, eso es lo que creo.


Fijate aquí:
[http://magarto.com/blog/archivo/2008/05/31/solucionar-tamano-de-imagen-de-arranque-en-ubuntu-hardy-heron/](http://magarto.com/blog/archivo/2008/05/31/solucionar-tamano-de-imagen-de-arranque-en-ubuntu-hardy-heron/)

---

