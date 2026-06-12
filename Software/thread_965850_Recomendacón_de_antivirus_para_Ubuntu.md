---
title: "Recomendacón de antivirus para Ubuntu?"
date: 2008-10-31
forum: Software
---

### Post by Just64 on 2008-10-31
Algun antivirus para el Ubu 8.10? Firewall? y demas yerbas q piensen q tenga q instalar.

---

### Post by hictio on 2008-10-31
Firewall, tiene uno "interno" -por lo menos 8.04, asi que calculo que en 8.10 tambien esta- se llama 'ufw', por 'Ubuntu Firewall', o bien por 'Uncomplicated Firewall', es muy bueno, funciona como "front end" para iptables, con una sintaxis un poco mas sencilla e instrucciones bastante directas.

Igualmente hay un programa con GUI para administrarlo que se llama 'firestarter', abri Synaptic, click en 'Search' y tipea 'firestarter', instalalo.
Despues de instalado, para usarlo, lo accedes por "System -> Administration -> Firestarter"
Ubuntu viene sin el firewall activado porque tampoco viene con ningun servicio activo.

---

### Post by pol666 on 2008-10-31
no no pibe no. :P

Bueno antes que nada, bienvenido a ubuntu linux.

Te comento, no hay practicamente virus en gnu/linux, por lo que es obsoleto usar antivirus, si usas los programas de los repositorios y no bajas script ni ejecutables desconocidos (que tal vez no sean dañinos) estas a salvo.

---

### Post by PeTTi on 2008-10-31
No hace falta, me descargue 20 GB de Musica, Videos y otras cosas mas y todavia no tengo ningun virus :)

---

### Post by Jeff Seager on 2008-10-31
Avast! es eficaz para mí ...

[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

---

### Post by santiagoward2000 on 2008-11-01
Bienvenido Just64!
Mirá, por el tema de virus, como te dijeron antes, no hace falta. Casi no hay virus de para Linux, y menos si instalás los programas desde los repositorios de Ubuntu. La única razón por la que necesitarías un antivirus, sería para analizar algún archivo antes de copiarlo a una partición de Windows, mandarlo por mail o algo así. Para eso, en los repositorios hay uno que se llama **clamtk**.
Saludos!

---

### Post by victor_nesta on 2008-11-01
> **santiagoward2000 said:**
> Bienvenido Just64!
Mirá, por el tema de virus, como te dijeron antes, no hace falta. Casi no hay virus de para Linux, y menos si instalás los programas desde los repositorios de Ubuntu. La única razón por la que necesitarías un antivirus, sería para analizar algún archivo antes de copiarlo a una partición de Windows, mandarlo por mail o algo así. Para eso, en los repositorios hay uno que se llama **clamtk**.
Saludos!

Uhh a ver que onda, lo voy a probar. 
Graciela!

---

### Post by Kantier on 2008-11-02
> **Just64 said:**
> Algun antivirus para el Ubu 8.10? Firewall? y demas yerbas q piensen q tenga q instalar.

Hay un par de cosas que deberías saber acerca de lo que estás preguntando. Paso a explicar:

**Virus y antivirus:** Los virus son meramente una forma más automática de aprovechar una falla de segunridad para tomar control de una computadora, o romper el sistema, o hacer algo. los antivirus son programas que buscan cosas que parecen virus, o cosas que se ven como virus... pero idealmente, un sistema no debería permitir que se puedan aprovechar esas fallas de seguridad de forma TAN facil. Ubuntu arregla las fallas de seguridad rápido, así que el concepto de "virus" no se aplica. Además, no hay peligro de programas maliciosos porque todo lo que está en los repositorios es revisado por mucha gente muy hinchabolas, cosa que no pase nada malo ^_^


**Firewall:** Un firewall es un programa que limita lo que pasa a través de la red, y existe por cuestiones de seguridad. En windows hay muchos productos de firewall que miran los programas que está corriendo la computadora y manejan la seguridad al nivel de lo que le dejan o no hacer a cada programa. Si bien existen algunas cosas así en linux, el enfoque usual es usar el otro enfoque, que es filtrar lo que pasa por la conexión sin mirar de qué programa viene. Este otro enfoque es más facil de hacer, la parte del sistema que maneja redes ya viene preparada para que uno le diga qué dejar pasar y qué no (fijándose en protocolo, puerto, etc. de la información que pasa por la red).

Y de cualquier manera, si uno no deja un programa abierto que reciba comunicaciones, no hay necesidad de poner firewall (porque la computadora va a ignorar toda la información entrante que no esté esperando para recibir).

---

### Post by c4d0rn4 on 2008-11-02
la verdad quedé muy sorprendido por algunas respuesta. El avast de linux OMG!

con respecto a la persona que remarcó que después de bajar x cantidad de cosas; un tema fundamental es que la gran torta del mercado está distribuida a windows (guste o no). Entonces digamos que: para ser ""justos"" si existieran virus, la proporción en un p2p sería similar a los sistemas operativos [insertando números fruta] 90% win, 6% macOs, 4% linux-bsd-otros  [/insertando]

A modo de boba conclusión: si encontras un virus en internet tenés un 96% de probabilidades que sea más inofensivo que lasie atado y embalsamado.

Eso sin tomar en consideración especificación técnica alguna.

-------------

Por otro lado, nadie se va a animar a bajar un deb, sh, bin, run, rpm o lo que sea de un p2p.


Si tienen algo de que temer en linux, cosa que ningún antivirus podrá detenerlo, es el letro que tiene el foro, ese de Malicious Commands. [http://ubuntuforums.org/announcement.php?f=189](http://ubuntuforums.org/announcement.php?f=189)


Salvo algunas genialidades, en todos los sistemas operativos los virus se evitan con educación y criterio. Dentro de genialidades de virus, el blaster que se distribuía por windows update.

---

### Post by hictio on 2008-11-02
> 
Salvo algunas genialidades, en todos los sistemas operativos los virus se evitan con educación y criterio.


Sabias palabras!
Eso deberia estar grabado en todos los idiomas en todas las pantallas de inicio de todos los OS.
O, por lo menos, en los de contaduria, antes de "abrir" el video que le mando la prima, que se llama 'cumple.avi.exe'.

Lo mas conveniente, me parece a mi, para mantenerte libre de preocupaciones de antivirus y seguridad, es mantener tu maquina Ubuntu con todos los updates al dia.

---

### Post by felixcriv on 2008-11-02
Lo cierto es que hoy existen pocos codigos malignos para GNU/Linux.... los llamados rookits... 


Pero si tu pc sirve para llevar archivos de un lugar a otro y viceversa debes tener un antivirus para que los archivos que vengan de MS/win puedan analizarse.... Te recomiendo el clamav.... Panda tiene una solution parecida.....


cheers....

---

