---
title: "MySQL Administrator &amp; Pinnacle PCTV"
date: 2011-03-05
forum: Software
---

### Post by E_Blue on 2011-03-05
Hola, no se por donde empezar, hace 3 meses que estoy tratando de hacer funcionar la placa capturadora PCTV Rave pero si bien Ubuntu 10.04LTS la reconoce no es así desde las aplicaciones como XawTv, Me TV, Myth TV Front End, y TV Time.

Originalmente tenia instalado Ubuntu 8.04LTS y actualice desde GUI y había empezado a funcionar relativamente bien, no se como, pero se veía en TV Time, le faltaba intensidad al color pero ya el audio se oía bien cosa que antes no pues se oía solo ruido blanco y muy al fondo el sonido del canal.

Bueno, hace un tiempo atrás me puse a mirar el histórico de la red en el monitor del sistema y vi actividad aun cuando no había aplicaciones visibles corriendo así que instale el Wireshark para ver de que eran esos paquetes y vi que era el server de MySQL, asustado porque pensé que se me estaban metiendo en la maquina desinstale MySQL server y todo lo relacionado.
MySQL server lo tenia instalado porque Myth TV lo requiere así, no se para que usa la base de datos pero si no no funciona.

A partir de ese momento no me anduvo mas TV Time, me muestra pantalla azul como que no hay señal.

Ahora quiero reinstalar MySQL para hacer funcionar Myth TV pero no existe ni base de datos ni usuario ni contraseña; tal es así que desde el GUI de MySQL Administrator solo puedo "loguearme" si dejo vacíos los campos de usuario y contraseña y me conecto al puerto 3306 del localhost, es decir esta todo en blanco.
Además si quiero crear un usuario desde el GUI con "Add New User" se cierra misteriosamente MySQL Administrator.
Trato de crear un usuario pero no hay base de datos en donde guardar los permisos de acceso y no se por donde empezar, probé desde el GUI y desde consola pero nada, parece un circulo vicioso.

Amen de la macana que me mande, ¿Que me sugieren hacer?:confused:
Ya reinstale MySQL Server y tengo el PHP funcionado.

Desde ya les agradezco cualquier dato. :)

---

### Post by biale on 2011-03-06
Solo para empezar, y suponiendo que MySQL sea un prerrequisito de Myth TV, directamente reinstala Myth TV y deja que el se arregle con sus dependencias y configuraciones.

---

### Post by E_Blue on 2011-03-07
Eso ya lo intente y no funciona, si no hay base de datos no puedo configurar Myth TV.

Es una lastima porque el resto funciona mucho mas rápido que Windows XP. :(

---

