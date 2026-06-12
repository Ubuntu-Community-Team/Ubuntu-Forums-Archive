---
title: "Instalar KDE 4.2.3 en Ubuntu 9.04"
date: 2009-05-31
forum: Software
---

### Post by emiliano_raso on 2009-05-31
Eso mismo. Lo que dice el titulo. Como hago? No encuentro los repositorios en Google ni como instalarlo.

En Wikipedia dice que es la ultima version estable. Es asi?

---

### Post by guillermolisi on 2009-05-31
> **emiliano_raso said:**
> Eso mismo. Lo que dice el titulo. Como hago? No encuentro los repositorios en Google ni como instalarlo.

En Wikipedia dice que es la ultima version estable. Es asi?
Si, es asi, es la ultima estable.

Para actualizar tenes que agregar un repositorio de Launchpad, un PPA:

```
Binary (.deb)
http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu jaunty main

```
La clave esta en 

```
http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x2836CB0A8AC93F7A

```
Si queres acceso directo a la nota de KDE:

[http://www.kubuntu.org/news/kde-4.2.3](http://www.kubuntu.org/news/kde-4.2.3)

---

### Post by Hei Ku on 2009-05-31
Acá está el anuncio de Kubuntu, con el PPA a agregar y de dónde sacar la clave GPG para verificar la integridad de los archivos.

[http://www.kubuntu.org/news/kde-4.2.3](http://www.kubuntu.org/news/kde-4.2.3)

Y dentro de poco esta saliendo la 4.2.4, creo que ya esta taggeada, o casi.

---

### Post by josecuervo86 on 2009-05-31
Que te parece esto: [http://s230070429.mialojamiento.es/kde-423-en-jaunty/]("http://s230070429.mialojamiento.es/kde-423-en-jaunty/")

Curso de Google a la derecha :P

---

### Post by emiliano_raso on 2009-05-31
Gracias gente... ahora me surge una duda:
Como agrego la clave?
Porque, por ejemplo, tengo este ejemplo de cuando instalaba WICD en 8.10
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

Pero en lo que josecuervo86 me pasó, la agrega asi:
```
gpg &#8211;keyserver keyserver.ubuntu.com &#8211;recv 2836CB0A8AC93F7A
gpg &#8211;export &#8211;armor 2836CB0A8AC93F7A | sudo apt-key add -
```

Ahi agrega directamente la clave, no?
Mucho del tema no cazo, por si no se dieron cuenta xD Jaja...

PD: Gracias josecuervo86 por el palazo con lo de Google. Era innecesario ^^

---

### Post by josecuervo86 on 2009-05-31
> **emiliano_raso said:**
> Gracias gente... ahora me surge una duda:
Como agrego la clave?
Porque, por ejemplo, tengo este ejemplo de cuando instalaba WICD en 8.10
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

Pero en lo que josecuervo86 me pasó, la agrega asi:
```
gpg –keyserver keyserver.ubuntu.com –recv 2836CB0A8AC93F7A
gpg –export –armor 2836CB0A8AC93F7A | sudo apt-key add -
```

Ahi agrega directamente la clave, no?
Mucho del tema no cazo, por si no se dieron cuenta xD Jaja...

PD: Gracias josecuervo86 por el palazo con lo de Google. Era innecesario ^^

De nada :P

En cuanto a como instalarlo, dado que estamos en presencia de dos grandes conocedores de KDE como Guillermo y Hei Ku, te recomendaria que siguieras las instrucciones de las paginas que te dieron ellos

---

### Post by Hei Ku on 2009-05-31
> **josecuervo86 said:**
> Que te parece esto: [http://s230070429.mialojamiento.es/kde-423-en-jaunty/]("http://s230070429.mialojamiento.es/kde-423-en-jaunty/")

Curso de Google a la derecha :P

> Try to avoid acronyms and jargon when giving instructions. New, or "green" users may not be able to follow you, and many will not ask you for an explanation in order to avoid looking stupid. **RTFM, "Go look on google" are two inappropriate responses to a question.** If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question. Politely showing someone how you searched or obtained the answer to a question is acceptable, even encouraged.

Extraido del codigo de conducta de los foros de Ubuntu. Para los que crean necesario leerlo o releerlo: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)


@Emiliano: Las dos formas son validas. Una inserta la clave directo desde internet y la otra baja un archivo y despues mete la clave del archivo al ring.

---

### Post by josecuervo86 on 2009-05-31
> **Hei Ku said:**
> Extraido del codigo de conducta de los foros de Ubuntu. Para los que crean necesario leerlo o releerlo: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Hoy no estoy para buenas, me voy a dormir....:(

---

### Post by emiliano_raso on 2009-05-31
> **Hei Ku said:**
> 
@Emiliano: Las dos formas son validas. Una inserta la clave directo desde internet y la otra baja un archivo y despues mete la clave del archivo al ring.

Hice lo que decia en la pagina, de agregarla como un archivo.
Igual si alguien puede explicar como se hace por consola (en terminos generales para saberlo para otros casos) estaria bueno :-P

Ahora tengo otro drama:
Yo no tenia instalado KDE de antes, entonces el Upgrade lo unico que me hace es actualizarme las aplicaciones xD
Como instalo el entorno?
Porque he visto tantas variantes: kubuntu-desktop, kde4, kde, kde-desktop, etc...

---

### Post by guillermolisi on 2009-05-31
> **emiliano_raso said:**
> Hice lo que decia en la pagina, de agregarla como un archivo.
Igual si alguien puede explicar como se hace por consola (en terminos generales para saberlo para otros casos) estaria bueno :-P

Ahora tengo otro drama:
Yo no tenia instalado KDE de antes, entonces el Upgrade lo unico que me hace es actualizarme las aplicaciones xD
Como instalo el entorno?
Porque he visto tantas variantes: kubuntu-desktop, kde4, kde, kde-desktop, etc...
Para, para .... lo vas a instalar arriba de otro KDE o junto con Gnome ?

Si es la ultima posibilidad, no te la recomiendo porque te va a "ensuciar" la estructura de menues. Despues no digas que no fuiste avisado ;)

---

### Post by emiliano_raso on 2009-05-31
> **guillermolisi said:**
> Para, para .... lo vas a instalar arriba de otro KDE o junto con Gnome ?

Si es la ultima posibilidad, no te la recomiendo porque te va a "ensuciar" la estructura de menues. Despues no digas que no fuiste avisado ;)

Lo hago todo el tiempo :-P Pero esta version de KDE me mató.
No uso los menúes (o como se escriba xD) .
Si, se que pasa. No tengo problema. Formateo la computadora 2 veces por semana de todas las cosas que le hago.

Tengo Gnome y LXDE. El OS instalado es Ubuntu, no Kubuntu.

---

### Post by josecuervo86 on 2009-06-01
> **guillermolisi said:**
> Para, para .... lo vas a instalar arriba de otro KDE o junto con Gnome ?

Si es la ultima posibilidad, no te la recomiendo porque te va a "ensuciar" la estructura de menues. Despues no digas que no fuiste avisado ;)

Eso es verdad, te va a llenar el menu con aplicaciones de KDE. Que hice yo? desde alacarte los oculte y santo remedio :D

---

### Post by Hei Ku on 2009-06-01
Entonces instala el paquete kubuntu-desktop. En ese va todo completo. Te va a cambiar hasta la pantalla de login.

---

### Post by josecuervo86 on 2009-06-01
> **Hei Ku said:**
> Entonces instala el paquete kubuntu-desktop. En ese va todo completo. Te va a cambiar hasta la pantalla de login.

y tambien el usplash (en mi caso, solo el de inicio)

---

### Post by emiliano_raso on 2009-06-01
> **Hei Ku said:**
> Entonces instala el paquete kubuntu-desktop. En ese va todo completo. Te va a cambiar hasta la pantalla de login.

Ok gracias. Barbaro.

Si si, se que te cambia todo. Hasta el loguito de carga con barra de progreso del booteo (no me acuerdo el nombre xD)

Formateo, instalo y desinstalo entornos a diestra y siniestra, pero de KDE 4.2.3 no encontraba como instalarlo :-P Ese es el tema.

Es asi que cuando tengo 4 o 5 entornos se empiezan a consumir entre ellos y es un caos total de todas las pruebas que hago (cambiar windows managers y demas) y termino formateando :-P

Gracias por la ayuda.

---

### Post by josecuervo86 on 2009-06-01
> **emiliano_raso said:**
> Si si, se que te cambia todo. Hasta el loguito de carga con barra de progreso del booteo (no me acuerdo el nombre xD)

Usplash

---

### Post by emiliano_raso on 2009-06-01
> **josecuervo86 said:**
> Usplash

esato'!
Recuerdo que habia una aplicacion para editarlo, usplash-manager creo que era o algo asi.
usplash-manager no es porque probé y no está :-P

---

### Post by SLA_leandrin on 2009-06-01
> **emiliano_raso said:**
> esato'!
Recuerdo que habia una aplicacion para editarlo, usplash-manager creo que era o algo asi.
usplash-manager no es porque probé y no está :-P

startup-manager me parece? alguna vez lo usé, sirve para bastante mas que cambiar el usplash.

---

### Post by emiliano_raso on 2009-06-01
> **SLA_leandrin said:**
> startup-manager me parece? alguna vez lo usé, sirve para bastante mas que cambiar el usplash.

Ese! Gracias!

---

### Post by Applelnx on 2009-06-09
Hola, estaba leyendo este thread porque tengo Ubuntu 9.04 y quiero pasar a Kubuntu 9.04. Segun vi tengo 2 opciones:

1) En Google lei que se podia hacer solo con poner en consola

```
sudo apt-get kubuntu-desktop
```

Es cierto esto? 


2) La otra opcion es hacer una tercera particion con Kubuntu, pasar todos los archivos desde Ubuntu, y despues eliminar esta ultima. No se si habra algun problema con el GRUB (?)


Personalmente, creo que es mejor la 2da opcion, me parece mas limpia, sobre todo porque no se que hace exactamente la primera. La unica duda que tengo es que pasa con el GRUB cuando elimino la particion de Ubuntu. Que me recomiendan?

PD: una tercera opcion podria ser grabar los archivos que necesite en un DVD y formatear la particion de Ubuntu, instalando Kubuntu ahi.

---

### Post by staar on 2009-06-09
mirá, la primera opción ```
sudo aptitude install kubuntu-desktop
```te instala KDE en el ubuntu que tenés ahora, y vos, al iniciar sesión (en la pantalla de login, en Opciones) podés elegir que escritorio iniciar, Gnome o KDE, el problema de esta opción es que se arma lio en los menus, porque uno toma los programas del otro y se arma una ensalada bárbara, pero con un poquito de toqueteo con el Editor de menú, queda bien, además, si no te gusta KDE, podés desinstalarlo con ```
sudo aptitude remove kubuntu-dektop
```

la segunda opción me parece un poco liada, y lenta...

si no te va la primera, andá por la tercera, que es algo extrema para probar un entorno de escritorio, pero si querés, es viable...

el GRUB está instalado en ubuntu, si le instalas kubuntu encima, el instalador de este lo va instalar de nuevo, no te hagas drama...

saludos

---

### Post by Air23 on 2009-06-09
> **Applelnx said:**
> Hola, estaba leyendo este thread porque tengo Ubuntu 9.04 y quiero pasar a Kubuntu 9.04. Segun vi tengo 2 opciones:

1) En Google lei que se podia hacer solo con poner en consola

```
sudo apt-get kubuntu-desktop
```

Es cierto esto? 


2) La otra opcion es hacer una tercera particion con Kubuntu, pasar todos los archivos desde Ubuntu, y despues eliminar esta ultima. No se si habra algun problema con el GRUB (?)


Personalmente, creo que es mejor la 2da opcion, me parece mas limpia, sobre todo porque no se que hace exactamente la primera. La unica duda que tengo es que pasa con el GRUB cuando elimino la particion de Ubuntu. Que me recomiendan?

PD: una tercera opcion podria ser grabar los archivos que necesite en un DVD y formatear la particion de Ubuntu, instalando Kubuntu ahi.
Tenes /home en una particion aparte (de /)?

Si es asi podes seguir usando la misma particion que usas como home en ubuntu instalando Kubuntu con un nombre de usuario distinto al que tenes en ubuntu (formateas tu actual particion / y la usarias como / de kubuntu pero no formateas tu actual /home)

---

### Post by Applelnx on 2009-06-09
Gracias por sus respuestas staar y Air23.

Air23, en cuanto a tu pregunta, tengo el directorio home en la misma particion (asi es por default creo, asi que prefiero hacer la que dice staar.

Saludos ;)

---

