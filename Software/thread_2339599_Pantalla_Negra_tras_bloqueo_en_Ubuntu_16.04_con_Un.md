---
title: "Pantalla Negra tras bloqueo en Ubuntu 16.04 con Unity"
date: 2016-10-10
forum: Software
---

### Post by rthelmofp on 2016-10-10
Hola amigos del foro.

Les comento que soy nuevo aquí, pero soy un usuario de Ubuntu desde la versión 11.10 a partir de la cual he ido actualizando sólo a versiones LTS. Actualmente estoy usando la 16.04.1 y he encontrado un problema que no he podido resolver completamente dado que no encuentro información sobre él en la web y tampoco he podido verlo como un bug reportado en Launchpad.net. Inicialmente pensé que era problema de mi laptop pero luego hice memoria y me dí cuenta que este problema comenzó presentarse una vez que actualicé a la versión 16.04, por cuanto creo que puede ser un bugs. A continuación describo el problema:

Al utilizar Ubuntu con escritorio Unity, tras el bloqueo de pantalla y luego de que esta se apaga, la pantalla no vuelve a encenderse de ninguna forma. Probé moviendo el mouse, apretando teclas y usando combinaciones de teclas y nada, tampoco puedo acceder a la consola con Ctrl+Alt+F1. Sin embargo, sé que el sistema sigue encendido, tanto por las luces como por las descargas que siguen en curso mientras la pantalla está apagada. La única manera de restablecer el sistema es apagándolo de forma abrupta. Sólo puedo eviar esto quitando la opción de apagar la pantalla en las opciones de gestión de energía y evitando bloquear la pantalla. Ahora bien, he probado si esto se repite en otros entornos de escritorio y al usar el de Gnome más similar al 2.X, veo que este problema no se presenta, por lo cual asumo que es un problema de Unity o alguno de sus componentes (tal como ocurre con el unity-panel-service el cual no carga apropiadamente y debo reiniciarlo mediante un scrip durante el inicio, este si es un bug oficial).

Espero que esta descripción haya servido para entender el problema. Si requieren alguna información adicional les agradeceré me indiquen los comandos necesarios para extraer información del sistema.

Gracias de antemano.

---

### Post by morasaul on 2017-06-16
Tengo el mismo problema. ¿Lo has resuelto?

---

