---
title: "software para electronicos como yo"
date: 2009-03-29
forum: Software
---

### Post by infernus92 on 2009-03-29
hola... queria preguntarles a los ubuntueros de mi tema, la electronica, si conocen algun programita de simulacion de circuitos... onda el workbench de windows... pero en ubuntu y si se puede, intentando que sea un poco mas completo...
gracias

saludos

ah... aclaro... si es para gnome mucho mejor... je

---

### Post by rubioo on 2009-03-30
Hola, nunca use workbench, ni mucho menos, pero creo que algo de esto te puede servir:

[http://www.lis.inpg.fr/realise_au_lis/kicad/]("http://www.lis.inpg.fr/realise_au_lis/kicad/")

[http://qucs.sourceforge.net/]("http://qucs.sourceforge.net/")

 
 Saludos!

---

### Post by infernus92 on 2009-03-30
gracias por tu aporte... pero lo que ando buscando es un simulador esquematico para circuitos analogicos y digitales...
encontre klogic, pero es solo digital y casi todo con compuertas... igual gracias

---

### Post by Hernán-Amaya on 2009-03-30
Fijate por acá [0] tal vez te sirva. 

[0]http://www.lug.fi.uba.ar/documentos/lista-herramientas/index.php#SECTION000311000000000000000

---

### Post by EnriqueK on 2009-03-31
Probá con** ktechlab** , está en repositorios

---

### Post by faktorqm on 2009-04-01
Hola, electronico reportandose :P

La ultima FRSL (o algo asi, ya me olvide el nombre) asisti a un taller exclusivamente dedicado a electronica con SL. El resultado fue desastroso. Te cuento mas o menos por que, el chabon que dio la charla decia por ejemplo, para hacer el esquematico, lo haces en tal lado y lo dibujas con tal programa que tenes que conseguir la version 2.0.3.1 por que la 2.0.3.0 se cuelga y la ultima la 2.0.3.2 se cuelga cuando apretas guardar.
Para probar el circuito te tenes que conseguir el ktechlab (o cualquiera parecido) y bajarte las bibliotecas de componentes del sitio tal (que obvio no son libres :O) y listo.

El tipo habia usado un micro parecido a un motorola hc08, no se si era un pic de similares caracteristicas o que onda. La cosa es que programaba en C para no usar assembler (ahora ya es lo mismo... depende del compilador) y tenias que, agarrar tu programa, compilar a MANO con el gcc agregandole las bibliotecas del micro (exclusivas de ese micro solo) y luego tenias otro programa sin interfaz grafica que te intentaba grabarlo si lo enchufabas al puerto serie, pero en los nuevos programadores USB ya no andaba.

Panorama desolador no? si. falta mucho mucho para que aplicaciones potentes como autoCAD, protel, spice, y etc lleguen al mundo de linux, y despues al mundo libre....
De todas maneras te aclaro que si usas motorola, freescale tiene el programita que te hace todo para linux tambien (se llama codewarrior), obviamente necesitas el programador que te venden ellos, pero siempre conseguis un esquematico por la web :P

Si pedis algo parecido al electronics workbench (estas empezando?) hay algo que se llama oregano (un desarrollo de facultad de ingenieria uba) que hace algo parecido. Yo las pocas veces que lo use me puso mas nervioso que otra cosa, pero bueno. Son cuestiones de paciencias :P

De paso cañaso tiro el mangaso: Si alguien tiene el codewarrior para gnu/linux sera bienvenida una copia (por PM por fa) :D ):P

Saludos!!!!

---

### Post by jorgito on 2009-04-07
Hola Faktorqm, 

Otro electronico reportandose. 
Mira, yo probe el Oregano y me parecio de terror. No consegui hacer que converja una sola vez. Sin contar con que no reconocia cosas elementales como una inductancia mutua.
Dicen que el SwitcherCAD de Linear Technology anda perfecto en wine. Ni pienso romperme la cabeza para probarlo asi, porque lo tengo andando en otra maquina. El SwitcherCAD no parece ser mas que un SPICE disfrazado y anda bien.

Espero que te sirva.

Saludos

---

