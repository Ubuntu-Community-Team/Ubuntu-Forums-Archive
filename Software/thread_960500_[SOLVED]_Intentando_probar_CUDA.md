---
title: "[SOLVED] Intentando probar CUDA"
date: 2008-10-27
forum: Software
---

### Post by User21 on 2008-10-27
Estoy siguiendo [**este tutorial**]("http://lifeofaprogrammergeek.blogspot.com/2008/05/cuda-development-in-ubuntu.html")  para darle una probada a [CUDA]("http://www.nvidia.com/object/cuda_home.html"). 
Poseo una Nvidia GT 8600 y ya tengo funcionando los drivers de Nvidia NVIDIA-Linux-x86-177.73-pkg1 perfectamente. 
Seguí el tutorial como se indica y ya instale las dependencias que requeria. Me descargué los paquetes necesarios del sitio de Cuda y estoy casi listo. Solo que NO ENTIENDO que hay que hacer en la parte que dice:

# Add environment variables
[COLOR=#006600]echo "# CUDA stuff[/COLOR]
[COLOR=#006600]PATH=\$PATH:/usr/local/cuda/bin[/COLOR]
[COLOR=#006600]LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:/usr/local/cuda/lib[/COLOR]
[COLOR=#006600]export PATH[/COLOR]
[COLOR=#006600]export LD_LIBRARY_PATH" >> ~/.bashrc[/COLOR]
# restart the terminal for the changes to take effect. 

Alguien sabe al respecto ? O alguien puede tratar de duplicar el tutorial ?

---

### Post by faktorqm on 2008-10-27
Basicamente, pone "sudo gedit .bashrc" y agrega al final:

```

# CUDA stuff
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/cuda/bin
LD_LIBRARY_PATH=/usr/local/cuda/lib
export PATH
export LD_LIBRARY_PATH

```

El comando ese que pusiste en la terminal hace eso. Sino tenes permisos, deberias ejecutar:

```

echo "# CUDA stuff
PATH=\$PATH:/usr/local/cuda/bin
LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:/usr/local/cuda/lib
export PATH
export LD_LIBRARY_PATH" | sudo tee -a ~/.bashrc

```

Salu2!!!

---

### Post by User21 on 2008-10-27
Pero muchísimas gracias, caballero! Le pusiste la cereza al postre! 
Ya estoy probando CUDA! :D Fantastico! 

[[IMG]http://img229.imageshack.us/img229/6045/cudatesting01ya8.th.jpg[/IMG]]("http://img229.imageshack.us/my.php?image=cudatesting01ya8.jpg")[[IMG]http://img229.imageshack.us/images/thpix.gif[/IMG]]("http://g.imageshack.us/thpix.php")[[IMG]http://img504.imageshack.us/img504/829/cudatesting02ma9.th.jpg[/IMG]]("http://img504.imageshack.us/my.php?image=cudatesting02ma9.jpg")[[IMG]http://img374.imageshack.us/img374/1883/cudatesting03mv0.th.jpg[/IMG]]("http://img374.imageshack.us/my.php?image=cudatesting03mv0.jpg")

[[IMG]http://img504.imageshack.us/images/thpix.gif[/IMG]]("http://g.imageshack.us/thpix.php")

[[IMG]http://img374.imageshack.us/images/thpix.gif[/IMG]]("http://g.imageshack.us/thpix.php")
Ahora, necesito buscar aplicaciones que usen CUDA en Ubuntu y me den alguna utilidad REAL, jejeje xD 
Como ser, codificacion de video, creacion de DVD-VIdeos, o conversion de formatos de audio y video, etc.
¬_¬ ! Hay ?..

---

