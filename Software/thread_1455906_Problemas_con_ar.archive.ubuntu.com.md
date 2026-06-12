---
title: "Problemas con ar.archive.ubuntu.com"
date: 2010-04-16
forum: Software
---

### Post by lilat on 2010-04-16
Buenas! Soy nuevo por estos pagos y ando con un problemita. Estuve tratando de actualizar varias versiones de Ubuntu, Xubuntu, Kubuntu y con todas es lo mismo. 

ar.archive.ubuntu.com  parece que anda a pedal, lo prob{e en la oficina y tambiien. A alguien mas le pasa esto? Pregunto porque tengo Iplan en la oficina e Iplan en mi casa tmb... quizas sea Iplan...

Por otro lado, mucho no entiendo, pero para solucionarlo si edito el surces.list y le cambio AR.archive.ubuntu.com por ES.archive.ubuntu.com es lo mismo?

Consulto porque lo probe y me funciono al palo el update, pero me tiro algunos errores... asi que reinstale.

Gracias, saludos

---

### Post by guillermolisi on 2010-04-16
Cualquier mirror que figure en la lista es valido y deberian ser equivalentes.

Yo uso uno de Brasil desde que los mirrors de Argentina comenzaron a tener problemas.

---

### Post by lilat on 2010-04-16
Barbaro, graciela!!! Ya mismo le doy al update.

Saludos.

EDIT: la verdad que Brasil anda mucho mas r{apido que España, recomendado poner BR :) Saludos.

---

### Post by victor_nesta on 2010-04-21
Ya que estamos hago una preguntita.
¿En modo consola hay alguna manera automática de cambiar la ubicación de los repos?
Me paso de instalar el Alternate y marcar Argentina (por costumbre) y carga los repos de Argentina (que funcionaban mal), sin GUI no supe como cambiarlos y me era mas fácil reinstalar que modificarlos a mano. :P (Claro que no sabia la direccion ya que los de brasil por ejemplo son de una universidad) 

Saludos

---

### Post by alfplayer on 2010-04-21
> **victor_nesta said:**
> ¿En modo consola hay alguna manera automática de cambiar la ubicación de los repos?

Con "sed":

sudo sed -i "s/ar.archive.ubuntu.com/otro_repositorio/" /etc/apt/sources.list


Con "vi":

sudo vi /etc/apt/sources.list

(en el modo de comando)
:%s/ar.archive.ubuntu.com/otro_repositorio/

Después obviamente hay que actualizar el índice de paquetes (por ejemplo con "sudo apt-get update").

---

