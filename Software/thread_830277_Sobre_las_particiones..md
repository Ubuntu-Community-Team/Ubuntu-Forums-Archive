---
title: "Sobre las particiones."
date: 2008-06-15
forum: Software
---

### Post by rxx266 on 2008-06-15
Bueno como veran estube leyendo un poco sobre linux, y la parte que me mas me llamo la atenciona es la de crear la particiones, en una de las paginas el mismo autor recomendaba, hacer dos particiones para /usr y /home, y esto es lo que escribe:

# Home directories are always on their own partition and you can upgrade the distribution without having to backup the home directories.
# /usr is where software goes, so you can keep that whenever you upgrade distributions.

# El  directorio home está siempre en su propia partición y se puede actualizar la distribución sin tener que hacer una  copia de seguridad de los directorios home.
# /usr es en donde va el software, por lo que puede mantener cada vez que actualice la distribución.

Mi pregunta es : ¿Cuando se actualiza la distro, modificaria todos eso directios, haciendo un kilombo, a ver algun etendido en linux que me heche una mano?.

PD:fuente: [http://www.slackware.com/install/partitions.php](http://www.slackware.com/install/partitions.php)

---

### Post by pol666 on 2008-06-15
si la actualizas a veces hace embrollos y rompe cosas. Si reinstalas no pasa nada y conserva tus configuraciones hablando de /home, 
por que /usr jamas la movi, ni lo voy a hacer.

---

### Post by Air23 on 2008-06-15
No soy un entendido de linux (recien llevo 6 meses) pero te voy a dar mi opinion. 
A mi entender la gran ventaja de tener una particion root y otro home (como particiones separadas) es que se puede formatear solo la particion root e instalar otra version de ubuntu sin borrar los datos de tu home (ni tener la necesidad de hacer un backup de tus documentos, musica, videos, etc). Y en ese caso me parece que no tiene mucho sentido hacer una actualizacion (lo cual se justifica si no tenes tu home separado).
No se si soy claro, si tenes las dos cosas en 1 sola particion y sale una version nueva de ubuntu tenes 3 opciones: quedarte en la que tenes, hacer una actualizacion o una instalacion limpia (perdiendo todo tu home por lo cual deberias hacer un backup). Si bien nunca lo hice, segun tengo entendido las actualizaciones no son muy recomendables.
En cambio con las 2 particiones separadas, formateas solo root e instalar el nuevo ubuntu manteniendo todo tu home (incluyendo las configuraciones de los programas).

En sintesis mi humilde recomendacion: las 2 particiones

---

### Post by rxx266 on 2008-06-20
Muchas gracias por su aporte chicos,

---

### Post by Hei Ku on 2008-06-20
> **Air23 said:**
> Si bien nunca lo hice, segun tengo entendido las actualizaciones no son muy recomendables.

Pueden terminar con este rumor, por favor? Aca hay mucha, mucha gente que viene haciendo actualizaciones desde hace años. En mi caso, lo deje instalando a la noche, y a la mañana siguiente ya estaba.
Los casos en que no es recomendable es cuando toqueteaste el sistema por fuera del sistema de gestión de paquetes, Adept o Synaptic.

Yo vengo actualizando desde Edgy, hace 4 versiones, sin problemas.

Dicho esto, desde el punto de vista de backup, siempre es mejor tener las particiones separadas.

---

