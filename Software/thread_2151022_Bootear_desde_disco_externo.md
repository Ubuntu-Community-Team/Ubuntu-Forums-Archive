---
title: "Bootear desde disco externo"
date: 2013-06-03
forum: Software
---

### Post by dam1977 on 2013-06-03
Pude instalar correctamente Ubuntu 12.04 en un disco externo Verbatim de 500 gigas con conexion USB. Pero no consigo hacerlo bootear desde ahi. La notebook reconoce el disco al iniciar el bios. Pero al hacerlo iniciar desde el disco externo me aparece un mensaje de error (missing operating system) y luego va a iniciar desde el disco interno directamente. Sin embargo está todo bien instalado. Cuando booteo desde un CD con SuperGrub2 aparece y lo puedo hacer arrancar perfectamente-. Puede ser que algo falta para que el bios lo pueda hacer arrancar? Me da la impresión que el problema puede estar relacionado con el formato GPT (está en ese formato) en vez de MBR en la tabla particiones. Pero no se cómo arreglarlo. No encuentro la forma de que arranque el dichoso disco. 
gracias...

---

### Post by EnriqueK on 2013-06-03
La forma mas simple y segura de instalar en DD externo es hacer la instalaciñon con todos los DD internos desconectados, de esa manera el grub se instala en el externo sin mayores dramas, te recomiendo ademá que en el externo uses particiones msdos en vez de gpt

---

### Post by dam1977 on 2013-06-04
Gracias EnriqueK. El problema es que para usar msdos ahora tendría que instalar toodo otra vez y la verdad es que me chifla el moño (¿?). Ya instalé una bocha de cosas! Pero no se supone que GPT es mejor?? El GRUB está instalado en el disco externo correctamente. Cuando booteo desde un CD con SuperGrub2 se ve correctamente. El problema es que cuando está solo no hay caso, no arranca. Necesitará un empujoncito, como mi camioneta?

---

### Post by EnriqueK on 2013-06-04
Si al  DD extermo lo vas a usar de forma ocacional, lo mas práctico es seguir usando el SuoerGrub2Disk para arrancarlo, si no es así podés usar este método adaptántolo a tu caso, yo lo empleé para convertir mi tabla a Gpt pero al final no me convenció
[http://www.ubuntu-es.org/node/154663#.Ua3mnnzkAxQ](http://www.ubuntu-es.org/node/154663#.Ua3mnnzkAxQ)

---

### Post by dam1977 on 2013-06-04
Y cómo se hace para usar correctamente GPT y que arranque?? Debe haber un modo...

---

### Post by EnriqueK on 2013-06-05
Habría una forma siemore que uno de llos DD tenga tabla de particiones msdos, por lo que puedo deducir , gpt solo está en el DD externo , suponiendo que sea así y además  quie el DD interno  sea sda, los pasos a seguir son
1 arranca el Ununtu que tienes en el DD externo
2 ejecuta en un terminal
sudo su
grub-mkconfig && grub-install --force /dev/sda  && update-grub

---

### Post by gmunioz on 2013-06-05
Para que un disco rigido externo pueda iniciar desde el, cuando tiene tabla de particiones gpt y no se trata de un máquina con Uefi.
Es necesario crear al comienzo del disco una partición de unos 200 megas, tipo ef02 ó ef00 ó partición de arranque bios, bios boot, sin formato.
Reinstalar el Grub en el disco externo.
Al reiniciar, tendría que iniciar desde el disco externo con un menu para el interno.
Si todo está bien, reiniciar con el disco externo, pero seleccionando el interno, una vez iniciado desconectar el externo y reinstalar el Grub en el interno.

---

