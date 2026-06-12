---
title: "Iptables + Squid 2.7 + Webmin 1.510"
date: 2010-05-05
forum: Software
---

### Post by quedefantasma on 2010-05-05
Estimados, estoy con algunos problemas que no logro resolver...Tengo armado un Ubuntu server 9.10 + Squid 2.7 + Webmin 1.510

Pude levantar el SO e instalar el Webmin sin mayores problemas. Después levante el Squid y estoy compartiendo internet controladamente a grupos de usuarios con diferentes permisos de acceso y horarios...todo OK.

Ahora me encuentro con Iptables y/o firewall de linux... y/o shorewall...todavía no se bien cual ni como...

Ya tengo la cabeza un tanto quemada...aprendí muchas cosas!

Consultas....

El modulo "Contrafuegos linux" es solo una interfaz grafica para Iptables? y actua sobre el fichero "/etc/iptables.up.rules"

El "shorewall" tambien actua sobre Iptables? es decir...debería configurar uno u otro? o ambos?

Iptables actua sobre las ACL del squid? es decir...si yo estaba trabajando bien con el squid otorgando "permiso" de conexion a X puerto...iptables puede bloquearlo si no repito el mismo "permiso"?

Para habilitar los puertos 25 y 110...en Iptables, tambien tengo que aceptarlos por el squid?

Espero puedan aclararme un poco el panorama...la verdad estoy mareado...

Gracias y slds.

---

### Post by alfplayer on 2010-05-05
Los programas como Squid usan los puertos. Iptables permite o bloquea el acceso por red (que puede ser desde el mismo sistema) según cómo está configurado.

Los puertos 25 y 110 son de email, que es un sistema que funciona con puertos diferentes a los proxy HTTP como Squid.

---

### Post by quedefantasma on 2010-05-06
> **alfplayer said:**
> Los programas como Squid usan los puertos. Iptables permite o bloquea el acceso por red (que puede ser desde el mismo sistema) según cómo está configurado.

Los puertos 25 y 110 son de email, que es un sistema que funciona con puertos diferentes a los proxy HTTP como Squid.

Bien, gracias por tu respuesta...
Entonces, por ejemplo...el puerto 443 SSL que esta pasando por squid...tendria que abrirlo tambien en iptables? o si no le digo nada iptables lo deja pasar por defecto? o no actúa sobre ese puerto en particular como squid no lo hace sobre el 25 y 110?

Entonces,...como squid no actua sobre los puertos 25 y 110...solo debo decirle a iptables que los forwarde de la interfaz interna a la externa...y ya?

Gracias, saludos

---

### Post by alfplayer on 2010-05-06
> **quedefantasma said:**
> Entonces, por ejemplo...el puerto 443 SSL que esta pasando por squid...tendria que abrirlo tambien en iptables? o si no le digo nada iptables lo deja pasar por defecto? o no actúa sobre ese puerto en particular como squid no lo hace sobre el 25 y 110?

iptables es para configurar el firewall, tiene capacidad para actuar sobre cualquier puerto e interfaz de red.

> **quedefantasma said:**
> Entonces,...como squid no actua sobre los puertos 25 y 110...solo debo decirle a iptables que los forwarde de la interfaz interna a la externa...y ya?

Con lo del email, explicá cómo es tu sistema.

Te recomiendo aprender más del funcionamiento de un firewall o iptables para ser capaz de responder preguntas como estas.

---

### Post by quedefantasma on 2010-05-06
> **alfplayer said:**
> iptables es para configurar el firewall, tiene capacidad para actuar sobre cualquier puerto e interfaz de red.

Con lo del email, explicá cómo es tu sistema.

Te recomiendo aprender más del funcionamiento de un firewall o iptables para ser capaz de responder preguntas como estas.

Si, estoy aprendiendo...pasa que en pocos meses me meti con linux, ubuntu, squid, webmin, dansguardian, iptables...tengo la tapa limada! y ahora estaba tan enredado que me largue a preguntar...

leí sobre iptables en particular, sobre shorewall, sobre el modulo cortafuegos de linux del webmin...y ahi se me mezclo todo

Mi sistema, tengo una red con unos 25 puestos. todos con un ip fija asignada por DHCP. Los usuarios estan accediendo a internet por este servidor con squid. Estan redireccionados al puerto 808. y separados en grupos de usuarios que pueden o no acceder a diferentes listados de paginas en diferentes horarios...etc, esto funciona OK.
Tengo 2 placas eth0 internet y eth1 redlocal. 

El correo esta en un servidor externo. al cual quisiera acceder también por este servidor local (que tiene el proxy)

Gracias por contestar.

---

### Post by alfplayer on 2010-05-06
Qué computadoras deben acceder a esos servidores de correo? Solo el servidor? Los puestos? Ambos? Con un servidor de correo en el servidor? Cualquiera sea la opción, es cuestión de configurar iptables para permitir el tráfico necesario.

---

### Post by quedefantasma on 2010-05-06
> **alfplayer said:**
> Qué computadoras deben acceder a esos servidores de correo? Solo el servidor? Los puestos? Ambos? Con un servidor de correo en el servidor? Cualquiera sea la opción, es cuestión de configurar iptables para permitir el tráfico necesario.

bien, por el momento me conformaría con que los puestos puedan acceder al correo...los configuro como usulmente para que usen mail.xxxx.com (25) y mail.xxxx.com (110) pero no camina...

Slds...

---

### Post by alfplayer on 2010-05-06
Si los que establecen la conexión son los puestos se puede darle acceso a internet a los puestos, y si el router lo permite filtrar los puertos o direcciones que no se usen.

También se podría aunque no se si es buena idea configurar un proxy SMTP y POP en el servidor. De esa manera se evitaría darle acceso a internet (con NAT) a los puestos.

---

### Post by quedefantasma on 2010-06-29
[FONT=Verdana][SIZE=1]Mis muy estimados,

Desafortunadamente sigo sin dar pie con la configuración de iptables! AYUDA...
Estoy utilizando para la configuración, el modulo "CONTRAFUEGOS DE LINUX" incluido en WEBMIN 1.510, ya que lo hago remotamente por la red lan.

El modulo "CONTRAFUEGOS DE LINUX" modifica el archivo "/etc/iptables.up.rules" y viseversa...[/SIZE][/FONT]

He agregado y desagregado reglas de todas las formas posibles con el objetivo de permitir la conexión de los clientes de mi red al correo electrónico en los puertos 25 y 110 / 465 y 995... sin ningún exito.

Como puedo comprobar si las reglas en el script [FONT=Verdana][SIZE=1]"/etc/iptables.up.rules" se están aplicando?[/SIZE][/FONT]

---

### Post by kiarras on 2010-09-19
Buenas,

yo tengo un problema similar.

En un servidor ubuntu 8.04 32 bits con squid y webmind funciona bien tanto el proxy como el paso de correo pop3 y smtp externos. Utilice iptables para enmascarar el proxy, y funciono el correo.

Ahora he instalado ubuntu 10.04 amd64 de la misma forma que el anterior, y funciona todo menos el correo para los puestos (windows). He probado casi de todo con iptables y nada.

¿Hay tanta diferencia entre versiones?

---

### Post by guillermolisi on 2010-09-19
Puede ser que entre ambas instalaciones no estes trabajando con las mismas versiones de Squid. Hay un poco mas de dos años entre una y otra instalacion (mirando desde las versiones de Ubuntu).

Tambien revisaria minuciosamente las reglas que estan operando en Iptables como para descartar diferencias por ese lado.

---

### Post by kiarras on 2010-09-27
Buenas, ya solucioné mi problema.

Era tan simple como instalar bind9, para convertir el servidor en dns.

---

