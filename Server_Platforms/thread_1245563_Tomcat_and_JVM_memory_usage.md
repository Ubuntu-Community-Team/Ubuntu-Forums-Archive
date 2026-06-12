---
title: "Tomcat and JVM memory usage"
date: 2009-08-20
forum: Server Platforms
---

### Post by doktoreas on 2009-08-20
Hello folks,
I have a question about memory usage and JVM/Tomcat:
This is the script I created to start tomcat:
```

    export JAVA_HOME=/usr/lib/jvm/java-6-sun
    export JAVA_OPTS="-Djava.awt.headless=true -server -Xms48m -Xmx1024M -XX:MaxPermSize=512m -XX:+UseParallelGC"
    case $1 in
    start)
            sh /usr/local/tomcat/bin/startup.sh
            ;;
    stop)
            sh /usr/local/tomcat/bin/shutdown.sh
            ;;
    restart)
            sh /usr/local/tomcat/bin/shutdown.sh
            sh /usr/local/tomcat/bin/startup.sh
            ;;
    esac
    exit 0


```
After some days top shows that java is using 53% ( 2 Gb); why this value? using the xmx option doesn't block the max to 1024?

Thank you
Luca

---

### Post by DaithiF on 2009-08-20
Hi, -Xmx limits the size of the java heap, but the size of the java process will be bigger than this.  But first, which column are you looking at in top ?  VIRT, or RES ?
thanks

---

### Post by doktoreas on 2009-08-21
Hi and thanks for your answer.
After a lot of use of the web application, I have got:

VIRT 3491m
RES 2.1g
SHR 15m

%MEM 53.5

Ciao
Luca

---

### Post by DaithiF on 2009-08-24
Hi, 
at first i assumed this would be a case of the OS reporting lots of VIRT memory,which is generally fine and doesn't bear much resemblance to the amount of physical memory actually being used by your process.  But when I saw the RES figure of 2gb I was surprised, because that is indeed the amount of physical memory being allocated, so a java process with a max heap of 1gb consuming 2gb of memory is quite unusual.

Taking a closer look at your original post, you have set a max permgenspace of 512mb -- that is separate to the heap size controlled by the Xmx setting, so that is 1.5gb in total.   That amount of Permgenspace may well be too much -- the default is 64mb I believe (though it can vary by platform).  I would have thought you could reduce this pretty substantially -- unless or until you start getting out of memory permgen errors you can try reducing this to reduce overall memory usage.

That still doesn't account for the remaining 0.5gb usage.  I'm a little rusty here, as its a year or more since I've been working in java, but there are some additional variables in play here ...
So the heap (as controlled by Xmx) is split into New Generation and Tenured.  The ratio can be controlled by the NewRatio parameter, and the default varies by processor and platform, but is often 2, which means a new generation of 1/3 the size of the overall heap.  Within the NewGeneration you have an Eden space and Two survivor spaces -- the ratio of eden to survivor can be controlled by the Survivor parameter, but usually defaults to 8.  Now I think that the NewGen size = Eden + 1xSurvivor space, and therefore there is additionally the second Survivor space to be included when calculating total memory usage.  You could possibly have a smaller than normal survivor ratio, which would mean a larger survivor space, and therefore a higher than expected total memory usage.

There are lots of jvm options you can pass to get more details on sizing of the various spaces, and I'd be curious to debug further to fully explain the 2gb, but i suppose the short answer is that the size of your permgen space is likely far greater than it needs be.  If you want to limit overall memory usage to ~1gb, then reduce Xmx a little below that, and bring down MaxPermGen space too.

cheers
D

---

