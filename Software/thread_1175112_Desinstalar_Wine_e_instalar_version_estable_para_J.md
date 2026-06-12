---
title: "Desinstalar Wine e instalar version estable para Jaunty"
date: 2009-05-31
forum: Software
---

### Post by leonardomdq on 2009-05-31
Hola a todos, quiero desinstalar wine, instale una version que no es estable y queria desinstalarla y volver a instalar pero una version que funciene bien en Jaunty (estable).

Gracias

---

### Post by staar on 2009-05-31
como instalaste la versión inestable? te bajaste algún deb? agregaste algún repositorio? compilaste?

saludos

---

### Post by guillermolisi on 2009-05-31
Wine tiene una opcion propia de desinstalacion. Buscala en el menu de Wine.

Estoy usando la ultima version no estable de Wine, las bajo desde los repositorios propios de Wine, y con JJ anda muy bien. 

Que problemas te trajo ?

---

### Post by NickCis on 2009-05-31
Y mira si lo instalaste con algun deb, lo pods desinstalar con:
sudo apt-get remove wine

Si agregaste los repositorios de wine borras la linea de los repositores de wine del /etc/apt/sources.list 
Haces un:
sudo apt-get update

Y dsp instalas:
sudo apt-get install wine

Saludos..

---

### Post by leonardomdq on 2009-05-31
Les comento como lo instale.

Añadi el repositorio
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/winehq.list

```

Despues añadi la clave publica
```

sudo wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Despues actualize sistema
```

$ sudo apt-get update

```

Y despues lo inslale
```

$ sudo apt-get install wine

```

Estos fueron todos los pasos que hice para instalarlo. Se que me instalo la ultima version, pero quiero volver a la version mas estable.
La version que tengo instalada es 1.0.1

Salu2

---

### Post by guillermolisi on 2009-05-31
> **leonardomdq said:**
> Les comento como lo instale.

Añadi el repositorio
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/winehq.list

```Despues añadi la clave publica
```

sudo wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && sudo apt-get update

```Despues actualize sistema
```

$ sudo apt-get update

```Y despues lo inslale
```

$ sudo apt-get install wine

```Estos fueron todos los pasos que hice para instalarlo. Se que me instalo la ultima version, pero quiero volver a la version mas estable.
La version que tengo instalada es 1.0.1

Salu2
Desactiva con el utilitario Software Sources, el repositorio de Wine.

Actualiza el cache de paquetes (update) y busca la version estable con Synaptic para instalarla.

---

### Post by leonardomdq on 2009-05-31
perdon guillermo pero soy re novato, para desactivar con el utilitarios software sources el repositorio de Wine, donde encuentro eso?

gracias y perdonen las molestias

---

### Post by josecuervo86 on 2009-05-31
**Sistema > Administración > Origenes del software**

De ahi te vas a **software de terceros** y desmarcas las casillas de los repos que agregaste

---

### Post by guillermolisi on 2009-05-31
> **leonardomdq said:**
> perdon guillermo pero soy re novato, para desactivar con el utilitarios software sources el repositorio de Wine, donde encuentro eso?

gracias y perdonen las molestias
Si estas usando Ubuntu con Gnome (y no algunos de sus sabores k/X/etc.) deberias tener una opcion Software Sources (Origenes de Programas podria estar traducido) dentro del menu Sistema - Administracion.

Una vez seleccionado ese utilitario te pedira tu password (es como sudo) y te mostrara varias solapas. Dirigite a la segunda (de izquierda a derecha) llamada Software de Terceros (o Terceras Partes), Ubica la linea del repositorio de Wine y quitale el check/tilde, luego click en el boton Cerrar y segui las instrucciones en pantalla.

---

### Post by leonardomdq on 2009-05-31
Listo ya esta solucionado, gracias a todos por la ayuda.

Saludos

---

