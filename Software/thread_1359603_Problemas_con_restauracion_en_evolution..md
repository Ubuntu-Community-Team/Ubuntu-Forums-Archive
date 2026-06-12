---
title: "Problemas con restauracion en evolution."
date: 2009-12-19
forum: Software
---

### Post by flakojaime on 2009-12-19
HOla.

Bueno, tengo un problema y no he podido solucionar ni con san google.

Hice un respaldo de evolution (evolution-backup.tar.gz) y luego instale Karmic desde cero.

Todo impecable, excepto que cuando me voy a
[B][I]
archivo => restaurar ajustes[/I][/B] 

y busco el archivo (evolution-backup.tar.gz), me sale un mensaje que me dice:[B][I] 

"Seleccione un archivo de respaldo válido para restaurar"
[/I][/B]
El archivo pesa 280 mb.

Tengo instalado el Evolution 2.28.1 y el karmic actualizado.

¿que me recomiendan?

gracias:guitar:

---

### Post by Carlos C on 2009-12-20
¿Cómo fue que hiciste ese respaldo?

Saludos.

---

### Post by flakojaime on 2009-12-20
> **Carlos C said:**
> ¿Cómo fue que hiciste ese respaldo?

Saludos.


Hola:

Lo hice desde el mismo evolution

archivo=> respaldar

despues se cerro el evolution y comenzo a hacer el respaldo.

):P

---

### Post by Carlos C on 2009-12-20
Verifica la integridad del archivo. Puedes hacerlo así:

```
gunzip -v -t <nombre del archivo>
```

Saludos.

---

### Post by flakojaime on 2009-12-22
> **Carlos C said:**
> Verifica la integridad del archivo. Puedes hacerlo así:

```
gunzip -v -t <nombre del archivo>
```Saludos.

HOla

me sale esto

gunzip -v -t evolution-backup.tar.gz
evolution-backup.tar.gz:    
gzip: evolution-backup.tar.gz: invalid compressed data--crc error

Eso significa que murió el respaldo?


saludos

---

### Post by Carlos C on 2009-12-22
Editado: borro esto porque no esta bien lo que dije y puedo generar una confusión. :(

---

### Post by moreback on 2009-12-22
Me parece que el formato zip es bastante distinto al formato tar.gz. No creo que funcionen esos comandos.

Slds.

---

### Post by Carlos C on 2009-12-22
toda la razón, no va a funcionar.:icon_frown: Borro lo que escribí antes.

---

### Post by Carlos C on 2009-12-22
Ahora sí. Para recuperar ese tipo de archivos se puede instalar el paquete "gzrt". De esa manera se puede usar "gzrecover".
Saludos.

---

### Post by flakojaime on 2010-01-02
Hola,

estoy siguiendo los pasos,  algo estoy haciendo mal al compilar el gzrt-0.5

/Descargas/gzrt-0.5$ make
cc -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -lz  gzrecover.c   -o gzrecover
gzrecover.c:29:18: error: zlib.h: No existe el fichero ó directorio
gzrecover.c:118: error: expected ‘)’ before ‘*’ token
gzrecover.c:136: error: expected ‘)’ before ‘*’ token
gzrecover.c: In function ‘main’:
gzrecover.c:187: error: ‘z_stream’ undeclared (first use in this function)
gzrecover.c:187: error: (Each undeclared identifier is reported only once
gzrecover.c:187: error: for each function it appears in.)
gzrecover.c:187: error: expected ‘;’ before ‘d_stream’
gzrecover.c:244: warning: implicit declaration of function ‘init_zlib’
gzrecover.c:244: error: ‘d_stream’ undeclared (first use in this function)
gzrecover.c:245: warning: implicit declaration of function ‘skip_gzip_header’
gzrecover.c:253: warning: implicit declaration of function ‘inflate’
gzrecover.c:253: error: ‘Z_NO_FLUSH’ undeclared (first use in this function)
gzrecover.c:260: error: ‘Z_OK’ undeclared (first use in this function)
gzrecover.c:260: error: ‘Z_STREAM_END’ undeclared (first use in this function)
gzrecover.c:277: warning: implicit declaration of function ‘inflateEnd’
make: *** [gzrecover] Error 1

baje el archivo de la pagina y en el terminal me sale eso.

De paso muy feliz año!!!:guitar:

---

### Post by Carlos C on 2010-01-03
gzrt está disponible en los repositorios de Ubuntu. Puedes instalar esa versión y te evitas tener que compilarlo.

Saludos.

---

### Post by CdK1 on 2010-01-03
Para que quieres compilar?

CdK1@Caturra:~/Varios$ apt-cache search gzrecover
gzrt - gzip recovery toolkit
CdK1@Caturra:~/Varios$

---

### Post by moreback on 2010-01-04
Más fácil instalar desde este link: [apt:gzrt]("apt:gzrt")

Saludos.

---

### Post by flakojaime on 2010-01-04
> **moreback said:**
> Más fácil instalar desde este link: [apt:gzrt](apt:gzrt)

Saludos.

Hola

Bueno, ya está resuelto el problema del Gzrecover, gracias por los consejos.

Ahora en consola me sale esto:

[B]flako@xps1730:~/Descargas$ gzrecover -v evolution-backup.tar.gz
Opened input file for reading: evolution-backup.tar.gz
Opened output file for writing: evolution-backup.tar.recovered
Premature end of stream at 1048568
Found error at byte 1048572 in input stream
Found good data at byte 1048572 in input stream
Total decompressed output = 0 bytes
[/B]
Están bien escritos los comandos?


saludos....

---

### Post by Carlos C on 2010-01-04
Según parece el comando está bien, pero veo que dice "Total decompressed output = 0 bytes" ¿El archivo "evolution-backup.tar.recovered" está vacío?

---

### Post by moreback on 2010-01-04
Da la impresión que el archivo está dañado y no tiene remedio, probablemente ha quedado truncado al transferirlo entre soportes o por red.

---

### Post by flakojaime on 2010-01-04
> **Carlos C said:**
> Según parece el comando está bien, pero veo que dice "Total decompressed output = 0 bytes" ¿El archivo "evolution-backup.tar.recovered" está vacío?


Hola
el archivo recuperado pesa 407 megas..... el original pesaba 288 mb

saludos

---

### Post by moreback on 2010-01-04
¿Y recuperaste los datos o no?

---

### Post by CdK1 on 2010-01-08
Hola
el archivo recuperado pesa 407 megas..... el original pesaba 288 mb

Entonces, recuperaste los datos?

---

### Post by flakojaime on 2010-01-13
HOla, 

bueno disculpen el retraso.

PUedo ver todos los archivos si monto el tar. Pero no puedo usarlo para restaurar los ajustes, me sigue saliendo archivo invalido.

Cuando lo abro me sale esto (con el gestor de archivadores)
[B]
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors[/B]

Pero si lo monto, logro ver todas las carpetas

saludos!

---

### Post by CdK1 on 2010-01-14
Montalo y copia los archivos y listo....

---

### Post by juniorcas12 on 2010-01-14
Hola amigo de lo comunitario, y del software de código abierto.
cuando yo reinstale el karmic presento algún problema similar ya que tenia un archivo de respado del tipo evolution-backup.tar.gz y al realizar el procedimiento recomendado en la pagina de turorial de evolution aparecía el mensaje "seleccione archivo de restauración valido" o algo así...
el archivo de respaldo lo tenia en la partición de datos que nunca formateo, entonces lo que hice fue copiar el archivo a mi escritorio y desde allí : perfecta la restauración, pienso que tenia que ver con los permisos del archivo. 
ojala te sirva....
no te rindas

---

### Post by flakojaime on 2010-01-15
Ok

Voy a intentar lo que me sugieren..


Gracias por todo..

:popcorn:

---

### Post by brauliocesaralvarez on 2010-02-12
la solucion es facil...solo elimina del archivo de restauracion evolution-backup.tar.gz la extension gz...debe quedar asi: evolution-backup.tar...yo lo hize y de inmediato me restauró los ajustes...saludos.

---

### Post by flakojaime on 2010-02-26
Bueno.

Despues de mucho tiempo intentanto cosas, hice todo lo que me sugirieron.

Al final (lo unico que resulto) monte los archivos e hice un Copy/paste en la carpeta de evolution.:D

Recupere todos los correos y tuve que volver a configurar todas las cuentas.:p

Asi que, muchas gracias a todos por todo.:guitar:

Cada dia se aprende algo nuevo.\\:D/

Saludos

---

