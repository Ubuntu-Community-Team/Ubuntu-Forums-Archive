---
title: "Crear web en ubuntu"
date: 2009-06-11
forum: Software
---

### Post by giov on 2009-06-11
Sres.

quiero crear un sitio web no muy complejo creo que en html, con flash, formularios y si pillo plantillas de web  espectacular,  que mejor que preguntarles a quienes conocen mejor que yo este sistema...     con que recursos cuento en ubuntu jaunty para hacer este sitio, acudo a su experiencia la idea es llegar a hacer un buen sitio.


Giov

---

### Post by CarlosRuiz on 2009-06-11
Holap:

Te recomiendo los siguientes links:
[http://carlosruizortega.wordpress.com/2008/07/16/servidor-web-en-ubuntu/](http://carlosruizortega.wordpress.com/2008/07/16/servidor-web-en-ubuntu/)
[http://carlosruizortega.wordpress.com/2008/07/27/servidor-web-en-ubuntu-ii/](http://carlosruizortega.wordpress.com/2008/07/27/servidor-web-en-ubuntu-ii/)

Para usar PHP, después de instalar apache puedes instalar lo siguiente:
[B]sudo apt-get install libapache2-mod-php5
[/B] 
Saludooos :p

---

### Post by kamus on 2009-06-11
> **giov said:**
> Sres.

quiero crear un sitio web no muy complejo creo que en html, con flash, formularios y si pillo plantillas de web  espectacular,  que mejor que preguntarles a quienes conocen mejor que yo este sistema...     con que recursos cuento en ubuntu jaunty para hacer este sitio, acudo a su experiencia la idea es llegar a hacer un buen sitio.


Giov

Cuentas con el mejor software para servidor web del mundo en los repositorios principales, Apache (apt-get install apache), creo que con eso seria suficiente para lo que necesitas ;)

---

### Post by nopersona on 2009-06-11
También te recomiendo Joomla! que si bien no es exclusivo de Linux, si tiene un muy buen soporte al ser de codigo abierto. 

Joomla! Chile, qué mejor?

[http://www.joomla.cl](http://www.joomla.cl)

---

### Post by giov on 2009-06-11
pero de php   no se nada y menos de apache  si bien los he visto   lo encuentro algo complicado e intento hacer algo sencillo que pueda ejecutar rapido por eso opte por hacerla en html

---

### Post by CarlosRuiz on 2009-06-12
Holap:

Para montar un sitio web básico y simple en tu computador, prácticamente no se requieren conocimientos sobre apache... lo único que debes hacer es instalarlo (así: **sudo apt-get install apache2**), "copiar" el sitio web en la carpeta **/var/www** (en el caso de Ubuntu) y mantenerlo activado para que cualquiera que conozca tu dominio o IP pueda acceder a ella.

En cuanto a PHP, no es un lenguaje muy complejo (especialmente si lo que deseas es hacer cosas simples) y en internet hay muchísimos tutoriales... xD

Saludooos :p

---

### Post by giov on 2009-06-12
En todo caso quiero subir el sitio a un servidor ya que no contamos con ningún equipo que podamos conectar todo el tiempo a internet, y php lo puedo editar en modo gráfico como el html en kompozer o debo hacerlo solamente por codigos ya que por lo que he visto php puedes hacer muchos formularios, los foros, es como mas automatico. 
ahh y agradezco a todos quienes se animaron a ayudar :D

---

### Post by CarlosRuiz on 2009-06-12
Holap:

Si vas a subir tu sitio a un hosting pagado, entonces no tienes que preocuparte de nada, pues hasta el hosting más precario te ofrecerá la posibilidad de utilizar PHP (y la configuración de apache corre por cuenta de ellos). 
Lo único que deberás aprender a manejar es (probablemente) el famoso "CPanel" para administrar el sitio, pero la propia empresa te enseñará a hacerlo.

Editar PHP "gráficamente"? Eso no lo entendí... xD
Pero PHP es un lenguaje de programación como cualquier otro, por lo que puedes usar un IDE para que su manipulación sea más cómoda. 
Te recomiendo GEANY:
**sudo apt-get install geany**

Saludooos :p

---

### Post by CdK1 on 2009-06-12
Quieres crear una web con herramientas de Linux, o quieres hostear una web? o las dos cosas?...

---

### Post by giov on 2009-06-12
Quiero crear la pagina  el hosting sera pagado, editar la web como cuando ha haces en dreamweaver creas la web en tu pc y luego subes los archivos por ftp,  kiero solo crear todos esos archivos

Grax

---

### Post by CdK1 on 2009-06-12
Puedes usar los programas que usabas en WIndows, -wine- o bien usa prorgramas como NVU ([http://www.nvu.com/screenshots.html](http://www.nvu.com/screenshots.html)) etc...

---

### Post by rodrigovb-cl on 2009-06-12
Como siempre, la idea es tratar de usar lo menos posible software privativo y tratar, además, de no usar ubuntu como una plataforma para instalar programas de windows...

Para Linux, por ende Ubuntu, tienes varios editores, por ejemplo:

NVU (o Kompozer que son similares sino idénticos), se instala así en una consola:

```
sudo aptitude install nvu
```


Si quieres algo más potente puedes usar bluefish

```
sudo aptitude install bluefish
```

y otro más es screem

```
sudo aptitude install screem
```

Por supuesto que puedes instalarlos también usando synaptic, yo te recomendaría que los instales todos, los pruebes todos y decidas cual te gusta o acomoda más, la gracia del software libre, es eres libre de usar el que quieras ;).

---

### Post by giov on 2009-06-12
Bien amigo   creo que voy a comenzar asi  probando estas opciones, por otra parte otra duda  estos editan php asi como se edita el html (no es mucho lo que se de php pero si no es muy complicado podre aprender algo del tema).
Grax

---

### Post by rodrigovb-cl on 2009-06-12
Se me quedó uno en el tintero "quanta", dicen que es el más parecido a dreamweaber pero yo no lo conozco... lo voy a instalar también ;)

```
sudo aptitude install quanta
```

---

### Post by rodrigovb-cl on 2009-06-12
> **giov said:**
> Bien amigo   creo que voy a comenzar asi  probando estas opciones, por otra parte otra duda  estos editan php asi como se edita el html (no es mucho lo que se de php pero si no es muy complicado podre aprender algo del tema).
Grax

Varios de ellos si editan php, en realidad puedes editar php (o html...) hasta con un editor de texto, pero si te refieres a que te hace la vida más fácil... si, la respuesta es si.

---

### Post by giov on 2009-06-12
Los instale   vamos a probar como andan a ver que resultado dan.

---

### Post by AlvaroV on 2009-06-15
> **giov said:**
> Los instale   vamos a probar como andan a ver que resultado dan.

giov , yo trabajo sitios web exclusivamente con herramientas de Linux. Te aconsejo para trabajar que uses Kompozer (versión mejorada de NVU, añadir y quitar programas).Tiene algunos fallos, ya que es un sistema con poco desarrollo, pero te puedo asegurar que una vez que lo comiences a usar no vas a hechar de menos el dreamweaver. Programas como Quanta, bluefish y otros que te han señalado aquí son buenos si solo programas en código.

Para trabajar las CSS utiliza Cssed (añadir y quitar programas). Como programa FTP utiliza Filezilla (añadir y quitar programas). este último para subir archivos de imagenes y documentos en forma individual al hosting, ya que Kompozer se conecta al sitio y trabaja tus archivos html directamente ahí.

Saludos

---

### Post by augias on 2009-06-15
Hola! No quiero sonar elitista, porque en verdad soy muy amatuer en diseñar paginas web, pero yo solamente ocupo Gedit y filezilla (ultimamente para updates menores uso el ftp de nautilus. muy util!) para hacer paginas web. Bajé bluefish y veo que tiene herramientas utiles para insertar codigo y cosas por el estilo, pero siento que, sabiendo suficiente css y html (y si solamente vas a estar usando esos lenguajes), uno no precisa otra herramienta que un editor de texto. 

Es costumbre mia, pero uds que diseñan paginas con varias herramientas, quisiera aprovechar este topic para preguntarles cuales piensan uds que son las ventajas de usar una aplicacion dedicada para editar sus archivos css, html y php? Siempre es bueno oir otras experiencias y aprender mas. En mi caso, como gedit colorea muchos lenguajes de code, y el visor de errores de firefox, es mas que suficiente!  :)

---

### Post by Jonathan Dud Rodriguez on 2009-06-15
cuento corto y sacando partido a otras aplicaciones...
instalate "wine" y te bajas el "dreamweaver portable"
y listo...!


Saludos.

---

### Post by giov on 2009-06-15
Veo que existen variadas alternativas y estoy probandolas creo que es facil la alternativa del dreamweaver pero quiero conocer las que aki me estan ofreciendo, por otra parte buscando por aqui por alla llege a algo llamado joomla a ver si alguien sabe que es eso por que revise algunas paginas y no pude saber que es...  

Gracias por los aportes espero en un tiempo mas poder hacer esto con los nuevos.    :)

---

### Post by CarlosRuiz on 2009-06-15
Holap:

En ese caso te recomiendo KOMPOZER... es el equivalente al Frontpage de Windows... xD
**sudo apt-get install kompozer**

Saludooos :p

---

### Post by rodrigovb-cl on 2009-06-16
> **Jonathan Dud Rodriguez said:**
> cuento corto y sacando partido a otras aplicaciones...
instalate "wine" y te bajas el "dreamweaver portable"
y listo...!


Saludos.

Se que tu aporte es con buena intención, pero si vamos a ocupar los programas para windows en ubuntu... ¿no será mejor usar windows derechamente?... 

Este es el foro chileno de ubuntu y nosotros promocionamos el uso de software libre; sistemas operativos GNU/Linux en general y de ubuntu en particular, se que algunas veces no tenermos más alternativa que usar software privativo, pero habiendo alternativas libres, esa debe ser la elección de los miembros de esta comunidad.

---

### Post by giov on 2009-06-16
Rodrigo, tal vez estoy mal pero dentro de la gran promoción que se le hace y hacemos esta como uno de los mas importantes tips esta la libertad, y creo según mi apreciación que al decir usen software libre,  estamos limitando, osea quitando la libertad de elegir con que software trabajar, si bien comprendo que el objetivo es promocionar el software de licencia libre, creo que también debemos permitir al usuario ser libre de elegir su software independiente de su licencia, espero no polemizar, y pido no ocurra. 

Por otra parte de los software que han indicado, aun estoy en la difícil eleccion, considero que todos son mas que buenos, hasta el momento he probado bluefish, screem, kompozer y quanta,    difícil elección, aun estoy en los periodos de prueba y si alguien quiere seguir aportando bienvenido sea.

Les doy gracias por la cooperación.

---

### Post by Carlos C on 2009-06-16
> **giov said:**
> Rodrigo, tal vez estoy mal pero dentro de la gran promoción que se le hace y hacemos esta como uno de los mas importantes tips esta la libertad, y creo según mi apreciación que al decir usen software libre,  estamos limitando, osea quitando la libertad de elegir con que software trabajar, si bien comprendo que el objetivo es promocionar el software de licencia libre, creo que también debemos permitir al usuario ser libre de elegir su software independiente de su licencia, espero no polemizar, y pido no ocurra. 

Estoy de acuerdo con que cada uno tiene la libertad de elegir, pero debo manifestar mi desacuerdo con simplificar las cosas al punto de decir "instalate "wine" y te bajas el "dreamweaver portable y listo". No se dan las razones de la recomendación y se plantea esta elección como si continuar usando herramientas privativas fuera sinónimo de hacerse la vida fácil. Creo que este foro pretende resolver consultas y facilitar que los usuarios conozcan las posibilidades que brinda el sistema. Cuando se recomienda una herramienta que debe correrse con wine, mínimo se debe recomendar con seriedad. Tú escoges con qué software trabajar, pero recuerda cuál es la función del foro.
Es mi opinión y no lo digo para agredir a nadie.
Saludos.

---

### Post by moreback on 2009-06-16
He visto que se recomienda software propietario más que nada porque lo usan crackeado, creo que hay poca gente que realmente se lo compra. Y esto es una mala costumbre que se trae por mucho uso de Windows y por bolsillos sin plata o definitivamente tacaños.

La idea es que el software privativo no es malo, pero si lo vas a usar, por lo menos cumple sus normas y comprate una licencia.

No sé que tan legal es ese Dreamweaver portable, pero tengo la impresión que no.

Saludos.

---

### Post by giov on 2009-06-17
> **Carlos C said:**
>  No se dan las razones de la recomendación y se plantea esta elección como si continuar usando herramientas privativas fuera sinónimo de hacerse la vida fácil. Creo que este foro pretende resolver consultas y facilitar que los usuarios conozcan las posibilidades que brinda el sistema. Cuando se recomienda una herramienta que debe correrse con wine, mínimo se debe recomendar con seriedad. .

Carlos   me gusto tu respuesta creo que las fundamentaciones son lo que convence, como les dije antes espero no se polemice  por que no fue ese el objetivo con el que habri este hilo, con la intención de discutir esto, si no que ver el tema de creación de web disculpen por haber comenzado con crear polemica, pero soy un convencido de que las conversaciones habren posibilidades.

Por otra parte y retomando el tema KOMPOZER o QUANTA traen algún corrector de ortografía?
Otro problema se genera al colocar acentos gráficos los que derrepente se muestran en los navegadores con otros símbolos.


Gracias

---

### Post by AlvaroV on 2009-06-17
> **giov said:**
> Por otra parte y retomando el tema KOMPOZER o QUANTA traen algún corrector de ortografía?
Otro problema se genera al colocar acentos gráficos los que derrepente se muestran en los navegadores con otros símbolos.


Kompozer no trae corrector ortográfico (no uso quanta). Ahora creo que google es un muy buen ayudante para la corrección, por lo demás yo jamás dejaría la corrección ortográfica en manos de una máquina. 

Ahora con respecto al tema de los acentos (tildes) sería bueno explicaras en que momento te esta ocurriendo.

Y ya que de lo que se trata es de aportar sería bueno informarse que después de un largo tiempo sin avances Kompozer a revivido de sus cenizas y anuncia la salida de una nueva versión ver en: [http://kazhack.org/?post/2009/05/14/KompoZer-0.8a4](http://kazhack.org/?post/2009/05/14/KompoZer-0.8a4) así de la 0.7 que permaneció como 3 años estancada estaríamos listos para pasar a la 0.8. Sería una buen oprtunidad de darle una mirada.

---

### Post by giov on 2009-06-17
Existe algun lugar desde el cual sacar plantillas web para kompozer???

Del problema de los acentos  no me ha mostrado desde que comenze con kompozer el problema fue en quanta,   

gracias

---

### Post by AlvaroV on 2009-06-17
> **giov said:**
> Existe algun lugar desde el cual sacar plantillas web para kompozer???

Del problema de los acentos  no me ha mostrado desde que comenze con kompozer el problema fue en quanta,   

gracias

Plantillas para que. El problema es que no explicitas que tipo de web quieres y para que. eso es lo primero que tienes quedecir para poder ayudarte. ¿Quieres una web de noticias? o institucional, que?

---

### Post by giov on 2009-06-18
Disculpa, estoy viendo para hacer una web a una cia de bomberos de mi localidad, porfa   a ver si tienen algun lugar de donde pueda sacar

Gracias

---

### Post by CdK1 on 2009-06-18
[quote=rodrigovb-cl;7446589]Como siempre, la idea es tratar de usar lo menos posible software privativo y tratar, además, de no usar ubuntu como una plataforma para instalar programas de windows...




La verdad no veo la razón de pensar así, la idea de usar un determinado S.O es la comodidad mientras más comodo y a gusto te encuentres mejor, da lo mismo lo que hagas para conseguirlo...

---

### Post by moreback on 2009-06-18
> **CdK1 said:**
> La verdad no veo la razón de pensar así, la idea de usar un determinado S.O es la comodidad mientras más comodo y a gusto te encuentres mejor, **da lo mismo lo que hagas para conseguirlo**...

¿O sea que está bien dar tips para instalar programas pirateados? Na que ver.

No veo problema en usar software privativo, pero mientras respetes su contrato de licencia, lo cual generalmente significa pagar ($$$) la copia que tienes.

Saludos.

---

### Post by CdK1 on 2009-06-18
Me refiero a la instalación,s ea mediante wine, cedega sepa moya, además respecto a programas pirateados... todavía no conozco a un particular que tenga alguna licencia... ya sea de Windows, o haya pagado por un juego..., tú pagas por tus juegos? o si en tu casa hay Windows, pagaste la licencia? ;)

---

### Post by moreback on 2009-06-18
Tengo licencia de Vista Bussines, venía con el notebook, casi no la uso.
No tengo juegos, no los necesito.
Uso 100% Ubuntu, tanto en la casa como en la pega.

Por favor, nada de ataques hacia mi persona. Céntrese en el tema, aunque ya se desvirtuó.

Saludos.

---

### Post by CdK1 on 2009-06-18
Son dudas, no ataques...

---

### Post by giov on 2009-06-18
pero el hilo no es para esto

Sorry

---

### Post by Carlos C on 2009-06-18
Giov abrió este hilo para ver qué herramientas están disponibles en Ubuntu para crear un sitio web. El tema se ha ido desviando a otra discusión, en parte por mi culpa, lo admito. Por favor, de ahora en adelante quien intervenga en este hilo que se centre en el tema. Si alguien desea abrir otra discusión puede hacerlo en el subforo Comunidad. De ahora en adelante, quien no respete el objetivo a tratar en este thread me obligará a borrar su entrada.

Saludos y espero que no terminen enojados, que no vale la pena.

---

### Post by AlvaroV on 2009-06-18
El problema amigo que este es un sitio para dar soporte a Ubuntu y no para hacer cursos de diseño web. Antes de ofrecerte para hacer un sitio web sería conveniente que tomes un curso para ello. Ya que tu problema es que ni siquiera eres capaz de explicar lo que quieres.

---

### Post by giov on 2009-06-20
Sres.   que es joomla   alguien sabe como es y como se usa, me llama la atencion

Gracias

---

### Post by aledruetta on 2009-06-20
> **giov said:**
> Sres.   que es joomla   alguien sabe como es y como se usa, me llama la atencion

Gracias

Podrías crear un hilo con esa pregunta. A mí también me interesa, pero no sería éste el lugar para tratarlo. He visto que en Google hay mucha información, pero no estaría mal escuchar opiniones de primera mano.

Saludos,
Alejandro.

---

### Post by giov on 2009-06-20
Creo que este hilo se encuentra bien ya que en ninguna parte se limita a un tipo de software para creación de web si no que se consulta por las herramientas que existen para ello


Salu2

---

### Post by moreback on 2009-06-20
[Joomla]("http://en.wikipedia.org/wiki/Joomla") que yo sepa es un [CMS]("http://en.wikipedia.org/wiki/Content_management_system"), por lo que no tiene mucho que ver con este hilo.

---

