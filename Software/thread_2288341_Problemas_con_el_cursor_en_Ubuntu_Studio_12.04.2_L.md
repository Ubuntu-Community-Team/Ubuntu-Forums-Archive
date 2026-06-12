---
title: "Problemas con el cursor en Ubuntu Studio 12.04.2 LTS"
date: 2015-07-26
forum: Software
---

### Post by Christian_Osuna on 2015-07-26
Hola amigos:
Pido ayuda para este problema un tanto curioso.

Utilicé mi Compaq con Ubuntu Studio LTS, recién instalado y con poca experiencia en esta distribución, para conectarlo a una pantalla adicional.
La configuración de pantalla quedó modificada, después de usarlo para esto, pero no  hubo problema en volver a una configuración adecuada a la pantalla del portatil.
El problema está ocurriendo cada vez que conecto el equipo y todo parece funcionar bien salvo que no se puede ver el cursor del ratón. Parece que se mueve y las zonas por las que pasaría el ratón se activan y responden -pulsando a ciegas- a los click.
Modifico la configuración de pantalla a una resolución diferente y al volver a la configuración habitual, el cursor vuelve a mostrarse sin problemas.

¿Alguna sugerencia para resolver este pequeño problema?

Un saludo y gracias!!!

---

### Post by ElRick on 2015-07-27
No conozco la solución pero tengo tiempo leyendo en este foro y si quieres obtener buenos resultados a tus consultas hazlas en inglés 
Suerte

---

### Post by Christian_Osuna on 2015-07-27
Gracias por el consejo. voy a volver a publicarlo en ingles,

Saludos

---

### Post by enriquek2 on 2015-07-27
Prueba con
sudo update-alternatives --config x-cursor-theme

Elige uno de ellos tecleando el número de algún cursor que te sea adecuado

---

### Post by Christian_Osuna on 2015-07-30
Gracias por tu aportación, enriquek2. Lo he intentado.
Pero lo que me propones parece servir para seleccionar tipos de cursor. Algo que ya había intentado a través del menú del administrador de configuración. Pero no sirve para resolver este problema que explicaba arriba, que tiene toda la pinta de ser un error de software o de instalación o algo así.
Una vez intentado y al reiniciar, sigue apareciendo el mismo problema, el cursor no se muestra pero está ahí. Y solo hasta que cambio en la configuración de la pantalla la resolución y despues le pido que mantenga la anterior (esto es, amago con cambiarla resolución pero luego la devuelvo al origen) el compotamiento del cursor se vuelve normal.
Un saludo y gracias, de nuevo.

---

### Post by Christian_Osuna on 2015-08-01
Hola otra vez:
Un amigo me dio una idea. Quizá reinstalando el XFCE se resolvería el problema, si este fuera un problema del entorno gráfico.
NO ha funcionado. Ahora debería probar a instalar un entorno diferente. Quizá así...
Un saludo!

---

### Post by enriquek2 on 2015-08-03
Te recomiendo instaklar escritorio MATE , a partir de Ubuntu 14.04 está disponible en los repositorios
sudo apt-get install mate-desktop-environment

---

