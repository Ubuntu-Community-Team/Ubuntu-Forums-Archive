---
title: "Algunas dudas de quien instalo ayer Ubuntu 9.04"
date: 2009-07-08
forum: Software
---

### Post by matias_tati on 2009-07-08
Hola soy nuevo aca hace un par de dias instale ubuntu 9.04. Y tengo un par de dudas al respecto. La primera: Como visualizo correctamente videos en you tube con Mozilla Fire Fox lo hago perfectamente pero el control de volumen no sirve o sea lo bajo lo subo y no pasa nada, y con Opera directamente no los puedo ver. La segunda es que cada vez que inicio Ubuntu debo cambiar la configuracion de pantalla yo utilizo 1440x900 y lo configuro asi pero cada vez que inicio debo volverla a cambiar, mi placa de video es Geforce 8400 series. Y la ultima es como hago para tener la vista de esos maravillosos escritorios tipo cubo que veo en you tube la verdad es que soy un novato asi que me vendria bien una explicacion hecha para gente nueva.
Muchas gracias a quienes me puedan contestar estas inquietudes pero la verdad es que tengo muchas ganas de aprender a usar este SO de la mejor forma posible para poder recomendarlo tmbn. GRACIAS!!!

---

### Post by guillermolisi on 2009-07-08
> **matias_tati said:**
> Hola soy nuevo aca hace un par de dias instale ubuntu 9.04. Y tengo un par de dudas al respecto. La primera: Como visualizo correctamente videos en you tube con Mozilla Fire Fox lo hago perfectamente pero el control de volumen no sirve o sea lo bajo lo subo y no pasa nada, y con Opera directamente no los puedo ver. La segunda es que cada vez que inicio Ubuntu debo cambiar la configuracion de pantalla yo utilizo 1440x900 y lo configuro asi pero cada vez que inicio debo volverla a cambiar, mi placa de video es Geforce 8400 series. Y la ultima es como hago para tener la vista de esos maravillosos escritorios tipo cubo que veo en you tube la verdad es que soy un novato asi que me vendria bien una explicacion hecha para tarados.
Muchas gracias a quienes me puedan contestar estas inquietudes quizas sean estupideces pero la verdad es que tengo muchas ganas de aprender a usar este SO de la mejor forma posible para poder recomendarlo tmbn. GRACIAS!!!
Matias

Por cuestiones de orden en el tratamiento de los temas en el foro, te pido que abras un hilo/thread especifico por cada tema que necesites consultar.

De esta forma tambien facilitas las respuestas ya que recibiras algunas que solo se refieran a alguno de los temas y en definitiva el hilo se convertira en una "bolsa de gatos" tematica.

Gracias

---

### Post by Hei Ku on 2009-07-08
Instalaste el plugin de Flash para Opera?

El cubo es un plugin (complemento) de Compiz. Tenes instalados los drivers 3d de tu placa? Podes activar los efectos de escritorio? A partir de ahí, instalando un par de cosas, activar el cubo es muy facil.

PD: Por favor, cuidá el vocabulario.

---

### Post by Hei Ku on 2009-07-08
Instalaste el plugin de Flash para Opera?

El cubo es un plugin (complemento) de Compiz. Tenes instalados los drivers 3d de tu placa? Podes activar los efectos de escritorio? A partir de ahí, instalando un par de cosas, activar el cubo es muy facil.

---

### Post by staar on 2009-07-08
- el plugin de flash para linux es malo (en realidad todo flash es malo), pero si necesitás cambiarle el volumen solo a lo que estés reproduciendo en flash ( podés usar el applet del panel, si no te importa cambiar el volumen de todo) podés usar el PulseAudio Volume Control, buscalo por Synaptic con el nombre pavucontrol e instalalo, después lo encontrás en Aplicaciones > Sonido, este te deja cambiar el volumen de cada aplicación por separado...

- para el tema de la resolución de pantalla, pasate por acá [http://ubuntuforums.org/showthread.php?t=1183319]("http://ubuntuforums.org/showthread.php?t=1183319") (primero instalá los drivers privativos desde Sistema > Administración > Controladores de hardware)

- para compiz, buscá en Synaptic el paquete ccsm e instalalo, después lo encontrás en Sistema > Preferencias > Administrador de Opciones de CompizConfig, con este vás a poder configurar todos los plugins de compiz, el cubo, las woobly windows, y todas esas giladas...

saludos

---

### Post by matias_tati on 2009-07-09
Hola primero bueno no quiero innundar de dudas creo que son cosas pequeñas las que estoy pidiendo y no creo que abrir un tema por cada cosa hubiese sido lo apropiado, no es mi intencion acerle mal a nadie. Me sorprendio lo de cuidar el vocabulario soy Argentino je je!!!
Y mira trate de instalar el compiz buscando con googgle y no lo puedo hacer me aparece esto!!! Desde Synaptic tmbn lo mismo. Los drivers los tengo correctamente instalados.

matias@matias:~$ ccsm
El programa «ccsm» no está instalado actualmente.  Puede instalarlo escribiendo:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: orden no encontrada
matias@matias:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for matias: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  python-compizconfig
Se instalarán los siguientes paquetes NUEVOS:
  compizconfig-settings-manager python-compizconfig
0 actualizados, 2 se instalarán, 0 para eliminar y 1 no actualizados.
Necesito descargar 676kB de archivos.
Se utilizarán 4329kB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
AVISO: ¡No se han podido autenticar los siguientes paquetes!
  python-compizconfig compizconfig-settings-manager
¿Instalar estos paquetes sin verificación [s/N]? s
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/universe python-compizconfig 0.8.2-0ubuntu1
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/universe compizconfig-settings-manager 0.8.2-0ubuntu1
  404 Not Found
Imposible obtener [http://ubuntu.patan.com.ar/ubuntu/pool/universe/c/compizconfig-python/python-compizconfig_0.8.2-0ubuntu1_i386.deb](http://ubuntu.patan.com.ar/ubuntu/pool/universe/c/compizconfig-python/python-compizconfig_0.8.2-0ubuntu1_i386.deb)  404 Not Found
Imposible obtener [http://ubuntu.patan.com.ar/ubuntu/pool/universe/c/compizconfig-settings-manager/compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb](http://ubuntu.patan.com.ar/ubuntu/pool/universe/c/compizconfig-settings-manager/compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb)  404 Not Found
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar
apt-get update o deba intentarlo de nuevo con --fix-missing?
matias@matias:~$ 

Gracias a todos.

---

### Post by guillermolisi on 2009-07-09
Matias

No importa si son cosas pequeñas o no y tampoco importa si sos argentino o de otra nacionalidad.

Los foros de Ubuntu son Internacionales y tienen sus reglas que valen para cualquiera que participe de estos foros, sea de donde sea.

Una de ellas es escribir lo mas neutro posible asi los foristas de otros paises de lengua hispana tambien pueden entender que se dice.

La otra es abrir un thread, previa consulta en el foro por si el tema ya se toco y fue resuelto (usando la funcion Searh this forum, por ejemplo) por cada tema que se quiera exponer (ya expuse sinteticamente algunas razones de porque debe hacerse asi).

Las reglas figuran como sticky thread en la primer pagina del foro argentino y deben ser leidas, comprendidas, aceptadas para participar y observadas por todos y cada uno de nosotros cada vez que se hace un comentario.

Que haya flexibilidad no significa transgredirlas sistematica y permanentemente.

Los moderadores son quienes indican cuando se ha pasado de la raya o esta actuando indebidamente en funcion de estas reglas vigentes y deben rendir cuentas a los administradores del foro (que NO son Argentinos) cuando suceden cosas poco felices.

Espero haber sido mas claro ahora.

---

