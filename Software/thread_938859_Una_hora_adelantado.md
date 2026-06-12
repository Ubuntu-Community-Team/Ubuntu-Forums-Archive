---
title: "Una hora adelantado"
date: 2008-10-05
forum: Software
---

### Post by Hei Ku on 2008-10-05
A alguien mas le paso que hoy se le adelanto la hora?
Tengo la hora sincronizada con ntp.ubuntulinux.org y todos los upgrades al dia.

---

### Post by sajnox on 2008-10-05
Marcelo Fernandez de la lista de correo del grupo nos paso un link con la explicacion [1]

Solo hay que ver cuanto tardan en arreglarlo.

PS: Entra a la pagina de clarin y fijate que hora tiene, no solo tu maquina quedo una hora adelantada

[1] [http://juan.zauber.com.ar/2008/10/5/opps-we-did-it-again](http://juan.zauber.com.ar/2008/10/5/opps-we-did-it-again)

---

### Post by Mauro22 on 2008-10-05
WTF :confused:


Tenes razon... o tarde 1 hora en y venir de la cocina :confused: jejej


Ojala se solucione.... pronto...

---

### Post by User21 on 2008-10-05
Yo creí que llegaba tarde al trabajo, y salí volando.. pero era sábado, asi que cuando llegué, estaba todo cerrado. (????)

---

### Post by lega on 2008-10-05
entu caso atrasa, un día, hoy es domingo :P

---

### Post by victor_nesta on 2008-10-05
Noo! que lo dejen como esta. Por 1era ves en mi vida estoy llegando a horario a mis citas. :)

---

### Post by guisheca on 2008-10-05
Nooooo jajajajaja avisen que era eso!!!!! Lo que pasa es que me ando queriendo hacer el machito con un reloj binario en mi escritorio, hace como 15 minutos que estoy tratando de ver porque ***** no puedo leer bien la hora #-o](*,)

---

### Post by ramiro_md on 2008-10-05
Yo me levante y lei las 17.10 dije no el partido !!!! pero eran las 16.10, lop ude cambiar tranquilo. Raro...Un saludo

---

### Post by leo_rockway on 2008-10-05
> **guisheca said:**
> Nooooo jajajajaja avisen que era eso!!!!! Lo que pasa es que me ando queriendo hacer el machito con un reloj binario en mi escritorio, hace como 15 minutos que estoy tratando de ver porque ***** no puedo leer bien la hora #-o](*,)

Eso significa que ya aprendiste en leer en binario y que el del problema no sos vos, ¡copado! xD

---

### Post by sartrejp on 2008-10-05
O sea que dormí una hora menos de siesta? me voy a acostar entonces. 
Pero se cambia de ahí nomás, espero que no se me atrase un hora después (o tendré que estar atento).

---

### Post by Thalskarth on 2008-10-05
y yo que pensaba que mi Pc estsba loca :P

al menos no soy el unico... no se, tratando... le puse configuracion por internet y seleccione todos los servidores juntos... desde entonces, ahora veo bien la hora...pero no se porque :S

---

### Post by z37a on 2008-10-05
Otro mas con este problema, me llamo mucho la atencion hasta que lei esto, en mis 2 pcs con ubuntu me paso esto, y lo raro es que una tiene 64bits y la otra i386!!!!!

---

### Post by sartrejp on 2008-10-06
En el planet de ubuntu-ar, vi este post de Ubunlog, que dice como arreglarlo, por si le sirve a alguien.
[http://ubunlog.blogspot.com/2008/10/arreglar-error-time-zone-argentina.html](http://ubunlog.blogspot.com/2008/10/arreglar-error-time-zone-argentina.html)

---

### Post by jpmorelli on 2008-10-06
JAJAJAJA, yo volví de MDQ y pensé, como tardé en el viaje, juaaaaa !!! Despues miré el reloj y lo cambié a mano, no me di cuenta que se volvió a adelantar otra vez...

---

### Post by sergiom99 on 2008-10-06
confirmo que lo mismo pasa en CentOS. A ver quien arregla el tzdata mas rapidamente ;-)

---

### Post by niko_3100 on 2008-10-06
Che yo lo arregle, porque se ve que tambien cambia la hora de la bios... rarisimo entre a la bios puse la hora bien y creo que se soluciono.... estos argentos que no se ponen de acuerdo en adelantar la hora o no... soy argento jeje!! aguatee

---

### Post by osensei on 2008-10-06
Buenas, hace mucho que no escribo por acá, les cuento que este problema lo pueden solucionar instalando la última versión del paquete tzdata que hay en los repositorios de Debian. Lo pueden bajar de acá: [http://http.us.debian.org/debian/pool/main/t/tzdata/tzdata_2008f-1_all.deb](http://http.us.debian.org/debian/pool/main/t/tzdata/tzdata_2008f-1_all.deb)

Una vez que instalen el paquete, tienen dos opciones para que la hora se actualice: Reiniciar, o ejecutar el siguiente comando en la terminal.

```
sudo ntpdate ntp.ubuntulinux.org
```

---

### Post by Hei Ku on 2008-10-06
o ejecutar:

sudo /etc/init.d/ntpd restart

dependiendo de como tengan la sincronizacion.

---

### Post by facundocorradini on 2008-10-07
Diganmelo a mí, que caí en la desesperación al ver que media hora después de lo pautado aún no había venido nadie de mi banda... Cuando saqué el celu para llamarlos miré la hora de casualidad y no entendía nada!!! xD

---

### Post by santiagoward2000 on 2008-10-07
Me acaba de llegar un update del tzdata y se arregló!
Y parece que también se arregló en la página de clarín.

---

### Post by sergiom99 on 2008-10-07
> **santiagoward2000 said:**
> Me acaba de llegar un update del tzdata y se arregló!
Y parece que también se arregló en la página de clarín.

es cierto, es cierto!
los de centOS todavia no lo arreglan :-(

---

### Post by santiagoward2000 on 2008-10-07
> **sergiom99 said:**
> es cierto, es cierto!
los de centOS todavia no lo arreglan :-(

¿Se ganaron algún premio los de Ubuntu?

---

### Post by Hei Ku on 2008-10-07
> **santiagoward2000 said:**
> ¿Se ganaron algún premio los de Ubuntu?

Si, el de "tardar 2 dias para copiar el paquete de Debian". :p

Y ademas, esta mal el arreglo, asi que en menos de 2 semanas tienen que sacar otro o la hora va a volver a cambiar (esto es cortesia de Debian, creo)

---

### Post by santiagoward2000 on 2008-10-07
> **Hei Ku said:**
> Si, el de "tardar 2 dias para copiar el paquete de Debian". :p

Y ademas, esta mal el arreglo, asi que en menos de 2 semanas tienen que sacar otro o la hora va a volver a cambiar (esto es cortesia de Debian, creo)

JAJA! ¿En serio van a tener que arreglarlo? ¿Por que?

---

### Post by vk-cdg on 2008-10-09
Hoy a la mañana, mientras me cambiaba en el living de casa (para no despertar a la beba) vi en el noticiero que a partir del Domingo 19 se adelanta una hora.....

Lo primero que se me vino a la cabeza fue el tzdata
Lo segundo fue largar una cargajada
Lo tercero la puteada de mi jermu porque se despertó la beba.
Lo cuarto la puteada por esperar el nuevo tzdata

---

### Post by Mauro22 on 2008-10-09
:)

El Tzdata estaba en lo correcto, habia que modificar la hora...


No se olviden, el domingo 19 adelantamos otra vez los relojes :mad::mad:

---

### Post by guisheca on 2008-10-09
Menos mal que no toqué nada del tzdata XD

---

