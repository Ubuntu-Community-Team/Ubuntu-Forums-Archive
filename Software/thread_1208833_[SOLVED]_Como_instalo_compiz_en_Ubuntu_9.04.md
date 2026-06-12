---
title: "[SOLVED] Como instalo compiz en Ubuntu 9.04?"
date: 2009-07-09
forum: Software
---

### Post by matias_tati on 2009-07-09
Buscando en google encontre como hacerlo pero al ejecutar desde el terminal me aparece esto:

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

No lo puedo hacer desde Synaptic tampoco.

Gracias

---

### Post by staar on 2009-07-09
andá a Orígenes de software y cambiá el servidor, de 'Servidor para Argentina' al internacional, después recarga los repositorios (sudo aptitude update)

saludos

---

### Post by matias_tati on 2009-07-09
Muchisimas muchisimas gracias funciono de 10. Saludos.
Una ultima consulta cuando entro a sistema/preferencias/administrador de opciones compizconfig
tildo el efecto del avioncito pero despues cuando minimizo las ventanas no veo el efecto. Que estoy haciendo mal?

---

### Post by rubioo on 2009-07-09
Qué efecto activaste?
 Porque si querés que se haga un avioncito para que se minimice tenés
 que ir a Animaciones > Minimizar Animación y tildar la opción Aeroplano


           Saludos

---

### Post by matias_tati on 2009-07-10
Hice eso pero cuando minimizo no me aparece el avioncito. Hay que configurar algo mas?
[IMG]http://img196.imageshack.us/img196/8789/pantallazodti.png[/IMG]

---

### Post by matias_tati on 2009-07-10
Todo solucionado gracias solo me faltaria saber como cambiar las imagenes de arriba y abajo del cubo. Saludos y gracias de nuevo.

---

### Post by rubioo on 2009-07-10
Para cambiar las tapas del cubo, tenés que:

 Abrir el CCSM, ir a Cubo de Escritorio > Apariencia y ahí en la parte de
 Cube Caps haces clic en nuevo y agregas las 2 imágenes :)

---

