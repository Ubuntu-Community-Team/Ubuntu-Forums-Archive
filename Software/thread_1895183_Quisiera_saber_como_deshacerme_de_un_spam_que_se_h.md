---
title: "Quisiera saber como deshacerme de un spam que se ha adherido a mi navegador."
date: 2011-12-14
forum: Software
---

### Post by astinx on 2011-12-14
Hola, recientemente, cada vez que abro firefox, me aparece en la parte inferior del navegador un spam de publicidad, no tengo idea de donde pudo haber salido, pero no consigo sacármelo de encima. ¿Alguien por casualidad conoce algún software que me permita deshacerme de él? ¿O algún método?.

Desde ya muchas gracias por detenerse a leer.
Saludos!

---

### Post by guillermolisi on 2011-12-14
Por casualidad agregaste alguna barra de botones/herramientas que no sea nativa de FFox ?

---

### Post by astinx on 2011-12-14
No, el ultimo plugin que instale fue uno que uso para reproducir series, pero habrá sido ya hace un mes que lo instale asi que no creo que sea ese el problema. ¿Acaso reinstalado firefox crees que se podria solucionar?

---

### Post by guillermolisi on 2011-12-14
No, hay que investigar hasta llegar a la causa.

Otra forma efectiva pero que no te llevara a saber cual fue la razon de este problema es remover completamente FFox y luego volverlo a instalar (que no es lo mismo que reinstalar o desinstalar simplemente para volverlo a instalar. En estos casos los archivos de configuracion se preservan y cuando vuelvas a inicar FFox aparecera tal como lo tenes ahora.)

---

### Post by astinx on 2011-12-14
¿Y entonces como podría hacer para removerlo completamente?. Me imagino que desinstalarlo desde el Centro de Software no lo removerá completamente. Disculpa es que no hace mucho que uso Ubuntu, por eso la única manera que conocía de desinstalar un software era desde el Centro de Software.

---

### Post by guillermolisi on 2011-12-14
Abri una terminal/consola e ingresa ```
sudo apt-get purge <nombre-del-paquete>
``` reemplazando <nombre-del-paquete> por el qu quieras remover completamente (purgar). En tu caso y si no recuerdo mal se llama "firefox" (sin las comillas).

Esto desinstala el programa y borra todos los archivos de configuracion que haya generado.

Lo volves a instalar desde el Centro de Software como si fuera la primera vez. No hace falta que reinicies ni antes ni despues de todo este proceso.

Hay otra posibilidad antes de hacer esto y es deshabilitar ese add-on que le instalaste y probar si esa publicidad continua apareciendo (claro, siempre que no hayas probado ya).

---

### Post by astinx on 2011-12-14
Gracias Guillermo, lo solucione efectivamente, desactivando uno por uno los plugins que tenia instalados y verificando si alguno de ellos era el causante, y lo era. Me extraña que se haya comenzado a comportar de esa manera puesto que era un plugin que tenia hace tiempo instalado, pero bueno, al menos no tuve que ser tan drástico como para remover el Firefox y volverlo a instalar.
Muchas gracias por tu ayuda.=D>

---

