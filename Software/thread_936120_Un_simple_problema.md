---
title: "Un simple problema"
date: 2008-10-02
forum: Software
---

### Post by franqiiitooo on 2008-10-02
Hola Gente de Ubuntu, me presento soy Franco, me acabo de registrar, hace 1 o 2 dia instale Ubuntu 8.04.1 LTS adentro de Win$, como soy novato, no entiendo mucho sobre este facinante SO, pero qiero aprender, en fin, obviamente el problema es con esto, les cuento.. cuando prendo la pc, me sale cargando el GRUB, termina de cargar y me salen las opciones con cual SO qiero empezar, hay 3 opciones de ubuntu, otra qe me dice de otro SO, y la de Win$, el problema va a aca, cuando elijo la opcion de Ubuntu, no me deja, empieza a cargar la barrita de inicio de Ubuntu, y ahi se qeda, y despues me sale algo como una terminal qe me dice "Help",  y de ahi no entiendo, las otras opciones son (Memtest) obviamente me hace un test del SO de ubuntu, y la otra opcion me sale otra terminal qe sale cargando letras, y cuando entro con Win$ , me entra lo mas perfecto... y me dijieron qe tengo qe editar la entrada del GRUB, y no entiendo mucho eso, y es asi en ese caso, expliquemenlo o caso contrario diganme cual es el problema


Atte. Franco :)


PD: mi pc tiene 240 de ram, cuando insertaba el Live CD, me andaba bien, pero me tarda un poquito en abrir las ventanas

---

### Post by guisheca on 2008-10-02
Hay algo que no entendí bien: como es eso que instalaste ubuntu dentro de win, y te sale el grub?? si lo hiciste dentro de win, te tiene que salir un menu común de elección de SO.
Pasando eso por alto, en cual de las tres opciones del ubuntu entrás??
Otra cosa, el memtest lo que hace es un test de memoria ram.
Disculpá que no te dé una solución así de una, pero hay que recopilar un poco mas de info, ya vamos a dar en la tecla.
Saludos

---

### Post by franqiiitooo on 2008-10-02
si, si, instale Ubuntu dentro de win, y me sale un tal grub, y me sale el menu ese qe decis de eleccion de SO, pero no sê como es ese tal menu ami me sale fondo negro y letras de microsof* blancas, no se si vos lo tenes tambien, y no se en cual opcion de ubuntu entro, ya qe tengo qe reiniciar la pc y fijarme, si me contestas rapido te puedo decir rapido, ya qe me tengo qe ir al colegio, sino, me conecto a las 7.30 y me fijo si me contestaste

---

### Post by ramiro_md on 2008-10-02
Letras de micro$oft interesante...
Bienvenido franco, por lo que describís estás en presencia del GRUB. Te digo que el problema para mi radica en que tenés 240 mb de ram, cuando lo base para ubuntu son 256 mb ojo con eso. Se me ocurre que por eso salta el memtest. Por otro lado un error de GRUB no puede ser sino te diria "error de grub número tanto".
Probá Xubuntu, es ubuntu pero con xfce (entorno de escritorio) por defecto. Es más liviana que ubuntu, creo que con 128 mb corre. NUnca la probé en maquinas de ese estilo asique no te puedo decir mucho sobre xubuntu. Espero haberte ayudado, suerte y un saludo.

---

### Post by franqiiitooo on 2008-10-02
De hecho, cuando me respondio "guisheca" probe para fijarme en qe opcion de ubuntu entraba, y entre, me entro a Ubuntu, estube jugando al Ajedrez un ratito, y despues probe de nuevo, y no me entro :( , Emm, pero mi opinion no tiene qe ver con 240 de ram, me andaba muy bien, no se cual es el problema, qisiera qe me ayuden por Msn, asi es mas facil para mi, pero por motivos del foro, no puedo dar datos personales, asiqe no se como puedo hacer

---

### Post by ramiro_md on 2008-10-02
MIrá franco, en esto de las computadoras todo puede ser. Los reqeurimientos mínimos de ubuntu no los cumplís por muy poco, por eso tal vez te ocurrió que pudiste entrar al sistema, pero a la primera que lo hiciste sufrir un poco se cayo (n). 
Te sugiero que postees todo acá, ayudas por msn serían muy egoístas, debido a que otro puede tener tu problema y si vos no compartís esa información se pierde el sentido a todo esto. Para eso está la comunidad.Un saludo.

---

### Post by franqiiitooo on 2008-10-02
[FONT="Century Gothic"][COLOR="Green"]Bueno, muchas gracias por comentar....

Un saludo grande a todos[/COLOR][/FONT]

---

### Post by ramiro_md on 2008-10-02
No hay por que, acá siempre vas a encontrar alguien que te de una mano (te lo digo por experiencia, siempre me ayudó postear en este foro). 
Te recomiendo que antes de llegar a la instancia de preguntar acá, googlees un poco (hay grandes cantidades de data sobre ubuntu y linux en general), si google no te ayudó, buscá acá con el buscador (parte superior izquierda de la página xD). Si eso tampoco te sirvió a encontrar lo que buscabas, abrí un nuevo thread =).
Volviendo al tema de tu problema, haceme caso, intenta instalando xubuntu y comentá como te fue.
Un saludo. Y que tengas suerte.

---

### Post by faktorqm on 2008-10-03
Hola, che igual te deberia andar, acá tenés la prueba:

```

faktorqm@the-edge:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           185        178          6          0          1         50
-/+ buffers/cache:        126         58
Swap:          729        100        628
faktorqm@the-edge:~$

```

igual deberia decir 192mb (256mb menos 64mb de video) pero bueno...
Te recomiendo que instales, si no te anda o te anda lento, xubuntu. Es mucho mas rapido, perdes algunas funcionalidades pero nada que no puedas superar. Si te sigue pareciendo lento, podes seguir con fluxbuntu, mas liviano todavia. Si no te gusta, otro grosso que podes probar tambien es Elive Gem, que es un debian con escritorio enlightment.

Si con el ubuntu que tenes instalado ahora no te anda, intenta entrar en modo recuperacion o contanos EXACTAMENTE que ocurre, paso a paso, desde que prendes la compu, ves el grub y entras o no a ubuntu. salu2!

---

### Post by ramiro_md on 2008-10-03
Che y si prueba instalando con un alternate cd ?

---

### Post by faktorqm on 2008-10-03
si podria, pero no veo que haga la diferencia llevar a cabo esa accion...

guisheca: tengo entendido que instalo ubuntu mediante wubi, un programa que (yo nunca lo use) te instala ubuntu partiendo de windows digamos. (Igual creo que hay 2 modos, uno como programa directamente y otro que te lo instala desde windows)

para editar las opciones de arranque del grub, te paras sobre la que inicia y apretas la letra "e". entonces te deja editar (son solo por esa iniciada digamos, si reinicias esos cambios se borran) la linea con la que arrancas la pc. ahi podrias probar de cambiar la palabra "splash" por "nosplash", asi que en lugar de ver la barrita naranja, ves los mensajes de error que te tira el kernel, cuando se congela, anotas lo que dice y asi nosotros capaz te podemos ayudar mejor.
Otra cosa que podes probar tambien es agregar estos parametros a la linea "apic=noapic" (sin comillas).

Mas alla de todo eso, con 240mb de ram te conviene bajarte la iso del xubuntu, e instalarte eso en modo alternate como dijo aca Ramiro y vas a difrutar de mas velocidad que ubuntu normal (xubuntu esta pensado para pc's mas viejas, pero es lo mismo que el resto de los *buntus). Salu2!

---

### Post by ramiro_md on 2008-10-04
No, no instaló con wubi, estuve chateando con el pibe y le comenté que todos pesnabamos eso y su respuesta fue: ¿qué es wubi?. Se equivocó, quizo decir que instaló en particiones diferentes.

---

