---
title: "¿Alguien sabe cómo resolver esto?"
date: 2012-05-24
forum: Software
---

### Post by gsanchezs on 2012-05-24
Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de esto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

Gracias

---

### Post by gmunioz on 2012-05-24
Abre una terminal
Ejecuta en ella
gksu nautilus
Cargado Nautilus, pulsa control+H
Navega hasta:
/var/lib/apt/lists/
Borra todos los archivos que se encuentran
dentro de este directorio
Navega hasta:
/var/lib/apt/lists/partial/
Borra todos los archivos que se encuentran
dentro de este directorio
Cierra Nautilus
ejecuta en la terminal
sudo su
apt-get update
apt-get upgrade
apt-get clean

---

