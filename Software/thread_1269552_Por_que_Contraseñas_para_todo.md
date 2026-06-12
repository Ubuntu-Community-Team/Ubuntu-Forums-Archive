---
title: "Por que Contraseñas para todo??"
date: 2009-09-18
forum: Software
---

### Post by juanma2228 on 2009-09-18
Buenas! Soy muy muy nuevo en esto del Ubuntu. En realidad lo estoy probando ya que por fin vencio la garantia de mi HP y pude desinstalar el maldito Vista que te enchufan a la fuerza. Pero tengo un problema:
El Ubuntu me pide contraseñas para cualquier cosa, ya me tiene medio podrido el temita de andar colocando la contraseña y queria saber si alguna manera de hacer que no me la pida mas.
Seria una pena dejar de usar este SO solo por eso, pero realmente me canso, es peor que el vista con esto de las consultas, en cualquier momento voy a querer ir al baño y me va a pedir la contraseña (ja!). Bueno, se agradecen las futuras respuestas.
Saludos

---

### Post by pablo.s on 2009-09-18
Las contraseñas que te pide
Ubuntu son acreditaciones de
identidad.
Veamos: Para poder configurar
archivos globales del sistema
tenés que ser superusuario. Si
no sos superusuario NO PODES
efectuar cambios fuera de tu /home.
Cada vez que te pide contraseña
lo que hace es pedir que te acredites
como superusuario. Si prestás un
poquito de atención las veces que
se produce esto es porque estás a
punto de modificar un archivo que
determina preferencias de uso de
algún programa esencial para el sistema.
Llamese actualizar los paquetes,
crear usuarios nuevos, modificar la
configuración de Internet, permisos,
y la lista sigue.
Espero que no te asustes por lo que
te cuento. los sistemas multiusuario
son asi. No solo Ubuntu.

---

### Post by juanma2228 on 2009-09-18
gRACIAS POR LA INFO, ENTONCES SEGUN VOS, PARECE QUE ESTO DE LA CONTRASEÑA SE VA ACABAR EN TANTO TERMINE DE ACTUALIZAR TODO? APARTE CADA VEZ QUE QUIERA MODIFICAR ALGO DE UN PROGRAMA ESCENCIAL PARA EL SISTEMA , POR EJEMPLO, EL ESCRITORIO?

---

### Post by pablo.s on 2009-09-18
No, modificar el escritorio
no es esencial para el sistema.
Y tampoco se va a terminar
cuando termines de actualizar,
porque salen actualizaciones
diariamente.
Es cuestión que lo tomes más
como algo que te protege a vos
mismo de accidentes y te protege
de los demás para que no accedan
a tu sistema. Es parte de la
seguridad REAL que tiene GNU/Linux.

---

### Post by Hei Ku on 2009-09-18
> **juanma2228 said:**
> gRACIAS POR LA INFO, ENTONCES SEGUN VOS, PARECE QUE ESTO DE LA CONTRASEÑA SE VA ACABAR EN TANTO TERMINE DE ACTUALIZAR TODO? APARTE CADA VEZ QUE QUIERA MODIFICAR ALGO DE UN PROGRAMA ESCENCIAL PARA EL SISTEMA , POR EJEMPLO, EL ESCRITORIO?

Por favor, evitá el uso de mayusculas. Son de mala educación.

Existen formas de configurar para que no te pida contraseñas, pero no estan recomendadas. Te pide contraseña sólo en el caso que queres modificar algo del sistema, que no debería ser común.

---

### Post by ALEXEX on 2009-09-18
en realida ubuntu si te pide algunas ocasiones la contraseña, pero como dicen es para un uso especifico de un nivel de la misma configuracion, pero no veo que sea algo nuevo o algo malo de ubuntu, en win2 tambien te pide en algunas ocasiones la del administrador, cuando quieres entrar a una pc, instalar algun programa, etc...
 
por lo tanto creo que la seguridad no me incomoda.

---

### Post by rober-mpp on 2009-09-18
Calculo que logueandote todo el tiempo como root en el entorno grafico deberias evadir los promps de password. 

Ahora bien, vas a estar corriendo absolutamente todo como root y vas a ser muy propenso a dan~ar el sistema.

No lo recomiendo para nada, pero si taaaannn cansado te tiene poner la password para actualizar el SO y conectarte a la red wifi, venga.

Saludos!!

---

### Post by Hei Ku on 2009-09-18
El ingreso como root esta desactivado, y por muy buenas razones.

---

### Post by pablo.s on 2009-09-18
Complemento lo que dice Hei Ku
con el dato siguiente:
Los tres sistemas operativos que
uso casi diariamente se utilizan
los "sudoers" (En Mac OS X, 
OpenSolaris y GNU/Linux), asi
que a esta altura es un requisito
obligatorio.

---

