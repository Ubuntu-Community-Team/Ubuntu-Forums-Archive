---
title: "No puedo desinstalar virtualbox"
date: 2009-06-07
forum: Software
---

### Post by mano negra on 2009-06-07
Buenas,
    Tuve un problemita con el virtualbox 
    Instalé la última versión del Virtualbox bajándome el paquete .deb. Se que está en los repositorios, pero tengo entendido que la última versión trabaja mejor con las carpetas compartidas. El tema es que lo instalo y me aparece el siguiente mensaje de error:

'modprobe vboxdrv failed. Please use dmesg to find out why'. 

No sabía muy bien de que se trataba, hasta que vi que no funcionaba la máquina virtual que había creado.
Asi que decidí desinstalarlo para volver a instalarlo, pero no pude. Probé todas las formas que encontré por la web y nada. 
   Mi consulta es si saben como se puede solucionar ésto.
   De paso los pregunto otra cosa más. Me sugiere desde la consola, cada vez que desinstalo algún programa usar "apt-get autoremove" para eliminar otros paquetes que se instalaron. Nunca lu usé por temor a que se borrara algo del sistema. ¿No hay problemas en usarlo o mejor dejar las cosas como están?

---

### Post by s3MA00RRNY on 2009-06-07
English version of question (kind of):

[INDENT]I had a little problem with VirtualBox  
 I installed the latest version of VirtualBox bajándome package. Deb. It is in the repositories, but I understand that the latest version works better with the shared folders. The issue is that it installs and I get the following error message: 

 'modprobe vboxdrv failed. Please use dmesg to find out why.  

 I did not know very well that was until I saw that the virtual machine did not work he had created.  
 So I decided to uninstall then reinstall, but could not. I tried all the ways that the web and found nothing.  
 My advice is if you know how to resolve this.  
 Step of asking anything else. I suggested at the console every time you uninstall a program using "apt-get autoremove" to remove other packages that were installed. Lu never used for fear that something is removed from the system. Are there no problems in using it or better leave well alone?
[/INDENT]Did you try using 'sudo apt-get install --reinstall virtualbox-ose'? Also try using 'sudo apt-get remove virtualbox-ose' and then right after 'sudo apt-get autoremove' and 'sudo apt-get install virtualbox-ose'. If that doesn't work, try 'modprobe vboxdrv && dmesg > dmesg.txt' and send dmesg.txt as an attachment.

---

### Post by josecuervo86 on 2009-06-07
> **mano negra said:**
> Buenas,
    Tuve un problemita con el virtualbox 
    Instalé la última versión del Virtualbox bajándome el paquete .deb. Se que está en los repositorios, pero tengo entendido que la última versión trabaja mejor con las carpetas compartidas. El tema es que lo instalo y me aparece el siguiente mensaje de error:

'modprobe vboxdrv failed. Please use dmesg to find out why'. 

No sabía muy bien de que se trataba, hasta que vi que no funcionaba la máquina virtual que había creado.
Asi que decidí desinstalarlo para volver a instalarlo, pero no pude. Probé todas las formas que encontré por la web y nada. 
   Mi consulta es si saben como se puede solucionar ésto.
   De paso los pregunto otra cosa más. Me sugiere desde la consola, cada vez que desinstalo algún programa usar "apt-get autoremove" para eliminar otros paquetes que se instalaron. Nunca lu usé por temor a que se borrara algo del sistema. ¿No hay problemas en usarlo o mejor dejar las cosas como están?

En cuanto a desinstalarlo: cuales son los metodos que usaste para hacerlo?

En cuanto a lo segundo: dale sin miedo, que solo te va a eliminar los paquetes que te nombra ;)

---

### Post by josecuervo86 on 2009-06-07
> **pcdude2143 said:**
> English version of question (kind of):

[INDENT]I had a little problem with VirtualBox  
 I installed the latest version of VirtualBox bajándome package. Deb. It is in the repositories, but I understand that the latest version works better with the shared folders. The issue is that it installs and I get the following error message: 

 'modprobe vboxdrv failed. Please use dmesg to find out why.  

 I did not know very well that was until I saw that the virtual machine did not work he had created.  
 So I decided to uninstall then reinstall, but could not. I tried all the ways that the web and found nothing.  
 My advice is if you know how to resolve this.  
 Step of asking anything else. I suggested at the console every time you uninstall a program using "apt-get autoremove" to remove other packages that were installed. Lu never used for fear that something is removed from the system. Are there no problems in using it or better leave well alone?
[/INDENT]Did you try using 'sudo apt-get install --reinstall virtualbox-ose'? Also try using 'sudo apt-get remove virtualbox-ose' and then right after 'sudo apt-get autoremove' and 'sudo apt-get install virtualbox-ose'. If that doesn't work, try 'modprobe vboxdrv && dmesg > dmesg.txt' and send dmesg.txt as an attachment.

This is a Spanish-speaking forum. No need to repost in English.

Este es un foro español, no hay necesidad de escribir en ingles.

---

### Post by s3MA00RRNY on 2009-06-07
Sorry. Realized that afterward.

Perdón. Se dio cuenta de que después.

---

### Post by guillermolisi on 2009-06-07
> **pcdude2143 said:**
> Sorry. Realized that afterward.

Perdón. Se dio cuenta de que después.
It's Ok. You are welcome here, anyway.

Todo bien. Bienvenido de todas formas por aqui. ;)

---

### Post by guillermolisi on 2009-06-07
> **pcdude2143 said:**
> English version of question (kind of):
[INDENT]I had a little problem with VirtualBox  
 I installed the latest version of VirtualBox bajándome package. Deb. It is in the repositories, but I understand that the latest version works better with the shared folders. The issue is that it installs and I get the following error message: 

 'modprobe vboxdrv failed. Please use dmesg to find out why.  

 I did not know very well that was until I saw that the virtual machine did not work he had created.  
 So I decided to uninstall then reinstall, but could not. I tried all the ways that the web and found nothing.  
 My advice is if you know how to resolve this.  
 Step of asking anything else. I suggested at the console every time you uninstall a program using "apt-get autoremove" to remove other packages that were installed. Lu never used for fear that something is removed from the system. Are there no problems in using it or better leave well alone?
[/INDENT]Did you try using 'sudo apt-get install --reinstall virtualbox-ose'? Also try using 'sudo apt-get remove virtualbox-ose' and then right after 'sudo apt-get autoremove' and 'sudo apt-get install virtualbox-ose'. If that doesn't work, try 'modprobe vboxdrv && dmesg > dmesg.txt' and send dmesg.txt as an attachment.
Tambien pense en que una reinstalacion seria la solucion para volver al punto de partida anterior al origen de este thread.

Luego, lo que se necesita es regenerar el driver de Virtual Box porque posiblemente haya habido alguna actualizacion de version de Kernel y no esta en su lista de modulos compilados, por eso no funciona.

---

### Post by josecuervo86 on 2009-06-07
> **guillermolisi said:**
> Tambien pense en que una reinstalacion seria la solucion para volver al punto de partida anterior al origen de este thread.

Luego, lo que se necesita es regenerar el driver de Virtual Box porque posiblemente haya habido alguna actualizacion de version de Kernel y no esta en su lista de modulos compilados, por eso no funciona.

Habría que aclarar que la re-instalación la haga sobre la versión que bajo él (que casi seguro, por ser un deb de la pagina, es la versión cerrada y no la OSE)

---

### Post by mano negra on 2009-06-07
[quote=josecuervo86;7418018]En cuanto a desinstalarlo: cuales son los metodos que usaste para hacerlo?

   Para desinstalarlo usé: 
- sudo apt-get remove virtualbox. Pero eso pienso que está mal porque no lo instalé desde un repositorio.
- sudo dpkg -r virtualbox.
- sudo dpkg -p virtualbox.

  y nada. LA consola me tira el siguiente mensaje:

dpkg - atención: el paquete virtualbox no está instalado.
 no se tendrá en cuenta la petición de desinstalarlo

¿Alguna idea? Saludos

---

### Post by Hei Ku on 2009-06-07
cual era el nombre del archivo .deb? 
De acuerdo a eso es el nombre del paquete.

Y sí, si lo instalaste con un .deb lo podes desinstalar desde apt-get

---

### Post by mano negra on 2009-06-08
> **Hei Ku said:**
> cual era el nombre del archivo .deb? 
De acuerdo a eso es el nombre del paquete.

Y sí, si lo instalaste con un .deb lo podes desinstalar desde apt-get

  Ya probé desinstalarlo poniendo el nombre del paquete. Haber si esto ayuda a resolver ésto: cuando uso apt-get poniendo el nombre del paquete 
                           "virtualbox-2.2_2.2.4-47978_Ubuntu_intrepid_i386.deb"
   Me tira la consola 

"E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Además, se me activa el gestor de actualizaciones del Synaptic, ¡pero no hay nada para instalar!

---

### Post by guillermolisi on 2009-06-08
> **mano negra said:**
> Ya probé desinstalarlo poniendo el nombre del paquete. Haber si esto ayuda a resolver ésto: cuando uso apt-get poniendo el nombre del paquete 
                           "virtualbox-2.2_2.2.4-47978_Ubuntu_intrepid_i386.deb"
   Me tira la consola 

"E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Además, se me activa el gestor de actualizaciones del Synaptic, ¡pero no hay nada para instalar!
Que embrollo ....

Si no tenes ningun gestor de paquetes activo entonces se me ocurre que el error te lo da porque no tenes mas el paquete en tu maquina, en el cache.

Si esto es asi, con volverlo a instalar deberia funcionar otra vez (siempre y toda vez que invoques apt-get con sudo).

---

### Post by Hei Ku on 2009-06-08
Deberías poner:

sudo apt-get remove virtualbox-2.2

---

### Post by mano negra on 2009-06-08
Linux cada día me sorprende. Se me dió por revisar los repositorios y ahí estaba. El paquete que había instalado. Así que le dí eliminar ¡y ningún problema!! Por ahí tenía que poner virtualbox 2-2.
 Bueno, después veré de instalarlo de vuelta y ver que pasa. me voy a trabajar.
Saludos

---

### Post by prostata on 2009-06-08
Te cuento lo que yo hice después de probarlo y ver lo lento que es, incluso con recursos, me decidí a volver a lo típico, resetear cuando sea necesario algo del XP.

Desisntalé VB
Con Geparted, eliminé la partición del WXP
Instale nuevamente en dicha partición WXP
Sin Problema alguno, todo corre normalmente

Saludos

---

