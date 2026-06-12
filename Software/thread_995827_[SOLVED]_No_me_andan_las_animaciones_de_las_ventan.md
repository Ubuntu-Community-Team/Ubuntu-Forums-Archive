---
title: "[SOLVED] No me andan las animaciones de las ventanas"
date: 2008-11-28
forum: Software
---

### Post by leosr on 2008-11-28
Hola.
No me andan las animaciones de las ventanas, está habilitado compiz y funciona el cubo.
En la sección Efectos está habilitado Animaciones y Animaciones add-on pero no hace ninguna.
Con Hardy me funcionaban.

Saludos.

---

### Post by hictio on 2008-11-28
Fijate en System > Preferences > CompizConfig Settings Manager > Effects > Window Decoration.

El box de Command, que dice?

---

### Post by sajnox on 2008-11-28
A que te referis con animaciones de ventanas? A que las ventanas se mueven en forma "gelatinosa", si eso tenes que buscar en el Settings Manager de Compiz la opcion "wobbly windows"

Sino es eso trata de ser mas especifico en cuanto a que efecto buscas y ves que no anda

Saludos

---

### Post by leosr on 2008-11-28
> **hictio said:**
> Fijate en System > Preferences > CompizConfig Settings Manager > Effects > Window Decoration.

El box de Command, que dice?

Hola.

Dice: /usr/bin/compiz-decorator

Saludos

---

### Post by leosr on 2008-11-28
> **sajnox said:**
> A que te referis con animaciones de ventanas? A que las ventanas se mueven en forma "gelatinosa", si eso tenes que buscar en el Settings Manager de Compiz la opcion "wobbly windows"

Sino es eso trata de ser mas especifico en cuanto a que efecto buscas y ves que no anda

Saludos

Hola.
No me refiero a ese efecto sino a las animaciones de abrir, minimizar y cerrar. En Hardy por ej. la de minimizar la tenía en Aleatorio. "Wobbly windows" funciona.

Saludos

---

### Post by hictio on 2008-11-28
> **leosr said:**
> Hola.

Dice: /usr/bin/compiz-decorator

Saludos

En mi caso, uso Emerald, tengo:

```

/usr/bin/emerald &

```

Tenes que hacer logout para que tome el cambio.

---

### Post by leosr on 2008-11-28
> **hictio said:**
> En mi caso, uso Emerald, tengo:

```

/usr/bin/emerald &

```

Tenes que hacer logout para que tome el cambio.

Creo que no tengo instalado Esmerald, cómo lo instalo?

---

### Post by hictio on 2008-11-28
> **leosr said:**
> Creo que no tengo instalado Esmerald, cómo lo instalo?

Abri un Terminal, y tipea:

```

sudo aptitude install emerald (ENTER)

```

Te va a pedir tu passwd, y se va a bajar e instalar lo que necesite.

---

### Post by leosr on 2008-11-28
> **hictio said:**
> Abri un Terminal, y tipea:

```

sudo aptitude install emerald (ENTER)

```

Te va a pedir tu passwd, y se va a bajar e instalar lo que necesite.

No sirvió de nada, lo único que cambió fue los bordes de las ventanas.
Y si re-instalo Compiz?

---

### Post by hictio on 2008-11-28
> **leosr said:**
> No sirvió de nada, lo único que cambió fue los bordes de las ventanas.
Y si re-instalo Compiz?

Es que eso es exactamente lo que hace Emerald.

Puntualmente, cuales son las "animaciones de las ventanas" que no te andan?
Quiero decir, que efecto de animacion queres y que haga que cosa, o hacia que cosa, en un instalacion de Hardy?

---

### Post by leosr on 2008-11-28
Hola.
Lo solucioné yendo a Preferencias - Reestablecer valores por defecto. No tengo idea qué estaba mal.

Gracias a todos

---

### Post by Mago Jose on 2010-07-23
Hola.

Disculpen las molestias pero a mi no me funciono lo que uds hicieron
es decir restableci los valores por defecto y nada, instale el emerald y cambie el comando de decoracion de ventanas y nada...
no se si haga la diferencia pero tengo el lucyd...

de antemano muchas gracias

---

