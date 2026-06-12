---
title: "como reinicio el network para ver las demas PC"
date: 2009-01-23
forum: Software
---

### Post by papachan on 2009-01-23
Hola

Tengo unas pcs con windows en red se conectan a un router, y el linux las veia muy bien al inicio, ahora imposible, hago refresh en el network de windows y nada....
las perdi por completo


supongo que puede ser un problema de la red de windows, pero no cambie nada en la configuracion del grupo de trabajo. No sé lo que hay que hacer en este casa en ubuntu.


Abrazo !

---

### Post by sergiom99 on 2009-01-23
para reiniciar el servicio de red:
```
sudo /etc/init.d/networking restart 
```

---

### Post by papachan on 2009-01-24
ok genial.

y porque deje de ver las comparticiones windows desde ubuntu? como puedo y remediar?

---

### Post by Hei Ku on 2009-01-24
cambiaste algo en la configuracion de samba?

---

### Post by papachan on 2009-01-24
como se configura el samba? explicame un poco...

no veo que es lo que cambie en mi configuracion. solo uso la maquina para msn y internet.

la otra solucion es poder compartir una carpeta del linux para que los demas windows la ven... pero no se como se hace esto ...

---

### Post by Hei Ku on 2009-01-24
la unica manera en que puedas haber visto las carpetas de las pc windows es que hayas configurado samba, aunque sea sin saberlo. 
Recordas que fue lo que hiciste al principio para poder ver las carpetas? 
Eso nos puede dar una pista sobre que cambio.

---

### Post by papachan on 2009-01-24
Al principio? no toque nada solo tenia un grupo de trabajo unificado en las demas PC windows. y en el ubuntu siempre veia las maquinas a traves de la ventana network. tardaba un poco, a veces desaparecia pero siempre volvian.
Puede ser que hice un update del samba ultimamente descargando actualizaciones esto si puede haber pasado.

y Como reconfiguro mi samba ????

---

### Post by sergiom99 on 2009-01-24
para configurar samba te paso un tuto buenisimo que hizo faktorqm:
[http://ubuntu-ar.org/tutoriales/samba](http://ubuntu-ar.org/tutoriales/samba)

Esta simple y facil. Leelo que te va a servir.
Suerte!
\Sergio

---

### Post by papachan on 2009-01-25
No hay caso. Agregue mi maquina al samba le setée el nombre de mi workgroup
le puse security = share

pero no veo nada. ni de un lado ni del otro. Hago ping a las pcs y si la veo.

pero gracias igualmente...

---

### Post by guillermolisi on 2009-01-25
> **papachan said:**
> No hay caso. Agregue mi maquina al samba le setée el nombre de mi workgroup
le puse security = share

pero no veo nada. ni de un lado ni del otro. Hago ping a las pcs y si la veo.

pero gracias igualmente...
Despues de modificar el archivo de configuracion de Samba, reiniciaste el servicio ?

Si no haces esto no tomara los cambios hechos ```
sudo /etc/init.d/samba restart
```

---

### Post by papachan on 2009-01-26
Reinicié la maquina en realidad, porque me tiró =

```
sudo: /etc/init.d/samba: command not found
```

---

### Post by guillermolisi on 2009-01-26
> **papachan said:**
> Reinicié la maquina en realidad, porque me tiró =

```
sudo: /etc/init.d/samba: command not found
```
En principio si te dio este error es porque Samba server no esta instalado. Posiblemente solo tengas el cliente pero para ver entornos de red Windows necesitas el server.

Confirma esto revisando los paquetes de samba que tengas instalados y, por as dudas, con un
```
ls -al /etc/init.d/sa*
```
Deberia darte una salida con archivos que comiencen son 'sa' dentro de /etc/init.d, entre ellos samba.

---

### Post by papachan on 2009-01-26
Si correcto ! entonces no tengo installado el SAMBA Server. porque no veo nada en /etc/init.d/

lo instalo atraves de Synaptic?

---

### Post by guillermolisi on 2009-01-26
> **papachan said:**
> Si correcto ! entonces no tengo installado el SAMBA Server. porque no veo nada en /etc/init.d/

lo instalo atraves de Synaptic?
Si, usa Synaptic y para no tener problemas, siempre desde los repositorios de Ubuntu.

Si tenes dudas respecto de que paquete Samba tenes que instalar, consulta (por lo menos deberias tener el Samba server y el client).

Con la instalacion se inicia el servicio. Proba si ves la PCs con Win y si no vemos que puede estar pasando (vamos a necesitar algo mas de info).

---

### Post by papachan on 2009-01-27
SI despues que installe el SAMBA client desde synaptic, soy parte del workgroup de mi red hogareña :p ... 
pero desde el Linux sigo sin la posibilidad de ver las demas compus. lo raro es que hace unos días podía.

---

### Post by guillermolisi on 2009-01-27
> **papachan said:**
> SI despues que installe el SAMBA client desde synaptic, soy parte del workgroup de mi red hogareña :p ... 
pero desde el Linux sigo sin la posibilidad de ver las demas compus. lo raro es que hace unos días podía.

Solo para descartar una trivialidad, las PCs con Win tienen algun recurso compartido definido ?

Estan todas las maquinas en la misma LAN (en el mismo bloque de IPs) ?

---

### Post by papachan on 2009-01-28
perdon, debo ser muy nulo en este tema.

Bueno las pcs tienen todas un recurso compartido. si.

y por lo de la LAN, buena pregunta, no sé como averiguarselo en linux.

otra cosa que hice mal, el directorio en mi smb.conf le faltaba el acento : Público

a ver si logramos a algo, si meto buena voluntad, no?

---

### Post by guillermolisi on 2009-01-28
> **papachan said:**
> perdon, debo ser muy nulo en este tema.

Bueno las pcs tienen todas un recurso compartido. si.

y por lo de la LAN, buena pregunta, no sé como averiguarselo en linux.

otra cosa que hice mal, el directorio en mi smb.conf le faltaba el acento : Público

a ver si logramos a algo, si meto buena voluntad, no?
Fijate que IP tienen las placas de red de las maquinas con Win y pega la salida del comando ```
ifconfig
``` en un nuevo mensaje, asi podemos ver si estan todas las maquinas en la misma red.

---

### Post by papachan on 2009-01-28
aca te paso la salida del comando

[http://paste.ideaslabs.com/show/dG2HBeLhr2]("http://paste.ideaslabs.com/show/dG2HBeLhr2")

y por la correccion del smb.conf, ya se resolvió que desde las Wins ya pueden acceder al directorio público del ubuntu.

pero a partir del ubuntu, no entiendo, no se ve nada mas alla del workgroup, y tarda un monton cuando quiero que busque las wins....

---

### Post by guillermolisi on 2009-01-28
> **papachan said:**
> aca te paso la salida del comando

[http://paste.ideaslabs.com/show/dG2HBeLhr2]("http://paste.ideaslabs.com/show/dG2HBeLhr2")

y por la correccion del smb.conf, ya se resolvió que desde las Wins ya pueden acceder al directorio público del ubuntu.

pero a partir del ubuntu, no entiendo, no se ve nada mas alla del workgroup, y tarda un monton cuando quiero que busque las wins....
Bueno, la placa de red del Ubuntu tiene la direccion IP 192.168.0.184 con mascara de red 255.255.255.0. Ahora, podrias verificar que IP y mascara de red tienen las maquinas Windows y a que grupo pertenecen ?

Si el Ubuntu pertenece a Workgroup y las PCs con Win pertenecen a otro grupo tendrias que ver dos grupos en la red, pero desde la PCs Win no podrias entrar a la que tiene Ubuntu.

---

### Post by papachan on 2009-01-29
aqui la ip de la pc

   Dirección IP. . . . . . . . . . . : 192.168.0.148
   Máscara de subred . . . . . . . . : 255.255.255.0
   Puerta de enlace predeterminada   : 192.168.0.1

---

### Post by guillermolisi on 2009-01-29
> **papachan said:**
> aqui la ip de la pc

   Dirección IP. . . . . . . . . . . : 192.168.0.148
   Máscara de subred . . . . . . . . : 255.255.255.0
   Puerta de enlace predeterminada   : 192.168.0.1

Esa IP es de una de las PCs con Windows ?
Si es asi,  la otra PC con Win que tiene, que dice la configuracion de la placa de red ?

Y que nombre de grupo tienen esas PCs con Windows ? (ya te lo habia preguntado antes pero parece que no fui muy claro).

---

### Post by papachan on 2009-01-30
el grupo de trabajo se llama HOMEWORK. las dos otras pcs se ven entre ellas. la otra tiene vista. tiene una ipv6

---

### Post by guillermolisi on 2009-01-30
Si las PCs con Win tienen ese nombre de grupo de trabajo y queres que se vean todas las maquinas dentro del mismo grupo, renombra el grupo de trabajo del Samba y ponele en mismo que las PCs con Win.

Para hacer esto, tenes que editar el archivo de configuracion, buscar la etiqueta donde se define el grupo de trabajo, modificarla y reiniciar el servicio de samba.
Esto se traduce, si lo haces en una consola y usas el editor vi, en
```
sudo vi /etc/samba/smb.conf
```
Si queres usar otro editor, reemplaza 'vi' por el nombre del otro editor ('gvim' o 'nano' por ejemplo)
Luego tenes que reemplazar el nombre del grupo de trabajo por el de las maquinas Win:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = **HOMEWORK**

```
Salvas el cambio y reinicias el servicio de la siguiente forma:
```
sudo /etc/init.d/samba restart
```

Proba y conta como te fue.

---

### Post by papachan on 2009-01-30
Si es precisamente lo que tengo

[Global]
workgroup = HOMEWORK
security = share

Gracias a esto el linux estaba parte del grupo de trabajo de windows.
pero el resto, ya sabes...

---

### Post by guillermolisi on 2009-01-30
> **papachan said:**
> Si es precisamente lo que tengo

[Global]
workgroup = HOMEWORK
security = share

Gracias a esto el linux estaba parte del grupo de trabajo de windows.
pero el resto, ya sabes...

Perdon, entendi que tenia el valor por defecto que es Workgroup, por eso mi anterior mensaje.

---

### Post by papachan on 2009-01-31
Gracias que tengo que hacer entonces?
estoy leyendo toda la documentacion sobre SAMBA.

Si es tan simple como lo dicen el error debe venir en la configuracion de la red windows en las demas PC, estoy seguro que algo paso con el FireWall o algo por el estilo.

sigo buscando.

---

### Post by guillermolisi on 2009-01-31
> **papachan said:**
> Gracias que tengo que hacer entonces?
estoy leyendo toda la documentacion sobre SAMBA.

Si es tan simple como lo dicen el error debe venir en la configuracion de la red windows en las demas PC, estoy seguro que algo paso con el FireWall o algo por el estilo.

sigo buscando.
Puede ser que algun FIrewall este metiendose.

Tenes habilitado el FW en las maquians Win ?

Tenes como revisar el FW de Ubuntu para ver si permite conexiones para la LAN (solamente) en los ports 137-139 y 445 ?

---

### Post by jorgito on 2009-02-03
Hola a todos,  

Me parece que el problema puede venir por algún bug en las actualizaciones, porque a mi me pasa exactamente lo mismo.
Desde la notebook con wifi podia ver mi maquina de escritorio con red cableada, aunque no al reves, pero nunca levante ningun servicio para esto porque no lo necesito.
Ahora, de buenas a primeras, si abro la red me dice que hay un par de redes de windows, pero no se puede llegar mas alla.

Version de Ubuntu: 8.04 

Saludos!

Jorgito

---

### Post by papachan on 2009-02-05
ah si, esto lo piense desde el principio que algo pasaba con las actualizaciones. pero como no sabia nada sobre samba hasta ahora, esta falla me permitió descubrir como se configura samba

Guillermolisi: como se chekea el firewall de ubuntu? que comando harias tu?

desde ya muchas gracias !

---

