---
title: "Problema al iniciar sesion"
date: 2008-09-05
forum: Software
---

### Post by Mauro22 on 2008-09-05
Buenas!!


Tengo un problemita y no se me ocurre nada... y tampoco tengo internet (estoy desde la palm) como para hacer una busqueda en google.


El problema es que de la noche a la mañana, no me inicia sesion. Carga el wallpaper y el puntero y listo; ahi queda.


Borre .gnome .gnome2 .gnome_private y nada!



Espero sus respuestas! :)

---

### Post by Darkade on 2008-09-05
Logras entrar al GDM? le das tu user y tu password y se traba el login?

intenta reiniciando el X con Ctrl+Alt+Backspace e intenta loggear en un "failsafe gnome" ve si asi puedes loggear, eso recupera algunas configuraciones asi que quizas cuando cierres esa session ya puedas entrar en tu session normal de gnome

---

### Post by Mauro22 on 2008-09-06
Entro al GDM, pongo mis datos y carga el wallpaper y el mouse. Eso es todo.


Probe lo que dijiste pero no va...


Descubri que es algo con mi sesion unicamente. Cree otra y levanto lo mas bien.


Se puede crear otra cuenta, borrar la actual y mover el home de esa cuenta a la nueva??


Ahora estoy con XP (lo tuve que instalar :P) hasta que encuentre la solucion y de paso pruebo el Google Chrome !!

---

### Post by Darkade on 2008-09-06
Si es contu session podrias borrar los archivos de configuraciòn de tu home, pero es arriesgado, aunque podria servir.
Y si, es posible mover el home.
>Crea otra cuenta y loggea
>en un terminal escribe

```
gksudo nautilus /home/$nombredeusuarioanterior
```

eso va a abrir un nautilus en tu home anterior copia lo que necesites. luego en un terminal escribe

```
sudo chown $nuevousuario
```

Supongo que hay modo de recuperar tu cuenta, probablemente hay un error en alguno de tus archivos de configuracion o mandas a llamar a algun programa que se cuelga cuando inicias sesion. Aunque si no te importa cambiar de nombre de usuario y perder algunas configuarciones personales este metodo funcionará bien

PD trata de no copiar archivos y carpetas ocultos de tu home (los que empiezan con ".") porque alguno de ellos es probablemente el que te esta causando problemas

---

