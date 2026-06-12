---
title: "Instalación de Ubuntu en dual boot no inicia en otro SO"
date: 2009-10-11
forum: Software
---

### Post by 10921 on 2009-10-11
hola :
ante todo me presento soy cristian y me registre hace poco , como vi que esto era para novatos lo lei y segui todos los pasos , y logre instalar ubuntu correctamente , hasta hay todo bien pero lo que pasa es que cuando quiero reiniciar con el otro sistema operativo este no logra iniciarse .
desde ya les agradeceria su ayuda .
saludos .

---

### Post by josecuervo86 on 2009-10-11
Hola, primero que nada, te aparece la opción para cargarlo pero no podes iniciar? Para tener un poco mas de idea, podrias mostrarnos lo que hay en boot/grub/menu.lst?

Esto lo podes hacer poniendo en la terminal (**Aplicaciones** > **Accesorios** > **terminal**):
```
gedit /boot/grub/menu.lst
```

Lo que aparezca en el archivo pegalo aca asi lo vemos.

Tambien pega si podes lo que salga cuando pones esto (en la terminal tambien):

```
sudo fdisk -l
```

---

### Post by ramiro_md on 2009-10-13
Cuando decís que no logra arrancar...te referis a que "el otro SO" no figura en la lista del GRUB o que no carga ?. 
Un saludo.

---

