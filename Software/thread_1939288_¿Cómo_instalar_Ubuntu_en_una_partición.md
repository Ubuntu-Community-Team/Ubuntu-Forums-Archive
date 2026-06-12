---
title: "¿Cómo instalar Ubuntu en una partición?"
date: 2012-03-11
forum: Software
---

### Post by vegetasupersaiyajin on 2012-03-11
[FONT=Verdana]Hola, que tal.[/FONT]


  Quiero instalar Ubuntu, en un disco con Windows Vista.


  Tengo varias consultas al respecto ya que nose como hacerlo correctamente, por ejemplo, tengo entendido, que GRUB es el administrador de arranque de Ubuntu.


  [FONT=Calibri]1-     [/FONT]*¿Con que administrador tengo que iniciar el equipo, el Administrador de Arranque de Windows o GRUB, y porque?*
  *[FONT=Calibri]2-      [/FONT]¿Qué es BURG, es un una nueva versión de GRUB? ¿Debo utilizarla?*
  * *
  Buscando  en internet encontré que hay que hacer varias particiones para instalar Ubuntu.


  [FONT=Calibri]3-     [/FONT]*¿Con que herramienta hago las particiones, con Partición Magic, la herramienta que viene en  el CD de instalación de Ubuntu, con una herramienta de Windows? ¿Cuál me conviene más?*
  [FONT=Calibri]4-      [/FONT]Además, una partición la dejo para Windows, otra la hago para Ubuntu y otra para SWAP. *¿Qué es SWAP, cuantos GB le tengo que dedicar a dicha partición?*
   
  UbuntuUbuntu tiene como sistema de archivos EXT2, EXT3 y otros
  [FONT=Calibri]5-      [/FONT]*¿Cuál tengo que elegir, porque y  como hago para configurar la partición de Ubuntu para que sea EXT2 por ejemplo?*


  Quiero instalar este sistema operativo, pero tengo muchas dudas al respecto, espero puedan orientarme para hacerlo de la mejor forma posible.
   
  Muchas Gracias.

---

### Post by guillermolisi on 2012-03-11
> **vegetasupersaiyajin said:**
> [FONT=Verdana]Hola, que tal.[/FONT]


  Quiero instalar Ubuntu, en un disco con Windows Vista.


  Tengo varias consultas al respecto ya que nose como hacerlo correctamente, por ejemplo, tengo entendido, que GRUB es el administrador de arranque de Ubuntu.


  [FONT=Calibri]1-     [/FONT]*¿Con que administrador tengo que iniciar el equipo, el Administrador de Arranque de Windows o GRUB, y porque?*
  *[FONT=Calibri]2-      [/FONT]¿Qué es BURG, es un una nueva versión de GRUB? ¿Debo utilizarla?*
  * *
  Buscando  en internet encontré que hay que hacer varias particiones para instalar Ubuntu.


  [FONT=Calibri]3-     [/FONT]*¿Con que herramienta hago las particiones, con Partición Magic, la herramienta que viene en  el CD de instalación de Ubuntu, con una herramienta de Windows? ¿Cuál me conviene más?*
  [FONT=Calibri]4-      [/FONT]Además, una partición la dejo para Windows, otra la hago para Ubuntu y otra para SWAP. *¿Qué es SWAP, cuantos GB le tengo que dedicar a dicha partición?*
   
  UbuntuUbuntu tiene como sistema de archivos EXT2, EXT3 y otros
  [FONT=Calibri]5-      [/FONT]*¿Cuál tengo que elegir, porque y  como hago para configurar la partición de Ubuntu para que sea EXT2 por ejemplo?*


  Quiero instalar este sistema operativo, pero tengo muchas dudas al respecto, espero puedan orientarme para hacerlo de la mejor forma posible.
   
  Muchas Gracias.

Primero y principal, copia de resguardo de lo que tengas en WinVista.

Luego, defragmentar las particiones que tengas en WinVista.

La recomendacion es utilizar GRUB2 para que administre el inicio de WinVista y de Ubuntu.

Si por alguna razon reinstalas WinVista luego de haber instalado Ubuntu (o cualquier otro GNU/Linux), el proceso inevitablemente rompe GRUB2 y habra que recuperarlo con algun metodo o herramienta conocida (y con varios threads sobre el tema en este y demas foros de Ubuntu).

Hasta que obtengas mas experiencia con Linux, mi recomendacion es utilizar GRUB2. BURG lo podras usar mas adelante si te resulta practico.

Personalmente utilizaria el particionador de Ubuntu para trabajar el disco rigido. No usaria Partition Magic.

Las particiones que tenes que lograr para Ubuntu son:

Una para /
Una para /home
Una para Swap (es como el equivalente al archivo de intercambio o memoria virtual de Windows).

Para esta ultima, su dimension varia segun el uso que hagas de la maquina. Si no vas a correr maquinas virtuales, por ejemplo, podes darle el mismo tamaño que tenes de capacidad de meomoria RAM si esta ronda 1 Gb. Con mas de 1Gb podes marcar una particion Swap algo mas chica.

Para la particion dedicada a / (root), con marcarla de aproximadamente 10 Gb te tendria que sobrar. Esto dependera de la cantidad de programas que instales.
El resto del disco, descontando el espacio asignado a Swap, dedicaselo a /home.

Las particiones / y /home que sean del tipo ext4. Esto se determina cuando creas y formateas cada particion (Swap no permite elegir el tipo de sistema de archivos a usar)

---

### Post by vegetasupersaiyajin on 2012-03-12
> **guillermolisi said:**
> Primero y principal, copia de resguardo de lo que tengas en WinVista.

Luego, defragmentar las particiones que tengas en WinVista.

La recomendacion es utilizar GRUB2 para que administre el inicio de WinVista y de Ubuntu.

Si por alguna razon reinstalas WinVista luego de haber instalado Ubuntu (o cualquier otro GNU/Linux), el proceso inevitablemente rompe GRUB2 y habra que recuperarlo con algun metodo o herramienta conocida (y con varios threads sobre el tema en este y demas foros de Ubuntu).

Hasta que obtengas mas experiencia con Linux, mi recomendacion es utilizar GRUB2. BURG lo podras usar mas adelante si te resulta practico.

Personalmente utilizaria el particionador de Ubuntu para trabajar el disco rigido. No usaria Partition Magic.

Las particiones que tenes que lograr para Ubuntu son:

Una para /
Una para /home
Una para Swap (es como el equivalente al archivo de intercambio o memoria virtual de Windows).

Para esta ultima, su dimension varia segun el uso que hagas de la maquina. Si no vas a correr maquinas virtuales, por ejemplo, podes darle el mismo tamaño que tenes de capacidad de meomoria RAM si esta ronda 1 Gb. Con mas de 1Gb podes marcar una particion Swap algo mas chica.

Para la particion dedicada a / (root), con marcarla de aproximadamente 10 Gb te tendria que sobrar. Esto dependera de la cantidad de programas que instales.
El resto del disco, descontando el espacio asignado a Swap, dedicaselo a /home.

Las particiones / y /home que sean del tipo ext4. Esto se determina cuando creas y formateas cada particion (Swap no permite elegir el tipo de sistema de archivos a usar)

Perfecto, muchas gracias por orientarme, ahora tengo mucho mas claro como llevar a cabo la instalacion.

Tengo una ultima pregunta, ¿Como monto la /HOME automaticamente al iniciar el sistema?, ¿se monta sola? o ¿El sistema la reconoce automaticamente y no me tengo que preocupar por eso?

---

### Post by guillermolisi on 2012-03-12
> **vegetasupersaiyajin said:**
> Perfecto, muchas gracias por orientarme, ahora tengo mucho mas claro como llevar a cabo la instalacion.

Tengo una ultima pregunta, ¿Como monto la /HOME automaticamente al iniciar el sistema?, ¿se monta sola? o ¿El sistema la reconoce automaticamente y no me tengo que preocupar por eso?
Cuando le asignas con el particionador el punto de montaje /home te aseguras que el sistema se encargue de montar esa particion cada vez que se lo inicie.

---

