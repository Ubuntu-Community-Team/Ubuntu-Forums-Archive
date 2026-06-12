---
title: "Ventanas sin controles (Synaptic por ej.)"
date: 2008-10-15
forum: Software
---

### Post by nemodot on 2008-10-15
Buenas, me pasa muy seguido cuando instalo un tema que algunas ventanas no adoptan la morfología del tema recien instalado, por ejemplo la ventana del synaptic como pueden ver en el screenshoot que adjunto.

Alguien sabe como solucionar esto?

---

### Post by santiagoward2000 on 2008-10-15
Hola!
El problema es que los temas que instalás se instalan normalmente en tu usuario, en la carpeta **/home/esteban/.themes**, y los íconos en **/home/esteban/.icons**.
Programas como Synaptic se usan con gksudo, por eso usan los themes instalados en **/usr/share/themes** y **/usr/share/icons**.
Supongo que si copias las carpetas ahí tendría que andar, pero yo nunca lo probé.
Saludos!

---

### Post by lega on 2008-10-15
Es como dice Santiago yo lo solucioné así, tipeas en consola

```
sudo ln -s /home/tu_cuenta/.themes /root/.themes
```

```
sudo ln -s /home/tu_cuenta/.icons /root/.icons
```

y si tenes otra fuente que no se ve

```
sudo ln -s /home/tu_cuenta/.fonts /root/.fonts
```

donde **tu_cuenta** es tu usuario de Ubuntu ,espero te sirva, saludos

---

