---
title: "monkey messenger"
date: 2008-07-30
forum: Software
---

### Post by ramiro_md on 2008-07-30
Gente, he decidido probar este nuevo mensajero (monkey messenger), resulta que bajo el codigo fuente desde su pagina [http://monkeymessenger.sourceforge.net](http://monkeymessenger.sourceforge.net), la cuestion es que al descargarlo e ingresar a su carpeta (desde consola) una vez ejecutado el autogen.sh en una linea me tira el siguiente error "configure: error: No C# compiler found
". Si alguien podria darme una mano se lo agredeceria =). Aclaro que lo primero que hice fue ver si tenia instalado el CCG (Compialdor de C de GNU) y efectivamente esta instalado =S. Un saludo.

---

### Post by Mauro22 on 2008-07-30
Leiste el blog de ese IM??

Fue abandonado hace 2 años casi... pero el codigo lo dejo por si alguien quiere seguir con el proyecto bajo otro nombre...


Aun compilandolo no vas a tener algo "nuevo"



EDITO:

Lo compile y no me gusto, es parecido a emesene... tiene soporte para enviar/recibir archivos, la estetica es casi la misma, etc etc etc, no se si soporta webcam. Esta en ingles y... miralo vos mismo:

Me tiro ese error tambien, instalá:
* monodevelop
* mono-gmcs

y editar el archivo configure y cambiar:

```
if test ! -e `$PKG_CONFIG &#8211;variable=prefix mono`/lib/mono/2.0/$asm.dll; then
 

por 



 if test ! -e /usr/lib/mono/2.0/$asm.dll; then

Sacado de: http://nibblesmx.dimono.com/archives/226

```


Despues make y luego make install

---

### Post by ramiro_md on 2008-07-30
Ah bueno, gracias !, ya que me decis todo eso ni lo pruebo y sigo con amsn. Un saludo y gracias =)

---

