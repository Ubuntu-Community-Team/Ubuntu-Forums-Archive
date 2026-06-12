---
title: "Menus y ventanas sin texto"
date: 2008-11-06
forum: Software
---

### Post by sofocles92 on 2008-11-06
Hola amig@s:

He instalado Ubuntu 8.10. Resulta que tanto en OpenOffice 3 como en Opera los menus desplegables aparecen vacíos (falta el texto) y también en las ventanas de las distintas opciones y configuración de estas dos aplicaciones. No pasa esto en otros programas. No termino de encontrar la solución. También es verdad que llevo 2 meses como ubuntero y, francamente, estoy muy contento. Pero este asunto me quita el sueño. Naturalmente no puedo trabajar con el OpenOffice ni usar Opera así. ¿Cual puede ser el problema? Tengo Compiz-fusion. He probado a quitar efectos por si acaso y no parece que sea eso.

Gracias por vuestra atención.

Sof

---

### Post by faktorqm on 2008-11-07
Que raro lo que contas! PAreciera ser que es un error de que te falta una fuente o algo por el estilo. Hace una cosa, proba de ejecutar el writer por ejemplo desde la consola con el comando: 

```
ooffice -writer
```

y si tiene algun error es altamente probable que te lo muestre ahi. Adjunta la salida de todas maneras si no ves nada. Salu2!!

---

### Post by sofocles92 on 2008-11-07
Gracias por contestarme. Después de dar muchas vueltas y casi cargarme el Ubuntu (estoy aprendiendo mucho, afortunadamente) he visto que el problema sí está relacionado con los efectos visuales. Si elijo la opción "ninguno" entonces todo va bien. En cuanto pongo simplemente la opción "normal" entonces desaparece el texto de los menús y ventanas en esas aplicaciones.

Abriendo el Writer por consola se abre igual que usando el menú aplicaciones. No hay ningún mensaje de error. Lo mismo. Sin efectos visuales todo bien. Con efectos normales (o superior) se produce el error.

Pienso que tiene que ver con los controladores de la tarjeta gráfica. La mía es una Nvidia de las que están en la lista negra de Ubuntu 8.10. Estoy usando la última versión de los controladores privativos de Nvidia que, lamentablemente, son una beta. Con estos controladores la aceleración 3D y los efectos visuales funcionan muy bien... excepto este fallo con los menús en, al menos, OpenOffice y Opera.

Así que la solución temporal es (por el momento) desactivar los efectos visuales. Por una parte es una pena porque me gustaban mucho y los estaba disfrutando un montón... algo que con Windows y mi máquina hubiera sido totalmente imposible. Pero claro, prefiero poder trabajar :) De todas formas Ubuntu es impresionante incluso sin efectos visuales.

Reitero las gracias y si aparece alguna idea o posible solución o algo más que pueda hacer tendrás/tendreis mi gratitud eterna.

Un cordial saludo,

-Sof-

---

### Post by saibof on 2008-12-09
Saludo Yo tenia elmismo problema Igualito al tuyo, desactivaba los efectos y aparecian lo ménus, la solucion la encontre googleando
--> cierra el openOffice
--> ve a Sistema > Preferencias > Apariencia
--> En la Pestaña tipografia Seleciona **Suavizado De Subpixel (LCD)**
--> Abre de nuevo openoffice y espero que ya esten tus fuentes 
Saludos!!

---

