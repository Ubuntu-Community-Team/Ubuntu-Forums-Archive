---
title: "Gestor de actualizaciones en 9.04 no actualiza"
date: 2011-01-12
forum: Software
---

### Post by rubenb on 2011-01-12
Usuario novato en Linux. Ubuntu 9.04 en netbook MSI. Apareció un icono rojo con el mensaje "Ocurrió un problema al comprobar las actualizaciones". 
Al revisar var/log/syslog se lee:

Jan 12 17:50:01 ruben-laptop kernel: [  355.436982] apt-check[3385]: segfault at  1b529638 ip b7788613 sp bfd32c5c error 4 in [libc-2.9.so]("http://libc-2.9.so/")[b7711000+15c000]

Jan 12 17:53:06  ruben-laptop kernel: [  540.413410] update-manager[3437]: segfault at 192c0638  ip b773a613 sp bfbcb8fc error 4 in [libc-2.9.so]("http://libc-2.9.so/")[b76c3000+15c000]

Revisando ubuntuforums encontré:

[http://ubuntuforums.org/archive/index.php/t-1095767.html](http://ubuntuforums.org/archive/index.php/t-1095767.html)

>Try:
>sudo rm -vf /var/lib/apt/lists/*
>sudo dpkg --configure -a
>sudo  aptitude update
>sudo aptitude upgrade

Como en la línea de comandos soy un absoluto mono con navaja, pregunto si esa respuesta es aplicable en el caso de mi máquina. Sospecho que es aplicable, pero borrando en otro subdirectorio...
Cordial saludo.
-----------------------

---

### Post by hectorivand on 2011-01-12
Hola, no estoy seguro si está relacionado pero tene en cuenta que no hay más soporte para 9.04. Terminó en octubre de 2010.

[http://fridge.ubuntu.com/node/2132](http://fridge.ubuntu.com/node/2132)

Te recomiendo que actualices la distro.

Saludos
Nacho

---

### Post by rubenb on 2011-01-12
Gracias, hectorivand!
Me lo imaginaba...
Buscaré una versión netbook lts, entonces...
Cordial saludo.-

---

### Post by biale on 2011-01-13
Lo que te dijo hectorivand es cierto. Lo repositorios para 9.04 no van a incluir mas "actualizaciones" e incluso me queda la duda de si siguen existiendo en todos o cuales servidores.

Entretanto podrías revisar los "origenes de software" y si se puede salvar el error con 

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade       # que en este caso no seria util

---

### Post by rubenb on 2011-01-13
Gracias, Biale!
Consultas para vos o/y quienes lean este post:
1) qué significa "revisar los orígenes de software" y cómo lo hago?
2) si ejecuto los comandos que me copias en tu mensaje, teóricamente podría ingresar en repositorios que me permitiesen "subir" a 9.10 y de ahí a 10.04 que es un LTS?
3) otra posibilidad es probar si hay una versión para laptop de 10.04 (que es el LTS más reciente) e instalarlo encima. Alguna buena alma que me indique tutorial para "instalar encima"? (Para ponerla más fácil, uso una netbook con dual boot).
Gracias otra vez!

---

### Post by rubenb on 2011-01-13
.

---

### Post by biale on 2011-01-14
(1) En administracion/ Sistema aparece "origenes del software". La idea sería ubicar (si existe) algun servidor que mantenga 9.04. Suponiendo que exista...

(2) Dudo que sea lo mas recomendable. Si falla o no sale como debiera te quedas sin el pan y sin la torta.

(3) Si tenes el home separado, se puede reemplazar por 10.04 sin afectar los datos. O sea: nunca encima del home, hay que aclarar que no formatee esa particion o perdes los datos en ella. Igual yo haría un backup "tar" de las dos particiones. Es lo unico que hay que tener en cuenta.

Lo mejor es bajar una iso de la version que te guste, armar todo para un arranque live de cd o usb y probar todo lo que se pueda, que lo basico (aunque lento) funcione, que el HW sea detectado.

---

### Post by rubenb on 2011-01-14
> **biale said:**
> 
Lo mejor es bajar una iso de la version que te guste, armar todo para un arranque live de cd o usb y probar todo lo que se pueda, que lo basico (aunque lento) funcione, que el HW sea detectado.

Gracias biale!!!
Acabo de pasar por la página de descargas de lucid lynx, esta tarde bajo una iso de la versión netbook y la cargo en USB para ver si reconoce el wifi y la partición Redmond.
Habrá más novedades para este boletín!
--------------

---

