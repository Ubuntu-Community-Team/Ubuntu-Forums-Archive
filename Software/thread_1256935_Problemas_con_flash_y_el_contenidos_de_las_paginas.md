---
title: "Problemas con flash y el contenidos de las paginas!!!"
date: 2009-09-03
forum: Software
---

### Post by pelaolinux on 2009-09-03
[B]hola !!!
bueno les explico, al abrir una pagina ya sea en el navegador firefox o en el opera que son los dos que utilizo yo y en los cuales tengo los siguientes problemas : cuando entro a una web con mucho contenido como por ejemplo  muchas aplicaciones javascript, animaciones en flash y una gran cantidad de imágenes como en la pagina de facebook  que cuando escribo en ellas las letras me sale muy retrasadas al momento de haberlas tecleado eso me sucede en las paginas con mucha clases de contendido. El otro problema es cuando voy a ver un video en youtube o en alguna pagina similar que al momento de reproducir el video se ve muy cortado pero el sonido del video o de las animaciones en flash me funcionan excelente. E instalado muchas cosas y visto un monto de paginas en los cuales muestran casos similares e instalado distintas versiones de flash y algunas asta me dejan sin sonido las animaciones y los videos pero se siguen viendo igual de cortado, también e desinstalado paquete e instalados otros que recomiendan pero al final no pasa nada, también vi en unas parte que podría ser problema con la tarjeta de video y sus controladores pero me meti tanto en el tema de la tarjeta de video que al final configure el archivo /etc/X11/xorg.conf de tal manera que me reconose asta 1027.980 FPS con algunas aplicaciones abierta como el compiz y Avant Window Navigator, pero después de todo eso no e conseguido nada .[/B]

[U]Bueno si puede ayudar en algo esta otra informacion sobre mi ordenador :
ram 512
procesador 1000 Mhz
targeta de video de 128 ATI radeon 9200
sistema operativo: ubuntu 9.04 
[/U] 
ya la configuracion del fichero /etc/X11/xorg.conf es la siguiente :
> 

 Section "Monitor" 
     Identifier    "Configured Monitor" 
 EndSection 
  
 Section "Screen" 
     Identifier    "Default Screen" 
     Monitor        "Configured Monitor" 
     Device        "Configured Video Device" 
     SubSection "Display" 
         Virtual    1280 1024 
     EndSubSection 
 EndSection 
  
 Section "Device" 
     Identifier    "Configured Video Device" 
     Option         "Driver" "fglrx" 
     Option        "AGPMode" "2" 
     Option         "AGPFastWrite" "yes" 
     Option         "EnablePageFlip" "true" 
     Option         "ColorTiling" "true" 
     Option         "TripleBuffer" "true"  
     Option         "AccelDFS" "true" 
     Option         "AccelMethod" "EXA" 
     Option         "RenderAccel" "on" 
 EndSection


 _y eso mas los paquetes que instale para reconoser esa cantidad de FPS son los que salgo explicando en la siguiente dirección:_


 [http://ubuntuforums.org/showthread.php?t=1252463](http://ubuntuforums.org/showthread.php?t=1252463)
 

 [B]bueno espero que me puedan ayudar o alguien pueda saber cual es mi problema, por que a todos mis amigos le e instalado ubuntu en su pc y a todo le funcionan muy bien unbuntu  pero sin compiz  y efectos pero eso también me avía dado para pensar si era por los efectos y avía desactivado todos los efectos y me siguen funcionando todo igual &#8230; 

Saludos![/B]

---

### Post by armagedonc on 2009-09-03
Hola ,
Tu sistema es algo antiguo, un poco mas que el mio, en cuanto a la tarjeta, tengo una ati radeon 9250  con los drivers que vienen por defecto funciona bastante bien. Aunque creo que una buena opcion es que instales desde firefox addons adblock plus y flashblock, eso para empezar a bajarle la carga al sistema. Y luego que veas esto [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) es un thread donde se optimiza firefox y flash player pero esta en ingles.

Lo mas recomendable en tu caso es bajarle la carga al sistema ya que no hay mucha memoria.

Saludos.

---

### Post by Carlos C on 2009-09-03
> **armagedonc said:**
> Hola ,
Tu sistema es algo antiguo, un poco mas que el mio, en cuanto a la tarjeta, tengo una ati radeon 9250  con los drivers que vienen por defecto funciona bastante bien. Aunque creo que una buena opcion es que instales desde firefox addons adblock plus y flashblock, eso para empezar a bajarle la carga al sistema. Y luego que veas esto [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) es un thread donde se optimiza firefox y flash player pero esta en ingles.

Lo mas recomendable en tu caso es bajarle la carga al sistema ya que no hay mucha memoria.

Saludos.

Te pasaste, gracias por el dato!

---

### Post by pelaolinux on 2009-09-04
> **armagedonc said:**
> Hola ,
Tu sistema es algo antiguo, un poco mas que el mio, en cuanto a la tarjeta, tengo una ati radeon 9250  con los drivers que vienen por defecto funciona bastante bien. Aunque creo que una buena opcion es que instales desde firefox addons adblock plus y flashblock, eso para empezar a bajarle la carga al sistema. Y luego que veas esto [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) es un thread donde se optimiza firefox y flash player pero esta en ingles.

Lo mas recomendable en tu caso es bajarle la carga al sistema ya que no hay mucha memoria.

Saludos.


  	 	 	 	 	 	  Muchas gracias armagedonc, me ayudo demasiado ese link es súper bueno lo que sale en el además ahí mismo te salen otros link que te dan muchas mas explicaciones, lo que pude hacer con eso es optimiza el sistema en los navegadores haciéndolo mas estable y aparte ya no se me queda pegado cuando escribo en paginas como facebook que hay demasiados script, pero haun me queda un gran problema que es con los videos flash como en youtube y paginas similares, todavía se ven  cortado y no logro entender eso siendo que segui paso por paso y asta me di el animo de desinstalar compiz  para probar si eso era lo q me causaba ese problema, pero no fue a si pero bueno después de todo lo del link me ayudo demasiado y ayudara también a otras personas que tengan este problema... 

muchas gracias !  :D

---

