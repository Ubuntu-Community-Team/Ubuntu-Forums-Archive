---
title: "Problem using apache / tomcat / axis to deploy webservices."
date: 2006-08-01
forum: Server Platforms
---

### Post by mike_bioinf on 2006-08-01
Hi,

I'm attempting to deploy webservices using the apache / tomcat / axis trio. I installed tomcat using the [this]("http://blixtra.org/blog/category/tech/linux/ubuntu/") guide which was excellent, and very easy. Both apache and tomcat work.

I then downloaded axis and copied the required folder to the webapps folder in tomcat as per the instructions. However when I go to the [http://XXX.XXX.XXX.XXX:8080/axis/](http://XXX.XXX.XXX.XXX:8080/axis/) I am informed that the requested resouce is not available.

I'm not sure what the problem is, I tried restarting tomcat but still no luck.

I'm trying run a small server box under my desk to run java based SOAP webservices to take the strain off my laptop. I am very much a beginner when it comes to this, so I'm not adverse to a simpler/better solution to the one I'm currently using if anyone has any suggestions.

Any help from the ubuntu community would be greatfully received.

Mike

---

### Post by Renne on 2006-10-11
I've done the same and haven't succeeded either. Have you had luck since posting your message, or can someone else provide any clue?

I installed Tomcat 5.0 (via package manager) and then have tried both Axis 1.4 and Axis2 1.0. Concentrating on Axis 1.4, this is what appears in catalina

-----
INFO: Installing web application at context path /axis from URL file:/var/lib/tomcat5/webapps/axis
11/10/2006 11:37:37 org.apache.catalina.core.StandardContext listenerStart
SEVERE: Skipped installing application listeners due to previous error(s)
11/10/2006 11:37:37 org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
11/10/2006 11:37:37 org.apache.catalina.core.StandardContext start
SEVERE: Context startup failed due to previous errors
-----

All the JSP examples work correctly, but not Axis. I've previously run several versions of Axis  on several Tomcat 4.1 configurations (not on Ubuntu), always successfully, but I can't seem to figure out what's going on with this.

---

### Post by mike_bioinf on 2006-10-11
I eventually gave up after having no success.

I tried a few different things but didn't get any further.
I wish I could tell you what else I did at the time but It was a while ago now so I can't really remember.

Someone suggested to me using [xfire]("http://xfire.codehaus.org/") as an alternative. I don't think it's in the repositories but it might be worth taking a look at if you're not getting any further with axis.

Hope this helps.

---

### Post by jessecollins on 2006-10-11
I am suffering all the same problems with the Tomcat/Axis combo.  I have tried Tomcat 4 & Tomcat 5 with no luck for both(although I was receiving different errors :mad: ).  

I read on Apache's WS Wiki that it is suggested to not use Tomcat 5 with Axis.  (Look at the bottom)  [http://wiki.apache.org/ws/FrontPage/Axis/Install/Tomcat](http://wiki.apache.org/ws/FrontPage/Axis/Install/Tomcat)

Has anyone successfully deployed Tomcat & Axis?  If so, what versions of Tomcat and Axis were you using?

](*,)

---

### Post by Renne on 2006-10-11
That info is from 2004 - currently both Tomcat 5.0 and 5.5 are stable releases. I'm sure Axis should be quite okay with those.

Having spent hours so far on this... I think it first of all isn't Ubuntu-related, but more so a classloading problem, having something to do with commons-discovery package (in my case anyway). See Tomcat logs for clues. I'm getting a java.lang.ExceptionInInitializerError while Tomcat is initializing commons-discovery stuff, and this is caused by a java.security.AccessControlException.

No idea yet how to fix this, however... :-k

EDIT: Trying Tomcat 5.5 is of course an option, but since only the 5.0 is available in repositories (if I'm correct), how convenient would it be to stay up-to-date with security updates and such? :?:

---

### Post by jessecollins on 2006-10-11
> **Renne said:**
> That info is from 2004 - currently both Tomcat 5.0 and 5.5 are stable releases. I'm sure Axis should be quite okay with those.

Having spent hours so far on this... I think it first of all isn't Ubuntu-related, but more so a classloading problem, having something to do with commons-discovery package (in my case anyway). See Tomcat logs for clues. I'm getting a java.lang.ExceptionInInitializerError while Tomcat is initializing commons-discovery stuff, and this is caused by a java.security.AccessControlException.

No idea yet how to fix this, however... :-k

EDIT: Trying Tomcat 5.5 is of course an option, but since only the 5.0 is available in repositories (if I'm correct), how convenient would it be to stay up-to-date with security updates and such? :?:

Yep, it would be nice to stay up-to-date with the security updates.  That was one of the reasons I didn't want to rollback to Tomcat 4 in the first place.  I will go ahead and re-install Tomcat 5.  Thank you.

Have you looked into Axis2 ([http://ws.apache.org/axis2/index.html](http://ws.apache.org/axis2/index.html))?

Thank you for your help.  :D

EDIT: Renne, I just noticed that in an earlier post you mentioned using Axis2.  Sorry about that.  Are you focusing on Axis 1.x?

---

### Post by Renne on 2006-10-11
> **jessecollins said:**
> Have you looked into Axis2 ([http://ws.apache.org/axis2/index.html](http://ws.apache.org/axis2/index.html))?

EDIT: Renne, I just noticed that in an earlier post you mentioned using Axis2.  Sorry about that.  Are you focusing on Axis 1.x?

I would like to try Axis2, but it's giving me errors during Tomcat startup as well (in the logs):
StandardContext[/axis2]Servlet /axis2 threw load() exception
javax.servlet.ServletException

So I'm trying to get Axis 1.4 working first, since that I've used before. And who knows, the underlying cause might be the same.

---

### Post by jessecollins on 2006-10-11
> **Renne said:**
> I would like to try Axis2, but it's giving me errors during Tomcat startup as well (in the logs):
StandardContext[/axis2]Servlet /axis2 threw load() exception
javax.servlet.ServletException

So I'm trying to get Axis 1.4 working first, since that I've used before. And who knows, the underlying cause might be the same.

I am going to take a stab at Axis2 tonight just because I have tried Tomcat 4 & 5 with Axis 1.x.  It might be a late one :confused: .  I will post the outcome when I get done.  Thanks again.

---

### Post by Renne on 2006-10-12
Solved! :D Both Axis and Axis2 now work happily. In the end it wasn't a classloading problem, and in fact *is* Ubuntu-related.

Took way too long, but I finally found out that the Ubuntu (and Debian, generally) releases of Tomcat are shipped with Tomcat's Security Manager set on by default. This means that anything which is not specifically permitted to run on Tomcat, will not run.

Two approaches: either set TOMCAT5_SECURITY=no in /etc/default/tomcat5 (not recommended in production environments), or grant the needed permissions in policy files.

Stuff to read:
[http://jspwiki.org/wiki/BugFailsToLoadOnUbuntuDapperInstall](http://jspwiki.org/wiki/BugFailsToLoadOnUbuntuDapperInstall)
[http://tomcat.apache.org/tomcat-5.0-doc/security-manager-howto.html](http://tomcat.apache.org/tomcat-5.0-doc/security-manager-howto.html)

I hope this solves your problem too. This should really be in the [Tomcat install wiki]("https://help.ubuntu.com/community/ApacheTomcat5") and I think even in the [Server Guide]("https://help.ubuntu.com/ubuntu/serverguide/C/index.html").

---

### Post by jessecollins on 2006-10-12
Awesome!  Thank you so much for figuring this out Renne.

So, here are the exact steps in case anyone else has the same problem.  These steps are for Tomcat 5 and Apache Axis2.

1) First we want to check and make sure the problem is a policy problem.  Edit the file [/etc/default/tomcat5]("file://etc/default/tomcat5").
Change...
```
# Use the Java security manager? (yes/no, default: yes)
#TOMCAT5_SECURITY=yes
```
To...
```
# Use the Java security manager? (yes/no, default: yes)
TOMCAT5_SECURITY=no
```

2) Restart

3) Go to... [http://localhost:8180/axis2/](http://localhost:8180/axis2/)
If you are able to view the welcome screen, it is a policy problem.

4) Go back and edit [/etc/default/tomcat5]("file://etc/default/tomcat5").
Change...
```
# Use the Java security manager? (yes/no, default: yes)
TOMCAT5_SECURITY=no
```
Back to...
```
# Use the Java security manager? (yes/no, default: yes)
#TOMCAT5_SECURITY=yes
```

5) Create a new file in the directory [/etc/tomcat5/policy.d]("file://etc/tomcat5/policy.d") to contain the policy permissions.  I created a file named APACHE_AXIS.policy, but it doesn't matter.  All the files in this directory get added to the file [/usr/share/tomcat5/conf/catalina.policy]("file://usr/share/tomcat5/conf/catalina.policy")

6) In the file you just created add...
```
// permissons for apache axis2
grant codeBase "file:${catalina.home}/webapps/axis2/-" {
  permission java.security.AllPermission;
};
```

7) Restart, things should be working now.  :)

If anyone notices that something is wrong please let me know.  Again, all credit goes to Renne.

---

### Post by invalid on 2006-12-15
Thanks so much for this!
I was working for hours to figure this out, and now I know the reason!

---

### Post by lamadredelsapo on 2007-02-20
I installed Axis 1.4 following the included installation guide and everything looks to be working except when it comes to testing the "samples.stock.GetQuote".

Even though I've set up the CLASSPATH and AXISCLASSPATH in my .bashrc file i always get the following error when I run "java samples.stock.GetQuote -lhttp://localhost:8180/axis/servlet/AxisServlet -uuser1 -wpass1 XXX"

```
Exception in thread "main" java.lang.NoClassDefFoundError: samples/stock/GetQuote
```

My CLASSPATH contains the following:
```
echo $CLASSPATH
/usr/share/tomcat5/common/lib/jsp-api.jar:/usr/share/tomcat5/common/lib/servlet-api.jar:/opt/axis/lib/axis.jar:/opt/axis/lib/commons-discovery-0.2.jar:/opt/axis/lib/commons-logging-1.0.4.jar:/opt/axis/lib/jaxrpc.jar:/opt/axis/lib/saaj.jar:/opt/axis/lib/log4j-1.2.8.jar:/opt/axis/lib/activation.jar:/opt/axis/lib/mail.jar:/opt/axis/lib/xmlsec-1.4.0.jar:/opt/axis/lib/wsdl4j-1.5.1.jar
```

I've googled quite a lot but found nothing useful on this topic, so if anyone had this problem i would appreciate some wee help ;)

---

### Post by Renne on 2007-02-20
Your classpath seemingly has what Axis needs, but I don't see it including the actual samples you're trying to run.

---

### Post by lamadredelsapo on 2007-02-22
Oh! I forgot to try that. I'll try it and post results.

---

### Post by lamadredelsapo on 2007-02-23
Thanks for the tip. It was exactly what you said.

---

### Post by Maulwuff on 2008-01-06
wow, that saved me lots of time!
With TOMCAT5_SECURITY=no in /etc/default/tomcat5.5 
the validate link from [http://localhost:8180/axis2](http://localhost:8180/axis2) does finally work! :)

---

### Post by vealshanks on 2008-02-17
I'm having similar permission problems.  I added the "AllPermission" line for axis2 to the policy file, but I'm still getting a read permission problem:

[FONT="Courier New"][INDENT][ERROR] Servlet /axis2 threw load() exception java.security.AccessControlException: access denied (java.io.FilePermission /var/lib/tomcat5.5/webapps/axis2/WEB-INF/scriptServices read)
[/INDENT][/FONT]

When I disable the Security Manager([FONT="Courier New"]TOMCAT5_SECURITY=no[/FONT]), Axis2 works fine.

Any other suggestions on how to get it deployed with the Security Manager?

Any help appreciated.

---

### Post by kay-man on 2008-04-10
Hi,

I had the same problem trying to configure tomcat 5.5 with axis2. I've done some research to figure out exactly what Axis2 needs. I've attached a new policy file I created. This goes, without the .txt extension obviously, into /etc/tomcat5.5/policy.d.

As you can see, there's a whole bunch of permissions granted to the axis2 codebase, but also 2 permissions without any codebase. I haven't figured out what the codebase should be, maybe I will later.

You'll need to put in either your own hostname, or localhost. Also depending on your local classpath, you may need to add more lines such as the last one. But at least this should get you off to a good start.

Anyway, this enables me to run tomcat with a security manager without having to grant the AllPermission to axis.

Cheers,

Paul

---

### Post by sandeep_khurana on 2008-04-16
> **paulklos said:**
> Hi,

I had the same problem trying to configure tomcat 5.5 with axis2. I've done some research to figure out exactly what Axis2 needs. I've attached a new policy file I created. This goes, without the .txt extension obviously, into /etc/tomcat5.5/policy.d.

As you can see, there's a whole bunch of permissions granted to the axis2 codebase, but also 2 permissions without any codebase. I haven't figured out what the codebase should be, maybe I will later.

You'll need to put in either your own hostname, or localhost. Also depending on your local classpath, you may need to add more lines such as the last one. But at least this should get you off to a good start.

Anyway, this enables me to run tomcat with a security manager without having to grant the AllPermission to axis.

Cheers,

Paul

I too had the same problem when i didnt give permission java.security.AllPermission; in the grant block.

But when I tried gving the axis permissions as given in your attached file then also i was not able to run my web service. it is still giving me  scriptServices read exception. i havent used any such special class so that i need to grant permissions, then why is the webservice throwing exceptions...

Please help.....

---

### Post by kay-man on 2008-04-17
Could you post the relevant policy section, i.e. for axis as well as the error you're getting in the tomcat log?

I had to add these 2 lines, without codebase to get it to work. I still haven't figured out why this is.

grant {
    // For some mysterious reason these 2 are required outside the Axis-specific permissions
    // No idea what the codebase should be
    permission java.io.FilePermission "${catalina.base}/webapps/axis2/WEB-INF/-", "read";
    permission java.lang.RuntimePermission "getClassLoader";
};

The first line takes care of the scriptServices error, at least for me it does...

---

