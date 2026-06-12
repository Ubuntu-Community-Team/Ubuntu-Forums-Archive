---
title: "Problema, invertir rueda de mouse en ubuntu 11.10"
date: 2012-03-22
forum: Software
---

### Post by dupuydeg on 2012-03-22
Hola!, quizá este es un error de principiante,

la cosa es que cambiando opciones del administrador de configuraciones de compiz con ubuntu 11.10 y de cambios de unity a gnome, se me invirtió la rueda del mouse, ahora todos los movimientos para avanzar en las ventanas hacia abajo o hacia arriba quedaron invertidos, y he revisado casi todas las opciones de configuraciones y no logro encontrar la opción para restablecerlo.

alguien me puede ayudar??

gracias!

---

### Post by pabloposso on 2012-05-01
En tu carpeta personal, pon "ver archivos ocultos". Edita el archivo: ".Xmodmap" Tiene una numeración del 1 al 12. El 4 y el 5 seguro que están al revés(pointer = 1 2 3 5 4 6 7 8 9 10 11 12),solo los corriges(pointer = 1 2 3 4 5 6 7 8 9 10 11 12), reinicias sesión y listo.

---

### Post by dupuydeg on 2012-05-01
gracias [pabloposso]("http://ubuntuforums.org/member.php?u=1628471"), ahora estoy usando la version de linux mint 12 en vez de ubuntu como tal, y no se encuentra ese archivo en la carpeta personal, ni siquiera en ocultos, pero si vuelvo en algun momento a ubuntu revisaré la opcion, gracias!

---

### Post by pabloposso on 2012-05-02
pero en mint también tenés ese problema???:shock:

---

### Post by dupuydeg on 2012-05-02
nop en mint no, funciona de maravilla, gracias!

---

### Post by jnizama on 2012-07-26
Amigo yo tambien tuve ese problema que se me invirtio el scroll del mouse, pero eso fue porque instale ubuntu-tweaks y active el desplazamiento natural, desactivalo y todo volverá a la normalidad

---

### Post by dupuydeg on 2012-07-26
gracias, ahora estoy funcionando con debian squeeze, ya no están esos problemas, pero lo tendré en cuenta, gracias!

---

