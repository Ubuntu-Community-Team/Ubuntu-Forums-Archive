---
title: "Backup de notebook Ubuntu en desktop win"
date: 2009-10-23
forum: Software
---

### Post by jorgito on 2009-10-23
Hola a todos, 

Tengo una notebook con 8.04 y una desktop con w2k.
Lo que quiero hacer, es hacer backups de mi home en la desktop, donde tengo bastante lugar disponible.
Win no ve la notebook en la red. Supongo que samba no esta en condiciones. De hecho, si corro nautilus con sudo da algun mensaje de error relativo a eso.
Puedo ver la desktop desde la notebook de dos maneras: 
1.- Conectando con el servidor (parece servirle solo al nautilus)
2.- Montando la desktop en la estructura de archivos con smbmount.

Ahora la parte del backup: naufrague entre las opciones de la linea de comando del rsync. No pude dar pie con bola para hacer el backup.
Intente con el unison2.13, y lo unico que consigo es (cuando tengo montada la desktop y puedo configurar origen y destino como locales) que arranque el proceso, compare diferencias entre los directorios y que cuando quiero que haga el backup aborte diciendo:

Error in setting permissions:
Operación no permitida [chmod(/mnt/OtraPC/minitest/.#puntos2.9461b871185f9fc55e0589e565d47b26.unison.tmp)]

Intente tambien usar el unison en modo socket, pero si tengo unison unison 2.28 corriendo como server en la desktop me dice que las versiones son incompatibles. Si pongo a correr un unison2.13 en la desktop, directamente no se conecta.

Alguna idea? 
Fracase con el rsync porque hay algo mal en el concepto? (del tipo "muchacho, no podes copiar los archivos de ubuntu en una maquina win")
Como arreglo esto?

---

### Post by EnriqueK on 2009-10-23
Mirá, nunca he operado en red y de samba solo se que es mñusica de carnaval, pero si vos podés abrir un terminal en la PC win , mediante el comando cd , podrás crear un archivo tar.gz , de esa manera vas a poder guardar en una particióin de windoes, por ejemplo sería algo así
cd ruta_carpeta_en _win
sudo tar czvf rerspaldo.tar.gz /home/$USER

---

### Post by jorgito on 2009-10-23
Gracias Enrique!

Con ese metodo cada vez que quiero hacer el backup tengo que regenerar el .tar.gz completo? Y transferirlo completo?
Mi home completo son unos 14 gigas y la vez que lo hice tardo una eternidad...

Gracias de nuevo

---

### Post by EnriqueK on 2009-10-23
Si, tenés que hacerlo completo, pero si tenés muuuucho espacio disponible en la PC con win, podés obviar la compresi&#7765;n , o sea en vez de poner tar czvf ------  ponés tar cvf . Otra posibilidad que se que existe pero que nunca ensayé, es que uses el comando _dar_ , buscaá en Google por "comando dar" , permite hacer respaldos incrementales, a dar lo encontrás en los repositorios
[http://dar.linux.free.fr/doc/mini-howto/dar-differential-backup-mini-howto.es.html](http://dar.linux.free.fr/doc/mini-howto/dar-differential-backup-mini-howto.es.html)

---

### Post by biale on 2009-10-23
Posicionado en la notebook correría directamente un "tar", pero sin compresión para ahorrar tiempo. En cuanto a la performance no encontré ventajas usando "dar" y lo discontinué.

Tar en una Pentium simple 2,4 Ghz, desde Linux, home de unos 15 Gb, y hacia un disco USB 2.0, resuelve en menos de una hora. 

He corrido Unison y es bastante quisquilloso con los permisos. Muy práctico según los casos, pero puede tardar un monton de tiempo. 

Saludos

---

### Post by EnriqueK on 2009-10-23
Justamente por lo que estás comentando es que a mi no me gusta tener una carpeta de usuario con configuraciones y documentos, estos no tienen límite y con seguridad en algún momento vas a tener problemas para hacer respaldos, por eso es que tengo una partición /home pequeña para tener allí mi carpeta de usuario con mis configuraciones y además tengo otra partición de gran tamaño para tener allí todos los documentos, el respaldo de estos los hago de forma simple mediante DVDs , poco a poco mientras transcurre la historia , el respaldo de mi carpeta de usuario lo hago cpmo lo expliqué al principio (generando un .tar.gz).
Si ya tenés /home separada y no querés crear otra partición , lo que podés hacer es crear en /home , pero ojo, no dentro de la carpeta de usuario. sino en /home, una carpeta y poner allí todos tus documentos, le das tus permisos a esa carpeta y creas dentro de tu carpeta de usuario enlaces simbóllicos a las diferentes sub carpetas de documentos, de esa manera vas a poder crear respaldos de tus configuraciones con un peso mínimo y a los documentos los respaldas  de una forma tradicional y simple.

---

### Post by jorgito on 2009-10-24
Bueno, en lo del /home separado estoy de acuerdo, ahora que llevo un par de años usando Ubuntu. En el momento que arranque con esto acepte el default y aca me tenes: el que no sabe es como el que no ve.
Una de las cosas por la que estoy planeando backups como la gente es que pienso hacer una instalacion limpia con la proxima LTS. Ahi usare un home separado y pasare a ext4.

Biale: Muchas gracias. Como siempre fracaso miserablemente leyendo man tar. Y el otro extremo es un pdf con 230 páginas para aprender a usar tar desde cero (que de todos modos estoy leyendo). Deberia encontrar algo intermedio.

Saludos y gracias!

---

### Post by biale on 2009-10-25
Jorgito:

Tar es extremadamente sencillo de usar: comando, opciones vetustas, hacia adonde, desde donde".

Este es el script que uso arrancando live el SystemRescueCd (no existe el "sudo"):

```

tar -cvpf  /mnt/sdc2/Ubuntu-home.tar  --totals		        \
	  --exclude=Ubuntu-home.tar   --exclude=/mnt/sda5/NADA  \
	   /mnt/sda5   	     > /mnt/sdc2/Ubuntu-home.tar.out1

```

En este caso los dos" exclude" no hacen nada util, "totals" es un chiche.
Al último y con la redirección ">" salvo el listado de los archivos guardados, también lo podes sacar sin problemas.

Solo acordate que la "f" indica que lo sigue es el archivo de salida. O sea que es un parámetro posicional, o sea que no debe alterarse su posición.

Y lo único que complica la existencia es el indicar bien los caminos de lectura y escritura. Fijate en el ejemplo que hay una partición ya montada desde antes en "/mnt/sdc2" 

Con el mismo criterio mi home completo se encuentra (montado) en "/mnt/sda5". 

Luego el script sigue con algunas otras delicadezas mas y las he omitido.

---

