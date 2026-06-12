---
title: "Problema con Java"
date: 2009-05-08
forum: Software
---

### Post by kornykyano on 2009-05-08
Estimados amigos les cuento mi tema:

Creo que el problema es con java, porque JDownloader y Freemind no funciona, yo intuyo que fue después de haber instalado Cmap-Tools ( programa para crear mas conceptuales) la semana pasada.
Por lo que veo intenta buscar el archivo "libmawt.so" pero yo lo tengo en "/usr/lib/jvm/java-6-openjdk/jre/lib/i386" se lo puede mover? tendre algun problema mas adelante?.

Saludos



```
cristian@cristian-desktop:~/jDownloader$ java -jar JDownloader.jar
JAR
08/05/2009 11:44:48 - INFO [jd.config.DatabaseConnector(<init>)] -> Loading database
08/05/2009 11:44:48 - INFO [jd.config.DatabaseConnector(checkDatabaseHeader)] -> Checking database
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.Runtime.load0(Runtime.java:787)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.System.load(System.java:1022)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.System.loadLibrary(System.java:1047)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.security.AccessController.doPrivileged(Native Method)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.awt.Dimension.<clinit>(Dimension.java:87)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at sun.misc.Unsafe.ensureClassInitialized(Native Method)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at sun.reflect.UnsafeFieldAccessorFactory.newFieldAccessor(UnsafeFieldAccessorFactory.java:43)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at sun.reflect.ReflectionFactory.newFieldAccessor(ReflectionFactory.java:140)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.reflect.Field.acquireFieldAccessor(Field.java:936)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.reflect.Field.getFieldAccessor(Field.java:917)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.reflect.Field.getLong(Field.java:546)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectStreamClass.getDeclaredSUID(ObjectStreamClass.java:1631)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectStreamClass.access$700(ObjectStreamClass.java:69)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectStreamClass$2.run(ObjectStreamClass.java:442)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.security.AccessController.doPrivileged(Native Method)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectStreamClass.<init>(ObjectStreamClass.java:430)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectStreamClass.lookup(ObjectStreamClass.java:327)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectStreamClass.initNonProxy(ObjectStreamClass.java:564)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readNonProxyDesc(ObjectInputStream.java:1600)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readClassDesc(ObjectInputStream.java:1513)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1749)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.util.HashMap.readObject(HashMap.java:1047)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.lang.reflect.Method.invoke(Method.java:616)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectStreamClass.invokeReadObject(ObjectStreamClass.java:991)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readSerialData(ObjectInputStream.java:1865)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1770)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at org.hsqldb.lib.InOutUtil.deserialize(Unknown Source)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at org.hsqldb.types.JavaObject.getObject(Unknown Source)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at org.hsqldb.jdbc.jdbcResultSet.getObject(Unknown Source)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at jd.config.DatabaseConnector.getData(Unknown Source)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at jd.config.SubConfiguration.<init>(Unknown Source)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at jd.utils.JDUtilities.getSubConfig(Unknown Source)
08/05/2009 11:44:49 - GRAVE [jd.utils.JDUtilities$4(write)] -> 	at jd.Main.main(Unknown Source)
```

```
cristian@cristian-desktop:$ freemind 
ERROR:   Your Java is not a derivative from Sun's code,
         =======================================
         FREEMIND WILL MOST PROBABLY *NOT* WORK,
         =======================================
         define JAVACMD, JAVA_BINDIR, JAVA_HOME or PATH in order
         to point to such a VM. See the manpage of freemind(1) for details.
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at java.awt.Component.<clinit>(Component.java:568)
Could not find the main class: freemind.main.FreeMind. Program will exit.

```

---

### Post by pro003 on 2009-05-08
mi amigo, usted debe tratar de instalar Java en la manera regular, yo siempre hago:
```

# sudo apt-get update
# sudo apt-get install ubuntu-restricted-extras 
# sudo apt-get install -f
```

buena suerte

---

### Post by kornykyano on 2009-05-08
gracias amigo pero no funciona :) Ya tengo Java instalado sino no hubiera usado jdownloader, el tema creo que es el Cmap, este me hizo barullo en el directorio de Java

Saludos

---

### Post by Hei Ku on 2009-05-08
Fijate que te tira este comando:

ldd freemind

Despues con eso podemos ver de hacer un enlace simbolico a donde este buscando la biblioteca que no encuentra.

---

### Post by kornykyano on 2009-05-08
Funciono con este :)

```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by kornykyano on 2009-05-08
Gracias Hei Ku ya le encontre la vuelta, pero ya que esta, este comando ```
ldd freemind
``` tira error, para que sirve?

---

### Post by Hei Ku on 2009-05-08
te sirve para verificar las dependencias de un programa, pero tenes que estar en la carpeta del archivo.

man ldd

---

### Post by kornykyano on 2009-05-08
Siempre se aprende algo nuevo aca :)

Gracias

---

