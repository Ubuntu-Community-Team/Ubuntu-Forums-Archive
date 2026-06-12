---
title: "Problema para ver videos de YouTube"
date: 2008-10-31
forum: Software
---

### Post by PeTTi on 2008-10-31
Cuando recién instalas Ubuntu no podés ver los videos de Youtube, ni ningun tipo de video, pero cuando inicias con Firefox y vas a YouTube te aparece para instalar unos pluggins, y si instalas los 3 pluggins que te aparecen, podés verlos.. pero yo instalé el último y después no me apareció más eso para instalar otros plugins para ver los videos..
Gracias.-

---

### Post by kbzon_v8 on 2008-11-01
a mi me paso lo mismo... no podia ver youtube y cuando instale esos 3 plug-ins seguia sin andar.

buscando encontre esto: 
instale flashplugin-nonfree desde synaptic y despues baje install_flash_player_9_linux.tar.gz, lo instale y arranco lo mas bien. salvo a ahora de vez en cuando, tengo rithmbox abierto y lo tengo q cerra para ver los videos :S

espero q te sirva.
saludos

---

### Post by guisheca on 2008-11-01
> **PeTTi said:**
> Cuando recién instalas Ubuntu no podés ver los videos de Youtube, ni ningun tipo de video, pero cuando inicias con Firefox y vas a YouTube te aparece para instalar unos pluggins, y si instalas los 3 pluggins que te aparecen, podés verlos.. pero yo instalé el último y después no me apareció más eso para instalar otros plugins para ver los videos..
Gracias.-

No entiendo bien tu consulta, podrías reformularla?

---

### Post by PeTTi on 2008-11-02
> **kbzon_v8 said:**
> a mi me paso lo mismo... no podia ver youtube y cuando instale esos 3 plug-ins seguia sin andar.

buscando encontre esto: 
instale flashplugin-nonfree desde synaptic y despues baje install_flash_player_9_linux.tar.gz, lo instale y arranco lo mas bien. salvo a ahora de vez en cuando, tengo rithmbox abierto y lo tengo q cerra para ver los videos :S

espero q te sirva.
saludos
Hice todo eso, y el lo de Synaptic ya lo tenia, y lo otro lo insale y sigue igual :S

> **guisheca said:**
> No entiendo bien tu consulta, podrías reformularla?
Cuando recien terminas de instalar Ubuntu, en Firefox no tenes ningun plugin, y para ver videos en YouTube necesitas 3, yo siempre los instale en ese orden que aparecian, pero esta vez lo instale al revez, entonces instale el último y después no me apareció más para instalar los otros 2 plugins, entonces no tengo forma de ver los videos ni de instalar los plugins.

Capaz desinstalando Firefox, ahora lo intento.

---

### Post by hictio on 2008-11-02
No se si les sirva, ayer instale desde cero 8.10, instale estos plugins:
```

flashplugin-nonfree libflashsupport

```

Los videos de Youtube si estan andando, pero el audio no funciona, por lo que veo, en ninguno, probe [este](http://www.youtube.com/watch?v=_ImW0-MgR8I) que [postearon la semana pasada](http://ubuntuforums.org/showthread.php?t=958501), que me acuerdo perfecto que el audio andaba, porque hubo varias "quejas" que la musica del video era malisima.

---

### Post by PeTTi on 2008-11-02
Ahora volví a instalar Ubuntu, asi que espero no tener que hacer todos estos pasos
Gracias.

---

### Post by c4d0rn4 on 2008-11-02
Yo "tengo" un problema similar, pero en hardy.

La solución es instalar desde firefox el flash. Cuando lo instalo desde synaptic no ubica el plugin donde debiera.

Si alguien tiene ese problema, si instalaron vía synaptic fijense si dentro de tools->add ons-> plugins está Shockwave Flash.

Si no está desisntalen en synaptic todo, vean un video de youtube emebido en algún blog. En youtube no salta. Les aparece una barra como la de recordar contraseña, siguen las instrucciones, cuando terminan reinician firefox y listo el pollo.

---

### Post by hictio on 2008-11-02
> **c4d0rn4 said:**
> Yo "tengo" un problema similar, pero en hardy.

La solución es instalar desde firefox el flash. Cuando lo instalo desde synaptic no ubica el plugin donde debiera.

Si alguien tiene ese problema, si instalaron vía synaptic fijense si dentro de tools->add ons-> plugins está Shockwave Flash.


Mmmhhh... Puede ser que sea algo de Hardy nada mas? Yo el Flash lo instale via 'aptitude' y si lo veo listado en "Add-ons -> Plugins".

---

### Post by PeTTi on 2008-11-03
Yo tengo Hardy, porque con Ibex no puedo configurar el modem para tener internet :S

---

### Post by GGsalas on 2008-11-03
> **PeTTi said:**
> cuando inicias con Firefox y vas a YouTube te aparece para instalar unos pluggins, y si instalas los 3 pluggins que te aparecen


El primero Plugin que aparece es el de Adobe, los otros dos son opciones libres al primero (el privativo de Adobe). Lo que tenés que hacer es instalar únicamente el primero. Si ya instalaste los 3 habrá que preguntar a alguien que explique como desinstalarlos.

Saludos.

---

### Post by emiliano_raso on 2008-11-03
Gente, no se que version estaran usando, pero en "Agregar Quitar" busquen "macromedia flash"

El primero que les aparece es el flash player (se llama Macromedia Flash Player o algo asi). Instalenlo y listo.

Luego seguramente tendran el problema de no poder escuchar un video de youtube o cualquier cosa de internet y musica al mismo tiempo.
Busquen en google que hay varias soluciones y muy simples.

---

### Post by PeTTi on 2008-11-03
> **GGsalas said:**
> El primero Plugin que aparece es el de Adobe, los otros dos son opciones libres al primero (el privativo de Adobe). Lo que tenés que hacer es instalar únicamente el primero. Si ya instalaste los 3 habrá que preguntar a alguien que explique como desinstalarlos.

Saludos.
Reinstale Ubuntu e instale los 3 plugins que te aparecen al entrar a un video de Youtube y funcionan bien :D

Gracias a todos.

---

### Post by hictio on 2008-11-03
> **hictio said:**
> No se si les sirva, ayer instale desde cero 8.10, instale estos plugins:
```

flashplugin-nonfree libflashsupport

```

Los videos de Youtube si estan andando, pero el audio no funciona, por lo que veo, en ninguno, probe [este](http://www.youtube.com/watch?v=_ImW0-MgR8I) que [postearon la semana pasada](http://ubuntuforums.org/showthread.php?t=958501), que me acuerdo perfecto que el audio andaba, porque hubo varias "quejas" que la musica del video era malisima.

Soy un gil... Por dio!!!
El audio de Flash anda perfecto en Intrepid con esos plugins, el problema era que tenia setteado el nivel del audio 'PCM' en cero...
Estaba convencido que tenia un problema mas grave (tampoco escuchaba los audios de sistema, el del login, etc), y al final era esa estupidez.

---

### Post by maximi89 on 2009-03-01
> **hictio said:**
> Soy un gil... Por dio!!!
El audio de Flash anda perfecto en Intrepid con esos plugins, el problema era que tenia setteado el nivel del audio 'PCM' en cero...
Estaba convencido que tenia un problema mas grave (tampoco escuchaba los audios de sistema, el del login, etc), y al final era esa estupidez.

Otro problema que pudo haber sido fue.... sudo nano /usr/firefox/firefoxrc

Lo pueden cambiar de ALSA  a AOSS
FIREFOX_DSP="aoss"

Para los que usan Debian, tienen la solución acá... 
sudo nano /usr/iceweasel/iceweaselrc

ICEWEASEL_DSP="aoss"


es lo que logré encontrar en estos foros, cambié de alsa a aoss y me funciona mejor :O

---

### Post by elviolator2004 on 2009-04-07
Hola que tal amigos argentinos. Hace varios dias que estoy intentando entrar en Ubuntu.es pero no se que pasa no se conecta. Bueno gracias a ello descubri ubuntu.ar:guitar:
Bueno volviendo al tema que estan tocando acá yo instale hace poco el 8.04.1 LTS desktop edition y con firefox no puedo ver los videos de youtube. Apenas quiero reproducir alguno me aparece el mensaje que no tengo activado java script o que tengo una versión vieja de flash. Verifique lo de java y esta activado. Instale la ultima version del reproductor flash, tampoco funciono, la pagina de youtube sigue igual con el mismo mensaje. Instale el opera, pero me pasa lo mismo. Despues leyendo vi que habia que instalar un plugin desde los repositorios, no me acuerd como se llama, lo baje e instale pero nada. Que puedo hacer?, que me falta?. Desde ya gracias!!):P

---

### Post by Hei Ku on 2009-04-07
Tenes la version 32 bits o 64 bits. De eso depende como hagas la instalacion.

---

### Post by elviolator2004 on 2009-04-08
> **Hei Ku said:**
> Tenes la version 32 bits o 64 bits. De eso depende como hagas la instalacion.
Hola Maestro!!, mira tengo la version 32 bits. Gracias por contestar

---

### Post by Hei Ku on 2009-04-09
Aca hay un tutorial para instalar Flash de acuerdo a la version que tengas de Ubuntu. Solo para 32 bits.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by elviolator2004 on 2009-04-09
> **Hei Ku said:**
> Aca hay un tutorial para instalar Flash de acuerdo a la version que tengas de Ubuntu. Solo para 32 bits.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

Cha gracias!!!):P

---

