---
title: "programacion"
date: 2009-06-21
forum: Software
---

### Post by tsueseres on 2009-06-21
hola, estoy queriendo empezar a programar en ubuntu, pero no se mucho sobre los tipos de lenguages de rogramacion. yo usaba autoit en windows y mi pregunta es si 

existe autoit para ubuntu, he buscado pero nomas he encontrado el scite que traia autoit pero no puedo compilar.

tambien tengo otra pregunta los programas de java de windows funcionan en ubuntu?

---

### Post by Hei Ku on 2009-06-21
Java es multiplataforma, asi que teoricamente deberían correr sin problemas en Ubuntu.
Depende de las funciones particulares de cada programa, esto se cumple o no. A veces requieren algún ajuste.
Por supuesto, tenes los IDEs de java mas conocidos disponibles en Ubuntu (Eclipse, NetBeans, etc.)

---

### Post by tsueseres on 2009-06-21
grax por lo de java

y sobre autoit y el scite?

---

### Post by juancarlospaco on 2009-06-21
Me parece que Java lleva un leve toqueteo para laburar bien en Linux igual eh,
por el tema de los permisos, el filesystem, en general es muy diferente,
va no se he visto que no es que copias y pegas de Windows a Linux y 
le haces doble click y sale andando, 
es mas muchas cosas en Java ofrecen un instalador diferente para cada uno.
Hablando de hacer las cosas bien y de un software relativamente complejo.
*Es lo que vi como usuario, no programo en Java.*

---

### Post by Barasuishou on 2009-06-22
no se tanto ni de programación ni de sistemas, pero si vas a programar en java (creo) sería bueno pruebes el sistema operativo opensolaris, que está hecho en java, por sun microsistems, 

supongo que siendo hecho por sun, y en java debe ser un buen entorno para programar en java, 

chauu

---

### Post by Hei Ku on 2009-06-22
El problema no es que ande bien java, sino que anden bien los IDEs. Y el Eclipse o similares van a tener mejor soporte en Linux por simple cantidad de usuarios. Ademas que siendo un entorno poco familiar lo va a distraer de lo que realmente quiere, que es programar.

Esto no quita que pueda probar OpenSolaris, que por lo que dicen es un lindo SO, aunque nuevito todavia. (Hay que ver que pasa despues de la adquisicion de Oracle)

---

### Post by juancarlospaco on 2009-06-22
Solaris no esta *"hecho en Java"*, o me equivoco*(?)*.
*Por lo menos la ultima vez que lo use compilaba como un Gentoo.*

---

### Post by Hei Ku on 2009-06-22
No, esta hecho en C como cualquier otro SO.
Se podría inferir que estaría mejor optimizado para correr Java, viniendo de la misma empresa que desarrolla Java, pero es un salto de fé bastante grande si uno conoce lo "departamentalizado" que estan las empresas, donde un area puede que jamas hable con otra. 

Al fin y al cabo, OpenSolaris es un derivado de Solaris, que es un sistema servidor, y en ese caso, lo que mas importa para que corra bien Java es el application server, y no el SO. O sea, el SO influye, pero tiene mas peso el application server.

---

### Post by juancarlospaco on 2009-06-22
[Linux tiene mejor Performance que Solaris para correr Java]("http://www.dba-oracle.com/oracle_news/2005_2_10_linux_vs_sun_solaris_benchmark_clusters_RAC.htm") segun Oracle Benchmarks.

---

### Post by Barasuishou on 2009-06-22
uuu mil perdones me equivoqué XP, yo pensé estaba hecho en java x_x, bueno ahora  ya ta aclarado opensolaris NO está hecho en java, y según dicen acá arriba linux corre mejor java, así que hacele caso a los que saben más que yo mejor xD

---

### Post by WanderingKnight on 2009-06-23
> existe autoit para ubuntu, he buscado pero nomas he encontrado el scite que traia autoit pero no puedo compilar.

No, no hay nada tipo AutoIT para Ubuntu, pero eso es porque no hace falta.

AutoIT se inventó en Windows para dar una solución al problema de que el 95% de las aplicaciones bajo ese sistema, incluyendo las aplicaciones que manejan configuraciones del sistema mismo, no son parametrizables mediante scripts de shell (Batch es un chiste). Para los que no lo conocen, AutoIT es un hack bastante copado que permite manipular el entorno gráfico de Windows mediante un lenguaje similar a VB. Sin embargo, muchas veces resulta un poco engorroso porque dependés de que la aplicación que querés manipular juegue limpio con las APIs de win32, además de que intentar parametrizar un programa mediante eventos de GUI es algo de por sí molesto y completamente indeterminístico.

En Ubuntu y GNU/Linux en general, para lo que se suele usar AutoIT existe la línea de comandos y bash, que es un lenguaje mucho más completo y funcional, y obviamente completamente determinístico (bueno, depende de lo que quieras hacer, obviamente; AutoIT siempre que se usa es porque se trata de resolver un problema que no se puede resolver determinísticamente por otros medios). De bash hay bocha de tutoriales dando vueltas por la red.

Sino después tenés los clásicos C/C++, el multiplataforma Java, o Python, un lenguaje relativamente simple.

---

