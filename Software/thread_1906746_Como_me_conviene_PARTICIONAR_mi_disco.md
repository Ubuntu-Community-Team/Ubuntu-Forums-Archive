---
title: "Como me conviene PARTICIONAR mi disco?"
date: 2012-01-09
forum: Software
---

### Post by horacio_chiarella on 2012-01-09
Cómo andan todos!

Les comento que compré una nueva PC, y la misma tiene un disco de 500 gb. Ese disco ya vino particionado en dos: una parte de 32 gb se lo lleva el "recovery" donde tengo drivers, soft, bla bla bla, que me vino con la pc; y 434 lo tengo para windows. 

Ahora bien, mi idea es instalar Ubuntu. Debería hacer una partición "/", que sea la base para el sistema, y el cuarto hacerlo extendido para poner tres particiones lógicas, una swap, y la otra "/home" para documentos y configuración de programas, y una tercera (la más grande de todas) en formato ntfs para compartir archivos entre los dos sistemas operativo. 

Con esta disposición irían juegos en la de windows, música y otros documentos en última lógica.

Ahora bien. Me gustaría saber: 
1. Qué les parece esta disposición? 
2. el disco de "recovery" de 30 gb, se puede ampliar, y subdividirlo en dos particiones lógicas para poner ahí el ntfs de intercambio? Sirve de algo o en esencia es lo mismo que la división anterior? 
3. A los juegos los pongo en windows, o los pongo en la ntfs para ambos sistemas? 
4. Se les ocurre alguna división mejor?
5. Todas estas divisiones se pueden hacer con la primer etapa de la instalación de UBUNTU , no?


Muchas gracias y perdón por las molestias!

---

### Post by SSNova on 2012-02-06
Hola Horacio

 Lo que yo haría es ampliar la partición de recovery y ahi utilizarlo para backup y todos los archivos que quieras compartir como música y películas. Me parece que subdividirla sería incómodo. Los juegos tambien los podrías instalar ahi pero si la idea es "compartirlos" y correrlos con wine desde Ubuntu, hasta donde tengo entendido no es posible.
Luego tenés que tener una partición para windows y una más para Ubuntu, no es necesario dejar una partición para swap ya que esto se hace automáticamente durante la instalación.
Por último la creación de las particiones la podés hacer durante la instalación o desde un live cd/usb con gparted.

---

