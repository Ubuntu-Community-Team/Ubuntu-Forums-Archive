---
title: "Kubuntu 9.10 no guarda mi configuracion de pantalla"
date: 2010-04-19
forum: Software
---

### Post by matias_tati on 2010-04-19
Hola cada vez que inicio debo clickear el icono pantalla en prefeencias del sistema para que se establezca mi resolucion 1440x900, lo mismo me pasaba con Gnome pero se soluciono solo de un dia para otro. Gracias.

---

### Post by faktorqm on 2010-04-20
Yo tengo el mismo problema, antes con kubuntu 9.10 y ahora con Chakra alpha 5. Te digo como lo solucione

```
 cvt 1440 900 60
```
y te tira algo como esto:

```
# 1440x900 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
  Modeline "1440x900_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```

y despues haces (copia todo lo que aparece despues de la palabra modeline incluidas las comillas)

```
xrandr --newmode "1440x900_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```

y luego para hacer el cambio persistente haces

```
xrandr --addmode DVI-1 "1440x900_60.00"
```

donde dice DVI-1 en realidad tenes que poner la salida que tengas (en mi caso era VGA-0 por ejemplo, y creo que eso lo hacias con el comando "xrand -q" (sin comillas). Salu2!

fuente: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by matias_tati on 2010-04-20
El ultimo paso no lo pude hacer no se cual es la saliday el comando que me pasaste creo que estaba mal te falto una "r" creo si ee asi me arrojo esto.
Gracias.
```
matias@PCmatias:~$ xrandr -q
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1600 x 1200
default connected 1440x900+0+0 0mm x 0mm
   1600x1200      50.0
   1440x900       51.0*
   1400x1050      52.0     53.0     54.0
   1360x768       55.0     56.0
   1280x1024      57.0     58.0
   1280x960       59.0
   1152x864       60.0     61.0     62.0     63.0
   1024x768       64.0     65.0     66.0
   960x600        67.0
   960x540        68.0
   840x525        69.0     70.0     71.0
   832x624        72.0
   800x600        73.0     74.0     75.0     76.0
   720x450        77.0
   700x525        78.0     79.0
   680x384        80.0     81.0
   640x480        82.0     83.0     84.0     85.0     86.0
   512x384        87.0     88.0
   400x300        89.0
   320x240        90.0     91.0
  1440x900_60.00 (0x1ff)  106.5MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
matias@PCmatias:~$

```

---

### Post by faktorqm on 2010-04-21
che que raro, a mi me tira lo que te marco en negrita por ejemplo:

```
[faktorqm@the-missile ~]$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1920 x 1920                                                                                        
**DVI-1** disconnected (normal left inverted right x axis y axis)                                                                                                
**DVI-0** connected 1280x1024+0+0 (normal left inverted right x axis y axis) 352mm x 264mm                                                                       
   1280x1024      85.0*+   85.0*    75.0     60.0                                                                                                            
   1920x1440      60.0                                                                                                                                       
   1856x1392      60.0                                                                                                                                       
   1792x1344      60.0                                                                                                                                       
   1600x1200      75.0     70.0     65.0     60.0                                                                                                            
   1400x1050      74.8     60.0                                                                                                                              
   1280x960       85.0     60.0                                                                                                                              
   1152x864       75.0                                                                                                                                       
   1024x768       85.0     75.0     70.1     60.0                                                                                                            
   832x624        74.6                                                                                                                                       
   800x600        85.1     85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     75.0     66.7     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  
[faktorqm@the-missile ~]$
```

lo del VGA-0 era en otra maquina que lo habia hecho. Por las dudas probate este comando "xrandr --prop" que ahi te tiene que decir, sino decime e intento ayudarte. Mi salida es:

```
[faktorqm@the-missile ~]$ xrandr --prop
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1920 x 1920
DVI-1 disconnected (normal left inverted right x axis y axis)
        dvi_monitor_type: auto
        scaler: off
        coherent_mode: 1 (0x00000001)   range:  (0,1)
        load_detection: 1 (0x00000001)  range:  (0,1)
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 352mm x 264mm
        EDID:
                00ffffffffffff004c2d09013931484c
                150f01036c231a782fee91a3544c9926
                0f5054bfef808199615945593159a94f
                a940e1400101863d00c05100304040a0
                130060081100001e000000fd0032a01e
                6019000a202020202020000000fc0053
                796e634d61737465720a2020000000ff
                00485841593530313536340a202000a6
        dvi_monitor_type: auto
        scaler: off
        coherent_mode: 1 (0x00000001)   range:  (0,1)
        load_detection: 1 (0x00000001)  range:  (0,1)
   1280x1024      85.0*+   85.0*    75.0     60.0  
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      60.0  
   1600x1200      75.0     70.0     65.0     60.0  
   1400x1050      74.8     60.0  
   1280x960       85.0     60.0  
   1152x864       75.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     75.0     66.7     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  
[faktorqm@the-missile ~]$
```

Salu2!!!

---

### Post by matias_tati on 2010-04-21
```
matias@PCmatias:~$ xrandr --prop
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1600 x 1200
default connected 1440x900+0+0 0mm x 0mm
   1600x1200      50.0
   1440x900       51.0*
   1400x1050      52.0     53.0     54.0
   1360x768       55.0     56.0
   1280x1024      57.0     58.0
   1280x960       59.0
   1152x864       60.0     61.0     62.0     63.0
   1024x768       64.0     65.0     66.0
   960x600        67.0
   960x540        68.0
   840x525        69.0     70.0     71.0
   832x624        72.0
   800x600        73.0     74.0     75.0     76.0
   720x450        77.0
   700x525        78.0     79.0
   680x384        80.0     81.0
   640x480        82.0     83.0     84.0     85.0     86.0
   512x384        87.0     88.0
   400x300        89.0
   320x240        90.0     91.0
matias@PCmatias:~$

```

---

