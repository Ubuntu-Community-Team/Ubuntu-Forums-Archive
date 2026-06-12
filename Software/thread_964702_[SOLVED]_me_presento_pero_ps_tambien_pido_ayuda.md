---
title: "[SOLVED] me presento pero ps tambien pido ayuda"
date: 2008-10-31
forum: Software
---

### Post by sam_award on 2008-10-31
jejeje , mi nombre es alhef frias soy de mexico

pero ese no es el asunto jejeje

miren ya llevo tiempo usando ubuntu (no mucho solo lo nesesario jjejejeje)

bueno el caso es q hoy 30 de octubre del año en curso m actualize al intrepid ibex y ps m encuentro en un problemon , mas bien m encuentro dento del cubo , si , asi cmo lo escuchan dentro del mentado cubo , y no puedo salir cn nada, y ps queria saber si m pueden hechar una manita cn ese problemilla algo debo de haber hecho mal jejeje

bueno mi pc es una gateway 545 MX
prosesador : intel HT (bueno , no soy experto en eso)

---

### Post by sam_award on 2008-10-31
se m olvidaba ponel la pic jejeje

---

### Post by Afkael on 2008-10-31
ni idea.. pero empezaria por desactivar los efectos de compositing y reactivandolos..

---

### Post by santiagoward2000 on 2008-10-31
> **sam_award said:**
> jejeje , mi nombre es alhef frias soy de mexico

pero ese no es el asunto jejeje

miren ya llevo tiempo usando ubuntu (no mucho solo lo nesesario jjejejeje)

bueno el caso es q hoy 30 de octubre del año en curso m actualize al intrepid ibex y ps m encuentro en un problemon , mas bien m encuentro dento del cubo , si , asi cmo lo escuchan dentro del mentado cubo , y no puedo salir cn nada, y ps queria saber si m pueden hechar una manita cn ese problemilla algo debo de haber hecho mal jejeje

bueno mi pc es una gateway 545 MX
prosesador : intel HT (bueno , no soy experto en eso)

Bienvenido!
¿Te sentís encerrado en el cubo? JAJA!
Para "salir", abrí **compizconfig-settings-manager** (si no lo tenés instalalo, está en Synaptic con ese nombre) andá a **Desktop Cube**, y bajo la etiqueta **Behaviour** desmarcá **Inside Cube**.
Suerte!

_EDIT:_
Por las dudas aclaro que yo todavía no pude actualizar y sigo en Hardy, aunque me imagino que esa opción no cambió de lugar.

---

### Post by zeroadrenaline on 2008-10-31
Con el ultimo comentario solucionas tu problema perfectamente.Pero para proximas visitas fijate una cosita:
Por cada aplicacion que instalas, en tu home se crea un directorio .nombre_de_aplicacion en este caso .compiz .
Si alguna vez jugando con las configuraciones, tenes algun problema por el cual algo te estorba, y no sabes como vovler atraz, una solucion drastica pero efectiba es apretar ctrl + alt + F1 o 2 etc eso te mostrara una consola en pantalla, supongo que estaras familiarizado, logueas, y vas a estar en tu home/user de todas formas para confirmar podes hacer pwd eso te devuelve el directorio en el que te encontras. Por ultimo rm -R /home/user/.nombre_de_aplicacion en tu caso /home/user/.compiz .
Esto elimina la carpeta de configuracion, pero no la aplicacion, que significa esto, que no tenes que instalar de nuevo la pali, pero la tenes como cuando la instalaste, con la config "de fabrica digamos".
En general, cuando compiz, o kde4 me hinchan un poco los cocos, porque estube toqueteando, apelo a esto para volver a 0 la config y listo el pollo.
Un abrazo, y suerte con ese cubo!!.
PAZ!

---

### Post by sam_award on 2008-10-31
jejepa grax x la solucion , sabia q andaba el problemilla x ahi jejejej , pero jamas me di cuentade eso , santiagoward2000 de new thanks jijijiji ya tienes mivoto 
bueno chavos , los vere x las discuciones y ps ya quedo

una pregunta , aqui en este foro cmo pones solved , para q asi quede cerrado jejeje???

---

### Post by santiagoward2000 on 2008-10-31
> **sam_award said:**
> jejepa grax x la solucion , sabia q andaba el problemilla x ahi jejejej , pero jamas me di cuentade eso , santiagoward2000 de new thanks jijijiji ya tienes mivoto

Ya que estás podés hacer click en la medallita abajo de mi post ;)

> **sam_award said:**
> una pregunta , aqui en este foro cmo pones solved , para q asi quede cerrado jejeje???

Eh... vos! JEJE! Viste arriba del todo donde dice **Tread Tools**? Vas ahí y le ponés **Marked this thread as solved**.
Saludos!

---

### Post by sam_award on 2008-10-31
_EDIT:_
Por las dudas aclaro que yo todavía no pude actualizar y sigo en Hardy, aunque me imagino que esa opción no cambió de lugar.[/QUOTE]


para poder actualizar a ibes vete a origenes de software y en el apartado de actualizaciones cambia la opsion q dice ACTUALIZACION DE LA DISTRIBUCION marca :
ediciones normales , puesto q ibes es una normal y tu tienes una edicion de larga duracion , pues es x eso q no la puedes actualizar jeje , pero suerte , a  y despues de hacer esto escribes :

update-manager -d
y listo ahi la tienes , solo sigue los pasos jejeje santiagoward2000 y ya 

salu2

---

### Post by santiagoward2000 on 2008-10-31
> **sam_award said:**
> para poder actualizar a ibes vete a origenes de software y en el apartado de actualizaciones cambia la opsion q dice ACTUALIZACION DE LA DISTRIBUCION marca :
ediciones normales , puesto q ibes es una normal y tu tienes una edicion de larga duracion , pues es x eso q no la puedes actualizar jeje , pero suerte , a  y despues de hacer esto escribes :

update-manager -d
y listo ahi la tienes , solo sigue los pasos jejeje santiagoward2000 y ya 

salu2

Claro! Con un ancho de banda descente cualquiera! :lolflag:
Yo lo estoy bajando desde anoche, y todavía no termina...
(igual no quiero actualizarlo, estoy bajando el CD, voy a formatear e instalar de cero).
Gracias igual!
Saludos!

---

