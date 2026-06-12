---
title: "Edgy &amp; Tomcat 5.5 from repository: JSP jasper error"
date: 2006-11-17
forum: Server Platforms
---

### Post by Robvdl on 2006-11-17
Hi, I'm setting up Ubuntu Edgy Server with Tomcat 5.5 from the universe repositories. I haven't found any examples on the net on how to do this from the actual repositories in Edgy, as most examples seem to install Tomcat 5.5 manually as downloaded from the Apache Tomcat website. But I figured... if Tomcat 5.5 is actually in the repositories, it's ought to work... so why not try to use these instead.

Well, I have successfully installed Tomcat 5.5 using the following steps:

First Java:

```
sudo apt-get install sun-java5-bin sun-java5-fonts
```

And the JDK:

```
sudo apt-get install sun-java5-demo sun-java5-jdk sun-java5-source
```

In Ubuntu Edgy, you don't need to run the update alternatives command like you used to have to do in Dapper, as java and javac already point to the correct programs. There is no other java on the system from what I know, so let's move on and install Tomcat 5.5 from the repositories:

```
sudo apt-get install tomcat5.5 tomcat5.5-admin tomcat5.5-webapps
```

Next, I edited the config file:

```
sudo nano /etc/default/tomcat5.5
```

I uncommented, and changed JAVA_HOME to:

```
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
```

I saved this file, then edited the users file:

```
sudo nano /var/lib/tomcat5.5/conf/tomcat-users.xml
```

I changed the tomcat user to:

```
<user username="tomcat" password="my_pass" roles="tomcat,admin,manager"/>
```

I saved the users file and started up Tomcat:

```
sudo /etc/init.d/tomcat5.5 start
```

Ok, started up fine, now move onto my main machine and test it using [http://192.168.0.1:8180/](http://192.168.0.1:8180/)

All good, Tomcat Manager working, Tomcat status working, Servlet examples working... But JSP samples come up with an error, anything JSP seems to come up with an error, here's what I get:

```

HTTP Status 500 -

type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

org.apache.jasper.JasperException: org.apache.jasper.tagplugins.jstl.If
	org.apache.jasper.servlet.JspServletWrapper.handleJspException(JspServletWrapper.java:510)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:375)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:275)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

root cause

org.apache.jasper.JasperException: org.apache.jasper.tagplugins.jstl.If
	org.apache.jasper.compiler.TagPluginManager.init(TagPluginManager.java:109)
	org.apache.jasper.compiler.TagPluginManager.apply(TagPluginManager.java:51)
	org.apache.jasper.compiler.Compiler.generateJava(Compiler.java:189)
	org.apache.jasper.compiler.Compiler.compile(Compiler.java:295)
	org.apache.jasper.compiler.Compiler.compile(Compiler.java:276)
	org.apache.jasper.compiler.Compiler.compile(Compiler.java:264)
	org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:563)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:303)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:275)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

root cause

java.lang.ClassNotFoundException: org.apache.jasper.tagplugins.jstl.If
	java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	java.security.AccessController.doPrivileged(Native Method)
	java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	java.lang.Class.forName0(Native Method)
	java.lang.Class.forName(Class.java:164)
	org.apache.jasper.compiler.TagPluginManager.init(TagPluginManager.java:106)
	org.apache.jasper.compiler.TagPluginManager.apply(TagPluginManager.java:51)
	org.apache.jasper.compiler.Compiler.generateJava(Compiler.java:189)
	org.apache.jasper.compiler.Compiler.compile(Compiler.java:295)
	org.apache.jasper.compiler.Compiler.compile(Compiler.java:276)
	org.apache.jasper.compiler.Compiler.compile(Compiler.java:264)
	org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:563)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:303)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:275)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

note The full stack trace of the root cause is available in the Apache Tomcat/5.5 logs.
Apache Tomcat/5.5

```

I had a look around on the net, but nothing really seems to point me to the right direction - I can't find enough information about Tomcat on Edgy. I would prefer to keep the Tomcat 5.5 installed from the repositories and not install it manually, I would rather resolve getting the ones from the repositories going. It appears I am very close to getting it going 100% as it's only JSP that seems to be the problem now - Servlets are fine.

Any hints, it appears I have hit a brick wall ](*,)

---

### Post by Robvdl on 2006-11-18
I have found out that this is because of a bug in Debian (#393905), apparently it is already fixed in Debian with Tomcat 5.5.20-1, but not yet in Edgy.

[https://launchpad.net/distros/ubuntu/+source/tomcat5.5/+bug/69043](https://launchpad.net/distros/ubuntu/+source/tomcat5.5/+bug/69043)

In other words, looks like a manual install is required for now to get Tomcat 5.5 going in Edgy, but let's hope it gets fixed for Feisty :-)

---

### Post by Robvdl on 2006-11-19
If anyone has been reading this, I have successfully been able to install Tomcat 5.5.20-1 from Debian unstable instead, using:

```
sudo dpkg -i libtomcat5.5-java_5.5.20-1_all.deb tomcat5.5_5.5.20-1_all.deb tomcat5.5-admin_5.5.20-1_all.deb tomcat5.5-webapps_5.5.20-1_all.deb
```

---

### Post by Robvdl on 2006-11-21
I am writing this reply, because I got a pm regarding this installation method. I experienced the same myself later on actually, so here's the fix...

If you try to install the Debian unstable packages with the dpkg command in my previous message, for some reason it will not get the other dependencies with it from the Ubuntu repositories. I found that I had to install these dependencies first:

```

sudo apt-get install ant libcommons-collections3-java libcommons-dbcp-java libcommons-el-java libcommons-launcher-java libcommons-logging-java libcommons-modeler-java libcommons-pool-java libmx4j-java libservlet2.4-java libxerces2-java adduser apache2-utils ecj-bootstrap java-gcj-compat-dev libcommons-beanutils-java libstruts1.2-java

```

Then run the following command to install the Tomcat debs from Debian unstable:

```
sudo dpkg -i libtomcat5.5-java_5.5.20-1_all.deb tomcat5.5_5.5.20-1_all.deb tomcat5.5-admin_5.5.20-1_all.deb tomcat5.5-webapps_5.5.20-1_all.deb
```

That way it should work.

Anyway, if you had already typed the dpkg command to install the Debian unstable packages, without getting these dependencies first, you will need to fix the broken packages error first. I recall it showed me on screen how to fix the broken packages, unfortunately I cannot remember what I typed to fix the broken packages and it's not in my bash history, but it can definitely be fixed as I did it at the time. After fixing the broken packages, I manually installed the dependencies, then installed the Debian version of Tomcat, this time without any errors.

I did however have to run update alternatives this time to select the Sun java and javac as it was set to the open source one:

```

sudo update-alternatives --config java
sudo update-alternatives --config javac
```

Hope this helps.

---

### Post by BobFleischman on 2006-11-26
Maybe this is the wrond place to ask, but how do I get the 5.5.20 deb packages from unstable using Ubuntu.

I've spent the afternoon searching the web but no clear instructions. Currently when running your dpkg command I get 'No such file or directory'

Thanks for writing up what you found on this error.

---

### Post by ernie_coats on 2006-11-27
Here you go Bob.

[http://debian.mirror.frontiernet.net/debian/pool/main/t/tomcat5.5/](http://debian.mirror.frontiernet.net/debian/pool/main/t/tomcat5.5/)

---

### Post by houdain on 2006-12-04
Hi, 

I've followed your explanations but I still get the same error "jasper".

But it seems that when I install tomcat 5.5 with dpkg -i, it returns an error during the configuration. Any ideas ?

---

### Post by BobFleischman on 2006-12-04
I just downloaded the .deb files from the link that Ernie provided and then installed them without any problem.

What error are you getting?

---

### Post by xboxer21 on 2006-12-05
Hello All,
I tried the above mentioned instructions. The installation went without a problem. however when i try to access [http://localhost:8180/](http://localhost:8180/) I get a blank page with the tomcat favicon displayed in the address bar. any help would be appreciated.

Thanks

---

### Post by BobFleischman on 2006-12-05
Did you also install the admin and webapp debs? Without these Tomcat is just an engine waiting to do something.

---

### Post by xboxer21 on 2006-12-05
> **BobFleischman said:**
> Did you also install the admin and webapp debs? Without these Tomcat is just an engine waiting to do something.

BobFleischman,
I did install the webapps as well as admin packages.

---

### Post by lurch on 2006-12-06
Hi,

after reading some of the Bug reports ([msg252754]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg252754.html") and [msg00038]("http://lists.debian.org/debian-java/2006/06/msg00038.html")), there seems to be a simple manual fix for the original problem with the JSP example pages. 
To get the examples running, simple install the edgy packages as described in the first message of this thread and edit:

```
/var/lib/tomcat5.5/webapps/jsp-examples/WEB-INF/tagPlugins.xml
```

The file should contain:

```
<tag-plugins>
 <tag-plugin>
    <tag-class>org.apache.taglibs.standard.tag.rt.core.IfTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.If</plugin-class>
  </tag-plugin>
  <tag-plugin>
   <tag-class>org.apache.taglibs.standard.tag.common.core.ChooseTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.Choose</plugin-class>
  </tag-plugin>
  <tag-plugin>
    <tag-class>org.apache.taglibs.standard.tag.rt.core.WhenTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.When</plugin-class>
  </tag-plugin>
  <tag-plugin>
    <tag-class>org.apache.taglibs.standard.tag.common.core.OtherwiseTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.Otherwise</plugin-class>
  </tag-plugin>
  <tag-plugin>
    <tag-class>org.apache.taglibs.standard.tag.rt.core.ForEachTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.ForEach</plugin-class>
  </tag-plugin>
</tag-plugins>

```

Only the content of the *plugin-class* tags changed because the classes moved to another package. All classes of *org.apache.jasper.tagplugins.jstl* are now located in *org.apache.jasper.tagplugins.jstl.core*, which caused the ClassCastException because the refactoring was not reflected by the tagPlugins.xml in the edgy package.

As for me, this solved the problem and everything seems to run fine, including the JSP examples.

cheers

---

### Post by xboxer21 on 2006-12-06
lurch,
thanks for posting the solution. I uninstalled tomcat, and downlaoded the binary from the apache tomcat website and manually installed it. Everything is working fine now.

Thanks again.

---

### Post by huggy77 on 2006-12-07
i followed these step by step and had no problems... cannot run the examples though... i was able to run admin and manager..

---

### Post by huggy77 on 2006-12-07
try tek-tips if we cant help you... this is probally more a tomcat issue than a linux issue... i dont know any other good java boards....

---

### Post by bonustracks on 2007-01-18
> **lurch said:**
> Hi,

after reading some of the Bug reports ([msg252754]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg252754.html") and [msg00038]("http://lists.debian.org/debian-java/2006/06/msg00038.html")), there seems to be a simple manual fix for the original problem with the JSP example pages. 
To get the examples running, simple install the edgy packages as described in the first message of this thread and edit:

```
/var/lib/tomcat5.5/webapps/jsp-examples/WEB-INF/tagPlugins.xml
```

The file should contain:

```
<tag-plugins>
 <tag-plugin>
    <tag-class>org.apache.taglibs.standard.tag.rt.core.IfTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.If</plugin-class>
  </tag-plugin>
  <tag-plugin>
   <tag-class>org.apache.taglibs.standard.tag.common.core.ChooseTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.Choose</plugin-class>
  </tag-plugin>
  <tag-plugin>
    <tag-class>org.apache.taglibs.standard.tag.rt.core.WhenTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.When</plugin-class>
  </tag-plugin>
  <tag-plugin>
    <tag-class>org.apache.taglibs.standard.tag.common.core.OtherwiseTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.Otherwise</plugin-class>
  </tag-plugin>
  <tag-plugin>
    <tag-class>org.apache.taglibs.standard.tag.rt.core.ForEachTag</tag-class>
    <plugin-class>org.apache.jasper.tagplugins.jstl.core.ForEach</plugin-class>
  </tag-plugin>
</tag-plugins>

```

Only the content of the *plugin-class* tags changed because the classes moved to another package. All classes of *org.apache.jasper.tagplugins.jstl* are now located in *org.apache.jasper.tagplugins.jstl.core*, which caused the ClassCastException because the refactoring was not reflected by the tagPlugins.xml in the edgy package.

As for me, this solved the problem and everything seems to run fine, including the JSP examples.

cheers

Works perfectly now.  Thanks.

---

### Post by trat02community on 2007-02-05
It worked for me too. Tnx a lot :guitar:

---

