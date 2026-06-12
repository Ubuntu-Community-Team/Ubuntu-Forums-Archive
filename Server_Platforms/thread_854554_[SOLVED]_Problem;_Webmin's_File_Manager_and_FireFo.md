---
title: "[SOLVED] Problem; Webmin's File Manager and FireFox 3.0"
date: 2008-07-09
forum: Server Platforms
---

### Post by Adoran on 2008-07-09
Hello all,

I am creating a home server/client network and I have been getting to grips with the excellent Webmin service ([http://www.webmin.com/](http://www.webmin.com/)).

The problem is this - 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77037&stc=1&d=1215633578[/IMG]

Here I have clicked the the file manager hyperlink and the resulting grey box appears but does not initialize the java applet. I am positive that this is a FireFox 3.0 specific issue and here are the steps I've taken so far - 

[LIST]
Upgraded to Webmin 1.420
Checked that I have java enabled in FireFox 3.0 (Edit > Preferences > Enable Java)
Verified that my browser views java by visiting this site.
[http://www.bodo.com/javame.htm]("http://www.bodo.com/javame.htm")
Logged onto webmin with a copy of Internet Explorer 7 - The java applet worked.
Appealed to you lovely people for help!
[/LIST]

I'll check the firefox forums again but so far I haven't found the answer. 

Many thanks all!

---

### Post by curtis on 2008-07-09
Works here with Firefox 3 and the free version of Java JRE.
I use Intrepid though - but I am sure it worked on Hardy.

---

### Post by Adoran on 2008-07-09
Very useful reply mate. I googled Intrepid but I'm unclear what it is, is it a browser or java-like service?

I've check my version of java using

```
java --version
```

and the output was - 

```
 :~$ java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)

```

Which version of Java are you using? This might be the cause.

---

### Post by cariboo on 2008-07-09
Intrepid Ibex is the next release of Ubuntu. I use Firefox 3.0 to access my server and I have no problems with the applets starting either. Check your java installation on the computer you are using to access Webmin.

Jim

---

### Post by akoutsoulelos on 2008-07-10
I do have the same problem, using Hardy, Firefox 3.0 and the same version of Java...I've been also through the same steps, trying to solve this one, but still no success...The thing is that before the today's update of java-plugin no other java apllet would be loaded through Firefox (not even the java's test page!!!), but after this update everything works but webmin!!!

My search to the net showed that similar bugs had poped up in the past and (hopefully) solved (by Webmin development team), but no answer to this one yet...

Could this be a bug of Firefox or Webmin?

---

### Post by Adoran on 2008-07-11
At last, I'm not going mad! :) I'm sorry to here you have the same problem as I do. I've still had no luck with the support forum on mozilla.org and I've yet to get through the queue to have a support chat; Anything I find I'll report back to here.

> **akoutsoulelos said:**
> 

Could this be a bug of Firefox or Webmin?

I'm not sure in the slightest but I'm sure will learn something in the process of finding out. Anybody out there familiar with how java and firefox work with one another?

---

### Post by akoutsoulelos on 2008-07-13
A friend just suggested that we should use not IcedTea Project OpenJDK Runtime but Sun Java Runtime, 'cause Webmin (File Manager) works right only with it! I have no time to check this one out now and in a couple of hours I'm leaving (finally) for a 6-day-vacations, during which I will have access to a PC and net, but not from my PC...

So, please check this hint and post here any results..

---

### Post by Adoran on 2008-07-16
Congratulations akoutsoulelos, my friend! Your mate had the right idea. The problem is with the IcedTea Java program and by selecting Sun's Java runtime the problem is resolved. 

I'll post the solution shortly and rename the title of this post as solved.

---

### Post by Adoran on 2008-07-16
**SOLUTION**

There is a bug with the Webmin service and FireFox 3.0 whereby the java applet does not initialize for some of the features of webmin, namely the file manager. 

The problem is with the java plugin that you are using. To check which java plugin you have installed (and running) type in the address box of the firefox broswer; 

```
 about:plugins

```

Scroll down. By default with Hardy you will have IcedTea installed. To change from IcedTea to Sun Java runtime type this into terminal;

```
 sudo update-alternatives --config xulrunner-1.9-javaplugin.so
```

You will receive a prompt, which hopefully should include the 'java-6-sun' plugin, it is there, I assume, by default-

```
 There are 2 alternatives which provide `xulrunner-1.9-javaplugin.so'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/gcjwebplugin.so
          2    /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Enter the number of selection. Restart your firefox, (I simply closed mine but I imagine there is a code for that and all).

Your problem should now be solved. 

My thanks goes to kubug for this post[http://ubuntuforums.org/showthread.php?t=856703]("http://ubuntuforums.org/showthread.php?t=856703") where I sourced the code for changing the java plugin type. :)

---

### Post by akoutsoulelos on 2008-07-20
Super!! Finally it worked also for me...

Thanks Adoran, getting back from vacations and having the solution to this problem (which troubled me quite long) just served is the best painkiller against the ugly thoughs of getting back to work tomorrow... :-D

The credits should also go to Hellenic Linux Format forum administrator, as the idea was his own... thanks dimitris ;-)

---

