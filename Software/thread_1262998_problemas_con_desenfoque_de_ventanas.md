---
title: "problemas con desenfoque de ventanas"
date: 2009-09-10
forum: Software
---

### Post by leviatan300 on 2009-09-10
Hola, soy nuevo en esto de linux y como todo nuevo usuario tengo un problemita con desenfocar ventanas, al momento de señalar esta opción todas las ventanas se ponen en negro y de heho toda la pantalla se torna negra y no puedo seleccionar nada, mi pregunta es ¿cómo podria desactivar esta opción? un saludote.

---

### Post by guillermolisi on 2009-09-10
> **leviatan300 said:**
> Hola, soy nuevo en esto de linux y como todo nuevo usuario tengo un problemita con desenfocar ventanas, al momento de señalar esta opción todas las ventanas se ponen en negro y de heho toda la pantalla se torna negra y no puedo seleccionar nada, mi pregunta es ¿cómo podria desactivar esta opción? un saludote.
Pasado a Software.

Estas usando Compiz / efectos de escritorio ?

---

### Post by leviatan300 on 2009-09-10
Si, estoy usando compiz, la verdad no tengo buena tarjeta de video y creo ke por eso es mi problema.

---

### Post by staar on 2009-09-10
pasate a una consola virtual con Ctrl + Alt + F1, logueate, y borrá la carpeta con la configuración de compiz ```
rm -r ~/.config/compiz
``` después reiniciá gdm con ```
sudo /etc/init.d/gdm restart
``` y apretá Ctrl + Alt + F7 para volver al entorno gráfico, logueate en él y ya tendrías que ver el escritorio, pero con la configuración de compiz reiniciada...

tu suposición está bien, para usar el efecto blur de compiz se necesita una placa de video que específicamente lo soporte...

saludos

---

