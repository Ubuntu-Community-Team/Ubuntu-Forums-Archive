---
title: "poner el monitor en blanco y negro"
date: 2012-08-20
forum: Software
---

### Post by drazhe on 2012-08-20
Hola, básicamente eso, si hay alguna manera de configurar el sistema para que muestre todo en escala de grises... 
lo pongo en categoría **Software**, porque ya probé desde los controles del monitor y no me lo permite, así que imagino que tiene que hacerse desde el **NVIDIA X Server Setting** o desde algún otro lugar dentro del programa... 

Se que suena raro, querer ver en blanco y negro, pero todo tiene una razón jejej, saludos y gracias por la atención...

---

### Post by gmunioz on 2012-08-21
Puedes intentar con:
1- El comando xgamma
2- Creando un xorg.conf similar a este:

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV40"
        Monitor         "Generic Monitor"
        DefaultDepth    8
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Visual "GrayScale"
                Depth           8
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

---

### Post by irv on 2012-08-21
Estoy usando un tema llamado Negro Opal y casi todo es blanco y negro con muchas canas.
Espero que usted puede leer esto, estoy usando Google Translate para escribir esto.

---

