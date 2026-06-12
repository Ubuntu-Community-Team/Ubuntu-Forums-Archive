---
title: "dpkg: error en el análisis, en archivo «/var/lib/dpkg/available»"
date: 2011-03-21
forum: Software
---

### Post by Hadso on 2011-03-21
Hola. Cada vez que trato de instalar algo en Ubuntu 10.10 me aparece este mensaje: 

> dpkg: error en el análisis, en archivo «/var/lib/dpkg/available» línea cercana 31812 paquete «libcanberra0»:
campo `Depends', referencia a `libvorbisfile3': la versión contiene ` '

Intenté con **$ sudo dpkg --configure -a** pero tampoco pude. 
Alguna sugerencia? 
Muchas gracias!

---

### Post by juanman on 2011-03-21
El archivo es una cache de dpkg, podes borrarla y recrearla con:
```

sudo dpkg --clear-avail && sudo apt-get update
```

Salutes

---

### Post by Hadso on 2011-03-22
> **juanman said:**
> El archivo es una cache de dpkg, podes borrarla y recrearla con:
```

sudo dpkg --clear-avail && sudo apt-get update
```

Salutes

Funcionó de maravilla. 
Mil gracias!

---

