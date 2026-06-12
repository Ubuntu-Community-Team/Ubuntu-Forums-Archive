---
title: "Dudas con KDE"
date: 2009-10-31
forum: Software
---

### Post by FB91 on 2009-10-31
Tengo ganas de darle una segunda oportunidad a KDE, (creo que el comando era [FONT=Courier New]sudo aptitude install kubuntu-desktop[/FONT]) pero la última vez que lo intenté no me fué muy bien que digamos, así que ahora que salió karmic capaz que me funcione mejor...

La última vez que ejecuté  ese comando se me instaló todo lo más bien y cuando iniciaba sesión me daba a elegir entre Gnome o KDE, pero cuando entraba con Gnome tuve algunos problemas como por ejemplo que no me iniciaba el Synaptic entre otras...

Así que mi pregunta es si me conviene intentar de nuevo... (recuerdo que en KDE me tiraba unos pantallazos negros terribles y creo que era por la versión del KDE, que capaz que ahora ya viene actualizada)

Salu2! :D

---

### Post by oktubrer on 2009-10-31
Si es por darle la oportunidad, dasela que se la merece!
Ahora particularmente yo nunca tuve buenas experiencias mezclando ambos entornos.  Prefiero hacer otra particion chiquita e instalar Kubuntu / Ubuntu separados.  Al final termina siendo menos trabajoso, bah, por lo menos asi lo veo yo.

---

### Post by FB91 on 2009-10-31
si hago como vos me decis, si instalo kubuntu en una partición hay algún problema  con que le ponga para que use las particiones /home y swap ?? es decir, las mismas que estoy usando ahora con Ubuntu

---

### Post by oktubrer on 2009-10-31
Con la /swap no hay ningún problema, aunque no estoy seguro como reacciona si hibernas una sesión al rigido, y después levantás la otra instalación.  Nunca probé.  Si no sos de hibernar, no problem.
Con el /home tampoco habría problemas, yo lo usaba de esa forma, pero si usas el mismo nombre de usuario en ambas instalaciones y tenés programas en común te va a pisar las configuraciones.

---

### Post by guillermolisi on 2009-10-31
> **oktubrer said:**
> Con la /swap no hay ningún problema, aunque no estoy seguro como reacciona si hibernas una sesión al rigido, y después levantás la otra instalación.  Nunca probé.  Si no sos de hibernar, no problem.
Con el /home tampoco habría problemas, yo lo usaba de esa forma, pero si usas el mismo nombre de usuario en ambas instalaciones y tenés programas en común te va a pisar las configuraciones.
Correcto, seria como haber instalado los dos entornos graficos: un desastre con los menues y algunas otras cosas. 

Si fuera posible, undual boot seria mi recomendacion: Ubuntu por un lado y Kubuntu por otro (o Ubuntu en ambos pero uno con gdm y otro con kdm)

---

### Post by aledruetta on 2009-11-06
Yo preparé cuatro particiones. Una para Ubuntu Jaunty (que es el que venía usando), otra para Kubuntu Karmic, otra para Home, y la última para Swap.

La Home, es la de Jaunty. Cuando instalé Kubuntu lo instalé en una sola partición para la raíz y todo lo demás. Lo único que están compartiendo en este momento las dos distros es Swap.

Entonces, si yo cambio el nombre de usuario de una de las dos distribuciones (que ahora tienen el mismo usuario) Puedo asociar la partición Home con Kubuntu sin problemas ¿es así?

Lo que no puedo hacer es mezclar los dos usuarios ¿verdad? porque ahí se me mezclan todas las configuraciones ¿voy bien?

Ahora, una vez hecho eso ¿existe alguna forma de establecer vínculos (links) entre, por ejemplo, las carpetas Documentos, Música, Videos, etc., para que lo que haya en una se vea en la otra como si pertenecieran a la misma carpeta? Como se hace en gnome cuando uno quiere que los temas, los iconos y las fuentes del usuario sirvan para root.

Yo creé una carpeta vacía en cada home y ejecuté en terminal:
```
ln -s carpetagnome /media/partición/usuario/carpetakde
```
y no dio resultado.

¿Cómo sería?

---

### Post by pablo.s on 2009-11-06
> **aledruetta said:**
> Yo creé una carpeta vacía en cada home y ejecuté en terminal:
```
ln -s carpetagnome /media/partición/usuario/carpetakde
```y no dio resultado.

¿Cómo sería?

Ahi tendrias que verificar los permisos
y grupos de las carpetas. Cuales
usuarios tienen acceso a cada carpeta,
etcetera.

Seria mas facil si tuvieras 
tres particiones asi:
-Una / para Ubuntu
-Una / para Kubuntu
-Una /home para ambas.

Y le definis en la instalacion que
la particion que creaste para /home
sea, valga la redundancia, /home.
De todas maneras los permisos te 
los cambia para el usuario de la instalacion,
asi que es mas o menos igual.

---

### Post by oktubrer on 2009-11-06
> **aledruetta said:**
> Ahora, una vez hecho eso ¿existe alguna forma de establecer vínculos (links) entre, por ejemplo, las carpetas Documentos, Música, Videos, etc., para que lo que haya en una se vea en la otra como si pertenecieran a la misma carpeta? Como se hace en gnome cuando uno quiere que los temas, los iconos y las fuentes del usuario sirvan para root.

Yo creé una carpeta vacía en cada home y ejecuté en terminal:
```
ln -s carpetagnome /media/partición/usuario/carpetakde
```
y no dio resultado.
¿Cómo sería?

Para cambiar el tema del usuario root en Gnome, lo más simple es ejecutar la aplicación de apariencia con sudo desde una terminal.  Modificas tema, iconos, etc, y esos cambios son sólo para el root.  Tené en cuenta que a veces es conveniente que no sea el mismo tema que el usuario común, sobre todo para darte cuenta cuando podés hacer macanas con mayúsculas.

Con respecto a los links, si las carpetas reales están en Ubuntu, recomiendo hacerlo desde Kubuntu.  Primero asegurandote que la partición /home se monta automáticamente al inicio.  Después desde el home de tu usuario en Kubuntu, directamente 
```
ln -s /particion_home_ubuntu/carpetagnome carpeta_vinculada_kde
```
No creo que sea problemas de permisos porque por defecto ambos setean el UID y GID del primer usuario como 1000, por lo que sería el mismo.

---

### Post by aledruetta on 2009-11-07
> **oktubrer said:**
> Con respecto a los links, si las carpetas reales están en Ubuntu, recomiendo hacerlo desde Kubuntu.  Primero asegurandote que la partición /home se monta automáticamente al inicio.  Después desde el home de tu usuario en Kubuntu, directamente 

Muy bueno ese dato!!

---

### Post by aledruetta on 2009-11-07
Mi primer intento consistió en cambiar el usuario de Kubuntu por otro distinto al que ya tenía:
```
sudo chgrp nuevo_usuario usuario_anterior

sudo usermod -l nuevo_usuario usuario_anterior

sudo usermod -d /home/nuevo_usuario -m usuario_anterior
```

Ahí cambié el grupo de mi usuario por el nuevo; el nombre de mi usuario por el nuevo; y moví mi directorio en home para el nuevo directorio.

Todo bien, salvo... que no quería funcionar el Wicd y algunas otras cosas. Así que, como mi instalación de Kubuntu es reciente y no tiene casi nada. Voy a reinstalar con un nuevo usuario.

Después, probaré el tema de los links.

---

