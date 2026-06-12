---
title: "Preguntas sobre ecryptfs"
date: 2008-10-31
forum: Software
---

### Post by Marcos on 2008-10-31
¿Cómo puedo renombrar la carpeta /Private? Digo, ¿lo hago bajo el mismo método que cualquier carpeta o hay que seguir ciertos pasos para no arruinar la encriptación?

---

### Post by Sylchat on 2008-11-07
No, no puedes renombrar la carpeta como cualquiera carpeta, porque es una carpeta montada.

Si usas la herramienta ecryptfs-setup-private (en /usr/bin/), puedes ver en las primeras líneas :
PRIVATE_DIR="Private"

i supongo que es la configuración para el nombre de la carpeta que montar.

Después, hay esta linea:
MOUNTPOINT="$HOME/$PRIVATE_DIR"

pero no he intentado cambiar el nombre...

:-D

---

