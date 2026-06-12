---
title: "una ayuda con la carpeta /HOST?"
date: 2009-05-03
forum: Software
---

### Post by goldenfox on 2009-05-03
hola gente tengo un problema un poco grabe verán es que ya hace un tiempo instale ubuntu con wubi y lo instale en lo que seria el D: de windows y en esa partición esta casi todo el espacio del disco 
haora necesito mucho espacio pero no tengo solo veo la partición de windows C: que es de 23 GB y esta casi del todo ocupada 
por lo que me puse a buscar y encontré que todo el espacio de lo que seria D: esta en la carpeta /host y acá mi problema solo puedo editar la carpeta si soy root con el usuario común slo puedo verla :( 
lo que necesitaria hacer es ponerla como una partición y darle permisos a mi usuario de verla y editarla

---

### Post by z37a on 2009-05-03
> **goldenfox said:**
> hola gente tengo un problema un poco grabe verán es que ya hace un tiempo instale ubuntu con wubi y lo instale en lo que seria el D: de windows y en esa partición esta casi todo el espacio del disco 
haora necesito mucho espacio pero no tengo solo veo la partición de windows C: que es de 23 GB y esta casi del todo ocupada 
por lo que me puse a buscar y encontré que todo el espacio de lo que seria D: esta en la carpeta /host y acá mi problema solo puedo editar la carpeta si soy root con el usuario común slo puedo verla :( 
lo que necesitaria hacer es ponerla como una partición y darle permisos a mi usuario de verla y editarla

Lo que necesitas es utilizar lso permisos de root, parea ello se usa el comando sudo, seguramente queres hacerlo desde la interfaz grafica, asi que lo que podes hacer es abrir una ventana de nautilus(navegador de carpetas) como root haciendo lo siguiente:

- Preciona Alt+F2
- Ejecuta lo siguiente, "gksudo nautilus" o "sudo nautilus" si usas 8.10

Con eso abris una ventana de nautilus como root, con permisos totales, solo tene cuidado con lo que haces!!!!!!

---

### Post by goldenfox on 2009-05-03
el tema es que necesito ese espacio para cosas como crear DVD's guardar archivos .iso y con root en nautilus no podria hacer

un ejemplo seria usar el programa devede para crear un dvd de algún anime y necesite el espacio para el archivo iso que genera

---

### Post by z37a on 2009-05-04
> **goldenfox said:**
> el tema es que necesito ese espacio para cosas como crear DVD's guardar archivos .iso y con root en nautilus no podria hacer

un ejemplo seria usar el programa devede para crear un dvd de algún anime y necesite el espacio para el archivo iso que genera

Ahh ahora entendi mejor, bueno podrias hacer lo mismo que con sudo nautilus, pero con la aplicacion que quieras, la ejecutas como root y esta asi configurarla para usar el /home

---

### Post by goldenfox on 2009-05-04
ok lo probare
pero me parese una forma no muy eficiente xD

no hay forma de darle a mi usuario permisos de edicion sobre esa carpeta?

---

### Post by Hei Ku on 2009-05-04
Si, se puede. Lo mas facil es que abriendo nautilius con sudo, despues le des permisos de edicion a tu usuario.

---

### Post by goldenfox on 2009-05-04
bien lo probe y no me deja cambiarle el grupo, el propietario me dise que no tengo permisos suficientes y soy root :S 
despues al queres cambiar los permisos sobre la carpeta para los demas tampoco me deja
pero me deja cambiar los permisos sobre los archivos pero al cerrar el sudo nautilus todo buelve a como estaba antes T_T

---

