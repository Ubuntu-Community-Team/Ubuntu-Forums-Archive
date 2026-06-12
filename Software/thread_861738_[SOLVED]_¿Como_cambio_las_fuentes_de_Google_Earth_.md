---
title: "[SOLVED] ¿Como cambio las fuentes de Google Earth 4.3?"
date: 2008-07-16
forum: Software
---

### Post by atari130xe on 2008-07-16
Gente, alguien sabe como cambiar las fuentes de Google Earth? la verdad que al instalarlo es practicamente ilegible, si alguien sabe le agradeceria el dato. :)

Mil disculpas! pregunté esto y encontré la solucion en Ubuntu-Es:

1)```
 sudo gedit ~/.config/Google/GoogleEarthPlus.conf
```

2) modificar la sección "Render" y cambiar lo que hay por lo siguiente:
```
[Render]
AnisotropicFiltering=0
CompassVisible=true
DisableAdvancedFeatures=false
ElevationExaggeration=1
FeetMiles=true
GridReference=0
GuiFontFamily=Arial
GuiFontSize=20
GuiFontStyle=0
GuiFontWeight=50
IconSize=1
OverviewSize=34
OverviewZoom=99
PrimaryFontVersion2Family=Arial
PrimaryFontVersion2Size=28
PrimaryFontVersion2Style=0
PrimaryFontVersion2Weight=75
RenderingApi=1
SecondaryFontVersion2Family=Bitstream Vera Sans
SecondaryFontVersion2Size=28
SecondaryFontVersion2Style=0
SecondaryFontVersion2Weight=75
TerrainQuality=-1
TextureColors=1
TextureCompressionDXTC=true

```

Y la resolución cambia en casi todo los menúes, pero habría que ajustar el tamaño de la fuente en mi caso ya que mi escritorio esta puesto en 1024x768 y con esos datos quedan un poco grandes pero mucho mejor que cuando recíen se instala el programa. espero les sirva el dato.

---

### Post by FlyerDie on 2008-07-16
yo aun no quise instalar la 4.3 ...tengo la 4.2.0205.5730 y se ven muy bien.
a vos las de la 4.2 se te veian bien o tambien mal?

Saludos!

---

### Post by atari130xe on 2008-07-16
> **FlyerDie said:**
> yo aun no quise instalar la 4.3 ...tengo la 4.2.0205.5730 y se ven muy bien.
a vos las de la 4.2 se te veian bien o tambien mal?

Saludos!

Sip esa version andaba bien, pero como actualicé quedo asi medio como "deschavetada" :P

---

### Post by FlyerDie on 2008-07-17
ahhh ok! pense que podia ser algo que arrastraras de version ;)
alguna mejora considerable o me quedo en la 4.2?:lolflag:

Saludos!

---

### Post by atari130xe on 2008-07-17
> **FlyerDie said:**
> ahhh ok! pense que podia ser algo que arrastraras de version ;)
alguna mejora considerable o me quedo en la 4.2?:lolflag:

Saludos!

Bueno más que mejoras, noté cambios en algunos menúes, pero el sistema es muy parecido en las 2. Salvo por el tema de las fuentes que en el caso de los carteles informativos de un punto específico te aparecen ilegíbles.:)

---

