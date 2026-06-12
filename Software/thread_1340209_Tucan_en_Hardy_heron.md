---
title: "Tucan en Hardy heron"
date: 2009-11-28
forum: Software
---

### Post by Criminel on 2009-11-28
¿Podrían informarme si Tucan funciona bajo Hardy? (no parece estar en los repositorios). De no ser así, ¿hay algún programa similar que no sea JDownloader?

Gracias.

---

### Post by gmunioz on 2009-11-28
Hola cri.....:

Prueba descargar el .tar.gz e instalarlo.

[http://forja.rediris.es/frs/download.php/1470/tucan-0.3.9.tar.gz](http://forja.rediris.es/frs/download.php/1470/tucan-0.3.9.tar.gz)

---

### Post by Tosh78 on 2009-11-29
Si, yo lo tuve funcionando. Podes fijarte en la pagina [www.getdeb.net](www.getdeb.net)
Yo en los repositorios no lo encontre, asi que me baje el .deb de alguna pagina. En este momento no recuerdo si fue esta o no, pero a mi me funciono perfectamente en su momento.

---

### Post by Applelnx on 2009-11-29
Fijate si te sirve:

[http://www.getdeb.net/updates/tucan](http://www.getdeb.net/updates/tucan)

Podes bajarte el archivo .deb o instalar el repositorio:

> Go to System-Administration-Software Sources, Third-Party Software tab, Add:
```
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```

Add the repository GPG key, open a terminal window and type:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

---

### Post by Criminel on 2009-11-30
Gracias a todos. Probaré las sugestiones prontamente.

---

### Post by Criminel on 2009-11-30
La URL «apt:tucan?refresh=yes» indicada es incorrecta; saliendo
Ese es el mensaje que obtengo desde getdeb.

¿Alguna idea?

---

### Post by Applelnx on 2009-11-30
> **Criminel said:**
> La URL «apt:tucan?refresh=yes» indicada es incorrecta; saliendo
Ese es el mensaje que obtengo desde getdeb.

¿Alguna idea?

Perdon, ese error salta cuando lo tratas de instalar desde el repositorio o tratando de bajar el archivo .deb?

---

### Post by Criminel on 2009-12-01
Ese error salta cuando trato de instalarlo desde el link para bajart el archivo deb.
Desde el repositorio el programa parece bajar, pero a la mitad de la instalación tira errores de que le falta algo y no puede continuar (estoy fuera de casa, cuando llegue trato de copipastear el error exacto en este segundo caso).
En ambos casos no parece funcionar bajo Hardy.

---

### Post by Kabezon on 2009-12-02
Funciona perfectamente en Hardy, la PC de mi hermana sigue con Hardy y va de 10. Bajate directamente el [source]("http://forja.rediris.es/frs/download.php/1470/tucan-0.3.9.tar.gz"), instalarlo es facilísimo:

- Descomprimi el tar.gz
- Abrí una terminal
- $ cd lugar del archivo (ej: cd Desktop/tucan-0.3.9)
- $ sudo make install
- Lo encontas en Aplicaciones > Internet > Tucan Manager

Por si no podés bajar de Megaupload:

$ sudo apt-get install python python-gtk2 python-imaging tesseract-ocr tesseract-ocr-eng librsvg2-common

Cualquier cosa, chiflá :D

---

### Post by Criminel on 2009-12-02
root@drutus-desktop:/home/drutus# $cd Escritorio/tucan-0.3.9
bash: Escritorio/tucan-0.3.9: es un directorio
root@drutus-desktop:/home/drutus# 

Eso es el mensaje de terminal que me sale luego de seguir tu primer paso (tengo el tar desempaquetado en Escritorio). 
Seguramente algo hago mal, pero no puedo darme cuenta de qué es.

---

### Post by Kabezon on 2009-12-03
Te dejo un pantallazo, así entendés bien como seguir los pasos.

---

### Post by Criminel on 2009-12-03
Ahora sí!
Gracias.

---

### Post by Kabezon on 2009-12-03
De nada. No te olvides de tirar también:
```
sudo apt-get install python python-gtk2 python-imaging tesseract-ocr tesseract-ocr-eng librsvg2-common
```

---

### Post by shimoda on 2009-12-09
Muchas gracias... Yo también lo andaba buscando...

saludos!

---

