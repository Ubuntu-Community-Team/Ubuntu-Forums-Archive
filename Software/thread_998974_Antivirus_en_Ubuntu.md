---
title: "Antivirus en Ubuntu"
date: 2008-12-01
forum: Software
---

### Post by leosr on 2008-12-01
Hola.

Ya sé, me van a decir que no es necesario usar antivirus en Linux, que son inofensivos, que no existen, etc..
La idea es tener un antivirus para que escanear los archivos adjuntos de los mails o soft de Win descargado de la web, ya que comparto archivos con máquinas con Winchot y además tengo una partición con XP (por ahora). En la web veo que recomiendan el Avast, que tiene interfaz gráfica.
Qué recomiendan?

Saludos.

---

### Post by santiagoward2000 on 2008-12-01
> **leosr said:**
> Hola.

Ya sé, me van a decir que no es necesario usar antivirus en Linux, que son inofensivos, que no existen, etc..
La idea es tener un antivirus para que escanear los archivos adjuntos de los mails o soft de Win descargado de la web, ya que comparto archivos con máquinas con Winchot y además tengo una partición con XP (por ahora). En la web veo que recomiendan el Avast, que tiene interfaz gráfica.
Qué recomiendan?

Saludos.

Hola!
Para eso a mí me gusta el **clamav**, es está en los repositorios. Si querés una interfaz gráfica podés instalar el **clamtk** (interfaz GTK) o el **klamav** (para KDE).
Saludos!

---

### Post by Jammy4041 on 2008-12-01
También puede utilizar libre de AVG antivirus.

---

### Post by gmunioz on 2008-12-01
Hola leo...:
Te sugiero instales clamav-freshclam clamav clamav-base clamav-daemon klamav
Klamav, es un front-end gráfico, se debe editar el menu y al comando anteponerle gksu, dado que para eliminar archivos infectados es necesario actuar con permisos temporarios de administrador.
Freshclam, es un demonio autónomo que actualizará, si estas conectado a internet, automáticamente las bases de datos de virus.
Clamav solo actua por mandato, es decir que por intermedio de Klamav deberás indicarle que y donde escanear, solo detecta y pone en cuarentena o elimina los archivos infectados, no repara ni limpia.
Es sumamente efectivo, liviano, seguro y de código libre. Se puede automatizar su actividad mediante scripts.
[B]Saludos.
Gabriel.[/B]
*Solo doy soporte para Ubuntu* **6666 -- Más malo que el diablo**.

---

### Post by leosr on 2008-12-01
> **gmunioz said:**
> Hola leo...:
Te sugiero instales clamav-freshclam clamav clamav-base clamav-daemon klamav
Klamav, es un front-end gráfico, se debe editar el menu y al comando anteponerle gksu, dado que para eliminar archivos infectados es necesario actuar con permisos temporarios de administrador.
Freshclam, es un demonio autónomo que actualizará, si estas conectado a internet, automáticamente las bases de datos de virus.
Clamav solo actua por mandato, es decir que por intermedio de Klamav deberás indicarle que y donde escanear, solo detecta y pone en cuarentena o elimina los archivos infectados, no repara ni limpia.
Es sumamente efectivo, liviano, seguro y de código libre. Se puede automatizar su actividad mediante scripts.
[B]Saludos.
Gabriel.[/B]
*Solo doy soporte para Ubuntu* **6666 -- Más malo que el diablo**.

Klamav es para KDE, va a andar bien en Gnome? Yo instalé el clamtk que es una interfaz gráfica, como comentó santiagoward2000.

---

### Post by b17w153 on 2008-12-01
Si, cuando descargas KlamAV tambien esta descargado todo que necesitas para usar KlamAV con GNOME.

Uso antivirus con Ubuntu tambien porque no quiero que mis sistemas comparten sus problemas, solo mis filas!

---

### Post by santiagoward2000 on 2008-12-01
> **b17w153 said:**
> Si, cuando descargas KlamAV tambien esta descargado todo que necesitas para usar KlamAV con GNOME.

Yo prefiero usar ClamTK para no tener que instalar las librerías QT en Gnome o Xfce, pero es un tema de gustos. Los 2 son solo interfaces para el mismo clamav.

---

### Post by leosr on 2008-12-02
> **gmunioz said:**
> Hola leo...:
Te sugiero instales clamav-freshclam clamav clamav-base clamav-daemon klamav
Klamav, es un front-end gráfico, se debe editar el menu y al comando anteponerle gksu, dado que para eliminar archivos infectados es necesario actuar con permisos temporarios de administrador.
Freshclam, es un demonio autónomo que actualizará, si estas conectado a internet, automáticamente las bases de datos de virus.
Clamav solo actua por mandato, es decir que por intermedio de Klamav deberás indicarle que y donde escanear, solo detecta y pone en cuarentena o elimina los archivos infectados, no repara ni limpia.
Es sumamente efectivo, liviano, seguro y de código libre. Se puede automatizar su actividad mediante scripts.
[B]Saludos.
Gabriel.[/B]
*Solo doy soporte para Ubuntu* **6666 -- Más malo que el diablo**.

Cómo se configura el Freshclam? Puede escanear los mails entrantes de Thunderbird en forma automática?

gracias.

---

### Post by gmunioz on 2008-12-07
Hola leo...:
Freshclam, no requiere absolutamente nada, una vez instalado en forma periódica tratará de actualizar las bases de virus, lo que logrará si estas conectado a internet.
Para revisar mails entrantes y salientes, thunderbird no alcanza, son necesarias las aplicaciones:
MailScanner Exim Clamav Clamav-freshclam Razor Unrar Lha Arj

El funcionamiento, consta en disponer de dos colas de correo, una para recibir y otra para enviar.

El correo que se recibe es almacenado por exim en sus carpetas.
Cada determinado lapso de tiempo MailScanner comprueba si hay o no hay correo nuevo
Si hay, lo analizará mediante su sistema antispam, el spamassassin y razor (red colaborativa para notificación de spam), y con el antivirus clamav.
Si el mensaje supera todos los criterios establecidos, lo moverá a la cola de salida, y exim, lo enviará adonde se desee (cuenta local de un usuario - equipo remoto - etc. etc.).
Esto mismo se puede implementar para el correo saliente.
Lógicamente deberás leer al respecto de las configuraciones en la red, donde hay varios tutoriales al respecto.
Por ejemplo:
[http://alufis35.uv.es/Configurar-Exim3-con-MailScanner-y.html](http://alufis35.uv.es/Configurar-Exim3-con-MailScanner-y.html)
Saludos.
Gabriel.
**Solo doy soporte para Ubuntu.*Hay tres clases de personas* - Las que saben contar y las que no**

---

### Post by Hei Ku on 2008-12-07
Como agregado, KMail tiene un plugin que funciona en conjunto con KlamAV para el chequeo de antivirus. Y otro plugin para el chequeo de spam usando Bogofilter.

---

### Post by santiagoward2000 on 2008-12-07
> **leosr said:**
> Puede escanear los mails entrantes de Thunderbird en forma automática?

Hay un add-on para el thunderbird para eso: [clamdrib]("https://addons.mozilla.org/en-US/thunderbird/addon/6663"). Todavía es experimental, y necesitás registrarte par poder bajarlo. La verdad que no sé que onda, como no quiero registrarme todavía no lo probé, pero puede que a alguien le interese.
Saludos!

---

### Post by pabloatilio on 2008-12-08
> **leosr said:**
> Hola.

Ya sé, me van a decir que no es necesario usar antivirus en Linux, que son inofensivos, que no existen, etc..
La idea es tener un antivirus para que escanear los archivos adjuntos de los mails o soft de Win descargado de la web, ya que comparto archivos con máquinas con Winchot y además tengo una partición con XP (por ahora). En la web veo que recomiendan el Avast, que tiene interfaz gráfica.
Qué recomiendan?

Saludos.


Yo tengo instalada la versión de AVG para linux y funciona muy bien, tiene interfaz gráfica si eso te interesa, la uso para  casi lo mismo que vos, todo archivo sospechoso primero lo escaneo con el AVG en Ubuntu y desde el mismo S.O. los copio en las carpetas de destino de W$ que sean necesarias. Además después si el archivo es muy dudoso le hago un escaneo con algún otro antivirus desde W$. Nunca está de mas y lo que no te detecta uno te lo puede llegar a detectar el otro.

Para los que quieran instalar el AVG para linux y no lo encuentren, tienen que bajar éste paquete :

[http://www.avg.com/filedir/inst/avg75fld-r51-a1243.i386.deb](http://www.avg.com/filedir/inst/avg75fld-r51-a1243.i386.deb)

Después lo instalan con Synaptic o desde terminal (apt-get).

Una vez instalado, para que funcione tiene que tener permisos de administrador, si alguien no sabe como automatizarlo, en el lanzador (está en las pestañas de las propiedades del icono, boton derecho -->propiedades) basta con que diga "gksudo avggui", después te va a pedir contraseña cuando lo inicies. La versión para linux de AVG, no tiene una protección en tiempo real.

Saludos.

PabloA

---

### Post by chulelinux on 2008-12-08
Hola a todos,

resulta que pasé clamtk y me arrojó lo siguiente, y no se que hacer con el mismo. Aparte, por más que marque "poner en cuarentena" como opción, no me hace nada con los archivos que aparecen con virus. Perdí el historial donde me aparecían otros dos más posibles virus... ¿Qué hago? 
SLDS y Gracias por cualquier ayuda...

Encontrados 1 posibles virus (97317 archivos escaneado).

/sys/kernel/slab/                                           0000320/slab_size
-----------------------------------------------------------------------------

---

### Post by gmunioz on 2008-12-09
Hola leo...:
Acabo de encontrar este plugin para thunderbird.
Es experimental, asi que para instalarlo debes registrarte en el sitio de addons.
No se como funciona, dado que hace años que me desligué de los virus, pues no solo no los uso, sino que ya me olvidé de los operativos de Microsoft.
Este es el sitio:
[https://addons.mozilla.org/es-ES/thunderbird/addon/6663?adv=true](https://addons.mozilla.org/es-ES/thunderbird/addon/6663?adv=true)
Saludos.
Gabriel.
**Solo doy soporte para Ubuntu - Existen muchas soluciones - Las equivocadas y la mia.**

---

