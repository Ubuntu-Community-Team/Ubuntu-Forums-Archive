---
title: "Problemas con comando su"
date: 2009-12-08
forum: Software
---

### Post by Hanataro on 2009-12-08
Hola estimados son un mortal que trata de salir de windows y entrar al mundo Ubuntu sin ser informatico  jejejeje

pero tengo un problema para instalar Java me piden ejecutar un comando su y no permite escribir la contraseña.

he leido en varios foros que por seguridad no aparece y que se debe escribir igual y darle enter pero = no me resulta, por eso me atrevo a preguntar.

de antemano gracias :KS

---

### Post by Carlos C on 2009-12-08
Hola. Varias cosas. En primer lugar debes saber lo que estás haciendo cuando administres tu sistema o puedes llegar a dañarlo. El comando "su" no es lo mismo que "sudo". En Ubuntu comúnmente utilizamos "sudo" y te recomiendo que te documentes para que entiendas en qué consiste:

[http://www.guia-ubuntu.org/index.php?title=Sudo](http://www.guia-ubuntu.org/index.php?title=Sudo)

El comando "su" es diferente, te permite abrir la sesión de otro usuario. En caso de no entregar el ID de ningún usuario, es decir simplemente escribir "su", le estás diciendo al sistema que te vas a cambiar a la cuenta del super usuario, el "root". El problema es que Ubuntu no trae la cuenta root habilitada por defecto. Es posible hacerlo e información al respecto en internet hay bastante. Te recomiendo que entiendas primero la diferencia entre "sudo" y "su", que comprendas por qué es importante saber lo que cada comando significa y luego decidas si quieres trabajar con un usuario root.

Sobre la instalación de java sería bueno que nos dijeras de qué manera lo estás intentando. Lo más recomendable en tu caso es que instales la versión de los repositorios oficiales, lo que puedes hacer con la aplicación "Gestor de paquetes Synaptic", el comando "apt-get" o el comando "aptitude".

Saludos.

---

### Post by bichopro on 2009-12-09
Intenta reemplazandolo con el comando: sudo su

---

### Post by moreback on 2009-12-09
Lo mejor para instalar Java es instalar el plugin para Firefox usando:

[apt-get install icedtea6-plugin]("apt:icedtea6-plugin")

---

