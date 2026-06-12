---
title: "MS-DOS en Ubuntu"
date: 2008-12-03
forum: Software
---

### Post by Josecanalla on 2008-12-03
Hola, mi papá trabaja con un programa diseñado en MS-DOS y yo quería saber si podía hacerlo andar en Ubuntu. Las extensiones son .bak, .bak, etc.

Este programa genera los archivos y los manda a imprimir a un archivo de Word. ¿Será posible mantener eso en Ubuntu? O al menos que me permita cargar datos, lo imprimo desde Windows.

Gracias, José.

---

### Post by Zeq on 2008-12-03
Podrias hacer una maquina virtual con Windows con VirtualBox o VMWare y listo, la usas directamente como si fuera una maquina de windows comun.

O fijarte si con el Wine o DOSBox podes correrlo directamente.

---

### Post by Hernán-Amaya on 2008-12-03
podes probrar con dosemu que esta en los repositorios te de dejo un tutorial por si te interesa

[http://es.tldp.org/COMO-INSFLUG/COMOs/Dosemu-Como/](http://es.tldp.org/COMO-INSFLUG/COMOs/Dosemu-Como/)

---

### Post by Josecanalla on 2008-12-03
Instalé el VirtualBox, lo configuré y todo, pero cuando intento iniciar la máquina virtual creada me sale este error: 


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by DrKenobi on 2008-12-03
en su momento yo use el DOSBox para un programa que arma torneos de esgrima. Pero si no recuerdo mal, lo unico que no podia hacer era imprimir. El sitio de DOSBox dice que es para juegos............

Suerte!!

---

### Post by c4d0rn4 on 2008-12-03
> **Josecanalla said:**
> Instalé el VirtualBox, lo configuré y todo, pero cuando intento iniciar la máquina virtual creada me sale este error: 


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Me pasó igual pero es fácil de arreglar, tenés que entrar en synaptic y buscar 

virtualbox-ose module for linux-image-TUKERNEL

para saberlo, hay varios modos, pero el más sencillo en la terminal poner

```
uname -r
```

---

### Post by granjero on 2008-12-03
hola josecanalla, a mi me paso algo similar si mal no recuerdo. lo que tenes que hacer es entrar en synaptic e instalar el paquete que corresponda con el kernel de tu ubuntu...

fijate que te pide 

Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..


en synaptic hace clik en buscar

escribi **ose modules** y tilda el que empiece asi **virtualbox-ose-modules-** y termine con el numero de tu kernel. 

ojala te sirva...


salud!

---

### Post by zeroadrenaline on 2008-12-04
Ni hablar yo uso una plataforma de FOXPLUS en dosbox, ni te gastes en maquinas virtuales, ni esas locuras, eso dejalo para Mocosoft, instalate dosbox, esta en repositorios y anda fenomeno!.
Y ademas, en virtual vox, te vas a complicar para compartir carpetas, en dosbox le montas los directorios, que te explica ahi mismo, es una ganzada.

---

### Post by Josecanalla on 2008-12-04
Che, pero no voy a pode imprimir de DOS Box ¿eh?

---

### Post by juanman on 2008-12-04
Si te genera archivos de Word, los guardas y despues los imprimis desde el OpenOffice en Ubuntu... Aunque supongo q debe generar archivos de texto plano, en ese caso, lo podes imprimir desde gedit tambien... 
Tal vez con algun script se pueda automatizar la tarea, pero habría q tener más datos sobre el programa...

---

### Post by DrKenobi on 2008-12-04
> **juanman said:**
> Si te genera archivos de Word, los guardas y despues los imprimis desde el OpenOffice en Ubuntu... Aunque supongo q debe generar archivos de texto plano, en ese caso, lo podes imprimir desde gedit tambien... 
Tal vez con algun script se pueda automatizar la tarea, pero habría q tener más datos sobre el programa...

Site genera archivos de texto plano, no dudes en usar el openbox! y si son de word tambien!

---

### Post by MeduZa on 2008-12-04
DOSBOX anda de 10, el otro dia me jugue un magic carpet 2 ^_^

---

### Post by Josecanalla on 2008-12-20
No tengo mucha idea de programación, así que les voy a explicar como funciona el programa. Yo pongo imprimir en el programa MS-DOS y después me voy al archivo IMPRIMIR, que es un archivo de texto que tengo que elegir abrir con Word. Después, me da para elegir la codificación y tengo que elegir MS-DOS. Después le tengo que aplicar una Macro que ya tengo preparada, para que encuadre bien las hojas y demás.

¿Qué recomiendan?

José.

---

### Post by Josecanalla on 2008-12-23
¿No hay nadie que pueda ayudarme? Es que lo necesito para trabajar.

---

### Post by Hei Ku on 2008-12-23
El tema es que usas una macro de Word. En general, esas no son compatibles con OpenOffice, asi que estarias medio complicado salvo que instalaras todo bajo Wine.
O repliques lo mismo en Openoffice, latex, u otro programa similar, pero me parece que todavia no estas tan familiarizado con Linux.

---

### Post by Hei Ku on 2008-12-23
El tema es que usas una macro de Word. En general, esas no son compatibles con OpenOffice, asi que estarias medio complicado salvo que instalaras todo bajo Wine.
O repliques lo mismo en Openoffice, latex, u otro programa similar, pero me parece que todavia no estas tan familiarizado con Linux.

---

### Post by Josecanalla on 2008-12-23
Claro, es verdad, no sé si podría imitar una macro de Word en OpenOffice. De todos modos es una macro bastante corta, y podrían ayudarme a imitarla... porque es corta, no sé si llega a una página.

---

### Post by sajnox on 2008-12-23
Estoy seguro que encontraras gente que te pueda ayudar con la macro, pero me parece que te puede ir mejor en los [foros]("http://user.services.openoffice.org/es/forum/index.php") de Open Office

---

### Post by Hei Ku on 2008-12-23
En realidad, antes de decidir la herramienta, habria que ver qué hace la macro. Si es para imprimir, lo mas probable es que sea mas facil pasarlo por latex.

---

### Post by rojojuan on 2008-12-24
> **Josecanalla said:**
> Claro, es verdad, no sé si podría imitar una macro de Word en OpenOffice. De todos modos es una macro bastante corta, y podrían ayudarme a imitarla... porque es corta, no sé si llega a una página.

En Writer tenés Herramientas, Macros, Grabar Macro, igual que en Word. Te puede servir esto?

---

### Post by Josecanalla on 2008-12-26
Acá les pongo la macro y ustedes dirán que es lo más conveniente.

Sub Macro3()
'
' Macro3 Macro
' Macro grabada el 13/01/2005 por Jose Persichini
'
    With ActiveDocument.Styles(wdStyleNormal).Font
        If .NameFarEast = .NameAscii Then
            .NameAscii = ""
        End If
        .NameFarEast = ""
    End With
    With ActiveDocument.PageSetup
        .LineNumbering.Active = False
        .Orientation = wdOrientLandscape
        .TopMargin = CentimetersToPoints(1.27)
        .BottomMargin = CentimetersToPoints(1.27)
        .LeftMargin = CentimetersToPoints(0.99)
        .RightMargin = CentimetersToPoints(0.99)
        .Gutter = CentimetersToPoints(0)
        .HeaderDistance = CentimetersToPoints(1.25)
        .FooterDistance = CentimetersToPoints(1.25)
        .PageWidth = CentimetersToPoints(29.7)
        .PageHeight = CentimetersToPoints(21)
        .FirstPageTray = wdPrinterDefaultBin
        .OtherPagesTray = wdPrinterDefaultBin
        .SectionStart = wdSectionNewPage
        .OddAndEvenPagesHeaderFooter = False
        .DifferentFirstPageHeaderFooter = False
        .VerticalAlignment = wdAlignVerticalTop
        .SuppressEndnotes = False
        .MirrorMargins = False
        .TwoPagesOnOne = False
        .BookFoldPrinting = False
        .BookFoldRevPrinting = False
        .BookFoldPrintingSheets = 1
        .GutterPos = wdGutterPosLeft
    End With
    Selection.WholeStory
    Selection.Style = ActiveDocument.Styles("Estilo2")
    CommandBars("Task Pane").Visible = False
End Sub

Ahí está, cualquier ayuda será bienvenida, y gracias a todos.

---

