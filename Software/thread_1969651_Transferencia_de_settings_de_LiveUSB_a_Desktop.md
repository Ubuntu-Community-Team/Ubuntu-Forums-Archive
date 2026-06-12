---
title: "Transferencia de settings de LiveUSB a Desktop"
date: 2012-04-30
forum: Software
---

### Post by BIackHero on 2012-04-30
Hay alguna forma de transferir los settings y programas de la data persistente de un Live USB a una instalacion nueva en mi PC? Me ahorraria tener que hacerlo todo de nuevo manualmente.

---

### Post by asterix77 on 2012-04-30
Bueno a mi por ejemplo cada vez que actualizo a una nueva versión de ubuntu, y para no tener que configurar todo de nuevo, tengo el /home/ en una partición aparte. Así es que al instalar la nueva versión, solo instalo el directorio raiz (/) que está en otra partición con la opción de formatearla con algún sistema de ficheros (en mi caso ext4), y monto el home (de la instalación), en el home de mi disco duro (ojo pero sin formatear o perderás tus datos).

De esta forma me queda la configuración tal cual la tenía. Eso si, debes crear el mismo user y password en la instalación nueva.

De acuerdo a tu consulta, creo que deberías copiar la carpeta /home/ de tu live usb, instalar ubuntu al disco duro y copiar el home del live al home creado.

Ahora si haz instalado programas, puedes obtener una lista de los programas instalados para luego restituirlos. Con el siguiente comando obtienes lo instalado.

#sudo dpkg --get-selections | grep -v deinstall

Inclusive puedes dirigir la salida a un texto de la siguiente forma:

#sudo dpkg --get-selections | grep -v deinstall  > respaldo.txt

Para luego en la nueva instalación correr el siguiente comando (eso sí con acceso a internet)

#sudo dpkg -- set-selections < respaldo.txt
 
y de esta forma tendrás de nuevo tus aplicaciones, tal cual las tenías configuradas antes.

Espero que te sirva

Saludos

---

