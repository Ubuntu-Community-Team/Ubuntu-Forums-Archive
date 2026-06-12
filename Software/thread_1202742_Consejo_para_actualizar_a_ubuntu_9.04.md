---
title: "Consejo para actualizar a ubuntu 9.04?"
date: 2009-07-02
forum: Software
---

### Post by milovan1971 on 2009-07-02
Hola,
Tengo instalado ubuntu 8.10 en una laptop Dell latitude D800 (1.8ghz, 1gb Ram, 80gb HD, Nvidia GeForceGo 5200 32mb), anda todo perfecto [con algun trabajo extra para escaner e impresora, varios "toques" para dejarlo a mi gusto, etc.]. He leido opiniones variadas sobre el 9.04, sobre la velocidad (que anda mas lento en maquinas viejitas como la mia), etc. Ustedes que opinan? Me conviene actualizar? 
Pero si conviene, yo quiero actualizar a JJ 9.04, usando ext4. Lo que significa formatear la particion de ubuntu, e instalar de nuevo.... ahora: como hago para no perder todo los programas y settings que tengo en el 8.10? Si copio el /home completo que puedo recuperar, y como lo hago? (mails y favoritos ya los tengo en backup).
Hace un tiempo lei por algun lado que hay un programa que te lista todo lo que tenes, y te ayuda con el backup... pero ahora no puedo encontrar nada parecido.
Agradezco cualquier ayuda ;),
salute
C.

---

### Post by staar on 2009-07-02
tengo una desktop de similares características, y la verdad que la diferencia de velocidad con respecto a intrepid es notable, es mucho más rápido jaunty, si no tenés problemas con ningún dispositivo (los problemas de jaunty son, en la mayoría de los casos, culpa de los drivers de video intel o ati, con nvidia no hay dramas), te conviene actualizar...

podés hacer backup de tu home y usarlo en la nueva instalación (por las dudas, usa el mismo nombre de usuario) casi sin dramas, cualquier problema, con borrar la carpeta de configuración del programa que de problemas es suficiente...

los programas los vas a tener que instalar de nuevo, pero podes crear una lista con los paquetes instalados desde Synaptic, en Archivo > Guardar selecciones, y despues, en jaunty, hacer que lea el archivo generado con Leer selecciones...

saludos

---

### Post by milovan1971 on 2009-07-02
Gracias Staar!
Buenisimo lo de la lista de paquetes desde synaptic! No me habia dado cuenta de eso...
un detalle, hay que tildar "guardar el estado completo, no solo los cambios" en el menu de guardar, sino queda un archivo vacio. Ahora me doy cuenta de la cantidad enorme de paquetes que no se para que sirven... y hay mucha redundancia me parece. Creo que usare la lista pero bien depurada, para no joder la instalacion del Jaunty.
gracias de nuevo... seguro despues vuelvo con algun problema nuevo :P.
saludos,
milo

---

### Post by EnriqueK on 2009-07-02
Trabajo inútil eso de depurar la lista, lo único que tenés que hacer es habilitar los repositorios equivalentes para la nueva instalación , no debes tener temor a que se te estropee la instalación de Jaunty, ya que el gestor de paquetes Sunaptic ( APT) se encargará del control de dependencias .
Si te fijás en la lista vas a ver que solo figuran los nombres de los paquetes y no así la versión de los mismos , esto es lo que va a permitir que la nuea instalación use esa información para instalar los paquetes pero para la nueva versión y los que ya estén instalados , no los volverá a instalar, reduciendo notablemente la lista real a instalar, , por ejemplo en mi caso en la lista me figuran unos 2500 paquetes, pero los que realmente va a instalar son unos 1500 .
Usando este método instalé Intrepid 64 birs basado en una lista de paquetes de Intrepid 32 birs que me faciñitó un amigo.
Solo queda indicar que la clave está en usar repositorios equivalentes y aquellos progranas que fueron instalados por medio de gdebi o por compilación, vas a tener que instalarlos de la misma manera, ya que este método "solo " instala paquetes desde los repositorios.

---

### Post by milovan1971 on 2009-07-02
Excelente dato EnriqueK! Asi no voy a perder mucho tiempo mirando (y descrifrando) la lista interminable!!
saludazo (gran saludo en cordobes)!!

---

### Post by EnriqueK on 2009-07-02
Respecto a tu** /home**, lo primero que te recomiendo es respaldar de forma tradicional todos tus docm,entos que tengas allí en por ej DVDs y los vas borranfo en la medida que avances, al final que va a quedar tu carpeta de usuario con solamente configuraciones, por lo que no va a pesar gran cosa, seguidamente ejecuta los siguientes comandos
[B]cd /tmp
sudo tar cvf copia.tar /home/$USER[/B]
El resultado va a ser que se ha creado el archivo copia.tar dentro de la carpeta temporal /tmp , seguidamente la copias preferentemente a un pendrive  y seguifamente provedes a instalar Jaynty , una vez instalado, copias el archivo respaldado (copia.tar) al directorio temporl /tmp ,sales del entorno gráfico y ejecuta los siguientes comados

[B]sudo rm -Rf /home/$USER
cd /tmp
sudo sudo tar -xvf copia.tar --directory /[/B]
Lo que va a pasar es que primero va a borrar la carpeta de usuario creada en la nueva instalación y luego en ese mismo lugar se pondrá la carpeta de usuario de respaldo, pero antes de hacer esto **asegurate muy bien de tener en /tmp el archivo copia.tar**

---

