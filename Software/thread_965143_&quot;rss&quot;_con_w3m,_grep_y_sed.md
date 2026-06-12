---
title: "&quot;rss&quot; con w3m, grep y sed ?"
date: 2008-10-31
forum: Software
---

### Post by c4d0rn4 on 2008-10-31
Que tal gente, inspirado por un script que permite ver la temperatura en conky, he pensado en hacer una suerte de rss de algunas páginas que NO poseen rss, o no del modo que yo quisiera.

La utilidad en cuestión son unos blogs y foros que actualizan los post poniendo links nuevos una vez por semana, pero no son tan religiosos que digamos en la puntualidad.

El script en cuestión fue este:

```
#!/bin/bash
sciezka=~/scripts
kod=ARDF0002
plik=~/weather
 	w3m -dump http://weather.yahoo.com/forecast/"$kod"_c.html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik

	stan=`head -n3 $plik | tail -n1`
	temp=`tail -n1 $plik | awk '{print $1}'`
	tempo=`head -n6 $plik | tail -n1`
	cisn=`head -n8 $plik | tail -n1`
	wiatr=`head -n16 $plik | tail -n1`
	wilg=`head -n10 $plik | tail -n1`
	wsch=`head -n18 $plik | tail -n1`
	zach=`head -n20 $plik | tail -n1`
	if [ `cat "$sciezka"/pogodynka.sh | grep -x "# $stan" | wc -l` -eq 0 ]
	  then
		stanpl=$stan
	  else
		stanpl=`cat "$sciezka"/pogodynka.sh | grep -xA1 "# $stan" | tail -n1 | awk '{print $2,$3,$4,$5,$6,$7}'`
	fi

	echo $temp C  / $zach / $stan
```

(creo)Tengo idea de cual es el principio que utiliza: w3m le da el texto a grep, este obtiene las líneas que necesita y sed no palida idea jaja xD, ¿le da formato?.

Traté de leer pero no entiendo muy bien el uso y funcionalidad real de grep y sed; alguien me da un empujoncito como para empezar?

---

### Post by clasificado on 2008-10-31
grep busca texto, es como el buscar en un notepad.
sed reemplaza texto, es como el "buscar y reemplazar" en el notepad.

Ambos usan la sintaxis de Regular Expressions

Son programas escritos por humanos, pero el concepto es Poder de Dios.

Ahora miro un poco mas el script y veo que entiendo

clasificado

---

### Post by c4d0rn4 on 2008-11-02
Que tal gente,

bueno por ahora tengo esto; pero no me devuelve nada el echo jajjaa xD

Alguna idea de porqué pasa eso?

```
#!/bin/bash
rm prueba.txt
tora= w3m -dump http://www.mcanime.net/descarga_directa/anime/detalle/ddmursonline_toradora_04_55mb/10149 | grep -A 15 "Capitulo 1"
big= w3m -dump http://www.tv-mafia.com/the_big_bang_theory | grep -A 15 "The Big Bang Theory - Season 2"


echo $tora >> prueba.txt


gedit prueba.txt
```


Edit: ya pude hacer a Groserisimo modo lo que quería.

```
#!/bin/bash
rm prueba.html
echo `w3m -dump_source http://www.mcanime.net/descarga_directa/anime/detalle/ddmursonline_toradora_04_55mb/10149 | grep -A 15 "Capitulo 1";  w3m -dump_source http://www.tv-mafia.com/the_big_bang_theory | grep -A 15 "The Big Bang Theory - Season 2" ` >> prueba.html


firefox prueba.html
```

Pero me deja muchas dudas. Como puedo establecer el valor de una variable tipo $cosa1 $cosa2 y después hacer echo a esa variable =S

y otra es, echo no puede sobreescribir un archivo?. La verdad es 103% ensayo y error lo que hice; pero me gustaría tener más idea para poder mejorarlo.

---

