---
title: "Escuchar radios via Internet (ex Novato que viene de windows)"
date: 2009-08-05
forum: Software
---

### Post by jarsoft on 2009-08-05
No he podido oir ninguna radio en linux aún. El firefox intenta instalar controladores y no encuentra nada. Una pista por favor. 
Gracias.

---

### Post by EnriqueK on 2009-08-05
La forma mas rápida y simple sería primero instalá el reproductor **vlc** , seguidamente en Firefox instalá el complemento "MediaPlayerConnectivity", luego si es necesario configuralo para que VLC sea el reproductor predeterminado. Lo que queda es ir a la pagina de cada emisora, le das a reproducir y esto hará que lo haga con el player que tengás predefinido , en este caso sería con VLC y esto te va a permitir tomar nota de la URL de la transmisión y así conformar tu lista de reproducción y así no tendrás que ingresar a la página de las emisoras, sinó que podrás reproducir directamente.

---

### Post by euzkoarima on 2009-08-05
Te puede resultar útil leer [este post]("http://ubuntuforums.org/showthread.php?t=1162559") donde hablan del tema.

Saludos,
Eduardo

---

### Post by josecuervo86 on 2009-08-06
Tambien podrias bajarte el soft que hizo el amigo juancarlospaco ;) Se llama RadioGUI y te permite escuchar radios de la Argentina.

Lo podes bajar de [ACA]("http://tecnicoslinux.com.ar/livecd/RadioGUI_1.6_all.deb")

---

### Post by lega on 2009-08-06
Deberías agregar repositorios medibuntu e instalar non-free codecs 
>  * Primero debemos instalar el paquete ubuntu-restricted-extras desde el repositorio multiverse de ubuntu, en una terminal tipeamos.

sudo apt-get install ubuntu-restricted-extras

    * Agregamos el repositorio Medibuntu al final de nuestro archivo sources.list

sudo gedit /etc/apt/sources.list
 
## Medibuntu.
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

    * Añadimos la llave del repositorio recargamos nuestro archivo sources.list e instalamos el paquete

    wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
    sudo apt-get install non-free-codecs

con eso no deberías tener problemas

---

### Post by juancarlospaco on 2009-08-07
> **lega said:**
> Deberías agregar repositorios medibuntu e instalar non-free codecs

**[Hice un .deb para eso tambien ]("http://tecnicoslinux.com.ar/livecd/medibuntu-repo-all-ubuntus_1_all.deb")**:)

---

