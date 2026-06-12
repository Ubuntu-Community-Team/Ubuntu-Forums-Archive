---
title: "Firefox 3 es una M*****"
date: 2008-07-08
forum: Software
---

### Post by Darth Trix on 2008-07-08
Gracias a dios existe Konqueror, por que el Firefox de repente se murió. Arranca anda un rato y cuando quiero entrar a alguna página [(como Gmail)]("http://www.gmail.com") se muere sin previo aviso y me tira este error: 
```
Fallo de segmentación
trix@trix-desktop:~$ 
```
Ya purgue y reinstale el Firefox 20 mil veces me tome le trabajo de borrar manualmente cada archivo de configuración y volverlo a instalar y nada, sin previo aviso sigue muriéndose.
Si alguien tiene una idea de como salvarlo me hace un favor, sino tendre que quemar mi certificado de Record Guiness.

---

### Post by EnriqueK on 2008-07-08
Tomá nota de tus extensiones, respaldá tus marcadores a html o mejor entrá a la carpeta de usuario ubica la carpeta oculta .mozilla , navegá hasta encontrar los archivos **places.sqlite** y** cookies.sqlite** los respaldás , luego borras la carpeta .mozilla y arranca nuevamente firefox3 , esto va a generar nuevamente la carpeta .mozilla y reemplaza los archivos mencionados, luego arrancas nuevamente firefox y vuelve a descargar las extensiones.

---

### Post by pol666 on 2008-07-08
mas respeto con Don Firefox Tres

---

### Post by Darth Trix on 2008-07-08
Gracias por intentar ayudarme, pero no tengo problema con mis archivos personales, ya purgue totalmente el programa y borre todo maulamente. Lo reinstale e inicié una sesion como si lo acabara de instalar y sigue pasando lo mismo, se cierra y me tira ese error

---

### Post by luchardi on 2008-07-08
No tendrás un problema de compatibilidad con Java o la JVM que estas usando no?

---

### Post by Darth Trix on 2008-07-08
Gracias a todos por intentar de ayudar, pero para intanetar hacerlo andar vovli atras todos mis pasos y removí cialquier paquete que haya instalado despues de haber instaldo Firefox 3.0. El problema resulto ser nfs-common, no se por que pero cuando borre ese paquete y todas sus dependencias Firefox volvío a andar

Otra vez gracias a todos

---

### Post by Hei Ku on 2008-07-08
que raro. yo tengo el nfs-common instalado y no tengo ningun drama en ninguna de las dos PCs.
Para mas informacion, el paquete es para compartir archivos por NFS (Network file system)

---

### Post by Kantier on 2008-07-08
por ahi el problema está en alguna dependencia de nfs-common (o algo que depende de nfs-common)

---

### Post by Darth Trix on 2008-07-08
> **Kantier said:**
> por ahi el problema está en alguna dependencia de nfs-common (o algo que depende de nfs-common)

Si seguro que es problema de alguna dependencia.
Para ser mas constructivo tendría que instalar cada una de las dependencias una por una y ver cual es exactamente la que me causa problemas.
Pero no lo voy ha hacer

---

### Post by BlackHero on 2011-01-16
Y probaste borrando los archivos ocultos de configuracion en tu carpeta de usuario? yo creo que el titulo que le pusiste a este post no es el correcto, mas siendo una novato como sos vos.

---

### Post by guillermolisi on 2011-01-17
Fijate que este thread es un poquito viejo. Calculo que a esta altura no debe tener problemas con FFox o esta usando otro navegador.

---

