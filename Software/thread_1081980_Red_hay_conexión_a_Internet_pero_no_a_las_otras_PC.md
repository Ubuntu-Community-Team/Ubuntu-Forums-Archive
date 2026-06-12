---
title: "Red: hay conexión a Internet pero no a las otras PCs de la red"
date: 2009-02-27
forum: Software
---

### Post by Mr.Linc on 2009-02-27
Hola gente,

No soy de pedir ayuda, no me gusta hacerlo, cualquier dificultad o desconocimiento que tengo lo soluciono el 99% de las veces buscando por los foros; pero ahora ando con un problema que no sé cómo resolver y no he encontrado solución por más que busqué y busqué.

Aunque hace más de 2 años que uso Ubuntu en mi casa (tengo una sola PC), hace una semana que instalé el 8.10 en la oficina, donde tenemos varias PCs en red. Todas tienen WinXP, están todas conectadas por cable a un router Linksys, de ahí a un cable modem para tener acceso a Internet. Una de las cosas conectadas a la red no es una PC sino un disco duro externo también conectado al router.
Desde las PCs con XP, y hasta desde una notebook con Vista, aparece toda la red incluyendo ese HD externo.

Pero desde mi Ubuntu no aparece NADA de lo que esté conectado a la red, aunque sí tengo conexión a Internet perfectamente, que anduvo sin problemas y por sí sola ya desde la instalación del sistema.

O sea, para usar Internet, paso por el router, de ahí al cable modem, y de ahí a Internet, es decir que cualquier PC de la red puede conectarse individualmente a Internet sin necesidad de usar conexión compartida de otra.
Aclaro que desde esta misma PC donde tengo Ubuntu, tengo en otra partición el XP y puedo ver toda la red, compartir archivos, directorios, copiar de una PC a la otra, etc. Pero en Ubuntu no puedo hacer nada de esto. Cuando voy a Lugares - Red aparece un solo ítem, "Red de Windows", pero al querer entrar allí, sale el mensaje de error: "No se pudo montar el lugar - Failed to retrieve share list from server"

¿Alguna idea de qué hacer para solucionar esto? Concretamente, ni me interesa que aparezca toda la red; con que me pueda conectar al HD externo (es un Western Digital MyBook de 1 Tb) que es donde están los archivos con los que trabajo, es más que suficiente.

Desde ya les agradezco.

P/D: puse esto en la sección "Software" ya que creo que se trata de una cuestión referida al soft y no al hard.

---

### Post by biale on 2009-02-27
Para acceder a la red de Windows necesitas instalar y comfigurar "samba". Googleando vas en encontrar lo que quiras, solo tratá de elegir un tuto para una red "sencilla", sin controladores de dominio, Wins server ni otras cosas raras.

Yo configure a mano los archivos /etc/smb.conf y /etc/smbusers.

Viejo truco Windows: Incluso si lograras compartir el directorio "Público" de Ubuntu usando solo la interfase gráfica tendrías el problema resuelto. Yo prefiero algo mas clásico y controlable.

Curiosidad: ¿El disco duro se conecta al router por USB o por Ethernet?

Exitos!

---

### Post by hictio on 2009-02-27
Acá hay una pequeña confusión con el post de Biale.
El archivo '/etc/samba/smb.conf' lo tenés que configurar si querés que se conecten a tu máquina Ubuntu *desde* Windows por la red (además tenés que instalar el servidor y arrancar el servicio, y si estamos hablando de una instalación Desktop).

Si lo que vos querés es conectarte a un directorio (o disco) compartido en una máquina Windows *desde* tu máquina Ubuntu, digamos un desktop plain vanilla con Gnome, tenés que:

Places > Connect to Server.. > Service type: Windows share

En Server, lo más sencillo es que uses el IP de la máquina Windows a la que te querés conectar.
En Share, el nombre del directorio al que te querés conectar.
La info de login no es necesaria, si se necesita para acceder al share te la va a pedir.
Dale click a Connect, y esperá, se va a abrir una ventana de Nautilus normal con el directorio compartido.

Otra opción (en Linux hay 47 trillones de formas de hacer algo, y eso está bueno :D ), abrí una ventana de Nautilus, y en el box de Location: tipea:

```

smb://direccion.ip.servidor/share/

```

---

### Post by Mr.Linc on 2009-02-27
> **hictio]Si lo que vos querés es conectarte a un directorio (o disco) compartido en una máquina Windows desde tu máquina Ubuntu[/QUOTE]
Exactamente ESO es lo que quiero hacer. Es lo que necesito para poder trabajar... es lo que quiero lograr para poder ponerme a trabajar directamente con Ubuntu en el laburo, sin necesidad de tener que usar Windows otra vez. (con Win no tengo ningún problema, pero quiero dejarlo de lado y trabajar desde Ubuntu).

Ahora estoy en mi casa por el fin de semana, pero el lunes a primera hora vuelvo al laburo y voy a probar lo que me dijiste. Casi todo el trabajo que venía haciendo en Windows lo puedo hacer perfectamente desde Ubuntu, así que quiero pasarme definitivamente said:**
> Curiosidad: ¿El disco duro se conecta al router por USB o por Ethernet?
Por Ethernet. Tiene posibilidad de conexión USB también, pero no la usamos, se conecta directo al router por Ethernet.

Muchas gracias por las respuestas... el lunes cuando vuelva a la oficina pruebo con lo que me dijeron y después les cuento.

:)

---

### Post by hictio on 2009-02-27
Una cosa más, por defecto, todos los 'puntos de montura', es decir los shares a los que te conectes, se agregan como links a tu desktop.
Cuando terminás de trabajar, le das click derecho a ese ícono, y seleccionás 'Unmount Volume'.

---

### Post by biale on 2009-02-28
Vale y agradezco la aclaración de Hictio. Saludos a ambos.

---

### Post by Mr.Linc on 2009-03-06
Disculpen muchachos por no volver a responder antes, es que estuve bastante ocupado.

Funcionó. :P
Tuve que instalar un programa aparte para que escanee las IPs de toda la red porque la IP del hd externo no podía verla ni siquiera desde Windows, y así me funcionó mediante la opción de *Conectar con servidor/Connect to server*.

Lo que me resultaba extraño de todo esto es que a algunas personas el sistema les detectaba toda la red en seguida, pero a mí no.
Igual eso ya no importa, logré lo que necesitaba.

Muchas gracias. :)

---

### Post by razor7 on 2009-04-22
> **Mr.Linc said:**
> Funcionó. :P
Tuve que instalar un programa aparte para que escanee las IPs de toda la red porque la IP del hd externo no podía verla ni siquiera desde Windows, y así me funcionó mediante la opción de *Conectar con servidor/Connect to server*. Hola tengo el mismo problema...que programa instalaste para que escanee las IP de la red?

Gracias por la data.

---

### Post by razor7 on 2009-04-22
me parece que con esto lo solucione [http://ubuntuforums.org/showthread.php?p=7120419#post7120419](http://ubuntuforums.org/showthread.php?p=7120419#post7120419)

saludos.

---

