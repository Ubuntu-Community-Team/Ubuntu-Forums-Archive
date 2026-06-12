---
title: "como actualizar mi version de 7.10. a 8.04"
date: 2008-05-30
forum: Software
---

### Post by michay on 2008-05-30
Buenas por recomendacion de un integrante que me ha ayudado en todo desde que instale ubuntu, me quiero pasar de 7.10 a 8.04.
mis preguntas son:
tengo que bajar la version 8.04 y formatiar la que tengo?
viene un tipo de Serv Pack tipo win... para actualizar ??
o puedo actualizarme desde mi version a la nueva, que seria lo ideal no??
Desde ya muchas gracias y recuerden que soy muuuuuy nuevo en esto.
Salu2

---

### Post by Oktubre on 2008-05-30
Hola, yo lo actualice hace una semana, desde el Update Manager (dentro del menu System sino recuerdo mal) tenes un boton que dice Upgrade to 8.04. 
Ahi empieza a bajarse los paquetes (en mi caso fueron 1180) y despues de casi 24hs el sistema queda actualizado. 

Se reinicia y listo!

Saludos

---

### Post by michay on 2008-05-30
Ok oktubre, vamos a ver que onda.
muchas gracias:)

---

### Post by rojojuan on 2008-05-30
> **michay said:**
> Buenas por recomendacion de un integrante que me ha ayudado en todo desde que instale ubuntu, me quiero pasar de 7.10 a 8.04.
mis preguntas son:
tengo que bajar la version 8.04 y formatiar la que tengo?
viene un tipo de Serv Pack tipo win... para actualizar ??
o puedo actualizarme desde mi version a la nueva, que seria lo ideal no??
Desde ya muchas gracias y recuerden que soy muuuuuy nuevo en esto.
Salu2

Actualicé por Internet sin problemas.

---

### Post by phxnd on 2008-05-30
me parece que es mejor instalarlo desde 0,,,osea,,,formatear y instalar hh :P,,,, no lo invente,,,lo habia sacado de otro lado XD

saludos

---

### Post by xpelaox on 2008-05-30
yo tambien en mi compu secundaria lo actualize por internet, y funciono bien... pero pienso igual a los muchachos que comentaron arriva, pera mi lo mejor es instalarlo de cero :)

---

### Post by rober-mpp on 2008-05-30
Te comento que yo tenia 7.10 instalado y actualizado a 8.04. Y andaba bastante bien, si bien tuve que reconfigurar algunas cosas que me piso durante la actualizacion en terminos generales andaba mas rapido que 7.10. Lamentablemente de una ***** bastante grande que me mande, tuve que instalar de 0, y aproveche para mandarle el 8.4 de una. Te puedo decir que anda mejor aun que el 7.10 actualizado, pero logico, tengo la instalacion bastante pelada. Yo te recomendaria instalarlo de 0, siempre y cuando no tengas muchas cosas configuradas a mano / customizadas.

---

### Post by Hei Ku on 2008-05-30
pongamos un manto de cordura sobre la actualizacion. Vieron realmente como es el proceso?
Lo que hace en la actualizacion es desinstalar TODOS los paquetes y reinstalar los paquetes de la nueva version. O sea, lo único que queda es a lo sumo ciertas configuraciones que hayan modificado e incluso en esos casos pueden elegir si pisar el archivo de configuración o dejar el que estaba.
Donde tienen que tener cuidado es si le metieron mano a configuraciones, o si tienen programas compilados. En esos casos pueden transpirar un poco, pero si no, sale joya.
Yo vengo actualizando desde Edgy y no soy de los mas viejos.

---

### Post by sergiom99 on 2008-05-30
> **Hei Ku said:**
> 
Yo vengo actualizando desde Edgy y no soy de los mas viejos.

O sea que siempre pisaste lo anterior? Vos usas Kubuntu no?
Entonces me parece que yo por lo menos te hago caso.

---

### Post by Hei Ku on 2008-05-30
> **sergiom99 said:**
> O sea que siempre pisaste lo anterior? Vos usas Kubuntu no?
Entonces me parece que yo por lo menos te hago caso.

Es que esa es la diferencia con el mundo Windows. No te pisa la version, es como hacer una actualizacion de un programa individual. Primero desinstala el que tenes, y luego te instala la version nueva. La actualizacion hace eso a nivel masivo. Marca todo para desinstalar y te instala las nuevas versiones.

Yo hice el cambio de Breezy a Dapper y despues a Edgy de esta forma. Cuando tenia Edgy cambie el disco, asi que reinstale de cero, y desde esa version vengo actualizando hasta ahora.

---

### Post by sergiom99 on 2008-05-30
bueno, maniana intento.

2 preguntas te hago:
1. sabes cuando viene una LTS de Kubuntu?
2. Que significa Hei Ku? :-)

Gracias- Sergio

---

### Post by Hei Ku on 2008-05-31
1. Probablemente en el proximo ciclo de LTS, digamos Kubuntu 10.4
2. Significa Paz del Vacio.

---

### Post by sergiom99 on 2008-05-31
gracias Heiku por tu ayuda.
Ya actualice y no tuve problemas. tardo unas 3hs, mas que nada por la descarga.
Creo que levanto casi todo ok, hasta ahora no encontre nada raro.

lo q necesito solucionar:
[COLOR="Red"]1. Al reiniciar queda la pantalla negra y al dar ctrl+alt+del cierra normalmente.
2. En compiz me deja de reconocer los JPG para el skydome y ademas haciendo scroll sobre el escritorio no puedo girar el cubo como hacia antes.[/COLOR]

otros comentarios:
me instalo firefox3 que no estoy seguro si lo queria (me mata como muestra las direcciones ya escritas!!)
sonido y wifi entraron perfecto y ahora conecta el wlan0 al iniciar de una y lo mantiene. (la eth0 ahora se llama eth1...)
cuando encuentre alguna otra cosa digna de mencion lo posteo.

---

### Post by EnriqueK on 2008-05-31
Yo pasé de la 7.04 a la 8.04 , pero no sería una actualización, sino una instalación de cero pero  de forma automatizada, los pasos son mas o menos los siguientes, primero respalda tu carpeta de usuario y todos los datos que creas conveniente,

Seguidamente abro Synaptic en la antigua instalación y voy a Archivo -> Guardar selecciones como , marco el casillero  "Guardar el estado completo ............" le doy un nombre cualquiera y se genera un documento de textos plano con todos los paquetes instalados, allí figura solo el nombre de los paquetes sin especificar la versión, ya APT se encargará de completar los "detalles" .

Luego instalo Hardy desde el Live Cd , habilito todos los repositorios equivalentes a la intalación antigua y haciendo un proceso semejante con el Synaptic o sea voy a Archivo -> Leer selecciones , busco el archivo de textos creado en la instalación anterior y que debes portar a la nueva instalación , sigo los pasos y comienza la descargas e instalación de todos los paquetes que corresponderán a la nueva versión.

Este método solo instala los paquetes que hayan sido descargados e instalados desde los repositorios, los que hayas compilado o instalados de forma manual , deberás volver a instalarlos de la misma manera, lo mas importante es que todo se hace bajo control de APT en la que instala las nuevas versiones de paquetes , por eso lo mas crítico del método es el de tener repositorios equivalentes en ambas instalaciones y si hubiera un paquete que no tiene un equivalente para en los repositorios de la nueva versión, simplemente no lo toma en cuenta, por ejem si antes tenías xmms , ahora no se podrá instalar.

---

### Post by sergiom99 on 2008-06-01
> **sergiom99 said:**
> 
[COLOR="Red"]1. Al reiniciar queda la pantalla negra y al dar ctrl+alt+del cierra normalmente.
2. En compiz me deja de reconocer los JPG para el skydome y ademas haciendo scroll sobre el escritorio no puedo girar el cubo como hacia antes.[/COLOR]


haciendo poweroff/reboot desde consola lo hace perfecto, pero al hacerlo desde el Kmenu queda con la pantalla en negro (con puntero del mouse). Hago ctrl+alt+del y cierra kdm y continua el reseteo/apagado normalmente. Alguna idea? Tendre que hacerlo por consola de ahora en mas?

---

### Post by sergiom99 on 2008-06-02
en realidad la secuencia que hago es reiniciar el X y ahi al toque Ctrl+Alt+Sup si es que lo hago por el menu de apagar, y si mando el comando por consola lo hace perfecto.

---

