---
title: "Compiz se desconfigura cuando lo cierro"
date: 2010-11-13
forum: Software
---

### Post by FenxD on 2010-11-13
Buenas, hay alguna forma de que el compiz no se desconfigure todo cuando lo cierro y lo vuelvo a abrir?

Tengo que cerrarlo porque se me hace imposible jugar al gta3 sino(ya se que linux no es para los juegos, pero no me interesan los juegos NUEVOS, y el gta3 me lo tire re bien con el wine), pero es medio embolante configurarlo devuelta después.

alguna solución?

---

### Post by hectorivand on 2010-11-18
> **FenxD said:**
> Buenas, hay alguna forma de que el compiz no se desconfigure todo cuando lo cierro y lo vuelvo a abrir?

Tengo que cerrarlo porque se me hace imposible jugar al gta3 sino(ya se que linux no es para los juegos, pero no me interesan los juegos NUEVOS, y el gta3 me lo tire re bien con el wine), pero es medio embolante configurarlo devuelta después.

alguna solución?

Hola FenXD, intentaré dar luz sobre el asunto...

Tal vez el archivo de configuración está jodido, así que proba con borrar la siguiente carpeta.:

```
/home/usuario/.compiz
```

Después de hacerlo, volve a instalar Compiz Manager.:

```
sudo apt-get install compizconfig-settings-manager
```

Saludos
Nacho

---

