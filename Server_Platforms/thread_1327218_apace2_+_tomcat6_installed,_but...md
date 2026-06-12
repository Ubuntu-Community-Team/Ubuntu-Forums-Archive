---
title: "apace2 + tomcat6 installed, but.."
date: 2009-11-15
forum: Server Platforms
---

### Post by DeaD SouL on 2009-11-15
hello guys

i installed apache2, mysql, php5, phpmyadmin, ssl, tomcat6

and they are working just fine..

i didn't need tomcat6 till now because i have to install php/java bridge

aw, i downloaded "php-java-bridge_5.4.4.2-3_i386.deb" and succeed to install it

then i checked phpinfo()

> java
java support 	Enabled
java bridge 	5.4.4.2

so, i believe it should work fine now..

but i can't use php/java bridge :( and i don't know why
can anyone tell me how should i test it?

* tomcat6 doesn't run any page but html & jsp, it doesn't execute php files

and tomcat6 uses port 8080 next to server name (localhost:8080)
how can i hide the port, or mix it with appache2 www folder?
tried /etc/tomcat6/server.xml but didn't work


i'm a php programmer and working on an e-commerce project
my job is done, now i have to install the jsp plugin the bank just gave me to my php script otherwise i'll face a big problem with them :(
besides i do have a deadline :(

i know its not your problem.. but please guys help me out 

thanks

---

### Post by wojox on 2009-11-15
Have you checked out their site [php-java-bridge]("http://php-java-bridge.sourceforge.net/pjb/index.php")

---

### Post by DeaD SouL on 2009-11-15
yes i did

but when i try this
```
java -classpath JavaBridge.war
```

i get
> Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image


and about this step
> Browse to [http://localhost:8080/JavaBridge](http://localhost:8080/JavaBridge) and run the PHP and JSP examples. 
which is mentioned in [Installation Guides]("http://php-java-bridge.sourceforge.net/pjb/installation.php")

i can't execute the php files on tomcat6 which are stored in /var/lib/tomcat6/webapps/ROOT/

i can only run php files on apache2 default folder which is on /var/www/

thanks for trying :)

---

### Post by peter_jones_jr on 2009-11-17
Seems like your command is wrong.

Please take a look at the URL mentioned above again and make sure that you type in the commands correctly.

---

