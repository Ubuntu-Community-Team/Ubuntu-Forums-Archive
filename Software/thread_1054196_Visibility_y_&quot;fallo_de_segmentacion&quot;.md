---
title: "Visibility y &quot;fallo de segmentacion&quot;"
date: 2009-01-29
forum: Software
---

### Post by NickCis on 2009-01-29
Hola, yo tengo Ubuntu 8.04, hice una instalacion minima usando openbox, y de bara tengo visibility.

El problema, es que despues de un tiempo se cierra sola. Visibility esta abierto atomaticamente por el openbox.
Pero, si la abro manual y veo en consola que me dice cuando el programa se cierra solo dice esto:

```
oldpc@oldpc:~$ visibility
Fallo de segmentación
oldpc@oldpc:~$
```

Tinen alguna idea de como solucionarlo?

Saludos.

---

### Post by guillermolisi on 2009-01-29
> **NickCis said:**
> Hola, yo tengo Ubuntu 8.04, hice una instalacion minima usando openbox, y de bara tengo visibility.

El problema, es que despues de un tiempo se cierra sola. Visibility esta abierto atomaticamente por el openbox.
Pero, si la abro manual y veo en consola que me dice cuando el programa se cierra solo dice esto:

```
oldpc@oldpc:~$ visibility
Fallo de segmentación
oldpc@oldpc:~$
```

Tinen alguna idea de como solucionarlo?

Saludos.

Lo instalaste de un paquete binario o lo compilaste ?

Errores como ese pueden deberse a diferencias en versiones de librerias, por ejemplo.

---

### Post by NickCis on 2009-01-30
Lo instale desde un Deb... supongo qe no era un deb para la 8.04... :S

Como puedo solucionar esto?...

---

### Post by Hei Ku on 2009-01-30
desinstalalo y trata de conseguir otro deb.

O el codigo y vemos como hacer para compilarlo.

---

### Post by NickCis on 2009-01-30
Esta es la pagina de visibility: 
[http://code.l3ib.org/?p=visibility-python.git;a=summary](http://code.l3ib.org/?p=visibility-python.git;a=summary) 
(sacada desde la pagina del openbox, [http://icculus.org/openbox/index.php/Help:Contents#Cool_programs_to_run_with_Openbox](http://icculus.org/openbox/index.php/Help:Contents#Cool_programs_to_run_with_Openbox) ), 
y para bajar el codigo meparec que es este link:
[http://code.l3ib.org/?p=visibility-python.git;a=snapshot;h=HEAD](http://code.l3ib.org/?p=visibility-python.git;a=snapshot;h=HEAD)

Y el deb del visibility lo saque de este link [http://linexiando.blogspot.com/2008/07/openbox-en-ubuntu-804.html](http://linexiando.blogspot.com/2008/07/openbox-en-ubuntu-804.html) ( [http://www.adrive.com/public/7904941b34ec0991def4fc3dcc040a56d3629952d2b75336954d5a0bb3051254.html](http://www.adrive.com/public/7904941b34ec0991def4fc3dcc040a56d3629952d2b75336954d5a0bb3051254.html) )

Nunca compile, si me ayudan en esto les agradezco mucho =)

Saludos.

---

### Post by Hei Ku on 2009-01-30
Ok. Vamos con paciencia entonces:

Abri una terminal y empeza a teclear: :D

```

cd ~
mkdir visibility
cd visibility

sudo apt-get install git-core python-gnome2-desktop-dev python-glade2

git clone git://code.l3ib.org/visibility-python.git visibility-python.git
cd visibility-python.git/
chmod +x visibility.py


```

Y despues de eso, podes probar de ejecutarlo:

```

./visibility.py

```

Si te anda, podes alardear que sos una fiera que usa el mismo repositorio que Linus Torvalds y usa programas en python. :D

---

### Post by NickCis on 2009-02-01
Jeje, ahora anda!!!,, Ensima es mejor que el otro qe tenia ahora cuando usas el segundo boton pods cerrar ventanas y esas cosas xD...

Bueno, el tema es que no puedo configurar el color de fondo :S, en las preferencias no se por que no esta,,, y los archivos de configuracion qe usaba antes no me sirven (o cambio de carpeta a donde los guardan)...

Si alguien tiene idea de como hacer esto, no me molestaria una ayuda xD...

Saludos.

---

### Post by jjgomera on 2009-03-04
> **NickCis said:**
> Jeje, ahora anda!!!,, Ensima es mejor que el otro qe tenia ahora cuando usas el segundo boton pods cerrar ventanas y esas cosas xD...

Bueno, el tema es que no puedo configurar el color de fondo :S, en las preferencias no se por que no esta,,, y los archivos de configuracion qe usaba antes no me sirven (o cambio de carpeta a donde los guardan)...

Si alguien tiene idea de como hacer esto, no me molestaria una ayuda xD...

Saludos.

Hola, si, ese es el gran problema, de esta versión, por eso yo venía usando y puse en mi blog (el que citas de donde te bajaste el deb) la otra versión ([http://code.l3ib.org/?p=visibility.git;a=summary](http://code.l3ib.org/?p=visibility.git;a=summary))
No sabría ayudarte, ya que este parece no usar ningún archivo de configuración y usar tema gtk, lo cual es mucho más difícil de controlar, yo probaría a cargarlo con diferentes temas gtk para intentar buscar alguno que coincidiera con lo que quieres, pero me temo que si alguno ajusta el color de fondo adecuado, quiza desajusta el color de letra ..., lanzándolo con un comando como:

bash -c 'GTK2_RC_FILES=/direccion/archivo/gtkrc  /direccion/archivo/visibility.py'

Yo sigo usando la otra versión, que aunque se cierra de vez en cuando, tengo un acceso de teclado para arrancarla de nuevo, y es ultraconfigurable

---

