---
title: "RED CON DOMINIO W2003 y UBUNTU 9.04"
date: 2009-08-28
forum: Software
---

### Post by quedefantasma on 2009-08-28
Hola a todos! Mi nombre es Mariano y esta es mi primer consulta en el foro.

Bueno, como verán mi consulta es una mas de las tantas en relación a este tema...
Hace varios días estoy dando vuelta por los distintos foros...how to's..y demases...con algo de suerte.

Mi intención es migrar varios equipos (actualmente winXP pro) que están en una red de oficina a ubuntu. La red esta bajo un dominio w2003 y por el momento no me es posible cambiarlo. La red debera ser mixta entre equipos Ubuntu y Win ya que tengo un sistema contable que solo corre en win.

Actualmente los usuarios se loguean contra el dominio, se les asignan IPs fijas por DHCP, conexion a internet por medio de un proxy server (que da permisos x MAC+IP) y acceso a carpetas compartidas en el servidor con distintos permisos por usuario.

Hasta ahora migre dos maquinas a ubuntu con algo de exito mediante samba y winbind ...en el camino tuve varios problemas...intente sin exito usar LIKEWISE-OPEN...etc.

Finalmente utilize para el usuario UBUNTU el mismo nombre de equipo y el mismo usuario/contraseña que teniamos en los winXP. Modifique los archivos smb.conf y nsswitch.conf segun lei en algunos tutoriales y logro ver la "red de windows", el grupo de trabajo, y accesar las carpetas del servidor...esto ultimo despues de ingresar los datos de logueo nuevamente (supongo que por ser los mismos que usaba en windows) y marcar la opcion de recordar para siempre. No se si es la mejor opcion...pero funciona hasta ahora.

En este momento estoy complicado con las comparticiones locales de estos equipos que migre a ubuntu (por ejemplo IMPRESORAS)... Activo la comparticion, pero cuando trato de accesarlas desde otros equipos (tanto ubuntu como xp) me solicita usuario y contraseña...y hasta ahi llego. (supongo que tendria que crear todos los usuarios y darles permisos en el smb local?...imposible!)

Cuando tenia los equipos con win y compartiamos algo local (solo lo podia hacer el admin, no el usuario) se seleccionaba del AD que usuarios podian accesar la comparticion local y con que permisos... como es esto en smb?

Espero se entienda el planteo...

Se escuchan comentarios, consejos, correcciones, dudas, AYUDA!

Gracias a todos...slds!

MOVIDO: Perdon! Gracias Sr. Mod / Admin...

---

### Post by uylug on 2009-08-28
> **quedefantasma said:**
> Hola a todos! Mi nombre es Mariano y esta es mi primer consulta en el foro.

Bienvenido :p

> **quedefantasma said:**
>  Bueno, como verán mi consulta es una mas de las tantas en relación a este tema...
Hace varios días estoy dando vuelta por los distintos foros...how to's..y demases...con algo de suerte.

Mi intención es migrar varios equipos (actualmente winXP pro) que están en una red de oficina a ubuntu. La red esta bajo un dominio w2003 y por el momento no me es posible cambiarlo. La red debera ser mixta entre equipos Ubuntu y Win ya que tengo un sistema contable que solo corre en win.

Actualmente los usuarios se loguean contra el dominio, se les asignan IPs fijas por DHCP, conexion a internet por medio de un proxy server (que da permisos x MAC+IP) y acceso a carpetas compartidas en el servidor con distintos permisos por usuario.

Hasta ahora migre dos maquinas a ubuntu con algo de exito mediante samba y winbind ...en el camino tuve varios problemas...intente sin exito usar LIKEWISE-OPEN...etc.


¿Vos sabes que justo hoy logre configurar por completo el dominio con Ubuntu? Estoy trabajando en un proyecto y acabo de terminar de hacer una guia de como configurarlo. Te lo adjunto aca mismo
> **quedefantasma said:**
> 
Finalmente utilize para el usuario UBUNTU el mismo nombre de equipo y el mismo usuario/contraseña que teniamos en los winXP. Modifique los archivos smb.conf y nsswitch.conf segun lei en algunos tutoriales y logro ver la "red de windows", el grupo de trabajo, y accesar las carpetas del servidor...esto ultimo despues de ingresar los datos de logueo nuevamente (supongo que por ser los mismos que usaba en windows) y marcar la opcion de recordar para siempre. No se si es la mejor opcion...pero funciona hasta ahora.
Si... pero esos workarounds despues te matan. Alguna c*****a te va a complicar la vida. Fijate si lo podés dejar andando bien de una vez con eso que te pasé. Igual si tenes problemas me hablas por privado o por msn... todo bien. Además yo vivo en Uruguay, tenemos la misma zona horaria, o sea, no hay problema.

> **quedefantasma said:**
>  En este momento estoy complicado con las comparticiones locales de estos equipos que migre a ubuntu (por ejemplo IMPRESORAS)... Activo la comparticion, pero cuando trato de accesarlas desde otros equipos (tanto ubuntu como xp) me solicita usuario y contraseña...y hasta ahi llego. (supongo que tendria que crear todos los usuarios y darles permisos en el smb local?...imposible!)
Mmm... Yo en mi casa tengo varios equipos con Ubuntu y una laptop con Windows. Tengo paralalemente compartidas las impresoras por sistemas propios de Linux para los hosts Linux, y por Samba para los hosts Linux y Windows. Pero como no me importa ningun aspecto de seguridad no tengo ningun dominio, pero en tu caso me parece que es mas complicado porque queres compartir impresoras a los usuarios del dominio. En ese caso me parece que vas a tener que compartir las impresoras, no sé, desde el servidor Windows y configurarlas no deberia ser problema, aunque quieras compartir impresoras desde Linux, que ta, eso es mas complicado pero en casa lo hice, editando el smb.conf. Yo tengo un dominio en una maquina virtual, para hacer pruebas, pero no lo tengo con impresoras ni nada de eso, pero si puedo autenticarme desde Linux impecable. Supongo que si sos usuario del dominio podés acceder a los shares sin problemas.

---

### Post by quedefantasma on 2009-08-30
Buena onda UYLUG...Muchas gracias por la respuesta!
Ya me pongo a leer lo que me pasaste y despues te comento como me fue.

Gracias y Slds.

---

### Post by uylug on 2009-08-30
> **quedefantasma said:**
> Buena onda UYLUG...Muchas gracias por la respuesta!
Ya me pongo a leer lo que me pasaste y despues te comento como me fue.

Gracias y Slds.

De mas! Dale, suerte.

Si algo no queda muy claro o no esta muy bien explicado, fijate esta guia que hice en ingles, que basicamente es lo mismo, pero la hice despues que ese documento, capaz aclare cosas que ahi no.

[http://ubuntuforums.org/showthread.php?p=7863547#post7863547](http://ubuntuforums.org/showthread.php?p=7863547#post7863547)

---

### Post by quedefantasma on 2009-09-17
Lamentablemente sigo sin poder comunicarme correctamente con el resto de mi red...esto esta también impidiendo la migración de los otros equipos a UBUNTU.

El usuario Uylug (PABLO, Muchas gracias!) fue de mucha ayuda y puso su mejor empeño...pero hay algo que no me esta funcionando...

También me metí un poco mas en profundidad con LIKEWISE pero no hay caso...

Si alguien tiene alguna otra recomendación, sera mas que bienvenida!

Realmente me parce que este tema es MUY IMPORTANTE para que las empresas se decidan a pasar a UBUNTU, y por lo mucho que vengo leyendo es un tema racurrente...

Slds!

---

### Post by Hei Ku on 2009-09-17
Podes aportar mas datos? Decir solamente "no me anda" no contribuye a una mejor calidad de la ayuda que podamos brindarte.

---

### Post by juancarlospaco on 2009-09-17
Yo trabajo en una red con DOMINIO W2003 y UBUNTU 9.10.

:)

---

### Post by quedefantasma on 2009-09-17
> **juancarlospaco said:**
> Yo trabajo en una red con DOMINIO W2003 y UBUNTU 9.10.

:)

So, Te odio! :)

---

### Post by quedefantasma on 2009-09-17
> **Hei Ku said:**
> Podes aportar mas datos? Decir solamente "no me anda" no contribuye a una mejor calidad de la ayuda que podamos brindarte.

Si como no...!!!

Segui el tutorial que paso el amigo Pablo desde Uruguay... Tengo instalados SMB, KRB, WINBINDS...etc. Tengo bien el resolv.conf...hago ping al servidor por nombre e Ip...con exito...y hasta ahi llego, todo lo demas no pude hacerlo...le di vueltas para atras y para adelante...pero no hay caso.

Decime que datos mas necesitarias saber y te los posteo...obviamente

Gracias por el interes y Slds.

---

### Post by Hei Ku on 2009-09-17
Que pasa si tratas de conectar por smb? El ping utiliza dns, pero el problema aca es la parte de samba. 

Pudiste unir esta maquina al dominio?

---

### Post by quedefantasma on 2009-09-21
Hei Ku, SMB funciona aparentemente bien...veo la red y listado de equipos del dominio. Al file server  ingrese bien (puse mi usuario y contraseña que tenia en el win) y respeta los permisos que tenia a las carpetas compartidas.

No puedo ingresar a las comparticiones de las otras maquinas, ahi me vuelve a pedir user/password en cada carpeta y en las impresoras tambien...Por lo que supongo que donde esta funcionando bien solo lo hace porque el user/password son iguales a los que tenia en win...y no porque este funcionando bajo el dominio.

Espero que se enitienda...

Como dice el tutorial, instale los prequisitos... e hice los test corespondientes. Pero cuando quiero hacer el KINIT, me dice que la configuracion de KRB es incorrecta. Busque info de como configurar KRB, probe varias modificaciones...pero no hay caso.

---

### Post by Hei Ku on 2009-09-21
Podes poner el error exacto que te tira?

---

### Post by quedefantasma on 2009-09-21
Sale...

El archivo krb5.conf esta asi:

                                 [FONT=Courier new, monospace][logging][/FONT] 
 [FONT=Courier new, monospace]default = FILE:/var/log/krb5.log[/FONT] 
[FONT=Courier new, monospace]kdc = FILE:/var/log/krb5kdc.log[/FONT] [FONT=Courier new, monospace]
admin_server = FILE:/var/log/kadmin.log[/FONT] 
  [FONT=Courier new, monospace]
[libdefaults][/FONT] 
[FONT=Courier new, monospace]default_realm = edos.com.ar[/FONT] 
[FONT=Courier new, monospace]dns_lookup_realm = false[/FONT] 
[FONT=Courier new, monospace]dns_lookup_kdc = true[/FONT] [FONT=Courier new, monospace]
ticket_lifetime = 24000[/FONT]  [FONT=Courier new, monospace]

[realms][/FONT] [FONT=Courier new, monospace]
edos.com.ar = {[/FONT] [FONT=Courier new, monospace]
kdc = server-edos.edos.com.ar[/FONT] 
[FONT=Courier new, monospace]admin_server = server-edos.edos.com.ar[/FONT] [FONT=Courier new, monospace]
default_domain = edos.com.ar }[/FONT]  [FONT=Courier new, monospace]

[domain_realm][/FONT] 
[FONT=Courier new, monospace].dominio.local = edos.com.ar[/FONT] 
[FONT=Courier new, monospace][SIZE=2]dominio.local = edos.com.ar[/SIZE][/FONT] 

El error dice:

kinit(v5): Improper format of Kerberos configuration file while initializing Kerberos 5 library

---

### Post by quedefantasma on 2009-09-23
> **juancarlospaco said:**
> Yo trabajo en una red con DOMINIO W2003 y UBUNTU 9.10.

:)

Es mucho pedir que me pases tus configuraciones para probarlas? :)

---

### Post by guillermolisi on 2009-09-23
> **quedefantasma said:**
> Es mucho pedir que me pases tus configuraciones para probarlas? :)
Como complemento y para entender y comprender mejor lo que leas de las distintas configuraciones tuyas o de terceros, dale una leida [a esto]("http://guillermolisi.com.ar/?q=node/13") y bajate el libro "Usando Samba".

---

### Post by quedefantasma on 2009-09-23
> **guillermolisi said:**
> Como complemento y para entender y comprender mejor lo que leas de las distintas configuraciones tuyas o de terceros, dale una leida [a esto]("http://guillermolisi.com.ar/?q=node/13") y bajate el libro "Usando Samba".

OK, leyendo me quedo...gracias!

---

### Post by quedefantasma on 2009-10-08
No hay caso....esta complicada la cosa.....:(

---

### Post by faktorqm on 2009-10-09
Hola, no se por que no lei tu post antes, pero bueno.

fmsismo y yo estamos trabajando en hacer un tutorial para levantar un dominio de w2003 en linux, del lado del server, claro, con autenticacion LDAP, perfiles moviles, que el user cambie el password, impresoras, toda la bola. 

Ahora bien, segun tu caso, lo que yo veo es que tendrias que haber empezado al reves, es decir, instalando el servidor con ubuntu y luego los clientes. Es mi opinion, nada mas, ahora ya tenes la mitad implementado y fue.

Para el tema de los usuarios, siempre se manejo "aparte" eso, cuando vos te conectas a un recurso compartido, en realidad lo que tenes que hacer no es crear un usuario de sistema, sino es crear un usuario virtual, sin home y sin logueo, y que este unicamente en el grupo samba. Lo mismo para ssh (si usas chroot), lo mismo para VSFTPD, etc.

Ahora en que situacion estas ahora mismo?

---

### Post by quedefantasma on 2009-10-09
Hola FAKTORQM, gracias por tu interes...

Si, la idea de montar un servidor LINUX cruzo varias veces por mi mente...y supongo que simplificaria las cosas...pero bueno, quedara para mas adelante y cuando tenga un poco mas de experiencia!

Te cuento como esta la cosa ahora... La red esta basada en un server W2003, tambien hace de file-server, y soporta un par de aplicaciones (CRM y ERP) para los usuarios WIN.

La idea es migrar a todos los usuarios basicos y que no usan las aplicaciones antes mencionadas a UBUNTU (openoffice, correo, impresoras y acceso a los files de servidor)

Pude conectar estos usuarios a la red sin problemas y que aparezcan listados cuando accesamos a LUGARES/RED...estan visibles todos los usuarios WIN y los UBU

El tema por ahora es que no tienen permisos para las diferentes carpetas compartidas de los usuarios, las impresoras, y los files del servidor...

Entonces empezaron los problemas al tratar de registrar los usuarios UBUNTU bajo el dominio WIN. Intente sin exito con LIKEWISE y con el tutorial posteado mas arriba...

La verdad es que ya hice tantas cosas y modifique tantos archivos .conf ...que ya estoy perdido!

Hoy hice una instalacion nueva del UBUNTU para asegurarme de estar con una version limpia...pero sigo sin poder avanzar.

Comence de cero con el tutorial (instalar SMB, KRB, WINBINDS, ETC)...y no puede pasar de la configuracion del KRB5...ya ahi se me clava todo...

Escucho cualquier propuesta nueva!!!! o VIEJA!!! Slds...

---

### Post by quedefantasma on 2009-10-21
Se termino el problema! .... UBUNTU 9.10.....:)

---

### Post by guillermolisi on 2009-10-21
> **quedefantasma said:**
> Se termino el problema! .... UBUNTU 9.10.....:)
Podrias dar algunos detalles sobre que y como se resolvio el problema con la 9.10 ?

---

### Post by quedefantasma on 2009-10-21
Si, perdon! Fue la emocion...:KS

Se resolvio instalando una Aplicacion llamada SAMBA desde el "centro de software de ubuntu"

_Acerca de:_

Herramienta de Configuración del Servidor Samba 1.2.63
Copyright 2002 - 2005 (c) Red Hat, Inc. 
Copyright 2002 - 2004 (c) Brent Fox <bfox@redhat.com>
Copyright 2002 - 2004 (c) Tammy Fox <tfox@redhat.com>
Copyright 2004 - 2005 (c) Nils Philippsen <nphilipp@redhat.com>

Una interfaz gráfica para configurar recursos compartidos SMB

Es simplemente una GUI (como otras tantas...) pero que funciono de maravillas.

Gracias a todos los que colaboraron.

---

### Post by quedefantasma on 2009-10-27
Estimados quiero compartir con uds. las configuraciones finales que resolvieron el problema en mi entorno.

Esta muy simplificado y reducido, pero basado en el archivo adjunto al principio de este thread.

**Configuración de DNS**
 sudo gedit /etc/resolv.conf

[FONT=Courier new, monospace][SIZE=2]domain ejemplo.local
[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]search [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]ejemplo.local[/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]nameserver (IP del servidor)
[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]nameserver nombredelservidor.[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]ejemplo.local[/SIZE][/FONT]
                 
**Configuración de HOSTS**
 sudo gedit /etc/hosts
  
[FONT=Courier new, monospace][SIZE=2]127.0.0.1    localhost[/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2](IP del equipo)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]nombredelequipo.[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]ejemplo.local[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] nombredelequipo
[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2](IP del servidor)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]nombredelservidor.[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]ejemplo.local[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] nombredelservidor[/SIZE][/FONT]

[FONT=Courier new, monospace][SIZE=2]#The following lines are desirable for IPv6 capable hosts[/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]::1                 localhost ip6-localhost ip6-loopback[/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]fe00::0             ip6-localnet[/SIZE][/FONT]
 [FONT=Courier new, monospace][SIZE=2]ff00::0             ip6-mcastprefix[/SIZE][/FONT]
 [FONT=Courier new, monospace][SIZE=2]ff02::1             ip6-allnodes[/SIZE][/FONT]
 [FONT=Courier new, monospace][SIZE=2]ff02::2             ip6-allrouters[/SIZE][/FONT]
 [FONT=Courier new, monospace][SIZE=2]ff02::3             ip6-allhosts[/SIZE][/FONT]
                 
**Instalación de los paquetes esenciales**
[FONT=Courier new, monospace][SIZE=2]sudo apt-get install samba winbind krb5-user[/SIZE][/FONT]

**[B]Configuración de Kerberos**[/B]
 sudo gedit /etc/krb5.conf
  [FONT=Courier new, monospace][SIZE=2]
[/SIZE][/FONT]   	 	 	 	 	[FONT=Courier new, monospace][SIZE=2][libdefaults] [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	default_realm = ejemplo.local [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	dns_lookup_realm = false [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	dns_lookup_kdc = true [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	ticket_lifetime = 24000 [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	clockskew = 300 [/SIZE][/FONT]

[FONT=Courier new, monospace][SIZE=2][realms] [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	EJEMPLO.LOCAL = { [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]		kdc = (IP del servidor) [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]		admin_server = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2](IP del servidor)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]:88 [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]		default_domain = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]EJEMPLO.LOCAL[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]	} [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	ejemplo.local = { [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]		kdc = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2](IP del servidor)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]		admin_server = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2](IP del servidor)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]:88 [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]		default_domain = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]ejemplo.local[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]	} [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]	[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]EJEMPLO[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] = { [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]		kdc = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2](IP del servidor)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]		admin_server = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2](IP del servidor)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]:88 [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]		default_domain = EJEMPLO [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]	} [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	ejemplo = { [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]		kdc = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2](IP del servidor)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]		admin_server = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2](IP del servidor)[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]:88 [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]		default_domain = ejemplo [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]	} [/SIZE][/FONT]

[FONT=Courier new, monospace][SIZE=2][logging] [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]	kdc = FILE:/var/log/krb5/krb5kdc.log [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]	admin_server = FILE:/var/log/krb5/kadmind.log [/SIZE][/FONT]
  [FONT=Courier new, monospace][SIZE=2]	default = FILE:/var/log/krb5/krb5.log [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	 [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2][domain_realm] [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	.ejemplo = EJEMPLO [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	.EJEMPLO = ejemplo [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	.ejemplo.local = [/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]EJEMPLO.LOCAL[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] [/SIZE][/FONT]
[FONT=Courier new, monospace][SIZE=2]	.[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]EJEMPLO.LOCAL[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2] = ejemplo.local[/SIZE][/FONT] **Unir el usuario al DOMINIO**
[FONT=Courier new, monospace][SIZE=2]kinit [EMAIL="usuario@EJEMPLO.LOCAL"]usuario@EJEMPLO.LOCAL[/EMAIL][/SIZE][/FONT]

Para verificar:  **klist**

  	 	 	 	 	 	  [FONT=Courier new, monospace][SIZE=2]usuario@equipo:~$ klist [/SIZE][/FONT] 
 [FONT=Courier new, monospace][SIZE=2]Ticket cache: FILE:/tmp/krb5cc_1000 [/SIZE][/FONT] 
 [FONT=Courier new, monospace][SIZE=2]Default principal: [email]usuario@EJEMPLO.LOCAL[/email] [/SIZE][/FONT] 
 

 [FONT=Courier new, monospace][SIZE=2]Valid starting     Expires            Service principal [/SIZE][/FONT] 
 [FONT=Courier new, monospace][SIZE=2]10/27/09 10:13:24  10/27/09 16:53:24  krbtgt/EJEMPLO.LOCAL@[/SIZE][/FONT][FONT=Courier new, monospace][SIZE=2]EJEMPLO.LOCAL[/SIZE][/FONT] 

**[B]Configuración de SAMBA**[/B]
 sudo gedit /etc/samba/smb.conf
  	 	 	 	 	 	  [FONT=Courier New, monospace][global] [/FONT]  [FONT=Courier New, monospace]	workgroup = ejemplo [/FONT] [FONT=Courier New, monospace]	realm = nombredelservidor.ejemplo.local [/FONT] [FONT=Courier New, monospace]	netbios name = nombredelequipo [/FONT] [FONT=Courier New, monospace]	server string = usuario [/FONT] [FONT=Courier New, monospace]	dns proxy = no [/FONT] [FONT=Courier New, monospace]	log file = /var/log/samba/log.%m [/FONT] [FONT=Courier New, monospace]	max log size = 1000 [/FONT] [FONT=Courier New, monospace]	syslog = 0 [/FONT] [FONT=Courier New, monospace]	panic action = /usr/share/samba/panic-action %d [/FONT] [FONT=Courier New, monospace]	security = ads [/FONT] [FONT=Courier New, monospace]	domain master = no [/FONT] [FONT=Courier New, monospace]	idmap uid = 10000-20000 [/FONT] [FONT=Courier New, monospace]	idmap gid = 10000-20000 [/FONT] [FONT=Courier New, monospace]	template shell = /bin/bash [/FONT] [FONT=Courier New, monospace]	template homedir = /home/%d/%u [/FONT] [FONT=Courier New, monospace]	client use spnego = yes [/FONT] [FONT=Courier New, monospace]	winbind enum groups = yes [/FONT] [FONT=Courier New, monospace]	winbind enum users = yes [/FONT] [FONT=Courier New, monospace]	winbind use default domain = yes [/FONT] [FONT=Courier New, monospace]	winbind separator = / [/FONT] [FONT=Courier New, monospace]	usershare allow guests = no [/FONT] [FONT=Courier New, monospace]	password server = nombredelservidor.ejemplo.local[/FONT] [FONT=Courier New, monospace]	encrypt passwords = yes [/FONT] [FONT=Courier New, monospace]	guest ok = no [/FONT] [FONT=Courier New, monospace]	guest account = nobody [/FONT]  [FONT=Courier New, monospace][Público] [/FONT] [FONT=Courier New, monospace]	path = /home/usuario/Público [/FONT] [FONT=Courier New, monospace]	writeable = yes [/FONT] [FONT=Courier New, monospace]	browseable = yes [/FONT] [FONT=Courier New, monospace]	guest ok = yes[/FONT] Para verificar: **testparm**

Reiniciar Samba y Winbind
[FONT=Courier New, monospace][SIZE=2]/etc/init.d/winbind stop
/etc/init.d/samba restart
/etc/init.d/winbind start[/SIZE][/FONT]
   
**[B]Unirse al DOMINIO**[/B]
[FONT=Courier New, monospace][SIZE=2]sudo net join ads -w DOMINIO -U usuario [/SIZE][/FONT]             
   
**[B]Autenticación por medio de Winbind**[/B]
sudo gedit /etc/nsswitch.conf.
  
[FONT=Courier New, monospace]passwd: compat winbind[/FONT] 
[FONT=Courier New, monospace]group:  compat winbind[/FONT] 
[FONT=Courier New, monospace]shadow: compat winbind[/FONT] [FONT=Courier New, monospace]
hosts:     files dns wins[/FONT] 
[FONT=Courier New, monospace]networks:  files dns[/FONT] 
[FONT=Courier New, monospace]protocols:   db files[/FONT] [FONT=Courier New, monospace]
services:    db files[/FONT] 
[FONT=Courier New, monospace]ethers:      db files[/FONT] [FONT=Courier New, monospace]
rpc:         db files[/FONT] 
[FONT=Courier New, monospace]netgroup:     nis[/FONT]                

 Reiniciar Samba y Winbind
  [FONT=Courier New, monospace][SIZE=2]/etc/init.d/winbind stop
/etc/init.d/samba restart
/etc/init.d/winbind start[/SIZE][/FONT]
 
**[SIZE=2]Verificar Winbind[/SIZE]**
[FONT=Courier New, monospace][SIZE=2]wbinfo -u[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]wbinfo -g[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]net ads info [/SIZE][/FONT]             
                

 [SIZE=2]**PERMISOS**[/SIZE]
 sudo gedit /etc/pam.d/common-auth (agregar al principio del archivo)
[FONT=Courier New, monospace][SIZE=2]auth sufficient pam_winbind.so[/SIZE][/FONT]

 sudo gedit /etc/pam.d/common-session (agregar al principio del archivo)
  [FONT=Courier New, monospace][SIZE=2]session required pam_mkhomedir.so[/SIZE][/FONT]
                
Espero sea de utilidad para otros usuarios! Gracias a todos los que colaboraron.

---

### Post by quedefantasma on 2009-10-30
Me queda un problema por resolver...

Hasta ahora todo parece correr bien salvo por el detalle de que cada vez que inicio/reinicio el sistema tengo que ejecutar manualmente el comando KINIT. Para que cuando ingreso a las carpetas compartidas de los equipos WIN no me pida la contraseña....

Calculo que es algun problema con PAM.D o algo asi...

Si alguien tiene algun dato, sera agradecido...

Slds.:D

---

