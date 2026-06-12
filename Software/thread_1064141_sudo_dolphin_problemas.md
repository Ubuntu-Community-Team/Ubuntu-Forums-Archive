---
title: "sudo dolphin problemas"
date: 2009-02-08
forum: Software
---

### Post by tsueseres on 2009-02-08
cuando se abre en una terminal
sudo dolphin y luego se cierra, despues de eso al brir cualquier otra carpeta aparece problemas de permisos

este se puede resolver con este comando,
cd /home
sudo chown -R name:name name 

pero deja el problema principal de que volvera a pasar lo mismo si se vuelve a correr sudo dolphin

saben como corregirlo

---

### Post by Hei Ku on 2009-02-08
Para correr las aplicaciones kde como root te conviene el kdesudo, en vez del sudo.

Creo que correrlas con sudo trae problemas con el sycoca. (que no me acuerdo que era, pero te aparecen esos errores de permisos). Creo que para arreglarlo tenes que correr kbuildsycoca y te soluciona eso. Recuerdo que era un problema frecuente en los primeros Kubuntu.

---

### Post by tsueseres on 2009-02-08
> **Hei Ku said:**
> Para correr las aplicaciones kde como root te conviene el kdesudo, en vez del sudo.

Creo que correrlas con sudo trae problemas con el sycoca. (que no me acuerdo que era, pero te aparecen esos errores de permisos). Creo que para arreglarlo tenes que correr kbuildsycoca y te soluciona eso. Recuerdo que era un problema frecuente en los primeros Kubuntu.

ha ok gracias

---

