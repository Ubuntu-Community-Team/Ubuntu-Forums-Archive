---
title: "OpenAl"
date: 2009-09-21
forum: Software
---

### Post by lucasgz on 2009-09-21
hola, estoy intentando instalar el juego Thunder and Lightning que es nativo de linux, el problema es que me dice que no tengo instalado OepnAl y no lo encuentro ni en synaptic  ni en la pagina oficial [http://connect.creativelabs.com/openal/default.aspx](http://connect.creativelabs.com/openal/default.aspx) 

encontre un archivo ,que no se si sera, pero no entiendo como instalarlo:confused: se llama 
openal-soft-1.8.466.tar.bz2

---

### Post by guillermolisi on 2009-09-21
> **lucasgz said:**
> hola, estoy intentando instalar el juego Thunder and Lightning que es nativo de linux, el problema es que me dice que no tengo instalado OepnAl y no lo encuentro ni en synaptic  ni en la pagina oficial [http://connect.creativelabs.com/openal/default.aspx](http://connect.creativelabs.com/openal/default.aspx) 

encontre un archivo ,que no se si sera, pero no entiendo como instalarlo:confused: se llama 
openal-soft-1.8.466.tar.bz2
Estas intentando instalar desde un .deb u otro formato de archivo ?

Desde donde bajaste la distribucion ?

---

### Post by lucasgz on 2009-09-22
ese archivo de openal lo baje de esta pagina [http://kcat.strangesoft.net/openal.html#overview](http://kcat.strangesoft.net/openal.html#overview) que la saque de la pagina del juego
no es .deb al descomprimirlo hay una carpeta que en la pagina explica algo de hacer cmake.. pero no entendi o no me salio
pero bue no se si esa es la forma de instalar openal:( 


Este es el error que me tira el juego al instalar:

Checking for required C library versions ... OK
Checking for Simple DirectMedia Layer (SDL) ... OK
Checking for OpenGL Graphics Toolkit ... OK
Checking for OpenAL Audio Toolkit ... failed
-------------------------------
Error: Package 'OpenAL Audio Toolkit' was found but was of the wrong version and the correct version could not be located.

[IV 0.0 for @openal.org/openal]

Error: Unable to prepare package Thunder and Lightning.


disculpen q no cree en la parte de software

---

### Post by guillermolisi on 2009-09-22
> **lucasgz said:**
> ese archivo de openal lo baje de esta pagina [http://kcat.strangesoft.net/openal.html#overview](http://kcat.strangesoft.net/openal.html#overview) que la saque de la pagina del juego
no es .deb al descomprimirlo hay una carpeta que en la pagina explica algo de hacer cmake.. pero no entendi o no me salio
pero bue no se si esa es la forma de instalar openal:( 


Este es el error que me tira el juego al instalar:

Checking for required C library versions ... OK
Checking for Simple DirectMedia Layer (SDL) ... OK
Checking for OpenGL Graphics Toolkit ... OK
Checking for OpenAL Audio Toolkit ... failed
-------------------------------
Error: Package 'OpenAL Audio Toolkit' was found but was of the wrong version and the correct version could not be located.

[IV 0.0 for @openal.org/openal]

Error: Unable to prepare package Thunder and Lightning.


disculpen q no cree en la parte de software
Tenes algun conflicto de versiones en el OpenAl Audio Toolkit.
Revisa los requerimientos del juego respecto de librerias y sus versiones.

Tambien tenes algun problema con paquetes de Thunderbird y Lightinig que habria que ver en detalle de que se trata, pero en otro thread porque este versa sobre OpenAL.

---

