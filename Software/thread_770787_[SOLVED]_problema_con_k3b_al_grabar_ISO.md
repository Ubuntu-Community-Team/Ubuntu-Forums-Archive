---
title: "[SOLVED] problema con k3b al grabar ISO"
date: 2008-04-27
forum: Software
---

### Post by sergiom99 on 2008-04-27
hola gente, nuevamente sigo preguntando.
tengo un problema al grabar una ISO de DVD con el K3b en un DVDRW. La grabacion se hace perfecto, pero al terminar queda colgado completamente el sistema. Reseteo y arranca OK. el DVD lo saco y lo pongo en el reproductor y se ve perfecto.

alguna tip de donde buscar problemas?
Lo que ya hice fue purgar y reinstalar el K3b.

---

### Post by faktorqm on 2008-04-27
Hola, colgado en que sentido? Quiero decir, colgado por hardware o que se te colgo el X? para ver eso cuando te pase apreta ctrl + alt + F2 y si te devuelve una consola, no se colgo por hardware.

Tambien lo que podes hacer para ver que pudo haber pasado es escribir en una consola "dmesg | tail" y ver que te dice.
Sino en /var/log ver a ver que pudo haber pasado. Sino instalate otro soft cualquiera de grabacion y fijate que pasa. Salu2!

---

### Post by clasificado on 2008-04-28
Mirá que hay unos cuantos niveles de cuelgues eh! y cada uno quiere decir algo distinto:

**1)** No te responde la ventana de k3b, pero podés cambiar a otras ventanas y abrir el menu de inicio (si ya se, esto no es que se cuelga "todo" pero hay veces que al postear en caliente uno tiende a exagerar)

**2)** No responde nada del escritorio, ni podes cambiar de ventanas, pero se mueve el mouse (usualmente conocido como, se colgó el XServer) Como bien dice el amigo faktorqm, con **ctrl+alt+f2 te da consola**, tambien se resetea el x con ctrl+backspace

**3)** No responde nada del escritorio, tampoco podés cambiar de consola y tampoco podés resetearlo,** no responde nada nada**. (mirá que todavia no está muerta eh!!!. Es enmarañado encontrarle pulso a este estado de coma, pero la red todavia está disponible, uno incluso puede abrir una consola por ssh. No se puede matar al XServer **pero se puede resetear el equpo por [REISUB]("http://www.dosbit.com/tag/reisub").**

Éste suele ser problemas con algún modulo agregado al kernel. Osea que tenés el 90% de la culpa. Lo mas probable son módulos propietarios, como NVidia-glx o el de ATI. También puede ser V4L, Módulos de monitoreo, Módulos de FileSystem y quinientas cosas mas.

Ponele un par de fichas a este eh. Probá quitar los drivers propietarios de la placa y probá grabar de nuevo.

4) Problemas del kernel. Incompatibilidad de hardware. Kernel panic. Meto a todos dentro de esta bolsa porque no te deseo ninguno.

clasificado

---

### Post by sergiom99 on 2008-04-28
gracias por las tips, esta noche pruebo de grabar alguno a ver en que nivel estoy.

---

### Post by sergiom99 on 2008-05-17
hola. creo q estoy en el caso 3.
no puedo conectarme por ssh porque lo tengo todo deshabilitado, pero termina de grabar y cuelga mal.
apago la notebook apretando el boton de Off y la vuelvo a prender. el DVD esta grabado y se puede ver ok.


Update> acabo de grabar y verificar una ISO en Nero @ WinXP sin ningun problema :-( asi que la grabadora esta OK.

---

### Post by sergiom99 on 2008-05-31
bueno hoy probe de grabar unos mp3 en un DVD-R de datos y tardo un monton y termino en error. adjunto la salida.
llego hasta el 8x% y estuvo un rato largo ahi y hacia un ruido como de "acelerar-desacelerar".

El asunto es que estoy re-cag****do de que se haya roto la grabadora.

---

### Post by sergiom99 on 2008-06-07
parece q en Hardy esta solucionado.

---

