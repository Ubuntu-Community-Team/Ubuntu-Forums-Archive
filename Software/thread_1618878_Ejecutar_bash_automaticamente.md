---
title: "Ejecutar bash automaticamente"
date: 2010-11-11
forum: Software
---

### Post by coolblood12 on 2010-11-11
Quiero ejecutar un bash automaticamente.

Que no salga el mensaje de "Run in Terminal" o "Display"

Segun esta pagina [http://guide.ubuntuforums.org/showthread.php?p=10101884#post10101884](http://guide.ubuntuforums.org/showthread.php?p=10101884#post10101884)

lo puedo hacer con un codigo que sale ahi, pero no se donde es que uno pone este codigo.


Gracias!,

---

### Post by sys.adm.og on 2010-11-11
Quieres ejecutar un script en bash?
opia tu script en /usr/local/bin/xyz , dale los permisos de ejecucion chmod 755 y ahi ya te va reconocer como comando interno! Al escribir xyz se va ejecutar tu script

---

### Post by coolblood12 on 2010-11-11
Realmente te agradesco tu pronta contestacion.
Soy nuevo en esto. Podrias ser un poco mas detallado.

Vengo del mundo de Windows y esto es completamente diferente para mi ;O)

Gracias!

---

### Post by Wiredfixer on 2010-11-11
pues mira... BASH es un interprete, asi que SIEMPRE se ejecuta al principio..

Ahora, que si lo que quieres es ejecutar un script al inicio...

¿Que quieres que haga? 
¿Ya intentaste en introducir el comando en "Aplicaciones de Inicio"?

Se mas especifico, explica completo tu caso y vemos como hacerlo.

---

### Post by coolblood12 on 2010-11-11
PROBLEMA: Yo utilizo una aplicacion para ejecutar PHP, Apache y MySQL. Esta aplicacion se llama XAMPP. Yo cree un bash para esta aplicacion. El bash que cree contiene un menu con 4 opciones.

NECESITO: Ejecutar el bash dandole doble click con el mouse, PERO que cuando yo le doy DOBLE CLICK sale un mensaje que da Run in Terminal, Display, Cancel, Run.

LO QUE QUIERO: Que cuando le de doble click al bash abra automaticamente como "Run in Terminal"

Hay una pagina en su foro Segun esta pagina [http://guide.ubuntuforums.org/showth...4#post10101884](http://guide.ubuntuforums.org/showth...4#post10101884)
que da una solucion. Pero dado a mi experiencia no se como hacerlo.

Gracias por la pronta contestacion! :O)

---

### Post by Wiredfixer on 2010-11-11
Este lo tienes que ejecutar de manera manual? 

la idea es que te lo habra con en MS-Dos no? que dabas doble click y no te preguntaba...

para esto, lo mas comodo sera que hagas un Launcher al bash, En escritorio, crea un launcher, solo especificalo como "Aplicacion de Terminal" , pones la ruta al archivo .sh que creaste (/home/usuario/script.sh) y ya..

Es lo mas simple si lo quieres hacer "On Demand".

---

### Post by coolblood12 on 2010-11-11
Excelente! ME FUNCIONO DE MARABILLA

GRACIAS!

---

