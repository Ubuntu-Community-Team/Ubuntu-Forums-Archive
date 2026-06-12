---
title: "Usuarios, politicas y permisos en Ubuntu???"
date: 2010-01-27
forum: Software
---

### Post by shingo630 on 2010-01-27
Hola, este es mi primer posteo en el foro, y básicamente es un planteo sobre mi experiencia reciente con Ubuntu.
  Lo instale dentro de mi trabajo, básicamente para probarlo y ver hasta donde podia interactuar con nuestra red y programas.:p
  La verdad que es prácticamente perfecto para el usuario promedio, es tan APB que realmente sentís que no tenes que explicarle 5 mil veces a los usuarios como poner un pie de pagina en Office.:rolleyes:
  Si bien desde el punto de vista funcional es mas que eficaz (excepto por la nula ejecución de programas para Windows que están tan mal hechos que ni el Wine los levanta:tongue:), pero el mas grande de los retos es que respete los permisos que el Active Directory otorga a los diferentes grupos de usuarios.8-)
  Si bien logre que se pudieran ingresar a la computadora los usuarios dentro del AD, no puede lograr que los permisos de este fueran respetados. Osea, quienes dentro del AD son administradores tenían los mismos permisos que los usuarios comunes dentro de Ubuntu.](*,)
  Al navegar por carpetas de red me di cuenta que igualmente los permisos estaban vigentes, ya que si bien estaba usando Ubuntu las maquinas por las que navegaba tienen Windows XP, y pude ver que con usuarios administradores podía ingresar a carpetas en los equipos que con usuarios comunes no.:!:
  Se bien que el echo de que no me tome los permisos es por la diferencia de arquitecturas, mi pregunta es si existe algún programa para hacerlos vigentes dentro del equipo y que por ejemplo los administradores con sus clave puedan acceder a privilegios de administrador dentro de Ubuntu para cambiar configuraciones e instalar programas y que los usuarios rasos solo puedan usar la computadora para trabajar.:-k
  Bueno eso es todo por ahora, dejo esa inquietud, si alguno menciona el paquete Likewise Open, les comento que gracias a este pude hacer que los usuarios de mi AD de Windows se loguearan pero no que respete los permisos.
  [FONT=&quot]Saludos! \\:D/[/FONT]

---

### Post by quedefantasma on 2010-01-27
Hola shingo630, fijate si la info que me pasaron en este thread te sirve como guía para algo...[http://ubuntuforums.org/showthread.php?p=8196130#post8196130](http://ubuntuforums.org/showthread.php?p=8196130#post8196130)

> **quedefantasma said:**
> Me queda un problema por resolver...

Hasta ahora todo parece correr bien salvo por el detalle de que cada vez que inicio/reinicio el sistema tengo que ejecutar manualmente el comando KINIT. Para que cuando ingreso a las carpetas compartidas de los equipos WIN no me pida la contraseña....

Calculo que es algun problema con PAM.D o algo asi...

Si alguien tiene algun dato, sera agradecido...

Slds.:D

Me interesa mucho este tema, yo también arranque haciendo pruebas en el trabajo y me dio la misma buena impresión que a vos para con los usuarios básicos...(sin mencionar que seria una solución excelente a las famosas licencias..)

Me quedo suscrito a este tema para ver si se avanza algo...SLDS!

---

### Post by shingo630 on 2010-01-28
Estu biendo tu threatd y veo que vos tubiste los mismos problemas que yo al inicio, luego encontre la forma de instalar las maquinas de forma sencilla en mi dominio, primero instale ubuntu 9.1 y lo actualice, luego instale el samba y con esta erramienta cambie la pc a mi doninio o grupo de trabajo (ya con esto la pc estaba registradad en el Active Directory).
Luego utilice el Likewise Open, operandolo desde el terminal, aca te dejo como lo ejecute yo para que anduviera.
> 
This is a second version of [this other guide]("http://anothersysadmin.wordpress.com/2007/08/03/active-directoy-authentication-with-ubuntu/") that applied to previous Ubuntu versions.
Since Ubuntu 8.04 (Hardy Heron), and now Ubuntu 8.10 (Intrepid Ibex) it come the [Likewise Open]("http://www.likewisesoftware.com/products/likewise_open/") package that makes basic Active Directory authentication in Ubuntu a breeze.
 Just follow these steps:
 
[LIST=1]
[*][FONT=Courier New]sudo apt-get update[/FONT]
[*][FONT=Courier New]sudo apt-get install likewise-open[/FONT]
[*][FONT=Courier New]sudo  domainjoin-cli join fqdn.of.your.domain Administrator[/FONT]
[*][FONT=Courier New]sudo update-rc.d likewise-open defaults[/FONT]
[*][FONT=Courier New]sudo /etc/init.d/likewise-open start[/FONT]
[/LIST]
 and you can now log into your machine using your DOMAIN\user credentials. Remember that the DOMAIN\ part is mandatory and that it represents the short name of your Active Directory domain. You can join the domain using any user with sufficient privileges (there&#8217;s no need to use Administrator), and you can even directly join the PC in a particular OU passing the &#8211;ou argument to domainjoin-cli. The fourth point maybe won&#8217;t be necessary when Ubuntu 8.04 LTS wil be released because it seems to be a bug in the package (it won&#8217;t start likewise on reboot, so if you don&#8217;t issue this command it would seem that nothing is working after a reboot).
 I&#8217;ve just started to use this method on a test machine so I&#8217;ll leave more opinions on this product in the future.
 *EDIT:** First impressions***
 After some days of not so extensive usage, I&#8217;ve seen a couple of things that it&#8217;s worth notice:
 
[LIST]
[*]the likewise-open process seems to &#8220;die&#8221; from time to time, blocking all your login accesses with a &#8220;ERROR&#8221; message. Restarting it through init script solves the issue&#8230; but it&#8217;s something that definitely should not happen
[*]It informs you on login if your password is going to expire in X days (as set in your GPO). Very nice indeed.
[/LIST]
 Notes to the readers: if you&#8217;re experiencing installation problem, the best way is to report them to the [likewise-open-discuss mailing list]("http://lists.likewisesoftware.com/cgi-bin/mailman/listinfo/likewise-open-discuss"). There you can contact directly likewise developers (of Samba fame) and solve your problems or doubts.



Chequealo a mi me funciono, con esto logre que mis usuarios de AD ingresaran a la maquina, pero no que mantubieran sus permisos.
A ver si alguien tira la respuesta jajaja

---

### Post by quedefantasma on 2010-01-28
En algún momento también estuve peleándome con LIKEWISE...pero no se por que coños no pude hacerlo funcionar...e igualmente me parecía una solución muy traída de los pelos para una función que debería ser básica! ... pero voy a probarlo de nuevo a ver que onda...

Yo ahora estoy "jugando" con un servidor ubuntu y esta en mis planes probarlo como controlador de dominio...quizás así a la inversa sea mas fácil y confiable!

---

### Post by juancarlospaco on 2010-01-28
* a la inversa es mas fácil y confiable...*

---

### Post by shingo630 on 2010-01-29
La verdad que es cierto, los servidores linux son mas agiles y comfiables, fallan solo cuando falla el usuario que los maneja, pero bueno, cuando tenes toda una infraesctura con 300 puestos de trabajo tratar de cambiar el sistema de servidores como que no es muy viable, es por eso que lo que trato de adaptar es el puesto de trabajo en si, por eso quiero saber si existe la posivilidad de instalar algun Frame Work que avilite los permisos de usuario del Active Directory en Ubuntu Desktop.
Saludos

---

### Post by Wiredfixer on 2010-08-17
Pues hasta ahorita yo no he tenido problemas con Likewise, aqui les dejo el dato de la actualizacion a la version 6.0:

[http://www.likewise.com/community/index.php/forums/viewthread/797/](http://www.likewise.com/community/index.php/forums/viewthread/797/)

Hay que seguir todos estos pasos, en realidad no es complicado y en poco tiempo podran ver a su equipo en el dominio de windows.

Si esta bien instalado SMBFS no debe haber problema para poder ver los recursos compartidos.

La comodidad de que un Desktop Linux sea unido a un dominio windows reside precisamente en la cuestion de implementacion, ya que es mas facil unir estos equipos a una infraestructura existente que realizar un cambio de DC.

 En mi caso, ya hay una infraestructura de windows y solo un porcentaje de equipos se migrara a Ubuntu, para esto ya se usaba Likewise y ha funcionado correctamente para los servicios de intranet y otros.

 Hay algunos casos en los cuales en un equipo no puedes hacer un "apt-get" ya que se puede presentar el caso de que estemos tras un ISA server, esto se resuelve con NTLMAPS o configurando un servidor de repositorios "mirror" local, que en un ambiente Empresarial seria lo correcto, asi los equipos pueden ser gestionados completamente desde un servidor e inclusive gestionarlos con Puppet, que es lo que ando investigando en estos momentos.

 Saludos!!

---

