---
title: "Como setear gmail como programa de mail preferido"
date: 2010-05-14
forum: Software
---

### Post by DrKenobi on 2010-05-14
Hola! Cada vez que en algun sitio o programa esta la opcion d mandar un mail, automaticamente me manda a Evolution. Pero yo uso gmail desde chromium, como puedo hacer que directamente me abra una ventana o pestaña con la pagina de gmail en chromium?

Yo creo q es en 'Sistema-->Preferencias-->Aplicaciones Preferidas', pero el problema es que no se que escribir ahi :(

Gracias!

---

### Post by guillermolisi on 2010-05-14
> **DrKenobi said:**
> Hola! Cada vez que en algun sitio o programa esta la opcion d mandar un mail, automaticamente me manda a Evolution. Pero yo uso gmail desde chromium, como puedo hacer que directamente me abra una ventana o pestaña con la pagina de gmail en chromium?

Yo creo q es en 'Sistema-->Preferencias-->Aplicaciones Preferidas', pero el problema es que no se que escribir ahi :(

Gracias!
Si no recuerdo mal, esas opciones son para aplicaciones preferidas (tal como dice su titulo) y Gmail via web no es una aplicacion sino un servicio. Es ese caso la aplicacion seria el navegador web que permite te conectes a Gmail pero, tal como estas pensando, no podras pasarle parametros a Gmail de esa forma para que te componga o permita leer un mensaje. Y si hay una forma, bienvenido el que sepa como.

---

### Post by rojojuan on 2010-05-14
Recién encontré esto:

[http://www.javielinux.com/140-GMail_como_correo_por_defecto_en_Ubuntu.htm](http://www.javielinux.com/140-GMail_como_correo_por_defecto_en_Ubuntu.htm)

Todavía no lo probé.

---

### Post by DrKenobi on 2010-05-14
> **rojojuan said:**
> Recién encontré esto:

[http://www.javielinux.com/140-GMail_como_correo_por_defecto_en_Ubuntu.htm](http://www.javielinux.com/140-GMail_como_correo_por_defecto_en_Ubuntu.htm)

Todavía no lo probé.

rojojuan, me alegraste el dia! Anda ES-PE-TA-CU-LAR!

Eso si, como dice el segundo comentario del link, hay que hacer 'chown'. Y tambien, fijense bien porque los comandos que estan publicados en la pagina no coinciden con el nombre del archivo que ta da para que te bajes.

Yo cambie 'firefox' por 'chromium-browser' y anda perfecto.

Gracias!

---

### Post by rojojuan on 2010-05-15
> **DrKenobi said:**
> rojojuan, me alegraste el dia! Anda ES-PE-TA-CU-LAR!

Eso si, como dice el segundo comentario del link, hay que hacer 'chown'. Y tambien, fijense bien porque los comandos que estan publicados en la pagina no coinciden con el nombre del archivo que ta da para que te bajes.

Yo cambie 'firefox' por 'chromium-browser' y anda perfecto.

Gracias!

Me alegro que te haya servido!

---

### Post by leonardo83 on 2010-05-15
no entendi como usar chown, en que parte uso eso y como? me podrian ayudar?

Saludos! :P

---

### Post by DrKenobi on 2010-05-15
> **leonardo83 said:**
> no entendi como usar chown, en que parte uso eso y como? me podrian ayudar?

Saludos! :P

Por supuesto que te podemos ayudar.
Experto no soy, pero te explico lo que yo hice.

Despues de hacer lo siguiente en el directorio donde bajaste el archivo

```
chmod u+x open_gmail.sh
```

y luego de copiarlo en el directorio bin

```
sudo cp open_gmail.sh /usr/bin
```

Luego vas al directorio /usr/bin y le cambias el dueño:

```
sudo chown **tu_nombre_de_usuario** open_gmail.sh
```

Listo, despues solo sigue los pasos del link y todo anda.

---

