---
title: "problema con wine y Ragnarok Online"
date: 2009-06-30
forum: Software
---

### Post by sexon on 2009-06-30
Hola muy buenas tardes, tengo un pequeño problema, al utilizar el glxinfo |grep direct tengo Direct Rendering: Yes y en el glxgears tengo alrededor de 700 FPS con una tarjeta intel i945GM, y habiendo logrado finalmente lograr todo el rendimiento de mi tarjeta de video, me dispuse a instalar wine y poder jugar un simple juego que de verdad me gustaria poder jugarlo desde mi ubuntu 9.04 (ahora instale KDE sobre el GNOME, para ver si era un problema de la X) pero solo puedo correr el juego en la resolucion de 640x480, en cualquier otra resolucion me aparece el siguiente problema:

fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x137a5:cool:->(1,(nil)): Stub
intel_regions.c:413: intel_region_cow: Afirmación `region->cpp * region->pitch * region->height == pbo->Base.Size' fallida.
err:ntdll:RtlpWaitForCriticalSection section 0x7e59d4c0 "x11drv_main.c: X11DRV_C

como mencione anteriormente mi tarjeta de video es una intel i945GM y mi notebook es un HP530

muchas gracias

P.D.: Mi computador de escritorio que tiene una tarjeta ATI Radeon HD 2600 XD con intrepid ibex presenta exactamente el mismo problema, por lo que aparentemente no es de la tarjeta de video ni de la distribucion, asi que porfavor si me pudiesen ayudar, lo agradeceria =)
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7541965") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7541965")

---

### Post by CdK1 on 2009-06-30
Prueba una versión de wine más recienta:

Haz esto:

sudo gedit /etc/apt/sources.list

Y agrega;

deb [http://www.lamaresh.net/apt](http://www.lamaresh.net/apt) sid main

Guarda y cierra:

Ejecuta:

sudo wget -O - [http://www.lamaresh.net/apt/key.gpg](http://www.lamaresh.net/apt/key.gpg) | apt-key add
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install wine 
rm -rf /home/$USER/.wine*

Ejecutas;

winecfg

y corres de nuevo el juego....

---

