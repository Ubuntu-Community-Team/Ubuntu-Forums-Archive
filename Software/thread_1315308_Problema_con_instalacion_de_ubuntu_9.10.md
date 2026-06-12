---
title: "Problema con instalacion de ubuntu 9.10"
date: 2009-11-05
forum: Software
---

### Post by juanes2009 on 2009-11-05
Hola, el motivo de este mensaje es para los que tuvieron problemas con la actualizacion de 9.04 a 9.10. Primero lo que me paso fue que quedo sin sonido y no aparecia ningun hardware de sonido, a este lo solucione instalando grub2 y magicamente funciono. Luego reinicie y se colgaba en el inicio, despues de luchar un par de horas me di cuenta que tenia conflicto con mi aceleradora ATI, lo que hice fue iniciar en modo seguro he instalar este driver [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English) , fue el unico que funciono ya q es justamente para la version 9.10 x86_ 64, necesitan tener instalado cualquiera de estas versiones de X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4, lo bajan y lo instalan $ sudo sh ati-driver-installer-9-10-x86.x86_64.run y listo. Ubuntu nuevamente funcionando.

P/D: este fue mi caso y solucion espero que les sea util.):P

---

