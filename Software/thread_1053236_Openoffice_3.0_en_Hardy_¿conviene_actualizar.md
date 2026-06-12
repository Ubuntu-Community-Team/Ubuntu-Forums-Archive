---
title: "Openoffice 3.0 en Hardy ¿conviene actualizar?"
date: 2009-01-28
forum: Software
---

### Post by rojojuan on 2009-01-28
Estoy usando Hardy Heron. Quise actualizar a Openoffice 3.0 desde 2.4, coloqué los repositorios correspondientes y la clave gpg. Actualicé como lo propone Synaptics.
 Aparecen en actualización de software los paquetes para instalar, pero salta una leyenda que dice que se trata de paquetes no autenticados.
Estuve leyendo en Internet que ese cartel aparece porque Ubuntu todavía no lo registró y que se puede instalar sin ningún problema.
Todo esto me ofrece dudas.
Conviene actualizar o esperar hasta que aparezca la actuación en Hardy?

---

### Post by edd07 on 2009-01-28
Ese letrero aparece cuando hay problemas con la clave gpg que obtuviste (y por lo tanto no se puede autentificar). En teoría, alguien podría interceptar tu descarga y darte un archivo malicioso, y no podrías comprobar si es el auténtico o no. Pero en la práctica, no creo que haya problema, yo tengo algunos repositorios sin clave GPG y no he tenido dificultades. 

Acerca de si vale la pena actualizar el OO.org, yo te diría que no. No noté ninguna mejora significativa y solo me causó problemas de manejo de paquetes y de integración con GNOME. Pero yo lo instalé por otro método, entonces lo último puede que no aplique para ti.

Y no estoy seguro de que los paquetes oficiales aparezcan en Hardy, ya que Ubuntu nunca actualiza las versiones del software en un "release", solo actualizaciones de seguridad. Con mayor razón siendo LTS.

Espero que te sea útil

---

### Post by rojojuan on 2009-01-28
> **edd07 said:**
> Ese letrero aparece cuando hay problemas con la clave gpg que obtuviste (y por lo tanto no se puede autentificar). En teoría, alguien podría interceptar tu descarga y darte un archivo malicioso, y no podrías comprobar si es el auténtico o no. Pero en la práctica, no creo que haya problema, yo tengo algunos repositorios sin clave GPG y no he tenido dificultades. 

Acerca de si vale la pena actualizar el OO.org, yo te diría que no. No noté ninguna mejora significativa y solo me causó problemas de manejo de paquetes y de integración con GNOME. Pero yo lo instalé por otro método, entonces lo último puede que no aplique para ti.

Y no estoy seguro de que los paquetes oficiales aparezcan en Hardy, ya que Ubuntu nunca actualiza las versiones del software en un "release", solo actualizaciones de seguridad. Con mayor razón siendo LTS.

Espero que te sea útil

Muchas gracias por una respuesta tan rápida. La clave la obtuve en launchpad, pero evidentemente no funciona.
Te agradezco las opiniones y en base a ellas voy a quedarme con la 2.4 por ahora.
Hasta pronto...

---

### Post by guillermon on 2009-01-29
> **rojojuan said:**
> Muchas gracias por una respuesta tan rápida. La clave la obtuve en launchpad, pero evidentemente no funciona.
Te agradezco las opiniones y en base a ellas voy a quedarme con la 2.4 por ahora.
Hasta pronto...

   Yo me doy el permiso de opinar que el paso de openoffice 2.4 a 3.0 ha tenido algunos aspectos importantes, y que en mi caso me vinieron bien. Destaco el hecho de  poder intercambiar con archivos docx o office2007; aspecto visual (me gusta más), los pps no tienen errores...
   La instalación desde el sitio oficial no me resultó dificil...

Saludos
Guillermo

---

### Post by ubuntu27 on 2009-01-29
Hola OP (rojojuan). Osea que instalaste OpenOffice.org 3 desde [PPA]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") pero te da errores de autenticacion.

Lo que tienes que hacer es agregar la llave OpenPGP a apt. No a tu PGP personal.


Como hacerlo:

1) Ir a la pagina [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) 

2) Esocoge tu version de Ubuntu

3) [Saltar si ya lo has hecho] Agregar repositorios

4) Click en el link de una coleccion de letras y numeros como " D2BB86E0EBD0F0A43D4DB3A760D11217247D1CFF"

5) Click en el KeyID como "47D1CFF"

6) Abrir un procesador de texto como Gedit

7) Copiar todo el text COMENZANDO desde 

"-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10


hasta 

-----END PGP PUBLIC KEY BLOCK-----





8) Guardar como xxx.key   donde xxx puede ser cualquier nombre. Ejemplo "OpenOffice.key"


9) Abrir Software Sources en el menu Administracion

10) Escribe tu constrasenya

11) Click en la tabla "Autenticacion"

12) Click en "Importar Archivo Key"

13) Escoge el archivo que acabas de guardar (OpenOffice.key)

14) Click ok

15) Actualiza la lista de repositorios.

---

### Post by guillermon on 2009-01-30
Yo en su momento lo que leí es que lo recomdable era desintalar primeramente 2.4; eliminar los repositorios, y luego instalar 3.0. Inclusive había un ítem para los íconos... Yo de esa forma no he tenido ningún problema... ¿será este el problema?
   Saludos

---

### Post by rojojuan on 2009-01-31
> **ubuntu27 said:**
> Hola OP (rojojuan). Osea que instalaste OpenOffice.org 3 desde [PPA]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") pero te da errores de autenticacion.

Lo que tienes que hacer es agregar la llave OpenPGP a apt. No a tu PGP personal.


Como hacerlo:

1) Ir a la pagina [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) 

2) Esocoge tu version de Ubuntu

3) [Saltar si ya lo has hecho] Agregar repositorios

4) Click en el link de una coleccion de letras y numeros como " D2BB86E0EBD0F0A43D4DB3A760D11217247D1CFF"

5) Click en el KeyID como "47D1CFF"

6) Abrir un procesador de texto como Gedit

7) Copiar todo el text COMENZANDO desde 

"-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10


hasta 

-----END PGP PUBLIC KEY BLOCK-----





8) Guardar como xxx.key   donde xxx puede ser cualquier nombre. Ejemplo "OpenOffice.key"


9) Abrir Software Sources en el menu Administracion

10) Escribe tu constrasenya

11) Click en la tabla "Autenticacion"

12) Click en "Importar Archivo Key"

13) Escoge el archivo que acabas de guardar (OpenOffice.key)

14) Click ok

15) Actualiza la lista de repositorios.

Gracias por la respuesta, esto lo hice, comprobé que la gpg estaba agregada y sin embargo Hardy no la reconoce.
Seguí averiguando y parece que es problema de launchpad que todavía no terminó de trabajar con las claves.

---

### Post by NickCis on 2009-02-01
Yo cuando intente actualizar, (usando los repositorios de ubuntu), desinstale el 2.4, y pudeinstalar perfectamente el 3, el problema es que me dejo de andar el sonido en el OO, era un supuesto problema con la maquian virtual de java (antes en la 2.4 me andaba perfecto), volvi a instar al jvm, y todo eso... y seguia sin andar, por eso volvi a la 2.4...

Saludos...

---

### Post by rojojuan on 2009-02-02
> **NickCis said:**
> Yo cuando intente actualizar, (usando los repositorios de ubuntu), desinstale el 2.4, y pudeinstalar perfectamente el 3, el problema es que me dejo de andar el sonido en el OO, era un supuesto problema con la maquian virtual de java (antes en la 2.4 me andaba perfecto), volvi a instar al jvm, y todo eso... y seguia sin andar, por eso volvi a la 2.4...

Saludos...

Gracias por la respuesta. Seguiré por todo lo dicho aquí con la 2.4...más adelante veremos qué soluciones aparecerán.

---

