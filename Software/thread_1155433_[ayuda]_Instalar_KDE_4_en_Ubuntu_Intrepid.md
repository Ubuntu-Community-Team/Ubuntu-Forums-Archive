---
title: "[ayuda] Instalar KDE 4 en Ubuntu Intrepid"
date: 2009-05-10
forum: Software
---

### Post by leonardomdq on 2009-05-10
Hola a todos, gente necesito ayuda para instalar KDE4 en mi Intrepid, si alguien me puede guiar estare agradecido.

saludos

---

### Post by josecuervo86 on 2009-05-10
Queres instalar el gestor completo? Yo te recomendaria que te bajes Kubuntu-desktop

```
sudo apt-get install kubuntu-desktop
```

Asi podes mantener Gnome y a la vez tambien podes usar Kubuntu

---

### Post by Ptero-4 on 2009-05-10
Si estoy en lo correcto, kubuntu 8.10 (intrepid ibex) ya viene con el KDE 4 (el 4.0 o 4.1), solo necesitas instalar el paquete kubuntu-desktop.

---

### Post by leonardomdq on 2009-05-10
gracias por responder, miren esto me devuelve:

```

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  kubuntu-desktop: Depende: ark pero no va a instalarse
                   Depende: dolphin pero no va a instalarse
                   Depende: dragonplayer pero no va a instalarse
                   Depende: kde-window-manager pero no va a instalarse
                   Depende: kde-zeroconf pero no va a instalarse
                   Depende: kdebase-workspace-bin pero no va a instalarse
                   Depende: kdemultimedia-kio-plugins pero no va a instalarse
                   Depende: kdepasswd pero no va a instalarse
                   Depende: kdm pero no va a instalarse
                   Depende: khelpcenter4 pero no va a instalarse
                   Depende: klipper pero no va a instalarse
                   Depende: kmix pero no va a instalarse
                   Depende: konsole pero no va a instalarse
                   Depende: ksnapshot pero no va a instalarse
                   Depende: ksysguard pero no va a instalarse
                   Depende: ksystemlog pero no va a instalarse
                   Depende: kuser pero no va a instalarse
                   Depende: language-selector-qt pero no va a instalarse
                   Depende: okular pero no va a instalarse
                   Depende: software-properties-kde pero no va a instalarse
                   Depende: systemsettings pero no va a instalarse
                   Recomienda: adept pero no va a instalarse
                   Recomienda: akregator pero no va a instalarse
                   Recomienda: gdebi-kde pero no va a instalarse
                   Recomienda: guidance-power-manager pero no va a instalarse
                   Recomienda: gwenview pero no va a instalarse
                   Recomienda: install-package pero no va a instalarse
                   Recomienda: jockey-kde pero no va a instalarse
                   Recomienda: kaddressbook pero no va a instalarse
                   Recomienda: kamera pero no va a instalarse
                   Recomienda: kate pero no va a instalarse
                   Recomienda: kde-printer-applet pero no va a instalarse
                   Recomienda: kdebase-plasma pero no va a instalarse
                   Recomienda: kdebluetooth pero no va a instalarse
                   Recomienda: kdegraphics-strigi-plugins pero no va a instalarse
                   Recomienda: kdepim-kresources pero no va a instalarse
                   Recomienda: kdepim-strigi-plugins pero no va a instalarse
                   Recomienda: kdepim-wizards pero no va a instalarse
                   Recomienda: kdeplasma-addons pero no va a instalarse
                   Recomienda: kdesudo pero no va a instalarse
                   Recomienda: kgrubeditor pero no va a instalarse
                   Recomienda: kmag pero no va a instalarse
                   Recomienda: kmail pero no va a instalarse
                   Recomienda: kmousetool pero no va a instalarse
                   Recomienda: knotes pero no va a instalarse
                   Recomienda: konqueror pero no va a instalarse
                   Recomienda: konqueror-nsplugins pero no va a instalarse
                   Recomienda: konqueror-plugin-searchbar pero no va a instalarse
                   Recomienda: kontact pero no va a instalarse
                   Recomienda: kopete pero no va a instalarse
                   Recomienda: korganizer pero no va a instalarse
                   Recomienda: krdc pero no va a instalarse
                   Recomienda: krfb pero no va a instalarse
                   Recomienda: ktimetracker pero no va a instalarse
                   Recomienda: ktorrent pero no va a instalarse
                   Recomienda: kubuntu-docs pero no va a instalarse
                   Recomienda: kubuntu-konqueror-shortcuts pero no va a instalarse
                   Recomienda: kvkbd pero no va a instalarse
                   Recomienda: kwalletmanager pero no va a instalarse
                   Recomienda: okular-extra-backends pero no va a instalarse
                   Recomienda: openoffice.org-kde pero no va a instalarse
                   Recomienda: plasmoid-quickaccess pero no va a instalarse
                   Recomienda: update-notifier-kde pero no va a instalarse
E: Paquetes rotos
leonardo@leonardo-laptop:~$ 


```

---

### Post by Hei Ku on 2009-05-10
Proba poniendo:

sudo apt-get install kde-core

A ver si te tira algun error.

---

### Post by leonardomdq on 2009-05-10
puse ese comando , me cargo todo y cuando reinicio me tira un error al cargar el panel, no me lo cargo bien parece y el entorno KDE no me lo cargo, sigo con el gnome pero el boton de apagado en el panel superior no lo veo y me carga la pantalla de usuario y contraseña la de KDE esa color gris y negro.

---

### Post by pol666 on 2009-05-10
Mira cuando estas en el login (GDM), abajo donde dice sesion selecciona KDE4.
Igual no te recomiendo tener dos escritorios, se vuelve todo lento. experiencia propia.

---

### Post by SLA_leandrin on 2009-05-10
mmm podés entrar en la sesión de KDE y apretar ALT+F2, y ahí escribir

```
plasma
```

A ver que pasa?

---

### Post by Hei Ku on 2009-05-10
Volve a poner ahora:

sudo apt-get install kubuntu-desktop

A ver si ahora mejoro tu situacion. Con el comando que te di solo te instala una base de kde, pero no lo suficiente para loguearte.

Igualmente, ojo que si lo instalas te va a meter el 4.1, que esta lleno de bugs. Deberias agregar el PPA del 4.2 para tener algo mas usable.

---

### Post by leonardomdq on 2009-05-10
me instalo el 4.1 , para volver gnome y revertir lo que hice como seria?? digo desinstalar y dejar todo como esta.

---

### Post by Hei Ku on 2009-05-11
sudo aptitude remove de todos los paquetes que instalaste.

---

### Post by leonardomdq on 2009-05-11
Gracias Hei Ku pude desisntalar los paquetes. 

saludos

---

### Post by pablo.s on 2009-05-11
> **Hei Ku said:**
> sudo aptitude remove de todos los paquetes que instalaste.

Fua, lo dijo y no se le 
escapó una lagrima...

---

### Post by leonardomdq on 2009-05-11
Gracias a todos ya pude solucionarlo. Cuando me instalo la 4.1 efectivamente tiene bugs, con la 4.2 queda mejor.

Saludos

---

### Post by Hei Ku on 2009-05-11
La diferencia entre 4.1 y 4.2 es abismal. No me imagino cómo va a ser la 4.3.

---

### Post by leonardomdq on 2009-05-11
Ya esta solucionado ;)

Si hay mucha diferencia Hei Ku entre y otra.

Muchas gracias  todos por la onda que ponen y como ayudan permanentemente en el foro.
Eternamente agradecido.

Saludos

---

