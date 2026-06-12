---
title: "Configurar X a baja resolucin 640x480"
date: 2010-03-02
forum: Software
---

### Post by victor_nesta on 2010-03-02
Hola amigos, resulta que me regalaron una compu viejita, pero el monitor si que da lastima, no soporta resoluciones mayores a 640x480 sino se va de frecuencia.
Quería aprovechar esta compu para hacer pruebas y demas cosas que no haría en la que uso siempre.
Por el momento instalé un Alternate 9.10 y funciona barbaro, el tema es cuando llamo a las X, ahi se va de frecuencia el monitor.
¿Hay alguna manera de configurar el Xorg para que se accione en 640x480?
Si se puede hacer esto, ¿Que escritorio de bajos recursos me recomiendan? Xfe, Fluxbox... Escucho ofertas.

Desde ya muchas gracias.
Saludos!!

---

### Post by juancarlospaco on 2010-03-02
Ubuntu minimal CD

icewm

:)

---

### Post by victor_nesta on 2010-03-02
Muchisimas Gracias juancarlopaco,ya bajo el minimal es bien sencillo.

De todos modos instale el escritorio que instale me sigo complicando la vida, bah el xfe arranca en 800x600 segun recuerdo. Tal ves me equivoque.
Igualmente para saber y aprender ¿no hay manera de tocar el Xorg para que arranque en 640x480?

Gracias nuevamente!!

---

### Post by juancarlospaco on 2010-03-03
**sudo apt-get install grandr ; grandr**

---

### Post by victor_nesta on 2010-03-03
Buenísimo, en cuanto pise mi casa lo pruebo y le meto el SOLVED al topic.
Un millón de gracias juancarlospaco.

PD: Perdón Guille, nose que habré puesto de "inappropiate", se me escapo.

---

### Post by victor_nesta on 2010-03-03
No hubo manera de hacer correr las X en el Monitor Markvision 4963A.
Después encontrar un par de manuales, vi que si
```
#Xorg -configure
```
crea el archivo xorg.conf(.new) como el de toda la vida. (ya que las nuevas versiones de Xorg no lo creaban automáticamente.
y que con
```
#Xorg -config xorg.conf.new
```
podemos probar los cambios antes de dejarlo definitivo.
Ahora no se va de frecuencia sino que directamente queda la pantalla en negro, calculo que será que no tengo los datos de HorizSync y de VertRefresh que nose donde conseguir, aunque en verdad a esta altura ya ni se si es eso :)

Gracias por la ayuda y seguiremos buscando alguna solución.

---

### Post by juancarlospaco on 2010-03-03
**sudo dpkg-reconfigure xserver-xorg**

*creo que era asi...*

---

### Post by victor_nesta on 2010-03-05
No, no hubo caso. De todos modos estoy aprendiendo un montón de comandos que vienen bárbaro que no conocia y que no tenia donde probarlos tampoco. Si después de todo un monitor como el que tengo, lo debo tener yo y 4 personas mas en el mundo. :D

Mientras sigo buscando la solución, ¿puedo hacer una pregunta que esta un poco fuera de lugar en el hilo?

Si, le meto un cable de red "cruzado", conectado desde esta compu a mi notebook, podre levantar vídeo en remoto?
Por que si puedo levantar las X, ya esta, después lo demás seria dejarlo configurado en 640x480 desde gui. (Aun no compre el Router aclaro) 
Si esto se puede, como es mas o menos la cosa o de que manera lo busco en google :)

Gracias juancarlospaco, te debo una cerveza o un ubuntu coffe!

---

### Post by guillermolisi on 2010-03-05
> **victor_nesta said:**
> 
Mientras sigo buscando la solución, ¿puedo hacer una pregunta que esta un poco fuera de lugar en el hilo?

Si, le meto un cable de red "cruzado", conectado desde esta compu a mi notebook, podre levantar vídeo en remoto?
Por que si puedo levantar las X, ya esta, después lo demás seria dejarlo configurado en 640x480 desde gui. (Aun no compre el Router aclaro) 
Si esto se puede, como es mas o menos la cosa o de que manera lo busco en google :)

Gracias juancarlospaco, te debo una cerveza o un ubuntu coffe!
En teoria, si, deberias poder usar el escritorio en forma remota. Esto es valido con ese cable o con algun tipo de conexion de red que te permita "ver" por IP (de minima) al otro equipo.
Obviamente tenes que habilitar/permitir que el escritorio pueda ser accedido remotamente para que desde la otra maquina puedas acceder y operar.

---

### Post by juancarlospaco on 2010-03-05
**ssh -X $USER@ip-de-pc-remota nautilus**

---

### Post by victor_nesta on 2010-03-06
Gracias por la atención!!
Entonces no hay mucha ciencia en esto, seria lo mismo que si configurara 2 computadoras en red.
Vamos a ver si me sale, si quedo algo abierto hoy hago armar el cable, después les cuento.

Gracias de nuevo.

---

