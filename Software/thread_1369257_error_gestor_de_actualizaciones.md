---
title: "error gestor de actualizaciones"
date: 2009-12-31
forum: Software
---

### Post by marceze on 2009-12-31
holas! gente! tengo un problemon al tratar de actualizar mi ubuntu, en el gestor de actualizaciones, me aparece esto:



------------------gestor de actualizaciones------------------
No se pudieron descargar todos los índices de los repositorios

El repositorio quizá no esté disponible o no se pudo contactar con él por problemas en la red. Si hay disponible una versión más antigua del índice que falló, se usará esa versión. En caso contrario el repositorio se ignorará. Compruebe su conexión de red y que la dirección del repositorio esté escrita correctamente en las preferencias.
                            ------------------------
Imposible obtener [http://ppa.launchpad.net/dnaz88/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/dnaz88/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

----------------------------------------------------------------


No se si alguien mas tuvo este problema, ya intente de todo y no logro solucionarlo...

gracias de antemano!

---

### Post by kamus on 2009-12-31
> **marceze said:**
> holas! gente! tengo un problemon al tratar de actualizar mi ubuntu, en el gestor de actualizaciones, me aparece esto:



------------------gestor de actualizaciones------------------
No se pudieron descargar todos los índices de los repositorios

El repositorio quizá no esté disponible o no se pudo contactar con él por problemas en la red. Si hay disponible una versión más antigua del índice que falló, se usará esa versión. En caso contrario el repositorio se ignorará. Compruebe su conexión de red y que la dirección del repositorio esté escrita correctamente en las preferencias.
                            ------------------------
Imposible obtener [http://ppa.launchpad.net/dnaz88/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/dnaz88/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

----------------------------------------------------------------


No se si alguien mas tuvo este problema, ya intente de todo y no logro solucionarlo...

gracias de antemano!

Efectivamente ese repositorio ppa esta con problemas (borraron el contenido probablemente) por eso te aparece ese mensaje. Lo mejor sera que elimines ese ppa de tu lista de repositorios y ocupes un mirror oficial para actualizar tu sistema.

Saludos

---

### Post by marceze on 2009-12-31
ohhh!! muchisimas gracias por contestar! ya me estaba asustando!
un pedido más, ¿como hago para eliminar ese ppa de la lista de repositorios? y ¿como utilizo uno oficial? como hago para solucionarlo?? 
gracias, de nuevo, por contestar tan rápidamente!

edito-------------
desde orígenes del software des tilde el [http://ppa.launchpad.net/dnaz88](http://ppa.launchpad.net/dnaz88), pero, como hago para utilizar uno oficial??

---

### Post by marceze on 2010-01-11
Nadie me puede explicar como hacer para usar repositorios oficiales o que funcionen?? estoy teniendo muchos problemas y creo que es debido a esto.

---

### Post by guillermolisi on 2010-01-11
> **marceze said:**
> Nadie me puede explicar como hacer para usar repositorios oficiales o que funcionen?? estoy teniendo muchos problemas y creo que es debido a esto.
Para determinar si efectivamente tenes problemas con la lista de repositorios, lo mejor seria que nos muestres como esta actualmente y en base a eso te sugerimos que cambiar, que dejar, que agregar y que quitar.

Para mostrarnos la lista: ```
less /etc/apt/sources.list
```copias y pegas en un nuevo mensaje la salida que obtengas

Tambien y por las dudas, mostranos el contenido de /etc/apt/sources.list.d copiando y pegando la salida que te de ```
ls -al /etc/apt/sources.list.d
```

---

### Post by marceze on 2010-01-11
Muchas gracias, guillermolisi, por contestar!:D pero ya lo solucione! tenia varios problemas, inclusive en el inicio del sistema! y en su mayoría debido a el gnome do... que por supuesto desinstale y por suerte ahora el sistema funciona de maravillas... además de un par de problemas de estos repositorios que ya solucione, cambiándolos... principalmente con unos de sonic roboblast 2 y unos translate-es que los solucione actualizando mi soporte de idiomas...
Así que muchas gracias de todas formas!

---

