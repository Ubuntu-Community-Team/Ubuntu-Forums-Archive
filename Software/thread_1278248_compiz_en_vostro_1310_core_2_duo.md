---
title: "compiz en vostro 1310 core 2 duo"
date: 2009-09-29
forum: Software
---

### Post by eduardofranco on 2009-09-29
que tal gente linux, soy nuevo en foro, convivo con win2 y ubuntu, pero hoy me he decicido a abandonar la ventaninta):P y darle todo el espacio de mi laptop al pinuinito, es más bonniro, simpático, gratis, legal etc y por último me gusta + , así que respaldaré la info de mi hd.  y haré  la instalación limpia, manual, reseteando todo mi hd. 

luego les cuento.
\\:D/
si hay algun consejillo o truco que quieran compartir antes de proceder se agradece:lol:

---

### Post by eduardofranco on 2009-09-29
ah!!! mi note es un vostro 1310 core 2 duo :P

---

### Post by eduardofranco on 2009-09-30
ojalá pudieran ayudarme
 ya instalé, todo en hardware funciona ok, pero no puedo hacer funcionar compiz. con el 8.4 andaba bien, me he cambiado aprobechando de hacer la migración definitiva, 

bajé compiz, lo configure en el compiz setting manager, pero no se ve nada, vuelvo a repetir, no es un problema de targeta grafica por que en 8.4 andaba bien
gracias

---

### Post by AlexDDR on 2009-09-30
primero tienes que decir que tareta grafica tienes, si instalaste la version 9.04 deberias darte una vuelta por del post de intel


[http://ubuntuforums.org/showthread.php?t=1166388](http://ubuntuforums.org/showthread.php?t=1166388)

la proxima version de Ubuntu que sale el proximo mes OCTUBRE , que es la 0.10, ya vendran solucionados esos problemas, ademas de kernel modde setting , que evitará pestañeos cuando se cambia de resolucion de pantalla


EL TIP MAXIMO para esto es que instales una perticiones root "/" separada del "/home", asi puedes reinstalar o actualizar a una version superior sin tener que respaldar datos, a que tus datos de usuario y configuraciones de programas se encuentran separados de la instalacion del sistema

hay varias guias para eso y depende del disco duro que tengas cuanto espacio dejar para el raiz o root "/", en mi opinion minimo 20GB, pero yo deje en mi disco duro 50GB ara raiz, ya que algunas veces instalo juegos muy pesados o codifico videos que ocupan mucho espacio (aunque tambien se puede usar el espacio del home), pero igual se puede crear una carpeta dentro con permisos de escritura para usuario normal e igual se puede guardar cosas por si hace falta, por eso te recomiendo 20GB si tienes un disco duro grande, aunque algunos les alcanza hasta con 5GB pero depende de cuantos progrmas y el espacio en disco




saludos

---

### Post by Carlos C on 2009-09-30
Hola eduardofranco. Por favor recuerda publicar tus threads en el subforo adecuado. Lo habías hecho en el foro principal, que usamos para temas generales relacionados con el funcionamiento del foro. En cada subforo hay un [sticky]("http://ubuntuforums.org/showthread.php?t=1162708") que te dice qué corresponde publicar en él. Por lo mismo, debes publicar cada problema en un post independiente.
Por otro lado, trata de que los título de tus threads hagan referencia al problema, que sean términos que saldrían en caso de que otra persona usara el buscador para resolver una situación parecida, "pajarito nuevo" no es un buen ejemplo de ello.

En caso de dudas siempre puedes leer las normas:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Como bien dice AlexDDR debes decir cuál es tu tarjeta gráfica para poder ayudarte. En caso de que no lo sepas puedes escribir en el terminal:
```
lspci grep| VGA
```y pegar acá lo que te salga.

Título editado. Movido al subforo "Software".
Saludos.

---

### Post by moreback on 2009-09-30
El comando en realidad debiera ser:

```
lspci | grep VGA
```

---

### Post by Carlos C on 2009-09-30
Cierto cierto cierto...

---

