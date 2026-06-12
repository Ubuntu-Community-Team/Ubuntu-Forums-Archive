---
title: "Problema Wine Patch"
date: 2009-02-16
forum: Software
---

### Post by sebasthian777 on 2009-02-16
Hola de nuevo fieles seguidores del pinguino endemoniado. Vuelvo por estos pagos para seguir con mi mision de aprender linuSSSSSSSSSS

Se me presento un problema a la hora de instalar una herramienta de programacion bajo WINE...

Estoy queriendo instalar el RAD Studio 2007 (delphi) y obviamente lo estoy subiendo sobre wine (si si, ya se que tengo el lazarus y el kylix, pero necesito por fuerzas mayores el RAD delphi, es porque me lo piden asi en el laburo)

a la hora de instalarlo me sale un error....

El error es del tipo de: InstallAware Wizard 
y el error es : Runtime Error in install: Cannot open AVI.
(no, no me mande a este foro sin antes buscar nada por internet)
ahora bien, busque por internet posibles soluciones para este problema y enontre en la pagina de Wine que hay un patch para este tipo de errores, tiran el link ( [http://appdb.winehq.org/commentview.php?iAppId=5880&iVersionId=13890&iThreadId=40480]("http://appdb.winehq.org/commentview.php?iAppId=5880&iVersionId=13890&iThreadId=40480") el ultimo comentario es ) que lleva a esta pagina despues [http://bugs.winehq.org/attachment.cgi?id=12843]("http://bugs.winehq.org/attachment.cgi?id=12843")


cuando habro ese link solamente me aparece esto:

```
diff --git a/dlls/msvidc32/msvideo1.c b/dlls/msvidc32/msvideo1.c
index 9de2a2d..b5a2f04 100644
--- a/dlls/msvidc32/msvideo1.c
+++ b/dlls/msvidc32/msvideo1.c
@@ -383,6 +383,8 @@ static LRESULT CRAM_DecompressBegin( Msvideo1Context *info, LPBITMAPINFO in, LPB
         info->mode_8bit = 1;
     else if( in->bmiHeader.biBitCount == 16 )
         info->mode_8bit = 0;
+    else if( in->bmiHeader.biBitCount == 24 )
+        info->mode_8bit = 0;
     else
     {
         ERR("Bad output format\n");

```

y no se como instalar eso en wine.... alguine sabe como se hace asi sigo investigando?


desde ya como siempre gracias gente!!!!
salu2 grandes!

---

### Post by guillermolisi on 2009-02-16
> **sebasthian777 said:**
> Hola de nuevo fieles seguidores del pinguino endemoniado. Vuelvo por estos pagos para seguir con mi mision de aprender linuSSSSSSSSSS

Se me presento un problema a la hora de instalar una herramienta de programacion bajo WINE...

Estoy queriendo instalar el RAD Studio 2007 (delphi) y obviamente lo estoy subiendo sobre wine (si si, ya se que tengo el lazarus y el kylix, pero necesito por fuerzas mayores el RAD delphi, es porque me lo piden asi en el laburo)

a la hora de instalarlo me sale un error....

El error es del tipo de: InstallAware Wizard 
y el error es : Runtime Error in install: Cannot open AVI.
(no, no me mande a este foro sin antes buscar nada por internet)
ahora bien, busque por internet posibles soluciones para este problema y enontre en la pagina de Wine que hay un patch para este tipo de errores, tiran el link ( [http://appdb.winehq.org/commentview.php?iAppId=5880&iVersionId=13890&iThreadId=40480](http://appdb.winehq.org/commentview.php?iAppId=5880&iVersionId=13890&iThreadId=40480) el ultimo comentario es ) que lleva a esta pagina despues [http://bugs.winehq.org/attachment.cgi?id=12843](http://bugs.winehq.org/attachment.cgi?id=12843)


cuando habro ese link solamente me aparece esto:

```
diff --git a/dlls/msvidc32/msvideo1.c b/dlls/msvidc32/msvideo1.c
index 9de2a2d..b5a2f04 100644
--- a/dlls/msvidc32/msvideo1.c
+++ b/dlls/msvidc32/msvideo1.c
@@ -383,6 +383,8 @@ static LRESULT CRAM_DecompressBegin( Msvideo1Context *info, LPBITMAPINFO in, LPB
         info->mode_8bit = 1;
     else if( in->bmiHeader.biBitCount == 16 )
         info->mode_8bit = 0;
+    else if( in->bmiHeader.biBitCount == 24 )
+        info->mode_8bit = 0;
     else
     {
         ERR("Bad output format\n");

```y no se como instalar eso en wine.... alguine sabe como se hace asi sigo investigando?


desde ya como siempre gracias gente!!!!
salu2 grandes!
Lo que te estan mostrando con la ejecucion del comando diff entre esos dos archivos de c, son las diferencias entre el original (indicado con un prefijo a) y el modificado (indicado con el prefijo b).

Entonces editas el que tengas en tu maquina, previa copia de resguardo por las dudas, y le agregas las lineas indicadas con un signo + en la columna 1.

Aparentemente le han agregado un "if" para controlar profundidad de 24 bits en los colores de video y antes parece que solo llegaban a 16 bits (luego daba mensaje de error).

Lo que no se, porque en realidad no fui a leer la documentacion del patch al site de Wine, es si hay que compilar o se deja como esta.

---

### Post by sebasthian777 on 2009-02-17
Hola, estuve probando el comando Diff, pero no tiene incluida la sentencia "--git"

??

esta bien que esto sea asi?

---

### Post by Hei Ku on 2009-02-17
es que no es un comando.
Eso que ves es un archivo con un parche, y la parte de "diff --git ..." es el encabezado, que dice que es un parche de git, de tal archivo, de tal version.

---

### Post by guillermolisi on 2009-02-17
Ademas, no tenes que correr diff, como comente, tenes que agregar las lineas que estan marcadas con un signo + en la columna 1 de cada una con un editor de texto tipo nano, vi, etc. (dependiendo de la cantidad de pelos que tengas en el pecho y/o espalda :)  )

---

### Post by sebasthian777 on 2009-02-17
> **guillermolisi said:**
> Ademas, no tenes que correr diff, como comente, tenes que agregar las lineas que estan marcadas con un signo + en la columna 1 de cada una con un editor de texto tipo nano, vi, etc. (dependiendo de la cantidad de pelos que tengas en el pecho y/o espalda :)  )



a ver si entendi por las moscas de que me mande una *****....


tengo que buscar el archivo msvideo1.c ... editarlo y agregarle las lineas que tienen un + en col 1....

si es asi.... busque el archivo por todos lados pero no lo encuentro....

el que si encontre es el msvidc32.dll.so, tiene que ver con ese?

este archivo que dije a lo ultimo esta dentro del directorio /usr/lib/wine

(se sarpan en la ayuda! muchas gracias!!!! =D)

---

### Post by guillermolisi on 2009-02-17
> **sebasthian777 said:**
> a ver si entendi por las moscas de que me mande una cagada....


tengo que buscar el archivo msvideo1.c ... editarlo y agregarle las lineas que tienen un + en col 1....

si es asi.... busque el archivo por todos lados pero no lo encuentro....

el que si encontre es el msvidc32.dll.so, tiene que ver con ese?

este archivo que dije a lo ultimo esta dentro del directorio /usr/lib/wine

(se sarpan en la ayuda! muchas gracias!!!! =D)
Suponiendo que el resultado de tu busqueda es correcto, entonces luego de modificar ese archivo fuente (el que termina con .c) deberias compilarlo para generar una nueva version del que encontraste (que es el objeto, por eso la terminacion con .so).

Todo esto sin considerar otras posibles alternativas como ser aplicar el parche sobre el modulo .so que ya tenes con algun editor hexadecimal (y no es chiste) u obtener la version binaria de ese programa/DLL ya arreglado (con lo cual el tema se reduce a reemplazar un archivo por otro).

Aclaro que aun no entre en el site de Wine para indagar mas a fondo este tema.

---

### Post by sebasthian777 on 2009-02-17
Guillermo,

te agradesco enormemente la buena onda que le pusiste.

creo que ya encontre la solucion pero se me esta terminando el tiempo en el laburo asi que posiblemente lo termine mañana,

apenas termino vuelvo a estos pagos y explico como lo arregle...

otra vez gracias por la buena onda...


pd: puede que todo salga mal y que me tengas preguntando mas cosas otra vez JAJAJAJA

salu2!!!!

---

### Post by guillermolisi on 2009-02-17
> **sebasthian777 said:**
> Guillermo,

te agradesco enormemente la buena onda que le pusiste.

creo que ya encontre la solucion pero se me esta terminando el tiempo en el laburo asi que posiblemente lo termine mañana,

apenas termino vuelvo a estos pagos y explico como lo arregle...

otra vez gracias por la buena onda...


pd: puede que todo salga mal y que me tengas preguntando mas cosas otra vez JAJAJAJA

salu2!!!!
Ningun problema mientras mantengas una actitud positiva en busca de la solucion :)

Conta como te fue !

---

### Post by sebasthian777 on 2009-02-18
Uf, en el laburo me apuraron un poco, asi que decidi instalar virtual box, xp arriba y despues delphi (o estoy en eso).
Pero me quede con las ganas de ver como se hace el tema, asi que cuando tenga un poco de tiempo despues de los finales en la facu, lo vere tranca en casa y les comentare que onda con el tema.

Pero de igual forma agradesco infinitamente la ayuda, Me encanta este foro, siempre encontras gente copada que esta mas que dispuesta a darte una mano! salu2 enormes gente!
see ya!

---

