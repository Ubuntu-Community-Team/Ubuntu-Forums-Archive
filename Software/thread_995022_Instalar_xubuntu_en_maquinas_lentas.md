---
title: "Instalar x/ubuntu en maquinas lentas"
date: 2008-11-27
forum: Software
---

### Post by NickCis on 2008-11-27
Hola, Tengo una compaq presario Intel Celeron 500Mhz, 128ram, placa de video de 8mb intel (onboard)
Intente poner el xubuntu 8.10, pero anda demaciado lento, el ubuntu, ni lo carga. Que recomiendan que instale?.
Actualmente esta con un Windows Xp, y no entiendo por que funciona mas rapido que el xubuntu :S...

Saludos.

---

### Post by sergiom99 on 2008-11-27
Proba Xubuntu 8.04 que tiene soporte por 2 años mas.

Aca tenes una lista con las distros mas livianas:
[http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/)

Las mas conocidas: DamnSmallLinux, Puppy Linux.

---

### Post by guillermolisi on 2008-11-27
> **NickCis said:**
> Hola, Tengo una compaq presario Intel Celeron 500Mhz, 128ram, placa de video de 8mb intel (onboard)
Intente poner el xubuntu 8.10, pero anda demaciado lento, el ubuntu, ni lo carga. Que recomiendan que instale?.
Actualmente esta con un Windows Xp, y no entiendo por que funciona mas rapido que el xubuntu :S...

Saludos.

Esa maquina con tan poca RAM y aun menos para video va a andar lenta siempre, por mas que Ubuntu funcione bien ya que con solo cargar FireFox, por ejemplo, se queda sin RAM y empieza a hacer swapping.

Si queres algo mas liviano, proba Ubuntu Lite ([http://u-lite.org/?q=node/2](http://u-lite.org/?q=node/2)) con LXDE ([http://lxde.org/](http://lxde.org/)) y despues conta como te fue.

---

### Post by DrKenobi on 2008-11-27
Hola! Yo andaba con un problema similar al tuyo y por eso antes de instalar emule con el qemu DamnSmallLinux, Puppy Linux, xubuntu y fluxbuntu.

Al final termine con xubuntu, que me parecio el mejor y por suerte mi pc se lo banca muy bien (Pentium 4 1.8Ghz 256MB 30GB y 32MB-Video)

Pero con tan poca memoria, de los 4 arriba mencionados te recomiendo Puppy Linux, te va a andar bien y la intefaz es agradable.

Te paso un link q me pasaron a mi, pero que no anime a usarlo porque tengo apenas 1 semana en linux: [Installation Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

Suerte!


> **sergiom99 said:**
> Proba Xubuntu 8.04 que tiene soporte por 2 años mas.

Aca tenes una lista con las distros mas livianas:
[http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/)

Las mas conocidas: DamnSmallLinux, Puppy Linux.

---

### Post by hictio on 2008-11-27
Se le puede agregar mas RAM?
Que tama~no de HDD tiene?

Mi desktop es un 350 MHz pero con 512 MB de RAM, y la cosa, con Intrepid, es "usable" para tareas basicas de Internet, email, etc.
El unico tema que tuve con la maquina es que la instalacion (en 8.04 tambien) la hice con el CD Alternativo, y solo a un sistema de linea de comando, y despues lo subi a desktop bajandolo de internet; pero eso seguramente es porque mi maquina es muuuuuy vieja, especialmente el CD ROM.

---

### Post by NickCis on 2008-11-27
Ok, voy a intentar con El Puppy, eso del UbuntuLite y LXDE, no entendi bien como es la cosa pero pruebo, total no pierdo nada. Con lo de Installation Low Memory Systems, estoy mas perdido, este seria mi primer Linux. Va el segundo, taba cambiando mis dos maquinas a linux, y ya le instale ubuntu a un amigo, pero ando con 0 experiencia.

Saludos.

P.D.: El ubuntuLite, no tiene interfax grafica que tengo qe instalarle el LXDE?

---

### Post by andy_91 on 2008-11-27
exacto esa es la idea ;)

---

### Post by guillermolisi on 2008-11-27
> **NickCis said:**
> Ok, voy a intentar con El Puppy, eso del UbuntuLite y LXDE, no entendi bien como es la cosa pero pruebo, total no pierdo nada. Con lo de Installation Low Memory Systems, estoy mas perdido, este seria mi primer Linux. Va el segundo, taba cambiando mis dos maquinas a linux, y ya le instale ubuntu a un amigo, pero ando con 0 experiencia.

Saludos.

P.D.: El ubuntuLite, no tiene interfaz grafica que tengo que instalarle el LXDE?

Si no tenes experiencia en Linux, mi recomendacion es que pruebes Ubuntu Lite que, por lo que lei en su site, ya incluye el escritorio grafico LXDE (que tambien esta en los repositorios de Ubuntu).

Con tu PC deberia funcionar bien ya que los requerimientos recomendados son:

Recommended configuration

    * Pentium 2 or better
    * 96MB of RAM or better
    * 4GB Hard Drive or better

---

### Post by andy_91 on 2008-11-28
a yo tmb pense que UbuntuLite era un ubuntu con un entorno en linea de comando :p

---

### Post by hictio on 2008-11-28
> **andy_91 said:**
> a yo tmb pense que UbuntuLite era un ubuntu con un entorno en linea de comando :p

Me parece que se confunden con [Cubuntu](https://wiki.ubuntu.com/Cubuntu)

---

### Post by DrKenobi on 2008-11-28
esto del ubuntu lite me esta tentando :popcorn:

---

### Post by NickCis on 2008-12-03
Bueno, despues de probar varias distros, me decidi por hacer la instalacion de ubuntu en maquinas de poca ram.
Probe varios manejadores de ventanas (o como se llamen), y decidi qedarme con LXDE.
Ahora, tengo un problema, yo instale Slim como selector de usuario, en el /etc/slim.conf puse de opciones para elegir las interfaces lxsession,xfce4-session,lxde.
La opcion que supuestamente tendria que andar es lxsession (para entrar en lxde), pero da un error, pero al entrar por lxde, tambien da un error pero magiacamente entra. Se puede arreglar este problema?.

Ademas, me gustaria, que cuando prenda la computadora entre solo al usuario, sin tener que pasar por la pantalla de login (usando el sistema LXDE), es posible?, como lo hago?.

Saludos, y muchas gracias :P

---

### Post by NickCis on 2008-12-07
Alguna idea?.

Saludos.

---

### Post by c4d0rn4 on 2008-12-07
[http://ubuntuforums.org/showpost.php?p=4552480&postcount=3](http://ubuntuforums.org/showpost.php?p=4552480&postcount=3)

no se si es lo que quieres, pero si tienes un solo user puede ser útil. Lo que haces es eliminar el login manager y que la consola arranque logeada como un determinado usuario, y por último ejecuta automaticamente start x.

La verdad no se como se configura el desktop default para el startx... pero me resulta muy interesante.

---

### Post by hictio on 2008-12-07
> 
La verdad no se como se configura el desktop default para el startx... pero me resulta muy interesante.


El startx se controla desde un archivo de configuracion que se llama .xinitrc que tiene que estar en el root de tu $HOME, es decir, en ~/.xinitrc.

Tiene todos los programas que queres que se carguen cuando arranca X Window, [aca hay una copia de uno mío](http://www10.brinkster.com/hictio/linux/dot_xinitrc.htm) de hace varios años atrás...

Además, podés leer esto sobre la configuración del .xinitrc: [Switching Between Window Managers and Desktop Environments](http://www.rapierbit.org/linux/winmgrs.html)

Una cosa importante, el startx es un comando de consola, la única manera de ejecutarlo y que sirva de algo, a menos que uses xnest, es que lo arranqués desde la consola, es decir, con el login gráfico, y el ambiente gráfico todavía no iniciado.

---

