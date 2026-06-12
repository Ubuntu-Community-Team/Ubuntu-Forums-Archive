---
title: "Problema Emathy no muestra mi imagen en MSN"
date: 2010-10-17
forum: Software
---

### Post by 3nG3ndR0 on 2010-10-17
hola bueno como dice el titulo uso ubuntu 10.10 todo bien excepto en empathy que no me deja cambiar ni mostrar mi imagen del protocolo MSN, ¿ a alguien  mas le sucede lo mismo  o si hay solucion?

---

### Post by themasterdark on 2010-10-17
una "solucion" sería que uses otro software para el protocolo msn, podría ser:

amsn
emesene

ambos estan en los repositorios de ubuntu.

Saludos

---

### Post by 3nG3ndR0 on 2010-10-18
> **themasterdark said:**
> una "solucion" sería que uses otro software para el protocolo msn, podría ser:

amsn
emesene

ambos estan en los repositorios de ubuntu.

Saludos

pf para esa respuesta o creo el tema, quiero saber si a alguien mas tiene el problema o es que ami me esta funcionando mal

---

### Post by themasterdark on 2010-10-18
no es forma de contestar esa, si contestas asi no preguntes entonces.

PD: no tengo problemas con empathy.

---

### Post by RafaelG on 2010-10-18
Estimados Colegas Ubunteros,

Segun los comentarios emitidos en este post se estaria incumpliendo con el codigo de conducta que a continuacion dejo parte puntual donde se hace alusion a como debemos tratarnos unos a otros en la Comunidad Ubuntu. 

**Codigo de conducta Link oficial de Ubuntu: ****[http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct)**

*""Ser respetuosos."" La comunidad Ubuntu y sus miembros se tratan unos a otros con respeto. Todo el mundo puede hacer una valiosa *[I]contribución a Ubuntu. Puede que no siempre están de acuerdo, pero los            desacuerdos no es excusa para el mal comportamiento y los malos modales. Todos puedemos experimentar algo de frustración de vez en cuando, pero no podemos permitir que la frustración se convierta en un ataque personal. Es importante recordar que una comunidad donde la gente se sienta incómodo o amenazada no es productiva. Esperamos que los miembros de la de la comunidad Ubuntu sean respetuosos cuando se trata de otros contribuyentes, así como con personas fuera del proyecto Ubuntu y con los usuarios de Ubuntu.

'''Be respectful.''' The Ubuntu community and its members treat[/I][I]
      one another with respect. Everyone can make a valuable
      contribution to Ubuntu. We may not always agree, but disagreement
      is no excuse for poor behaviour and poor manners. We might all
      experience some frustration now and then, but we cannot allow that
      frustration to turn into a personal attack. It's important to
      remember that a community where people feel uncomfortable or
      threatened is not a productive one. We expect members of the
      Ubuntu community to be respectful when dealing with other
      contributors as well as with people outside the Ubuntu project and
      with users of Ubuntu.
[/I]  
[B]Codigo de Conducta del Foro Link Oficial Ubuntu: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
[/B] [I]
"El propósito de los foros de Ubuntu es proporcionar apoyo para Ubuntu. También queremos que se trate de un lugar donde la comunidad puede desarrollar y podamos disfrutar de su mutua compañía. Para  ello, nos esforzamos por mantener una atmósfera que puede ser  disfrutado por todos, y pedimos a todos los miembros de la comunidad a  ser respetuosos en todo momento. Esto significa que por favor, utilice la etiqueta y la cortesía. Tratar a la gente con amabilidad, gentileza y respeto. Si lo hace, el resto del código de conducta no necesitará más que una mención superficial."

"The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with kindness, gentleness and respect. If you do this, the rest of the code of conduct won't need more than a cursory mention."
[/I]

Por todo lo explicado anteriormente en el codigo de conducta, se agradeceria que para poder optimizar  las respuestas de los usuarios unos a otros, mantener la buena convivencia y continuar con el normal funcionamiento del foro en Chile es necesario utilizar este codigo de conducta que es fundamental he importante para poder ingresar post y comentarios en el mismo. Me despido de ustedes agradeciendo su comprension en todo lo explicado anteriormente de mi parte.

Saludos!

---

### Post by 3nG3ndR0 on 2010-10-21
para cerrar el tema ya lo solucione de esta manera  agregando la PPA for Telepathy:

```
sudo apt-add-repository ppa:telepathy/ppa
sudo apt-get update
sudo apt-get upgrade

```
listo reinicias empathy y soluciona el bug

---

