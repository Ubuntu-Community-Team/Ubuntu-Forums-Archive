---
title: "Problemas para instalar Iceweasel en Kubuntu 8.10"
date: 2009-05-05
forum: Software
---

### Post by phyro on 2009-05-05
Luego de que la lista de correo directamente no me quiera(mandé 56 millones de veces el email preguntando algo, y nunca llegó, lo mandé sin links, con links, corto, largo, etc :P ), recurro al foro :P :

**¡Hola a todos! Quise instalar Iceweasel en Ubuntu 8.10 pero tengo algunos problemas. Baje el paquete debian de los repos de Debian:**

[http://http.us.debian.org/debian/pool/main/i/iceweasel/](http://http.us.debian.org/debian/pool/main/i/iceweasel/)

**Exactamente, este paquete:**

[http://http.us.debian.org/debian/pool/main/i/iceweasel/iceweasel_3.0.9-1_i386.deb](http://http.us.debian.org/debian/pool/main/i/iceweasel/iceweasel_3.0.9-1_i386.deb)

**A la hora de instalar:**

phyro@phyro:~$ sudo dpkg -i iceweasel_3.0.9-1_i386.deb 
Seleccionando el paquete iceweasel previamente no seleccionado.
(Leyendo la base de datos ...                                  
212555 ficheros y directorios instalados actualmente.)         
Desempaquetando iceweasel (de iceweasel_3.0.9-1_i386.deb) ...  
dpkg: error al procesar iceweasel_3.0.9-1_i386.deb (--install):
 intentando sobreescribir `/usr/bin/firefox', que está también en el paquete firefox-3.0
Procesando activadores para man-db ...                                                  
Se encontraron errores al procesar:                                                     
 iceweasel_3.0.9-1_i386.deb                   

[B]Entonces, remuevo firefox y firefox-3.0 y lo logré instalar correctamente.
Pero a la hora de ejecutar:[/B]

phyro@phyro:~$ iceweasel              
exec: 293: /usr/lib/iceweasel/firefox-bin: not found

**Entonces, vuelvo a instalar Firefox:**

phyro@phyro:~$ sudo apt-get install firefox                                                              
Leyendo lista de paquetes... Hecho                                                                       
Creando árbol de dependencias                                                                            
Leyendo la información de estado... Hecho                                                                
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.                        
  python-kde4-dev                                                                                        
Utilice «apt-get autoremove» para eliminarlos.                                                           
Se instalarán los siguientes paquetes extras:                                                            
  apturl firefox-3.0 firefox-3.0-branding libcairo-perl libglib-perl libgnome2-canvas-perl libgnome2-perl
  libgnome2-vfs-perl libgtk2-perl python-vte ubufox                                                      
Paquetes sugeridos:                                                                                      
  firefox-3.0-gnome-support latex-xft-fonts libgtk2-perl-doc                                             
Se instalarán los siguientes paquetes NUEVOS:                                                            
  apturl firefox firefox-3.0 firefox-3.0-branding libcairo-perl libglib-perl libgnome2-canvas-perl       
  libgnome2-perl libgnome2-vfs-perl libgtk2-perl python-vte ubufox                                       
0 actualizados, 12 se instalarán, 0 para eliminar y 0 no actualizados.                                   
Se necesita descargar 2578kB/3736kB de archivos.                                                         
Se utilizarán 12,9MB de espacio de disco adicional después de desempaquetar.                             
¿Desea continuar [S/n]? s                                                                                
Des:1 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid/main python-vte 1:0.17.4-0ubuntu1 [29,1kB]                   
Des:2 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid/main apturl 0.2.7ubuntu1 [16,4kB]                            
Des:3 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid/main libcairo-perl 1.060-1 [116kB]                           
Des:4 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid/main libglib-perl 1:1.183-1 [425kB]                          
Des:5 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid/main libgtk2-perl 1:1.183-1 [1253kB]                         
Des:6 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid/main libgnome2-canvas-perl 1.002-1+b1ubuntu3 [134kB]                 
Des:7 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid/main libgnome2-vfs-perl 1.080-1build2 [219kB]                        
Des:8 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid/main libgnome2-perl 1.042-1build2 [332kB]                            
Des:9 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) intrepid-updates/main ubufox 0.6-0ubuntu1.8.10.1 [54,3kB]                     
Descargados 2578kB en 21s (121kB/s)                                                                              
Seleccionando el paquete python-vte previamente no seleccionado.                                                 
(Leyendo la base de datos ...                                                                                    
212569 ficheros y directorios instalados actualmente.)                                                           
Desempaquetando python-vte (de .../python-vte_1%3a0.17.4-0ubuntu1_i386.deb) ...                                  
Seleccionando el paquete apturl previamente no seleccionado.                                                     
Desempaquetando apturl (de .../apturl_0.2.7ubuntu1_all.deb) ...                                                  
Seleccionando el paquete firefox-3.0-branding previamente no seleccionado.                                       
Desempaquetando firefox-3.0-branding (de .../firefox-3.0-branding_3.0.10+nobinonly-0ubuntu0.8.10.1_i386.deb) ... 
Seleccionando el paquete firefox-3.0 previamente no seleccionado.                                                
Desempaquetando firefox-3.0 (de .../firefox-3.0_3.0.10+nobinonly-0ubuntu0.8.10.1_i386.deb) ...                   
dpkg: error al procesar /var/cache/apt/archives/firefox-3.0_3.0.10+nobinonly-0ubuntu0.8.10.1_i386.deb (--unpack):
 intentando sobreescribir `/usr/bin/firefox', que está también en el paquete iceweasel                           
Seleccionando el paquete firefox previamente no seleccionado.                                                    
Desempaquetando firefox (de .../firefox_3.0.10+nobinonly-0ubuntu0.8.10.1_all.deb) ...                            
Seleccionando el paquete libcairo-perl previamente no seleccionado.                                              
Desempaquetando libcairo-perl (de .../libcairo-perl_1.060-1_i386.deb) ...                                        
Seleccionando el paquete libglib-perl previamente no seleccionado.                                               
Desempaquetando libglib-perl (de .../libglib-perl_1%3a1.183-1_i386.deb) ...                                      
Seleccionando el paquete libgtk2-perl previamente no seleccionado.                                               
Desempaquetando libgtk2-perl (de .../libgtk2-perl_1%3a1.183-1_i386.deb) ...                                      
Seleccionando el paquete libgnome2-canvas-perl previamente no seleccionado.                                      
Desempaquetando libgnome2-canvas-perl (de .../libgnome2-canvas-perl_1.002-1+b1ubuntu3_i386.deb) ...              
Seleccionando el paquete libgnome2-vfs-perl previamente no seleccionado.                                         
Desempaquetando libgnome2-vfs-perl (de .../libgnome2-vfs-perl_1.080-1build2_i386.deb) ...                        
Seleccionando el paquete libgnome2-perl previamente no seleccionado.                                             
Desempaquetando libgnome2-perl (de .../libgnome2-perl_1.042-1build2_i386.deb) ...                                
Seleccionando el paquete ubufox previamente no seleccionado.                                                     
Desempaquetando ubufox (de .../ubufox_0.6-0ubuntu1.8.10.1_all.deb) ...                                           
Procesando activadores para man-db ...                                                                           
Se encontraron errores al procesar:                                                                              
 /var/cache/apt/archives/firefox-3.0_3.0.10+nobinonly-0ubuntu0.8.10.1_i386.deb

**Y trato de corregir esto:**

phyro@phyro:~$ sudo apt-get -f install                                                                   
Leyendo lista de paquetes... Hecho                                                                       
Creando árbol de dependencias                                                                            
Leyendo la información de estado... Hecho                                                                
Corrigiendo dependencias... Listo                                                                        
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.                        
  python-kde4-dev                                                                                        
Utilice «apt-get autoremove» para eliminarlos.                                                           
Se instalarán los siguientes paquetes extras:                                                            
  firefox-3.0                                                                                            
Paquetes sugeridos:                                                                                      
  firefox-3.0-gnome-support latex-xft-fonts                                                              
Se instalarán los siguientes paquetes NUEVOS:                                                            
  firefox-3.0                                                                                            
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.                                    
11 no instalados del todo o eliminados.                                                                  
Se necesita descargar 0B/887kB de archivos.                                                              
Se utilizarán 3539kB de espacio de disco adicional después de desempaquetar.                             
¿Desea continuar [S/n]? s                                                                                
(Leyendo la base de datos ...                                                                            
213055 ficheros y directorios instalados actualmente.)                                                   
Desempaquetando firefox-3.0 (de .../firefox-3.0_3.0.10+nobinonly-0ubuntu0.8.10.1_i386.deb) ...           
dpkg: error al procesar /var/cache/apt/archives/firefox-3.0_3.0.10+nobinonly-0ubuntu0.8.10.1_i386.deb (--unpack):
 intentando sobreescribir `/usr/bin/firefox', que está también en el paquete iceweasel                           
Se encontraron errores al procesar:                                                                              
 /var/cache/apt/archives/firefox-3.0_3.0.10+nobinonly-0ubuntu0.8.10.1_i386.deb                                   
E: Sub-process /usr/bin/dpkg returned an error code (1) 

[B]Al desinstalar IceWeasel, puedo instalar normalmente Firefox. Pero sin Firefox, parece que Iceweasel no anda. Estoy en un bucle infinito :P . ¿Qué puedo hacer?.

Gracias desde ya :P [/B]

---

### Post by phyro on 2009-05-06
UP (a.k.a. "No es por nada, pero no se desesperen XD")

---

### Post by Hei Ku on 2009-05-06
revisaste las dependencias del paquete de iceweasel?  Seguro que tenes todo, aparte de firefox?

---

### Post by pablo.s on 2009-05-06
Algúna razón en especial para usar
Iceweasel?

[Acá creo que está para bajar]("http://ftp.gnu.org/gnu/gnuzilla/3.0.9-g1/") cómo
binario comprimido, para utilizarlo
paralelo a Firefox.

EDIT: Ironicamente con este IceCat,
o IceWeasel puedo ver este foro sin
las demoras que me provoca el
Firefox... Y estuve a un pelo de bardear
a phyro por la consulta, snif...

---

### Post by phyro on 2009-05-07
> **Hei Ku said:**
> revisaste las dependencias del paquete de iceweasel?  Seguro que tenes todo, aparte de firefox?

No se quejó de nada en la instalación, como haría para fijarme las dependencias de un paquete?.

> **pablo.s said:**
> Algúna razón en especial para usar
Iceweasel?

[Acá creo que está para bajar]("http://ftp.gnu.org/gnu/gnuzilla/3.0.9-g1/") cómo
binario comprimido, para utilizarlo
paralelo a Firefox.

EDIT: Ironicamente con este IceCat,
o IceWeasel puedo ver este foro sin
las demoras que me provoca el
Firefox... Y estuve a un pelo de bardear
a phyro por la consulta, snif...

Porque es libre de verdad. Pensaba en ser un poco más libre, ya que uso Opera. Pero si pienso cambiar de navegador, voy a cambiar por uno que me garantize verdaderamente mi libertad :P . La idea es tenerlo instalado, no ejecutar el binario :P .

¡Saludos!

---

### Post by pablo.s on 2009-05-07
> **phyro said:**
>  La idea es tenerlo instalado, no ejecutar el binario

Y cual es la diferencia entre
tenerlo instalado y ejecutar
el binario? 

Te dejo pensandolo un rato eh!

---

### Post by phyro on 2009-05-07
> **pablo.s said:**
> Y cual es la diferencia entre
tenerlo instalado y ejecutar
el binario? 

Te dejo pensandolo un rato eh!

Que, no tengo que ir carpeta por carpeta buscando el lanzador, y que, cuando lo ejecutas así o creas un enlace simbólico(o como se llame), cuando cerras el programa quedan colgados procesos haciendo nada :P(al menos me pasa con Firefox 3.5 que lo tengo en binario y un enlace con el comando "firefox3").

---

### Post by pablo.s on 2009-05-07
Bueno, entonces buena suerte en
la búsqueda de la libertad!
Saludos.

---

### Post by Hei Ku on 2009-05-07
Tiene razon con lo del menu. Es sólo una molestia, pero tiene razon. :)

En cuanto a las dependencias, podes fijarte en [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) la informacion sobre el paquete de iceweasel y verificar las dependencias.

---

### Post by phyro on 2009-05-08
Tengo todas las dependencias, parece :P .
¿Qué hago ahora :P ?

---

### Post by Hei Ku on 2009-05-08
Desinstala el firefox, con la opción purge. Te da algún mensaje de error al desinstalar, como que no pudo borrar alguna carpeta?

sudo aptitude remove firefox

y despues instala el iceweasel, con el dpkg.

---

### Post by phyro on 2009-05-09
> **Hei Ku said:**
> Desinstala el firefox, con la opción purge. Te da algún mensaje de error al desinstalar, como que no pudo borrar alguna carpeta?

sudo aptitude remove firefox

y despues instala el iceweasel, con el dpkg.

Sin uno, no me dejaba tener el otro. Pero ya solucioné este problema, instalando Icecat(pregunté en la lista de correo):

[https://lists.ubuntu.com/archives/ubuntu-ar/2009-May/019780.html](https://lists.ubuntu.com/archives/ubuntu-ar/2009-May/019780.html)

¡Gracias igualmente!

---

