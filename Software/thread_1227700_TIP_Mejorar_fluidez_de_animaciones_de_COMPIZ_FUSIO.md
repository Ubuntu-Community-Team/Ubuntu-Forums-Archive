---
title: "TIP: Mejorar fluidez de animaciones de COMPIZ FUSION (efectos de escritorio)"
date: 2009-07-31
forum: Software
---

### Post by AlexDDR on 2009-07-31
Algunas veces cuando se ejecutaban aplicaciones muy demandantes de de rendimiento notaba como los efectos de escritorio sufrian perdida de cuadros por segundo, lo que me hizo recordar que habia activado la sincronizacion vertical de pantalla, para poder ver las cosas sin el efecto de barrido o tearing en ingles.

 Por lo que en mis tiempo de jugon recorde que siempre el Vsync quita algo de rendimiento, ya que al tener que esperar por el barrido vertical este completo, se pierden FPS (frames por segundo)

 Para no perder el vsync y seguir disfrutando de buen rendimiento es que se creo el triple buffer, ya que de esa forma no se produce el problema con el vsync sin triplebuffer, que al no poder mostrar los cuadros a la suficiente velocidad la tarjeta grafica los disminuye or la mitad en un instante. Por ejemplo si no puede con 60fps, se pasa a 30fps y despues a 15fps y asi...
  en cambio con el triple buffer al disminuir no lo hace de saltos sino que de forma suave que uno ni nota, lo que da animaciones fluidas y mas bonitas.

la solucion
-------------


activar el triplebuffer en el xorg.conf agregando en la seccion device
 	Option "TripleBuffer" "true"

para editar apretar ALT+F2 y poner 
    gksu gedit /etc/X11/xorg.conf



el mio esta de la siguiente forma

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option "TripleBuffer" "true"
EndSection


reinician el pc  y listo


ahora para activar el vsync (sincronizado vertical) deben tener instaldo el paquete: compizconfig-settings-manager desde synaptic

despues lo ejecutan en SISTEMA --> Preferencias --> Administrador de opciones CompizConfig

van a Opciones Generales en la pestaña "Display Settings" activan la casilla "sincronizar con el borrado vertical" y ajustan la frecuencia de actualizacion a la de su monitor o modo de video, pueden probar desactivar la deteccion auntomatica de frecuencia ya que a mi me funciona estableciendo el valor manualmente de mejor manera.


y ya debiesen tener animaciones mas fluidas, sobre todo muy notorio en efectos de Desvanecimiento  oLampara magica en ventanas grandes de aplicaciones mas pesadas como firefox.


Bien , espero les sirva el Tip y auq eme ha dejado muy feliz con mi nvidia que se pegaba saltos raros en la animaciones


Espero sus comentarios
saludos


PD: si tienen nvidia, no olviden desactivar el "forzar el pintado de salida independiente" en Opciones generales para evitar el bug de los videos de pantalla completa con TOTEM y otros en el que se ve el fondo de escritorio cuando uno mueve el mouse.

---

### Post by aledruetta on 2009-07-31
Pucha, pensé que iba a poder solucionar [éste]("http://ubuntuforums.org/showthread.php?t=1221867&highlight=awn"), mi problema con AWN y Compiz, pero no tuve suerte.

Muy buena información, igualmente.
Saludos,
Alejandro.

---

### Post by maxmoraga on 2009-08-03
Otra buena opción es bajar la calidad de los efectos en el compiz-manager, 

en "general options" se puede elegir entre 3 o 2 opciones(no recuerdo que estoy en la oficina) para los efectos, pero bueno la cosa es que si seleccionan la opcion de favorecer rendimiento la calidad de detalle de los efectos bajara el mínimo pero sin perder la gracia lo que te permite tener los efectos a menor costo de recursos.

Saludos.

---

### Post by AlexDDR on 2009-08-03
claro de hecho en la configuracion de efectos de escritorio aparecen los niveles de potencia de los efectos, ya que no todos tenemos una tarjetqa que soporte todo y algunos plugins consumen mas recursos que otros.

Pero este tip esta orientado a avitar las bajas en cuadros por segundo de las animaciones

He probado la integrada intel de mi pc y reaccionaq en forma mas fluida que la nvidia, asi que no es tan notorio, pero con la nvidia si uno activa el vsync en algunos momento mas exigentes de cada animacion al no alcanzar los 60fps (refresco del monitor) los baja , generando una animmacion con saltos, pero con el triplebiffer+vsync los saltos no son  por divisiones 2, sino que va en forma más suave.


saludos

---

