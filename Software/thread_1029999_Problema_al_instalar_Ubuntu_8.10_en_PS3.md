---
title: "Problema al instalar Ubuntu 8.10 en PS3"
date: 2009-01-04
forum: Software
---

### Post by Athos_aramis on 2009-01-04
Hola, antes que nada quiero presentarme, mi nombre es Josue y espero que me ayuden con una cuestion.

Estoy tratando de instalar el citado sistema en mi PS3 y todo salia bien hasta que termino y me pidio los datos de cuenta, nombre y contraseña.

Por lo que veo... si que entra a ubuntu pero lo hace en modo texto, ya anteriormente en kubuntu 7.10 me ocurria y con solo poner "Startx" cambiaba a modo grafico, sin embargo aqui no ocurre, me dice que dicho comando no existe o algo por el estilo.

alguien podria ayudarme con esto?, e instalado varios SO linux y nunca pase por este problema.

Por lo visto en todos los tutoriales online que eh consultado entra directo a modo grafico.

---

### Post by Hei Ku on 2009-01-04
algo no le gustó con el modo gráfico.

Probaste con:
```

sudo dpkg-reconfigure xserver-xorg -phigh

```

o sino, si lo instalaste con gnome, probá:

```

sudo /etc/init.d/gdm start

```

---

