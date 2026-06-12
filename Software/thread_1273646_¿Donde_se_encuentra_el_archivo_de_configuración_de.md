---
title: "¿Donde se encuentra el archivo de configuración de combinación de teclas?"
date: 2009-09-23
forum: Software
---

### Post by emiliano_raso on 2009-09-23
**Gnome Menu / Sistema / Preferencias / Combinacion de teclas**

Supongo que **Combinacion de teclas**, debe encontrarse en un archivo de texto en algun directorio.
Alguien sabe cual es ese directorio y/o archivo?
El objetivo es modificar y personalizar accesos directos de teclado mas especificos que los que la configuracion por interfaz grafica de **Combinacion de teclas** nos permite.

EDIT: Tampoco encuentro la opcion de editar los hotkeys en el GCONF-EDITOR

---

### Post by gmunioz on 2009-09-23
Hola emi....:


   1. Ejecuta gconf-editor

   2. Navega hasta  apps \ metacity \ global_keybindings

---

### Post by emiliano_raso on 2009-09-23
Ok. Gracias, es una ayuda.
Ahora, esas configuraciones que están en **apps \ metacity \ global_keybindings** tecnicamente están en algun archivo de configuración, el cual se puede editar en gedit o nano.

Sabes donde está ese archivo?

---

### Post by electronpositivo on 2009-09-24
> **emiliano_raso said:**
> Ok. Gracias, es una ayuda.
Ahora, esas configuraciones que están en **apps \ metacity \ global_keybindings** tecnicamente están en algun archivo de configuración, el cual se puede editar en gedit o nano.

Sabes donde está ese archivo?

A nivel solamente del usuario actual, debe ser el archivo:
"$home/.gconf/apps/metacity/global_keybindings/%gconf.xml"

Al igual que con las combinaciones de teclas, en la estructura que hay bajo "$home/.gconf/" tienes todos los ficheros de configuración que el usuario actual tiene distintos al gconf global... no sé si me explico

Para editar a nivel global, mira este enlace, que me parece podrás adaptar la solución planteada a lo que quieres hacer:

[http://osdir.com/ml/linux.pxes.spanish/2007/msg00159.html](http://osdir.com/ml/linux.pxes.spanish/2007/msg00159.html)

---

### Post by emiliano_raso on 2009-09-25
Muchas gracias che. Era lo que estaba buscando.

El archivo contiene lo siguiente:
```
<?xml version="1.0"?>
<gconf>
        <entry name="run_command_9" mtime="1253721776" type="string">
                <stringvalue>&lt;Shift&gt;F9</stringvalue>
        </entry>
        <entry name="run_command_8" mtime="1253721774" type="string">
                <stringvalue>&lt;Shift&gt;F8</stringvalue>
        </entry>
        <entry name="run_command_7" mtime="1253721771" type="string">
                <stringvalue>&lt;Shift&gt;F7</stringvalue>
        </entry>
        <entry name="run_command_6" mtime="1253721769" type="string">
                <stringvalue>&lt;Shift&gt;F6</stringvalue>
        </entry>
        <entry name="run_command_5" mtime="1253721767" type="string">
                <stringvalue>&lt;Shift&gt;F5</stringvalue>
        </entry>
        <entry name="run_command_4" mtime="1253721763" type="string">
                <stringvalue>&lt;Shift&gt;F4</stringvalue>
        </entry>
        <entry name="run_command_3" mtime="1253721761" type="string">
                <stringvalue>&lt;Shift&gt;F3</stringvalue>
        </entry>
        <entry name="run_command_2" mtime="1253721758" type="string">
                <stringvalue>&lt;Shift&gt;F2</stringvalue>
        </entry>
        <entry name="run_command_12" mtime="1253721755" type="string">
                <stringvalue>&lt;Shift&gt;F12</stringvalue>
        </entry>
        <entry name="run_command_11" mtime="1253721753" type="string">
                <stringvalue>&lt;Shift&gt;F11</stringvalue>
        </entry>
        <entry name="run_command_10" mtime="1253721749" type="string">
                <stringvalue>&lt;Shift&gt;F10</stringvalue>
        </entry>
        <entry name="panel_run_dialog" mtime="1253721510" type="string">
                <stringvalue>&lt;Alt&gt;F2</stringvalue>
        </entry>
        <entry name="run_command_1" mtime="1253721745" type="string">
                <stringvalue>&lt;Shift&gt;F1</stringvalue>
        </entry>
</gconf>
```

Lo que yo quería probar es si a mano puedo agregar mas *run_command*s escribiendo mas sentencias en el codigo.
Poder agregar voy a poder. El tema es que funcione :-P
El tema es que estoy en Debian, no creo que sea diferente con Ubuntu. Igual voy a postear los resultados tal vez a alguien le sirva.

---

