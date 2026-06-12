---
title: "Xubuntu 11.04 no inicia sesión"
date: 2011-10-17
forum: Software
---

### Post by Liv~ on 2011-10-17
Hola a todos.
Tuve que reinstalar el sistema (xub natty) y ahora resulta que cuando aparece la pantalla de login, escribo la contraseña, se pone la pantalla negra por unos segundos y vuelve a la pantalla de inicio de sesión.
Probé de iniciar sesión desde consola y reinstalar el gdm pero no me funcionó, no hay forma de entrar al escritorio de Xubuntu en modo gráfico y cómo no tengo idea qué hacer, los consulto a ustedes.
Habrá alguna posible solución o tendré que reinstalar otra vez?

Desde ya gracias a quien pueda ayudarme.

---

### Post by collisionystm on 2011-10-17
> **Liv~ said:**
> Hola a todos.
Tuve que reinstalar el sistema (xub natty) y ahora resulta que cuando aparece la pantalla de login, escribo la contraseña, se pone la pantalla negra por unos segundos y vuelve a la pantalla de inicio de sesión.
Probé de iniciar sesión desde consola y reinstalar el gdm pero no me funcionó, no hay forma de entrar al escritorio de Xubuntu en modo gráfico y cómo no tengo idea qué hacer, los consulto a ustedes.
Habrá alguna posible solución o tendré que reinstalar otra vez?

Desde ya gracias a quien pueda ayudarme.

Hola,

Eso significa que algo se estrelló. Probablemente los gráficos relacionados.

No estoy usando Xubuntu. Creo que hay un botón de la pantalla de inicio de sesión que le debe permitir elegir un modo seguro de gráficos

---

### Post by Liv~ on 2011-10-18
Bueno, reinstalé y sigue igual, pero tengo unos datos nuevos, a ver si sirven de algo...

Entré en recovery console y al poner startxfce4 primero me tira "X server is already running on display :0"
Después dice que no se puede crear el directorio /home/usuario/.config: permiso denegado.
Tira el mismo error para /home/usuario/.cache (y la lista de carpetas dentro de home, como ser imágenes, documentos, descargas, etc).

Finalmente tira error sobre .ICEauthority: permiso denegado.

Pareciera que haga lo que haga sigue todo igual :/

---

### Post by Liv~ on 2011-10-19
Nadie que me pueda ayudar? No sé qué hacer ya :(

---

### Post by euzkoarima on 2011-10-19
No se como se arregla este problema, sobre todo no uso xfce
Sin embargo en mi apuntes (ya viejos x cierto) figura que cuando hay un problema con el Xserver se acostumbraba a hacer desde consola 

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

Antes de intentarlo googlealo un poco a ver si esto sigue sirviendo, tengo idea que con algún cambio de versión pudo dejar de ser efectivo.

Si esto tampoco te sirve, te sugiero que preguntes en los foros en inglés, ya que al haber mayor cantidad de gente, puede que alguno haya tenido un problema similar.

Saludos,
Eduardo

---

### Post by ubudog on 2011-10-19
Aver si puedo decir eso en espanol...
Entre esto en el console (CTL>ALT>F1 desde la pantalla de login), para (quizas) arreglar su problema de .ICEauthority:
```
sudo chown tuusuario:tuusuario /home/tuusuario/.ICEauthority
```
(tuusuario es tu usuario personal, tu cuenta o sea si tu nombre en el computador es 'liv' entre liv)
- ubudog

---

### Post by guillermolisi on 2011-10-19
> **ubudog said:**
> Aver si puedo decir eso en espanol...
Entre esto en el console (CTL>ALT>F1 desde la pantalla de login), para (quizas) arreglar su problema de .ICEauthority:
```
sudo chown tuusuario:tuusuario /home/tuusuario/.ICEauthority
```
(tuusuario es tu usuario personal, tu cuenta o sea si tu nombre en el computador es 'liv' entre liv)
- ubudog
Has podido y muy bien ! :)

Gracias por la ayuda !

---

### Post by Liv~ on 2011-10-20
Bueno, no sé. Ya perdí la cuenta de la cantidad de cosas que probé y nada. Leí varias páginas tanto en inglés como español.
Probé lo de chown, de reinstalar gdm, de cambiar los permisos de /home, etc, y siempre es una de dos: o me dice "acceso denegado" o me dice que "el fichero o directorio no existe". A veces no dice nada siquiera. 
Me frustra demasiado no saber qué hacer, que nada funcione y no saber exactamente qué es lo que pasa.
Estoy tratando de evitarlo pero ya veo que voy a tener que reinstalar completamente de cero y perder las cosas que tenía en /home, viendo que ya reinstalé 3 veces conservando /home y todo sigue igual.

Por si sirve de algo, ésto es lo que dice cuando pongo ls -l /home (lo copié tal cual a mano, porque no tengo forma de hacer copy/paste ya que estoy en otra máquina):

drwx------ 2 root        root         16384 2011-08-16 17:08 lost+found
dr-x------- 2 marianne marianne   4096 2011-08-16 19:27 marianne

(marianne es mi usuario)

Gracias euzkoarima y ubudog (very good spanish!) por intentar ayudarme.

---

### Post by ubudog on 2011-10-20
Gracias!  :)

Bueno, si no tienes tus datos en el computador, yo recomiendo reinstalar y iniciar completamente de nuevo.  (O sea, formatear TODO, y reinstalarlo de nuevo)

En la instaladora de Xubuntu, en la parte de particionamiento, selecciona todo el disco.  

Eso va a formatear todo, y reinstalar Xubuntu completamente.

Si tienes datos que quieres salvar, pon los en un disco duro externo o algo asi.

:)

---

### Post by Liv~ on 2011-10-20
Entré con el live cd a ver si podía hacer un backup de mi /home para pasarla al otro disco que tengo, pero no... La carpeta con mi nombre de usuario aparece con una cruz y no me deja hacer nada. En las propiedades dice que el propietario es 1000 y tengo acceso completamente denegado.
Quiero al menos poder salvar la carpeta del aMule que está ahí dentro de /home, y poder pasarla a mi otro disco.
No hay alguna forma, alguna cosa, algo que pueda hacer desde el live cd para poder entrar a /home y copiarme esa sola carpeta aunque sea?

Si realmente no quedan opciones, terminaré haciendo la instalación completamente de cero, pero si hay una mínima posibilidad de poder salvar al menos algo de /home, quiero intentarlo antes de formatear por completo. No quiero darme por vencida aún!

---

### Post by euzkoarima on 2011-10-20
El usuario con id 1000 es el primero que se crea (típicamente TU usuario y con permisos de administración).
Supongo que con sudo (o sea, como root) deberías poder acceder.
Si es gnome (pre unity) con alt-F2 podías hacer "sudo nautilus" y te abría una ventana pero con permisos de root.

Saludos,
Eduardo

---

### Post by Liv~ on 2011-10-20
Abrí la terminal como root, como me dijiste, solo que en vez de nautilus puse thunar ya que estoy en xubuntu. Aparentemente localicé la carpeta/partición/directorio, como sea, de mi /home pero igual no puedo acceder. Cuando intento montar el directorio por terminal me dice: 

ERROR: Encrypted private directory is not setup properly.

Creo que eso es porque tengo que montarlo en /home/usuario, pero no sé cómo hacerlo.

Si me pudieras guiar un poco -si no es mucha molestia- te agradecería. Como verás no tengo mucha cancha con esto...

PD: probé lo de ecryptfs-recover-private pero parece que la passphrase que tengo guardada no es la correcta así que eso no va.

---

### Post by euzkoarima on 2011-10-20
Por el error que te da parece que tu home esta encriptado y el problema no sería de permisos, sino de la encriptación.
Si no te acordás la clave que usaste me parece que estamos al horno :(

Yo nunca encripte, así que no tengo experiencia en el tema.
Alguno en el foro que si ?

Saludos,
Eduardo

---

### Post by hictio on 2011-10-20
> **Liv~ said:**
> Entré con el live cd a ver si podía hacer un backup de mi /home para pasarla al otro disco que tengo, pero no... La carpeta con mi nombre de usuario aparece con una cruz y no me deja hacer nada. En las propiedades dice que el propietario es 1000 y tengo acceso completamente denegado.
Quiero al menos poder salvar la carpeta del aMule que está ahí dentro de /home, y poder pasarla a mi otro disco.
No hay alguna forma, alguna cosa, algo que pueda hacer desde el live cd para poder entrar a /home y copiarme esa sola carpeta aunque sea?

Si realmente no quedan opciones, terminaré haciendo la instalación completamente de cero, pero si hay una mínima posibilidad de poder salvar al menos algo de /home, quiero intentarlo antes de formatear por completo. No quiero darme por vencida aún!

Podrías probar algo como esto, por ejemplo, abrí un Terminal y tipeá:

```

sudo cp -R -v /home/tu.user/ /media/USB.drive/ ENTER

```

---

### Post by Liv~ on 2011-10-20
@euzkoarima: Sí, mi /home está encriptado. Cuando elegís encriptar, al iniciar el sistema por primera vez después de la instalación, te aparece un cartel que te dice la clave de encriptación que es un choclo de 32 caracteres entre diferentes números y letras. La tenés que guardar en un lugar seguro. Si alguna vez tenés un problema y necesitás acceder a tu /home encriptada (como mi caso ahora), podés seguir unos pasos para recuperarla y te va a pedir esa clave, la "encryption passphrase".

Yo tengo la frase guardada que es de la última vez que hice instalación de cero, o sea, creando una nueva /home, hace unos meses.
Se ve que como ahora hice reinstalación del sistema sin tocar /home, por alguna razón esa frase ya no me sirve. Y sin frase, no se pueden recuperar los datos encriptados... a menos que alguien los hackee? :rolleyes:

Así que creo que todo tiene más sentido ahora, haber probado varias cosas y que nada haya funcionado. No me queda mucho que hacer más que una fresh install que tampoco viene mal, solo me da un poco de fiaca tener que reconfigurar programas y demás. Pero lo vale. No cambio Linux por nada.
Y al menos aprendí nuevas cosas.


Muchas gracias de todas maneras a quienes me ofrecieron su ayuda :)

---

