---
title: "iniciar windows directo"
date: 2008-10-15
forum: Software
---

### Post by gonzalo4018 on 2008-10-15
Hola..

¿como puedo hacer para que se inicie directamente pero XP en vez de Ubuntu?
Otra cosa...
¿Puedo instalar Fedora arriba de Ubuntu? sin necesidad de formatear el disco? porque no tengo el CD de windows... Y porque no me anda la conexion a internet, no logro hacerla iniciar

---

### Post by majatu on 2008-10-15
> **gonzalo4018 said:**
> Hola..

¿como puedo hacer para que se inicie directamente pero XP en vez de Ubuntu?

Te recomiendo que como no tenes internet para instalarte el Administrador de arranque, entres en una terminal (aplicaciones/accesorios/terminal) y escribas:

sudo gedit /boot/grub/menu.lst

y escribas tu pass de root si lo tenes activado o tu pass de usuario normal con la que inicias Ubuntu.

Se te va a abrir un editor de textos, lo que tenes que hacer es previamente fijarte cuando arrancas la maquina y te aparece el menu para elegir al sistema operativo, que te fijes en que lugar de la lista tenes a Windows, tene en cuenta que el valor de Ubuntu por defecto es el 0 asi que tu segundo de la lista es en realidad el numero 1.

Modifica en el texto donde disce "Default 0" , pone el numero del lugar de Windows, si está 7mo, cambia el "0" por un "7".

guarda el archivo y listo, tendria que aparecerte marcado Windows la proxima vez que prendas tu pc.

> 
Otra cosa...
¿Puedo instalar Fedora arriba de Ubuntu? sin necesidad de formatear el disco? porque no tengo el CD de windows... Y porque no me anda la conexion a internet, no logro hacerla iniciar

En esta ya no te puedo ayudar, no tengo idea, pero quedate tranqui que ya te lo van a saber responder!

Un saludo y espero te ayude!

---

### Post by gonzalo4018 on 2008-10-15
Hola majatu, con lo que vos me explicaste, me apareceria Windows primero?
Mira.
En la pantalla del Boot me aparecen todas las opciones de Ubuntu (creo que son 3), Other Operative Sistem, y Windows XP professional edition. Lo que yo quiero es que Windows XP me aparezca primero en la lista, e inicie automaticamente cuando pasen los 10 segundos.

---

### Post by guisheca on 2008-10-16
> ¿Puedo instalar Fedora arriba de Ubuntu? sin necesidad de formatear el disco? porque no tengo el CD de windows... Y porque no me anda la conexion a internet, no logro hacerla iniciar
Esta parte no la entiendo bien, no te hace falta el cd de win para poder instalar fedora. Lo único que tenés que formatear es la partición donde está el ubuntu para instalar fedora, el win queda intacto.
Con respecto a lo de arriba, lo que va a hacer lo que te dijo majatu es que la opción para ingresar a win esté selecionada por defaul, así despues de pasados los 10 segundos empieza win.
Saludos.

---

### Post by gonzalo4018 on 2008-10-16
Gracias, ya solucione lo de windows, esta por defecto para iniciarse!, es hasta acostumbrarme a Linux, seguramente si me va de 10 saco Windows, pero por ahora no me puedo despegar de el :S


Y con respecto a lo del disco, lei por ahi que se necesita el cd de windows, cuando desinstalo ubuntu, para recuperar las particiones o algo asi... no se si sera asi

---

### Post by guisheca on 2008-10-16
> Y con respecto a lo del disco, lei por ahi que se necesita el cd de windows, cuando desinstalo ubuntu, para recuperar las particiones o algo asi... no se si sera asi

Para quitar ubuntu y quedarte con fedora lo unico que tenés que hacer es, en la instalación de fedora, elegir la partición donde está el ubuntu para instalarla, eso formatea la partición donde está ubuntu y te quedás con fedora en ves de ubuntu.
No te hace falta el cd de win. Lo que si hace falta es el cd de alguna distribución en el caso de reinstalar win, ya que eso te borra el grub y te quedás sin acceso a linux y con el cd de casi cualquier distribución arreglás ese problema.

---

### Post by santiagoward2000 on 2008-10-16
> **gonzalo4018 said:**
> Y con respecto a lo del disco, lei por ahi que se necesita el cd de windows, cuando desinstalo ubuntu, para recuperar las particiones o algo asi... no se si sera asi

Sí, es casi verdad eso. Cuando instalás Ubuntu, te instala el GRUB en el MRB, encima del arranque de Windows, entonces si querés desistalar Ubuntu hay que recuperar el de Windows. Supuestamente se puede hacer con el cd de Windows (personalmente no me anduvo). Pero hay otros programas que podés bajar (ahora no tengo el nombre, pero por ahí leí que había uno).
Igual eso es si querés dejar solo Windows. Si instalas otra distro, te va a instalar su arranque y no hace falta recuperarlo.
Saludos!

_EDIT:_
Lo encontré: [http://www.ubcd4win.com/]("http://www.ubcd4win.com/")
Aunque aclaro que no lo usé nunca...

---

### Post by majatu on 2008-10-16
me alegro de que te ayudase lo que te pase ;)

ahora, si sacas windows y queres arreglar el arranque me parece que es mejor usar el Super Grub Disk que viene con menues en español y es bastante entendible (arranca en ingles y lo podes cambiar una vez andando a español).

Se puede bajar desde la web oficial:

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

Un saludo!

---

### Post by gonzalo4018 on 2008-10-16
Joya che, me viene al pelo...
Gracias

---

