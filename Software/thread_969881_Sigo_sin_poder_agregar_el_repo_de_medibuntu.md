---
title: "Sigo sin poder agregar el repo de medibuntu"
date: 2008-11-03
forum: Software
---

### Post by victor_nesta on 2008-11-03
lo primero que hago:
 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Lo segundo:
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Y este es el error:
W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

Pense que era por el relase, pero no veo que ayan tenido este problema

Desde ya muchas gracias.

---

