---
title: "Soy nuevo y necesito ayuda por favor"
date: 2009-05-17
forum: Software
---

### Post by elvis77 on 2009-05-17
Hola, hace unos 20 dias que me instale Ubuntu en la notebook. Venia usando Vista pero colapso por un virus, tuve que formatear toda la maquina y como venia hace tiempo con ganas de pasar a Ubuntu lo hice y la verdad es que no me puedo quejar, me vengo desenvolviendo bastante bien. Pero me surgio un problema. Yo venia haciendo catalogos con un programa muy sencillo llamado "Directory link" que lo que hacia era crearme archivos html del contenido del cd o dvd que le cargara y creaba archivos llamados "dvd 1", "dvd 2" y asi. A partir de ahi cuando queria buscar algun disco iba al explorador de Windows y ponia, por ejemplo, "Beatles", y me decia en que cd o dvd aparecia la palabra "Beatles". Muy sencillo. El tema es que con el "explorador" de Ubuntu si quiero buscar el nombre de una banda dentro de la carpeta con todos los archivos .html no me los encuentra. Conocen algun programa o saben como tengo que hacer para poder buscar palabras dentro de archivos html?
Si me ayudan se los agradecere mucho.
Saludos.

Elvis

---

### Post by pablo.s on 2009-05-17
Hola: Si sos nuevo, mi recomendación
no te va a servir, porque implica conocer
el funcionamiento de comandos básicos
de consola como cat, sed y grep.
Supongo que a falta de otra sugerencia
puedo comentarte que hay un programa
que se llama GnomeCatalog, que es muy
similar a lo que necesitás, lo malo que 
tiene es que no se con certeza si te va a
reconocer los archivos que ya tenés en
HTML como parte de la base de datos.
Aunque podés probar si te sirve. Es
probable que alguien sugiera algún
programa mas útil y aproximado a lo que
estás buscando.

---

### Post by luks911 on 2009-05-17
El buscador de Nautilus (el explorador de Ubuntu ;-) ) debería servir. Es cuestión de que uses las opciones de búsqueda. Por ejemplo, que busque archivos con el contenido "beatles", en la carpeta donde tenés los html y que en el nombre contengan "html". Esto más allá de otras posibilidades que pueda haber.

---

### Post by Mauro22 on 2009-05-17
Si no entendi mal vos tenes un archivo html por cd, donde adentro de ese archivo esta todo lo que contiene el cd, no?


En ese caso, desde la consola podes hacer:

grep textoabuscar *.*


textoabuscar es lo que queres encontrar (si tiene espacios va entre comillas) y lo que le sigue es el filtro (en este caso si pones html no te devuelve en que archivo esta)


Ejemplo, 

hice un html con la palabra beatles adentro y corri el comando y me devolvio:

```

mauro@mauro-acer:~$ grep beatles /home/mauro/*.*
/home/mauro/dvd1.html:beatles
mauro@mauro-acer:~$

```

Proba con los que tenes y con ese comando a ver si te lo encuentra.

/home/mauro es mi carpeta personal, vos tendrias otro nombre.

---

### Post by staar on 2009-05-17
no creo que necesites ningún programa en especial, con la Terminal basta y sobra, el procedimiento sería así:

-Abrís la Terminal, Aplicaciones > Accesorios > Terminal

-Por defecto al abrir la Terminal, el directorio donde te encontrás es tu home, vos tendrías que moverte al directorio donde estén esos .html, para eso usas el comando 'cd' (de 'change directory'): ```
cd */ruta/al/directorio/con/los/html*
```

-luego usas el comando 'grep', que lo que hace es imprimir lineas que se correspondan con una expresión dada, es decir busca, en los archivos que se le indica, la expresión que se le indica, y muestra la línea que contiene dicha expresión, vos tendrías que usarlo así: ```
grep -l Beatles ./*
``` donde -l (un guión y una ele) es para que te devuelva el nombre de archivo y no la línea, Beatles es lo que querés buscar y ./* le indica que busque en todos los archivos (*) del directorio actual (./)

para que esto te funcione, los html deben estar todos en una carpeta (o dentro de subcarpetas en una misma carpeta, en cuyo caso el directorio al que te tendrías que mover es al que esté más arriba y contenga esas subcarpetas) y su nombre de archivo debe de ser explícito en cuanto a que contiene (si es el html del dvd1, que el archivo se llame dvd1.html) para que no te confundas con la salida del grep...

saludos

---

### Post by elvis77 on 2009-05-18
Muchas gracias amigos, pude solucionarlo gracias a sus aportes.
Comprobe por primera vez lo que varios me habian dicho, que la comunidad Ubuntu responde al instante ante cualquier duda.
Que bueno empezar a ser parte de esto.
Espero alguna vez poder yo responder preguntas de gente que tenga dudas.
Abrazo!

Elvis

---

### Post by juancarlospaco on 2009-05-18
Tendrias que buscarte un Catalogador Grafico si lo usas con frecuencia, 
... en Synaptic hay, en Launchpad Tambien.

---

### Post by EnriqueK on 2009-05-18
Yo uso el catalogador **Cathy** , vas a necesitar Wine por que es para windows, es gratuito y extremadamente rápido para catalogar y sobretodo para hacer búsquedas, lástima que en Linux no tiene la funcionalidad de mandar a ejecutar el archivo encontrado, pero es un detalle de comodidad.
Uso el Cathy simplemente por que no encontré nada mejor tanto en win como en Linux.

---

### Post by emiliano_raso on 2009-05-18
> **elvis77 said:**
> Muchas gracias amigos, pude solucionarlo gracias a sus aportes.
Comprobe por primera vez lo que varios me habian dicho, que la comunidad Ubuntu responde al instante ante cualquier duda.
Que bueno empezar a ser parte de esto.
Espero alguna vez poder yo responder preguntas de gente que tenga dudas.
Abrazo!

Elvis

Este tipo de mensajes me ponen re feliz :oops::oops:
Porque a el le gustó y va a repartir mugre con 2 o 3 mas, y esos con otros y asi y asi y asi...

Estoy diciendo algo que todos sabemos, pero es que fue la primera vez que leo que una persona agradece así :-P

---

