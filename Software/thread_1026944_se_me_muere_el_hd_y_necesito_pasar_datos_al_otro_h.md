---
title: "se me muere el hd y necesito pasar datos al otro hd"
date: 2008-12-31
forum: Software
---

### Post by dj_isaco on 2008-12-31
hola gente aca les hago esta consulta ya que stoy en un aprieto
mi situacion es la siguiente.
tengo dos discos uno sata 160gb,con 2 particiones (ntfs), y el otro ata160g,  3 particiones (ext3) y 1 (ntfs).
el hd q se esta mal es el ata en el tengo instalado ubuntu 7.10 y xp, Luego de intentar reinstalar xp varias veces sin poder hacerlo tome la precaucion de ver el stado del disco ya q tambien me daba error en ubuntu al iniciar, y me di cuenta q el era el disco y no los S.O.

me gustaria q me ayuden a salvar los datos q tengo en una particion del disco sata para poder ahi instalar un S.O. por lo menos hasta q compre otro hd.
la config el la sigueinte (sata lo usaba para poner mis documentos anda bien)
2 partciones
la primera de 30gb aprox
la segunda 130gb aprox (espacion libre 90gb)

acabo de reinstalar ubuntu y se instalaron mal algunos archivos y cuando quiero actualizar me dice q el indice de software esta dañado
cuando ejecuto "sudo apt-get install -f" no me corre me tira este error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

y no me deja installar nada ni correr Synaptic este error me tira

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

saludos y espero q me puedan ayudar y asi pueda empezar un año con mi pc andando
felices fiesta a todos
:KS

pd: si me pueden ayudar a leer y escribir en elos discos ntfs ya q nunca pude hacerlo

---

### Post by Hei Ku on 2009-01-01
Para resolver el problema de Synaptic, en una consola pone:

```

sudo dpkg --configure -a
sudo apt-get update

```

No entiendo qué es lo que queres hacer exactamente. Copiar los datos a la otra partición? Crear una particion tomando el espacio libre de las otras?

Para escribir en ntfs, instalá el paquete ntfs-3g, aunque deberías tenerlo por defecto.

---

### Post by dj_isaco on 2009-01-02
gracias hei ku por el comando ya sta salucionado
 ahora cuando intento acceder al disco con las particiones ntfs
me tira esto error

[[IMG]http://img58.imageshack.us/img58/8093/pantallazognomemountcvz7.th.png[/IMG]](http://img58.imageshack.us/my.php?image=pantallazognomemountcvz7.png)

mi intension es liberar una particion de este disco para asi poder instalar los S.O. en el ya q tengo muchos datos en ella y no los quiero perder por eso no quiero formatearla

---

### Post by Hei Ku on 2009-01-02
Lo que te dice es que la particion NTFS no se desmonto de manera limpia. Si podes iniciar en Windows y cerrarla bien, mejor. Si no, podes forzar el montaje con las instrucciones que te da ahi.

---

### Post by dj_isaco on 2009-01-02
no puedo entrar al windows ya q el disco donde tenia instalados los so se rompio y no puedo reinstalarlo se claba al 20% de la instalacion y no pasa de ahi
instale de nuevo ubuntu pero anda con muchos errores no puedo instalara o descargar nada gde ya q se clava o se corrompe los archivos.
y como lei en otro post al forzarlo corro el riesgo de perder todo o no es mi caso?

---

### Post by Hei Ku on 2009-01-02
si solamente vas a leer de esa particion, no creo que corras un gran riesgo. Ese tipo de proteccion son para escritura.

---

