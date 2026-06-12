---
title: "remote destop"
date: 2009-05-21
forum: Software
---

### Post by greynand on 2009-05-21
Hola me pueden ayudar quiero hacer remote destop con mi trabajo yno puedo por favor ayudame, soy un chica sin ayuda

---

### Post by Hei Ku on 2009-05-21
Por empezar necesitariamos saber que software de remote desktop usan en tu trabajo.

---

### Post by KaKuS on 2009-05-22
> **greynand said:**
> Hola me pueden ayudar quiero hacer remote destop con mi trabajo yno puedo por favor ayudame, soy un chica sin ayuda

Se pueden presentar varias combinaciones con los datos que nos diste :KS, pero para no dejarte sin nada te trato de dar una mano.

En todos los casos vas a necesitar que el equipo que queres usar desde lejos tenga una ip publica o que los paquetes estén ruteados desde la puerta de enlace o router a ese equipo. 

Caso 1, Servicio VNC o similar instalado. [linux(casa) a windows(oficina):
Solución A_ Desde el linux te vas al Menu "Aplicaciones->Internet->Cliente Terminal Server", seleccionas VNC, pones la IP publica del equipo a donde queres llegar y te conectas.


Solución B_ Seguro hay una versión open source, pero yo uso Real VNC y no tengo problemas, en [http://www.realvnc.com/cgi-bin/download.cgi](http://www.realvnc.com/cgi-bin/download.cgi) te bajas el instalador de la versión gratuita para linux y la instalas.
Desde el linux te vas al Menu "Aplicaciones->Internet->VNC Viewer", pones la IP publica del equipo a donde queres llegar y te conectas.

Caso 2, Servicio de escritorio remoto de Microsoft [linux(casa) a windows(oficina):
Desde el linux te vas al Menú "Aplicaciones->Internet->Cliente Terminal Server", seleccionas RPDv5, pones la IP publica del equipo a donde queres llegar y te conectas.

Caso 3, dos linux:
En el de la oficina te vas al Menú "Sistema.>Escritorio Remoto", le das a "Permitir a otros usuarios ver mi escritorio", destildas la opción "Debe confirmar cada acceso a este equipo", tildas "Requerir que el usuario ingrese una contraseña" y pones una contraseña (la que vas a usar para entrar desde tu casa). Después desde tu casa podes usar cualquiera de las dos soluciones del Caso 1.

Quizás no sean las soluciones más óptimas, soy nuevo en linux, pero quería aportar lo que sé.

Suertes! ):P

---

