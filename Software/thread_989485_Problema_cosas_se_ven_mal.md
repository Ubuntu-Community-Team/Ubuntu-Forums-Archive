---
title: "Problema cosas se ven mal"
date: 2008-11-21
forum: Software
---

### Post by --Lutari-- on 2008-11-21
Instalé Ubuntu 8.10 en esta computadora

Procesador Intel Celeron
601 Mhz 320 Mb de RAM

anda bien un poco arrastrado mas lento iba windows. pero hay un problema cuando paso el cursor sobre el algo deja un cuadro y cuando inicio a veces dice que hay un error con Xorg o algo. Tambien toda la barrita donde estan los iconos para cerrar la ventana no estan.

---

### Post by guillermolisi on 2008-11-21
> **--Lutari-- said:**
> Instalé Ubuntu 8.10 en esta computadora

Procesador Intel Celeron
601 Mhz 320 Mb de RAM

anda bien un poco arrastrado mas lento iba windows. pero hay un problema cuando paso el cursor sobre el algo deja un cuadro y cuando inicio a veces dice que hay un error con Xorg o algo. Tambien toda la barrita donde estan los iconos para cerrar la ventana no estan.

Podrias decir que placa de video estas usando ?

Si no te acordas y no tenes el manual de la motherboard para consultar, abri una consola y pega en tu respuesta la salida del comando
```
lspci |grep VGA
```

---

### Post by --Lutari-- on 2008-11-22
Hice lo que dijiste fui a la terminal lo ejecuto pero no pasa nada aparece un cuadro blanco. En el se puede escribir pero no se ve nada.

En el LiveCD de ubuntu todo funcionaba bien. Intente instalar Xubuntu que tambien el LiveCD anda bien pero llega al 45 % y dice que hay un error.

Que debo grabar el cd de nuevo en menos velocidad o limpiar la lectora. Pero con ubuntu instale sin problemas.

---

### Post by arielcabral on 2008-11-22
Veamos... abrí la consola y ejecutá el comando 

lspci

y pegá la respuesta.

---

### Post by --Lutari-- on 2008-11-22
Pero no anda la consola se convirtio en un cuadro blanco totalmente ademas de no tener la barrita para cerrarlo ni nada solo un cuadro. Se puede escribir pero no se ven las letras.

Creo que ni siquiera tiene placa de video esa computadora decia al de 32 bits de video no me acuerdo mucho.

---

### Post by arielcabral on 2008-11-22
Entonces tu problema puede ser que no cumplís los requisitos mínimos de memoria RAM.

REQUERIMIENTOS MINIMOS PARA UBUNTU 8.10

# 700 MHz x86 processor
# 384 MB of system memory (RAM)
# 8 GB of disk space
# Graphics card capable of 1024×768 resolution
# Sound card
# A network or Internet connection

REQUERIMIENTOS RECOMENDADOS PARA UBUNTU 8.10 (Compiz Fusion)

# 1.2 GHz x86 processor
# 384 MB of system memory (RAM)
# Supported graphics card

---

### Post by arielcabral on 2008-11-22
Para ese tipo de equipo te recomiendo Xubuntu... es igual pero con escritorio xfce.

Espero que sirva...

---

### Post by --Lutari-- on 2008-11-22
Gracias ya lo solucione era por que tenia activados los efectos visuales ahora anda de 10. :)

---

### Post by arielcabral on 2008-11-22
Ok... de nada... suerte

---

