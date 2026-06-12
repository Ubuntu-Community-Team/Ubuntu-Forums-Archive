---
title: "Problemas al inicio (v. 12.10)"
date: 2012-12-14
forum: Software
---

### Post by rodrigonayar on 2012-12-14
Hola amigos,

Acabo de instalar la última versión (12.10).
En un primer intento, tuve problemas de movida, ya que el instalador generó un error y borró la partición donde dejaba windows.
Además de eso, el sistema operativo no iniciaba y quedaba una pantalla violeta o negra. Cuando lograba iniciar, comenzaba a marcar que había una falla en el sistema, sin dar detalles de cuál era el problema y después fallaba la aplicación que informa los errores, además de otras (variaban los fallos con cada reinicio de sistema).

Volví a instalar Ubuntu y ahora inicia normalmente (por ahora), pero persisten el fallo general y los fallos de aplicaciones.

Espero que puedan ayudarme y desde ya les voy agradeciendo por adelantado.
Saludos.
--
Rodrigo

---

### Post by guillermolisi on 2012-12-15
Verificaste la integridad de la imagen ISO que utilizas ?

---

### Post by rodrigonayar on 2012-12-16
Hola Guillermo,

Gracias por tu respuesta.
En un principio creí que podía ser ese el problema o también el pendrive que usé. Pero descargué el instalador en otra Pc y utilicé otro pen y sigue generando fallos.
Marca un error de sistema y cuando selecciono el botón para informarlo, la plicación "Report a Problem" genera este fallo:

ExecutablePath
usr/share/apport/apport-gtk

Otro fallo que me marca es que la aplicación lsb_release se cerró inesperadamente.

Te voy a estar agradecido por cualquier ayuda que puedas ofrecerme.
Saludos.
--
Rodrigo H. Nayar

---

### Post by guillermolisi on 2012-12-16
Actualizaste todo el sistema ?
Ese comportamiento de que cada vez que inicias la sesion de escritorio y aparece el aviso de que una aplicacion se cerro inesperadamente ahora o hace poco tiempo, mas la posibilidad del reporte, corresponde a un informe de fallas y teoricamente fue solucionado hace unas muy pocas semanas atras.

---

### Post by rodrigonayar on 2012-12-17
Guillermo,

Estoy bajando todas las actualizaciones que me indica el sistema. 
Anoche bajé las últimas y hoy no tuve fallas. Si vuelve a suceder, aviso.
Muchas gracias por tu ayuda.
Un abrazo.
--
Rodrigo Nayar

---

### Post by rodrigonayar on 2012-12-26
Hola Guillermo y hola a todos,

Vuelvo a molestarte porque luego de unos días sin problemas, volvieron los errores de sistema.
Primero, el sistema no arranca y cuando reinicio, al comprobar el disco marca que falta el controlador del disco /.

Una vez reiniciado el sistema, va marcando distintos errores, pero no da detalles.
Los únicos errore que mostraron detalles me indicaban: 

/usr/sbin/aptd

/usr/share/apport/

/usr/bin/lsb_release

Todos estos errores ocurren luego de que selecciono la opción para reportar el problema. Y el sistema me informa que "Report a problem" se cerró inesperadamente.

Saludos.

---

### Post by guillermolisi on 2012-12-27
Creo que el tema amerita una detallada revision del hardware. Eso que mencionas sobre el disco no esta bien, por ejemplo, y pueden haber mas factores jugando, sectores defectuosos en el disco, algun banco de memoria que este fallando, pobre compatibilidad de placas de memoria en uso, cables de datos haciendo falso contacto y una larga lista de etcs.

---

### Post by rodrigonayar on 2012-12-27
Guillermo,

Nuevamente agradezco tu respuesta.
Le voy a llevar la máquina a un técnico.
Saludos.

---

