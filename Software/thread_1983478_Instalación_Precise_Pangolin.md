---
title: "Instalación Precise Pangolin"
date: 2012-05-20
forum: Software
---

### Post by Vero1 on 2012-05-20
Hola,

Como dice el título, estoy por instalar Precise Pangolin, que ya tengo grabado en un DVD.

Ahora, necesito por favor me indiquen cuál es la forma de no perder mi home, como tampoco los Bookmarks de Firefox y el Correo y Adress Book de Thunderbird.

Pido esta información ya que la última vez hice upgrade a la versión actual y me trajo algunos problemas desde el principio.

Desde ya muchas gracias por su ayuda.

saludos

---

### Post by gmunioz on 2012-05-20
Inicia la instalación.
Al llegar a particionamiento elige manual.
Selecciona la partición para /, acepta se formatee, en el sistema que esta o en el que mas te guste, ext4 es el mas conveniente.
Selecciona la partición para /home, en el sistema en que se encuentra, no le des formato.
Selecciona la partición swap, las opciones por defecto.
El Grub en el mbr de /dev/sda

Utiliza el mismo nombre de usuario y la misma contraseña.

---

### Post by ubuntu27 on 2012-05-20
Siempre es bueno hacer una copia de seguridad antes de instalar cualquier sistema operativo.

Copia tus archivos personales en un disco portable, USB Drive, o DVD.

Looks Bookmarks de Firefox se puede grabar haciendo...:

1) menu Bookmarks
2)Mostrar todos los Bookmars (Show all bookmarks)
3) menu Import and Backup
4) Backup...
5) Guardalo en un lugar seguro

list.

No se como guardar de Thunderbird. Pero seguramente puedes copiar el /home/nombre-usuario/.thunderbird

---

### Post by Vero1 on 2012-05-21
Muchas gracias a los dos.

saludos

---

### Post by Vero1 on 2012-05-22
Hola,
Ya he instalado Precise Pangolin y tambien pude transferir los Bookmarks pero tengo problemas para instalar thunderbird.tar.gz donde están todos mis mails y Adress Book, porque no encuentro cómo hacerlo.

Este archivo está actualmente en Documentos pero no veo que haya  opción de importarlo.

Por otro lado el Servidor me rechaza la contraseña(que siempre fue la misma), pero lo curioso es que pasa nada mas al abrir la aplicación, no así cuando quiero enviar un correo. En fin, estuve toda la tarde probando una cosa y otra sin lograr nada.

Si alguien me contesta por favor que sea a: [email]veronicab647@hotmail.com[/email], ya que no puedo recibir en mi correo habitual.

Muchas gracias.

---

### Post by guillermolisi on 2012-05-22
Exactamente, cual fue el punto de origen que utilizaste para generar ese tarball con los mails y las direcciones ?

Es decir, cual fue el directorio en el cual te paraste para generar esa copia ?

---

### Post by EnriqueK on 2012-05-22
Prueba hacer lo siguiente
1.- Respalda por las dudas el directorio oculto situado dentro de tu carpeta personal .thunderbird , para ello ejecuta
cd && mv .thunderbird .thunderbird1
2. abre otro terminal y pones
tar -zxvf
dejas un espacio
arrastra a este terminal el respaldo thunderbird.tar.gz
escribes -C /
pulsa Enter y ya

---

### Post by Vero1 on 2012-05-23
Hola Guillermo,

Fue en mi home, archivos ocultos, thunderbird.
Hoy por fin pude lograr que acepte la contraseña. Faltaba indicar que fuera una contraseña segura, cosa que antes se hacía de otra manera, o sea directamente no necesitaba aclarar éso porque tomaba la configuraciòn de Windows donde se indica: mi Servidor necesita autenticaciòn, pero bueno, éso ya está. Han bajado mails que estaban en el Servidor. Aparentemente el correo funciona.
Pero de todas formas me gustaría recuperar el archivo .tar.gz. 
Muchas gracias.

Hola EnriqueK,

ok intentaré hacer lo que me decís.

Muchas gracias

---

### Post by Vero1 on 2012-05-24
Hola EnriqueK,

Es para decirte que ya pude trasladar el contenido de .thunderbird y está todo ok.

Muchas gracias y saludos

---

