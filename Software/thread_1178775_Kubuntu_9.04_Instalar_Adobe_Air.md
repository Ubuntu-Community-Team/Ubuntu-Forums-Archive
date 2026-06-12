---
title: "Kubuntu 9.04 Instalar Adobe Air"
date: 2009-06-04
forum: Software
---

### Post by lega on 2009-06-04
Estoy tratando de instalar Adobe Air en Kubuntu y me da un error, me dice que debo tener instalado gnome-keyring o kwallet (captura) sin embargo Kwallet está instalado y me sigue dando ese error, al estar en KDE supongo que gnome-keyring no es necesario instalarlo.

Los pasos que sigo para instalar Adobe Air son los mismos que hice para instalarlo en Gnome

```
    wget -c http://airdownload.adobe.com/air/lin/download/1.5/AdobeAIRInstaller.bin

El archivo bajado podés encontrarlo en Lugares->Carpeta Personal

Le damos permisos

    chmod +x AdobeAIRInstaller.bin

y luego instalamos

    sudo ./AdobeAIRInstaller.bin
```

Agradezco cualquier ayuda que me puedan dar.

---

### Post by clasificado on 2009-06-05
Queria ver que pasaba, y se instaló :P

Probá ejecutar el binario pero sin SUDO, que me anduvo bien

Tiene sentido, ya que el kwallet corre en el entorno del usuario

clasificado

PD: Así como se instaló me dijo que hay una versión mas nueva. Podés bajarte esa e instalarla directamente si querés

---

### Post by lega on 2009-06-05
Gracias funcionó perfecto! :)

---

### Post by pol666 on 2009-06-06
Hola, una duda al respecto. ¿Que hay hasta ahora hecho en adobe air?

---

### Post by staar on 2009-06-06
> **pol666 said:**
> Hola, una duda al respecto. ¿Que hay hasta ahora hecho en adobe air?

[http://airapps.pbworks.com/]("http://airapps.pbworks.com/")

[http://www.myairapplications.com/]("http://www.myairapplications.com/")

mucho, la única app que usé fue Snackr, muy bonita, casi todas son basadas en servicios web...

saludos

---

