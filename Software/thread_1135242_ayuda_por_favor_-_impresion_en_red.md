---
title: "ayuda por favor - impresion en red"
date: 2009-04-24
forum: Software
---

### Post by gastoncl on 2009-04-24
Hola, soy Gaston y soy nuevo en el mundo linux, para adentrarme decidi instalar en la empresa donde trabajo ubuntu (7.10, 8.04 ) y xubuntu ( 7.10 ) para las maquinas mas pequeñas, mi problema es este, en mi terminal donde tengo ubuntu 8.04 tengo instalada una hp f4280, la cual la pongo en red y todas las terminales con ubuntu y xubuntu la ven, la instalan y pueden imprimir en red, ahora, en otras terminales tengo otras impresoras, hp 3180 ( con ubuntu 8.04) hp 710c ( con ubuntu 8.04) y las demas terminales tambien las pueden ver e instalar, tanto por sistemas, administracion, impresoras, como por localhost:631, pero al momento de largar una impresion en red, no larga nada, me dice que la impresora esta ocupada y que va a tratar de imprimir en 15 seg, y asi hasta llegar a mas de 5 min, tambien lo que hize fue, mirar bien como esta declarada la impresora en cada maquina, y colocar en localhost en cada terminal, en URL tal cual esta declarada, pero no hay caso siempre lo mismo, ya no se que hacer, con el poco conocimiento que tengo, hace bastante que estoy con este problema, si alguien me puede dar una idea de que hacer les voy a agradecer

---

### Post by pablo.s on 2009-04-24
Analizando el problema:

> **gastoncl said:**
> Hola, soy Gaston y soy nuevo en el mundo linux, para adentrarme decidi instalar en la empresa donde trabajo ubuntu (7.10, 8.04 ) y xubuntu ( 7.10 ) para las maquinas mas pequeñas, mi problema es este, 

Un gusto conocerte.

> **gastoncl said:**
> en mi terminal donde tengo ubuntu 8.04 tengo instalada una hp f4280, la cual la pongo en red y todas las terminales con ubuntu y xubuntu la ven, la instalan y pueden imprimir en red,

Ya està configurada en CUPS, supongo,
con tu máquina como servidor CUPS.
Decìs que funciona.

> **gastoncl said:**
> ahora, en otras terminales tengo otras impresoras, hp 3180 ( con ubuntu 8.04) hp 710c ( con ubuntu 8.04) y las demas terminales tambien las pueden ver e instalar, tanto por sistemas, administracion, impresoras, como por localhost:631, 

Teniendo en cuenta que las demás
máquinas están configuradas de la
misma manera que la tuya

> **gastoncl said:**
> pero al momento de largar una impresion en red, no larga nada, me dice que la impresora esta ocupada y que va a tratar de imprimir en 15 seg, y asi hasta llegar a mas de 5 min, 

De cual impresora estás hablando ahora?
La tuya (f4280), la hp 3180, o la hp 710c?

> **gastoncl said:**
> tambien lo que hize fue, mirar bien como esta declarada la impresora en cada maquina, y colocar en localhost en cada terminal, en URL tal cual esta declarada, pero no hay caso siempre lo mismo, ya no se que hacer, con el poco conocimiento que tengo, hace bastante que estoy con este problema, si alguien me puede dar una idea de que hacer les voy a agradecer

Ahora tengo una consulta para hacerte:
Son impresoras con USB o Ethernet directamente?
La mejor idea no serìa armar un servidor para
las impresoras?
Saludos

---

### Post by gastoncl on 2009-04-24
Hola Pablo, muchas gracias, mira todas las impre son usb, menos la 710 que es paralela, y armar un servidor, mmm es complicado, ya que trabajo en una empresa donde tengo dos pisos, y se me complica de que el que esta en el piso 1, venga a buscar su impresion en el piso 2, o al reves, en realidad estan por hacer eso, pero yo estoy tratando de evitarlo para comodidad de cada usuario, ya que tiene una impresora cerca porque no usarla? lo que me parece extraño es que todas las terminales puedan ver la mia ( f4280) e imprimir sin problema en esta, las otras tambien las ven ( 3180 y 710) y las instalo sin problemas en cups mediante ipp, me dice que se instalo correctamente, todo chiche, pero al momento de largar una impresion en cualquiera de las dos ( 3180 y 710 ) nada, se queda, me dice usuario ocupado se reintentara en 15 seg y asi sigue, si se te ocurre algo mas, soy todo orejas

---

### Post by pablo.s on 2009-04-24
Las impresoras usando CUPS localmente
(quiero decir: la maquina que tiene la
impresora 3180 y la maquina que tiene
la 710c) imprimen bien?
Estàs usando SAMBA para compartir?
Puede ser que haya que modificar la
configuraciòn de smb.conf para que
lea bien a las otras dos impresoras...

Marco Antonio sabria responder esto
mucho mejor que yo!

---

### Post by gastoncl on 2009-04-24
si todas las impresoras que estan instaladas en su correspondiente maquina, imprimen correctamente, y a todas les habilite el samba, pero te repito escucho cualquier tipo de solucion, y como hago plis para ubicarlo a marco antonio, muchas gracias amigo

---

