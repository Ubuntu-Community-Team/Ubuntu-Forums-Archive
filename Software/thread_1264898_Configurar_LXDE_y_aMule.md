---
title: "Configurar LXDE y aMule"
date: 2009-09-12
forum: Software
---

### Post by Gonz@lo on 2009-09-12
Hola, qué tal? Soy nuevo en el foro y quisiera hacerles unas preguntas:

1º Uso LXDE porque mi pc es un poco viejita (por no decir bastante) ¿Cómo puedo hacer para configurar el menú aplicaciones?

2º En el aMule siempre recibo ID baja, a pesar de que tengo el cortafuegos del router desactivado. ¿Qué puedo hacer?

Desde ya muchas gracias a quien me ayude.

Saludos!
Gonzalo

---

### Post by gmunioz on 2009-09-12
Hola gon....:

a- Por favor lee y respeta las normas.

   Solo un tema por post.

Respecto de LXDE:

El panel de lxde, esta constituido por la 

aplicación lxpanel, que permite su modificación

mediante la edición de un archivo de texto plano.

la modificación del menú requiere modificar este 

archivo de configuración del panel que lo contiene.

El archivo de configuración es:

/home/usuario/.config/lxpanel/LXDE/panels/panel

Su estructura consiste en la existencia de bloques,

Que poseen un nombre seguido de lineas entre llaves:

```
Nombre{
...
...
}
```

El primer bloque Global, contiene las características

del panel, color, transparencia, tamano.

siguen los bloques Plugins, que corresponden a los applets

del panel, iconos de lanzamiento, menús, compuestos por:

```
type=,  Un campo que indica que tipo

config, Un bloque que determina sus características.
```

Dentro de estos Plugins esta el menu, que aparece como:

```
Plugin {
    type = menu
    Config {
        image=/usr/share/lxde/images/lxde-icon.png
        system {
        }
        separator {
        }
        item {
            command=run
        }
        separator {
        }
        item {
            image=gnome-logout
            command=logout
        }
    }
}

```


Los bloques según se listan, aparecen en el menu

el primero será primero en el menu, el segundo será

segundo y asi sucesivamente.

El bloque config presenta primero el campo:

Image, este corresponde al icono de la aplicación

que aparecerá en el menu

Los bloques que aparecen en el plugin menu son:

**system **

El menú por defecto, que contiene los submenues:

Juegos

Audio

Video

Gráficos

Programación

Herramientas de sistema

Preferencias

Internet

Oficina

Accesorios

Todos los elementos del menú, se hallan en el directorio

(carpeta)

/usr/share/applications

Su formato es como archivo .desktop. 

Cada uno de estos archivos tiene un campo 

**Category**

Este campo establece la categoria de la aplicacion.

El menú de LXDE al interpretar estas categorías 

establece en que submenu de system se colocará

Por esto si quieres que una aplicación pertenezca por

ejemplo al submenu Accesorios, al archico .desktop

le editas la categoría en Ingles, por ejemplo:

    Category=[otras categorias];Accessories;


**separator**

Crea un separador en el menu.

**item**
   
Crea un lanzador en el menú

Para agregar un lanzador directamente, sin submenu:

  ```
  item{
        name=[nombre del item](Opcional)
        image=[Icono](Opcional)
        command=[comando a ejecutar (es decir el binario de la  aplicación)]
    }
```

**menu**
    
Determina un submenu, diferente a system

Se compone de los campos:

name

Nombre del submenu

image

Hace referencia al icono. 

El lanzador es establecido por un bloque item

en el que el campo command cambia a action
```
     
    menu{
         name=[nombre del submenu](Opcional)
         image=[Icono](Opcional)
         item {
               name=[nombre de la aplicación](Opcional)
               image=[Icono](Opcional)
               action=[comando a ejecutar (es decir el binario de la  aplicación)]
          }
          item {
                name=[nombre de la aplicación](Opcional)
                image=[Icono](Opcional)
                action=[comando a ejecutar (es decir el binario de la  aplicación)]
           }
    }

```


Para que que los cambios tengan efecto, es necesario

reiniciar la sesión.

---

