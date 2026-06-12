---
title: "Problema en instalación de Ubuntu 9.10"
date: 2010-01-27
forum: Software
---

### Post by agmm on 2010-01-27
Hola a todos. Soy completamente nuevo en linux y de la mano de una implementación de servidor de archivos que se hizo en la empresa donde trabajo conocí Ubuntu. A partir de allí hice algunas averiguaciones que confirmaron mi interés en instalarlo en mi casa. Entré a la página y descargué el live cd, bajé la imagen a un CD y tal y como decían las instrucciones, hice un reboot. El disco nunca arrancó. 
Primero pensé que podía ser un problema del orden de booteo, pero no lo era. Intenté ejecutando manualmente desde Windows el disco de instalación de Ubuntu y allí se abre un programita que dice facilitar la instalación. La opción 1 es simplemente bootear de nuevo. Naturalmente no funciona. La segunda opción es un ayudante que comienza a instalar algo hasta que el proceso se corta porque el instalador no puede copiar un file por problemas de permisos(??). 
El usuario en Windows es obviamente administrador y tiene todos los permisos que Windows le da al administrador del equipo. 
A continuación pego el extracto del log del instalador de Ubuntu donde se ve la causa por la que se detiene.

01-26 23:02 DEBUG  TaskList: ## Finished create_uninstaller
01-26 23:02 DEBUG  TaskList: ## Running copy_installation_files...
01-26 23:02 DEBUG  WindowsBackend: Copying D:\DOCUME~1\ALEJAN~1\CONFIG~1\Temp\pyl12.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
01-26 23:02 DEBUG  WindowsBackend: Copying D:\DOCUME~1\ALEJAN~1\CONFIG~1\Temp\pyl12.tmp\winboot -> D:\ubuntu\winboot
01-26 23:02 DEBUG  WindowsBackend: Copying D:\DOCUME~1\ALEJAN~1\CONFIG~1\Temp\pyl12.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
01-26 23:02 DEBUG  TaskList: ## Finished copy_installation_files
01-26 23:02 DEBUG  TaskList: ## Running use_cd...
01-26 23:02 DEBUG  TaskList: New task copy_file
01-26 23:02 DEBUG  TaskList: ### Running copy_file...
01-26 23:04 DEBUG  TaskList: ### Finished copy_file
01-26 23:04 ERROR  TaskList: [Errno 13] Permission denied Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-26 23:04 DEBUG  TaskList: # Cancelling tasklist
01-26 23:04 DEBUG  TaskList: New task check_iso
01-26 23:04 ERROR  root: [Errno 13] Permission denied Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied

¿Alguna sugerencia?

Desde ya agradecido.

---

### Post by juancarlospaco on 2010-01-28
No, instalalo Fuera de Windows, booteando con el CD.

Si no bootea usa las opciones de** F6** en el menu de booteo, 
todas MENOS las 2 que dicen "solo software libre" y "modo experto", esas no.

salu2

---

### Post by agmm on 2010-01-28
Las opciones de booteo en mi placa se acceden con la tecla "del" y el orden de booteo es el correcto. Con F9 puedo elegir el dispositivo desde donde bootear. También lo he intentado pero siempre termina apareciendo la ventana donde me da para seleccionar cual de los 2 Windows quiero arrancar. 
no tengo idea a qué te referís con el menú que mencionás y, aunque probé, nada para al apretar F2 durante el booteo. 
Si hay algo más que pueda hacer agradeceré lo que puedas decirme.
Saludos.

Por si sirve tengo una placa Assus P5LMX con un pentium IV de 3GHz y dos discos de 250, cada uno con un windows (esto porque me cansé de que colapsara y tener que reinstalarlo). Tengo sólo 1G de ram.

---

### Post by agmm on 2010-01-28
Quise decir F6 en el booteo, no F2. Igual con ninguna tecla de función hace nada.

---

### Post by agmm on 2010-01-29
El problema era la grabación de la imagen con Nero. Usé lo recomendado en la documentación y listo.

---

