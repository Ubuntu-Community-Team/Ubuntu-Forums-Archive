---
title: "Chat MSN + Webcam"
date: 2010-07-26
forum: Software
---

### Post by biale on 2010-07-26
Gente, les voy a pedir una ayudita...

Se trata de una computadora de escritorio que tienen Ubuntu instalado y la idea es poder chatear con soporte de webcam. La PC pero no tiene webcam propia, pero las notebooks que andan dando vueltas por alli si tienen.  Hasta ahora en modo texto todo OK

O sea que se intentaríamos recibir imágenes, aunque sabemos que (por ahora) no podríamos enviarlas.  Protocolo de chat: MSN/ WLM. 

Mis consultas son...

(1) Que aplicación podría usar y que a Uds les este dando buenos resultados. No me interesa si es gtk o qt, basta con que funcione. Por ahora esta instalado emesene 1.6.1 y kopete 1.0.0.  

(2) Tengo que instalar/ configurar algún paquete especial? De lo que pude googlear, hay problemas con el protocolo MSNP18  (?)

(3) El adaptador ADSL esta configurado en modo router y filtrando puertos. Algún port para direccionar?

(4) ¿Alguna opción “no MSN” de alternativa y que tenga base de usuarios?  Por ahí vi que sugerían pasarse directamente a Skype!  Ademas y si no entendí mal, algunos protocolos (chat) hasta permiten compartir el escritorio,  es cierto?

Tengan en cuenta que como yo personalmente rara vez chateo puedo desconocer cosas muy elementales del tema.

Agredezco desde ya las respuestas y paso un saludo a todos.

---

### Post by alfplayer on 2010-07-26
Hace mucho que no veo este tema, pero por lo que sé, el video funciona mal, o no funciona, y si funciona MS puede cambiar algo de su red que lo vuelva incompatible.

Para llamadas de video el número uno se dice que es Skype, que funciona aceptablemente en linux.

Empathy tiene funcionalidad para compartir escritorio, pero creo que no funciona con windows.

---

### Post by erjoalgo on 2010-07-26
Para compartir escritorio usa TeamViewer, es excelente y gratis, ademas puede conectar windows con linux.

---

### Post by alfplayer on 2010-07-26
Teamviewer es propietario. El mejor sistema es VNC en mi opinión (también se puede conectar con windows), pero depende del tipo de uso.

---

### Post by pabletesss on 2010-07-26
Buenas noches, hace bastante que no uso Linux, pero vi pcs con Ubuntu haciendo video-llamadas a través del protocolo de WLM, no recuerdo si es con el AMSN o con EMESENE. Hace unos días instale Ubuntu Lucid Lynx Netbook Remix en mi Netbook porque me canse de Win2 y por cuestiones de trabajo estuve configurando la conexión por RDP. Es bastante simple y rápido, es otra alternativa para compartir el escritorio, pero si hay que elegir me quedaría con el VNC. Depende del uso que se le va a dar. Si solo necesitas acceder a equipos windows y no queres instalarle ningun soft adicional a dichos equipos podes habilitarles el acceso por RDP y acceder con el cliente RDP de GNOME (el cual soporta tambien los protocolos VNC y SSH).

> 
Si no me equivoco lo instale con el comando:
sudo apt-get install gnome-rdp


En caso de que sea al revez, conviene utilizar VNC y habilitar el acceso por web java, ya que es bastante comodo. Son todas alternativas a evaluar dependiendo de lo que necesites.
Voy a probar el tema de las videollamadas a ver si puedo configurar todo y te aviso como me fue, ya que es algo que necesito usar en el futuro.

---

### Post by biale on 2010-07-27
Si nadie dice "estoy usando MSN + Webcam" es muy probable que simplemente no este funcionando. MS tuvo que introducir cambios en el protocolo, la duda sería mas "si el software libre ya se adapto a esos cambios".

¿alguien probo Google o yahoo como alternativa a MSN?

El tema del acceso al escritorio era secundario, pero ya que salió vale la pena elaborarlo.

Bajo red local o internet acotada acceder al escritorio es bastante simple. Pero este es un caso muy particular. La otra PC se encuentra en la zona de Bariloche, no puedo saber rápidamente que equipo es, que versión de Win tiene, como se conecta a la internet, que firewall esta dando vueltas por alla. Y para colmo es una situación que se da durante una semana y cada 6 meses.

Tiene que ser algo muy "ad-hoc". Y me parece que para un caso así Teamviewer sería la posta. El tema firewall ajena pesa demasiado. Y además el cliente de Teamviewer bajo Windows corre sin instalación, no dejaría ningún problema potencial en el equipo.

"Windows a Windows" y en red local, el protocolo rdp es muy cómodo, Pero Ubuntu a Ubuntu no lo pude hacer funcionar, Interesante: no había considerado los casos Ubuntu a Windows (cliente rdp) & Windows a Ubuntu (VNC+Java) como pensables en forma independiente/ separada.

De nuevo agradezco las respuestas, y saludo a todos.

---

### Post by granjero on 2010-07-27
yo uso emesene + webcam y amsn + webcam con buenos resultados. también skype + webcam com mejores resultados.

tengo el router configurado así (imagen) 

nota: el router se confiró solito cuando le puse add msn en una opción que tiene.

salud!

---

### Post by granjero on 2010-07-27
me olvide la imagen

---

### Post by guillermolisi on 2010-07-27
> **biale said:**
> Si nadie dice "estoy usando MSN + Webcam" es muy probable que simplemente no este funcionando. MS tuvo que introducir cambios en el protocolo, la duda sería mas "si el software libre ya se adapto a esos cambios".

Mi mujer utilizo webcam con aMSN usando Ubuntu 9.04/9.10 (Bangho FIT, webcam USB).

>  ¿alguien probo Google o yahoo como alternativa a MSN?
Todo el tiempo ya que uso GTalk/Jabber preferentemente, junto con MSN, desde Kopete. Eso si, nada de webcam porque no le veo mucho sentido (por ahora).

> El tema del acceso al escritorio era secundario, pero ya que salió vale la pena elaborarlo.

Bajo red local o internet acotada acceder al escritorio es bastante simple. Pero este es un caso muy particular. La otra PC se encuentra en la zona de Bariloche, no puedo saber rápidamente que equipo es, que versión de Win tiene, como se conecta a la internet, que firewall esta dando vueltas por alla. Y para colmo es una situación que se da durante una semana y cada 6 meses.

Tiene que ser algo muy "ad-hoc". Y me parece que para un caso así Teamviewer sería la posta. El tema firewall ajena pesa demasiado. Y además el cliente de Teamviewer bajo Windows corre sin instalación, no dejaría ningún problema potencial en el equipo.

"Windows a Windows" y en red local, el protocolo rdp es muy cómodo, Pero Ubuntu a Ubuntu no lo pude hacer funcionar, Interesante: no había considerado los casos Ubuntu a Windows (cliente rdp) & Windows a Ubuntu (VNC+Java) como pensables en forma independiente/ separada.

De nuevo agradezco las respuestas, y saludo a todos.

Cuando accedes via rdp/remote desktop contra una PC que tiene habilitado ese acceso, el escritorio remoto queda bloqueado al usuario con un cartel que avisa que se esta utilizando remotamente (caso Ubuntu). Esto no sucede con VNC.

Usando RDP contra un Terminal Server en un Windows 2003/2008 server, tampoco hay bloqueo de escritorio remoto. Detalles para considerar.

---

### Post by biale on 2010-07-28
Bien, si granjero en este momento usa Webcam + MSN significa que en principio se puede...

Ya actualice al emesene via ppa. Hay un cartel en el sitio que invita a hacerlo.

Ajusto mi firewall (vetusto Zytel 600 vs 1), cruzo los dedos y paso la posta a mi usuaria final. Y corto aqui, porque no puedo asegurar el funcionamiento de una PC que esta a quichicientosmil Km de distancia.

Un saludo a todos.

---

### Post by alfplayer on 2010-07-28
Hay varios programas de mensajería, cada uno con distintas versiones, en distintos sistemas (linux, windows, etc.), y cada sistema también con distintas versiones. Son muchas variables. Hay probabilidades muy altas de falla, no es confiable.

---

