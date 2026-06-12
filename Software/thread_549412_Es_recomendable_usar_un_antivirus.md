---
title: "Es recomendable usar un antivirus?"
date: 2007-09-12
forum: Software
---

### Post by niko_3100 on 2007-09-12
Bueno gente eso, es recomendable en una compu hogareña instalar un antivirus para ubuntu? No era que no existian virus para linux? Por que estan esos antivirus hasta hay un avg para linux... :confused:

---

### Post by ubuntu27 on 2007-09-12
Hola Niko. Bienvenido a la comunidad Ubuntu, y al Sistema Operativo UBuntu GNU/Linux.

Los Antivirus no son necesario en maquinas con GNU/Linux, puesto que no existe virus en wild (corriendo por aqui y por alla, contagiendaose a cada makina y distribuyendose).

Existe aproximadamente 40 Virus para Linux, pero ellos estan confinadas en el laboratorio. Osea son virus que fue creado para probar la seguridad de Linux. Esos virus no pueden llegar a tu computadora. 

Los antivirus que se usan en GNU/Linux son para scanear maquinas que tengan Windows en la red. O simplemente para gente que usan servidores y quieren buscar virus que pueden dañar la computadora de sus clientes que la mayoria usa WIndows.

Puedes recivir un archivo infectado con un virus, pero no te hara nada, puesto que esta hecha para WIndows nada mas. WIndows y Linux no son compatibles. 

En si, aunque el sistema operativo es seguro, hay que ser inteligentes tambien. SE dice que es mejor tener un usuario sabio sin antivirus ni ninguna proteccion, que un usuario tonto con todo tipo de proteccion. Un usuario tonto de alguna manera logra romper su propuia proteccion que esta instatalada.

NO te preocupes, no necesitas isntalar ANtivirus. :)

---

### Post by niko_3100 on 2007-09-12
Ja buenisimo en realidad *******.... con el synaptics encontre un avg y dije "que al dope que esta esto aca" pero ahora que me explicaste no es tan asi. Por suerte mi notebook con ubuntu anda barbaro por eso me dio temor ver un antivirus y no tenerlo instalado. Gracias por la data.

---

### Post by Mafber on 2007-09-12
Hola Niko_3100!!! Adhiero a lo que te dice Ubuntu27. Es más, recuerdo una vez que instale el antivirus de panda.... tuve que reinstalar mi ubuntu :(
Por otro lado, si te recomendaría que uses un firewall, con eso tenés toda la protección que se necesita.
Suerte!!!

---

### Post by ubuntu27 on 2007-09-12
> **Mafber said:**
> Hola Niko_3100!!! Adhiero a lo que te dice Ubuntu27. Es más, recuerdo una vez que instale el antivirus de panda.... tuve que reinstalar mi ubuntu :(
Por otro lado, si te recomendaría que uses un firewall, con eso tenés toda la protección que se necesita.
Suerte!!!

No problem Mafber. Ubuntu y muchas otras distribuciones ya vienen un Firewall. Se llama "iptables" y corre desde que arracas Ubuntu. :)  

para configurar los iptables, debes de usar ciertos comandos en el terminal (lo cual yo aun no he aprendido), pero lo bueno es que hay una applicacion que es un frontend al iptables, al tener GUI (Graphic User Interface) te permite configurar haciendo clicks :)  

Hay dos o mas frontends al iptables, lo mas conocidos son firestarter (para GNOME, osea Ubuntu), kmyfirewall (KDE, osea Kubuntu) y guarddog (para KDE).

Todos ellos estan el erepositorio. 

Instalar un frontend de iptables para GNOME:

```
sudo aptitude install firestarter
```

---

### Post by msangil on 2007-09-12
hola niko, bienvenido!

mirá, si te sentís generoso (no es mi caso) podés instalarte un antivirus para que cada vez que te manden un archivo y después tengas que reenviar a otra persona te asegures que no le infectás la máquina.

...en todo caso para que no te culpen de que le infectaste la compu con un virus del cual ni te enteraste (alternativa menos altruista).

Mafber tiene razón con respecto a lo del firewall. Instalate rápido el Firestarter o en caso que tengas ya cancha editate las IP Tables para asegurarte que nadie te ande probando usuarios y contraseñas de tu sistema.

Un abrazo!

---

### Post by Mauro22 on 2007-09-12
De acuerdo con todos, con antivirus en linux, creo que lo unico que vas a lograr es quemar RAM y recursos.


Iptables es lo mejor!! :)

Una vez que le agarras la mano para editar las reglas a mano va todo joya, te recomiendo bajar el iptraf

```
sudo apt-get install iptraf
```

Despues lo corres desde consola, y ahi ves segundo a segundo las conexiones de tu pc.


PD: les dejo la regla basica para rechazar peticiones tipo PING

```
sudo iptables -A INPUT -p icmp -j DROP
```
Respetar mayusculas y minusculas :)

---

### Post by por100pre1 on 2007-09-12
Puedes buscar rootkits con chkrootkit y rkhunter.

Para instalarlos (en terminal):

```
sudo aptitude install chkrootkit rkhunter
```

Para usarlos:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

---

### Post by Mafber on 2007-09-12
Te recomiendo que mires esta [página]("http://es.tldp.org/Manuales-LuCAS/doc-guia-ubuntu-breeze/guia-ubuntu-htmls/aplicaciones-herramientas_del_sistema.html") en donde dice ¿Cómo instalar el Firewall Firestarter?
Suerte!!!

EDITO: no hagan caso a esta pagina que esta mal.

---

### Post by ubuntu27 on 2007-09-12
> **Mafber said:**
> Te recomiendo que mires esta [página]("http://es.tldp.org/Manuales-LuCAS/doc-guia-ubuntu-breeze/guia-ubuntu-htmls/aplicaciones-herramientas_del_sistema.html") en donde dice ¿Cómo instalar el Firewall Firestarter?
Suerte!!!

aunque la isntalacion de Firestarter sigue siendo lo mismo en diferente versiones de Ubuntu. Hay que tener en cuenta de que esa guia es para Ubuntu Breezy Badger. Hay cosas que no sirve para la version actual :)

UN ejemplo seria "¿Cómo instalar mondoarchive para hacer copias de seguridad bootables?" te da links a unas aplicaciones antiguas. 

> **por100pre1 said:**
> Puedes buscar rootkits con chkrootkit y rkhunter.

Para instalarlos (en terminal):

```
sudo aptitude install chkrootkit rkhunter
```

Para usarlos:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

se me olvido sobre los rootkits. :)  chkrootkit es bueno.

---

### Post by FlyerDie on 2007-09-12
gente, 99,9% peque de ignorante...pero hace unos años, cuando usaba SUsE, me "contagie" de algo que si mal no recuerdo era un root-kit, desconozco si era es el equivalente a un virus o que, pero tuve que correr un aplicativo para poder quitarlo.

Seguramente alguien con mayor experiencia sepa explicar que es el root-kit, pero dentro de lo que supe entender en su momento era algo como un virus.

---

### Post by Mafber on 2007-09-12
Ubuntu27: tenés razón se me pasó!! perdón :(
Por otro lado, mi intención era la de hacer que Niko_3100  vea como iniciar el Firestarter cuando arranca la pc y no le pida el pass.

---

### Post by Hei Ku on 2007-09-12
En realidad no es necesario correr el firestarter todo el tiempo.
Es simplemente una interfaz para las iptables, que en Ubuntu corren todo el tiempo. Lo que te conviene es correrlo, configurarlo, y cerrarlo. Y volverlo a abrir solo si tenes que cambiar alguna cosa, o queres chequear alguna cosa.

DE HECHO, recorde que como corre bajo root, no se recomienda tenerlo abierto todo el tiempo. Hace mucho tiempo vi una thread que hablaba sobre el tema, y la recomendacion, por los mismos desarrolladores de firestarter era justamente esa.

---

### Post by Mafber on 2007-09-12
Hei Ku: no sabia eso. Entonces por más que reinicie la pc no es necesario arrancar el firestarter? estoy muy acostumbrado al SO-aquel-que-no-debe-ser-nombrado (jajaja)

---

### Post by ubuntu27 on 2007-09-13
> **Hei Ku said:**
> En realidad no es necesario correr el firestarter todo el tiempo.
Es simplemente una interfaz para las iptables, que en Ubuntu corren todo el tiempo. Lo que te conviene es correrlo, configurarlo, y cerrarlo. Y volverlo a abrir solo si tenes que cambiar alguna cosa, o queres chequear alguna cosa.

...


Lo que dice Hei Ku es cierto :)

> **Mafber said:**
> Hei Ku: no sabia eso. Entonces por más que reinicie la pc no es necesario arrancar el firestarter? **estoy muy acostumbrado al SO-aquel-que-no-debe-ser-nombrado (jajaja)**

jeje, eso da risa. Dialogo de Harry Potter :P

---

### Post by Montsegur87 on 2007-09-13
De hecho , "aquel cuyo nombre no debe ser pronunciado" viene del Sauron del señor de los anillos

---

### Post by niko_3100 on 2007-09-13
Hay muchos que tienen esa frase para no nombrar al malo de turno. Entonces me reservo el hecho de instalar un antivirus, off topic mal pero bue: acabo de ver un documental de como inicio linux y todo ese movimiento, realmente es muy loco como sucedio todo y como de a poco fue ganando gente hasta llegar a ser lo que es hoy.

---

### Post by leo_rockway on 2007-09-13
> **niko_3100 said:**
> Hay muchos que tienen esa frase para no nombrar al malo de turno. Entonces me reservo el hecho de instalar un antivirus, off topic mal pero bue: acabo de ver un documental de como inicio linux y todo ese movimiento, realmente es muy loco como sucedio todo y como de a poco fue ganando gente hasta llegar a ser lo que es hoy.

que viste? revolution OS? ese esta bueno, hasta que aparece la placa del final...

---

### Post by por100pre1 on 2007-09-13
> **Montsegur87 said:**
> De hecho , "aquel cuyo nombre no debe ser pronunciado" viene del Sauron del señor de los anillos

¿No viene de las criaturas de [La Aldea]("http://www.imdb.com/title/tt0368447/")?

---

### Post by LaHire on 2007-09-13
Che, una pregunta off topic :P

alguien conoce algun buen tut de iptables?

---

### Post by por100pre1 on 2007-09-13
> **LaHire said:**
> Che, una pregunta off topic :P

alguien conoce algun buen tut de iptables?

[Aquí]("http://www.ubuntu-es.org/node/422") hay uno. Dime si te sirve. :)

---

### Post by Mister X on 2007-09-13
> **LaHire said:**
> Che, una pregunta off topic :P

alguien conoce algun buen tut de iptables?

Fijate en la pagina de abajo, hay de todo.

[TLDP-ES - Manuales]("http://es.tldp.org/htmls/manuales.html")

---

### Post by Montsegur87 on 2007-09-13
> **por100pre1 said:**
> ¿No viene de las criaturas de [La Aldea]("http://www.imdb.com/title/tt0368447/")?

No , si mal no recuerdo la cita que menciono se encuentra en la comunidad del anillo , cuando Gandalf le cuenta a Frodo la historia del anillo

---

### Post by por100pre1 on 2007-09-13
> **Montsegur87 said:**
> No , si mal no recuerdo la cita que menciono se encuentra en la comunidad del anillo , cuando Gandalf le cuenta a Frodo la historia del anillo

A duras penas miré **La Comunidad del Anillo**, así que por eso no recuerdo esa cita. Es por eso que confundí la cita con *los que no se nombran* de **La Aldea**.

---

### Post by Montsegur87 on 2007-09-13
me referia al libro.

---

### Post by leo_rockway on 2007-09-14
re offtopic, haha.

en el hobbit tampoco se lo llama por su nombre (no se si a tolkien no se le habia ocurrido todavia o que), pero cuando gandalf se va, se dice que se va a combatir al "nigromante".

---

### Post by je01091979 on 2009-06-26
> **ubuntu27 said:**
> Hola Niko. Bienvenido a la comunidad Ubuntu, y al Sistema Operativo UBuntu GNU/Linux.
 
Los Antivirus no son necesario en maquinas con GNU/Linux, puesto que no existe virus en wild (corriendo por aqui y por alla, contagiendaose a cada makina y distribuyendose).
 
Existe aproximadamente 40 Virus para Linux, pero ellos estan confinadas en el laboratorio. Osea son virus que fue creado para probar la seguridad de Linux. Esos virus no pueden llegar a tu computadora. 
 
Los antivirus que se usan en GNU/Linux son para scanear maquinas que tengan Windows en la red. O simplemente para gente que usan servidores y quieren buscar virus que pueden dañar la computadora de sus clientes que la mayoria usa WIndows.
 
Puedes recivir un archivo infectado con un virus, pero no te hara nada, puesto que esta hecha para WIndows nada mas. WIndows y Linux no son compatibles. 
 
En si, aunque el sistema operativo es seguro, hay que ser inteligentes tambien. SE dice que es mejor tener un usuario sabio sin antivirus ni ninguna proteccion, que un usuario tonto con todo tipo de proteccion. Un usuario tonto de alguna manera logra romper su propuia proteccion que esta instatalada.
 
NO te preocupes, no necesitas isntalar ANtivirus. :)
 
Hola Ubuntu27
 
Yo ya tengo instalado en mi sistema ubuntu 9.04 el antivirus AVG, pero como ya se que no lo necesito, lo quiero desinstalar, pero no se como hacerlo, es decir siento como si el programa de AVG esta oculto en el sistema operativo y por tanto no se como desinstalarlo. Espero puedas ayudarme con esto, y gracias

---

### Post by ubuntu27 on 2009-06-26
> **je01091979 said:**
> Hola Ubuntu27
 
Yo ya tengo instalado en mi sistema ubuntu 9.04 el antivirus AVG, pero como ya se que no lo necesito, lo quiero desinstalar, pero no se como hacerlo, es decir siento como si el programa de AVG esta oculto en el sistema operativo y por tanto no se como desinstalarlo. Espero puedas ayudarme con esto, y gracias

Como has instalado AVG ANtivirus? Has usando Gestor de Paquetes Synaptic, o has instalado manualmente bajando el instalador de la pagina de AVG?


Si has instalado usando *apt-get install* en el terminal o con *Synaptic*, entonces solamente abre Synaptic [Sistema/Administracion/Gestor de Paquetes Synaptic]
 busca AVG

Click derecho a los paquetes relacionados a AVG y seleccion desinstalar [B]completamente
[/B]

y click en Aplicar.


Suerte

---

### Post by aledruetta on 2009-06-27
> **Hei Ku said:**
> En realidad no es necesario correr el firestarter todo el tiempo.
Es simplemente una interfaz para las iptables, que en Ubuntu corren todo el tiempo. Lo que te conviene es correrlo, configurarlo, y cerrarlo. Y volverlo a abrir solo si tenes que cambiar alguna cosa, o queres chequear alguna cosa.

DE HECHO, recorde que como corre bajo root, no se recomienda tenerlo abierto todo el tiempo. Hace mucho tiempo vi una thread que hablaba sobre el tema, y la recomendacion, por los mismos desarrolladores de firestarter era justamente esa.

¿Lo mismo vale para UFW o GUFW?

---

### Post by guillermolisi on 2009-06-28
> **aledruetta said:**
> ¿Lo mismo vale para UFW o GUFW?
Siempre que cualquiera de esas alternativas necesite ser utilizada como root user, valdria la misma practica.

---

