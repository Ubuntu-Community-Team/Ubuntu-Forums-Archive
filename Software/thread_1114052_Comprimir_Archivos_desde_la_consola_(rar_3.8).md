---
title: "Comprimir Archivos desde la consola (rar 3.8)"
date: 2009-04-02
forum: Software
---

### Post by talamilla on 2009-04-02
Hola amigos, sigo investigando ubuntu y necesito saber como comprimir un archivo usando el comando 
```
rar
```

ya que cuando lo ejecuto me sale lo siguiente

```
rar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  a             Add files to archive
  c             Add archive comment
  cf            Add files comment
  ch            Change archive parameters
  cw            Write archive comment to file
  d             Delete files from archive
  e             Extract files to current directory
  f             Freshen files in archive
  i[par]=<str>  Find string in archives
  k             Lock archive
  l[t,b]        List archive [technical, bare]
  m[f]          Move to archive [files only]
  p             Print file to stdout
  r             Repair archive
  rc            Reconstruct missing volumes
  rn            Rename archived files
  rr[N]         Add data recovery record
  rv[N]         Create recovery volumes
  s[name|-]     Convert archive to or from SFX
  t             Test archive files
  u             Update files in archive
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ad            Append archive name to destination path
  ag[format]    Generate archive name using the current date
  ap<path>      Set path inside archive
  as            Synchronize archive contents
  av            Put authenticity verification (registered versions only)
  av-           Disable authenticity verification check
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  df            Delete files after archiving
  dh            Open shared files
  ds            Disable name sort for solid archive
  dw            Wipe files after archiving
  e[+]<attr>    Set file exclude and include attributes
  ed            Do not add empty directories
  en            Do not put 'end of archive' block
  ep            Exclude paths from names
  ep1           Exclude base directory from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  hp[password]  Encrypt both file data and headers
  id[c,d,p,q]   Disable messages
  ierr          Send all messages to stderr
  ilog[name]    Log errors to file (registered versions only)
  inul          Disable all messages
  isnd          Enable sound
  k             Lock archive
  kb            Keep broken extracted files
  m<0..5>       Set compression level (0-store...3-default...5-maximal)
  mc<par>       Set advanced compression parameters
  md<size>      Dictionary size in KB (64,128,256,512,1024,2048,4096 or A-G)
  ms[ext;ext]   Specify file types to store
  n<file>       Include only specified file
  n@            Read file names to include from stdin
  n@<list>      Include files in specified list file
  o[+|-]        Set the overwrite mode
  ol            Save symbolic links as the link instead of the file
  or            Rename files automatically
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  r0            Recurse subdirectories for wildcard names only
  rr[N]         Add data recovery record
  rv[N]         Create recovery volumes
  s[<N>,v[-],e] Create solid archive
  s-            Disable solid archiving
  sc<chr>[obj]  Specify the character set
  sfx[name]     Create SFX archive
  si[name]      Read data from standard input (stdin)
  sl<size>      Process files with size less than specified
  sm<size>      Process files with size more than specified
  t             Test files after archiving
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tk            Keep original archive time
  tl            Set archive time to latest file
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             Create volumes with size autodetection or list all volumes
  v<size>[k,b]  Create volumes with size=<size>*1000 [*1024, *1]
  ver[n]        File version control
  vn            Use the old style volume naming scheme
  vp            Pause before each volume
  w<path>       Assign work directory
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files in specified list file
  y             Assume Yes on all queries
  z[file]       Read archive comment from file
```

No Entiendo que debo poner en los Switch, comprendo que son parametros, pero mi duda es como armar la sentencia final,

suponiendo que tenga una archivo llamado ubuntu.pdf localizado en /home/cristian/Documentos

quizas sea una pregunta muy obvia pero no he dado con la sentencia final, bueno sigo investigando.... saludos

---

### Post by Hei Ku on 2009-04-02
ehhh, es lo mismo que usar el rar en el DOS, no es algo de ubuntu.

Y si no queres usar la terminal, podes usar el ark, o supongo que en gnome desde Nautilius podras hacer click derecho y comprimir.


Para usar el rar desde la consola, deberia ser algo asi:

rar a <archivo.rar> <archivo que queres agregar al rar>

Igualmente, no entiendo por qué no usas la interfaz grafica. 

Si la respuesta es que queres aprender sobre la terminal de ubuntu, proba con un comando que no sea un port de windows. 
En linux se usa gzip y tar para comprimir archivos, que son mas eficientes para comprimir y archivar.

---

### Post by talamilla on 2009-04-02
> **Hei Ku said:**
> ehhh, es lo mismo que usar el rar en el DOS, no es algo de ubuntu.

Y si no queres usar la terminal, podes usar el ark, o supongo que en gnome desde Nautilius podras hacer click derecho y comprimir.


Para usar el rar desde la consola, deberia ser algo asi:

rar a <archivo.rar> <archivo que queres agregar al rar>

Igualmente, no entiendo por qué no usas la interfaz grafica. 

Si la respuesta es que queres aprender sobre la terminal de ubuntu, proba con un comando que no sea un port de windows. 
En linux se usa gzip y tar para comprimir archivos, que son mas eficientes para comprimir y archivar.

Muxhas gracias, pues si usar la consola es uno de mis objetivos... si me dices que gzip y tar son mejores pues voy a usarlos, ahora mismo estoy leyendo sobre eso. Muchas gracias, saludos

---

### Post by clasificado on 2009-04-02
acá te tiro una punta mas:

```
tar -cavvf libros.tar.gz libros/
```
**Eso significa, comprimir como gzip la carpeta libros**
```
tar -xvvf libros.tar.gz
```
**Eso significa, descomprimir el paquete libros en el directorio actual**

_Un par de anotaciones serían:_
[LIST]
[*]tar es un empaquetador, el equivalente linux de rar, zip y todo eso.
[*]**los switches "vv"** son para que te muestre los archivos comprimidos en pantalla. si se los sacás el comando es igual de válido pero silencioso
 "tar -caf" y "tar -xf" respectivamente
[*]**el switch "a"** en el comando de *compresión* significa **comprimir**. si se lo omite, los archivos se empaquetan pero no se comprimen por lo que el tamaño del paquete será igual a la suma de todos los archivos contenidos: por ej: 
"tar -cf archivo.tar carpeta/" Si la carpeta tiene diez archivos de 5 megas, el paquete ocupará 50 y no menos.
[*]**el switch "f"** significa "utilizar archivos en disco". Este switch va siempre, si lo sacás te tira el comprimido a través de la consola. Probalo! es muy divertido aunque no creo que sea lo que buscas.
Sin este switch se usaría, por ejemplo 
"tar -c carpeta/ > carpeta.tar". De esta manera, se enruta el archivo comprimido al ">", haciendo de este un comando muy versátil.
Este switch ocupa un lugar especial, porque además tar es una herramienta de empaquetado multipropósito, increíblemente mas potente que el winzip: Se utiliza para el acceso directo a sistemas de backup de cintas; se puede usar la entrada y salida estándar; o pipes. Cosas que en windows hay que caer en herramientas especializadas (de backup) o directamente no existe (el uso de pipes).
[*]Por último nos quedan los **switch "c" y "x"**, que significan comprimir y descomprimir. respectivamente. otro switch que va en el lugar es el "t", que significa "solo listar archivos". Quedaría algo asi como 
"tar -tvvf libros.tar" y te devuelve en la consola los archivos que hay adentro, nada mas.
[/LIST]
clasificado

---

### Post by josecuervo86 on 2009-04-02
Muy buena la explicación clasificado, yo siempre tengo la duda de porque ponen esos caracteres. Segui desburrando loco!

---

### Post by talamilla on 2009-04-02
muchas gracias muchachos por la atención, estoy probando las sentencias, jejeje esto es muy divertido, yo naci con windows nunca maneje DOS, se podran imaginar que estas cuestiones son mas que interesantes para mí. jejeje:guitar:

---

