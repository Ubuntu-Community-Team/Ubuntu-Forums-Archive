---
title: "Change Eclipse IDE to use Sun Java jre1.8.0_66 64 bit in Ubuntu Studio 14.04"
date: 2015-12-07
forum: Ubuntu Application Development
---

### Post by sethanath2 on 2015-12-07
Hi,

Last night, I was trying to install Eclipse IDE with the following steps.
[INDENT][/INDENT]
[INDENT]

[LIST=1]
[*]Installed OpenJDK Java 7 from "Ubuntu Software Center".
[*]Eclipse  in "Ubuntu Software Center" is too old. By googling, I found out that I  should download the Eclipse Installer (Release 4.5.1) from  "http://www.eclipse.org/downloads/", which I chose the Linux 64 bit  version.
[*]By extracting the downloaded file, clicked on , I was able to install the software to "/home/erick/eclipse/cpp-mars/".
[/LIST]
[/INDENT]

However, I want to start another fresh install, because it had so much problems. I could not install any Eclipse plugins, afterward. I could see many error messages coming from Java.
I want to make sure that this new Eclipse installation would be using "Sun Java jre1.8.0_66 64 bit", not OpenJDK 7, this time.

I performed the following steps, which I hope someone can guide me further, because I am pretty much guessing at this point.

1. sudo mkdir -p -v /opt/java/64
2. cd /home/erick/Downloads/
3. tar xvzf ~/Downloads/jre-8u66-linux-x64.tar.gz
4. sudo mv -v ~/Downloads/jre1.8.0_66 /opt/java/64
5. sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.8.0_66/bin/java" 1
6. sudo update-alternatives --set java /opt/java/64/jre1.8.0_66/bin/java
7. mkdir -v ~/.mozilla/plugins
8. sudo apt-get remove icedtea-6-plugin && sudo apt-get remove icedtea-7-plugin
9. rm -v ~/.mozilla/plugins/libnpjp2.so
10. ln -s /opt/java/64/jre1.8.0_66/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
11. $ java -version[INDENT]java version "1.8.0_66"
Java(TM) SE Runtime Environment (build 1.8.0_66-b17)
Java HotSpot(TM) 64-Bit Server VM (build 25.66-b17, mixed mode)
[/INDENT]

Please note that I still see the folders "/usr/lib/jvm/java-7-openjdk-amd64/" and "/usr/lib/jvm/java-1.7.0-openjdk-amd64/" left inside the OS. 

Thank you so much.

---

### Post by sethanath2 on 2015-12-07
> **sethanath2 said:**
> Hi,

Last night, I was trying to install Eclipse IDE with the following steps.[INDENT]

[LIST=1]
[*]Installed OpenJDK Java 7 from "Ubuntu Software Center". 
[*]Eclipse  in "Ubuntu Software Center" is too old. By googling, I found out that I  should download the Eclipse Installer (Release 4.5.1) from  "http://www.eclipse.org/downloads/", which I chose the Linux 64 bit  version. 
[*]By extracting the downloaded file, clicked on , I was able to install the software to "/home/erick/eclipse/cpp-mars/". 
[/LIST]
[/INDENT]

However, I want to start another fresh install, because it had so much problems. I could not install any Eclipse plugins, afterward. I could see many error messages coming from Java.
I want to make sure that this new Eclipse installation would be using "Sun Java jre1.8.0_66 64 bit", not OpenJDK 7, this time.

I performed the following steps, which I hope someone can guide me further, because I am pretty much guessing at this point.

1. sudo mkdir -p -v /opt/java/64
2. cd /home/erick/Downloads/
3. tar xvzf ~/Downloads/jre-8u66-linux-x64.tar.gz
4. sudo mv -v ~/Downloads/jre1.8.0_66 /opt/java/64
5. sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.8.0_66/bin/java" 1
6. sudo update-alternatives --set java /opt/java/64/jre1.8.0_66/bin/java
7. mkdir -v ~/.mozilla/plugins
8. sudo apt-get remove icedtea-6-plugin && sudo apt-get remove icedtea-7-plugin
9. rm -v ~/.mozilla/plugins/libnpjp2.so
10. ln -s /opt/java/64/jre1.8.0_66/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
11. $ java -version[INDENT]java version "1.8.0_66"
Java(TM) SE Runtime Environment (build 1.8.0_66-b17)
Java HotSpot(TM) 64-Bit Server VM (build 25.66-b17, mixed mode)
[/INDENT]

Please note that I still see the folders "/usr/lib/jvm/java-7-openjdk-amd64/" and "/usr/lib/jvm/java-1.7.0-openjdk-amd64/" left inside the OS. 

Thank you so much.

I have just downloaded the Eclipse Installer (Release 4.5.1), and have installed the software to "/home/erick/eclipse/cpp-mars/".
I think Eclipse work better now with jre1.8.0_66.
I checked the content of eclipse.ini, and I believe it is now using Sun Java successfully.

Why would I still see the two folders "/usr/lib/jvm/java-7-openjdk-amd64/" and "/usr/lib/jvm/java-1.7.0-openjdk-amd64/" left inside the OS.
Also, I still could not install any software through Help -> Install New Software. I keep getting the same error message.

[INDENT]An error occurred during the org.eclipse.equinox.internal.p2.engine.phases.CheckTrust phase.
session context was:(profile=_home_erick_eclipse_cpp-mars_eclipse, phase=org.eclipse.equinox.internal.p2.engine.phases.CheckTrust, operand=, action=).
Error reading signed content.
zip file is empty
[/INDENT]

I googled and added the flag "-Djava.util.Arrays.useLegacyMergeSort=true" to eclipse.ini file, but the problem does not go away. Here is the content of ini file.[INDENT]
-startup
../../../.p2/pool/plugins/org.eclipse.equinox.launcher_1.3.100.v20150511-1540.jar
--launcher.library
../../../.p2/pool/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.300.v20150602-1417
-product
org.eclipse.epp.package.cpp.product
--launcher.defaultAction
openFile
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
--launcher.defaultAction
openFile
--launcher.appendVmargs
-install
/home/erick/eclipse/cpp-mars/eclipse
-vm
/opt/java/64/jre1.8.0_66/bin
-vmargs
-Djava.util.Arrays.useLegacyMergeSort=true
-Dosgi.requiredJavaVersion=1.7
-XX:MaxPermSize=256m
-Xms256m
-Xmx1024m
-Doomph.update.url=http://download.eclipse.org/oomph/updates/milestone/latest
-Doomph.redirection.index.redirection=index:/->[http://git.eclipse.org/c/oomph/org.eclipse.oomph.git/plain/setups/](http://git.eclipse.org/c/oomph/org.eclipse.oomph.git/plain/setups/)
[/INDENT]

Thanks.

---

### Post by sethanath2 on 2015-12-07
Is there any way I can install "Pkg-config" support without using Help -> Install New Software or Eclipse MarketPlace?
Here is the plugin I need.

[https://marketplace.eclipse.org/content/pkg-config-support-eclipse-cdt](https://marketplace.eclipse.org/content/pkg-config-support-eclipse-cdt)


Thanks.

---

### Post by sethanath2 on 2015-12-08
I also tried launching eclipse as su, but it still did not help.

$ cd /home/erick/eclipse/cpp-mars/eclipse/
$ sudo ./eclipse
   Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=256m; support was removed in 8.0
Help -> Eclipse MarketPlace -> Pkg-config support for Eclipse CDT 1.0.0

---

### Post by sethanath2 on 2015-12-08
> **sethanath2 said:**
> 

Please note that I still see the folders "/usr/lib/jvm/java-7-openjdk-amd64/" and "/usr/lib/jvm/java-1.7.0-openjdk-amd64/" left inside the OS. 

Thank you so much.

As I run the OS update this morning, I found out that I need to run "sudo apt-get autoremove" to remove many Java program, including the two folders above.

Thanks.

---

### Post by sethanath2 on 2015-12-08
Hi,

Someone gave me a great idea. I was installing Eclipse using eclipse-inst-linux64.tar.gz
Now, I have just downloaded eclipse-cpp-mars-1-linux-gtk-x86_64.tar.gz

Its MD5 value on the web is 5f0bf4989075058af670866e952be044 eclipse-cpp-mars-1-linux-gtk-x86_64.tar.gz

Mine is below. The values match, which are good. 
$ md5sum "/home/erick/Downloads/eclipse-cpp-mars-1-linux-gtk-x86_64.tar.gz"
5f0bf4989075058af670866e952be044  /home/erick/Downloads/eclipse-cpp-mars-1-linux-gtk-x86_64.tar.gz

Now, by navigating to Help -> Install New Software, I was able to  install "Web, XML, Java EE and OSGi Enterprise Development" successfully  with no error message.

Here is another problem, however.
By navigating to Help -> Eclipse Marketplace, to install "Pkg-config  support for CDT Eclipse 1.0.0", this plugin would not be installed  successfully. I do not know what the error message is, but it would say  "Cannot perform operation. Computing alternate solutions, " and "Cannot  complete the request.  See the error log for details.".

Can someone help?

---

### Post by sethanath2 on 2015-12-08
> **sethanath2 said:**
> Hi,

Someone gave me a great idea. I was installing Eclipse using eclipse-inst-linux64.tar.gz
Now, I have just downloaded eclipse-cpp-mars-1-linux-gtk-x86_64.tar.gz

Its MD5 value on the web is 5f0bf4989075058af670866e952be044 eclipse-cpp-mars-1-linux-gtk-x86_64.tar.gz

Mine is below. The values match, which are good. 
$ md5sum "/home/erick/Downloads/eclipse-cpp-mars-1-linux-gtk-x86_64.tar.gz"
5f0bf4989075058af670866e952be044  /home/erick/Downloads/eclipse-cpp-mars-1-linux-gtk-x86_64.tar.gz

Now, by navigating to Help -> Install New Software, I was able to  install "Web, XML, Java EE and OSGi Enterprise Development" successfully  with no error message.

Here is another problem, however.
By navigating to Help -> Eclipse Marketplace, to install "Pkg-config  support for CDT Eclipse 1.0.0", this plugin would not be installed  successfully. I do not know what the error message is, but it would say  "Cannot perform operation. Computing alternate solutions, " and "Cannot  complete the request.  See the error log for details.".

Can someone help?

Okay, I have just noticed now that I have  "https://raw.githubusercontent.com/TuononenP/pkg-config.p2/master/site.xml" in my  "Available Software Sites". I also see Pkg-config.

The installation went successful.

---

