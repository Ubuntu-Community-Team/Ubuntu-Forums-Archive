---
title: "Problemas con conexion a Internet en Ubuntu 10.10"
date: 2011-03-23
forum: Software
---

### Post by unamierda on 2011-03-23
Hola a todos! Este es mi primer ingreso y ya tengo miles de dudas con este sistema operativo. Pero ahora vengo a explicar con mi conexion a Internet en Ubuntu.

En Windows 7 anda genial, pero inicializo Firefox y tarda mucho en conectarse al sitio, pero en descargar y todo eso es rápido. Luego me dijeron que deshabilite IPv6 en Firefox y soluciona mi problema, pero no del todo, por ejemplo en Empathy, Gwibber y Google Earth tarda mucho. Como soluciono esto? Gracias.

---

### Post by biale on 2011-03-23
Hay una manera de desabilitar IPv6 para toda la máquina. Pero esa manera ha ido variando con las versiones y de memoria no me acuerdo. Involucra el cambio de un parámetro en uno de los archivos de sistema: Googlea con disable IPv6 Maverick

En otro orden de cosas, al pasar a FFox 4.0 la diferencia de velocidad se nota.

---

### Post by biale on 2011-03-23
Al menos para Lucid se puede hacer así

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html/](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html/)

Yo edite el archivo /etc/sysctl.conf a mano, no use los comandos de consola. Y si no anda bien facil de volver atras.

Lineas agregadas al final del archivo:

```

# 140610 - Agregado a Lucid para desabilitar IPv6
# disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

---

