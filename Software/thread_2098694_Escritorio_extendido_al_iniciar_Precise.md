---
title: "Escritorio extendido al iniciar Precise"
date: 2012-12-27
forum: Software
---

### Post by asterix77 on 2012-12-27
Tengo mi pc conectado vía VGA a un tv. Cada vez que arranca ubuntu me aparece el escritorio extendido, y para dejar solo el monitor de mi pc habilitado debo ingresar a  la configuración de Nvidia-setting y cambiarlo manualmente.

¿alguien sabe como dejar por defecto desactivado el escritorio extendido al arranque del sistema, y activarlo solo cuando se necesite?.

Saludos

---

### Post by guillermolisi on 2012-12-27
En una consola/terminal, ingresa ```
sudo nvidia-settings
``` haces los ajustes que necesites y salvas la configuracion que deberia quedarte permanente de esta forma.

---

### Post by asterix77 on 2012-12-28
Gracias Guillermo, tienes razón, no se me había ocurrido hacerlo con privilegios de root, me ha funcionado super bien. Un problema menos....

Saludos

---

