---
title: "[SOLVED] Problemas para configurar Conky en Fluxbox"
date: 2008-12-30
forum: Software
---

### Post by emiliano_raso on 2008-12-30
Bueno. Como les va?

El problema que tengo es ese basicamente. Instalo conky con un "sudo aptitude install conky", luego creo el archivo ".conky" en el HOME (lo creo con gedit, tal vez ese sea uno de los problemas) y alli pongo las distintas configuraciones que encuentro en internet pero ninguna funciona.

No solo eso, sino que se ejecuta en una ventana en vez de acoplado al escritorio.

Tengo Ubuntu Intrepid Ibex instalado. Instale fluxbox sin sacar Gnome ni nada. Antes de instalar Fluxbox instale XFCE.
No creo que nada de esto tenga que ver. Pero mas vale que sobre a que falte.

Agradeceria ayudas y consulten lo que sea.
Desde ya gracias...

---

### Post by Air23 on 2008-12-30
> **emiliano_raso said:**
> Bueno. Como les va?

El problema que tengo es ese basicamente. Instalo conky con un "sudo aptitude install conky", luego creo el archivo ".conky" en el HOME (lo creo con gedit, tal vez ese sea uno de los problemas) y alli pongo las distintas configuraciones que encuentro en internet pero ninguna funciona.


Por las dudas, el archivo que hay que crear en tu home es ".conkyrc" (no .conky solo)

Podes crearlo con 

```
sudo gedit ~/.conkyrc
```

Te va a aparecer un archivo de texto en blanco en el cual pega la configuracion del conky que te interese

Luego guardas y cerras. Por ultimo ejecutas "conky" desde una terminal y deberia andar

---

### Post by emiliano_raso on 2008-12-30
jaja... que ****** xD era eso xD jajaja...

gracias... perdon... fue un error re pavo mio...

---

### Post by Air23 on 2008-12-30
> **emiliano_raso said:**
> jaja... que ****** xD era eso xD jajaja...

gracias... perdon... fue un error re pavo mio...

Todo bien, esas cosas pasan

---

