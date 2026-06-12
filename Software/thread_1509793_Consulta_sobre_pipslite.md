---
title: "Consulta sobre pipslite"
date: 2010-06-14
forum: Software
---

### Post by ramiro_md on 2010-06-14
Buenas gente, resulta que anduve haciendo limpieza y reorganizacion en el disco y tuve que formatear lamentablemente mi Debian Squeeze.
El tema es que hoy me dispuse a instalar los drivers de mi Epson TX400 y para poder agregar la impresora a cupsys (luego de instalar el deb de los drivers proporcionados amablemente por la pagina de Epson) debo instalar un programa generador de archivos ppd. El programa también lo encuentro en la página de Epson, el tema es que cuando hago dpkg -i me dice que depende de libltdl3 (>= 1.5.2-2) y que el paquete no esta instalado. Inmediantamente hice un aptitude search libltd y me sale esto:
```

i   libltdl-dev                                - A system independent dlopen wrapper for GNU libtool  
v   libltdl3-dev                               -                                                      
i A libltdl7                                   - Un contenedor de dlopen para libtool de GNU independi
v   libltdl7-dev                               -                                             
```
Intenté instalando los -dev y nada :/. Me esta sacando el mate esto y más sabiendo que hasta hace 4 días andaba de lujo :@.
Espero que me puedan dar una mano je.
Un saludo y gracias.

---

### Post by alfplayer on 2010-06-15
No entiendo: el problema es en Debian o en Ubuntu ?

---

### Post by ramiro_md on 2010-06-15
> **alfplayer said:**
> No entiendo: el problema es en Debian o en Ubuntu ?

Debian testing :)

---

