---
title: "Instalar .NET framework con Wine"
date: 2007-01-09
forum: Software
---

### Post by felipelerena on 2007-01-09
Estube tratando de instalar en .NET framework en Ubuntu y no pude.
lo necesito par instalar en autocad (todo con WINE).
Alguien sabe de alguna manera de instalarlo?

Es para mi viejo, para que se pase a Ubuntu.

ah... si alguine sabe de un tutorial para instalar autocad o de un programa que abra los ".dwg" se lo agradezco
Desde ya, muchas gracias.


PD: no vale mono, tiene que ser el .net framework con wine.

Aclaraciones: es el autocad 2006 y el ultimo wine del repo.

ahora si... un abrazo a todos.

---

### Post by MeduZa on 2007-01-10
me mataste con eso :P voy a ver q encuentro....

---

### Post by spg76 on 2007-01-10
Según la base de datos de aplicaciones de Wine ([http://appdb.winehq.org](http://appdb.winehq.org)) para instalar .NET Framework hay que hacerlo en modo Win98. Podes ver en [http://appdb.winehq.org/appview.php?iVersionId=3754&iTestingId=2232](http://appdb.winehq.org/appview.php?iVersionId=3754&iTestingId=2232)
Lamentablemente el mismo tester dice que lo instalo porque lo necesita AutoCAD y no funciona (aunque .NET esta bien instalado).
Podes ver las pruebas con las distintas versiones de AutoCAD en [http://appdb.winehq.org/appview.php?iAppId=86](http://appdb.winehq.org/appview.php?iAppId=86) (aunque creo que no funciona ninguna)

---

### Post by felipelerena on 2007-01-10
> Según la base de datos de aplicaciones de Wine ([http://appdb.winehq.org]("http://appdb.winehq.org/")) para instalar .NET Framework hay que hacerlo en modo Win98. Podes ver en [http://appdb.winehq.org/appview.php?...TestingId=2232]("http://appdb.winehq.org/appview.php?iVersionId=3754&iTestingId=2232")
con lo primero que probe es con eso... no funciona
[]("http://appdb.winehq.org/appview.php?iVersionId=3754&iTestingId=2232")

---

### Post by BlackHero on 2007-01-11
holas yo te recomendaria que te instales vmware player del add/remove entres a [http://www.easyvmx.com/](http://www.easyvmx.com/) te crees una maquina virtual la seteas ovbio y desde ubuntu te instalas windows y te instalas todas las aplicaciones necesarias para tu viejo para que siga usando windows o en lo posible si lo nececita por el autocad es mi recomendacion create una virtual machine que tenes mucho mas soporte que con wine por el hecho de que tiene todos los dll correspondientes al sistema windows por que es windows de verdad nada mas que dentro de una maquina virtual te lo recomiendo ahora parece que tambien te soporta el directx asi que mejor todavia depende tu placa de video proba no esta nada mal tener una maquina virtual :) 



DIGANLE SI A LAS MAQUINAS VIRTUALES

---

### Post by felipelerena on 2007-01-11
NI LOCO!!!!
la idea es quie deje de usar windows no romperle las pelotas con complejidades inutiles. la joda de todo esto es dejar de tener Windows, no tener otro mas...

digale no a las VM.

---

### Post by BlackHero on 2007-01-11
jajajaja okas disculpa

---

### Post by felipelerena on 2007-01-12
es que me pongo como loco viteh

---

### Post by Enverex on 2007-01-12
I'm not sure if you're going to be able to understand what I'm saying but I'll try and help anyway.

.NET v1 and v2 do not currently work (or even install) in Wine. They are also not likely to work for quite some time either, if ever. The Wine team are, however attempting to get Wine to work with Mono running inside it (OpenSource replacement for .NET v1) but it probably wont be perfect so .NET applications are likely to be a big issue for some time to come. Sorry.

---

### Post by beuno on 2007-01-12
> **Enverex said:**
> I'm not sure if you're going to be able to understand what I'm saying but I'll try and help anyway.

.NET v1 and v2 do not currently work (or even install) in Wine. They are also not likely to work for quite some time either, if ever. The Wine team are, however attempting to get Wine to work with Mono running inside it (OpenSource replacement for .NET v1) but it probably wont be perfect so .NET applications are likely to be a big issue for some time to come. Sorry.

Thanks for the response, I'll translate it:


.NET version 1 y 2 no funcionan (ni siquiera se instalan) en Wine. Por otro lado es probable que no funcione por un tiempo grande, si es que alguna vez funciona.
El equipo de wine, si esta intentando hacer que funcione Mono (el reemplazo open source de .net v1), pero probablemente no funcione "perfecto", asi que es probable que los proximos tiempos no sean los mejores para aplicaciones .net. Lo siento.

---

### Post by felipelerena on 2007-01-12
thanks man, I will still try to install it. there must be some way.

---

### Post by Enverex on 2007-01-12
Just tried again with wine-0.9.29-g8d82a8c but still no progress since quite a while ago, but apparently customers of Codeweavers (the commercial side of Wine) are "demanding" .NET support so it may be focussed on. If someone hires CW to fix it then it could be fixed in a few weeks but I doubt that is likely to happen, but at least it's on the plan.

---

### Post by bolchevique on 2009-04-01
felipe, pudiste instalarlo finalmente??

o alguien pudo hacer funcionar .net framework con WINE???

---

### Post by clasificado on 2009-04-02
> **felipelerena said:**
> Estube tratando de instalar en .NET framework en Ubuntu y no pude.
lo necesito par instalar en autocad (todo con WINE).
Alguien sabe de alguna manera de instalarlo?

Es para mi viejo, para que se pase a Ubuntu.

ah... si alguine sabe de un tutorial para instalar autocad o de un programa que abra los ".dwg" se lo agradezco
Desde ya, muchas gracias.


PD: no vale mono, tiene que ser el .net framework con wine.

Aclaraciones: es el autocad 2006 y el ultimo wine del repo.

ahora si... un abrazo a todos.
De las veces que intenté hacer funcionar programas de .net en wine, le instalé MONO version WINDOWS (ahora está el paquete 2.2). 

El wine se encarga de hacerlo pasar como Microsoft.net sin que el programa se de cuenta y ejecuta .net como loco.

Dos anotaciones:
1) Mono no tiene TODAS las dlls que microsoft ofrece (por ejemplo: Microsoft.VisualBasic.Compatibility.dll, que lo usan los desarrolladores para hacer parches) pero se puede hacer lo mismo que hace wine de agregar las dlls desde windows a un lugar central y comienzan a usarlas en reemplazo, esto me ha SALVADO la vida y llevado a programas a finalmente ejecutarse joya

2) yo he probado programas sin ser demasiado grandes: AUTOCAD me da así como miedo :D

Bah, probalo si querés y contá como te fue

clasificado

---

### Post by gmunioz on 2009-04-02
Hola fel...:

Aquí una guia, en inglés y algo compleja, del sitio de wine para instalar y usar el autocad.

> 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4105&iTestingId=1232](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4105&iTestingId=1232)


Saludos.

---

### Post by EnriqueK on 2009-04-11
En el siguiente enlace te podés bajar un Script que se encarga de instalar aplicaciones mediante wine, entre ellas está el MS Net 2.0 
> [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

El proceso comienza con obtener el script **winetricks**
luego, para instalar una aplicación que figura en la lista de la página, se pone **sh winetricks programa** (asumiendo que al sdript lo tienes en tu carpeta de usuario) y para el caso concreto del Net framewortk 2.0 sería 
**sh winetricks dotnet20** 
Hay muchas aplicaciones que pueden ser interés, por lo que vale la pena agendar esta página.

---

