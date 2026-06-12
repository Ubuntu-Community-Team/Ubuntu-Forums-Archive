---
title: "Football Manager 2009"
date: 2009-02-26
forum: Software
---

### Post by signos2006 on 2009-02-26
Hola, alguien me tira un cable para poder instalar este juego con Wine? vi algunos tutoriales pero en su mayoria en ingles, el cual no manejo bien. De momento logre instalarlo pero al momento de ejecutarlo el juego no abre.

Desde ya muchas gracias.

---

### Post by signos2006 on 2009-02-26
Nadie sabe como instalarlo?

Por las dudas tengo Ubuntu 8.10 y Wine 1.1.10

---

### Post by marianom on 2009-02-27
Tenés que dar más información...
que comando corres, que error te da, es la única forma en la cual alguien puede intentar darte una mano.

---

### Post by signos2006 on 2009-02-27
No me da ningun error, lo instale con el Wine, para abrirlo voy a 

Aplicaciones -> Wine -> Porgramas -> Sports Interactive -> Football Manager 2009

Y directamente no se abre, aparece en la barra diciendo "Iniciando Footbal Manager" pero nunca se abre.

De todas formas si alguien tiene un tutorial en español para instalarlo lo intalo de nuevo.

---

### Post by marianom on 2009-02-27
No soy muy wine pero creo que si abrís una consola y haces:

```
wine /ruta/a/mi/futbolito.exe
```

va a correr y vas a tener un output de todo lo que haga el programa.

Probalo y nos avisás.

---

### Post by signos2006 on 2009-02-27
A ver esto me da

signos2006@signos2006-desktop:~$ wine "C:\Archivos de programa\Sports Interactive\Football Manager 2009/fm.exe"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Sports Interactive\\Football Manager 2009\\saAuditMD.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Sports Interactive\\Football Manager 2009\\saAuditMD.dll") not found
err:module:import_dll Library saAuditMD.dll (which is needed by L"C:\\Archivos de programa\\Sports Interactive\\Football Manager 2009\\fm.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Archivos de programa\\Sports Interactive\\Football Manager 2009\\fm.exe" failed, status c0000135

Supongo que tendre que conseguir esos dll que me pide, la pregunta ahora es de donde los saco.

---

### Post by signos2006 on 2009-02-28
Ya lo logre hacer funcionar.

---

### Post by signos2006 on 2009-02-28
Tengo un problema a la hora de activar el juego, a la hora de instalarlo la pantalla de instalacion se veia toda gris pero de todas formas con el tab la barra espaciadora y el enter pude instalarlo sin ver lo que decia, pero ahora a la hora de activar el juego la pantalla me sale sin botones, de manera que no puedo poner siguiente ni nada.

Ahi puse una catura, al pasar el mouse arriba de next no pasa nada no me deja interactuar.

---

### Post by Tosh78 on 2009-02-28
Hola Signos, yo instale el juego. No lo pude hacer funcionar todavia porque me tira un error de la placa de video, pero te doy una mano en lo que necesites. Cualquier cosa, mandame un mensaje privado.

---

### Post by NickCis on 2009-02-28
Busque en Wine Hq, para ver como hacer andar y por suerte hay una guia.
Link: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=8597](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8597)

Segun lo que dice ahi la vercion normal no anda, si no que andan la 9.1.0 y la 9.2.0.

Aca como instalarlo:
```
Installation:
Use Steam (see instructions for installing Steam on wine) - you can insert your CD key from retail versions to download and install via Steam.

You must have directx9, dotnet20 and msxml3 installed to run FM2009, these can all be installed with winetricks.

Activation:
Download the fixed activator (http://www.footballmanager.com/fixv2.zip), run the program to extract activator.exe over the one at (default) ~/.wine/drive_c/"Program Files"/Steam/steamapps/common/"football manager 2009"/activator.exe.

Run the new activator from the command line as follows:
wine ~/.wine/drive_c/"Program Files"/Steam/steamapps/common/"football manager 2009"/activator.exe -activate ufhw8eff89ff0nwf08ww

Where ufhw8eff89ff0nwf08ww is the key printed on your manual (if you bought the game through Steam, right click it in My Games and click 'Show CD key' - do NOT paste directly from here, it will not work in uppercase)

Make sure your CD key is all lowercase, and watch out for 1's that look like l's, or o's that look like 0's (use http://keycheck.fm2009.softanchorinsight.com/ to check your key).

You should now be able to launch the game via Steam. I'll be testing Network mode later and will report back with my findings.

If for some reason it doesn't work, please check ~/.wine/drive_c/windows/profiles/"All Users"/"Application Data"/"Sports Interactive"/"Football Manager 2009 Certificate"/HttpCheck.log and make sure that the end reads something like:

SI Activator: Activation succeeded
Activation reads success.

kEvalTestNumComponents: 1
kEvalTestMatches: 1
kEvalTestTier1Matches: 1
kEvalTestMismatches: 1
kEvalTestInvalidItems: 1
kEvalTestNonces: 1
kEvalTestTier2Matches: 1
kEvalTestNonceDiffs: 1
License reads success.
License key: YOUR_CD_KEY

VIRTUAL CRACK IS BACK! 
```

Este manual es para instalar la vercion 9.1.0 y lo saque de este link: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555) (Entra ahi por que hacen muchas mas aclaraciones).

Te recomiendo que antes de instalar cualqier programa de windos busques en la pagina de wine informacion. ( [http://www.winehq.org](http://www.winehq.org) ).

Saludos.

---

### Post by signos2006 on 2009-03-01
Claro, yo estoy instalando la version 9.2, la 9.1 ya la hice fundionar, pero con la 9.2 no puedo poner el serial porque me sale la ventana como adjunte arriba.

Asi deberia salirme la pantalla de activacion (screen que encontre buscando en google)


Me faltaria algun tipo de programa o libreria en wine para poder ver la ventana de forma normal?

---

### Post by NickCis on 2009-03-01
Mira, busca en google y en la pagina de wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15000](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15000)
La verdad nunca instale este juego, no te puedo decir nada mas. Segun la pagina de wine la vercion 9.2 anda, pero la 9.3, no.

Saludos.

---

### Post by marianom on 2009-03-02
> **signos2006 said:**
> Ya lo logre hacer funcionar.

Harías bien en decir como fue, si el día de mañana alguien tiene la misma necesidad que vos, puede encontrar acá la respuesta.

---

