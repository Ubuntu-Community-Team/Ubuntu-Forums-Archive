---
title: "Firefox"
date: 2010-04-27
forum: Software
---

### Post by RafaelG on 2010-04-27
Hola a todos los companeros Ubunteros, bueno yo comenze en ubuntu 8.10 y ahora estoy en la version 9.10, con el tiempo he modificado muchas cosas ya que he realizado actualizaciones a las nuevas versiones y con ellas he ido solucionando los inconvenientes que he tenido con mi notebook dell vostro 1510.

       He modificado el firefox en varias oportunidades y ya en este momento estoy utilizando  la version 3.7, despues de un tiempo simplemente decidi eliminar windows y ese espacio libre coloque una nueva particion con ubuntu diferente a mi partion original. estuve usando entonces esta particion nueva donde realize una instalacion limpia con la version 9.10 karmic que quedo como la principal y trabaja a la perfecion en cambio el firefox que tengo en mi partion original es lenta en comparacion a mi nueva partion obviamente todo esto se debe a las diferentes versiones que instale desde la 3.0 hasta la que tengo actualmente que es 3.7

       Por todo lo explicado anteriormente lo que deseo es eliminar todas esas versiones y simplemente instalar la que viene por defecto en la version 9.10 en mi partion original que trabaja muy bien  segun mi opinion por este motivo estuve buscando en google pero no he logrado conseguir con el post el cual pueda ayudarme con lo que necesito.

       Bueno me despido agradeciendo ante mano cualquier opinion constructiva o solucion para dejar firefox tal como viene en la version 9.10

---

### Post by Carlos C on 2010-04-27
Puedes eliminar todos los repositorios relacionados con firefox, luego eliminar firefox mediante el comando "sudo aptitude purge" (o con synaptic escoger la opción "Marcar para desinstalar completamente"). Si lo deseas también puedes borrar los archivos de configuración que están en home. Después de eso basta un "sudo aptitude update" para que esté todo listo para una instalación por defecto.

Saludos.

---

