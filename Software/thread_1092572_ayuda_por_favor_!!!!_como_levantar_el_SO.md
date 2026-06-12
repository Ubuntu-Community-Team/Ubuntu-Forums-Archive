---
title: "ayuda por favor !!!! como levantar el SO"
date: 2009-03-10
forum: Software
---

### Post by franko71ar on 2009-03-10
Hola:
Soy nuevo con linux, tengo instalado Ubuntu 8.04 Server, la instalación fué todo bien. Una vez que me logueo veo una pantalla (tipo DOS) con este símbolo $ para introducir directamente comandos; mi pregunta es ¿como puedo arrancar en un modo gráfico?

Gracias

---

### Post by santiagoward2000 on 2009-03-10
Hola!
Mirá, la versión Server de Ubuntu viene sin ningún escritorio instalado. Si querés entrar tendrías que instalar alguno.
Yo te recomendaría instalar la version Desktop, que sí viene con un escritorio instalado.
Saludos!

---

### Post by franko71ar on 2009-03-10
Gracias por tu respuesta, que escritorio puedo instalar? sobre esta versión?

---

### Post by santiagoward2000 on 2009-03-10
Cualquiera tendría que andar. Xfce, Gnome, KDE, Lxde... Si te da la máquina para cualquiera, ya es un tema de gustos.
Por las dudas, ¿qué máquina tenés? Como para ver si alguno andaría medio lento.

---

### Post by Hei Ku on 2009-03-10
Dado que sos nuevo, yo te recomendaria reinstalar con un Ubuntu Desktop. 

El server esta mas tuneado para funcionar como servidor, pero lo mismo podes hacer con un desktop y si la consola te marea es mejor que tengas un escritorio, al menos al principio.

---

### Post by ADICTOALMAXIMO on 2009-03-10
Nose que seria de mi sin escritorio

---

### Post by abn91c on 2009-03-10
en esa pantalla de "DOS" ```
startx
```

---

### Post by santiagoward2000 on 2009-03-10
> **abn91c said:**
> en esa pantalla de "DOS" ```
startx
```

Hmmm... Me parece que en este caso esto no va a servir de mucho, porque instaló Ubuntu Server. Tendría que instalar algún escritorio antes, no?

---

### Post by abn91c on 2009-03-10
> **santiagoward2000 said:**
> Hmmm... Me parece que en este caso esto no va a servir de mucho, porque instaló Ubuntu Server. Tendría que instalar algún escritorio antes, no?
si el codigo es```
sudo apt-get install ubuntu-desktop
```

---

### Post by josecuervo86 on 2009-03-10
A mi me paso algo similar: estaba en mis primeras epocas de ubuntu y al querer desinstalar apache, por error borre Gnome entero, no me pregunten como. Cuando vi que estaba desisntalando muchos paquetes reinicie la maquina y volvi en modo texto.
Asique puse

```
sudo apt-get install gnome
```

y volvio a la "normalidad"

Imagino que tiene que hacer lo mismo

---

### Post by faktorqm on 2009-03-11
codigo?!? no sera **comando**?....

---

### Post by santiagoward2000 on 2009-03-11
> **faktorqm said:**
> codigo?!? no sera **comando**?....

Es de Indiana y se gastó en escribir en castellano! No seamos tan exigentes! ;)

---

### Post by franko71ar on 2009-03-12
> **santiagoward2000 said:**
> Es de Indiana y se gastó en escribir en castellano! No seamos tan exigentes! ;)

gracias a todos por la data, santiago te comento mi pc es un P4 2.4 a 3.0 mhz con un hd 1024 mb, 256 de ram

---

