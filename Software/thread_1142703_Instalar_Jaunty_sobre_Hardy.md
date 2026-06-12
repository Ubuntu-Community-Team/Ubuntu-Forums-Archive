---
title: "Instalar Jaunty sobre Hardy"
date: 2009-04-29
forum: Software
---

### Post by guidito73 on 2009-04-29
Bueno, visto y considerando que ya hace 1 año que no actualizo mi Ubuntu :P

Vamos a ver, quiero hacer una instalación limpia, y básicamente hago la misma estúpida pregunta que siempre, pero es que para mí es muy importante.

1) Cómo mantengo mi /home y swap? Simplemente formateando el directorio raíz y dejando a los otros tranquilos durante la actualización? (La hago desde un CD Alternate, tengo 256 de RAM no más)

2) NO, y repito, NO quiero ***** el GRUB porque eso sería privar a mi familia de Güindous con la respectiva paliza.

3) Tengo que instalar todos los programas de terceros de nuevo no? (Tampoco son tantos)

Desde ya gracias!

---

### Post by EnriqueK on 2009-04-29
1.- Tenés que elegir la opción de instalaxión manual , selecioná la partición donde está tu /home y elige como punto de montaje /home y eso si, asegurate de no tener marcada la opción de formatear. Sobre la Swap no haces nada, el instalador la va a detectar.
2.- Respecto al Grub no lo vas a estropear, pero es ppsible que te altere el orden de booteo , creo que te va a dejar como primera opción a Ubuntu , si actualmente tenés como primera opción a windoes, la forma simple de editarlo es usand el programa **startupmanager**
3.- Todos los programas hay que reinstalarlos, no solo los de terceros, lo que pasa si usas actualización automática, eso lo hace el sistema, en cambio si hacés una instalación de cero, los programas debés reibstalarlos manualnente.
Hay una forma que empleo para hacer una instalación en limpio pero totalmente desatendida  y esto se logra uando la información de paquetes instalados que te brinda por ejemplo usando Synaptic , para ello en la instalación actual entras a Synaptic--> Abrir-->Guardar seleciones como--> le das un nombre y marcas el casillero Guardar el estado completo no solo los cambios . Esto te va a generar un archivo plano con el nombre de todos los paquetes instalados con la particularidad de que solo contiene los nombres de los paquetes sin especificar las versiones de los mismos, por lo que esta información te va a permitir instalar todos esos paquetes para una versión igual o diferente de Ubuntu , para ello instala la nueva versión, entras a Synaptic --> Abrir--> Leer selecciones--> Pulsa el botón Aplicar y a a esperar a que se descarguen todos los nuevos paquetes y luego los instale, la espera puede ser larga, a mi me lleva unas 15 horas tinieno una conexión a 160 kbps .
Para este método se requieren básicamente dos cosas, una es usar repositorios equivalentes y la otra es tener una muy buena conexión a Internet y no te olvidés de asegurarte de portar el listado de paquetes para la nueva instalación y tomar nota de los repositorios usados para así activar repositorios equivalentes.
Usando este método he pasado de la versión 7.04 a la 8.04 (sin pasar para nada por la 7.10) y últimamente instalé la 8.10 64 bits basado en una lista de paquetes de una instalación de 8.10 32 bits que me pasó un amigo.
El éxito del proceso esta asegurado por que todo queda bajo el directo control de APT (en donde demuestra toda su potencia), lo que garantiza el extricto control de dependencias.
Otra cosa, el sistema de archivos que elijas para la nueva instalación es totalmente independiente de este método.

---

### Post by guidito73 on 2009-04-29
Buenisimo Enrique, gracias por la respuesta.

El GRUB obviamente lo voy a cambiar para que arranque Windows (mi vieja muere si arranca Ubuntu, no sabe que hacer) y el resto ya me lo voy figurando. Lamentablemente, también tengo una conexion de 128 Kbps =(

Supongo que me voy a llevar la PC a lo de mi novia (1 MB!) para poder instalar todos los paquetes.

El finde creo que estaría haciendo todo ya. Les cuento cuando termine.

---

### Post by EnriqueK on 2009-04-29
Si tenés baja velocidad de conexión, puedes hacer lo siguiente:
1.- Siguiendo la explicación anterior, antes de pulsar el botón Aplicar en Synaptic, te desconectás de Internet y luego le das a Aplicar, esto evidentemente va a dar un error que se manifiesta en un mensaje de alerta , entonces , esterá unos 30 segundos por las dudas ya que son muchas las lineas de error que debe informar , luego entrás al mensaje de alerta --> Click secundario--> Seleccionar todo--> Copiar y luego pegás a un nuevo documento de textos , seguidamente editás a ese documente para que solo contenga la URLs de descargas.
2.- Abrís al documento anterior con Open Office Calc , entre las opciones de separación elige  "Ancho fijo" , luego lo guardas como planilla de cáculo.
3.- Abre nuevemente la planilla anterior, selecciona todas las celdas --> entrás a Data --> Sort --Enter , esto para agrupar a reglón seguido todos las URLs y borrás todo lo que no sea una URL , al final te va a quedar la planilla con todas las URLs  --> guardas.
4.- Si el equipo a descargar será con Windows, la planilla anterior la debés salvar en formato .xls , la llevás al otro equipo y este debe tener instalado FlashGet , lo abres , abre con excel la planilla , selecciona todas las URLs y esto hará que se active el FlashGet y a descargar, previo seleccion de carpeta de descargas, etc, etc
5.- Si el equipo a descargar es con Linux , creas un archivo de textos , en la primer fila le pones 
#!/bin/sh
luego copias todas las celdas de la planilla
Seguidamente editas el acrchivo con Buscar - Reeplazar , en Buscar ponés http:// y en reeplazar ponés **wget -c http://**, o sea sería una forma de agregarle wget -c a todas la URLs , lo que queda es salvar este documente y ya tenés el Script de descargas.
6.- Una vez descargados todos los paquetes , entrás a Synaptic--> Archivo--> Inastalar paquetes descargados, seleccioná la carpeta donde está todos los paquete con un click (no sirve hacer doble click) , pulsa el botón Abrir , acepta todo y a esperar a que se instale todo.

---

### Post by guidito73 on 2009-04-29
Wow, suena complejo.

En fin, estuve revisando y tengo muchos paquetes al **** instalados, asi que voy a arrancar de cero y bajar únicamente los que más uso (que son poquísimos: TuxGuitar, Cairo-Dock, Wine, Deluge y a lo sumo algún que otro juego).

Gracias de nuevo por la respuesta, espero que todo salga bien =)

---

