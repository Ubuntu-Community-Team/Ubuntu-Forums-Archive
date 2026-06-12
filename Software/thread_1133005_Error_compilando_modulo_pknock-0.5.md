---
title: "Error compilando modulo pknock-0.5"
date: 2009-04-22
forum: Software
---

### Post by dhcancelo on 2009-04-22
Buenas.
Escribo para ver si alguien me ilumina.
Estoy tratando de compilar el modulo pknock-0.5 para iptables y poder
utilizar portknocking.

Uso Debian Lenny (actualizado y sin entorno grafico, una instalacion
basica), kernel linux server 2.6.26-1-amd64 e iptables version 1.4.2-6
configurado mediante un script que tengo dentro de init.d
Instale los build-essential para poder compilar e iptables-dev v.1.4.2-6.

Me baje pknock-0.5 desde aca
[http://developer.berlios.de/project/showfiles.php?group_id=7093](http://developer.berlios.de/project/showfiles.php?group_id=7093)
Y estas son las instrucciones que figuran en la web:

# cd portknocko
# ~/portknocko/cd iptables
# ~/portknocko/iptables/make clean
# ~/portknocko/iptables/make
# ~/portknocko/iptables/make install

# cd ../kernel
# ~/portknocko/kernel/make clean
# ~/portknocko/kernel/make
# ~/portknocko/kernel/make install

# depmod -Ae

Pero al hacer make tengo este problema.

server:~/pknock-0.5/iptables# make clean
rm -fv libipt_pknock_sh.o libipt_pknock.so *.o *.so *.so.* *~
server:~/pknock-0.5/iptables# make
cc -O2 -Wall -Wunused -I/usr/src/linux/include
-I/usr/include/iptables-1.4.0 -DIPTABLES_VERSION=\"1.4.2\"  -fPIC -o
libipt_pknock_sh.o -c libipt_pknock.c
libipt_pknock.c:15:22: error: iptables.h: No existe el fichero o el directorio
libipt_pknock.c:51: warning: 'struct xt_entry_match' declared inside
parameter list
libipt_pknock.c:51: warning: its scope is only this definition or
declaration, which is probably not what you want
libipt_pknock.c: In function 'parse_ports':
libipt_pknock.c:79: warning: implicit declaration of function 'string_to_number'
libipt_pknock.c: At top level:
libipt_pknock.c:111: warning: 'struct xt_entry_match' declared inside
parameter list
libipt_pknock.c: In function 'parse':
libipt_pknock.c:116: error: dereferencing pointer to incomplete type
libipt_pknock.c:121: warning: implicit declaration of function 'exit_error'
libipt_pknock.c:121: error: 'PARAMETER_PROBLEM' undeclared (first use
in this function)
libipt_pknock.c:121: error: (Each undeclared identifier is reported only once
libipt_pknock.c:121: error: for each function it appears in.)
libipt_pknock.c: In function 'final_check':
libipt_pknock.c:237: error: 'PARAMETER_PROBLEM' undeclared (first use
in this function)
libipt_pknock.c: At top level:
libipt_pknock.c:283: warning: 'struct xt_entry_match' declared inside
parameter list
libipt_pknock.c: In function 'print':
libipt_pknock.c:288: error: dereferencing pointer to incomplete type
libipt_pknock.c: At top level:
libipt_pknock.c:307: warning: 'struct xt_entry_match' declared inside
parameter list
libipt_pknock.c: In function 'save':
libipt_pknock.c:312: error: dereferencing pointer to incomplete type
libipt_pknock.c: At top level:
libipt_pknock.c:334: error: variable 'pknock' has initializer but
incomplete type
libipt_pknock.c:335: error: unknown field 'name' specified in initializer
libipt_pknock.c:335: warning: excess elements in struct initializer
libipt_pknock.c:335: warning: (near initialization for 'pknock')
libipt_pknock.c:336: error: unknown field 'version' specified in initializer
libipt_pknock.c:336: warning: excess elements in struct initializer
libipt_pknock.c:336: warning: (near initialization for 'pknock')
libipt_pknock.c:337: error: unknown field 'size' specified in initializer
libipt_pknock.c:337: warning: implicit declaration of function 'IPT_ALIGN'
libipt_pknock.c:337: warning: excess elements in struct initializer
libipt_pknock.c:337: warning: (near initialization for 'pknock')
libipt_pknock.c:338: error: unknown field 'userspacesize' specified in
initializer
libipt_pknock.c:338: warning: excess elements in struct initializer
libipt_pknock.c:338: warning: (near initialization for 'pknock')
libipt_pknock.c:339: error: unknown field 'help' specified in initializer
libipt_pknock.c:339: warning: excess elements in struct initializer
libipt_pknock.c:339: warning: (near initialization for 'pknock')
libipt_pknock.c:340: error: unknown field 'init' specified in initializer
libipt_pknock.c:340: warning: excess elements in struct initializer
libipt_pknock.c:340: warning: (near initialization for 'pknock')
libipt_pknock.c:341: error: unknown field 'parse' specified in initializer
libipt_pknock.c:341: warning: excess elements in struct initializer
libipt_pknock.c:341: warning: (near initialization for 'pknock')
libipt_pknock.c:342: error: unknown field 'final_check' specified in initializer
libipt_pknock.c:342: warning: excess elements in struct initializer
libipt_pknock.c:342: warning: (near initialization for 'pknock')
libipt_pknock.c:343: error: unknown field 'print' specified in initializer
libipt_pknock.c:343: warning: excess elements in struct initializer
libipt_pknock.c:343: warning: (near initialization for 'pknock')
libipt_pknock.c:344: error: unknown field 'save' specified in initializer
libipt_pknock.c:344: warning: excess elements in struct initializer
libipt_pknock.c:344: warning: (near initialization for 'pknock')
libipt_pknock.c:345: error: unknown field 'extra_opts' specified in initializer
libipt_pknock.c:346: warning: excess elements in struct initializer
libipt_pknock.c:346: warning: (near initialization for 'pknock')
libipt_pknock.c: In function '_init':
libipt_pknock.c:350: warning: implicit declaration of function 'register_match'
make: *** [libipt_pknock_sh.o] Error 1
server:~/pknock-0.5/iptables#

Dentro de la carpeta iptables este es el Makefile que hay dentro:

KERNEL_DIR_INC=/usr/src/linux/include
IPT_DIR_INC=/usr/include/iptables-1.4.0
IPT_LIB_DIR=/lib/iptables
IPTABLES_VERSION=$(shell iptables -V | sed 's/iptables v//')
CC=cc
LD=cc
CFLAGS=-O2 -Wall -Wunused -I$(KERNEL_DIR_INC) -I$(IPT_DIR_INC)
-DIPTABLES_VERSION=\"$(IPTABLES_VERSION)\"  -fPIC
LDFLAGS=-shared
OBJS=libipt_pknock_sh.o
LIBS=libipt_pknock.so
all : $(OBJS) $(LIBS)
$(OBJS): libipt_pknock.c
       $(CC) $(CFLAGS) -o $@ -c $^
$(LIBS): libipt_pknock_sh.o
       $(LD) $(LDFLAGS) -o $@ $^
install:
       cp libipt_pknock.so $(IPT_LIB_DIR)
uninstall:
       rm -fv $(IPT_LIB_DIR)$(LIBS)
clean:
       rm -fv $(OBJS) $(LIBS) *.o *.so *.so.* *~

¿Tienen idea cual puede ser el problema?
De antemano muchas gracias.
Saludos.
Wex.

---

### Post by Hei Ku on 2009-04-22
Por empezar, te falta el iptables.h, asi que supongo que te falta instala el paquete dev de iptables. Verifica cuales son los requisitos para instalar, y bajate los paquetes dev de esos programas.

---

### Post by dhcancelo on 2009-04-22
> **Hei Ku said:**
> Por empezar, te falta el iptables.h, asi que supongo que te falta instala el paquete dev de iptables. Verifica cuales son los requisitos para instalar, y bajate los paquetes dev de esos programas.

Gracias por tu respuesta. Lo instale despues de compilar la primera vez. Igual al instalar iptables-dev seguia sin encontrar el fichero iptables.h que aperecio de una vez luego de instalar linux-headers'uname -r'
Pero me sigue dando el error.
Tenes alguna idea? 
Saludos.

---

### Post by Hei Ku on 2009-04-22
me parece que falta primero correr un configure.

./configure

---

### Post by clasificado on 2009-04-22
estube buscando un header de iptables y no encontré ninguno como la gente :S

y tirando un sudo apt-file search iptables.h tampoco me dio ninguno asi copado

Creo que son de esas cosas "por distro" tan comunes en linux. Habrán preparado el source contra el snapshot del kernel, y ubuntu puede estar un tanto alejado de eso

clasificado

---

### Post by dhcancelo on 2009-04-23
> **Hei Ku said:**
> me parece que falta primero correr un configure.

./configure

las pocas veces que compile siempre use ./configure antes del make y make install pero en este caso en particular las instrucciones son estas de abajo, por eso no lo use.

# cd portknocko
# ~/portknocko/cd iptables
# ~/portknocko/iptables/make clean
# ~/portknocko/iptables/make
# ~/portknocko/iptables/make install

# cd ../kernel
# ~/portknocko/kernel/make clean
# ~/portknocko/kernel/make
# ~/portknocko/kernel/make install

# depmod -Ae

---

### Post by dhcancelo on 2009-04-23
> **clasificado said:**
> estube buscando un header de iptables y no encontré ninguno como la gente :S

y tirando un sudo apt-file search iptables.h tampoco me dio ninguno asi copado

Creo que son de esas cosas "por distro" tan comunes en linux. Habrán preparado el source contra el snapshot del kernel, y ubuntu puede estar un tanto alejado de eso

clasificado

ok. es posible.. tendre que implementar esto de otra forma.
muchas gracias por tu respuesta.
saludos.

---

### Post by clasificado on 2009-04-23
PD: Volvé que el port knoking un poco también me interesa :P

clasificado

---

### Post by dhcancelo on 2009-04-23
> **clasificado said:**
> PD: Volvé que el port knoking un poco también me interesa :P

clasificado

No hay problema, me quedo por aca.. je
Hoy voy a tratar de implementar portknocking de otra manera, mediante reglas en el script de iptables utilizando el modulo recent. despues te cuento como me fue.
Por otro lado, con respecto al pknock-0.5, al parecer tiene problemas porque busca el iptables.h en otro path. Un amigo esta modificando en codigo, ya compilo la parte de iptables y le falta la parte del kernel (a mi para esto no me da... hace un par de años que estoy con linux pero no se programar), sin tengo alguna novedad sobre esto tambien te aviso.
Saludos.

---

### Post by pablo.s on 2009-04-23
Y [este]("http://packages.ubuntu.com/jaunty/knockd") paquete no te sirve?

---

### Post by dhcancelo on 2009-04-23
> **pablo.s said:**
> Y [este]("http://packages.ubuntu.com/jaunty/knockd") paquete no te sirve?

Ese paquete lo tengo esperando si esta segunda opcion no me anda.
Igual me interesaba mucho lo primero, el pknock-0.5, porque si anda es mas que facil de configurar. solo hace falta una linea como esta en el script de iptables: $IPTABLES -A INPUT -i eth0 -p tcp -m state --state NEW -m pknock --knockports 2001,2002,2003 --name SSH -m tcp --dport 22 -j ACCEPT

---

### Post by dhcancelo on 2009-04-24
Bueno.. por el momento (al no poder compilar pknock-0.5) implemente el portknocking de otra manera. 
Usando el modulo recent que ya viene incluido en el kernel. Tenes que agregar unas cuantas lineas al script pero funciona.

Aca esta el link de donde saca la info:
[http://www.esdebian.org/wiki/port-knocking](http://www.esdebian.org/wiki/port-knocking)

saludos
wex.

PD: no marque como solucionado, pues si bien ya funciona el portknocking esperare a ver si lo hago funcionar con el pknock

---

