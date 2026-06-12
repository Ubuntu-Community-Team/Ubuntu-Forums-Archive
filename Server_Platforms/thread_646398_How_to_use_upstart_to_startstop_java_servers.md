---
title: "How to use upstart to start/stop java servers?"
date: 2007-12-21
forum: Server Platforms
---

### Post by bashu on 2007-12-21
Hi friends,

I like upstart very much and the way to start/stop my own jobs (in /etc/event.d/) via initctl.

But I failed to create a job to start/stop java server (z3ext.lucene - lucene text indexer, from [http://sourceforge.net/projects/z3ext](http://sourceforge.net/projects/z3ext)).

Here is my upstart job:

```
# Lucene text indexer
#
# This service starts lucene server from the point the system is
# started until it is shut down again.

start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5

stop on shutdown

script
        # Jython interpreter
        JYTHON=/usr/bin/jython

        echo $JYTHON >> /tmp/lucene.log

        # Path to Lucene server
        SERVER_PATH=/usr/share/zope/z3ext/lucene/server

        echo $SERVER_PATH >> /tmp/lucene.log

        # Index Data directory
        INDEX=$SERVER_PATH/indexdata

        echo $INDEX >> /tmp/lucene.log

        # XML-RPC Server Port
        PORT=19983

        echo $PORT >> /tmp/lucene.log

        # Path to the Lucene library
        LUCENE=$SERVER_PATH/jar/lucene-core-2.2.0.jar:$SERVER_PATH/jar/lucene-queries-2.2.0.jar:$SERVER_PATH/jar/lucene-snowball-2.2.0.jar

        echo $LUCENE >> /tmp/lucene.log

        # Path to the XML-RPC library
        XMLRPC=$SERVER_PATH/jar/xmlrpc-1.2-b1.jar

        echo $XMLRPC >> /tmp/lucene.log

        export CLASSPATH=$LUCENE:$XMLRPC

        echo $CLASSPATH >> /tmp/lucene.log

        # Start the server
        exec $JYTHON $SERVER_PATH/indexserver.py $PORT $INDEX

        echo 'DONE!' >> /tmp/lucene.log
end script
```

I got this message in /var/log/syslog - init: lucene process (1599) terminated with status 1

However I able to start lucene server manually from command line, running process looks like:

```
/usr/bin/java -Djava.library.path=/usr/lib/jni -Dpython.home=/usr/share/jython -Dpython.path=.:/usr/share/jython/Lib:/usr/share/jython/Lib-cpython -Dpython.cachedir=/root/.jython-cache org.python.util.jython /usr/share/zope/z3ext/lucene/server/indexserver.py 19983 /usr/share/zope/z3ext/lucene/server/indexdata
```

I don't know how to debug upstart/initctl and have no idea why this job doesn't working...

Any help appreciated.

---

