---
title: "Paquetes huérfanos"
date: 2011-10-30
forum: Software
---

### Post by Vero1 on 2011-10-30
Hola a todos,

Tengo otro problema.
Ayer, instalé un programa desde el Centro de Soft que es para remover paquetes huérfanos.
Me mostró unos paquetes y me preguntó si quería eliminarlos. Le dije que sí.

Despues me dí cuenta de que había borrado archivos que de ninguna manera eran huérfanos, como es el caso de GParted, por ejemplo.

Hoy cuando encendí la máquina y me salió el Grub, me di cuenta que faltaba Memtest(ya lo reinstalé), pero me faltan los Linux headers de Versiones anteriores y me debe faltar algo mas porque entré en modo de recuperación y me lleva a tty, no me permite reiniciar gdm y tampoco me conduce a la ventana que me salía para iniciar normalmente o con las otras opciones que hay, como reparar paquetes rotos, etc.

Alguien podría decirme donde fueron a parar esos archivos que eliminé como huérfanos o si no, qué headers debo instalar para tener lo que tenía.

Desde ya muchas gracias y saludos

---

### Post by alfplayer on 2011-10-31
Se puede probar instalando el escritorio para intentar resolver ese problema.

---

### Post by Vero1 on 2011-10-31
Hola, gracias por responder.

Si te referis al escritorio de Ubuntu, está instalado, lo mismo que el de Gnome pero lamentablemente no se ha arreglado el problema.

saludos

---

### Post by EnriqueK on 2011-10-31
sudo apt-get install --reinstall ubuntu-desktop
Es peligroso remover paquetes huérfanos , especialmente si has estado instalando librerías para compilar
Para instalar el linux-headers que corresponda al linux-image que está en uso, ejecuta:
sudo apt-get install linux-headers-$(uname -r)

---

### Post by Vero1 on 2011-10-31
Hola EnriqueK,
Gracias por responder.
Voy a hacer lo que me dices.

En cuanto a que es peligroso remover paquetes huérfanos, pues al estar el programa en el Centro de Software y al no advertir nada, yo estaba confiada. Empecé a desconfiar cuando vi lo de Gparted. En fin.

Despues informo de los resultados.

saludos

---

