---
title: "Ausencia de tilde (acento) en Ubuntu 10.04"
date: 2010-05-02
forum: Software
---

### Post by Rolo linux on 2010-05-02
Hola:

He instalado Lucid Linux en mi notebook Toshiba M105-S3031, y no encuentro la forma de que aparezca la tilde (acento), en su lugar aparece este caracter: **{**
La portatil se compro en USA, asi que tiene el teclado con la disposicion para el idioma ingles.
Estuve buscando en google y nada. En opciones de teclado he probado varias opciones y tampoco soluciona el problema. El idioma elegido es "español - latinoamerica" y agregue el ingles (con este todo bien)
Vengo usando Ubuntu desde la version 9.04, luego 9.10 y ahora 10.104, instalacion limpia con un Cd, con particiones separadas para /, home y swap, sin mayor dificultad, Dual Boot con windows Xp. Como digo todo Ok, salvo este molesto problema de ausencia de la tilde. Posteo aca, donde compartimos el mismo idioma,en el foro en ingles no creo me presten mayor atencion.
Si alguien sabe la solucion a este problema o tienen una laptop Toshiba, agredeceria muchisimo su ayuda.

P.D. Con las distribuciones anteriores no tuve este problema.

Saludos.

---

### Post by hictio on 2010-05-02
Si el teclado está en inglés, lo más práctico creo yo es que habilites el layout de teclado que se llama "USA Alternative international", andá a:

System > Preferences > Keyboard > Layout tab

y agregá "USA Alternative international (former us_intl)".

Para tipear acentos tipeás la tecla "'" seguido de la vocal: á
Y para las eñes, Shift + "~" + n: ñ

Yo tengo todos los teclados con layout en inglés en mis máquinas, en lo personal me parece que es lo más práctico, y creo yo, se nota que que los comandos en Linux especialmente, se pensaron y crearon en un teclado en inglés, tienen más "sentido para los dedos" :)

---

### Post by Rolo linux on 2010-05-02
hola hictio

Gracias por la pronta respuesta, probé la sugerencia y funciona, lo de la tilde Ok lo que si es un garrón tener que usar tres teclas para poner la **ñ**, y aprender una nueva ubicación de los signos que vengo usando casi ya 4 años. El signo **¿ **se donde pueda estar en la versión inglesa ya que ellos no lo usan, y cambiar de u idioma a otro para construir un texto es tedioso. Por ahora me sirve, aunque creo que es un bug de Ubuntu o quizá un problema en la instalación, como comente antes no me sucedió con las versiones anteriores tampoco en otra Pc de escritorio, ni tampoco en Win Xp versión en inglés donde alterno ambos idiomas sin problema.

Una pregunta: que tipo de teclado tienes seleccionado? Yo lo he dejado por defecto: gestionado por evdev.

---

### Post by anch0 on 2010-08-27
Tenía el mismo problema. Justo ahora probé con "USA Alternative international (former us_intl)", funcionó los acentos pero se me perdió el signo "?" y comencé a probar con otros hasta que "España Incluir teclas Muertas" era el adecuado. :p

---

