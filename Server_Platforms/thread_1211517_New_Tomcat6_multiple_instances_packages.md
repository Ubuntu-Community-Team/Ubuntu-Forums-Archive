---
title: "New Tomcat6 multiple instances packages"
date: 2009-07-12
forum: Server Platforms
---

### Post by voidmain on 2009-07-12
I finally got around to updating my Debian scripts for installing multiple instances of Tomcat on the same box. This time around I decided to go ahead and make some .deb packages and really do things the right way. 

At this point I'm looking for beta testers to help work out the bugs and then I'll be submitting these packages upstream as well as to Ubuntu for consideration. I'll also be creating a repository in the near future to allow them to be installed via apt.

First, let me start by addressing the issues I've battled with on all Linux varieties for years:

[LIST]
[*]No distro correctly package Tomcat. Most of them don't include the same JAR files that the Tomcat bundles you download from Apache do. The most severe issue is the commons-dbcp.jar and commons-pool.jar re-package into tomcat-dbcp.jar.
[*]The package that all Linux distros use is really messy and scatters things all over the file system. Very annoying
[*]Trying to change the installation to allow for multiple instances that all get started using /etc/init.d scripts all with separate CATALINA_HOME and CATALINA_BASE directories is extremely painful
[/LIST]

My object is to allow you to install a base set of packages and then use some super-user scripts to create new instances of Tomcat. Each instance should be completely separate from the others and it should have these things:

[LIST]
[*]Its own CATALINA_HOME so that you can drop jar files specifically for that application and they won't conflict with other applications
[*]Its own CATALINA_BASE, which is the same as the CATALINA_HOME to make life simple
[*]Its own log directory separate from all the others so that log harvesting is simpler
[/LIST]

Okay, on to the good stuff. First, if you want to install these packages, you'll need to use dpkg for now, until I get my repository setup. Grab the packages from here:

[http://www.inversoft.org/libtomcat6-java.deb]("http://www.inversoft.org/libtomcat6-java.deb")

[http://www.inversoft.org/tomcat6-multiple-instances.deb]("http://www.inversoft.org/tomcat6-multiple-instances.deb")

Next, follow these steps to install them from the terminal:

```

$ sudo dpkg -i libtomcat6-java.deb
$ sudo apt-get install -f
$ sudo dpkg -i tomcat6-mulitple-instances.deb
$ sudo apt-get install -f

```

This will install the two packages and all their dependencies. Next, test out the scripts that let you create and remove Tomcat instances. These scripts are executed like this:

```

$ sudo /usr/sbin/tomcat6-new-instance
or
$ sudo /usr/sbin/tomcat6-rm-instance

```

Executing the command will give you information about how they work. After you create the instance, you might have to tweak the Apache2 configuration and the Tomcat configuration for your instance. The directories below will tell you where those files are.

Lastly, there are a few locations that you will want to know about as you beta test:

[LIST]
[*]/usr/share/tomcat6/skel - This is the location that contains the template used to create new instances
[*]/var/lib/tomcat6 - This directory will contain each instance
[*]/var/lib/tomcat6/<domain>/conf/server.xml - This is the Tomcat configuration file for the Tomcat instance for <domain> 
[*]/var/log/tomcat6 - This directory will contain the logs for each instance
[*]/etc/init.d/tomcat6-<domain> - This is the start up script for a single instance whose domain name is <domain>
[*]/etc/apache2/sites-available/<domain> - This is the Apache2 configuration file for the Tomcat instance for <domain>
[*]/etc/libapache2-mod-jk/workers.properties - If you are setting up Mod-JK, the tomcat6-new-instance script will add the Mod-JK settings into this file
[/LIST]

Feel free to comment on this thread with any issues or concerns. Also, email me directly or send me private messages through the forums (I'm assuming this is supported here).

---

### Post by verticaltier on 2009-08-11
Server seems to be down.  Are you still hosting he deb packages?

---

### Post by voidmain on 2009-08-12
Sorry about that. I was switching servers and forgot to update my DNS records. Those should be fixed now and you can grab the files from the URLs above.

---

### Post by born2chill on 2009-10-07
hi all,

as discussed in [bug 207787]("https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/207787") , tomcat5.5 seems to pretty hopeless, so i went to backport tomcat 6.0.20 from original tomcat sources ([http://tomcat.apache.org/download-60.cgi](http://tomcat.apache.org/download-60.cgi)). Reused most of the jaunty tomcat 6.0.18 package as you can see in the changelog ;). Packages have been  tested on the latest 8.04.3 64bit LTS release.

I'm going to re-work the the init mechanism for a server-multi instance script too, still have to discuss with voidman how to do that.

meanwhile anyone interested can grab the goods here:
[http://aegis.dest-unreachable.net/debs/tomcat/](http://aegis.dest-unreachable.net/debs/tomcat/)

dependencies (pretty much the same as tomcat5.5, list them anyways):
- java5 jre+jdk
- libcommons-dbcp-java
- libcommons-pool-java 
- libecj-java 
- jsvc 

br and please report back if/how this is working for you
b2c

PS: any maintainers out there please review the package and point out any obvious errors so i can work on them as I'm pretty new to this stuff...

---

### Post by voidmain on 2009-10-07
It looks like you are building from source and then repackaging the build result. Although this is fine, I would suggest not building from source and using the binary version from Apache.

Java isn't the same as other languages and the original binary releases are going to be best since they will work on any platform with a JDK.  You also don't have to worry about different architectures at all. My primary concern with a source build is the accuracy of your build environment compared to the Tomcat maintainers build environment.

The packages I created are merely a bundling of the binary Tomcat release along with the scripts necessary to create and remove instances and then template for the instances. This is the best approach in my opinion.

---

### Post by born2chill on 2009-10-07
> **voidmain said:**
> It looks like you are building from source and then repackaging the build result. Although this is fine, I would suggest not building from source and using the binary version from Apache.

True, but i needed to start somewhere and was interested in how it is done now. As i have a working build environment now, it shoudn't be too much hassle to adapt it to use binary instead of source based releases.

---

### Post by born2chill on 2009-10-08
update:
 
 - reworked the build process to use the binary tarballs provided by apache-foundation instead of building from source
 - added a 'tomcat6-server' package with scripts to manage multiple instances (works for tomcat5.5 and tomcat6)
 - split the the original bin-tarball the same way as the standard installation
 
 tested on 8.04 LTS
 
 download:
 [http://aegis.dest-unreachable.net/debs/tomcat-bin/](http://aegis.dest-unreachable.net/debs/tomcat-bin/)
 
info:
[http://wiki.dest-unreachable.net/display/DPKG/Tomcat-6+Ubuntu+LTS+Package](http://wiki.dest-unreachable.net/display/DPKG/Tomcat-6+Ubuntu+LTS+Package)

 enjoy and please report back!

---

### Post by voidmain on 2009-11-04
I finally managed to get some time to setup the open source project to manage the scripts and package creation. The project is hosted over at Google Code and the project page is:

  [http://code.google.com/p/tomcat-linux/]("http://code.google.com/p/tomcat-linux/")

Anyone that is interested should check the project out and grab everything out of SubVersion. Assistance with making the scripts better and tuning the process and setup is much appreciated.

---

### Post by mdeneen on 2010-01-20
> **voidmain said:**
> I finally managed to get some time to setup the open source project to manage the scripts and package creation. The project is hosted over at Google Code and the project page is:

  [http://code.google.com/p/tomcat-linux/](http://code.google.com/p/tomcat-linux/)

Anyone that is interested should check the project out and grab everything out of SubVersion. Assistance with making the scripts better and tuning the process and setup is much appreciated.

Where does this stand today?  I didn't see any files / packages released here.

---

### Post by voidmain on 2010-01-20
> **mdeneen said:**
> Where does this stand today?  I didn't see any files / packages released here.

The project doesn't have any files released yet. Currently, everything is in SubVersion and if you check it out, you'll be presented with a couple of scripts. These scripts can be used to create the Debian packages for tomcat and the tomcat libraries.

I have it setup this way because this will make it much simpler to rebuild this package for other versions of Debian or other operating systems.

I'd like feedback on the scripts that are part of the package. These scripts are used to create and remove Tomcat instances from the server and right now they don't have many options. I know that some other people who have written similar packages have created scripts that take numerous options to really let you control the configuration of the tomcat instances you are creating. My scripts are much simpler and you can still tweak the configuration after using them.

Once things are looking good overall, I'll roll new packages for Ubuntu and other distros and add them to the project.

---

### Post by mdeneen on 2010-01-20
> **voidmain said:**
> The project doesn't have any files released yet. Currently, everything is in SubVersion and if you check it out, you'll be presented with a couple of scripts. These scripts can be used to create the Debian packages for tomcat and the tomcat libraries.

I have it setup this way because this will make it much simpler to rebuild this package for other versions of Debian or other operating systems.

I'd like feedback on the scripts that are part of the package. These scripts are used to create and remove Tomcat instances from the server and right now they don't have many options. I know that some other people who have written similar packages have created scripts that take numerous options to really let you control the configuration of the tomcat instances you are creating. My scripts are much simpler and you can still tweak the configuration after using them.

Once things are looking good overall, I'll roll new packages for Ubuntu and other distros and add them to the project.

I gave it a shot on Ubuntu Server 9.10.  It installed fine, but something is missing.

/var/lib/tomca6/$HOST/lib/catalina.jar is a broken symbolic link to /usr/share/java/catalina.jar.  There are others like this as well.  Any idea what went wrong?

/usr/share/java/catalina.jar exists.  It is a broken symlink to "libtomcat6-java/usr/share/java/catalina-6.0.20.jar".

The script created the symlinks this way -- looking further

```


Index: build-dpkg.sh
===================================================================
--- build-dpkg.sh       (revision 7)
+++ build-dpkg.sh       (working copy)
@@ -80,7 +80,9 @@
 cp apache-tomcat-$VERSION/lib/*.jar libtomcat6-java/usr/share/java
 for f in $(ls libtomcat6-java/usr/share/java); do
   mv libtomcat6-java/usr/share/java/$f libtomcat6-java/usr/share/java/${f%%.jar}-$VERSION.jar
-  ln -s libtomcat6-java/usr/share/java/${f%%.jar}-$VERSION.jar libtomcat6-java/usr/share/java/$f
+  pushd libtomcat6-java/usr/share/java > /dev/null
+  ln -s ${f%%.jar}-$VERSION.jar $f
+  popd > /dev/null
 done


```

This is somewhat crude, but it gets the job done.

---

### Post by voidmain on 2010-01-20
Yeah, I think I had a similar fix for the symlinks and I lost my hard drive yesterday and had to re-install everything. Therefore, my fix is probably lost.

I think your diff should work fine. I'll commit it now.

---

### Post by Styles on 2010-02-09
Very, very, interested in this! Being that I'm an over worked sys admin ;) So do you have a svn or git repo up? If so what's the scoop? I also did not want to try the the debs in your first post as they look a bit stale July 2009.

Also on a side note: Ubuntu system startup script doesn't seem to follow the normal tomcat6 startup procedure. /etc/init.d/tomcat6 runs /usr/bin/jsvc instead of executing the normal startup scripts in /usr/share/tomcat6/bin

Are you going to be sticking to the same convention? Using jsvc? In my humble opinion it causes more issues than not, what's your take on it?

Thanks for your time,
Eric

---

### Post by voidmain on 2010-02-09
> **Styles said:**
> 
Also on a side note: Ubuntu system startup script doesn't seem to follow the normal tomcat6 startup procedure. /etc/init.d/tomcat6 runs /usr/bin/jsvc instead of executing the normal startup scripts in /usr/share/tomcat6/bin

Are you going to be sticking to the same convention? Using jsvc? In my humble opinion it causes more issues than not, what's your take on it?


I have just been working on the init scripts for a separate project. The issue I ran into was that I did not want to run Tomcat as the root user. Therefore, I needed a way to run everything as a different user while still be able to capture the PID of the Tomcat process.

What I ended up doing was using sudo to execute Java as a different user. Sudo is the only way to get access to the PID easily. I tried using su, but it doesn't work the same way because it forks off a separate shell to run the commands. This makes su even more painful if the user you want to run Tomcat as doesn't have a shell account (i.e. their shell is /bin/false).

The way that Tomcat suggests running things is to use JSVC because it provides two benefits over the Tomcat scripts:

[LIST]
[*]Run Tomcat as a user other than root
[*]Restart Tomcat if it crashes
[/LIST]

I'm open to other suggestions because I roll packages for CentOS and their repositories lack JSVC forcing me to manage that package as well, which is annoying. If you have other ideas of supporting the two items above or at a minimum the first one, let me know.

Also, everything is open sourced and available here:

  [http://code.google.com/p/tomcat-linux/]("http://code.google.com/p/tomcat-linux/")

You can check out the current code from SubVersion and it contains a script that will roll new DEBs for you. Let me know if you have questions or suggestions about the init scripts or other scripts I've created.

---

