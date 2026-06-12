---
title: "Configurar FTP en red"
date: 2010-02-11
forum: Software
---

### Post by FB91 on 2010-02-11
Necesito usar el FTP (más específicamente el Filezilla) pero no puedo conectarme. Yo estoy conectado en red con otra PC con Windows, la cual me comparte internet.

Supongo que hay que tocar algo relacionado a los puertos... cualquier ayuda me viene bárbaro.

Ésta es la salida del filezilla:

> Estado:    Resolviendo la dirección de ftp.fb91.com.ar
Estado:    Conectando a 75.125.162.228:99...
Error:    Conexión superó el tiempo de espera
Error:    No se pudo conectar al servidor
Estado:    Esperando para reintentar...
Estado:    Retrasando conexión por 1 segundo debido a un intento previo de conexión fallido...
Estado:    Retrasando conexión por 1 segundo debido a un intento previo de conexión fallido...
Estado:    Retrasando conexión por 1 segundo debido a un intento previo de conexión fallido...
Estado:    Retrasando conexión por 1 segundo debido a un intento previo de conexión fallido...
Estado:    Retrasando conexión por 1 segundo debido a un intento previo de conexión fallido...
Estado:    Resolviendo la dirección de ftp.fb91.com.ar
Estado:    Conectando a 75.125.162.228:99...
Error:    Conexión superó el tiempo de espera
Error:    No se pudo conectar al servidor

salu2!

---

### Post by guillermolisi on 2010-02-11
Suena a que tenes algun firewall que no deja pasar informacion ya sea en el port 21 o en el 20 y nunca te llega la respuesta de la conexion, por eso el timeout.
Dale una leida a [este link]("http://slacksite.com/other/ftp.html") en Ingles que si bien habla de otra caracteristica de FTP te da una buena idea en general sobre lo que necesitas.

---

### Post by juancarlospaco on 2010-02-11
Dice:

Estado: Conectando a 75.125.162.228**:99**...

Aparentemente esta usando un puerto no estandard para la conexion*(?)*

---

### Post by FB91 on 2010-02-11
> **juancarlospaco said:**
> Dice:

Estado: Conectando a 75.125.162.228**:99**...

Aparentemente esta usando un puerto no estandard para la conexion*(?)*

con el 21 me pasa lo mismo... lo que pasa es que entré a probar con cualquier número (20, 21, 22 ... 99) :D

---

### Post by guillermolisi on 2010-02-12
Revisa el firewall de Windows para que deje pasar paquetes FTP (ports 20 y 21).
Por las dudas, en una consola/terminal de Ubuntu ejecuta ```
iptables -S
iptables -t nat -n -L
``` y mostranos la salida.

Si queres trabajar mas comodo configurando iptables podes usar UFW, Firestarter o similares.

Si estas usando un router, revisa tambien que este ultimo tambien deje pasar paquetes de datos por esos puertos.

---

### Post by juancarlospaco on 2010-02-14
Recomiendo GUFW, Firestarter esta muerto de hace tiempo...

---

### Post by guillermolisi on 2010-02-14
> **juancarlospaco said:**
> Recomiendo GUFW, Firestarter esta muerto de hace tiempo...
Para lo que tiene que hacer alcanza y sobra. Lo tengo en uso desde hace tiempo tambien y hasta ahora ningun problema, es sencillo, relativamente amigable, posee algo de documentacion decente y para configuraciones domesticas es mas que eficiente.

Si fuera para una empresa no lo recomendaria porque hay productos que lo han superado como eBox y otros similares.

---

