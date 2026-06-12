---
title: "Ayuda , no puedo entrar en mi S.O.!!!!!"
date: 2008-10-08
forum: Software
---

### Post by darkarcangel_sam on 2008-10-08
miren , me estaba instalando el compiz fucion , y todo hiba bien , pero algo no m gusto y decidi borrarlo , y me puse a remover todo lo q habia instalado y a borrar todo lo q habia escrito en la terminal , de rrepente ya no podia abrir la terminal ni el reproductor ni nada , es como si hubiera borrado el S.O. por comleto y desgraciadamente se fue la luz en mi casa asi q cuando la volvi a prender cmo de costumbre ya no podia accesar , ya no tenia la pagina de entrada enonde se muestran los usuarios ni nada ,solo se queda la pantalla en negro pidiendome el nombre de usuario y la contraseña , lo peor es q se las escribo y me dice q hay error y no puedo hacer nada , nesecito mucho la ayuda , xfavor , no me dejen sin una respuesta , se q soy un novato y q la regue , pero porfavor ayudenme

---

### Post by santiagoward2000 on 2008-10-08
> **darkarcangel_sam said:**
> miren , me estaba instalando el compiz fucion , y todo hiba bien , pero algo no m gusto y decidi borrarlo , y me puse a remover todo lo q habia instalado y a borrar todo lo q habia escrito en la terminal , de rrepente ya no podia abrir la terminal ni el reproductor ni nada , es como si hubiera borrado el S.O. por comleto y desgraciadamente se fue la luz en mi casa asi q cuando la volvi a prender cmo de costumbre ya no podia accesar , ya no tenia la pagina de entrada enonde se muestran los usuarios ni nada ,solo se queda la pantalla en negro pidiendome el nombre de usuario y la contraseña , lo peor es q se las escribo y me dice q hay error y no puedo hacer nada , nesecito mucho la ayuda , xfavor , no me dejen sin una respuesta , se q soy un novato y q la regue , pero porfavor ayudenme

Hola!
¿Podrías decirnos qué estabas instalando y qué borraste? Compiz Fusion ya viene instalado en Ubuntu. ¿Estabas siguiendo alguna guía?
Saludos!

---

### Post by darkarcangel_sam on 2008-10-08
si , estaba siguiendo una guia de uno de los foros americanos , pero el compiz no m vino , se q suena rarao pero cuando lo busque en synamptic no estaba cn el cuadrito en verde , x eso lo estaba instalando , y de paso tambien estaba instalando el emerald pera tunear un poco , pero ya no m gusto q no podia activar los efectos visuales ni en normal ni experto , y entonses lo borre , y derrepente ya no podia abrir nada , y ni siquiera entrar a mi cuenta(por decirlo de alguna manera)

---

### Post by sergiom99 on 2008-10-08
voy a hacer una observacion que nunca esta de mas:
tenes 'BLOQ MAYUS' o 'CAPS LOC' activado?

---

### Post by darkarcangel_sam on 2008-10-08
si , pero no se cual sea el problema , no lo utilizo , si tu duda es q si escribo el usuario o la contraseña cn el teclado numerico , mi respuesta es no , escribo los numeros con los q estan ensima de las letras debajo de las teclas f1 etc.
y gracias x poner atencion en mi problema , es q ya estoy desesperado , y ya busq en otros foros y nada y pues tengo cosas importantes ahi

gracias

---

### Post by santiagoward2000 on 2008-10-08
Que raro que no haya estado instalado... ¿Qué versión usás? ¿Podés poner la dirección de la guía que usaste?
Sobre las cosas importantes, podés probar entrar desde el CD y copiar lo que necesites a un pendrive o algo así.

---

### Post by pol666 on 2008-10-08
compiz si staba instalado, no tenias que buscar nada. Solo Compiz-settings-manager. 


cuando inicias el sistema que te abre en consola, logueate como root


> sudo su


y hace un 

> dpkg-reconfigure xserver-xorg

segui las instrucciones, y reinicia. Si no pasa nada fijate haciendo un

startx y si tampoco pasa nada hace este.

> dpkg-reconfigure xserver-xfree86

Habiato otro reconfigure que lo use pero no me acuerdo cual era.

---

### Post by darkarcangel_sam on 2008-10-08
gracias pol666 lo intentare, no saben cmo c los agradesco , y ps si no funciona , de todos modos gracias

y tendre q reinstalar todo desde cero , el problema va ser reconfigurar lo del internet , GRACIAS

---

### Post by darkarcangel_sam on 2008-10-08
gracias pol666 lo intentare, no saben cmo c los agradesco , y ps si no funciona , de todos modos gracias

y tendre q reinstalar todo desde cero , el problema va ser reconfigurar lo del internet , GRACIAS

---

### Post by sergiom99 on 2008-10-08
lo que te decia mas arriba es que te fijes de no estar escribiendo usuario y contraseña con las mayusculas trabadas. Linux discrimina entre minusc/MAYUS.


> **darkarcangel_sam said:**
> 
y tendre q reinstalar todo desde cero , el problema va ser reconfigurar lo del internet , GRACIAS

Y si no tenes nada instalado todavia, esto va a ser lo mas facil tal vez. Con datos mas concretos de tu hard, podemos ayudarte a configurar la red.

No te preocupes que a mi tambien me paso de arruinar la primera instalacion (el video) y tener que reinstalarlo a los 2 dias.

---

### Post by darkarcangel_sam on 2008-10-08
jejeje , gracias x levantarme el animo , y gracias x la ayuda y la atencion prestada

---

### Post by darkarcangel_sam on 2008-10-08
gracias x los consejos pero tube q reinstalar todo el s.o. desde cero jaja
pero ps ahora aver si es q se puede hechenme una manita para instalar todos los codecs y demas jejej , pliss , GRACIAS

Sam

---

### Post by lega on 2008-10-08
instalar los codec multimedia es fácil,intenta reproducir un archivo multimedia y Ubuntu solito te va a preguntar si queres instalar los codecs necesarios para reproducirlo.

sino, más fácil aún tipeas en consola > sudo apt-get install ubuntu-restricted-extras y te instala los codecs, el flash y alguna cosita más [acá]("http://packages.ubuntu.com/hardy/ubuntu-restricted-extras") tenes el listado de lo que contiene el paquete

---

### Post by darkarcangel_sam on 2008-10-08
gracias x el paquetin lega , c agradece

---

