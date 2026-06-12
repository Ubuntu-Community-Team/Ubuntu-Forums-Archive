---
title: "grub piensa que tengo XP y no aparece el win7 :O"
date: 2010-02-19
forum: Software
---

### Post by sebatectura on 2010-02-19
Saludos a todos,  tengo un pqño problemita que no he podido encontrar solucion, soy semi novato ni tan semi que digamos.

Resulta que tengo un Acer Apire 4520, Athlon 1,9 X2 64bit, 3gb Ram, 160 gb de disco duro, y lo tenia con XP Y UBUNTU 9.04. Hasta que pisé el palito y me decidí a probar el WIN7 que de verdad mejoró bastante, sin dejar de ser s-h-i-t , el asunto es que obviamente perdí el grub en el proceso, por lo que dejé botado el ubuntu como 6 meses, trabajando en Autocad, (que solo anda en window$ ). Ahora en verano con mas tiempo, me decidí a recuperar mi acceso al UBUNTU y lo logrè hacer. El asunto es que el grub sigue dandome acceso al xp que ya no existe, y no me sale el win7, que es donde esta todo mi trabajooo aaaaaaaaaa 

mi olfato de novato me dice que no es complicado de arreglar, dehecho creo que alguna ves edite algún .bat o .sys pero no he podido encontrar como lo hice esa vez.

Esooo ojala me puedan ayudar, estaré atento, muchas graciassss


BendiZión.oOo.o

---

### Post by Carlos C on 2010-02-19
Hola. Por favor recuerda siempre publicar tus dudas en el subforo adecuado. Cuando no estés seguro de dónde hacerlo puedes mirar [aquí]("http://ubuntuforums.org/showthread.php?t=1319475").

Sobre tu problema, la manera de solucionarlo depende de si usas GRUB o GRUB2. Puedes encontrar información respecto al tema en la Guía Ubuntu:

[http://www.guia-ubuntu.org/index.php?title=Grub](http://www.guia-ubuntu.org/index.php?title=Grub)


Saludos.

---

### Post by sebatectura on 2010-02-19
> **Carlos C said:**
> Hola. Por favor recuerda siempre publicar tus dudas en el subforo adecuado. Cuando no estés seguro de dónde hacerlo puedes mirar [aquí]("http://ubuntuforums.org/showthread.php?t=1319475").

Sobre tu problema, la manera de solucionarlo depende de si usas GRUB o GRUB2. Puedes encontrar información respecto al tema en la Guía Ubuntu:

[http://www.guia-ubuntu.org/index.php?title=Grub](http://www.guia-ubuntu.org/index.php?title=Grub)


Saludos.

oops, creí haberlo puesto en "novatos" o algo asi, pido las disculpas del caso

con respecto al tema, lo solucione asi:

Lo que hice fue editar el archivo menu.lst ubicado en /boot/grub/menu.lst, primero hice un backup porsiacaso, y edite la ultima linea donde salen los otros sistemas operativos, copiando esas lineas varias veces y cambiandole el numero del disco a cada uno para probar.

editar el menu.lst:

sudo gedit /boot/grub/menu.lst

una vez ahi, al final de una gran lista de lineas de comando sale algo como esto:

[b]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows SEVEN
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/b]

solo que en ves de decir eindows seven decia xp y donde dice root (hd0,0) decia (hd0,1), asi que copie esas lineas que puse en negrita  4 veces para abajo, y a cada una le cambie ese numerito (pues en ese momento yo no sabia cual iba a funcionar)

al reiniciar, el grub me daba muchas opciones de windows y las fui probando una por una, cuando ya sabes cual es la que te funciona, vuelves a editar el menu.lst y borras las que sobran y LISTOO!!!


ojala le sirva a alguien


adioss

---

