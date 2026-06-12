---
title: "Configurar Visual 2005 y mysql en VirtualBox"
date: 2009-06-30
forum: Software
---

### Post by mario2130 on 2009-06-30
Antes que me digan por que esta en visual y por que no uso mono, bueno es que no es un proyecto mio y tengo que trabajarlo en Visual

bueno la duda radica en que instale VirtualBox instale Visual 2005 y mysql y cuando trato de hacer la conexion a la base de dato no puedo realizarla.
Ahora este conexion esta testeada en windows y corre bien.

LA pregunta, Alguien a trabajado en esta situación? y logrado configurar correctamente mysql sobre virtualbox.

Yo averiguando se me ocurre la posibilidad de levantar el servidor en ubuntu y luego conectar visual a este servidor. (cosa que tampoco e podido realizar) pero me tinca que es mas factible de esta manera.

saludos

---

### Post by moreback on 2009-06-30
¿Al final es un MySQL en Windows? ¿Revisaste si estaba corriendo el servicio de MySQL? ¿Revisaste si estaba configurado el MySQL para aceptar conexiones y qué métodos de autenticación estaban habilitados?

Yo creo que la cosa va por ahí.

Saludos.

---

### Post by mario2130 on 2009-06-30
> **moreback said:**
> ¿Al final es un MySQL en Windows? 
Claro los primero que trato de probar es que si efectivamente puedo conectar mysql y visual studio 2005, pero no olvidar que estan ambos corriendo en virtualbox

> **moreback said:**
> ¿Revisaste si estaba corriendo el servicio de MySQL?
Si, entro en Mysql Adminitrador y puedo verificar que esta todo corriendo, es más levanto el script y en el Query puedo hacer consultas a la base de dato, feliz de la vida.

> **moreback said:**
>  ¿Revisaste si estaba configurado el MySQL para aceptar conexiones y qué métodos de autenticación estaban habilitados?

Si instale nuevamente mysql para modificar todos los permisos y dejar todas las conexiones listas

El problema radica (para aclarar más el asunto), que:
1) Visual studio 2005 se instaldo y funciona perfectamente
2)mysql se instaldo perfectamente, levantando scrip y haciendole consultas normales
3)Todo esta en wintendo corriendo en virtualbox
4) PEro a la hora de hacer la conexion, tal como se hace en windows instalado normalmente, esta conexion no funciona.

Es un tema de conexion, y para más claridad esta conexión esta requete probada en windows (repito instaldo normalmente), pero no reacciona = en la virtualización.

e hay el meollo del asunto


_____________________________________
edito por nuevas pruebas:

el mensaje de error por la conexion es:
"Unable to connect any of the specified MySQL hosts."

logre conectar mysql de ubuntu hacia windows(virtualizado), pero no puedo conectar al reves yo creo que apenas pueda hacer esa conexion. me lanzo jajaj
saludos

---

### Post by moreback on 2009-06-30
Yo creo que habría que ver cómo te conectas con el Visual Basic para ver que estás haciendo mal.

---

