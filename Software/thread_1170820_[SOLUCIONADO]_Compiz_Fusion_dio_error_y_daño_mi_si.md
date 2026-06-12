---
title: "[SOLUCIONADO] Compiz Fusion dio error y daño mi sistema"
date: 2009-05-26
forum: Software
---

### Post by Matnet on 2009-05-26
resulta que explorando las capacidades de 9.04 me tope con un progama llamado ubuntu tweaks, que es, a mi juicio, bastante interesante. En este se me ofrecía instalar compiz fusion para tener acceso a mas efectos de ventanas y cosas así. Funcionó, pero con unos dias, y no se poerque, aparece un error que me indica que un tal xfonts 100dpi tiene un error y el sistema no se puede actualizar. ademas, ahora las vetanas no abren bien en todos los casos y apt y synaptic no se inician (muestran el error y cierran).

como puedo volver a metacity si no puedo instalar ni desinstalar???

pd: ya lo intente en modo texto y es igual

Gracias de antemano
MatNet

---

### Post by DarkTemplarMark on 2009-05-26
1- Por casualidad por consola te tira un error de segmentación?
2- Te aparece un signo de no entrar tipo europeo en el panel superior?

Si es así, intenta con el encargado de limpieza ver qué cosas puedes "limpiar" que estén fuera de regla. Me pasó algo similar, y así fue como lo solucioné (El tema todavía está en este mismo foro)(Agradecimientos a los respectivos usuarios que me dieron la idea)

---

### Post by Matnet on 2009-05-27
Aptitude y Synaptic muestran errores similares a este:

[html]asprev@Cyber00:~$ sudo apt-get install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar `apt-get -f install' para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
  foomatic-filters: Depende: libgs8 pero no está instalado
  ghostscript: Depende: libgs8 (= 8.64.dfsg.1-0ubuntu8) pero no está instalado
  libspectre1: Depende: libgs8 pero no está instalado
  marble: Depende: libqt4-net&#65533;ork (>= 4.5.0~+rc1) pero no es instalable
          Depende: libqt4-svg! (>= 4.5.0~+rc1) pero no es instalable
E: Dependencias incumplidas. Pruebe de nuevo usando -f.[/html]Creo que debería borrar marble del archivo status... talvés eso ayude...

---

### Post by Carlos C on 2009-05-28
¿y si pruebas con lo que te sugiere el mensaje de error?
```
apt-get -f install
```

---

### Post by Matnet on 2009-05-31
Hola,

Afortunadamente conseguí reparar el problema a través del borrado de los archivos defectuosos del registro de Status.

Ahora el problema es más grave. Pasaron unas 2 dias OK, y luego, el sistema no encendía, porque al iniciarse ubuntu aparece una pantalla distorsionada que es como un pantallazo de la ultima imagen mostrada por WinXP (ya que es un sistema dual).

He intentado repararlo a traves del inicio de recuperación, pero los comandos DPKG y XFIX no consiguen nada.

Les indico los componentes :

Tarjeta ATI Radeon x550 256Mb
Ubuntu 9.04
WinXP SP3
Metacity
Compiz Fusion
Configuración con efectos 0 de pantalla
inicio automatico de sesión
firewall (esto porque pide la contraseña para iniciarlo y pone la pantalla oscurecida para ello)

creo que estos serán datos suficientes

Muchas Gracias de Antemano
MatNet

---

### Post by Matnet on 2009-06-01
> **Matnet said:**
> Hola,

Afortunadamente conseguí reparar el problema a través del borrado de los archivos defectuosos del registro de Status.

Ahora el problema es más grave. Pasaron unas 2 dias OK, y luego, el sistema no encendía, porque al iniciarse ubuntu aparece una pantalla distorsionada que es como un pantallazo de la ultima imagen mostrada por WinXP (ya que es un sistema dual).

He intentado repararlo a traves del inicio de recuperación, pero los comandos DPKG y XFIX no consiguen nada.

Les indico los componentes :

Tarjeta ATI Radeon x550 256Mb
Ubuntu 9.04
WinXP SP3
Metacity
Compiz Fusion
Configuración con efectos 0 de pantalla
inicio automatico de sesión
firewall (esto porque pide la contraseña para iniciarlo y pone la pantalla oscurecida para ello)

creo que estos serán datos suficientes

Muchas Gracias de Antemano
MatNet

Ademas les añado que hoy probé borrar el archivo de paginación de windows y desfragmentar el disco, pero no pasó nada.

Estoy pensando seriamente en reinstalar ubuntu

---

### Post by Carlos C on 2009-06-02
Creo que has hecho varios cambios y no es fácil saber en qué estado está tu equipo. Dices que borraste archivos defectuosos del registro de Status, no sabemos cómo lo hiciste, por lo tanto es difícil saber si era la mejor decisión o no (tengo la impresión de que fue mala idea). Te sugerí que probaras con el comando que te daba el error pero no comentaste si eso te entregó más información. La razón por la que te comento estas cosas es para que entiendas que se hace difícil ayudarte cuando no interaccionas con nosotros. En este caso no dialogaste con nadie.
Si de algo sirve, en vista de que ya hiciste cambios y al parecer no tienes datos importantes que recuperar, reinstala Ubuntu y, para la próxima, te sugiero que nos comentes tu situación, dando toda la información necesaria, y luego respondas a las preguntas que se te hacen.

Mucha suerte con eso y espero que al reinstalar la cosa marche de nuevo.
Saludos!

---

### Post by Dan_Dranath999 on 2009-06-02
lo más fácil hubiese sido ejecutar la recomendación de la consola:

```
apt-get -f install
```

Yo creo que el problema es que durante el proceso de alguna actualización o instalación, no se hayan podido descargar algunas dependencias

---

### Post by Carlos C on 2009-06-02
> **dan_dranath999 said:**
> lo más fácil hubiese sido ejecutar la recomendación de la consola:

```
apt-get -f install
```yo creo que el problema es que durante el proceso de alguna actualización o instalación, no se hayan podido descargar algunas dependencias
+1 ;)

---

### Post by Matnet on 2009-06-02
> **Carlos C said:**
> +1 ;)


explico:

intente el modo forzado (-f) varias veces, y decia que los repositorios estaban mal, por lo que simplemente indique que los repositorios se configuraran por defecto

los porgramas que borre son unos que se instalaron mal cuando puse el paquete de edubuntu, por lo cual no eran escenciales.

posteriormente synaptic indico que tenía cuatro paquetes rotos; los desinstale y volví a instalar.

en ese momento el sistema funcionó bien

creo que tengo ya una respuesta a mi pregunta, porque me parece que un virus entró a windows, dañó el grub y hoy en la mañana bloqueo el ingreso a windows.

lo bueno es que tengo las particiones de documentos separadas.

muchas gracias por su apoyo y les aviso si puedo solucionar este problema con un formateo dual.

por lo demas creo que el problema de compiz fusion está reparado.

hasta luego
MatNet

---

