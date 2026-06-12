---
title: "Como instalar Medibuntu en los repositorios de Ubuntu 10.04."
date: 2011-04-07
forum: Software
---

### Post by Cacique1 on 2011-04-07
Hola. En estos días decidí desinstalar Ubuntu 10.04 (en dual-boot con Windows XP) y volverlo a instarlo para dejarlo solo para e-mail y tramites web, entre otros, y tambien para escuchar música o ver algun video mientras lo hago. Como antes no tenia Internet instale Medibuntu y sus derivados descargándolos desde la página web. Pero ahora que tengo Internet quería agregarlo a los repositorios. Estuve investigando en la Web y encontré 3 formas de hacerlo:
   
  1) Agregar el repositorio correspondiente desde una terminal:
  [COLOR=blue][FONT=&quot]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[/FONT][/COLOR]
  
Una vez agregados los repositorios, se instalan los codecs:
  **[FONT=&quot]Para la reproducción de DVD:[/FONT]**
  [COLOR=blue][FONT=&quot]sudo apt-get install libdvdcss2[/FONT][/COLOR]
**[FONT=&quot]El resto de codecs propietarios, todas las plataformas:[/FONT]**
  [COLOR=blue][FONT=&quot]sudo apt-get install non-free-codecs[/FONT][/COLOR]
**[FONT=&quot]Windows codecs para i386[/FONT]**
  [COLOR=blue][FONT=&quot]sudo apt-get install w32codecs[/FONT][/COLOR]
   
  2) Abrimos la terninal (Aplicaciones -> Accesorios -> Terminal) y damos dos pasos 
Primero agregamos el repositorio: 
**[FONT=Georgia]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list [/FONT]**
Nos pedirá la clave de usuario, que la necesitará para continuar. 
  
Y después añadimos la clave GPG: 
**[FONT=Georgia]sudo aptitude -q update && sudo aptitude -y --allow-untrusted install medibuntu-keyring && sudo aptitude update[/FONT]**
  
  3) Para agregar el repositorio hacemos clic en el menú **Sistema > Administración > Orígenes del software**.
  En la pestaña **Otro software** marcamos la primera línea para añadir también el repositorio de socios de Canonical en el que podemos encontrar Adobe Acrobat Reader o la máquina virtual de Java entre [esta lista de paquetes]("http://archive.canonical.com/dists/lucid/partner/binary-i386/Packages"). Esto no tiene nada que ver con el repositorio de Medibuntu pero aprovechamos que estamos en esta pantalla para hacerlo.
  Después hacemos clic sobre el botón **Añadir…** para agregar, esta vez sí, el repositorio de Medibuntu.
  A continuación debemos escribir la línea del repositorio que es la siguiente:
**deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free**
  Y hacemos clic en **Añadir origen**.
  Veremos el nuevo repositorio añadido y activado por lo que hacemos clic en **Cerrar**. Sin embargo, como cada vez que agreguemos un repositorio, tendremos actualizar la información de los programas disponibles pulsando el botón **Recargar**.
  Una vez terminada la actualización nos encontraremos con un mensaje de error. Éste nos informa que no se ha podido verificar la firma del repositorio. No es imprescindible pero sí muy útil obtener esa firma por lo que tras pulsar **Cerrar** vamos a solucionar este problema.
  Para solucionar el problema anterior de la firma hacemos clic en **Sistema > Administración > Gestor de paquetes Synaptic**.
  Abrimos el Gestor de paquetes Synaptic
  Buscamos **medibuntu** y hacemos doble clic sobre el paquete **medibuntu-keyring** para marcarlo.
  Inmediatamente veremos un aviso para informarnos que el paquete no está autenticado. Efectivamente, por eso queremos instalarlo. Así que pulsamos sobre el botón **Marcar** y desaparecerá el mensaje.
  A continuación hacemos clic sobre el botón **Aplicar** para instalar el paquete.
  De nuevo podemos leer que vamos a instalar un paquete no autenticado. Como estamos seguros de lo que estamos haciendo pulsamos el botón **Aplicar**.
  Una vez finalizada la instalación tenemos que actualizar la información de los paquetes. Por eso hacemos clic en el botón **Recargar**.
  Al terminar ya podemos cerrar la ventana del Gestor de paquetes Synaptic.
   
  Lo que quisiera saber es cual de las tres formas es la mejor y más segura manera de añadir Medibuntu a los repositorios. Desde ya, agradezco cualquier respuesta.

---

### Post by juancarlospaco on 2011-04-07
Estas haciendo lo mismo en las 3.
2 veces por Linea de comandos y 1 por Interface Grafica.

:)

---

### Post by Cacique1 on 2011-04-08
Estimado juancarlospaco, muchas gracias por tu respuesta. Lo que pasa es que soy novato en Ubuntu y quería estar seguro de configurar todo de forma correcta y segura. Hasta la próxima.:)

---

