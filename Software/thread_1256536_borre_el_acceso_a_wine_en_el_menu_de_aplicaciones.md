---
title: "borre el acceso a wine en el menu de aplicaciones"
date: 2009-09-02
forum: Software
---

### Post by waraltca on 2009-09-02
buenas gente...

necesito su ayuda.
hace unos dias durante unas pruebas con wine lo desinstale y me fui al menu de aplicaciones>boton derecho>editar los menus y borre el acceso a wine desde ahi.

Ahora resulta que he instalado nuevamente el wine pero no me sale en el menu de aplicaciones.

Como restauro ese acceso??

gracias de antemano.
salu2

---

### Post by Patriciologico on 2009-09-02
puede que no se haya actualizado el menu, para eso solo basta con reiniciar gnome-panel.

```
killall gnome-panel
```

Puedes tambien reconfigurar wine

```
sudo dpkg-reconfigure wine
```

Saludos!

Pd: Tu Pregunta ha sido movida ya que no lo publicaste en la seccion adecuada. Recuerda leer las normas. En cada seccion del foro hay un sticky indicando que puedes publicar en ella.

---

### Post by bichopro on 2009-09-02
Si no lo logras de otras formas puedes reiniciar la configuracion de gnome a su original, solo tendras que volver a colocar tus applets y cosas asi, pero no borra programas ni nada de eso.

Resetear el escritorio es sencillo, basta con acceder al directorio $HOME del usuario. y borrar los siguientes archivos ocultos: .gnome, .gnome2, .gconf, .gconfd, .metacity. Luego nos desconectamos. De esta manera el escritorio se resetea y la próxima vez que hagamos login estará como nuevo.

---

### Post by moreback on 2009-09-03
Los archivos del menú está en /home/user/.config/menus, archivos applications.menu y settings.menu, a lo mejor si puedes editarlos a mano (son archivos en formato XML) puedas resolver tu problema.

Saludos.

---

