---
title: "[SOLVED] Tema de las ventanas de Synaptic."
date: 2009-08-22
forum: Software
---

### Post by nemodot on 2009-08-22
Buenas,

Instalé un tema de gnome-looks que se ve muy bonito pero cuando quiero usar el synaptic y otros programas afines, las ventanas no heredan el tema y aparecen sin alguno y se ve feo.

Cómo puedo corregir este conflicto? Ya intente hacer estos enlaces simbolicos pero no sirve: 

```

sudo ln -s /home/yourusername/.themes /root/.themes
sudo ln -s /home/yourusername/.icons /root/.icons
```

Saludos!

---

### Post by santiagoward2000 on 2009-08-22
> **nemodot said:**
> Buenas,

Instalé un tema de gnome-looks que se ve muy bonito pero cuando quiero usar el synaptic y otros programas afines, las ventanas no heredan el tema y aparecen sin alguno y se ve feo.

Cómo puedo corregir este conflicto? Ya intente hacer estos enlaces simbolicos pero no sirve: 

```

sudo ln -s /home/yourusername/.themes /root/.themes
sudo ln -s /home/yourusername/.icons /root/.icons
```

Saludos!

Hola!
Para usar los temas como root, tenés que instalarlos en **/usr/share/themes** y **/usr/share/icons**. Supongo que debe andar si haces el link a estas carpetas, en vez de **/root/....**. También podés simplemente mover las carpetas de tu home a /usr, lo va a detectar igual (sacándoles el punto del nombre).
Saludos!

---

### Post by rubioo on 2009-08-22
Yo para hacer eso, copie y pege los temas (usando nautilus como root) en las carpetas correspondientes (/root/.themes y /root/.icons)

      Saludos!

---

### Post by nemodot on 2009-08-22
Eureka!

Solo funcionó cuando copie los archivos empleando el nautilus como root.

Parece que el comando cp hacia accesos directos en lugar de copiar las carpetas enteras.

Gracias!

---

### Post by nopersona on 2009-08-22
Ubuntu tweak también trae esa opción.

---

