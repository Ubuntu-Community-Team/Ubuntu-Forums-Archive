---
title: "[SOLUCIONADO] no conecta a google"
date: 2009-05-20
forum: Software
---

### Post by hiphosama on 2009-05-20
esta pregunta la encontré en otros foros de su comunidad pero los enlaces estaban rotos y las explicaciones no correspondían a la versión Ubunto9,04 por lo tanto nunca llegue a los lugares que especificaban.

soy nuevo en este sistema y espero no volver a microsoft, el tema es el siguiente no puedo conectarme a google se cualfuese ellink o pagina de esta compañia.
mi conexion es con VTrobo y compu un compaq v3000 especificamente v3418la, si nesecitan algun dato solo pidanlo pero indiquenme como obtenerlopq aun no me manejo en el sistema aunque me parece super simple de aprender.
saludos y gracias

---

### Post by Patriciologico on 2009-05-20
¿Solo a paginas google? Debiereas especificar mas datos de tu coneccion. A veces es problemas de DNS, a veces de configuracion del router (si es el caso) por que las conexiones MTU estan excedidas. Tambien existe el caso (que me paso a mi) que la compañia (telefonica) nos tuvo a todo nuestro sector de residencia, con conexion solo a algunas paginas, debido a problema de sus DNS, en este ultimo caso solo pudimos esperar.

Saludos!

---

### Post by Carlos C on 2009-05-20
A mí me pasó una vez y también con internet VTR (evitemos por favor los términos despectivos y concentrémonos en el problema ;)). Es un problema de DNS. Lo que debes hacer es reemplazar los DNS que te entrega vtr por los de [open DNS]("http://www.opendns.com/"). Los dns en cuestión son estos:

208.67.222.222
208.67.220.220

Si no sabes cómo cambiar tus dns te informo que tienes dos opciones: cambiarlos en tu router (en caso de que uses uno) o en tu equipo. La ventaja de cambiarlos desde tu router es que así todos los que se conecten a tu red podrán usarlos. Para saber cómo cambiarlos desde tu router debes ir al sitio de opendns y leer las instrucciones correspondientes al modelo de tu router:

[https://www.opendns.com/start/router/](https://www.opendns.com/start/router/)

La otra opción es cambiarlos desde tu equipo, lo que afectará sólo a tu computador:

[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

---

### Post by hiphosama on 2009-05-20
> **Carlos C said:**
> A mí me pasó una vez y también con internet VTR (evitemos por favor los términos despectivos y concentrémonos en el problema ;)). Es un problema de DNS. Lo que debes hacer es reemplazar los DNS que te entrega vtr por los de [open DNS]("http://www.opendns.com/"). Los dns en cuestión son estos:

208.67.222.222
208.67.220.220

Si no sabes cómo cambiar tus dns te informo que tienes dos opciones: cambiarlos en tu router (en caso de que uses uno) o en tu equipo. La ventaja de cambiarlos desde tu router es que así todos los que se conecten a tu red podrán usarlos. Para saber cómo cambiarlos desde tu router debes ir al sitio de opendns y leer las instrucciones correspondientes al modelo de tu router:

[https://www.opendns.com/start/router/](https://www.opendns.com/start/router/)

La otra opción es cambiarlos desde tu equipo, lo que afectará sólo a tu computador:

[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)



TE PASASTE MUCHAS GRACIAS

problema solucionado lo cambie desde el equipo ya que solo era mi computador.

gracias

---

### Post by vampireline on 2009-05-20
A mi también me pasaba..pensé que era solo yo y reiniciaba el router a cada rato...me soluciono el tema también.

saludos.

---

### Post by jverasobino on 2009-05-21
gracias por el tip Carlos C, realmente me tenia chato ocupar yahoo.
solucione el problema a mi note no mas, se me fue en collera configurar el router.
realmente soy un ignorante en tema de redes y me gustaria una ayuda para solucionar el problema limpiamente y no como parche.

nuevamente agradezco la ayuda.):P
saludos

---

### Post by Carlos C on 2009-05-21
> **jverasobino said:**
> gracias por el tip Carlos C, realmente me tenia chato ocupar yahoo.
solucione el problema a mi note no mas, se me fue en collera configurar el router.
realmente soy un ignorante en tema de redes y me gustaria una ayuda para solucionar el problema limpiamente y no como parche.

nuevamente agradezco la ayuda.):P
saludos

No se si entendí bien, pero usar los dns de opendns no es una solución parche, en mi opinión, sino que es la opción más recomendable. Opendns provee un servicio gratuito que resulta más seguro y a mi me funciona mejor. Puedes informarte más en esta dirección:

[http://www.opendns.com/solutions/overview/](http://www.opendns.com/solutions/overview/)

---

### Post by Carlos C on 2009-06-10
> **jverasobino said:**
> gracias por el tip Carlos C, realmente me tenia chato ocupar yahoo.
solucione el problema a mi note no mas, se me fue en collera configurar el router.
realmente soy un ignorante en tema de redes y me gustaria una ayuda para solucionar el problema limpiamente y no como parche.

nuevamente agradezco la ayuda.):P
saludos

Recién entiendo lo que querías decir, perdón :) Si puedes decir el modelo de tu router puede que alguien pueda orientarte.

Saludos.

---

### Post by tralala321 on 2009-06-30
bkn gracias

---

