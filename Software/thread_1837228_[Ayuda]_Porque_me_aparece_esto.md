---
title: "[Ayuda] Porque me aparece esto?"
date: 2011-09-01
forum: Software
---

### Post by Ferbetta on 2011-09-01
Hola, soy nuevo en ubuntu.
Bueno, tengo instalado 2 sistemas operativos.
Windows 7 y Ubuntu 11.04.

Resulta que ayer a la noche instale una actualizacion, y reinicio la maquina y elijo Ubuntu.
Bueno al cargar me aparece un terminal, y no puedo acceder al sistema operativo.
Intente salir pero se traba.

Alguna forma de acceder al sistema, porque es raro que me aparezca un terminal, para mi.

No quiero volver a formatear el sistema operativo ya que no quiero perder tiempo.

Gracias!
Lamentablemente no pude sacar una captura.

---

### Post by gmunioz on 2011-09-01
1- Edita el archivo /etc/default/grub
sudo su
nano /etc/default/grub

si esta línea, está asi
 GRUB_HIDDEN_TIMEOUT=0

la cambias a
 GRUB_HIDDEN_TIMEOUT=5
guarda el archivo
cierra nano

ejecuta
update-grub
reboot

2- Al reiniciar pulsa escape
en el menu del Grub, elige un kernel anterior al
último instalado.
si inicia, instala los kernel headers del ultimo kernel instalado y reinstala dkms y los drivers privativos de video, desde synaptic.

---

### Post by alfplayer on 2011-09-02
No podría ejecutar update-grub sin acceso al sistema.

---

### Post by gmunioz on 2011-09-02
Hola Esteban:
entiendo que cuando dice el usuario:
***"....Bueno al cargar me aparece un terminal, y no puedo acceder al sistema operativo..."***
Se refiere a que no tiene entorno gráfico, un terminal, consola: es el sistema operativo!

---

### Post by alfplayer on 2011-09-02
Hola.

Entiendo que puede ser busybox también.

Ferbetta, sería útil que proveas más información.

---

