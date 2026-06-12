---
title: "Por que no se puede ejectuar apt-get más de una vez?"
date: 2009-10-23
forum: Software
---

### Post by pol666 on 2009-10-23
Bueno, cual es la razón técnica hoy en día por la cual no pueda realizar varias operaciones de instalación y desinstalación simultaneas? la verdad es que se ahorraria bastante tiempo.

---

### Post by aledruetta on 2009-10-23
> **pol666 said:**
> Bueno, cual es la razón técnica hoy en día por la cual no pueda realizar varias operaciones de instalación y desinstalación simultaneas? la verdad es que se ahorraria bastante tiempo.

Es cierto. Si uno ve cómo funciona el Ubuntu Software Center en Karmic, lo primero que nota es que puede instalar varias cosas al mismo tiempo. Incluso, mientras está instalando, seguir agregando descargas a la cola.

Por otro lado, si uno está instalando con USC, abre una terminal y hace "apt-get update", por ejemplo, apt corre como si nada, el USC se detiene, y después que terminó apt es posible retomar la instalación, o al menos la descarga, en el punto en que estaba.

---

### Post by pablo.s on 2009-10-23
> **pol666 said:**
> Bueno, cual es la razón técnica hoy en día por la cual no pueda realizar varias operaciones de instalación y desinstalación simultaneas?

Porque se bloquea la base de datos
de los paquetes y al instalar o desinstalar
se modifica. Por consiguiente no se
permite que mas de un proceso la
modifique a la vez y se asegura que la
operación no arruine la base de datos.

---

### Post by pol666 on 2009-10-23
Ah claro, es entendible. Por cierto, interesante lo del Software center, lo busqué en los repos de Kubuntu pero no lo encuentro.

EDIT: Synaptic si lo encontró, Kpackagekit no, ademas tiro error en la actualización, es malisimo.

---

### Post by juancarlospaco on 2009-10-23
Imaginate que se pudiera hacer eso, entons...

Vos estas instalando un programa con Software Center *(usa APT)*,
y yo estoy desde Internet conectado por SSH a la misma PC y 
**pongo remover el mismo programa al mismo tiempo.**

...que pensas que pasa  :)

---

### Post by pol666 on 2009-10-23
Bueno podría haber una opción para que no sea posible eso.. Igualmente ubuntu-software-center no funciona en kubuntu, sale "Sorry, Ubuntu software center closed unexpectedly

---

