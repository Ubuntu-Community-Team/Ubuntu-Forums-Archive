---
title: "Rollback Drivers gráficos"
date: 2009-05-22
forum: Software
---

### Post by Killer Jacker on 2009-05-22
Hola estimados Ubunteros...
mi consulta, como lo indica el título es como puedo hacer un rollback de la instalación de los drivers de gráficos en Ubuntu 9.04, es decir, dejarlos tal cual vienen con la instalación.

He leído que los drivers que tiene Ubuntu por defecto andan mejor que los propietarios de ATI (estoy que me cambio a Nvidia ya...:mad:). Aún así probe instalar los driver ATI a ver si conseguía mejor aceleración... Después de instalarlos, no me partía el PC... se quedaba con puras rayas en la pantalla. Luego, por consola de recuperación, desinstale esos drivers (ATI) e instalé denuevo los fglrx que se encuentran en repositorios. Partió bien, pero no me activaba ni el más mínimo efecto de escritorio y me andaba medio lento. Procedí a desinstalar e instalar denuevo y BOING!!!! no partió... hahaha... nuevamente quedó con puras rayas raras al inicio. Entonces, quiero volver al punto de partida!!! ;)

Desde ya, les agradezco su ayuda...

a todo esto:

[LIST=1]
[*]mi tarjeta es ATI 9600 SE
[*]Cómo puedo activar y administrar todos los efectos de escritorio que están disponibles con Compiz/Beryl??? Esos que se queman las ventanas, el cubo, etc. etc...??
[/LIST]

---

### Post by Patriciologico on 2009-05-22
> **Killer Jacker said:**
> [LIST=1][*]Cómo puedo activar y administrar todos los efectos de escritorio que están disponibles con Compiz/Beryl??? Esos que se queman las ventanas, el cubo, etc. etc...??
[/LIST]

Instala Administrador de Opciones CompizConfig

```
sudo aptitude install compizconfig-settings-manager
```

Saludos!

---

### Post by kamus on 2009-05-22
> **Killer Jacker said:**
> Hola estimados Ubunteros...
mi consulta, como lo indica el título es como puedo hacer un rollback de la instalación de los drivers de gráficos en Ubuntu 9.04, es decir, dejarlos tal cual vienen con la instalación.

He leído que los drivers que tiene Ubuntu por defecto andan mejor que los propietarios de ATI (estoy que me cambio a Nvidia ya...:mad:). Aún así probe instalar los driver ATI a ver si conseguía mejor aceleración... Después de instalarlos, no me partía el PC... se quedaba con puras rayas en la pantalla. Luego, por consola de recuperación, desinstale esos drivers (ATI) e instalé denuevo los fglrx que se encuentran en repositorios. Partió bien, pero no me activaba ni el más mínimo efecto de escritorio y me andaba medio lento. Procedí a desinstalar e instalar denuevo y BOING!!!! no partió... hahaha... nuevamente quedó con puras rayas raras al inicio. Entonces, quiero volver al punto de partida!!! ;)

Desde ya, les agradezco su ayuda...

a todo esto:

[LIST=1]
[*]mi tarjeta es ATI 9600 SE
[*]Cómo puedo activar y administrar todos los efectos de escritorio que están disponibles con Compiz/Beryl??? Esos que se queman las ventanas, el cubo, etc. etc...??
[/LIST]

Te recomiendo usar la herramienta controladores de hardware ( menu sistema --> administracion -> Controlares de hardware) y habilitar el controlador correspondiente a tu tarjeta ATI. Por otro lado yo lo pensaria bien en comprar una tarjeta nvidia pues debo decir que el controlador en las ultimas versiones se ha puesto un poco inestable, al menos en mi Geforce 6xxx Go tuve algunos problemas con compiz y el rendimiento claramente era inferior a las versiones anteriores. 

> 
sudo aptitude install ccsm

No esta ese paquete en los repo de jaunty : (, no se si sera lo mismo que compizconfig-settings-manager (apt-get install compizconfig-settings-manager)

Saludos

---

### Post by Patriciologico on 2009-05-22
> **kamus said:**
>  No esta ese paquete en los repo de jaunty : (, no se si sera lo mismo que compizconfig-settings-manager (apt-get install compizconfig-settings-manager)

Saludos

Eso, eso, eso.

Saludos!

---

### Post by Killer Jacker on 2009-05-25
> **kamus said:**
> Te recomiendo usar la herramienta controladores de hardware ( menu sistema --> administracion -> Controlares de hardware) y habilitar el controlador correspondiente a tu tarjeta ATI. Por otro lado yo lo pensaria bien en comprar una tarjeta nvidia pues debo decir que el controlador en las ultimas versiones se ha puesto un poco inestable, al menos en mi Geforce 6xxx Go tuve algunos problemas con compiz y el rendimiento claramente era inferior a las versiones anteriores. 


No esta ese paquete en los repo de jaunty : (, no se si sera lo mismo que compizconfig-settings-manager (apt-get install compizconfig-settings-manager)

Saludos

Antes que todo, muchas gracias por su ayuda.

Ahora, el problema es que el sistema no me parte, por lo que no creo que pueda usar la pantalla de Administración de Hardware. No sé si esto se puede hacer de alguna forma por consola... gracias.

---

### Post by AlexDDR on 2009-05-27
Claro que si, de hecho puedes meter el live cd y desde ahi editar el archivo

/etc/X11/xorg.conf

y especificar el driver manualmente

debes buscar la seccion "Device" y poner driver "ati" como en el ejemplo

no es necesario que pongas las otras opciones

Section "Device"
    Identifier "Configured Video Device"
    Driver     "ati"
EndSection


Ademas puede que haya un back up del xorg de antes que se instalar el privativo, seria recomendable que dtrabajaras sobre ese, ademas comparalo con el que se activa en el live CD, para ver que cambios hizo el instalador del driver privativo

OJO: desde le live cd veras tu particion como otro disco, y el directorio raiz de  live cd son dos cosas diferentes.


ademas ve este post que hice

[http://ubuntuforums.org/showthread.php?t=1166846](http://ubuntuforums.org/showthread.php?t=1166846)


al final sale como modificar el xorg cuando no hay entorno grafico y sin live cd, que es mas lento , ya que dee cargar y todas esas cosas

lo ultimo que te quedaria por hacer es desinstalar el driver fglrx desde synaptic


espero  resulte


saludos

---

