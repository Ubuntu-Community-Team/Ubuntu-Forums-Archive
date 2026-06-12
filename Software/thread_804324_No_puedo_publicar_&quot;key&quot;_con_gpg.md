---
title: "No puedo publicar &quot;key&quot; con gpg"
date: 2008-05-23
forum: Software
---

### Post by RJQ on 2008-05-23
Por alguna razón no he podido publicar mi llave, desconozco cual sea la razon, gpg no puede hacerlo con ningun servidor resultando siempre in errores como este

gpg: keyserver internal error
gpg: keyserver send failed: keyserver error

lo he intentado en varias ocasiones sin resultado, estoy usando Hardy, cualquier ayuda o comentario es bienvenido.:confused:

---

### Post by euzkoarima on 2008-05-23
Yo esto lo hice ayer sin problemas, pero con 7.10

Se poco de esto, pero pregunta, es cuando haces gpg --send-keys que te da ese error ?

y por las dudas, estas siguiendo el [instructivo este]("https://help.ubuntu.com/community/FirmandoElCodigoDeConductaComo") ?

Saludos.

---

### Post by sergiom99 on 2008-05-23
yo tuve que hacer todos los comandos con sudo.
no tenia permiso para leer mi propio ~/.gnupg
y el paso de firmar el CC me pasa esto>
```
sergio@kubuntu:~$ sudo gpg --clearsign UbuntuCodeofConduct-1.0.1.txt

You need a passphrase to unlock the secret key for
user: "Sergio M (BUE @ ar) <xxxx@hotmail.com>"
1024-bit DSA key, ID 035CCE21, created 2008-05-24

gpg: gpg-agent is not available in this session
gpg: can't open `UbuntuCodeofConduct-1.0.1.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.0.1.txt: clearsign failed: file open error
```
ahi quedo

---

### Post by sergiom99 on 2008-05-23
ya lo arregle. me comi (o no lo dice) la parte del tutorial donde tenes que descargarte el CoC al home.

---

### Post by RJQ on 2008-05-23
> **euzkoarima said:**
> Yo esto lo hice ayer sin problemas, pero con 7.10

Se poco de esto, pero pregunta, es cuando haces gpg --send-keys que te da ese error ?

y por las dudas, estas siguiendo el [instructivo este]("https://help.ubuntu.com/community/FirmandoElCodigoDeConductaComo") ?

Saludos.

En efecto he seguido el tutorial y precisamente es cuando quiero mandar las llaves que me da el error, creo que lo dejo por ahora desconozco totalmente este tema, estoy por intentar con kubuntu tal vez sale mejor, si por ahí encuentro algo relacionado luego lo comento por aquí, gracias por sus comentarios, salud!!

---

### Post by MeduZa on 2008-05-24
hubo un update el otro dia referido a eso capas que tenga que ver, fue afectado todo lo referido a llaves,

---

### Post by sajnox on 2008-05-24
Meduza, 

No creo que eso sea la causa ya que vi algunas personas que se subscribieron con el tuto que indica RJQ y no tuvieron problemas

Saludos,

RJQ: Yo se que probablemente lo hayas hecho mas de una vez, pero el tutorial esta muy probado (te diria que por lo menos por la GRAN mayoria de todos los que se anotaron como ubunteros) Revisa paso a paso y arranca de cero en caso de ser necesario.

Te lo dice uno que lo hizo facil cuatro veces (esta en el user no en el tuto)

---

### Post by RJQ on 2008-05-24
No me lo tomes a mal sajnox, claro que se que el tutorial(guía) funciona y ademas que este te da información extra que no encuentras simplemente en launchpad, de hecho no fue lo primero que hice este tuto vendría a ser uno de mis segundos intentos, es por eso que recurrí al grupo viendo que aquí aveces hay mas avance que en ingles para ciertos detalles, creo que en mi caso alguna falla a de tener mi gpg he notado mi HH medio buggy casi al mismo nivel que GG, para esto es la tercera vez que reinstalo (y definitiva no tengo mucho tiempo ni ganas de reacomodar mi escritorio) por lo que creo que es algo en el sistema, y con eso que con mi dialup no me puedo dar lujo de actualizar es algo con lo que prefiero dejar de lidiar asta el siguiente, les digo voy a intentar en kubuntu, también si de casualidad salgo con una solución por aquí la ponemos luego. salud!!

---

### Post by faktorqm on 2008-05-25
Si, si yo traduje las 3 notificaciones con los problemas y NADIE fue capaz de contestar....... ¬¬ 

yo ahora tengo ke volver a subir mis llaves.... Salu2!

---

### Post by alejandro.mc on 2008-05-25
Te cuento yo tambien tuve un par de problemas para esto. Fijate este post mio de cuando tuve esos problemas, por ahi hiciste algo diferente, no se. A veces tenes que esperar unas horas despues de hacer algunos pasos, para que los servidores que tienen que renovar informacion te cuenten.

[http://ubuntuforums.org/showthread.php?t=741611](http://ubuntuforums.org/showthread.php?t=741611)

Saludos y suerte!

---

### Post by faktorqm on 2008-05-25
Despues de leer este post, me decidi a subir mi llave de vuelta.

El error tuyo tambien lo tuve, pero lo saltié escribiendo un comandito que lei por ahi, aca va la salida completa (lo que esta en # es info personal :P):

```

faktorqm@the-edge:~$ gpg --gen-key
gpg (GnuPG) 1.4.6; Copyright (C) 2006 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.

Por favor seleccione tipo de clave deseado:
   (1) DSA y ElGamal (por defecto)
   (2) DSA (sólo firmar)
   (5) RSA (sólo firmar)
¿Su elección?:
El par de claves DSA tendrá 1024 bits.
las claves ELG-E pueden tener entre 1024 y 4096 bits de longitud.
¿De qué tamaño quiere la clave? (2048)
El tamaño requerido es de 2048 bits
Por favor, especifique el período de validez de la clave.
         0 = la clave nunca caduca
      <n>  = la clave caduca en n días
      <n>w = la clave caduca en n semanas
      <n>m = la clave caduca en n meses
      <n>y = la clave caduca en n años
¿Validez de la clave (0)? 6m
La clave caduca vie 21 nov 2008 19:40:25 ARST
¿Es correcto (s/n)? s

Necesita un identificador de usuario para identificar su clave. El programa
construye el identificador a partir del Nombre Real, Comentario y Dirección
de Correo Electrónico de esta forma:
    "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

Nombre y apellidos: Faktor Q. Minimoog
Dirección de correo electrónico: faktorqm###@#####.com
Comentario: faktorqm
Ha seleccionado este ID de usuario:
    "Faktor Q. Minimoog (faktorqm) <faktorqm###@#####.com>"

¿Cambia (N)ombre, (C)omentario, (D)irección o (V)ale/(S)alir? v
Necesita una frase contraseña para proteger su clave secreta.

Es necesario generar muchos bytes aleatorios. Es una buena idea realizar
alguna otra tarea (trabajar en otra ventana/consola, mover el ratón, usar
la red y los discos) durante la generación de números primos. Esto da al
generador de números aleatorios mayor oportunidad de recoger suficiente
entropía.
++++++++++++++++++++++++++++++..++++++++++++++++++++++++++++++.+++++++++++++++.+++++++++++++++.+++++.+++++++++++++++++++++++++.+++++++++++++++>+++++.........................<..+++++...............>+++++.........................................................+++++

No hay suficientes bytes aleatorios disponibles. Por favor, haga algún
otro trabajo para que el sistema pueda recolectar más entropía
(se necesitan 119 bytes más).
Es necesario generar muchos bytes aleatorios. Es una buena idea realizar
alguna otra tarea (trabajar en otra ventana/consola, mover el ratón, usar
la red y los discos) durante la generación de números primos. Esto da al
generador de números aleatorios mayor oportunidad de recoger suficiente
entropía.
++++++++++.+++++..++++++++++.++++++++++++++++++++++++++++++..++++++++++++++++++++.++++++++++++++++++++.++++++++++..++++++++++...++++++++++++++++++++.+++++..+++++>+++++..+++++>.+++++.............+++++^^^
gpg: clave CF58B### marcada como de confianza absoluta
claves pública y secreta creadas y firmadas.

gpg: comprobando base de datos de confianza
gpg: 3 dudosa(s) necesarias, 1 completa(s) necesarias,
modelo de confianza PGP
gpg: nivel: 0  validez:   1  firmada:   0  confianza: 0-, 0q, 0n, 0m, 0f, 1u
gpg: siguiente comprobación de base de datos de confianza el: 2008-11-21
pub   1024D/CF58B### 2008-05-25 [[caduca: 2008-11-21]]
      Huella de clave = #### 1C8F 5B09 35B7 3A6A  6939 0BEF D358 CF58 B064
uid                  Faktor Q. Minimoog (faktorqm) <faktorqm###@#####.com>
sub   2048g/CB3E6149 2008-05-25 [[caduca: 2008-11-21]]

faktorqm@the-edge:~$ gpg --fingerprint
/home/faktorqm/.gnupg/pubring.gpg
---------------------------------
pub   1024D/CF58B### 2008-05-25 [[caduca: 2008-11-21]]
      Huella de clave = #### 1C8F 5B09 35B7 3A6A  6939 0BEF D358 CF58 B064
uid                  Faktor Q. Minimoog (faktorqm) <faktorqm###@#####.com>
sub   2048g/CB3E6149 2008-05-25 [[caduca: 2008-11-21]]

faktorqm@the-edge:~$ gpg --send-keys CF58B###
gpg: no hay servidores de claves conocidos (use opción --keyserver)
gpg: envío al servidor de claves fallido: URI incorrecto
faktorqm@the-edge:~$ gpg --keyserver keyserver.ubuntu.com --send-keys CF58B###
gpg: enviando clave CF58B### a hkp servidor keyserver.ubuntu.com
faktorqm@the-edge:~$ gpg --decrypt firma

BLABLABLABLA
Please go here to finish adding the key to your Launchpad account:

    https://launchpad.net/token/4fWPDH8jJ6g66Jh36###
faktorqm@the-edge:~$

```

Espero que les sirva. (Yo no firmé el CoC por que ya lo había firmado hace mucho) Salu2!!

---

### Post by euzkoarima on 2008-05-27
No estoy seguro de que puede ser, pero tiro un par de ideas. Por lo que vi podría ser un tema del server con el te conectas. Haciendo memoria, yo instalé seahorse antes de comenzar con esto. Es anecdótico, hize todo desde la terminal. Pero si miro en mi $HOME/.gunpg/gpg.conf dice
> keyserver hkp://subkeys.pgp.net

y según el seahorse en preferencias, servidores de claves, dice
> hkp://pgp.mit.edu:11371

Y según el man de gpg para --send-keys podés decir a que servidor conectarte con la opción --keyserver name

Proba de hacer
> gpg --keyserver subkeys.pgp.net --send-keys $GPGKEY
y
> gpg --keyserver pgp.mit.edu --send-keys $GPGKEY

a ver que pasa. (Obviamente a $GPGKEY lo reemplazar por tu clave)

---

### Post by RJQ on 2008-05-27
> **euzkoarima said:**
> No estoy seguro de que puede ser, pero tiro un par de ideas. Por lo que vi podría ser un tema del server con el te conectas. Haciendo memoria, yo instalé seahorse antes de comenzar con esto. Es anecdótico, hize todo desde la terminal. Pero si miro en mi $HOME/.gunpg/gpg.conf dice


y según el seahorse en preferencias, servidores de claves, dice


Y según el man de gpg para --send-keys podés decir a que servidor conectarte con la opción --keyserver name

Proba de hacer

y


a ver que pasa. (Obviamente a $GPGKEY lo reemplazar por tu clave)

Sabes que poco antes dejar de lado este asunto en mi compu me percate de que el problema radica en los puertos, es decir por alguna razon gpg no puede abrirlo (11371) y la verdad no tengo idea de como sucede y por lo tanto de como solucionarlo, he de lei un poco hacerca de usar el puerto 80, pero totalmente desconozco como hacer que gpg mande la informacion usando otro puerto, es mas desconozco todo referente a puertos y como funcionan, lo unico que puedo dar por cierto es que no uso ningun firewall, de ahi no se pa donde.
salud!! y gracias por sus sujerencias

---

### Post by euzkoarima on 2008-05-29
Che, hace desde que conteste que no me conecto. Es muy raro lo que contas de los puertos.
Alguno que sepa más de redes ?????

Suerte.

---

### Post by faktorqm on 2008-05-30
Para abrir un puerto tendrias que escribir algo parecido a esto:

```
sudo iptables -A INPUT -i eth0 -p tcp -m tcp --dport 11371 -m state --state NEW -j ACCEPT
```

y digo parecido por que en este caso es eth0, pero pueden tener eth1 y el puerto bueno, obviamente cambia el numero por el que quieras, si queres abrir uno udp, cambiar tcp por udp xD salu2!

---

