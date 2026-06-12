---
title: "Voy a instalar UBUNTU, pero....."
date: 2009-01-12
forum: Software
---

### Post by Carlos 2009 on 2009-01-12
...necesito que me den una mano..

Antes que nada, hola, soy Carlos y aprovechando que tengo un HD de 250gb al ****, me decidi a probar UBUNTU, hace años probe mandrake y me duro 10 horas y lo borre al diablo, pero me comentaron en en estos años se mejoro mucho todo lo que sea linux, asi que le voy a dar una nueva chance.

Uso estos programas si o si y ni idea si hay versiones para linux o programas parecidos y que no me hagan renegar.

les dejo la lista.

1- ConvertXtoDvd 3 (divx a dvd)
2- Subtitle Workshop (subtitulos)
3- Nero CoverDesigner (para imprimir caratulas)
4- EPSON Print CD (para una epson r220 e imprimir discos)
5- MediaChance.DVDLab.Pro (autoria de dvd)

Por otro lado, preguntar si no hay dramas con los drivers de una ATI HD4670, una impresora epson r220 que imprime discos y una sound blaster audigy SE.

Ante todo, muchas gracias. :guitar:

---

### Post by Dan_Dranath999 on 2009-01-12
Puedes buscar si tus aplicaciones de windows funcionan con Wine, pero sé que no todos los programas lo hacen, o no todos los que se pueden hacer funcionar, funcionan al 100%

Si la aplicación fué escrita para un sistema operativo concreto, hacerla funcionar en otro SIEMPRE SERÁ PROBLEMATICO. Usualmente no se le pide al MacOSX que corra programas de Windows, así que lo que se hace en Linux es ya de por sí impresionante.

Pero si te sientes obligado a usar un determinado set de programas, tal vez deberías plantearte seguir usando Windows, después de todo, lo importante es usar la herramienta adecuada y que te sirva a tí.

---

### Post by Carlos 2009 on 2009-01-12
Gracias, entiendo lo que dices, por eso puse "programas parecidos".. 

Gracias igual. ):P

---

### Post by euzkoarima on 2009-01-12
> **Carlos 2009 said:**
> 
1- ConvertXtoDvd 3 (divx a dvd)
2- Subtitle Workshop (subtitulos)
3- Nero CoverDesigner (para imprimir caratulas)
4- EPSON Print CD (para una epson r220 e imprimir discos)
5- MediaChance.DVDLab.Pro (autoria de dvd)


No conozco esos programas en windows, con lo cual no sé justo cuál sería el equivalente, pero te paso links a páginas que tratan de establecer ese tipo de "equivalencias"

[linuxappfinder]("http://www.linuxappfinder.com/alternatives")
[open source software alternatives]("http://www.osalt.com/")

Además, dale una mirada a [getdeb]("http://www.getdeb.net/") como para ver "que hay"

con respecto a armar un dvd a partir de un divx probá [devede]("http://www.rastersoft.com/programas/devede.html") que es bueno y muy fácil de usar.

Saludos,
Eduardo

---

### Post by luks911 on 2009-01-12
¡Bienvenido!
Lo que sé: hay alternativas linux para algunos de los programas que necesitás según entiendo por los nombres para lo que sirven. Sólo nombro algunas, puede haber más, bah, seguro hay más:

ConvertXtoDvd 3 (divx a dvd) --> devede
Subtitle Workshop --> gnome-subtitles, Gaupol
Nero CoverDesigner --> discwrapper ([http://ubuntuforums.org/showthread.php?t=933474](http://ubuntuforums.org/showthread.php?t=933474))
MediaChance.DVDLab.Pro --> creo que devede otra vez

En cuanto a la impresora y el video habría que buscar un poco más. También es recomdable que pruebes el LiveCD, para saber qué funciona de una y qué no.

Saludos

---

### Post by Carlos 2009 on 2009-01-12
Estaba viendo que ubuntu ahora se puede instalar como si fuese un programa mas en windows???? puede ser..??

Esto me vendria al pelo para probar bien que anda y que no, es mejor que el livecd, creo yo, o no?

---

### Post by luks911 on 2009-01-12
> **Carlos 2009 said:**
> Estaba viendo que ubuntu ahora se puede instalar como si fuese un programa mas en windows???? puede ser..??

Esto me vendria al pelo para probar bien que anda y que no, es mejor que el livecd, creo yo, o no?

Mi humildísima opinion es que no es mejor, je. Para probar metés el LiveCD, booteas y sabés cómo va sin modificar nada. Lo cual no quita que al instalar algún driver vaya a mejorar. Por ejemplo, mi placa wifi necesita la instalación de determinado driver, lo mismo que mi placa de video. Así que con el CD no tenía ni wifi ni aceleración 3D.
Con el LiveCD tenés la seguridad de que no hacés ningún cambio a tu máquina. Mientras que con la instalación desde win estás poniendo ubuntu en tu disco y haciendo cambios. 
Otra opinión: teniendo un disco tan amplio y con espacio libre, haría un particionado para instalar Ubuntu desde sí mismo :-P y no con wubi, que lo instala como una aplicación para windows. Tené en cuenta que hay una herramienta gráfica e intuitiva para particionar desde el CD (Gparted) y que Ubuntu no requiere mucho espacio en disco para el sistema (10Gb, más el swap de 1GB, más el home casi a gusto).
Espero no haberte confundido.

:lolflag:

---

### Post by Air23 on 2009-01-12
> **Carlos 2009 said:**
> 

1- ConvertXtoDvd 3 (divx a dvd)



En los repositorios de ubuntu tenes el DeVede (para mas data: [http://www.rastersoft.com/programas/devede_es.html](http://www.rastersoft.com/programas/devede_es.html)) y otra opcion puede ser ManDVD (aca podes bajar debs [http://www.getdeb.net/app/ManDVD](http://www.getdeb.net/app/ManDVD))
Si ninguno te convence (como me paso a mi) podes usar el convertxtodvd con wine. Las versiones nuevas del convertxtodvd no andan muy bien con wine pero las mas viejitas andan bastante bien (no se puede previsualizar el video pero la conversion la hace sin problemas)

> **Carlos 2009 said:**
> 

2- Subtitle Workshop (subtitulos)



Gnome Subtitles ([http://gnome-subtitles.sourceforge.net/](http://gnome-subtitles.sourceforge.net/))  o Subtitle Editor ([http://home.gna.org/subtitleeditor/](http://home.gna.org/subtitleeditor/)). Ambos estan en los repositorios

> **Carlos 2009 said:**
> 

5- MediaChance.DVDLab.Pro (autoria de dvd)



'Q' DVD-Author ([http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)) y DVD Styler ([http://www.dvdstyler.org/](http://www.dvdstyler.org/) y [http://sourceforge.net/project/showfiles.php?group_id=92301&package_id=97621](http://sourceforge.net/project/showfiles.php?group_id=92301&package_id=97621)). El QDVD Author esta en los repos, el otro no pero hay debs.

Saludos

---

