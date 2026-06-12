---
title: "Una pregunta facil, facil."
date: 2008-10-16
forum: Software
---

### Post by victor_nesta on 2008-10-16
en terminal hago un ls de una carpeta con varias subcarpetas.
La pregunta es si se puede, hacer un ls para que quede en arbol, maso menos así.

Musica-------|
             Reggae---------|
             |              Toot and the Maytals
             |              Bob marley
             |              Alfa Blondy
             |              Otro mas
             Tango-------|
             |           Pugliese
             |           Gardel
             |           Centella (como cantaba este por dio) 
             |
             Cumbia Villera------|
                                 (Directorio Vacio)   

etcetera, etcetera.

Para que? Es para hacer un print e enviarlo por mail.

---

### Post by chalito on 2008-10-16
sudo apt-get install tree

:)

---

### Post by santiagoward2000 on 2008-10-16
```
ls -R
```
Ahí te tira todas carpetas y archivos. (Aunque no queda muy ordenado)

---

### Post by victor_nesta on 2008-10-16
jaja Vieron que era re-facil. No, si yo lo había leído por ahí.
Gracias Chalito

Edito por que no lo vi: Gracias santiagoward2000, o santi B)

---

### Post by pol666 on 2008-10-16
rm /home/música/cumbia villera ^^

---

### Post by santiagoward2000 on 2008-10-16
> **victor_nesta said:**
> jaja Vieron que era re-facil. No, si yo lo había leído por ahí.
Gracias Chalito

Edito por que no lo vi: Gracias santiagoward2000, o santi B)

De nada!! Pero me gustó más la forma de Chalito! :)

---

### Post by guisheca on 2008-10-16
WAW!! que buena herramienta!!

---

### Post by ramiro_md on 2008-10-16
che cómo hago para acceder a una carpeta que de nombre tiene varias palabras ? es decir por ejemplo: /home/ramiro/archivos de la facu. Si le doy cd me dice que no existe el directorio :O

---

### Post by victor_nesta on 2008-10-16
con comillas simples ' 
cd 'pedro es mi amigo'
victor@nesta-desktop:~/Escritorio/pedro es mi amigo$

---

### Post by guisheca on 2008-10-16
> **victor_nesta said:**
> con comillas simples ' 
cd 'pedro es mi amigo'
victor@nesta-desktop:~/Escritorio/pedro es mi amigo$

Y sigo aprendiendo, gracias!!

---

### Post by sherwoodinc on 2008-10-16
Me desasnaron con lo de las comillas simples.
Yo hasta ahora lo venía haciendo anteponiendo un a barra '\' al espacio en el nombre:

/home/yo/mis archivos locos

se escribe como

yo@localhost:~$ cd /home/yo/mis\ archivos\ locos

---

### Post by faktorqm on 2008-10-17
> **pol666 said:**
> rm /home/música/cumbia villera ^^

No te equivoques! es asi el comando:

```
sudo rm -rf /home/música/cumbia*
``` :KS

Bue, lo del caracter de escape tambien lo explique en otro post, alcanza con apretar la tecla TAB para autocompletar el directorio cuando escribis cd blaba. O poner las barras invertidas, o poner las comillas. Yo de todas maneras siempre use comillas dobles (") ya fue! Salu2!

---

### Post by chalito on 2008-10-17
Me hace acordar mis primeras experiencias con linux. Un amigo me instalo un redhat ... creo que era el 4. Y me dice "este es tu user, esta tu password, la documentacion esta en /usr/share/doc, y para ver que comandos tenes usa:
apropos <asunto> para encontrar comandos que tengan que ver con <asunto>.
una vez que encontraste un comando que te parece que puede ser el que necesitas, haces man <comando> para ver como se usa.
Suerte.


y la verdad que fue medio duro, pero aprendi bocha solo con esos dos comanditos ;)

---

### Post by Hernán-Amaya on 2008-10-17
esa fue la forma en que aprendí los comandos del viejo y odiado DOS con Gnu/Linux fue distinto mucha info en la red foros y listas me dieron una gran mano

---

### Post by EnriqueK on 2008-10-17
Mas fácil, abrís un terminal, ponés cd, dejas un espacio y seguidamente arrastras al terminal la carpeta en cuestión. Este método está basado en el hecho de que si arrastras a un terminal cualquier carpeta o archivo ubicada en cualquier partición montada, provoca que el terminal muestre la ruta completa a ese archivo o carpeta y te ,a muestra en comillas simples así se evita también el problema de los nombres compuestos.

---

### Post by chalito on 2008-10-17
> **Hernán-Amaya said:**
> esa fue la forma en que aprendí los comandos del viejo y odiado DOS con Gnu/Linux fue distinto mucha info en la red foros y listas me dieron una gran mano

Uff ojala! Hubiera sido genial tener todo eso disponible en 1997, pero todavia ni existia google. Había info, pero era dificil de encontrar, y conectarse a internet con linux no era tan facil como ahora, sobre todo usando solo man y apropos hehe. Tener google y los foros de ubuntu de hoy en dia me hubiese salvado de mas de un dolor de cabeza!

---

### Post by pol666 on 2008-10-17
> 

sudo rm -rf /home/música/cumbia*

con -rf sacas permisos de administrador nomas?
el "*" lo pusiste por algo?

con el rm no la tenia muy claro por que creo que no pude borrar carpetas.. va no me acuerdo

---

### Post by vampichoke on 2008-10-17
> **victor_nesta said:**
> con comillas simples ' 
cd 'pedro es mi amigo'
victor@nesta-desktop:~/Escritorio/pedro es mi amigo$

> **guisheca said:**
> Y sigo aprendiendo, gracias!!

x2!!!

---

### Post by guisheca on 2008-10-17
> **chalito said:**
> Me hace acordar mis primeras experiencias con linux. Un amigo me instalo un redhat ... creo que era el 4. Y me dice "este es tu user, esta tu password, la documentacion esta en /usr/share/doc, y para ver que comandos tenes usa:
apropos <asunto> para encontrar comandos que tengan que ver con <asunto>.
una vez que encontraste un comando que te parece que puede ser el que necesitas, haces man <comando> para ver como se usa.


Yo creo que esta entrada ya se va a convertir en la más útil para mi en toda la historia!!!

---

### Post by chalito on 2008-10-17
> **guisheca said:**
> Yo creo que esta entrada ya se va a convertir en la más útil para mi en toda la historia!!!

Me alegro que ayude :)

otro util para completar podria ser:

apt-cache search <palabra>

si con apropos no encontras lo que buscas porque no lo tenes instalado, con ese comando podes buscar en todos los paquetes listados en los repositorios que tenes definidos. Es el equivalente command-line de hacer una busqueda en synaptic, digamos.

---

### Post by victor_nesta on 2008-10-17
Hace un tiempo mi primo, gran usuario de Linux, me dijo cuando le pregunte sobre Como hacer algo:
Te voy a decir una palabra mágica, tenela presente SIEMPRE. 
**MAN SUDO**

---

### Post by faktorqm on 2008-10-20
> **pol666 said:**
> con -rf sacas permisos de administrador nomas?
el "*" lo pusiste por algo?

con el rm no la tenia muy claro por que creo que no pude borrar carpetas.. va no me acuerdo

emm no, -rf, la parte de r significa recursive (recursivo) para borrar el arbol de directorios entero, o sea, los archivos del directorio actual, las subcarpetas, los archivos de las subcarpetas, y todo lo que venga abajo. f significa force (forzar), o sea, si no lo podes borrar, borralo igual. Eso si, por las dudas de no tener permisos para algo, ejecutalo con sudo :D
Lo de cumbia* significa, todo lo que empiece con la palabra "cumbia", sea link, carpeta o archivo. 
Salu2!

---

