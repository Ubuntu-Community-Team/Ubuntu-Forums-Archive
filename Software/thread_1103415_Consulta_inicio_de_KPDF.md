---
title: "Consulta: inicio de KPDF"
date: 2009-03-22
forum: Software
---

### Post by mecdem on 2009-03-22
Hola. Había puesto esta consulta en Argentina Team  > Software, pero parece que no era allí el lugar correcto. Por favor, indicarme si no fuera este tampoco el lugar adecuado. Gracias.

Reproduzco la consulta.
_________________________

Buen día amigos.

No soy informática, así que si algo no está claro en mi consulta, por favor, indicármelo con cariño, no me tiren con el FManual...

Sistema: Kubuntu 8.04, kernel...
Ahora me doy cuenta de que no sé cómo se averigua la versión del kernel. Si el dato es necesario para esta consulta, agradezco desde ya la enseñanza.

El problema que consulto se refiere al inicio de la aplicación KPDF.
_____________

A) Al instalarla, el menú muestra en el menú de KDE no uno sino DOS íconos de
acceso a la aplicación:

1. En el menú general, aparece el ícono con el nombre “KPDF”. Clic en ese ícono no produce ningún efecto.

2. En el submenú Oficina. Aparece el ícono con el nombre “KPDF - Visor de PDF”. Clic en ese ícono ejecuta la aplicación, que funciona normalmente.

Nota: si editando el menú de KDE elimino el ícono indicado en 1, desaparece.
Pero al abrir nuevamente el menú... ¡allí está el iconito mirándome!!
_____________

B) Aspecto de los íconos en archivos .pdf

1) En el escritorio
Tengo en el escritorio varios archivos .pdf.
Cuando inicio el sistema, al aparecer el escritorio los íconos de los archivos .pdf muestran el logo de la aplicación, pero enseguida desaparece el logo y los íconos quedan parecidos a los que corresponden a archivos .txt.

2) En las ventanas de los directorios.
Los íconos de los .pdf se ven con el logo de la aplicacíón.
_____________

C) Ejecución de la aplicación desde un archivo.

Si intento abrir un archivo .pdf con doble clic aparece este mensaje:
KDEInit no pudo lanzar «/home/mecdem/[nombre_archivo].pdf»

Si el archivo .pdf está en un directorio que no sea el escritorio, doble clic solo produce un titilar del ícono. No se abre la aplicación y no arroja ningún mensaje

La única manera de abrirlos en reeemplazo del doble clic (sin ejecutar previamente la aplicación), es así:

clic con botón derecho
> Abrir con...
> tildar “Recordar asociación de programa para este tipo de archivo”
> Oficina
> KPDF
> Aceptar.

La instrucción “Recordar...” no queda guardada. Hay que incluirla en el proceso cada vez que se quiere abrir la aplicación desde el ícono del archivo.

El ícono final es el que en A) se indicó como 2. Si se intenta el mismo procedimiento con el ícono que se indicó como 1 NO se habilita el botón Aceptar.

Cuando se hace clíc con botón derecho sobre el archivo, en el menú aparece una opción “Abrir con KPDF”, cuyo ícono no muestra el logo de la aplicación. Clic sobre esa opción, genera el mismo mensaje referido antes:
KDEInit no pudo lanzar «/home/mecdem/[nombre_archivo].pdf»
_____________

Esto es todo lo que he podido observar.
Espero que se entienda la consulta.
Agradezco desde ya la respuesta. Saludos.
__________________
mecdem

---

### Post by Hei Ku on 2009-03-22
El subforo de Software es el lugar correcto.

Que version de KDE usas?

Que tocaste?

---

### Post by mecdem on 2009-03-23
> **Hei Ku said:**
> El subforo de Software es el lugar correcto.
Hola HeiKu, gracias por tu pronta respuesta.
Supuse que Sofware era el foro correcto, pero como no hubo respuesta en cuatro días creí que no estaba la consulta en el lugar adecuado. No es que piense que tenga alguien que venir corriendo a auxiliarme, pero son ustedes los que nos tienen mal acostumbrados a los consultantes con vuestra diligencia :)
Si por mejor ordenamiento quieres seguir la consulta allí, está en [http://ubuntuforums.org/showthread.php?p=6913372#post6913372](http://ubuntuforums.org/showthread.php?p=6913372#post6913372)

> Que version de KDE usas?
3.5.10

> Que tocaste?
Nada que haya advertido.

AGREGO: Observo que lo mismo que ocurre con los íconos de archivos .pdf ocurre con los íconos de otras aplicaciones. Por ejemplo, los íconos de archivos generados con Writer no muestran el logo propio de la aplicación, en el escritorio. Si los muevo a la ventana de otro directorio, por ejemplo a Documentos, ahí si se ve el ícono con su logo como corresponde.
Si arrastro un archivo desde la ventana de un directorio al escritorio, por un instante el ícono muestra el logo y enseguida el logo desaparece, queda el ícono parecido, no igual, a los de archivos .txt.

Ahora advierto que parecerían ser dos problemas:
Uno, el de los íconos en el escritorio.
Otro, el arranque de KPDF que originó esta consulta.

Gracias por tu ayuda y tu tiempo.

---

### Post by Hei Ku on 2009-03-23
Hmmm. Raro, me suena a un problema que va mas alla del KPdf.
Vamos a ver si podemos conseguir mas info.

En una terminal, pone:

kpdf <nombre de archivo pdf>

Y a ver si asi tira algun error que nos oriente.

---

### Post by mecdem on 2009-03-24
> **Hei Ku said:**
> 
En una terminal, pone:
kpdf <nombre de archivo pdf>

yo@minotebook:~$ kpdf DomPubPagante.pdf

abre la aplicación, no abre el archivo y tira mensaje:

Error kpdf
No se pudo abrir file:///home/mecdem/DomPubPagante.pdf
Aceptar

La aplicación queda abierta. Usando el menú Archivo > Abrir... el archivo se abre.

---

### Post by Hei Ku on 2009-03-24
En la terminal no tira mensaje de ningún tipo aparte de esos? :$

---

### Post by mecdem on 2009-03-24
> En la terminal no tira mensaje de ningún tipo aparte de esos? :$


No, no hay ningún <mensaje en la terminal.
Queda en suspenso (punto de inserción titilando a la izquierda).
El prompt reaparece luego de cerrar la aplicación.

---

### Post by mecdem on 2009-04-10
):P Hola, holita... Iujuuuu...
Hay alguien por aquí?

---

### Post by Loan_Refi on 2009-04-10
Hola,

Que pasa si en tu escritorio eliges uno de tus archivos y haces click on el boton derecho y navegas a propiedades, habre con y eliges la aplicacion correcta? como evince o lo que corresponda dependiendo al typo de archivo que quieras habrir?

---

### Post by mecdem on 2009-04-11
> **Loan_Refi said:**
> Hola,
Que pasa si en tu escritorio eliges uno de tus archivos y haces click on el boton derecho y navegas a propiedades, habre con y eliges la aplicacion correcta? como evince o lo que corresponda dependiendo al typo de archivo que quieras habrir?

Hola Loan_Refi. Gracias por continuar la consulta.

La apertura de las demás aplicaciones con el procedimiento que indicas funciona normalmente.
En el caso de Writer -dije antes que en el escritorio, en lugar del ícono correspondiente a la aplicación aparece uno "genérico"- también funciona bien el arranque.

---

### Post by Hei Ku on 2009-04-11
Que resultado te da correr este comando en la terminal?

```

cat /usr/share/mimelnk/application/pdf.desktop

```

Y otra cosa, el mensaje de error exacto es?

KDEInit no pudo lanzar «[nombre_archivo]»

Y por casualidad instalaste el Acrobat Reader? Es una de las cosas que puede causar este problema.

---

### Post by mecdem on 2009-04-13
Buen  día, Hei Ku.
Van respuestas:

> **Hei Ku said:**
> Que resultado te da correr este comando en la terminal?
```

cat /usr/share/mimelnk/application/pdf.desktop

```


Epa!! ¿Se volvió loca? Este es el resultado:

mecdem@Leia:~$ cat /usr/share/mimelnk/application/pdf.desktop
[Desktop Entry]
Type=MimeType
MimeType=application/pdf
Icon=pdf
Patterns=*.pdf;*.PDF;
X-KDE-PatternsAccuracy=90
Comment=PDF Document
Comment[af]=Pdf Dokument
Comment[ar]=&#1605;&#1587;&#1578;&#1606;&#1583; PDF
Comment[az]=PDF S&#601;n&#601;di
Comment[be]=&#1044;&#1072;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090; PDF
Comment[bg]=PDF &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Comment[bn]=&#2474;&#2495;-&#2465;&#2495;-&#2447;&#2475; &#2472;&#2469;&#2496;
Comment[br]=Teul PDF
Comment[bs]=PDF dokument
Comment[ca]=Document PDF
Comment[cs]=PDF dokument
Comment[csb]=Dokùment PDF
Comment[cy]=Dogfen PDF
Comment[da]=PDF-dokument
Comment[de]=PDF-Dokument
Comment[el]=&#904;&#947;&#947;&#961;&#945;&#966;&#959; PDF
Comment[eo]=PDF-dokumento
Comment[es]=Documento PDF
Comment[et]=PDF-dokument
Comment[eu]=PDF dokumentua
Comment[fa]=&#1587;&#1606;&#1583; PDF
Comment[fi]=PDF-asiakirja
Comment[fr]=Document PDF
Comment[fy]=PDF-dokumint
Comment[ga]=Cáipéis PDF
Comment[gl]=Documento PDF
Comment[he]=&#1502;&#1505;&#1502;&#1498; PDF
Comment[hi]=&#2346;&#2368;&#2337;&#2368;&#2319;&#2347; &#2342;&#2360;&#2340;&#2366;&#2357;&#2395;
Comment[hr]=PDF dokument
Comment[hu]=PDF-dokumentum
Comment[id]=Dokumen PDF
Comment[is]=PDF skjal
Comment[it]=Documento PDF
Comment[ja]=PDF &#12489;&#12461;&#12517;&#12513;&#12531;&#12488;
Comment[ka]=PDF &#4307;&#4317;&#4313;&#4323;&#4315;&#4308;&#4316;&#4322;&#4312;
Comment[kk]=PDF &#1179;&#1201;&#1078;&#1072;&#1090;&#1099;
Comment[km]=&#6063;&#6016;&#6047;&#6070;&#6042; PDF
Comment[ko]=PDF &#47928;&#49436;
Comment[lb]=PDF-Dokument
Comment[lt]=PDF dokumentas
Comment[lv]=PDF dokuments
Comment[mk]=PDF-&#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Comment[mn]=PDF-&#1041;&#1072;&#1088;&#1080;&#1084;&#1090;
Comment[ms]=Dokumen PDF
Comment[mt]=Dokument PDF
Comment[nb]=PDF-dokument
Comment[nds]=PDF-Dokment
Comment[ne]=PDF &#2325;&#2366;&#2327;&#2332;&#2366;&#2340;
Comment[nl]=PDF-document
Comment[nn]=PDF-dokument
Comment[nso]=Tokomane ya PDF
Comment[pa]=PDF &#2598;&#2616;&#2596;&#2622;&#2613;&#2651;
Comment[pl]=Dokument PDF
Comment[pt]=Documento PDF
Comment[pt_BR]=Documento PDF
Comment[ro]=Document PDF
Comment[ru]=&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090; PDF
Comment[rw]=PDF Inyandiko
Comment[se]=PDF-dokumeanta
Comment[sk]=PDF dokument
Comment[sl]=Dokument PDF
Comment[sq]=Dokument nga PDF
Comment[sr]=PDF &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Comment[sr@Latn]=PDF dokument
Comment[sv]=PDF-dokument
Comment[ta]=Pdf &#2950;&#2997;&#2979;&#2990;
Comment[te]=&#3114;&#3105;&#3086;&#3115; &#3114;&#3108;&#3120;&#3074;
Comment[tg]=&#1061;&#1091;&#1207;&#1207;&#1072;&#1090;&#1080; PDF
Comment[th]=&#3648;&#3629;&#3585;&#3626;&#3634;&#3619; PDF
Comment[tr]=PDF Belgesi
Comment[tt]=PDF &#304;stälek
Comment[uk]=&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090; PDF
Comment[uz]=PDF hujjati
Comment[uz@cyrillic]=PDF &#1203;&#1091;&#1078;&#1078;&#1072;&#1090;&#1080;
Comment[ven]=Manwalwa a pdf
Comment[vi]=Tài li&#7879;u PDF
Comment[wa]=Documint PDF
Comment[xh]=Uxwebhu lwe PDF
Comment[zh_CN]=PDF &#25991;&#26723;
Comment[zh_HK]=PDF &#25991;&#20214;
Comment[zh_TW]=PDF &#25991;&#20214;
Comment[zu]=Uhlu lwamafayela e-PDF
X-KDE-AutoEmbed=true
[Property::X-KDE-NativeExtension]
Type=QString
Value=.pdf

X-Ubuntu-Gettext-Domain=desktop_kdelibs
mecdem@Leia:~$   
______

> **Hei Ku said:**
> Y otra cosa, el mensaje de error exacto es?
KDEInit no pudo lanzar «[nombre_archivo]»


El mensaje exacto es:

Error kpdf
No se pudo abrir file:///home/mecdem/DomPubPagante.pdf
Aceptar

Error kpdf
No se pudo abrir file:///home/[usuario]/[nombre_archivo].pdf
Aceptar
_______

> **Hei Ku said:**
> Y por casualidad instalaste el Acrobat Reader? Es una de las cosas que puede causar este problema.

No. Porsi, revisé con Adept y para esta función KPDF es el único programa instalado.
_______

Gracias. Saludos.

---

### Post by mecdem on 2009-04-30
Bueh... supongo que tendré que dar por cerrada la consulta.
Gracias igual... :cry:

):P

---

### Post by clasificado on 2009-04-30
Es mas dificil cuando no tenemos el kpdf :P

con la llegada del kde4 lo hemos reemplazado con el okular. 

te diria que lo pruebes desde el live cd de kde3 (para ver si es un bug de la versión que tiene el kubuntu o es un problema de tu instalación)

porque de ser un problema de tu instalación, por ahi haciendole un purge y volviendo a instalarlo se arregle

de ser un problema de kpdf de kubuntu, se podria recompilar desde las fuentes

clasificado

---

### Post by guillermolisi on 2009-05-01
> **clasificado said:**
> Es mas dificil cuando no tenemos el kpdf :P

con la llegada del kde4 lo hemos reemplazado con el okular. 

te diria que lo pruebes desde el live cd de kde3 (para ver si es un bug de la versión que tiene el kubuntu o es un problema de tu instalación)

porque de ser un problema de tu instalación, por ahi haciendole un purge y volviendo a instalarlo se arregle

de ser un problema de kpdf de kubuntu, se podria recompilar desde las fuentes

clasificado
Tengo los dos, KPDF y Okular, y con ninguno de los dos experimente el problema que se menciona y los mas raro y desconcertante, para mi y por lo visto para varios mas, es que en consola no tira error o comentario alguno que sirva de indicio como para ensayar siquiera una hipotesis.

Uso KDE 3.5.10 con QT3 y QT4.

---

### Post by Hei Ku on 2009-05-02
Aparentemente es un problema con los mimetypes. Borrando los existentes y recreandolos podria solucionarse. Lo raro es que eso se da generalmente solo cuando trataste de instalar el Adobe Acrobat.

---

### Post by mecdem on 2009-05-05
Iupiiii !!!!!
Volvieron !!! =D>   Los estoy leyendo !!!
 
Veo que hubo silencio porque la consulta mía está complicadita y no porque me hubiesen abandonado.
Gracias clasificado, guillermolisi, HeiKu. 

Aclaro que en otra notebook, una Toshiba, tengo el mismo Kubuntu, misma versión, y no tengo ninguno de los problemas que motivan la consulta.

Ahora es tarde, mañana repasaré las respuestas para ver si puedo avanzar y regreso para contarles.

---

