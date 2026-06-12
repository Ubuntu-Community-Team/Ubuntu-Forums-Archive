---
title: "Kubuntu KDE4 ¿Cómo consigo estas librerías?"
date: 2008-09-13
forum: Software
---

### Post by valucha on 2008-09-13
[COLOR="DarkOrchid"]Buenas noches... ¿Cómo andan todos?, espero que bien...
Les cuento mi problema, estoy tratando de instalar unos plasmoids y en un principio me di por vencida porque tenía que compilarlos y nunca logré hacerlo correctamente. Hoy encontré un .deb de uno de los que me interesaba pero cuando lo ejecuto me sale lo siguiente:
 quickaccess: Depende: kdebase-runtime (>= 4:4.1.0) pero 4:4.0.3-0ubuntu2 va a ser instalado
               Depende: kdelibs5 (>= 4:4.1.0) pero 4:4.0.3-0ubuntu5.2 va a ser instalado
               Depende: libplasma2 pero no es instalable
               Depende: libqt4-dbus (>= 4.4.0) pero no es instalable
               Depende: libqt4-network (>= 4.4.0) pero no es instalable
               Depende: libqt4-svg (>= 4.4.0) pero no es instalable
               Depende: libqt4-xml (>= 4.4.0) pero no es instalable
               Depende: libqtcore4 (>= 4.4.0) pero no es instalable
               Depende: libqtgui4 (>= 4.4.0) pero no es instalable

Por lo que no puedo instalarlo correctamente.
Evidentemente no puedo hacer un sudo apt-get install libplasma2 por ejemplo proque me dice que no tiene candidato para su instalación. ¿Dónde o como puedo conseguir esas librerías? y ¿por qué no las tengo? siendo que tengo KDE4.1 actualizado recienttemente y son lso requisitos que me dice el creador que tengo que tener :S....


Espero no joderlos nuevamente... y gracias desde ya..



Edited: Los encontré, el tema es que son para Intrepid y cuando quiero instalarlo me dice que no se puede porque hay conflicto con ciertas librerías, que son las mismas pero en versiones anteriores: ej.libplasma2 no lo puedo instalarporque tengoel libplasma1... ¿Si desinstalo todo los actuales y pongo lo de Intrepid, tendré algún problema de funcionamiento?


Gracias desde ya(nuevamente)
Valen[/COLOR]

---

### Post by Hei Ku on 2008-09-13
y... siempre te podés encontrar con alguna sorpresa, como que dependan de algún kernel en particular y cosas así, sobre todo que son bastante de base. O sea, podes terminar rápido en un dependency hell o haciendo un upgrade a II.

Te podés comprar un problema. Vale la pena por un plasmoid, o podés esperar un mes?

---

