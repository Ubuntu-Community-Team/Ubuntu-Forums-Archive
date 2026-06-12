---
title: "Prueben OPERA 10, recomendacion para todo el que siente lento firefox"
date: 2009-09-15
forum: Software
---

### Post by AlexDDR on 2009-09-15
He creado este post para que todos los que lo vean le den una prueba Opera 10

He estado probandolo los ultimos dias y creo que es el navegador completamente funcional (mencion a chrome) más rapido y con menos consumo de recursos que está disponible para linux Ubuntu.

He probado tanto la version en QT4 como la en QT3 que es la oficial, y debo decir que la qt4 aun le falta en estabilidad que debe ser la razon por que la oficial sigue siendo en qt3.

Pasa el acid3 con 100/100

y carga correctamente el sitio de emol y no se sobrecarga con los script de peliplay u otros sitios con script pesados, com olo hace firefox

De momento lo unico qu eno me ha funcionado es el cargador de imagenes de JAVA en facebook

Syncroniza tus marcadores con los servidores de opera, y con Unite puedes compartir archivos directamente como un servidor web, tal como se puede hacer con MEIGA ([http://www.visualbeta.es/11525/linux/meiga-una-forma-sencilla-de-compartir-archivos-en-linux/](http://www.visualbeta.es/11525/linux/meiga-una-forma-sencilla-de-compartir-archivos-en-linux/))



el link de descarga es el siguiente para los que no lo conocen

[http://www.opera.com/](http://www.opera.com/)

---

### Post by Fisaulerod on 2009-09-16
Yo tambien recomiendo Opera 10, eso si la version en QT4, que a mí me funciona bastante bien. Se integra muy bien en el escritorio de gnome, siendo más bonito (a mi gusto) que Firefox y Chrome. Si bien ocupa más recursos, al momento de utilizarlo y cargar páginas se nota más ligero que Firefox, además en mi opinión es un mejor navegador (lástima que no sea libre). Eso..pruebenlo xD.

P.D: Aquí esta la version en QT4 en un paquete deb: [http://ftp.opera.com/pub/opera/linux/1000/final/en/i386/](http://ftp.opera.com/pub/opera/linux/1000/final/en/i386/)

---

### Post by por100pre1 on 2009-09-16
Saludos, si quieren mantener Opera actualizado agregen el repositorio de Opera:

En terminal añaden la clave GPG de Opera:

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```

y luego abren 

**Sistema > Administración > Orígenes del Software**

y en la pestaña **Software de Terceros**

añaden la siguiente linea:

```
deb http://deb.opera.com/opera/ sid non-free

```

Y finalmente presionar **Cerrar** y entonces recargar los repositorios.

Si aún no tienen Opera instalado entonces:

```
sudo apt-get install opera
```

---

