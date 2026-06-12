---
title: "Howto: Aligerar el escritorio sin perder atractivo."
date: 2009-06-19
forum: Software
---

### Post by nopersona on 2009-06-19
Tema rescatado del antiguo foro, principalmente, para euipos modestos y para aprnder a configurar. De ese tiempo a esta fecha, apareció [LXDE]("http://es.wikipedia.org/wiki/LXDE"), que es bastante bueno. 

**RE-edición: 19 Junio 2009 - work in progress**

**Edición: 2 Enero 2008**

**Mejoras:**

**1.-** Script mejorado para Conky

**2.-** Script mejorado para Adesklet (yab)

**3.-** Posibilidad de usar Conky, adesklets y Nautilus sin perder los íconos.

=========================================================

Hola comunidad! Sé que estoy en deuda sobre el asunto de ordenar los temas (cosas que yo mismo propuse) pero la verdad, el tiempo y, como se dice, la vida, no me alcanza para hacer todo lo que desearía.

Para ir reivindicándome, de a poco, he confeccionado este minihowto sobre cómo embellecer un escritorio sin necesidad de beryl ni aplicaciones botaratas. En mi caso cada poquito de RAM cuenta, por ello, durante días me pregunté cómo optimizar mi escritorio (que estaba chupando bastante!) y no perder el atractivo. A trabajar  8) 

**Materiales**

*Conky
*Idesk
*Adesklets
*Imaginación en abundancia

[B]
1.- Instalando Conky[/B]

Connky es un monitor de sistema muy liviano, potente y de fácil configuración. Similar a GKrellM, pero para mi gusto es más cuidado en el aspecto y de fácil edición. Para instalarlo sinplemente lo buscamos en synpatic o descargamos el paquete desde [http://conky.sourceforge.net](http://conky.sourceforge.net) (fíjense en que sea la versión 1.4.5, la última, después les diré por qué)

Después de instalar el paquete debemos crear en nuestro Home un documento con el siguiente nombre: *.conkyrc *   Este archivo guardará los scripts que le indiquemos. En la pagina de Conky, sección screenshots, hay bastantes scripts a elección. El mío lo he confecionado según mis necesidades en base a dos de aquella página. 

Los scripts de lo que aparecerá en pantalla comienzan apenas se lee TEXT (modiqué el script para que mostrara la distro por defecto y el kernel a mi gusto, sin preguntarle al sistema ya que el nombre era un poco largo) La posisicón en nuestra pantalla dependerá de los valores que le demos en *Gap between borders* (X/Y respectivamente) 

Cuando ya tenemos listo y confiurado Conky a nuestro gusto, debemos activar el doble buffer en el xorg para que no pestañee de forma molesta. *sudo gedit /etc/X11/xorg.conf * Buscamos la linea MODULE y le agregamos: *Load "dbe"* Guardamos y reiniciamos Conky. En la versión 1.4.5 el problema del doble buffer viene solucionado, por eso les recomiendo instalar aquella (correción, ya vamos en la versión 1.4.9)

Si a alguien le interesa, mi configuración es la siguiente: (Pack de antigua  configuración, más mejora para Nautilus) 

[http://www.mediafire.com/?ab1mifj2nhj](http://www.mediafire.com/?ab1mifj2nhj)


**1.1 Y mis íconos? Conky se ve rarito **

Problema resuelto con la nueva configuración. Para  no tener problemas cuando se dibuje el escritorio al inicio, simplemente demoramos la carga de Conky con un script:


```
sudo gedit /usr/bin/inicio-conky
```Y agregan:

#!/bin/bash
 sleep 15 && conky;

(pueden cambiar el valor de 15 a otro que se acomode al tiempo de carga de su escritorio) 

Después le dan los permisos

```
sudo chmod a+x /usr/bin/inicio-conky
```Por último lo agregan a los programas de inicio. Preferencias -> Sesiones->inicio-conky

Con esto ya se soluciona la convivencia entre Conky y Nautilus en el escritorio.

Ahora, si desean sacar los iconos, por cosa de gustos, teclean Alt+F2 y con gconf-editor vamos a Apps>Nautilus>Preferences y desmarcamos la casilla de *Show_desktop* 


**2.-Idesk (Opcional)**

Bueno, la verdad es que solamente perdí 3 íconos al modificar nautilus: Equipo, la papelera y una carpeta. La papelera... al panel! Los dos restantes  preferiría añadirlos de otra manera. Pero bueno, si alguien  de todas fomas quiere tener iconos en su escritorio puede hacer lo siguiente.  
Para esto emplearemos Idesk y dejaremos esos íconos con toque especial. Idesk es una aplicación para, como ya dije, mostrar íconos-lanzadores en el escritorio que con uno o dos click ejecutan un acción. Para instalarlo simplemente ejecutamos el siguiente comando en un terminal: *sudo apt-get install idesk* Ahora creamos, en Home, un documento con el siguiente nombre *.ideskrc* Dentro del mismo debemos pegar lo siguiente:
[I]
table Config
   FontName: tahoma
   FontSize: 8
   FontColor: #ffffff
   Locked: false
   Transparency: 150
   HighContrast: true
   Shadow: true
   ShadowColor: #000000
   ShadowX: 1
   ShadowY: 2
   Bold: false
   ClickDelay: 300
   IconSnap: true
   SnapWidth: 55
   SnapHeight: 100
   SnapOrigin: BottomRight
   SnapShadow: true
   SnapShadowTrans: 200
   CaptionOnHover: false
 end
 table Actions
   Lock: control right doubleClk
   Reload: middle doubleClk
   Drag: left hold
   EndDrag: left singleClk
   Execute[0]: left doubleClk
   Execute[1]: right doubleClk
 end[/I]

**2.1.- Ahora crearemos los íconos. **

Para ello hacemos un directorio en home con el nombre *.idesktop* 

* $ mkdir /home/usuario/.idesktop*

Luego, dentro de aquel directorio creamos un archivo con el nombre *icono.lnk* o con el que queramos. 
Ya hemos creado nuestro primer ícono!  :) Ahora debemos definir los parámetros. Dentro del mismo archivo icono.lnk pegamos lo siguiente:

table Icon
   Caption: Opera
   Command: opera
   Icon: /home/usuario/iconos/opera.png
   X: 100
   Y: 50
 end

**Caption:** indica el nombre que va a tener
**Command:** indica el comando que va a ejecutar
**Icon:** aca indicamos la dirección del archivo de imagen
**X e Y:** indican la posición inicial que va a tener el archivo, de todos modos una vez creado se la damos arrastrando el icono hasta donde 
 queremos.

En este ejemplo el ícono es para Opera. Guardamos, cerramos y ejecutamos en un terminal *idesk* 
Sorpresa! en la pantalla tenemos un ícono bastante vistoso y agradable. Con Idesk las posibilidades son ilimitadas. En el archivo .ideskrc que creamos podemos darle las caracteristicas: transparency va de 0 a 255 / 0=Color sólido. 255=Transparente. 
Si lo dejamos en un rango de 100to y algo veremos el ícono como parte del fondo de escritorio y cuando pasemos el mouse se activará su color. Un efecto bastante llamativo y que consume nada de recursos. Lo mismo haremos si queremos agregar carpetas, el home, el equipo o un programa. La unica consideración que hay que tener en cuenta es que idesk soporta mejor los íconos en formato png. **No olvidar agregar Idesk a los programas de inicio. **


**3.- Instalando Adesklets. **

Siguiendo con la búsqueda de mejoras para mi escritorio, encontré Adesklets, que vienen siendo *casi* lo mismo que los gdesklets, pero estos ocupan muchos menos recursos. Como siempre me ha gustado saber el clima (miren que Conce parece Trópico!) y tener la barrita para mis aplicaciones (únicos desklets que uso siempre), usaba la starterbar y el informe del clima. La  starterbar me chupaba demasiado para una simple barra, lo mismo que el weather del clima, mal mal gdesklets. 


Con Adesklets las cosas son distintas, se nota su bajo consumo, sobre todo al inicio de sesión. Para instalarlo simplemente se busca en synaptic, o si les resulta más cómodo desde el terminal. No pesa casi nada. Una vez intalado debemos seleccionar el desklet que deseamos en [http://adesklets.sourceforge.net/desklets.html](http://adesklets.sourceforge.net/desklets.html) y luego hacer un directorio .desklets en nuestro home en donde descomprimiremos y guardaremos todos nuestros desklets. 


**3.1.- Instalando y probando los desklets**

Una vez que tenemos todo en orden debemos agregar nuestros desklets, para ello nuestro amigo terminal nos ayudará. Existe una herramienta gráfica que se activa con el comando *adesklets_installer*, pero lo que es a mí no me funcionó nunca (después de instalar por terminal me reconoce los desklets instalados eso sí).  

Ahora vamos a instalar los desklets. Supondremos que bajamos weatherforecast-0.2.0 (para el clima) y yab-0.0.2 (barra tipo mac) y que ambos están en el directorio .desklets de nuestro Home.

Accedemos al directorio de weatherforecast:

* $ weatherforecast-0.2.0*

luego debemos probar el desklet:

*~/.desklets/weatherforecast-0.2.0$ ./weatherforecast.py*

y nos saldrá algo así:

*Do you want to (r)egister this desklet or to (t)est it? *


Para probar el desklet apretamos t y si está en condiciones de ejecutarse aparecerá en nuestra pantalla (sin opciones de configurar) Para registrarlo pulsamos r y lo cerramos con Ctrl+C. El desklet quedará registrado en el archivo de nuestro Home *.adesklets* (en ese archivo se guardarán las configuraciones de nuestros desklets, es importante respaldarlo por si acaso) Para registrar la barra yab hacemos lo mismo: 

[I]$ cd ~/.desklets/yab-0.0.2

~/.desklets/yab-0.0.2$ ./yab.py[/I]


**3.2.- Configurando los Desklets.**

Una vez que tenemos  probados y registrados nuestros desklets debemos configurarlos. Para ello en la carpeta de cada uno viene un archivo con el nombre *config.txt* Editando dicho archivo tendremos las características personalizadas. Por ejemplo, los íconos y fondos de la barra yab son bastantes feos, pero editando la plantilla puede quedar fabulosa, mi plantilla es la siguiente:

[I]#    
id0 = {'bar_background_1': None,
 'bar_background_2': None,
 'bar_foreground': None,
 'bar_gradient_angle': 0,
 'bar_height': 32,
 'bar_opacity_1': 100,
 'bar_opacity_2': None,
 'caption_above': True,
 'caption_color': 'AAAAAA',
 'caption_delay': 0.10000000000000001,
 'caption_fade_in': True,
 'caption_fade_in_duration': 1,
 'caption_fade_in_steps': 1,
 'caption_font': 'Vera',
 'caption_size': 20,
 'click_effect': 'tint(alpha=100,red=255,green=255,blue=255);',
 'click_effect_duration': 0.10000000000000001,
 'icon_max_height': 128,
 'icon_max_width': 128,
 'icon_maximize_threshold': 0.90000000000000002,
 'icon_min_height': 64,
 'icon_min_width': 64,
 'icon_spacing': 5,
 'icons': [('opera.png', 'Opera', 'opera'),
           ('amsn.png', 'Amsn', 'amsn'),
           ('kaboodle.png', 'Xmms', 'xmms'),
           ('vlc.png', 'Vlc', 'vlc'),
           ('abiword.png', 'Abiword', 'abiword'),
           ('k3b.png', 'K3b', 'k3b'),
           ('Azureus.png', 'Azureus', 'azureus'),
           ('tux.png', 'Conectar', 'sudo pon dsl-provider'),
           ('specto.png', 'Synaptic', 'gksu /usr/sbin/synaptic')]}[/I]

No olvidar poner los íconos que deseamos en la carpeta "icons" de yab, respetar los nombres (mayúsculas si las hay) y que la secuencia es la siguiente:

[I]('opera.png', 'Opera', 'opera'),

('nombre_del_icono', nombre_lanzador', 'comando_lanzador'), [/I]

Con weatherforecast es similar, en config.txt modificamos todo, iconos, tamaño y el código de nuestra ciudad. 

Guardamos todos los cambios y **agregamos adesklets a los programas de inicio. **

**Edit:** Ahora, con Conky y Nautilus en el escritorio, puede que algunos adesklets no arranquen, para solucionar esto, simplemente invocamos el proceso para Nautilus y demoramos su carga:


```
sudo gedit /usr/bin/inicio-adesklets
```Y agregan:

#!/bin/bash
sleep 19 && adesklets --nautilus;


Después le dan los permisos

```
sudo chmod a+x /usr/bin/inicio-adesklets
```Por último lo agregan a los programas de inicio. Preferencias -> Sesiones-> inicio-adesklets

Con este último paso tenemos la fiesta en paz entre Conky, Nautilus y Adesklets :wink: 



**4.- Predeterminar Otro navegador de ficheros**

Obtuve una considerable mejora al lograr predeterminar Thunar y PcMan Filemanager en vez de Nautilus (que chupa bastante) pero como Todavía no me atrevo a soltar la configuración (ya, lo diré) lo que sí pueden hacer para predeterminar Thunar o PCman de forma ficticia y segura es lo siguiente:

**Forma Ficticia:**

Instalar Thunar o PCman

# sudo aptitude install pcmanfm

# sudo aptitude install thunar


Luego hacemos un lanzador para que Thunar o PCMan abran dicha ruta, en este caso lo haré con el único ícono que dejé en mi escritorio por medio de Idesk, sería así:

table Icon
Caption:
Command: Thunar
Icon: /home/su_ruta_del_icono.png
X: 717
Y: 2
end



**Forma real:**

1.- Abrrimos la pantalla de Sesiones (Sistema > Preferencias > Sesiones)
2.- Seleccionamos la pestaña "Sesión actual".
3.- En la lista de programas en ejecución buscamos y seleccionamos donde aparece "nautilus".
4.- En la parte inferior de la lista, cambiamos el Estilo de Restart (predeterminado) a Trash.
5.- Quitar.


Con esto cierramos Nautilus y evitamos que se abra automáticamente la próxima vez que iniciemos sesión (Para revertirlo  basta con ejecutar Nautilus normalmente y él se encarga de registrarse como predeterminado. [Alt + F2] nautilus y le damos ejecutar.

Cargar PCMan File Manager automáticamente en el inicio de sesión (opcional)

1.- Abrimos la pantalla de Sesiones (Sistema > Preferencias > Sesiones)
2.- En la pestaña "Programas de inicio",  click en agregar.
3.- Completamos la información: PCMan File Manager (Nombre), pcmanfm (Comando)

**Ahora que se encargue de los íconos:**

1.- Abrir PCMan File Manager
2.- Menú Editar > Preferencias
3.- Pestaña Escritorio
4.- Activar la opción «Mostrar iconos en el escritorio» (y eventualmente la otras)

Lo último  es lograr que PCMan  (o Thunar) se abra cuando seleccionemos alguno de los itemes del menú Lugares (Equipo, Carpeta personal). (Si reemplazaste Nautilus por PCMan File Manager, al intentar abrir una de estas localidades se ejecutará Nautilus y volverá a ser el gestor predeterminado :S)

2.- Editar los archivos:

```
sudo gedit /usr/share/applications/nautilus-folder-handler.desktop
``````
sudo gedit /usr/share/applications/nautilus-computer.desktop
``` (para Equipo)

3.- Buscar la línea que comienza con Exec y reemplazarla por Exec=pcmanfm (PCMan File Manager) o Exec=thunar (Thunar)

4.- (Opcional). Para explorar como root reemplazamos la línea por Exec=gksu pcmanfm (PCMan File Manager) o Exec=gksu thunar (Thunar). 


En Feisty funciona, no sé si en Gutsy, he leído que también haría falta modificar 

```
/usr/share/applications/nautilus-folder-handler.desktop
```Si desean volver al principio, basta con restaurar 

/usr/share/applications/nautilus-folder-handler.desktop
/usr/share/applications/nautilus-computer.desktop


Más info:

[http://www.enricozini.org/2006/tips/pcmanfm-nautilus.html](http://www.enricozini.org/2006/tips/pcmanfm-nautilus.html)

Ya deberían tener predeterminado otro navegador de ficheros :P 


Si todo ha salido bien, tendremos un muy bello escritorio con un muy muy bajo consumo. Qué más se puede pedir? 

Y eso vendría siendo. Doy por terminado este Howto (ahora espero que sí) Unas nuevas caps:



**Conky+Adesklets+Nautilus conviviendo en paz**

[[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1763382Pantallazo.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo-1763382.html") [[IMG]http://s1.subirimagenes.com/imagenes/previo/thump_1763398Pantallazo.png[/IMG]]("http://www.subirimagenes.com/imagen-de-Pantallazo-1763398.html")


P.P.S.: Una última consideración antes que se me olvide. El desklets del clima me falló al cambiarle los íconos que traía por los de "Liquid" que vienen en la misma carpeta y que son más bonitos. Esto sucedió porque sólo venían 44 íconos y se necesitan 49. Lo solucioné copiando los últimos 4 íconos de la carpeta weather.com a la de Liquid. Fin.

Espero que este howto sirva, va con todo cariño  :D 

Saludos gente!

---

### Post by Carlos C on 2009-08-11
[Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [7 de agosto de 2009]("http://www.ubuntu-cl.org/grupos/foro/howto-aligerar-el-escritorio-sin-perder-atractivo")

---

### Post by Maciett on 2009-09-10
Hola,

Estan muy buenas estas aplicaciones, pero después de aplicar la guía me quedó una pura duda, ¿Cömo hiciste para que quedara transparente como parte del escritorio? Que al ejecutarlo a mi me sale como una ventana negra chica toda fea >.<. Eso.

Saludos

---

