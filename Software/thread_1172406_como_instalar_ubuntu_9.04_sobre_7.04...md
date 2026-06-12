---
title: "como instalar ubuntu 9.04 sobre 7.04.."
date: 2009-05-28
forum: Software
---

### Post by luica on 2009-05-28
[COLOR=#444444][FONT=Verdana]Antes q nada pido disculpa por mi ignorancia ya q no se si es el lugar correcto para preguntar pero soy nuevo en ubuntu y sabran entender.. mi pregunta es tengo windows XP y ubuntu 7.04 instalados en mi maquina con cuatro particiones Tipo de partición Disco Offset de arranque Tamaño de la partición
#1 (Activo)NTFS C: 0 MB 26003 MB
#2 Linux 26003 MB 19124 MB
#3 FAT32 D: 46006 MB 30302 MB
#4 Linux swap 45127 MB 878 MB
mi pregunta es ¿puedo instalar 9.04 sobre las mismas particiones del 7.04 es decir instalar solo la raiz/ y el swap sin tocar el /home? o como deberia hacerlo? desde ya muchas gracias por su tiempo.. saludos[/FONT][/COLOR]

---

### Post by pablo.s on 2009-05-28
Si lo tuvieras instalado
con / y /home en particiones
separadas sería posible,
pero viendo tu informe
no lo tenés asi.
Te recomiendo backup
e instalación de cero.

---

### Post by pol666 on 2009-05-28
y si no queres reinstalar.. actualiza online

---

### Post by pablo.s on 2009-05-28
> **pol666 said:**
> y si no queres reinstalar.. actualiza online

Buena acotación, Pol,
pero me parece que del
2007 al 2009 los programas
han tenido muchos cambios
y es probable que al
actualizar con dist-upgrade
tenga algunos quebraderos
de cabeza... 
Saludos.

---

### Post by luica on 2009-05-28
> **pablo.s said:**
> Si lo tuvieras instalado
con / y /home en particiones
separadas sería posible,
pero viendo tu informe
no lo tenés asi.
Te recomiendo backup
e instalación de cero.


gracias pablo por tu tiempo.. previamente intente actualizar el sistema pero los repositores ya caducaron supongo por eso la idea de instalar el 9.04 me recomendas algun manual o guia ya q me animo pero por las dudas es bueno siempre estar seguro jeje mas con el echo de las particiones gracias saludos

---

### Post by pablo.s on 2009-05-28
Como consejo, te daria
dos:
1) Cuando instalás, observá
cuidadosamente el tema de
las particiones. Elegí el tipo
de particionamiento manual,
asi sabés donde instala cada
cosa. Las particiones de
Windows asignalas como
/media/windows y /media/windows2
pero[B] cerciorate que bajo ningún
concepto las formatee[/B], sino que
las monte.
2) No tenés particionado
aparte el / y /home por separado.
Ya que vas a instalar de cero
es buena oportunidad para
hacerlo. Achicás la partición /
hasta mas o menos 6 GB y el resto
lo creás para /home. Así separás
los datos de usuario de los del
sistema, que es más conveniente.

Esos son mis aportes para que 
tengas una instalación satisfactoria.
Cualquier otra consulta estamos
a tu disposición.

---

### Post by luica on 2009-05-28
> **pablo.s said:**
> Como consejo, te daria
dos:
1) Cuando instalás, observá
cuidadosamente el tema de
las particiones. Elegí el tipo
de particionamiento manual,
asi sabés donde instala cada
cosa. Las particiones de
Windows asignalas como
/media/windows y /media/windows2
pero[B] cerciorate que bajo ningún
concepto las formatee[/B], sino que
las monte.
2) No tenés particionado
aparte el / y /home por separado.
Ya que vas a instalar de cero
es buena oportunidad para
hacerlo. Achicás la partición /
hasta mas o menos 6 GB y el resto
lo creás para /home. Así separás
los datos de usuario de los del
sistema, que es más conveniente.

Esos son mis aportes para que 
tengas una instalación satisfactoria.
Cualquier otra consulta estamos
a tu disposición.





gracias pablo ya me baje el iso del 9.04 te adjunto los numeros de mi disco para q le des una mirada y ver si modifico algo en los tamaños o alguna cosita mas... desde ya muchas gracias por tu tiempo y pasiencia                                  cfdisk 2.12r

                           Unidad de disco: /dev/hda
                      Tamaño: 80026361856 bytes, 80.0 GB
            Cabezas: 255   Sectores por pista: 63   Cilindros: 9729

    Nombre      IndicadoresTipo       Tipo de S.F.     [Etiqueta]     Tamaño(MB
)------------------------------------------------------------------------------
    hda1        Inicio      Primaria      NTFS             []              27266,81 
    hda2                    Primaria        Linux ext3                       20053,24
    hda5                    Lógica        Linux swap / Solaris               921,24
    hda3                    Primaria   W95 FAT32 (LBA)                  31774,26
                                                       Inutilizable                         8,23

---

### Post by pablo.s on 2009-05-28
> **luica said:**
> hda1        Inicio      Primaria      NTFS             []              27266,81 

Esta partición es la de 
arranque de Windows.
En el particionado manual
la tenés que nombrar
como /media/windows.
[B]NO LE DES FORMATO.
CHEQUEAR ESTO.[/B]

    > **luica said:**
> hda2                    Primaria        Linux ext3                       20053,24
    
Esta partición es la que
actualmente tenés como
/ y que deberías achicar
a 6 GB (ahora son casi 20 GB)
El resto de espacio libre lo
convertis en una partición
ext3 de 13 GB y monedas
para /home. Le dás la orden
que formatee tanto la de 6 GB
como la de 13 GB.

> **luica said:**
> hda5                    Lógica        Linux swap / Solaris               921,24
    
Tradicional partición de swap.

> **luica said:**
> hda3                    Primaria   W95 FAT32 (LBA)                  31774,26

Esta es otra partición (supongo
que contiene datos, no sistema)
En el particionado manual
la tenés que nombrar
como /media/windows2.
[B]NO LE DES FORMATO.
CHEQUEAR ESTO.[/B]

---

