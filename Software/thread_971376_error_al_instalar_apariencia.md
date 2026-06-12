---
title: "error al instalar apariencia"
date: 2008-11-04
forum: Software
---

### Post by papocha on 2008-11-04
estube leyendo y nose por que todos tienen facilidad para instalar los temas, pregunte pero nadie entendia mi error, aca les pongo el error que me manda al instalar la mayoria de los temas, si me podrian ayudar seria buenisimo gracias =D

"El tema no se mostrara como se pretende porque el motor de temas GTK+ necesario <> no esta instalado"

 si alguien me podria decir cual es el problema seria de gran ayuda

---

### Post by faktorqm on 2008-11-05
Tenes como motores GTK estos:

```
faktorqm@the-edge:~$ aptitude search gtk-engines
p   gtk-engines-begtk                                                           - Tema de escritorio parecido a BeOS para GTK+.                                        
p   gtk-engines-eazel                                                           - Motor de temas GTK+ Eazel, incluye el tema Crux                                      
p   gtk-engines-geramik                                                         - Geramik GTK1.x Theme                                                                 
p   gtk-engines-geramik-data                                                    - Geramik GTK Theme bitmaps                                                            
p   gtk-engines-lighthouseblue                                                  - LighthouseBlue theme for GTK+ 1.2                                                    
p   gtk-engines-mist                                                            - A flat theme for GTK+ 1.2                                                            
p   gtk-engines-mono                                                            - Mono theme for GTK+ 1.2                                                              
p   gtk-engines-qtpixmap                                                        - QtPixmap GTK1.x theming engine                                                       
p   gtk-engines-thingeramik                                                     - ThinGeramik GTK1.x Theme                                                             
p   gtk-engines-thingeramik-data                                                - ThinGeramik GTK Theme bitmaps                                                        
p   gtk-engines-thinice                                                         - Tema 'Hielo fino' para GTK+ 1.2                                                      
p   gtk-engines-xenophilia                                                      - Customisable GTK+ engine with a plain look                                           
faktorqm@the-edge:~$ 

```

No se cual es el que te sirve, pero de ultima (y si tenes espacio en disco de sobra) instalatelos todos y despues fijate cual activas. Espero que te haya servido. Salu2!

EDITO: Tambien tenes estos que creo que son mejores:

```
p   gtk2-engines                                                                - theme engines for GTK+ 2.x                                                           
p   gtk2-engines-blueheart                                                      - Blueheart GTK+ 2.x Theme                                                             
p   gtk2-engines-cleanice                                                       - CleanIce themes for GTK+ 2.x                                                         
v   gtk2-engines-clearlooks                                                     -                                                                                      
v   gtk2-engines-crux                                                           -                                                                                      
v   gtk2-engines-gartoon                                                        -                                                                                      
p   gtk2-engines-geramik                                                        - Geramik GTK2.x Theme                                                                 
p   gtk2-engines-gtk-qt                                                         - transitional dummy package                                                           
v   gtk2-engines-highcontrast                                                   -                                                                                      
v   gtk2-engines-industrial                                                     -                                                                                      
v   gtk2-engines-lighthouseblue                                                 -                                                                                      
p   gtk2-engines-magicchicken                                                   - Magic Chicken themes for GTK+ 2.x                                                    
v   gtk2-engines-metal                                                          -                                                                                      
v   gtk2-engines-mist                                                           -                                                                                      
p   gtk2-engines-murrine                                                        - cairo-based gtk+-2.0 theme engine                                                    
p   gtk2-engines-mythbuntu                                                      - Mythbuntu GTK+ 2.x Theme                                                             
p   gtk2-engines-pixbuf                                                         - Pixbuf-based theme for GTK+ 2.x                                                      
p   gtk2-engines-qtcurve                                                        - This is a set of widget styles for Gtk2 based apps                                   
p   gtk2-engines-qtpixmap                                                       - QtPixmap GTK2.x theming engine                                                       
v   gtk2-engines-redmond95                                                      -                                                                                      
p   gtk2-engines-sapwood                                                        - Pixbuf-based theme engine for GTK+ 2.x                                               
p   gtk2-engines-sapwood-dbg                                                    - Pixbuf-based theme engine for GTK+ 2.x -- debug symbols                              
v   gtk2-engines-smooth                                                         -                                                                                      
v   gtk2-engines-spherecrystal                                                  -                                                                                      
p   gtk2-engines-thingeramik                                                    - ThinGeramik GTK2.x Theme                                                             
v   gtk2-engines-thinice                                                        -                                                                                      
p   gtk2-engines-ubuntulooks                                                    - 'ubuntulooks' theme for GTK+ 2.x                                                     
p   gtk2-engines-wonderland                                                     - Wonderland theme for GTK+ 2.0                                                        
p   gtk2-engines-xfce                                                           - A GTK+-2.0 theme engine for Xfce                                                     

```

y obviamente los instalas con el gestor de paquetes synaptic, o con 

```
sudo apt-get install <paquete>
```

ejemplo:

```
sudo apt-get install gtk2-engines-xfce
```

Salu2!

---

### Post by sajnox on 2008-11-05
> **papocha said:**
> estube leyendo y nose por que todos tienen facilidad para instalar los temas, pregunte pero nadie entendia mi error, aca les pongo el error que me manda al instalar la mayoria de los temas, si me podrian ayudar seria buenisimo gracias =D

"El tema no se mostrara como se pretende porque el motor de temas GTK+ necesario <> no esta instalado"

 si alguien me podria decir cual es el problema seria de gran ayuda

Que tema queres instalar?

De donde lo bajaste?

---

### Post by papocha on 2008-11-05
> **sajnox said:**
> Que tema queres instalar?

De donde lo bajaste?

el tema que probe es este hemoglobinus, y lo baje de gnome-look.org, pero la verdad que me pasa eso con la mayoria de los temas que quiero instalar, me manda el error ese.

---

### Post by Zeq on 2008-11-05
En gnome-look encontre tres temas que saltan con hemoglobinus.

Para dos de ellos, necesitas **GTK 2** y para el otro **Compiz**.

Asegurate de tenerlos instalados y funcionando.

Si queres saber que es GTK: [http://www.gtk.org](http://www.gtk.org)
En la seccion de download tenes para bajar las versiones.

Pero pera, primero y mas importante: que version de Ubuntu estas usando?

---

### Post by ramiro_md on 2008-11-05
Por ahí no es la solución y estoy erradisimo con el tema :P..pero a veces bajo themes de gnome-look.org y bajan en un tar.bz, cuando o arrastro hasta el selector de themes me tira un error, entonces descomprimo el tar.bz y suele quedar o otro fichero comprimido o una carpeta, al intentar arrastrar eso que queda descomprimido se instala de toque.

Espero sirva mi respuesta. Un saludo.
Abrazo de pingüino.

---

### Post by papocha on 2008-11-05
> **ramiro_md said:**
> Por ahí no es la solución y estoy erradisimo con el tema :P..pero a veces bajo themes de gnome-look.org y bajan en un tar.bz, cuando o arrastro hasta el selector de themes me tira un error, entonces descomprimo el tar.bz y suele quedar o otro fichero comprimido o una carpeta, al intentar arrastrar eso que queda descomprimido se instala de toque.

Espero sirva mi respuesta. Un saludo.
Abrazo de pingüino.

ubuntu 8.10 intrepid instalacion desde cero, osea no instale arriba del hardy sino que formatie e instale la version nueva desde cero

---

