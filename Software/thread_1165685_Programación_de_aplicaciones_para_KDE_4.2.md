---
title: "Programación de aplicaciones para KDE 4.2"
date: 2009-05-20
forum: Software
---

### Post by fgl82 on 2009-05-20
Hola a todos y de antemano disculpa a los moderadores, porque es el 3er Thread que posteo en la sección general y no sé realmente si debería o no postearlo en software. De a poco voy viendo según lo que posteo dónde puedo ubicar futuras consultas. 

Mi duda es, básicamente, si me interesa desarrollar aplicaciones para KDE 4, con qué me convendría empezar, a saber:

- lenguaje recomendado
- IDE recomendada
- Constructor de interfaz recomendado, si existiera uno
- Cualquier otra cosa que puedieran recomendarme

Supongo que en este thread me podrá ayudar Hei-Ku, uno de los desarrolladores de KMyMoney.

Gracias desde ya a todos los que me vayan a responder y, una vez más, disculpas si este thread no está donde debería.

¡Saludos!

---

### Post by guillermolisi on 2009-05-20
> **fgl82 said:**
> Hola a todos y de antemano disculpa a los moderadores, porque es el 3er Thread que posteo en la sección general y no sé realmente si debería o no postearlo en software. De a poco voy viendo según lo que posteo dónde puedo ubicar futuras consultas. 

Mi duda es, básicamente, si me interesa desarrollar aplicaciones para KDE 4, con qué me convendría empezar, a saber:

- lenguaje recomendado
- IDE recomendada
- Constructor de interfaz recomendado, si existiera uno
- Cualquier otra cosa que puedieran recomendarme

Supongo que en este thread me podrá ayudar Hei-Ku, uno de los desarrolladores de KMyMoney.

Gracias desde ya a todos los que me vayan a responder y, una vez más, disculpas si este thread no está donde debería.

¡Saludos!
Lenguaje: Python / C++ (gran parte si no todo KDE4 esta escrito con C++)
IDE: Desde el vi hasta Eclipse, pasando por todas las que se te ocurran. Esto es como el perfume, cada cual con sus gustos y comodidades.
Interface: KDE4 usa Qt 4.X

Leer mucho y empezar por cosas sencillas que no te frustren y te permitan ver como avanzas en el dominio de las herramientas. Faltaria una pregunta referida a bibliotecas/librerias funcionales para usar en los desarrollos.

---

### Post by Hei Ku on 2009-05-20
<autobombo>
Je. Definitivamente te recomiendo C++. Y es mas, hay un programa en kde/playground que necesita MUCHA, PERO MUCHA ayuda de desarrolladores para portarlo a KDE4 :lolflag:
</autobombo>

Como dijo Guillermo, tenes python/C++. Si queres hacer plasmoids, hasta podes hacerlos en javascript o java, a traves de QtJambi.

IDE: Tenes el KDevelop3, o el 4 en beta o alpha, el QtCreator, el QDevelop y el Eclipse con CDT y el plugin de Qt. Yo en este momento uso el Kate. :D

Interfase: Qt4/KDE4. Si usas Qt4 solamente, supuestamente es portable a multiples plataformas sin problemas (guiño, guiño, porque existen particularidades) Si usas KDE4, podes aprovechar cosas como plasma, akonadi, nepomuk, etc.

Algo que no mencionaste, y que es importante, son las build tools. En KDE4 es todo cmake. En Qt4 tenes qmake. De ambos hay bastante informacion.

Recomendación: o empezas por hacer un hola mundo y arrancas desde ahi, o te vas a algun programa que te guste y uses mucho, le buscas algun error, y te bajas el codigo, te fijas si el error sigue en la nueva version, y tratas de arreglarlo y mandar un patch a la lista de ese programa. Yo empece asi, aunque el error ya estaba arreglado en CVS, asi que me meti por otro lado, me embalé, y mi primer patch termino siendo un modulo nuevo. :p

---

### Post by guillermolisi on 2009-05-21
Un detalle mas: Lee sobre programacion de objetos (que **no** es lo mismo que programacion *orientada* a objetos), tanto sus fundamentos como la aplicacion y uso con C++ y Python.

Con todo esto tenes para divertirte un buen rato.

---

### Post by fgl82 on 2009-05-21
OK muchachos, gracias por las respuestas, pero me dejaron algunas dudas:

1) Yo cuando hablaba de "construcción de interfaz" me refería a alguna aplicación gráfica/plugin de eclipse/lo que sea, que me ayudara a armar la parte visual. Digamos, algo como tiene el netbeans para armar la interfaz de las aplicaciones desktop. A eso me refería y creo que no me hice entender.

2) No entiendo bien qué querés decir, Hei-Ku, al decir que KDE4 es todo cmake pero QT4 usa qmake. O sea, entiendo que son dos compiladores distintos, pero no entiendo la diferencia que establecés entre "KDE4" y "QT4"; mi impresión era que KDE4 usaba las librerías de QT4 para armar la interfaz gráfica. O sea, mi idea era:

KDE4 = D.E.
QT4 = Librerías

¡¡¡Gracias por las respuestas!!!

pd: mi idea es empezar con un hola mundo, siempre empiezo así, lo encuentro más esclarecedor que meterme a corregir cosas sin saber bien como funciona lo otro alrededor de ellas.

EDIT: pd2: tenía pensado usar Python que me pareció muy lindo lenguaje, ¿cuál sería la ventaja de usar C++?

---

### Post by Hei Ku on 2009-05-21
1) Tenés el Qt Designer, para armar archivos .ui que despues en tiempo de compilacion generan los stubs correspondientes para la interfaz. [http://doc.trolltech.com/4.5/designer-manual.html](http://doc.trolltech.com/4.5/designer-manual.html)

Personalmente, yo prefiero muchas veces abrir el xml directo y laburarlo asi, pero es por deformacion profesional. :p

2) Obviamente cuando programas para KDE usas mucho de CMake, pero KDE te da un monton de cosas extra que vienen bien. Por ej, el manejo de configuracion del programa, a traves un framework llamado KConfigXT, para que solo tengas que armar un xml. Tenes tambien los colores o settings generales de KDE, accesibles por KGlobalSettings o KColorScheme. Despues, widgets especializados, como KMessageBox, KRecentFilesAction, KStandarAction, o similares. Cosas que si bien la base es Qt, KDE los especializó para hacerlo mas facil. O sea, si programas sólo Qt, tenes los ladrillos basicos, pero con KDE tenes un monton de cosas mas especificas que te permiten hacer las cosas mas rapido. 

Cuando utilizas KDE, cmake tiene una serie de macros particulares para KDE que te simplifican la vida al momento de compilar. Que yo sepa, qmake no las tiene, asi que tendrias que hacer esos pasos a mano en los scripts.

Se entiende un poco mas?

---

### Post by fgl82 on 2009-05-21
Si, se entiende mucho más.

Si entendí bien, lo mejor sería utilizar cmake como compilador ya que acepta los agregados que KDE hace sobre las apis standard de QT, ¿correcto? (si no me interesa que la aplicación sea portable, que no, no me interesa, yo sólo quiero que ande en KDE4 por ahora)

Igual cuando me hablás del xml ese de configuración para mí es (aún) chino básico :lolflag:

Por otro lado, quizá no viste mi edit, pero pregunté por qué preferís C++ a Python, si por un tema de costumbre o bien porque realmente te permite hacer más cosas. No lo pregunté así =P pero reformulo porque es lo que realmente quería preguntar.

---

### Post by Hei Ku on 2009-05-21
Y...mas que todo es costumbre. Yo vengo del mundo de C y Java. 

En cuanto a Python, todos los comentarios que escuché es que es muy bueno. Mi duda es cuánto se la banca para aplicaciones bien grandes, y por otro lado, KDE esta hecho en C++. Python funciona a través de bindings. Que yo sepa anda barbaro, pero siempre tenes una capa extra al medio.

Toma mi predilección por C++ como un achaque de viejo nostalgico de cuando en su adolescencia programaba en C. :lolflag:

---

### Post by fgl82 on 2009-05-21
Entiendo :D.

El tema es que yo he programado en C, C# y Java, pero nunca en C++ y lo que escuché por ahí es que es medio enquilombado.

La otra vez estuve haciendo algunas pavadas de consola con Python, empecé con algo estructurado y luego hice algo ya con clases; me gustó mucho y lo entendí rápido con la ayuda de un libro bastante conocido sobre ese lenguaje.

¿Qué tan difícil es, para vos, la transición de C/C#/Java a C++?

---

### Post by Hei Ku on 2009-05-21
Creo que si sabes programar bien en C y Java, no deberias tener problemas con C++. Tené en cuenta que los toolkits (Qt, KDE libs) te solucionan muchas de las cosas más complicadas de C++.

La parte que más me costó y me cuesta, fue la compilación, pero eso es porque yo desarrollo para un proyecto grande, donde la compilación no es algo trivial.

---

### Post by fgl82 on 2009-05-21
OK, entonces pongo manos a la obra :D

Si, lo de la compilación me lo temía, pero bueno, veré sobre la marcha; no creo que lo que yo voy a empezar a hacer me dé demasiados dolores de cabeza.

¡Gracias por todo!

---

