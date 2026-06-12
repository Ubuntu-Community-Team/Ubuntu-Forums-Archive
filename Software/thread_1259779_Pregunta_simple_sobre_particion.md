---
title: "Pregunta simple sobre particion"
date: 2009-09-06
forum: Software
---

### Post by Protohumano on 2009-09-06
Estimados. Soy nuevo en ubuntu. Tengo la distro Jaunty J, todo funciona mejor que lo esperado.
He hecho la particion de un disco nuevo de 80 gb cuando me la solicito la instalacion.  Ha particionado, segun parece, 25 GB o algo asi del disco. las preguntas son:
1) Como puedo ver la capacidad del disco disponible ? Libre y usado. 
2) En caso de que el disco de 80 gb no haya sido particionado originalmente (el disco era nuevo sin haber jamas sido usado por otro sist operativo)  ES POsible particionar lo que resta para usarlo sin tocar lo que ya ha sido instalado ? 
3) Hay alguna diferencia con particionar el disco completo desde el inicio ? Aclaro que no tengo la intencion de usar el resto del disco para instalar MS windows. 

Muchas gracias por la ayuda.
saludos
Protohumano :)

---

### Post by Applelnx on 2009-09-06
Creo que lo que necesitas lo podes hacer con el GPARTED. Lo podes instalar o lo tenes en el Live CD. Si lo que vos queres hacer es dedicarle todos los 80 GB a Ubuntu y solo le diste 25, eso se puede hacer sin ningun tipo de problema con este programa. Pero siempre, por las dudas se aconseja que hagas backups de las cosas mas importantes.

Saludos

---

### Post by staar on 2009-09-06
como bien te dijo Applelnx, podés usar gparted (lo encontrás en Sistema > Administración > Editor de particiones), en tu caso te convendría usarlo desde el livecd, para que puedas desmontar todas las particiones del disco (para modificar una partición, es preciso que esté desmontada)

para usar el espacio que tenés sin particionar en el disco, hay dos caminos, o creas una nueva partición en dicho espacio, formateándola con el sistema de archivos que más te guste, o extendés la partición actual para que ocupe todo el disco...

hay pocas diferencias prácticas entre las dos formas, en la primera, la partición que crees te figuraría como un Soporte nuevo aparte en el menú Lugares y podrías montarla y desmontarla *a piaccere*, en cambio con la segunda opción tendrías solo un Soporte, el mismo que tenés ahora, solo que más grande...

la segunda manera puede ser un poquito más complicada de llevar a cabo, ya que, al modificar la partición del sistema de ubuntu, muy probablemente se cambiaría su UUID (identificador único) y deberías buscar el nuevo valor, y corregirlo en el menu.lst del GRUB, porque sino no podrías iniciar el sistema, OJO, no es algo difícil de hacer...

saludos

---

### Post by alejandromafer on 2009-09-08
Las particiones las podes manejar como te exlicaron anteriormente. Para poder ver el espacio disponible tenés varias. 1).- desde una ventana de terminal con el comando df -H. Esto te mostrará todas las particiones que tenes montadas con su espacio disponible el espacio total, el porcentaje de uso y el punto de montaje de cada particion. 2).- La otra manera es gráfica. Podés utilizar el nautilus, y haciendo click sobre la carpeta personal o el icono de sistema de archivo te dice cuanto te queda libre en la particion. 3).- Si querés un detalle más elaborado de como está distribuido el espacio en el disco podés utilizar el analizador de uso en disco que se encuentra en Aplicaciones>Accesorios>Analizador de uso en disco.
Saludos!

---

### Post by Protohumano on 2009-09-08
iEstimados. Gracias por el consejo. Si, voy a optar por crear una nueva particion en el espacio restante y que se comporte como otro volumen. A los casos practicos es lo mismo y lo veo mas facil de implementar. 
Voy a ver si tengo el live cd para hacerlo. Si no es asi cual seria la aplicacion que Uds. sugieren ? 
Gracias Staar, AlejandroMafer y Applelnx por la ayuda.
saludos
P

---

### Post by luica on 2009-09-09
GPARTED fijate si no lo tenes instalado con Cntrl + F2 si no en el gestor de paquetes synaptic lo buscas es mas comodo que estar poniendo el live cd cada vez que lo precises

---

### Post by Protohumano on 2009-09-15
Muchas gracias Luica.
saludos

---

