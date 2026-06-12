---
title: "Nuevo Usuario de Ubuntu"
date: 2009-09-27
forum: Software
---

### Post by Verde Ñandu on 2009-09-27
Buenas, soy nuevo, acabo de instalar Ubuntu 8.04 y quisiera saber si perdí toda la información que tenía en windows... je, si es posible traerla para Ubuntu o si la perdí en el traspaso... es una compu compartida así q buen, me sirve mucho su ayuda, gracias de antemano!

---

### Post by emiliano_raso on 2009-09-27
1) Sin ofender: Se mas explicito :-S
2) Fijate si en LUGARES/EQUIPO te aparece la partición con Windows.
Si no te aparece es porque te morfaste todo el disco cuando instalaste Ubuntu.
3) Hiciste una particion para poner Ubuntu? Si es asi, y en el proceso de instalación no elegiste MANUAL, lo mas probable es que hayas instalado Ubuntu en TODO el disco, y perdiste hasta las ganas de vivir :-P
4) Bienvenido al foro y a GNU/Linux.

---

### Post by Fak89 on 2009-09-27
Como dijeron, si hiciste una partición, deberías poder ingresar a esta desde el menú "Lugares" como "Soporte de XGb" y desde ahí acceder a toda tu información.
Si no creaste una partición, lamento decirte que perdiste todo..

Un saludo, y bienvenido a los foros.

---

### Post by santiagoward2000 on 2009-09-27
Bienvenido! :)
Para ver si borraste la partición de Windows cuando instalaste Ubuntu, abrí una terminal (Aplicaciones > Accesorios > Terminal), y escribí:
```
sudo fdisk -l
```
Te va a pedir tu contraseña (ojo que no ves nada cuando la ingresás, pero entra igual). Si la partición de Windows sigue ahí, vas a ver un ítem en la lista con sistema NTFS.
Si tenés alguna duda, podés pegar el resultado que ves en la terminal acá, para ver si te podemos ayudar mejor.
Ojalá no hayas perdido nada.
Suerte!

---

### Post by staar on 2009-09-27
Aclaro, si seguiste el instalador usando las opciones por defecto, lo más probable es que los datos de Ventanas aún estén ahí, el comportamiento por defecto es crear una nueva partición (si no hay espacio, se achica una partición existente para hacerlo) y ahí instalar ubuntu, dejando a las otras particiones sin tocar...

sería ilógico (y hasta peligroso) que la opción por defecto fuera 'Usar todo el disco', se la debe seleccionar explícitamente...

saludos

---

### Post by emiliano_raso on 2009-09-27
> **staar said:**
> Aclaro, si seguiste el instalador usando las opciones por defecto, lo más probable es que los datos de Ventanas aún estén ahí, el comportamiento por defecto es crear una nueva partición (si no hay espacio, se achica una partición existente para hacerlo) y ahí instalar ubuntu, dejando a las otras particiones sin tocar...

sería ilógico (y hasta peligroso) que la opción por defecto fuera 'Usar todo el disco', se la debe seleccionar explícitamente...

saludos

Si no recuerdo mal, hay tres opciones:
La primera usar todo el disco, la segunda mitad y mitad, y la tercera MANUAL.

---

### Post by staar on 2009-09-27
[IMG]http://news.softpedia.com/images/extra/LINUX/small/ubuntu904installation-small_007a.png[/IMG]

saludos

---

### Post by emiliano_raso on 2009-09-27
> **staar said:**
> [IMG]http://news.softpedia.com/images/extra/LINUX/small/ubuntu904installation-small_007a.png[/IMG]

saludos

Perdon pero, eso de que version es? 9.04?

---

### Post by staar on 2009-09-27
> **emiliano_raso said:**
> Perdon pero, eso de que version es? 9.04?
Si, pero estoy razonablemente seguro de que en HH era muy similar, creo que no estaban las barritas bonitas, pero el orden de las opciones era el mismo, el más lógico y seguro, a prueba de 'comportamiento de instalación de software ventanero', si la primera opción fuera usar todo el disco, tendríamos una lluvia de quejas de novatos que, por querer probar el SO, perdieron todos sus datos por no leer y apretar Next todo el tiempo...

la primera opción no aparece si se está instalando en un disco vacío, pero este no es el caso...

saludos

---

### Post by Hei Ku on 2009-09-27
Si, el instalador viene así desde hace un rato largo. Tenés que ser bastante testarudo para romper una particion existente.

---

