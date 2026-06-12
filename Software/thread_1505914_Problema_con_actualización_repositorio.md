---
title: "Problema con actualización repositorio"
date: 2010-06-09
forum: Software
---

### Post by ketzelleshelle on 2010-06-09
Me sale un ícono triángulo rojo con signo de exclamación en la barra superior, que me dice que hay índices de repositorios que no pueden descargarse ya sea por que están obsoletos o porque hay un problema en la conexión. Como la segunda opción no es, intuyo que tiene que ver con la primera y me sale este aviso:

Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  No pude conectarme a archive.getdeb.net:80 (81.92.203.249). - connect (110: Expiró el tiempo de conexión)
Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-es.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-es.bz2)  Imposible conectar a archive.getdeb.net:http:
Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Imposible conectar a archive.getdeb.net:http:
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

El problema es que el ícono sigue apareciendo, no encuentro forma de quitarlo y/o solucionar el inconveniente...

Alguna ayuda?

Muchas Gracias!

---

### Post by guillermolisi on 2010-06-09
Los repositorios de GetDeb estan caidos desde hace unos dias a la fecha, por eso los errores.

Si los excluis de tus actualizaciones no deberias tener problemas y veras que desaparece el aviso que te molesta.

---

### Post by Cajuma on 2010-06-10
Hola:
Si alguien necesita actualizar GetDeb, pueden hacerlo desde los mirrors de Irlanda, son los utilizados por Clem el creador de Mint. Son seguros, los estoy utilizando desde que se cayeron los oficiales.

```
sudo gedit /etc/apt/sources.list, comentar los repos de Get Deb y agregar los siguientes:                                   

deb http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu lucid-getdeb apps

deb http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu lucid-getdeb games
```

Saludos....:p

---

### Post by ketzelleshelle on 2010-06-11
Gracias Guillermo y Cajuma!

---

