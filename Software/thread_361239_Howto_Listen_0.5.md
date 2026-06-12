---
title: "Howto Listen 0.5"
date: 2007-02-14
forum: Software
---

### Post by tychocity on 2007-02-14
Instalacion nueva version listen 0.5

[http://www.listen-project.org](http://www.listen-project.org)

Esta instalación la realice en Edgy

Primero instalamos las dependencias

$sudo apt-get build-dep listen

$sudo apt-get install python-elementtree intltool

instalar nueva version mutagen

   $wget [http://www.sacredchao.net/~piman/software/mutagen-1.10.1.tar.gz](http://www.sacredchao.net/~piman/software/mutagen-1.10.1.tar.gz)

   $tar -zxvf mutagen-1.10.1.tar.gz
   $cd mutagen-1.10.1/
   $./setup.py build
   $sudo ./setup.py install
   
$tar -zxvf listen-0.5.tar.gz
$cd listen-0.5/
$make
$sudo checkinstall

editar el /usr/bin/listen

 donde dice

python -OO /usr/lib/listen/listen.py "$@"
debe quedar (agregar el #) 
#python -OO /usr/lib/listen/listen.py "$@"
agregar la siguiente linea
LD_LIBRARY_PATH=/usr/lib/firefox python -OO /usr/lib/listen/listen.py "$@"

Listo.

---

### Post by BlackHero on 2007-02-14
es muy completo pero es muy multimedia que digamos =) gracias por el aporte =)
















aguante bpm =)

---

### Post by QUASAR_FREAK on 2007-02-14
grax!

aguante bpmx =P

---

### Post by Benji86 on 2007-02-15
mejor que AmaroK?

---

### Post by Nemesis Teufel on 2007-02-15
> **Benji86 said:**
> mejor que AmaroK?
A mi gusto no. Quiza se cuelga un poquito menos que el Amarok, pero es muy rebuscado para hacer las cosas. El amarok es muuuucho mas simple y eficiente.

---

### Post by screening on 2007-02-15
Intente instalarlo tal como dice aqui pero me da errores al hace "make" en la carpeta listen
```
ariel@dentrix:~/Downloads/listen-0.5$ make
Checking for Python... /usr/bin/python
Checking Python version: 2.4
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6: found
Checking for gnome.ui: found
Checking for egg.trayicon: found
Checking for pygtkmozembed: found
Checking for mutagen: found
Checking for PyGSt >= 0.10: found
Checking for DBUS: found
Checking for python-libgpod: not found
Listen recommends python-gpod (http://www.gtkpod.org)
Checking for python-musicbrainz2: not found
, but recommanded
Checking for python-tunepimp > 0.5: not found
, but recommanded
Checking for libsexy: not found
Listen recommends python sexy for sexy widget. 
make -C mmkeys
make[1]: se ingresa al directorio `/home/ariel/Downloads/listen-0.5/mmkeys'
make[1]: `mmkeys.so' está actualizado.
make[1]: se sale del directorio `/home/ariel/Downloads/listen-0.5/mmkeys'
cp mmkeys/mmkeys.so src/mmkeys.so
for lang in ./zh_CN ./be ./ar ./ca ./bn ./br ./da ./de ./cs ./es ./fi ./et ./fr ./gl ./hu ./ja ./it ./ko ./lv ./nb ./nl ./pa ./pl ./pt ./ro ./ru ./sk ./sr ./sv ./tr ./uk ./vi ./en_CA ./en_GB ./en_US ./pt_BR; do msgfmt po/$lang.po -o po/$lang.mo;done
intltool-merge -d po misc/listen.desktop.in misc/listen.desktop
make: intltool-merge: No se encontró el programa
make: *** [po-data] Error 127

```

Alguna idea? aparentemente me falta el paquete python-sexy, musicbrainz2 y tunepimp??? , pero no lo encuentro googleando...

---

### Post by tychocity on 2007-02-16
fijate te debe faltar el intltool $sudo apt-get install intltool

Saludos.

---

### Post by screening on 2007-02-16
gracias! tenias razon...
como supiste?

una cosa mas, como puedo hacer para que me reconozca archivos wma???

---

### Post by screening on 2007-03-08
y si al abrir listen desde la terminal me tira este error?

Traceback (most recent call last):
File "/usr/lib/listen/listen.py", line 54, in ?
raise ImportError,"Need mutagen >= 1.8"
ImportError: Need mutagen >= 1.8

como obtengo mutagen mayor o igual a 1.8??? hasta donde se esta la version 1.10 nada mas, o es otra cosa?

---

### Post by felipelerena on 2007-03-08
por que no te armas un deb y lo subis aca, jajaja. re vago el otro... yo lo tengo andando hace algunos dias. el 0.5 tiene el parchecito que les mande, estoy muy contento de haber solucionado mi propio problema y que lo incluyan, jajaja.

---

### Post by brunoaco on 2008-02-23
hice todo lo mencionado, y cuando ejecuto el programa no hace nada, es decir, se nota que lee desde hdd y que esta procesando, pero luego nada mas que lo que figura a continuacion:

bruno@bruno-laptop:~$ listen
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 66, in <module>
    import utils, const, stock, config
  File "/usr/lib/listen/utils.py", line 33, in <module>
    import stock
  File "/usr/lib/listen/stock.py", line 78, in <module>
    import const
  File "/usr/lib/listen/const.py", line 116
SyntaxError: Non-ASCII character '\xc3' in file /usr/lib/listen/const.py on line 117, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details

fui a ver el link de python, pero no entendi nada util...

---

### Post by maxsombra on 2010-03-10
hola soy nuevo con ubuntu muy nuevo. ayer instale listen0.5, tengo ubuntu 9.0.4 pero no me reproduce. lo descarge por la ventana de añadir y quitar programas. ¿nesesito intalar algunos puling? cuales?


cualquier ayuda se agradece correo diegoo-guio1hotmail.com

---

