---
title: "problema con actualizacion midori"
date: 2010-01-15
forum: Software
---

### Post by serbesa on 2010-01-15
Hola, tengo un pc edio viejo, xubuntu con lxde, instale midori, y intenet actualizarlo agregando estos repositorios
sudo add-apt-repository ppa:midori
sudo add-apt-repository ppa:webkit-team
 que lo saqué de este blog [http://noctuido.wordpress.com/2009/10/07/midori-en-ubuntu-9-04-en-sus-mas-recientes-versiones/](http://noctuido.wordpress.com/2009/10/07/midori-en-ubuntu-9-04-en-sus-mas-recientes-versiones/)

pero al colocar $ sudo apt-get install midori
sale:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  midori: Depende: libwebkit-1.0-2 (>= 1.1.16) pero 1.1.15.2-1 va a ser instalado
E: Paquetes rotos

no se que hacer y me preocupa tener paquetes rotos...

---

### Post by Carlos C on 2010-01-15
> sudo add-apt-repository ppa:webkit-team

¿Necesitas este ppa?

---

### Post by Carlos C on 2010-01-15
Tienes un problema de dependencias y me da la impresión que es un error en el empaquetamiento del ppa, porque intenté instalarlo y me ocurrió lo mismo. Es la versión inestable, así que tienes que esperar un poco, seguro que lo arreglan pronto. No se alcanza a instalar nada así que no hay problema, puedes verificarlo escribiendo 
```
sudo dpkg -C
```
verás que no te entrega ningún resultado.

Mientras tanto puedes desactivar ambos ppa de tu lista de repositorios y mantener la versión 0.1.9-0 que está en los repositorios oficiales.

Saludos.

---

