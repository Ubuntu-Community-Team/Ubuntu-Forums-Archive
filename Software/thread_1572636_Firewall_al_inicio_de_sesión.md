---
title: "Firewall al inicio de sesión"
date: 2010-09-11
forum: Software
---

### Post by kornykyano on 2010-09-11
Me gustaría saber porque el firewall no se carga al inicio de sesión? cada vez, tengo q ejecutar:

**sudo ufw -enable**

No debería ser por default?

---

### Post by guillermolisi on 2010-09-11
El FW en Linux esta incluido en el kernel, asi que esta siempre activo.

Lo que vos queres que se ejecute al inicio de sesion es una interface que te permite administrar las reglas de iptables para configurar el FW.

Con o sin interface de configuracion corriendo, el FW siempre esta activo con las reglas y filtros que se le hayan configurado y cargado.

---

### Post by DrKenobi on 2010-09-14
> **guillermolisi said:**
> El FW en Linux esta incluido en el kernel, asi que esta siempre activo.

Lo que vos queres que se ejecute al inicio de sesion es una interface que te permite administrar las reglas de iptables para configurar el FW.

Con o sin interface de configuracion corriendo, el FW siempre esta activo con las reglas y filtros que se le hayan configurado y cargado.

guillermolisi, voy a aprovechar para sacarme un gran duda. "Entiendo" que el firewall es parte del kernel y esta siempre activado, que al activar el ufw solo se esta ejecutando "un programita" para administrar iptables.

Pero vos decis que el FW esta siempre activo con las reglas y filtros que se le hayan configurado y cargado. ¿Quien configuro y cargo estas reglas? ¿Vienen por defecto?

---

### Post by guillermolisi on 2010-09-14
> **DrKenobi said:**
> guillermolisi, voy a aprovechar para sacarme un gran duda. "Entiendo" que el firewall es parte del kernel y esta siempre activado, que al activar el ufw solo se esta ejecutando "un programita" para administrar iptables.

Pero vos decis que el FW esta siempre activo con las reglas y filtros que se le hayan configurado y cargado. ¿Quien configuro y cargo estas reglas? ¿Vienen por defecto?
Si, por defecto estan cerrados, no se si tambien ocultos, los ports de entrada que solo se abren si algun servicio es publicado desde la maquina, caso webserver con http (port 80), por ejemplo.

Sinteticamente, por defecto se deja salir todo pero no se deja entrar cualquier cosa. Solo los servicios publicados y las respuestas a requerimientos iniciados desde la PC (pop. IMAP, smtp, scp, etc.).

Para modificar esto podes alterar las reglas via primitivas de iptables en linea de comando (consola/terminal) o alguna interface grafica tipo UFW, Firestarter, FWBuilder, etc.

---

### Post by juancarlospaco on 2010-09-14
sudo iptables --list --verbose

:)

---

### Post by DrKenobi on 2010-09-14
> **guillermolisi said:**
> Si, por defecto estan cerrados, no se si tambien ocultos, los ports de entrada que solo se abren si algun servicio es publicado desde la maquina, caso webserver con http (port 80), por ejemplo.

Sinteticamente, por defecto se deja salir todo pero no se deja entrar cualquier cosa. Solo los servicios publicados y las respuestas a requerimientos iniciados desde la PC (pop. IMAP, smtp, scp, etc.).

Para modificar esto podes alterar las reglas via primitivas de iptables en linea de comando (consola/terminal) o alguna interface grafica tipo UFW, Firestarter, FWBuilder, etc.

Para administrarlo estoy usando GUFW. Despues de instalarlo lo ejecute y me decia que el FW no estaba habilitado (ver imagen [http://ubuntuone.com/p/G8X/](http://ubuntuone.com/p/G8X/)) y recien cuando puse ENABLE me empezo a decir que el FW estaba habilitado (ver imagen [http://ubuntuone.com/p/G8Y/](http://ubuntuone.com/p/G8Y/)). Esto es lo que me marea, porque yo siempre entendi que el FW estaba andando.

---

### Post by guillermolisi on 2010-09-14
Es cierto que esos mensajes confunden. UFW y Firestarter tambien dicen que el "firewall esta habilitado o deshabilitado" pero no es asi. Aun sin la interface grafica las reglas definidas mediante esos frontends se cargan igual.

Piensenlo para el caso de un server, sin escritorio grafico y este tipo de interfaces. Imaginan un server sin firewall ? No, cierto ? Bueno, funciona siempre, lo que hay que considerar es que reglas carga. Es decir, si las reglas dicen "deja pasar todo lo que entra y sale" es como no tener FW, por mas que este funcionando como parte del kernel.

---

### Post by DrKenobi on 2010-09-14
El GUFW que uso es simplemente una herramienta para manejas el UFW, que uno normalmente usa mediante el terminal.

Si no entendi mal, me parece que lo que quiere decir el mensaje de ENABLE/DISABLE es con respecto al UFW. Porque cuando en un terminal hice lo que dijo juancarlospaco de poner** sudo iptables --list --verbose** y probe el UFW con _Enable_ y _Disable_ la unica diferencia fue con las reglas que yo tengo puestas en el UFW.

Bueno, espero haber entendido ja. Esto de los FW siempre me marearon je

Gracias guillermolisi!

---

### Post by asterix77 on 2010-09-14
Leyendo el post, me he confundido aún más. Creía que tan solo iptables era el cortafuegos de ubuntu y que estaba incluido por defecto en el kernel. Ahora bien con respecto a lo mencionado por guillermolisi de que ufw está siempre activo he ejecutado.

#sudo ufw status

Lo cual me devuelve:

Estado: inactivo 

:( ?????????    ](*,)

Pero sin embargo iptables se está ejecutando ya que sudo iptables -L me devuelve los servicios denegados y aceptados y además cuento con conexión a internet.

Consulta: al agregar reglas en la terminal usando iptables ¿en que archivo se guarda dicha regla?. ¿ o es mejor hacer un script, e iniciarlo en el arranque?.

Saludos

---

### Post by DrKenobi on 2010-09-14
> **asterix77 said:**
> Leyendo el post, me he confundido aún más. Creía que tan solo iptables era el cortafuegos de ubuntu y que estaba incluido por defecto en el kernel. Ahora bien con respecto a lo mencionado por guillermolisi de que ufw está siempre activo he ejecutado.

#sudo ufw status

Lo cual me devuelve:

Estado: inactivo 

:( ?????????    ](*,)

Pero sin embargo iptables se está ejecutando ya que sudo iptables -L me devuelve los servicios denegados y aceptados y además cuento con conexión a internet.

Consulta: al agregar reglas en la terminal usando iptables ¿en que archivo se guarda dicha regla?. ¿ o es mejor hacer un script, e iniciarlo en el arranque?.

Saludos

yo entendi que con > sudo ufw status lo que esta activo o inactivo es UFW y no el FW.... por lo menos asi lo entendi yo

---

### Post by guillermolisi on 2010-09-15
> **DrKenobi said:**
> yo entendi que lo que esta activo o inactivo es UFW y no el FW.... por lo menos asi lo entendi yo
Es tal cual como entendiste.

---

### Post by totolinux on 2010-09-15
Hola voy a comentar algo que me pasaba hace tiempo y que di con la solución no hace más de un mes.
Para compartir internet en una red ad-hoc uso firestarter que como bien dijeron uso para administrar opciones de iptables de amanera gráfica, Resulta que solo compartía internet cuando estaba activo y además en cada inicio de sesión pedía contraseña.
di con la solución al querer salvar el temita de la contraseña editando sudoers para que firestarter pueda ejecutarse en cada inicio de sesión sin clave. Pero curiosamente ahora no necesito ejecutarlo ya que al editar sudoers aplica las afamadas reglas de compartir internet. espero no haber hecho un berenjenal con este tema y eche algo de luz mi experiencia.

---

### Post by guillermolisi on 2010-09-15
El funcionamiento esperado por parte de Firestarter es el que mencionas en ultima instancia. Las reglas definidas mediante el deben utilizarse aun cuando no tengas corriendolo.

Uso Firestarter desde el 2007 en un server domestico y nunca tuve el problema que mencionas al inicio de tu mensaje. Es mas, ese server normalmente no tiene corriendo el escritorio grafico (que solo se usa si no hay otro recurso para acceder a Internet para solucionar algun problema) y las reglas NAT definidas siguen operando normalmente dando servicio de Internet a las demas maquinas de la red.

---

