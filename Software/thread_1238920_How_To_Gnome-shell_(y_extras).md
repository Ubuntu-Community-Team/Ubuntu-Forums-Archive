---
title: "How To: Gnome-shell (y extras)"
date: 2009-08-12
forum: Software
---

### Post by augias on 2009-08-12
Este how-to no lo estoy publicando en el subforo relativo al software porque considero que no es útil para solucionar un problema con ubuntu linux y, lo que es más relevante, este how to esta dirigido a los cumpas de la comunidad que quieran simplemente probar algo nuevo y monitorear el avanze de lo que eventualmente sera el window-manager de Gnome 3. 

A mis buenos moderadores: Si consideran que este tema debería encontrarse en Software, les pido disculpas y se mueve a software no más. 


[SIZE="5"]Introducción[/SIZE]

Gnome shell es el propuesto nuevo window manager para gnome 3. Es un rediseño bastante radical en cuanto a lo que los usuarios de gnome (y por lo general cualquier usuario de desktop managers visuales modernos) estan acostumbrados. Shell está escrito con Javascript, y depnde de las librerias clutter y mutter. No soy developer asique no me hagan preguntas acerca de eso.

Si te interesa shell y deseas seguirlo de cerca, agrega el siguiente URL a tus favoritos: [COLOR="Red"][http://git.gnome.org/cgit/gnome-shell/](http://git.gnome.org/cgit/gnome-shell/)[/COLOR] para revisar los updates mientras se suben al repositorio de git.

[SIZE="5"]Paso A: Instalando jhbuild y gnome-shell[/SIZE]
Primero hemos de bajar el script que nos instala jhbuild en nuestro direcotrio ~ (o donde lo quieras en verdad), y lo hacemos correr:
```

wget http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash ./gnome-shell-build-setup.sh

```

Luego de haber sido instalado, jhbuild estara en un direcotrio /bin/ en tu directorio de usuario. Asegurate de tener ~/bin en tu PATH. Si no sabe como, por favor investiguelo por su cuenta. Ahora estamos listos para instalar gnome-shell:
```

jhbuild build

```
[COLOR="Red"]Esto se demora un montón[/COLOR]. Ve a hacerte una taza de café. 

[SIZE="5"]Paso B: Usando gnome-shell[/SIZE]
Esta parte es bastante simple. Gnome shell parte por un script hallado en ~/gnome-shell/source/gnome-shell/src/ llamado "gnome-shell". Si lo abres así, se abrira en una ventana. Si deseas que reemplaze completamente a tu escritorio, debes agregarle el valor "--replace". Puede ser:

```
~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
```
o 
```

cd ~/gnome-shell/source/gnome-shell/src/
./gnome-shell --replace

```

Una vez adentro, la cosa se ve así:
[[IMG]http://dl.getdropbox.com/u/208391/shell-caps/thumbs/Shell4-0.png[/IMG]]("http://dl.getdropbox.com/u/208391/shell-caps/Shell1.png") [[IMG]http://dl.getdropbox.com/u/208391/shell-caps/thumbs/Shell4-1.png[/IMG]]("http://dl.getdropbox.com/u/208391/shell-caps/Shell2.png") [[IMG]http://dl.getdropbox.com/u/208391/shell-caps/thumbs/Shell4-2.png[/IMG]]("http://dl.getdropbox.com/u/208391/shell-caps/Shell3.png") [[IMG]http://dl.getdropbox.com/u/208391/shell-caps/thumbs/Shell4-3.png[/IMG]]("http://dl.getdropbox.com/u/208391/shell-caps/Shell4.png")
puedes salirte oprimiendo ctrl+c en la consola, cancelando el proceso, y volverás a metacity o compiz. 

Gnome-shell esta en pleno desarrollo y no está ni cerca de salir al público, asique no crean que las próximas distribuciones de ubuntu vayan a verse así. Lo primero que notamos es que desaparece del panel cualquier manera de escoger y cambiar de programas abiertos. Esto se puede hacer mediante el alt+tab clásico, o bien abriendo el menu de activities a lo que se llama el "overview". Puedes crear cuantos escritorios deseas y arrastrar ventanas donde deseas, como "expo" de compiz. El menu de Cairo ahora se reemplaza por un menu igual en el overview. 

Como sigue estando en desarrollo gnome-shell, es importante saber cómo mantenerlo al día. Nada más simple, pues si observas en la pagina de GIT de gnome que han habidos updates, simplemente escribes en tu consola:
```
jhbuild buildone gnome-shell
```
Si lo que necesitas es construir todo desde cero por algun error grave, o quizas porque haz cambiado algo desde los directorios src/, debes escribir
```
jhbuild build -f -a -c
```
Si al construir o reconstruir o updatear te alen errores de dependencias, significa que se han hecho cambios en jhbuild también, y tendras que volver a descargar [http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh) y construir todo desde el primer paso.

[SIZE="5"]Parte C: Breadcrumbs[/SIZE]
Parte de gnome-shell que a muchos les parece que falta, es una manera de escoger entre tus aplicaciones desde el escritorio sin recurrir al overview. Para esto hay un branch de git que se esta desarrollando en paralelo, y tomando siempre de los updates de shell. Se llama "breadcrumbs" de Jon Nettleton y los encuentro espectaculares. Pueden mirar estos screenshots y decidir si quieren instalar: 

[[IMG]http://dl.getdropbox.com/u/208391/shell-caps/thumbs/bread1.png[/IMG]]("http://dl.getdropbox.com/u/208391/shell-caps/bread1.png") [[IMG]http://dl.getdropbox.com/u/208391/shell-caps/thumbs/bread2.png[/IMG]]("http://dl.getdropbox.com/u/208391/shell-caps/bread2.png") [[IMG]http://dl.getdropbox.com/u/208391/shell-caps/thumbs/bread3.png[/IMG]]("http://dl.getdropbox.com/u/208391/shell-caps/bread3.png")

Para instalarlo, son dos pasos medianos en total, pero debes observar la calma y hacerlos en orden y no olvidarse de nada! Primero hay que cambiar el branch de mutter que soporta a shell.
```
cd ~/gnome-shell/source/mutter
git remote add -f linux4kix git://github.com/linux4kix/mutter.git
git checkout -b linux4kix
git fetch linux4kix
jhbuild shell
make
make install

```
Luego de eso pasamos a gnome-shell/ a instalar el branch de breadcrumbs mismo:
```
cd ~/gnome-shell/source/gnome-shell
git remote add -f linux4kix git://github.com/linux4kix/gnome-shell.git
git checkout linux4kix/livecrumbs
git fetch linux4kix
jhbuild shell
make
make install

```
Cuando está todo listo, puedes correr gnome shell y jugar con esta variación excelente. 

Para mantener este branch actualizado, los comandos son los siguientes. Para mutter: 
```
git checkout linux4kix
git fetch linux4kix
jhbuild shell
make
make install
```
Y luego lo mismo para los breadcrumbs:
```
git checkout linux4kix/livecrumbs
git fetch linux4kix
jhbuild shell
make
make install
```
Si quieres volver al gnome-shell original, solamente debes hacer 
```
git checkout master
jhbuild shell
make
make install
```
en ambos directorios: ~/gnome-shell/source/mutter y ~/gnome-shell/source/gnome-shell

[SIZE="5"]Conclusiones[/SIZE]
Como concepto, personalmente estoy muy de acuerdo con la dirección de gnome-shell. No diría que está mejor que gnome ahora, o mejor que cualquier otro desktop-manager, porque sigue estando en desarrollo, pero lo que promete lo encuentro interesante e incluso un poquito emocionante. Sigo estando muchísimo más cómodo usando gnome con compiz, es la verdad, pero simplemente porque algunos programas no corren demasiado bien en gnome-shell: OpenOffice y Firefox tienen un scroll un poco pegado y cuando hay muchas aplicaciones abiertas al mismo tiempo, empieza a ser un poco (apenas se nota) tiritón. Sin embargo no creo que se pueda pedir mucho más a una aplicacion en su etapa de Alpha testing. Además tienen que tomar en cuenta que las cosas estan cambiando TODOS LOS DIAS, y la mejora de hoy puede revertirse mañana. El bug que solucionan hoy puede volver la proxima semana, y el diseño que tiene ahora ni en broma es la definitiva. Desde que comenzé a usarlo han hecho cambios esteticos relativamente importantes como 4 veces asique, insisto, no crean que esto *ES* Gnome 3. Seguir este proyecto de cerca es muy gratificante, ademas de interesante ver qué cosas cambian, cómo y porqué, desde la pagina web GIT de gnome-shell. 

Si tienen preguntas, o si desean discutir sobre la viabilidad de gnome-shell, sean bienvenidos. Ojalá alguien se entusiame simplmente por probarlo, aunque sea una sola vez y luego le haga un rm -rf gnome-shell/. Disrutenlo!

Su amigo Augias. :eek:

---

### Post by Patriciologico on 2009-08-15
[Post de la Semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [15 de agosto]("http://www.ubuntu-cl.org/grupos/foro/instalando-gnome-shell") de 2009

---

### Post by Carlos C on 2009-08-16
Buenísimo augias.

---

