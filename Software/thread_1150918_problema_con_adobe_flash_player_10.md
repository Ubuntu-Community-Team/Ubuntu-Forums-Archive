---
title: "problema con adobe flash player 10"
date: 2009-05-06
forum: Software
---

### Post by ambystoma_19 on 2009-05-06
hola como estan todos, estoy pidiendo ayuda aqui porque ya estoy cansado.
bueno hace unos dias tuve que reinstalasr el sistema por problemas con un kernel, estoy usando ubuntu 8.10. pero el problemas de ahora no es por eso, es por el flash player.
bueno como yua dije tuve que reinstalar el sistema, terminado esto fui a youtube con mozilla y me pidoio los plugins, y nunca instalo el adobe flash player 10, intente hacerlo desde consola y se queda en la parte de peticion http enviada, esperando repuesta... y luego de multiples intentos llo cierro. lo cual me trajo muchos problemas con el dpkg, que ya estan solucionados. entonces intente descargarlo desde la pagina, pero jamas lo descarga, ni el.deb, ni el tar.gz ni el .rpm.
enconclusion no puedo usar ninguna pagina que necesite flash, alguien me podria ayudar coon este problemita.?

---

### Post by staar on 2009-05-06
??? tenés internet? podés instalar otras cosas desde apt o synaptic? flash está en el meta-paquete 'ubuntu-restricted-extras', junto con codecs y otras cositas...

saludos

---

### Post by ambystoma_19 on 2009-05-06
si tengo internet,con synaptic me funciona para instalar todo, menos eso, ya probe con apt-get install flashplugin-nonfree, pero se cuelga en la parte peticion http enviada, esperando repuesta... al igual que pasa con synaptic.

---

### Post by staar on 2009-05-06
ese paquete 'flashplugin-nonfree' lo que hace es bajar desde la página de adobe a flash e instalarlo (ya que flash NO está en los repositorios), seguramente debe haber un problema con adobe y su página, habrán cambiado el enlace...

te recomiendo que busques bien otro lugar donde bajarlo, o que esperes hasta que lo arreglen los de adobe...

saludos

EDIT: acabo de probar bajar el deb desde la página de adobe, y si puedo...
el link directo es este [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb")

---

### Post by ambystoma_19 on 2009-05-06
segui el enlace y me descarga un archivo de 0 bytes. con los ubuntu-restricted-extras se cuelga en la misma parte.

---

### Post by staar on 2009-05-06
mmm que raro, sera tu ISP, porque a mi me lo baja lo más bien...

saludos

---

### Post by pablo.s on 2009-05-06
Del [sitio de Adobe]("http://get.adobe.com/es/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29").

Luego instalar con Gdebi.

---

### Post by losoollenos on 2009-05-06
Seguro es tu ISP, por lo menos a mi me pasa lo mísmo a veces, no puedo bajar "nada", no usarás la misma porquería que tengo que usar yo = TELERED no?

Saludos

---

### Post by ambystoma_19 on 2009-05-06
no tengo speedy banda ancha, y la verad que nunca me paso esto, a pesar de todo lo malo de telefonica, esto nunca fue un problema. nadie sabe de donde bajar el archivo de adobe flash player que no sea la pagina oficial?

---

### Post by neo2008 on 2009-05-25
Hola, buenas tardes.
Soy nuevo en el foro pero tengo el mismo problema
no puedo bajar el flash player desde la pagina de adobe...
tarda muchisimo y cuando baja, el archivo es de 0kb, probe bajarlo desde esta maquina pero en win y pasa lo mismo.
Internet anda perfecto, no tengo problemas para bajar nada

No se si se puede (todavia no lei bien las reglas del foro) poner un link de descarga, pero si alguien ya lo bajo el flash player y lo puede subir a alguna pagina externa...

Gracias.

Saludos.

---

### Post by andy_91 on 2009-05-25
> **ambystoma_19 said:**
> segui el enlace y me descarga un archivo de 0 bytes. con los ubuntu-restricted-extras se cuelga en la misma parte.

:O tene cuidado con el flash ami me  rompio el debconf con esa http en espera

---

### Post by neo2008 on 2009-05-26
> **ambystoma_19 said:**
> no tengo speedy banda ancha, y la verad que nunca me paso esto, a pesar de todo lo malo de telefonica, esto nunca fue un problema. nadie sabe de donde bajar el archivo de adobe flash player que no sea la pagina oficial?

Bueno, viendo que tenes Speedy, voy a casi confirmar que es problema del ISP, ya que yo tambien tengo el mismo y como dije antes, no lo podia bajar.
Recien probe en el trabajo y bajo sin problemas. asi que ya lo tengo.

Saludos

---

### Post by Hei Ku on 2009-05-26
> **neo2008 said:**
> Bueno, viendo que tenes Speedy, voy a casi confirmar que es problema del ISP, ya que yo tambien tengo el mismo y como dije antes, no lo podia bajar.
Recien probe en el trabajo y bajo sin problemas. asi que ya lo tengo.

Saludos

Tendran alguna regla y se confundira con el Flash de Ciudad Internet, que es la competencia? :lolflag:

Probaron de bajarlo de otro site? Supongo que debe estar replicado por ahí. No para que instalen esa version, solo como prueba. Es raro que se ensañe con ese archivo en particular.

---

### Post by neo2008 on 2009-05-26
> **Hei Ku said:**
> Tendran alguna regla y se confundira con el Flash de Ciudad Internet, que es la competencia? :lolflag:

Probaron de bajarlo de otro site? Supongo que debe estar replicado por ahí. No para que instalen esa version, solo como prueba. Es raro que se ensañe con ese archivo en particular.

la verdad que lo busque por todos lados, pero cualquier link te lleva a la pagina oficial.
Es raro, pero puede pasar que hagan estas cosas, es speedy, se puede esperar cualqueir cosa, pero bueno, yo de aca del laburo lo pude bajar, asi que si alguien lo necesita que me avise.

---

### Post by elissss on 2009-11-16
Buenos dias!
Yo tengo el mismo problema, cuando bajo el adobe flash player 10, ya sea si lo bajo de la pag oficial o del link que dejaron aca me sale el siguiente error

"No se puede instalar adobe flash player 10 linux.deb"
El paquete podria estar dañado, o puede que usted no tenga los permisos para abrir el archivo. Revise los permisos del archivo.

Ya revise los permisos y sigue en lo mismo...

No se si a alguien le paso lo mismo...??

---

