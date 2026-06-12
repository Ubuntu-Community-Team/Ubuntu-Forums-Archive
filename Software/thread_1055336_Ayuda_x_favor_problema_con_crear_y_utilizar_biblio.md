---
title: "Ayuda x favor::: problema con crear y utilizar bibliotecas con g++"
date: 2009-01-30
forum: Software
---

### Post by danukmen on 2009-01-30
help! help!
me vengo recorriendo cuanto foro me cruso pidiendo ayuda 
y vengo ante ustedes de rodillas suplicando una solucion 

( un poco dramatico pero bue )

la onda es asi

estoy aprendiendo a programar en c ++ y un libro me dice q tengo q hacer algo con 2 listados

1:
//archivo de encavesado
#ifndef __21-a_H
#define __21-a_H

int fib (int n);

#endif

2:
#include <iostream>
#include "/home/d/c**/21-a.h"
using namespace std;

//archivo fuente de biblioteca 22-a.h

int fib (int n)
{
	cout << "procesando fib(" << n << ") ..." ;
if (n < 3 )
{
	cout << " regresa 1 !\n";
	return 1;
}
else
{
cout << "llama a fib(" << n-2 << ") y a fib(" << n-1 << " ).\n";
	return (fib(n-2) + fib(n-1));
 }
}



yo se que devo compilar de alguna manera el segundo pero para eso lo tengo q hacer tambien con el primero pero ahi esta el problema nose q hacer con el primero

x fa alguien q me allude a hacer funcionar esta cosa

PD: ya busque por varios lados las soluciones incluso el libro salu2!

---

### Post by sherwoodinc on 2009-01-30
Uno de los archivos (el 1) es el "header", donde se declaran las funciones que después se escriben en el otro archivo (el 2), que se llama "archivo fuente".

Con el 1er archivo no tenés que hacer nada a priori, si te fijás en el listado del segundo, la línea
```
#include "/home/d/c**/21-a.h"
``` ya está haciendo uso del contenido del "header".

El archivo que tenés que compilar es el segundo. En una Terminal, escribiendo el comando 
```
g++ -c 21-a.cpp
``` (suponiendo que el archivo fuente se llama "21-a.cpp"
se te va a generar un archivo compilado, llamado "21-a.o".

Este archivo compilado en principio no es ejecutable, porque no contiene ninguna función "main" que es la que debe estar presente en un ejecutable.

Supongo que en tu libro te explicarán bien todas estas cosas...

PD: Si no te encuentra el comando "g++", vas a tener que instalarte el paquete "g++" en el synaptic.

PD2: Si al archivo 2 le agregás lo siguiente:
```

int main()
{
   fib(10);

   return 0;
}

```
y lo compilás con
```
g++ 21-a.cpp -o 21-a.bin
```
te va a crear un archivo ejecutable llamado "21-a.bin" que se puede ejecutar desde tu Terminal con
```
./21-a.bin
```
y debería calculaarte el fibonacci 10.

---

### Post by Hei Ku on 2009-01-30
Instalate el paquete build-essential, que tiene todo lo necesario para compilar.

sudo aptitude install build-essential

---

### Post by danukmen on 2009-01-31
es q me sige dando el mismo herror el primero le puse 

21-a.h

y el segundo
21-b.cpp


cuando compilo el segudno me dice:

d@d-lap:~/c**$ g++ -c 21-b.cpp -o 21
En el archivo incluído de 21-b.cpp:2:
/home/d/c**/21-a.h:2:13: aviso: elementos extra al final de la directiva #ifndef
/home/d/c**/21-a.h:3:13: aviso: faltan espacios en blanco después del nombre de macro


y nose que hacer con esto, :-(:(

---

### Post by sherwoodinc on 2009-01-31
Te está compilando bien. Los avisos que te tira son probablemente porque en el nombre que sigue a un #ifndef no pueden ir signos menos '-'.
Reemplazalo por un guion bajo '_'.

El archivo 21-a.h debería quedarte:
```

#ifndef __21_a_H
#define __21_a_H

int fib (int n);

#endif

```

---

### Post by danukmen on 2009-01-31
> **sherwoodinc said:**
> Te está compilando bien. Los avisos que te tira son probablemente porque en el nombre que sigue a un #ifndef no pueden ir signos menos '-'.
Reemplazalo por un guion bajo '_'.

El archivo 21-a.h debería quedarte:
```

#ifndef __21_a_H
#define __21_a_H

int fib (int n);

#endif

```

jajajajajajajajajajajajajajaj


milll graciasss !!!!!!!!!!!!!!!!!!!!!!

no saves lo que te lo agradezco man

mil y 1 gracias

salu2 a toda la comunidad q esta de lujo !!

---

### Post by danukmen on 2009-01-31
nada sigo con problemas

d@d-lap:~/c**$ g++  21-b.cpp -o 21
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18 ) : undefined reference to `main'
collect2: ld devolvió el estado de salida 1

---

### Post by danukmen on 2009-01-31
QUOTE=danukmen;6651204]nada sigo con problemas

d@d-lap:~/c**$ g++  21-b.cpp -o 21
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18) : undefined reference to `main'
collect2: ld devolvió el estado de salida 1

---

