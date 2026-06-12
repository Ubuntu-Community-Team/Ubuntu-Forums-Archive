---
title: "[SOLVED] Splash de nvidia al inciar hardy"
date: 2008-08-03
forum: Software
---

### Post by ramiro_md on 2008-08-03
Gente, lo cierto es que dije que no iba a volver a usar una version x.04, pero ya fue :P lo necesitaba con urgencia jeje...la cuestion es que al iniciar me tira una "splash" o un pantallazo de nvidia, lo cual no quiero que aprezca, he googleado algo pero no encuerntro nada en concreto, si alguien tiene idea de como sacarlo es todo oido. Un saludo gente.

---

### Post by faktorqm on 2008-08-03
mas rapido q un bombero..... estas seguro que googleaste? no te creo... ;)

```

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Option          "AllowGLXWithComposite" "true"
	[COLOR="Red"]**_Option 		"NoLogo" "True"_**[/COLOR]
	Screen	0
	Vendorname	"NVIDIA"
EndSection

```

La opcion que esta en rojo dentro de la seccion device tenes que poner. Salu2!

---

### Post by ramiro_md on 2008-08-03
Faktoqm estas son mis lineas:

[B]Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:0:13:0"
	Driver		"nvidia"
	Screen	0
EndSection[/B]

no esta la que vos maracste en rojo =S..la agrego yo ??

---

### Post by SLA_leandrin on 2008-08-03
> **ramiro_md said:**
> Faktoqm estas son mis lineas:

[B]Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:0:13:0"
	Driver		"nvidia"
	Screen	0
EndSection[/B]

no esta la que vos maracste en rojo =S..la agrego yo ??

Si si, agregale esa línea, eso es todo...

---

### Post by ramiro_md on 2008-08-03
Gracias muchachos desaparecio el splash !.:lolflag:
Faktorqm el martes a copar avellaneda !:lolflag:

---

