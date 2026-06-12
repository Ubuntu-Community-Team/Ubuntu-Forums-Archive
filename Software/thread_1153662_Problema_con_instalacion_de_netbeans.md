---
title: "Problema con instalacion de netbeans"
date: 2009-05-09
forum: Software
---

### Post by Just64 on 2009-05-09
Quiero intalar el netbeans IDE c/c++ y tengo este problema:

```
pato@pato-laptop:~/Escritorio$ sudo sh netbeans-6.5.1-ml-cpp-linux.sh
[sudo] password for pato: 
Configuring the installer...
Searching for JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 6 or JDK 5 is required for installing the NetBeans IDE. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.

To download the JDK, visit http://java.sun.com/javase/downloads

```

Pero el JDK 6 ya lo tengo instalado y registrado:

```
Java(TM) SE Development Kit 6 successfully installed.

Product Registration is FREE and includes many benefits:
* Notification of new versions, patches, and updates
* Special offers on Sun products, services and training
* Access to early releases and documentation

Product and system data will be collected. If your configuration
supports a browser, the Sun Product Registration form for 
the JDK will be presented. If you do not register, none of
this information will be saved. You may also register your
JDK later by opening the register.html file (located in 
the JDK installation directory) in a browser.

For more information on what data Registration collects and 
how it is managed and used, see:
http://java.sun.com/javase/registration/JDKRegistrationPrivacy.html

Press Enter to continue.....

```

Lo raro es q en la instalacion la carpeta de JDK se me crea en el escritorio...

---

### Post by Hei Ku on 2009-05-09
Probaste correr el instalador con la opcion --javahome, como dice ahi?

Otra cosa, tenes seleccionado el java de Sun en update-java-alternatives?

---

