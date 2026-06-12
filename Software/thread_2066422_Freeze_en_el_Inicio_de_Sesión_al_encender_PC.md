---
title: "Freeze en el Inicio de Sesión al encender PC"
date: 2012-10-04
forum: Software
---

### Post by reLlene on 2012-10-04
Pues  resulta que son pocas las oportunidades, me atreveria a decir que 1 en  10, que al encender mi máquina,al seleccionar Ubuntu como S.O. a  arrancar, en la pantalla de inicio de sesión se congela y no puedo  ingresar mi contraseña para acceder. Tanto el cursor que se muestra para  el ingreso de la contraseña como la hora del sistema inclusive que  muestra arriba se congela por completo. Aguardo unos minutos para ver si  es cuestión de procesos, sin embargo el reloj deja de correr y pues me  veo obligado a tener que apagar y nuevamente encender mi máquina.
  Aclaración: esto me pasó SIEMPRE...me refiero. es una máquina  nueva(3 meses), me venía con el win 7 y la version de Ubuntu es la  última 12.04 LTS y no obtengo NINGÚN error, una vez a la hora de acceder  al sistema correctamente si que se freeze. Alguién sabe a que puede  deberse? Hay algún archivo de log del propio sistema dónde pueda ver si  me topo con alguna información que pueda ayudarme a encontrar el  problema? Por cierto, esto no sucede en mi Win 7 y mi maquina es una  notebook ASUS K53E, con un cpu Intel(R) Pentium(R) CPU B950 @ 2.10GHz  x64, RAM de 3GB DDR3...

---

### Post by guillermolisi on 2012-10-06
En /var/log/dmesg deberias ver en detalle que sucede cuando la maquina comienza a funcionar pero, dependiendo de la causa, puede ocurrir que no llegue a registrar las condiciones por las que se congela.

Las funciones de Suspender e Hibernar funcionan correctamente ?

---

### Post by reLlene on 2012-10-09
guillermolisi le echaré una mirada en cuanto llegue a casa a ver si me topo con algo :(
 Por cierto la funcion Suspension rula bien, Hibernar nunca la he probado. De qué manera puedo hacerlo con Unity o desde la terminal?

---

### Post by guillermolisi on 2012-10-09
Si tenes adecuadamente configurado el tamaño de la particion swap deberias ver la opcion de Hibernar cuando intentas apagar el equipo (o como una alternativa dentro de las opciones que se despliegan cuando haces click sobre el icono del extremo derecho superior de la barra de estado de Unity, ese que parece una ruedita dentada).

---

