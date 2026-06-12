---
title: "Ayuda con un script bash"
date: 2010-02-03
forum: Software
---

### Post by ramiro_md on 2010-02-03
Hola a todos, bueno les comento que toy tratando de resolver el siguiente ejercicio 

    Realizar un script que reciba como parámetro una extensión y haga un reporte
con 2 columnas, el nombre de usuario y la cantidad de archivos que posee con esa
extensión. Se debe guardar el resultado en un archivo llamado reporte.txt


Bueno mi problema esta a la hora de enlistar en 2 columnas, porque la idea seria que aparecieera de la siguiente forma

UsuarioX      10
UsiarioXX     20


yo he logrado contar la cantidad de archivos con esa terminacion por usuario...pero no logro imprimir el usuario q los posee , en 2 columnas...les dejo aca el script q hice

> #!/bin/bash
cd /home
for i in $(ls);do
	ls | find -user $i -name *$1 | wc -l 
	
done


agradeceria enormemente una ayuda!
desde ya muchas gracias,
Saludos



Aclaracion: lo del reporte en txt lo obvie porq mi problema es el ya comentado

---

### Post by macardos on 2010-02-05
Hola, Ramiro.

Ante todo te aclaro que soy docente y no puedo sacarme eso de encima, por lo que no te doy directamente el comando ni el script resuelto sino pistas para que consigas hacerlo.
Entre paréntesis, ¿quiénes son tus docentes de sistemas operativos?

Acá va la explicación:

No entiendo para qué volvés a hacer "ls" antes de contar los archivos, ya que se supone que estás dentro del for trabajando para un usuario particular y que es el for el que te asegura que trabajás con todos. Eso se nota en que usás el nombre del usuario correctamente en el find.
Lo que yo haría es guardar en una variable el resultado de la ejecución del pipe, para después armar las 2 columnas con las 2 variables y un par de tabuladores en el medio.
Para "imprimir" todo fijate en el man del bash que tiene que estar un comando "echo" o similar, y fijate bien como indicarle que ponga el tabulador.

Ah! Una aclaración: el ejercicio te pide que los archivos tengan una "extensión" dada, no que sus nombres terminen con ese dato. Eso significa que deberías buscar "*.$1" en lugar de "*$1", ya que es el punto el que te garantiza que la terminación es la extensión; de lo contrario estarías contando algo como "deftxt", que no tiene extensión txt mi minguna otra.

Cualquier cosa, aquí estaré.

---

### Post by macardos on 2010-02-05
Por si no quedó claro en el post anterior, en el pipe deberías eliminar el "ls" para que funcione lo que te dije.

Sorry.

---

### Post by ramiro_md on 2010-02-06
Gracias por tu ayuda, pero mi ejercicio ha dado un vuelco importante, tengo que listar de todos los usuarios, osea todo lo que aparezco en /etc/passwd.
intente una solucion, pero si bien imprime bien...no da el resultado que yo quiero y no puedo entener el por que?
dejo aca el script a ver si me podes guiar!


#!/bin/bash
a=*`cat /etc/passwd | cut -d ":" -f1`
for i in $a; do
	var=`find -user $i -name *.$1 | wc -l`
	echo $i $var
done		



en si no cambio mucho...pero al ejecutarlo, pasandole como parametro "conf" imprime lo siguiente



*root 0
daemon 0
bin 0
sys 0
sync 0
games 0
man 0
lp 0
mail 0
news 0
uucp 0
proxy 0
www-data 0
backup 0
list 0
irc 0
gnats 0
nobody 0
libuuid 0
syslog 0
messagebus 0
hplip 0
avahi-autoipd 0
avahi 0
couchdb 0
haldaemon 0
speech-dispatcher 0
kernoops 0
saned 0
pulse 0
gdm 0
gus 0
polkituser 0
pepe 0


y se que hay archivos .conf minimo en el directorio gus, pero no lo encuentra...

---

### Post by macardos on 2010-02-08
2 cosas:

1) Creo que se te escapó un * justo antes del cat en la asignación de a, por lo que el primer directorio te sale "*root" en lugar de "root".

2) Probá a ejecutar el find con y sin el wc, pasandole los datos concretos de algo que sabes que tiene que pasar. Por ejemplo, yo hice sobre mi usuario la busqueda de txt para ver que daba.
Parece ser que el tema es que estas asignando el codigo de retorno exitoso (0) y no la cantidad de cosas que hay.

---

