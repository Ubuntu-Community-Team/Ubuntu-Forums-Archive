---
title: "Me presento y hago unas preguntas sobre amule"
date: 2008-12-13
forum: Software
---

### Post by guillermon on 2008-12-13
Hola a todos:
            Mi nombre es Guillermo, vivo en Córdoba, es la primera vez que participo en este foro. Tras participar en el foro Ubuntu-es, decidí comenzar a hacerlo en este foro, pues quiero involucrarme más en lo que ocurre en mi país. Soy lego en la informática, solo sé cosas de uso doméstico, y me gusta perder mucho tiempo metiendo la pata y luego solucionar. Y podría decir que mi llegada al Software Libre en general, y a Ubuntu en particular, tiene que ver una postura ideológica, hasta militante diría. Veo con mucha claridad aspectos de dominación en el Software privativo; veo como dignificante las reinvindicaciones de las pequeñas cosas...
      Tengo instalado Ubuntu Hardy; pero estoy dudando en hacer una instalación limpia a Intrepix, pues me parece que he metido mucho la pata... (la verdad que no tengo muy en claro las consecuencias de hacer una instalación limpia de este sistema).
      La verdad que me encuentro con problemas desde que estoy en Ubuntu (al igual que antes los tenía con Win$), pero la diferencia, para mi muy importante, es que hay gente dispuesta a ayudarme... Tengo muchas dudas, pero para ir por parte comienzo por tratar de hacer andar la mula! paso a detallar:
     Resulta que había configurado la amule con un Router, abriendo los puertos, etc. y andaba bien (eso creo, pues había llegado a descargar unos 30 k/s... tengo banda ancha de 1 Mb). Luego decidí sacar la carpeta de descarga de este SO a otro disco, pues me saturaba el Home, y llevé todas las carpetas de descarga y de almacenamiento, en otra partición, pero he notado que ya prácticamente no descarga... este programa emite este error:
Logger.cpp(269): Error: Impossible to set permissions for the file '/media/Soporte/Amule/Temp/005.part.met.bak' (error 1: Operación no permitida)

	Esta partición tiene propiedad de Root, pero tiene los permisos creo haber puesto con máximo... he intendado cambiar el propietario...
	El planteo: está bien así? Será que no hay para descargar? O debo cambiar los permisos, el propietario del disco, o no queda otro que volver las descargas a mi Home (lo que no me gusta mucho)? A continuación escribo como figuran los permisos, y cómo lo cargué en mi fstab:

drwxrwxrwx 14 root root 16384 1969-12-31 21:00 Soporte

/dev/sda7       /media/Soporte  vfat    defaults,umask=000  0  1
 
      Luego, para complicar más, ya no tengo el Router; teniendo entonces la conexión directa a un modem (cablemodem) atlántida... Y no sé si eso puede alterar algo...

2) Una segunda pregunta sobre el amule: El Símbolo del mismo, cuando uno minimiza, a veces aparece, a veces no... o aparece en el escritorio... otras veces sobre la misma ventana del mismo programa... o no aparece, estando el programa activo. ¿hay alguna solución?

   Bueno, espero haber sido claro. No quiero explayarme más, tanto en la presentación como en el pedido de ayuda, pero por favor, no duden en preguntarme si es necesario. Desde ya muchas gracias, y aprovecho para saludar a todos, espero interactuar con Uds, compartir y participar!
     Hasta pronto, un gusto

Guillermo

---

### Post by faktorqm on 2008-12-14
Hola y bienvenido al foro! Te recomiendo que no hagas posts tan largos (a menos que postees en la seccion comunidad) por que por lo general los posts mas largos se dejan para leerlos ultimos ;)

Con respecto al problema de los permisos, estas trabajando sobre una particion fat32, o similar, ¿por que? La verdad que ese sistema de archivos deja mucho que desear...
De todas maneras, deberias probar esto, yo creo que te va a solucionar el problema

```
/dev/sda7 /media/Soporte vfat defaults,umask=007,uid=1000,gid=1000 0 0
```

Eso te establece ul ID de usuario y grupo en el tuyo (el numero 1000). Proba y fijate que ocurre, yo creo que no vas a tener mas problemas.

Y lo del modem de cablemodem no tenes que tener ningun problema, si antes tenias un router despues y ahora no el modem es el mismo, o entendi mal?

Lo del icono capaz sea algun bug, tenes compiz activado? Salu2!!!

---

### Post by guillermon on 2008-12-15
Gracias Faktorqm, he hecho el cambio en fstab, solo que poniendo usuario 1001, que soy yo; el 1000 quién será?? Supongo que este señor root (es un chiste). ¿Dará algún problema tenerlo así?
    Ahora ya no da problemas, y efectivamente ahora figuro como propietario de estas carpetas, y con los privilegios para el Grupo: exelente!. Ahora, respecto al hecho de que uso fat32, fue un consejo que me dieron cuando empecé a migrar, pues al tener también el sistema win$, es común a ambos; y puedo decirte que me ha funcionado muy bien. Me gustaría saber porqué no es tan deseable, si tienes ganas, pues ya no uso win$, y en cualquier momento hago un format c: (descripción simbólica), y brindaré saboreando el triunfo... en ese momento puedo cambiar el sistema...
    Por otra parte, lo del post largo lo tendré en cuenta. 
    Respecto del bug, no tengo muy en claro cómo saber si es, o cómo arreglarlo. Sí había instalado compiz para ver el cubo, pero lo he desactivado; ahora bien, no sé cómo desinstala (¿ remove compiz?). He dado el puntapié desactivando los efectos de pantalla, poniéndolo en Normal... y el símbolo ha aparecido en su lugar; pero no me confío pues como he dicho, viene siendo un día por aquí, otro por allá...
   Ahora bien, a riesgo de hacerlo largo otra vez, con el cambio efectuado en amule, ya sin el error, sigo sin poder descargar; la banderita para abajo está roja... he puesto a descargar varias cosas como prueba (cosa que no sea falta de fuente), y nada. He estado buscando algún post que me ayuda nuevamente a configurar de cero amule para que pueda funcionar, pero me cuesta manejarme en este foro, pues se mezcla con otros foros en ingles, cuesta volver a este... Otro problema que tengo es que en algún momento añadí el comando en Programas de inicio de amule, para que se cargue desde el inicio, luego lo borré, y sigue cargándose igual... no sé porqué...
Edito: he encontrado un wiki sobre configuración, con detalles y en castellano...
[http://www.amule.org/wiki/index.php/FAQ_aMule-es#.C2.BFQu.C3.A9_es_toda_esta_historia_sobre_el_conejo.3F](http://www.amule.org/wiki/index.php/FAQ_aMule-es#.C2.BFQu.C3.A9_es_toda_esta_historia_sobre_el_conejo.3F)

    Bueno, si puedes/n ayudarme, estaré agradecido... aprovecho para saludar; comento si encuentro alguna solución...
Hasta pronto

Guillermo

---

### Post by faktorqm on 2008-12-15
> **guillermon said:**
> Ahora, respecto al hecho de que uso fat32, fue un consejo que me dieron cuando empecé a migrar, pues al tener también el sistema win$, es común a ambos; y puedo decirte que me ha funcionado muy bien. Me gustaría saber porqué no es tan deseable, si tienes ganas, pues ya no uso win$, y en cualquier momento hago un format c: (descripción simbólica), y brindaré saboreando el triunfo... en ese momento puedo cambiar el sistema...

Hola, hagamos de cuenta que NTFS es guatemala y fat32 guatepeor, me entendiste ahora? No quiero desacreditar a quien te dio el consejo, pero gnu/linux trae soporte para particiones NTFS mediante el paquete ntfs-3g para lectura/escritura. Para windows, existe un driver que maneja particiones ext3, asi que tampoco es problema.

> **guillermon said:**
> Respecto del bug, no tengo muy en claro cómo saber si es, o cómo arreglarlo. Sí había instalado compiz para ver el cubo, pero lo he desactivado; ahora bien, no sé cómo desinstala (¿ remove compiz?). He dado el puntapié desactivando los efectos de pantalla, poniéndolo en Normal... y el símbolo ha aparecido en su lugar; pero no me confío pues como he dicho, viene siendo un día por aquí, otro por allá...


Bueno te recomendaria que abras un post nuevo en la seccion software del foro por que yo de eyecandy no tengo ni idea, y se confunden los titulos de los posts. Para desinstalar cualquier programa, lo mejor que podes hacer es ir a sistema -> administracion -> gestor de paquetes synaptics y si no sabes como se llama el paquete del programa usa el buscador.
OJO, no desinstales mas de la cuenta, si por ejemplo queres desintalar compiz y te dice que aparte hay que eliminar ubuntu-desktop o te dice muchos paquetes no lo desinstales. Esas cosas se llaman metapaquetes y si los desintalas se te el ubuntu al caño.


> **guillermon said:**
> Ahora bien, a riesgo de hacerlo largo otra vez, con el cambio efectuado en amule, ya sin el error, sigo sin poder descargar; la banderita para abajo está roja... he puesto a descargar varias cosas como prueba (cosa que no sea falta de fuente), y nada. He estado buscando algún post que me ayuda nuevamente a configurar de cero amule para que pueda funcionar, pero me cuesta manejarme en este foro, pues se mezcla con otros foros en ingles, cuesta volver a este... Otro problema que tengo es que en algún momento añadí el comando en Programas de inicio de amule, para que se cargue desde el inicio, luego lo borré, y sigue cargándose igual... no sé porqué...
Edito: he encontrado un wiki sobre configuración, con detalles y en castellano...
[http://www.amule.org/wiki/index.php/FAQ_aMule-es#.C2.BFQu.C3.A9_es_toda_esta_historia_sobre_el_conejo.3F](http://www.amule.org/wiki/index.php/FAQ_aMule-es#.C2.BFQu.C3.A9_es_toda_esta_historia_sobre_el_conejo.3F)

    Bueno, si puedes/n ayudarme, estaré agradecido... aprovecho para saludar; comento si encuentro alguna solución...
Hasta pronto

Guillermo

Pero te conectas a un servidor al menos? mira que con el amule recien instalado tenes que bajarte la lista de servidores, la lista de nodos kad y luego conectarte a las redes, y recien ahi te baja. Cual de todos los pasos te falla? y si ya hiciste todo, fijate abajo a la izquierda la pestaña errores y postea que error te tira. Salu2!!!!

---

### Post by guillermon on 2008-12-21
Estimado faktorqm: (o alguien que desee ayudarme)
     Tras varios días de intentos sobre lo que me has comentado, vuelvo a la carga con preguntas... No hay caso; es más, mi amule está "poseso", pues tiene comportamientos extraños... Entre ellos,(cosa que antes no pasaba, pues estaban verdes ambas flechas) ahora tengo ID baja. He leído cuanto foro pude clickear, pero no puedo solucionar. Pido entonces ayuda en esto: sé que tengo los puertos por defecto que se aconsejan bloqueados; esto a través de [http://www.amule.org/testport.php](http://www.amule.org/testport.php)  . También sé que aconseja cambiarlo en este caso a algún que vaya desde el 10000 al 65000 y pico. Ocurre que he estado probando varios y me dan todos cerrados. El único que me figura como abierto es 5000, pero no 5003 o 5004; cuestión que requiere el puerto tcp. Es entonces que sospecho que es mi proveedor de Internet que los cierra (aclaro que no tengo router, y mi conexión es cablemodem, siendo el modem modelo WebSTAR DPC2100; el proveedor figura como prima.com.ar).
    La opción de probar uno por uno la haría si sé que es la única opción, que tendré algo de éxito, y tener muchas ganas de hacer funcionar amule. La pregunta es: ¿hay alguna forma de saber qué puertos dispongo para hacer funcionar conexiones p2p? (netstat??)
     Desde ya muchísimas gracias. Buenas fiestas, buen año

PD: lamento faktorqm haber nuevamente hecho un post largo, y gracias por los consejos sobre los sistemas de discos, Seguramente volve&#341;é a preguntarte sobre ellos.

---

### Post by faktorqm on 2008-12-22
Y si el modem ese te esta filtrando los puertos... no tenes escapatoria! XD Proba activando ofuscacion de protocolo en las opciones del amule, quiza eso te ayude bastante.

Tambien podes probar puertos altos, tipo 50000 o 55000 o cualquiera entre 1000 y 65000 que te funcione. Si el 5000 lo tenes abierto empeza por ponerlo en tcp y si te conecta en alta ya esta, no recuerdo exactamente como era el tema, pero si tenes abierto uno ya alcanza. Proba y conta como te fue.

Por si las moscas, si queres hacer la prueba final de si es tu firewall o el modem, tira estos comandos en la consola y volve a probar.(no hace falta que copies uno por uno, copia todos y solo dale enter al ultimo, si no te deja, usar sudo para el primero, copiar hasta el final)

```
iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter

```

Salu2!!

---

### Post by guillermon on 2009-01-04
Bueno, luego de las fiestas continúo con la incognita del conejo... Antes que nada, felices fiestas (algo tarde) y muchas gracias por la paciencia de contestar! He hecho lo que sugieres (probando en la consola) y nada; los números grandes y chicos no funcionan (no los he probado todos, por supuesto). Tengo en tcp el puerto 5000, que es el único que sé que está abierto. Y hoy me dió ID baja; ayer creo, era alta... Otra cosa sobre la que no tengo respuesta en mis conocimientos es porqué a veces se inicia desde el comienzo del sistema y a veces no (cuando yo he borrado el comando de inicio -de modo gráfico-)... es un misterio para mi.
   Ahora mientras escribo se cambió la flechita de amarilla a verde... oh!, pero la descarga es muy lenta, y de una fuente (aún teniendo tasa de envío alta, y un buen tiempo haciéndolo)...
   Por otra parte, lo del protocolo de ofuscación, lo tengo activado; tenía desactivado "Aceptar solo conexiones ofuscadas", y lo clickié para probar...
   Bueno, si tenés (tienen) alguna otra idea desde ya agradecido. Saludo a todos!
Guillermo
PD: Otra pregunta: ¿no tendrá que ver en que no puedo acceder a conexiones TCP algo que observé en "Ventada de Entrada", donde en la pestaña Seguridad dice un Ítem "Denegar las conexiones TCP al servidor Xserver" ?

---

