---
title: "Cobol en Linux (Ubuntu)"
date: 2009-05-01
forum: Software
---

### Post by NickCis on 2009-05-01
Hola, ando nececitando usar programas de cobol en linux. La idea seria ayudar a pasar una oficina y server de windows a cobol.

Pense en usar algun emulador de DOS como Dosbox para poder correr el exe.
Tambien lei que se pueden recopilar y usar de forma nativamente en linux, algo de rmcobol o algo asi.

Mi situacion es que el programa se encontraria en un server, conectado por LAN a varios clientes. Los clientes ejecutarian los programas directamente del server. Ademas, varios de estos clientes tienen impresoras que el programa (en cobol, que esta ubicado en el server) que se ejecuta en ese mismo cliente usa para imprimir.

Que me recomiendan hacer? y Como lo podria hacer?.

Saludos.

---

### Post by gmunioz on 2009-05-02
Hola nic...:

OpenCOBOL es la aplicación que en las distribuciones Linux

implementa las partes substanciales de los standars de COBOL 85

y COBOL 2002.  OpenCOBOL traduce el código COBOL al lenguaje C 

y posteriormente lo compila usando GCC.

Saludos.

---

### Post by NickCis on 2009-05-03
Ok, muchas gracias, descarto la posibilidad de usar un emulador de DOS :P.

Que me dicen de usar Tiny Cobol ( [http://tiny-cobol.sourceforge.net/](http://tiny-cobol.sourceforge.net/) ) o Rm cobol ?.
Osea, tienen alguna ventaja frente a opencobol?.

Alguien tiene alguna experiencia en esto?.

Saludos.
P.D.: hay algun paquete deb de estos programas?, tengo que instalarlo en varias maquinas, compilarlo en cada una tardaria demaciado y seria molesto, puedo hacer un paquete deb en una maquina y despues pasarlo a las demas?.

---

### Post by gmunioz on 2009-05-03
Hola:

Opencobol esta en los repositorios.

Saludos.

---

### Post by NickCis on 2009-05-06
No se puede compilar en cobol directamente para linux?, hay algun ventaja/desventaja usar OpenCobol (que lo pasa a C)?

El tema es que me pidieron ayuda para mudar una red de un local que trabaja en Cobol a linux, (estan harto de windows por licencias y todo eso). Ellos usan cobol en todos sus programas, el programador tiene la licencia (o eso que le compras a microfocus), y me tendria que apegar mas a cobol.

Alguna idea?.

Saludos.

---

### Post by gmunioz on 2009-05-07
Hola nic.....:

En principio te sugiero, si vas a mudar una red local a Linux, que 

utilices Debian Lenny, esto porque es estable, no se actualiza cada 6 

meses como Ubuntu y si es necesario actualizar la distribuciòn no hace 

falta reinstalar con solo utilizar en los repositorios en lugar del 

nombre propio de la distribuciòn Lenny - Squeeze su denominaciòn 

genérica stable - testing, cada vez que se cambie la versiòn, el sistema 

se actualizará sin contratiempos y se mantendrá asì permanentemente.

Respecto de opencobol es básicamente un traductor: traduce el código

COBOL a código C que luego compila con GCC. Es lo suficientemente 

compatible con COBOL-85 y COBOL-2002 como para que se hayan llegado a 

portar aplicaciones de mainframes a Linux con éxito, lo de generar código

C lo hace internamente y ni siquiera guarda los fuentes generados, si no

se desea, la traducción y compilación las hace en un solo paso en 

forma automàtica.

Como prueba instala en un ordenador simple debian server con opencobol y 

que el programador comprube si su código es compilado correctamente y se 

ejecuta.

Obviamente si en algunos ordenadores ademàs de la aplicaciòn utilizan

aplicaciones de ofimática y son winusers extremos, puedes sin problemas 

instalar en ellos Ubuntu, actualmente te sugerirìa hardy, siempre para

estar seguros de la estabilidad, para que no extrañen su antiguo entorno.

Saludos.

---

### Post by NickCis on 2009-05-08
Primero, gracias Gmunioz por la ayuda.
Bueno, todavia no me trajeron una maquina para que empiece a probar. Voy a tener en cuenta de que el server use debian, por lo que me dijiste.
Ahora, estoy teniendo unos problemas con Open-Cobol, lo instale desde los repositorios pero cuando voy lo estoy probando (como dice esta pagina [http://www.opencobol.org/modules/bwiki/index.php?cmd=read&page=UserManual%2F1#content_1_1](http://www.opencobol.org/modules/bwiki/index.php?cmd=read&page=UserManual%2F1#content_1_1) ), haciendo un hello world, me devuelve errores en la compilacion.
Me dice esto: 
```
newpc@ubuntu-newpc:~/Documentos/cobol$ cobc -x hola.cob
/usr/bin/ld: cannot find -lncurses
collect2: ld devolvió el estado de salida 1

```
Alguna idea?.
Despues, actualmente los programas se alojan en el server (montado en todas las Pc como un disco externo Z:), y lo ejecutan por red. Usando Open-Cobol, podria hacer lo mismo?.

Estube probando el RM Cobol, alguien lo conoce?, saben como podria hacer para que los clientes ejecuten los programas del servidor?. El problema es que el Rm Cobol, compila los programas, pero siempre los tenes que ejecutar con un programa "runcobol".

Me gustaria presentar las dos opciones, para que el programador decida, cual segun su criterio es la mejor. Yo veo mejor Open-Cobol, por ser un proyecto abierto, pero bueno...

Saludos.

---

### Post by Hei Ku on 2009-05-08
Instalaste el paquete build-essential? ncurses es uno de los paquetes basicos para compilar.

---

### Post by NickCis on 2009-05-09
Si ya los tenia instalados, busque en los paquetes de ubuntu "ncurses" y despues de instalar libncurses5-dev libcunit1-ncurses y libcunit1-ncurses-dev el problema se soluciono, creo que la unica necesaria es libncurses5-dev (fue la ultima que instale y la que me soluciono el problema, libncurses5 ya la tenia instalada pero la vercion de desarrollo no)

Saludos y muchas gracias :P

---

### Post by guillermolisi on 2009-05-09
> **NickCis said:**
> Primero, gracias Gmunioz por la ayuda.
Bueno, todavia no me trajeron una maquina para que empiece a probar. Voy a tener en cuenta de que el server use debian, por lo que me dijiste.
Ahora, estoy teniendo unos problemas con Open-Cobol, lo instale desde los repositorios pero cuando voy lo estoy probando (como dice esta pagina [http://www.opencobol.org/modules/bwiki/index.php?cmd=read&page=UserManual%2F1#content_1_1]("http://www.opencobol.org/modules/bwiki/index.php?cmd=read&page=UserManual%2F1#content_1_1") ), haciendo un hello world, me devuelve errores en la compilacion.
Me dice esto: 
```
newpc@ubuntu-newpc:~/Documentos/cobol$ cobc -x hola.cob
/usr/bin/ld: cannot find -lncurses
collect2: ld devolvió el estado de salida 1

```Alguna idea?.
Despues, actualmente los programas se alojan en el server (montado en todas las Pc como un disco externo Z:), y lo ejecutan por red. Usando Open-Cobol, podria hacer lo mismo?.

Estube probando el RM Cobol, alguien lo conoce?, saben como podria hacer para que los clientes ejecuten los programas del servidor?. El problema es que el Rm Cobol, compila los programas, pero siempre los tenes que ejecutar con un programa "runcobol".

Me gustaria presentar las dos opciones, para que el programador decida, cual segun su criterio es la mejor. Yo veo mejor Open-Cobol, por ser un proyecto abierto, pero bueno...

Saludos.
Use durante casi 10 años RM-Cobol para aplicaciones comerciales. En esa epoca y existiendo un MS-Cobol (que no era ni mas ni menos que una licencia que Ryan McFarland le otrogo a Microsoft) desarrolle sistemas para plataformas *nix (existia un Unix para pequeñas maquinas Intel x286 que Microsoft habia licencia con SCO) que era un RM con algunas funciones que MS le habia incorporado para diferenciar su producto.

Para lo que habia en esa epoca (RPG, Fortran, Basic, etc.) Cobol era lo aconsejable para aplicaciones comerciales.

Ambos, RM y MS-Cobol corren los programas con un runtime porque se compilan pero no se link editan (que es cuando generas verdaderamente un ejecutable con todas las funciones para que dialogue con el kernel para evitar un shell - interprete de comandos y obtener servicios de bajo nivel para utilizar recursos de maquina, como abrir un archivo por ejemplo).

Con el tiempo aparecio MicroFocus Cobol que tuvo mucha aceptacion porque introdujo varios cambios que relegaron a RM. Uno de ellos fue que podias compilar un programa escrito con RM-Cobol 85 y facilitabas la migracion de todo un sistema sin tocar codigo.
Otra fue que introdujo el concepto de "framework", entonces inexistente para Cobol.
Luego, no menor, permitia usar ventanas similando una aplicacion Windows (RM incorporo esto algun tiempo despues con su version 85 o posterior) y le agregaron funcinalidad para usar bases de datos (dejando de lado los archivos planos). En esa epoca Informix era the must en motores de RDBMS.

Si tuviera que volver a desarrollar en Cobol, Dios no lo permita :), me inclinaria por RM o Microfocus, hablando de sintaxis y funcionalidades. MS-Cobol murio hace mucho tiempo (o por lo menos es lo que me parece).

En la epoca que cuento mi experiencia, muchas versiones propietarias, como la de Digital o la de DataGeneral, contemplaban el standard RM Cobol 85. Imaginate la difusion que tenia en ese entonces para ser considerado de esa forma.

Todo esto para decirte que no solo hay que evaluar la herramienta de desarrollo en funcion a sus caracteristicas sino tambien a su grado de adopcion en el mercado. Si elegis algo que no tuvo aceptacion masiva, cuando necesites contratar y/o incorporar gente al desarrollo estaras tan limitado que te vas a arrepentir de la decision tomada.

---

### Post by pablo.s on 2009-05-09
A ver si tienen personas tan tan grosas
como Guille en otros foros...

---

### Post by NickCis on 2009-05-10
si,,, mal,,, toda la explicacion me dio :P.

La idea aca, no es desarrollar en Cobol, es pasar un sistema ya hecho y funcional que esta en cobol con server win y clientes win, a server linux y clientes linux.

El programador tiene el compilador de microfocus, y por ahora las unicas soluciones son opencobol y rm-cobol. Cual me sugieren usar?.

Saludos.

---

### Post by guillermolisi on 2009-05-10
> **NickCis said:**
> si,,, mal,,, toda la explicacion me dio :P.

La idea aca, no es desarrollar en Cobol, es pasar un sistema ya hecho y funcional que esta en cobol con server win y clientes win, a server linux y clientes linux.

El programador tiene el compilador de microfocus, y por ahora las unicas soluciones son opencobol y rm-cobol. Cual me sugieren usar?.

Saludos.
Bueno, considerando una parte de lo que mencione respecto de RM y Microfocus y viendo [este informe de features de OpenCobol]("http://www.opencobol.org/modules/bwiki/index.php?Features"), me inclinaria (sin un analisis muy profundo) por RM.

**Me parece que el que deberia analizar pros y cons del caso es el mismo programador** (el que decis tiene la licencia de Microfocus). El sabra, en funcion de los sistemas desarrollados, que compatibilidad es la mas adecuada (por ejemplo, OpenCobol no implemento aun Embedded SQL y esto podria ser determinante si trabajan con bases de datos relacionales).

Tal vez en un futuro no muy lejano OpenCobol este tan o mas completo que Microfocus y sea una alternativa absolutamente valida para todo caso de aplicacion.

---

### Post by NickCis on 2009-05-10
Muchas gracias por todo :P

Salu2

---

### Post by guillermolisi on 2009-05-10
> **NickCis said:**
> Muchas gracias por todo :P

Salu2
De nada, espero haber ayudado.

Conta que resulto de todo esto !!

---

### Post by evanrmurphy on 2009-05-11
COBOL es ese lenguaje prehistoríco, vdd? ;) Jaja, no te creas, espero que ya estén resolvidas tus dudas con esto. ¡Muchos saludos!

---

