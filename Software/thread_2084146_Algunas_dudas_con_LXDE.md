---
title: "Algunas dudas con LXDE"
date: 2012-11-14
forum: Software
---

### Post by Tosh78 on 2012-11-14
Hola a todos, ando con una netbook y estoy viendo que escritorio instalarle. A ver si me pueden ayudar.
Por ahora, el que mas me convencion fue LXDE, que es muy ligero, pero me encuentro con dos problemas:
1) el icono de status de la bateria no anda bien, me marca siempre 100%. Se que es un problema comun por lo que estuve viendo en google, pero hasta ahora no encontre una forma de solucionarlo, alguien sabe como hacerlo?
2) Y esto hasta me da un poco de verguenza preguntarlo porque debe ser muy tonto, pero juro que no encontre solucion. Como ejecuto un script con pcmanfm? Con gnome o cinnamon, daba doble click y me preguntaba si queria ejecutar, ejecutar en terminal o editar. Con LXDE no tengo esas opciones, y para colmo uno de mis scripts arranca con sudo...con lo cual deberia poner la contrasenia, pero nunca llego a ese punto.

La otra opcion que estuve pensando fue XFCE como alternativa al escritorio, pero lo probe y tengo basicamente los mismos problemas.

Si alguien me puede dar una mano, les agradeceria muchisimo. Sepan disculparme si son dudas muy basicas, la verdad es que solo uso linux en casa despues del trabajo para ver videos o mandar mails. Intento arreglarmelas con google, pero hay veces que no encuentro lo que necesito.
Desde ya les agradezco.

---

### Post by guillermolisi on 2012-11-16
Tanto XFCE como LXDE usan componentes de OpenBox y por eso las diferencias que encontras al momento de ejecutar scripts y demas.

Si lo que estas buscando es una solucion de compromiso entre algo liviano y funcional (desde el punto de vista de un usuario final avanzado), creo que XFCE es el candidato, IMHO.

En el menu principal de XFCE tenes una opcion Settings que te permite configurar practicamente todo el escritorio, por lo menos lo mas grueso. Dentro de ello podes indicar que cargue al inicio aplicaciones de Gnome y KDE.

Si en el icono del Menu Principal haces click derecho podras editarlo y, para los casos de tener que ejecutar algun comando con sudo, podras ver cual es el metodo de aplicacion y repetirlo para los casos particulares que tengas.

Si queres un file manager mas completo que Pcmanfm, mi sugerencia (personal) es Dolphin.

Como ves, podes estar utilizando un escritorio liviano como XFCE y agregarle esas aplicaciones de Gnome y/o KDE que mas te gusten.

---

### Post by dirty fingers on 2012-11-27
Y si usas conky para ver el estado de la batería ? no es una solución pero una buena forma de esquivar el problema ;-)

---

