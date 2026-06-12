---
title: "Referenciar Librerias Publicas"
date: 2011-03-12
forum: Software
---

### Post by sebasthian777 on 2011-03-12
Hola chicos, no se si estoy usando los términos correctos porque soy muy nuevo en esto de desarrollar en linux, hasta el momento siempre lo he usado a modo computadora de offmatica o de entretenimiento. Pero bueno, acá va mi problema.

Estoy trabajando con OpenCV y gcc, el OpenCV lo tengo instalado pero no puedo referenciar correctamente las librerias que son propias del OpenCV cuando desarrollo en C compilando/ejecutando con gcc.

Describo a modo de ejemplos lo que me esta ocurriendo

Supongamos que tengo un codigo "programtest.c"
Dentro del codigo tengo esto:

```
#include <highgui.h>
int main( int argc, char* argv[] ) {
(...)
(...)
return 0
}
```

Ahora bien, luego de instalar OpenCV no me toma highgui.h, o sea que cuando ejecuto:

```
sebastiandell@sebastiandell-laptop:~/ejemplosopcv$ gcc  programtest.c

programtest.c:1:21: error: highgui.h: No existe el fichero o el directorio
...
...
...

```

Pero si lo hago indirectamente:

```
sebastiandell@sebastiandell-laptop:~/ejemplosopcv$ gcc `pkg-config --cflags --libs opencv` programtest.c

```

Con:
pkg-config --cflags --libs opencv
Logro compilar y ejecutar mi codigo satifactoriamente.

Alguna idea de como puedo hacer para que tome a las librerias de OpenCV de forma publica o global (no se cual es el termino en linux) para evitarme tener que ejecutar de esta forma?

otro ejemplo seria en "MONO" donde directamente no puedo referenciar absolutamente ninguna libreria.

Bueno eso solo, gracias de antemano =)

EDIT:

En mono logre un cambio, es como lo anterior, pero es mas facil la ejecucion.

en Proyecto-> Opciones "nombredelproyecto"
En la seccion de "generacion de codigo":

en opciones adicionales bastaba agregar:
```
`pkg-config 
--cflags 
opencv`
```

```

`pkg-config 
--libs 
opencv`

```

Respectivamente

---

### Post by sebasthian777 on 2011-03-17
nadie nadie? =(

---

