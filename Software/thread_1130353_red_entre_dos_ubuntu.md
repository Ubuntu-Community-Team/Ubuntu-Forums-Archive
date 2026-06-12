---
title: "red entre dos ubuntu"
date: 2009-04-19
forum: Software
---

### Post by marcelok1985 on 2009-04-19
Que tal, tengo dos maquinas con ubuntu conectadas mediante un router y este router a un modem que les da internet a ambas maquinas. Una compu es de escritorio esta conectada al router mediante cable, la otra es una notebook y es por Wifi al router. Lo que necesito es pasar datos de la compu de escritorio a la notebook, como lo hago? Les comento q la conexion a internet se configuro automaticamente desde el setup del router linksys wrt54g2, poro que no ingrese ninguna direccion ip manualmente. muchas gracias y espero respuesta. clq dato que falte me avisan. gracias.

---

### Post by Hei Ku on 2009-04-19
podes conectarte por ssh usando la direccion IP, o si queres algo mas civilizado podes usar NFS para compartir el disco de las PCs.

Acá esta el tutorial para configurar NFS: [http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208)

---

### Post by guillermolisi on 2009-04-19
> **Hei Ku said:**
> podes conectarte por ssh usando la direccion IP, o si queres algo mas civilizado podes usar NFS para compartir el disco de las PCs.

Acá esta el tutorial para configurar NFS: [http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208)
Sin duda alguna, NFS es lo indicado para el caso.

Proba y despues comenta como te fue.

---

### Post by ADICTOALMAXIMO on 2009-04-19
Buenisimo

y com se hace para conectar en red dos maquinas de escritorio  (ambas con placa de red)

saludos

---

### Post by guillermolisi on 2009-04-19
> **ADICTOALMAXIMO said:**
> Buenisimo

y com se hace para conectar en red dos maquinas de escritorio  (ambas con placa de red)

saludos
Las direcciones IP de ambas maquinas deben estar en la misma red.
Si usas la red 192.168.x.x, una PC podria tener, por ejemplo, 192.168.0.10 y la otra 192.168.0.11, ambas con mascara 255.255.255.0

Ahora, lo que faltaria que digas es si ambas tendran Ubuntu/Linux o no. Tambien si la conexion es directa o pasa por un switch/router

---

### Post by Hei Ku on 2009-04-19
Si usan wifi o cable no influye. Nos abstraemos de ese tema y nos concentramos en el sistema operativo que usan ambas PC. De acuerdo a eso, podes decidir si te conviene usar NFS o Samba o FTP.

---

