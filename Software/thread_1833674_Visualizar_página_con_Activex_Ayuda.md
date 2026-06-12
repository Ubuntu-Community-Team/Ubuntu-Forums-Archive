---
title: "Visualizar página con Activex Ayuda"
date: 2011-08-26
forum: Software
---

### Post by asterix77 on 2011-08-26
Hola a todos

Les comento que en mi lugar de trabajo, debo ingresar información a un servidor intranet a través de un navegador. La empresa usa IE en sus equipos para ingresar los datos.

Uso ubuntu lucid, y he intentado hacerlo a través de firefox 6.0 como de chrome 13, pero sin exito. Puedo conectarme y loguearme en el servidor, pero después de esto cuando accede a las opciones y menúes, no puedo seguir. Aparecen los botones de seleccion, cuadros de ingreso de información, etc. pero no puedo hacer ni ingresar nada.

Creyendo que el problema era el navegador, instalé Internet Explorer por playonlinux, el cual se instaló bien. Al acceder al servidor a través de él, se despliega una barra que me indica que por políticas de seguridad, no se está ejecutando activex, por lo que asumo que hay que activarlos. Esto no lo puedo hacer desde herramientas ---->opciones de Internet (como se hace en windows), ya que aquí se abre un cuadro de diálogo que se muestra en blanco y no se puede hacer nada.

Sé que esa página web usa activex, por lo que creo que ese es el problema, por eso la empresa usa IE, ya que activex es solo para ese navegador.

Es lo único que me falta para definitivamente usar mi ubuntu en mi trabajo, ya que he configurado mi intranet, internet, impresora en red bien. Con un poco de trabajo eso si, pero así se aprende.

Espero alguna ayuda de la comunidad, ideas, alternativas de como hacerlo, etc.

Saludos

---

### Post by asterix77 on 2011-08-26
Bueno, he solucionado creo en gran parte el tema.

Instalé el paquete winetricks, luego en una terminal escribí.

./winetricks IE7

Y me instaló una versión en inglés de IE7, el cual si me muestra la ruta para activar activex a través de opciones ---->Herramientas----->etc.

En algunas pequeñas porciones de la aplicación, hay problemas de gráfica, pero igual es legible, y pude ingresar a la página mencionada y trabajar sin mayores problemas.


Saludos

---

