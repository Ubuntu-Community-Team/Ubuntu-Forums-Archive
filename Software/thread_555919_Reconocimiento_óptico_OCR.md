---
title: "Reconocimiento óptico OCR"
date: 2007-09-20
forum: Software
---

### Post by rojojuan on 2007-09-20
Hola a todos.
Alguien tiene experiencia con OCR en Ubuntu? Anduve tratando de hacer algo con  Gocr y Tesseract, pero el resultado que obtengo es desastroso. Aclaro que uso scanimage porque tengo un scanner canon que no funciona con el entorno gráfico (Gimp and company). Pero sí, logro obtener buenas imagenes pero el OCR es malo. Me parece que la cosa no esta muy adelantada en Linux, pero en fin, puede ser solamente mi desconocimiento.
Gracias desde ya por la ayuda.

---

### Post by leo_rockway on 2007-09-20
la verdad que mucha idea de scanners en linux no tengo xq el scanner que tengo esta en la otra maquina y todavia no la pase a linux (sigue con xp).

de todas formas me intereso tu consulta porque incluso en windoze se me complico encontrar algun buen ocr (hasta que encontre el finereader).

buscando en los repositorios encontre otros dos ocr: ocrad y clara. quizas puedas probarlo y comparar los resultados.

avisa si alguno te da buenos resultados asi aprendo de tu experiencia y se me hace mas facil despues pasar la otra compu a linux.

---

### Post by rojojuan on 2007-09-21
> **leo_rockway said:**
> la verdad que mucha idea de scanners en linux no tengo xq el scanner que tengo esta en la otra maquina y todavia no la pase a linux (sigue con xp).

de todas formas me intereso tu consulta porque incluso en windoze se me complico encontrar algun buen ocr (hasta que encontre el finereader).

buscando en los repositorios encontre otros dos ocr: ocrad y clara. quizas puedas probarlo y comparar los resultados.

avisa si alguno te da buenos resultados asi aprendo de tu experiencia y se me hace mas facil despues pasar la otra compu a linux.

Por los datos que encontré funcionan igual de regular. Estoy viendo que Google esta trabajando en el tema. Seguiré indagando y te comento que pasa.

---

### Post by leo_rockway on 2007-09-21
quizas esto te interese:

[http://appdb.winehq.org/appview.php?iVersionId=4598&iTestingId=11376](http://appdb.winehq.org/appview.php?iVersionId=4598&iTestingId=11376)

aunque a mi siempre me gusta mas una solucion gnu.

---

### Post by rojojuan on 2007-09-22
> **leo_rockway said:**
> quizas esto te interese:

[http://appdb.winehq.org/appview.php?iVersionId=4598&iTestingId=11376](http://appdb.winehq.org/appview.php?iVersionId=4598&iTestingId=11376)

aunque a mi siempre me gusta mas una solucion gnu.

Concuerdo totalmente. Sigo buscando y esperando que el software que desarrolla Google este listo para Ubuntu!!

---

### Post by hernan blau on 2007-09-22
Mirá, yo probé casi  todos los ocr disponibles.  Ninguno es satisfactorio. Estamos a la espera del prometido ocropus de google. Suerte

---

### Post by rojojuan on 2007-09-23
> **hernan blau said:**
> Mirá, yo probé casi  todos los ocr disponibles.  Ninguno es satisfactorio. Estamos a la espera del prometido ocropus de google. Suerte

Sí, llegamos a la misma conclusión! Si tenés algún dato de Google, pasalo, así nos vamos enterando. Hasta la próxima.

---

### Post by rojojuan on 2009-11-03
Le dejo esta novedad para quienes esten interesados en OCR.
Al menos para mi fue una sorpresa y mi propósito es hacerles conocer a quienes no estan muy informados sobre el tema que después de un largo tiempo Tesseract mejoró mucho.
Es más, se integra con Gnome y posibilita escanear y correrlo directamente  con soporte para idioma español.
El resultado es muy bueno, con pocos errores.
No quiero ser pesado y si a alguien le interesa la cuestión, sigo con la forma de instalarlo, etc.
Ah, lo estoy corriendo en Karmic sin problemas.

---

### Post by chronos00 on 2009-12-11
> **rojojuan said:**
> Le dejo esta novedad para quienes esten interesados en OCR.
Al menos para mi fue una sorpresa y mi propósito es hacerles conocer a quienes no estan muy informados sobre el tema que después de un largo tiempo Tesseract mejoró mucho.
Es más, se integra con Gnome y posibilita escanear y correrlo directamente  con soporte para idioma español.
El resultado es muy bueno, con pocos errores.
No quiero ser pesado y si a alguien le interesa la cuestión, sigo con la forma de instalarlo, etc.
Ah, lo estoy corriendo en Karmic sin problemas.

Hola!

En tu post comentas que Tesseract tiene una integracion con gnome; como es esto? Solo encontre un comando de consola al instalar este paquete. Como logro usarlo desde la interfaz grafica?
Gracias!

---

### Post by rojojuan on 2009-12-12
Tenés que instalar gscan2pdf que está en los repositorios. Este programa se integra a Aplicaciones - Gráficos. 
Una vez instalado lo corrés, y el el seteo le indicás que el OCR lo haga a través de Tesseract (que obviamente ya lo tenés instalado). Además de instalar Tesseract, tenés que instalar teseeract-ocr-spa, que es para idioma español.
Suerte y si tenés alguna otra duda que uyo pueda evacuar, dale comás.




> **chronos00 said:**
> Hola!

En tu post comentas que Tesseract tiene una integracion con gnome; como es esto? Solo encontre un comando de consola al instalar este paquete. Como logro usarlo desde la interfaz grafica?
Gracias!

---

### Post by chronos00 on 2009-12-12
EXCELENTE APLICACION!!

Yo venia usando el XSane para escanear imagenes, y me resultaba muy antiestetico e incomodo. Esta nueva aplicacion es realmente una bendicion!

Muchisimas gracias!

Una ultima pregunta:
En preferencias puedo seleccionar diferentes "frontend". Cual me conviene elegir? Cual es la diferencia entre cada uno?

---

### Post by euzkoarima on 2009-12-12
> **rojojuan said:**
> Tenés que instalar gscan2pdf que está en los repositorios. Este programa se integra a Aplicaciones - Gráficos. 
Una vez instalado lo corrés, y el el seteo le indicás que el OCR lo haga a través de Tesseract (que obviamente ya lo tenés instalado). Además de instalar Tesseract, tenés que instalar teseeract-ocr-spa, que es para idioma español.
Suerte y si tenés alguna otra duda que uyo pueda evacuar, dale comás.

Buenísimo, en cuanto el laburo me deje volver a tener vida propia lo pruebo en casa.

Gracias,
Eduardo

---

### Post by rojojuan on 2009-12-12
> **chronos00 said:**
> EXCELENTE APLICACION!!

Yo venia usando el XSane para escanear imagenes, y me resultaba muy antiestetico e incomodo. Esta nueva aplicacion es realmente una bendicion!

Muchisimas gracias!

Una ultima pregunta:
En preferencias puedo seleccionar diferentes "frontend". Cual me conviene elegir? Cual es la diferencia entre cada uno?

Mirá libsane me parece que corresponde a Xsane; scanimage es otro programa de escaneo que alguna vez tuve instalado. Libsane lo colocó el programa por efecto y anda bien. Las diferencias -fuera de lo dicho- no las conozco.
Gscan2pdf me cambió la forma de trabajar!!!!
Suerte!

---

