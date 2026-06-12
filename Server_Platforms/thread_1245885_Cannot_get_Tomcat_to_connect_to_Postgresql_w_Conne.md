---
title: "Cannot get Tomcat to connect to Postgresql w/ ConnectionPool"
date: 2009-08-21
forum: Server Platforms
---

### Post by slowtrain on 2009-08-21
PROBLEM SOLVED:  SEE 3rd msg Below

Hi folks:  I've installed a JSP application of mine that uses Tomcat and Postgresql previously without problems on both Redhat and Ubuntu, but that was before I used Synaptic to install Tomcat.  Now I get the following error message (tomcat 6, postgresql 8.3, connection pooling setup in tomcat).  I'm a tad stumped.

"Cannot create PoolableConnectionFactory (Your security policy has prevented the connection from being attempted.  You probably need to grant the connect java.net.SocketPermission to the database server host and port that you wish to connect to.)"

I figured the problem would be solved by my adding the following to /etc/tomcat6/50local.policy, but I get the exact same error msg:

// The permissions granted to the context WEB-INF/classes directory
grant codeBase "file:${catalina.base}/webapps/ROOT/WEB-INF/classes/-" {
     permission java.net.SocketPermission "127.0.0.1:5432", "connect";
};

Any suggestions on what to try next would be much appreciated!  Is the above permission grant formed properly?  Do I also need to add permissions for the postgresql/jdbc jar file?  That's in the lib folder, which is not under catalina.base.  I guess I could move it under catalina.base.

---

### Post by slowtrain on 2009-08-21
Well, I've tried about a dozen alternatives, including adding permissions for the jdbc file, and I still get the same error.  I've taken the webapps and moved it over to a copy of Tomcat I put on the system without Synaptic, and it works like a charm.  The problem is likely the security system, but I can't seem to make any progress fixing it.  

The Apache Tomcat 6 Security Manager How-To is useless.  It doesn't make very clear how permissions should be written.  It suggests looking at debug output to find out exactly what the security manager is choking on.  But given the way Synaptic sets up Tomcat, it was difficult to get Tomcat to cough up the debug output.  Presumably, you can use this: export CATALINA_OPTS=-Djava.security.debug=all .  But that assumes Tomcat will execute catalina.sh.  Ubuntu's implementation of Tomcat doesn't start up by executing the usual Tomcat files like catalina.sh.  Instead, it uses jsvc to start up instances of tomcat.  

I tried to splice -Djava.security.debug=all into the command line used to start jsvc.  This worked, and as far as I can tell, the output went to syslog.  It isn't enlightening.

Without a clue as to what else to try, I will have to default to using the non-Synaptic installed version of Tomcat.  This is probably less than ideal because it isn't running w/ a security policy (though the server itself is quite secure and this version of Tomcat isn't running under root, as does the Synaptic version) and probably won't take advantage of more efficient code buried in the system.

---

### Post by slowtrain on 2009-08-21
After searching for hours on the web, I finally found something that works:

At the top of 04webapps.policy, I put the following:

grant {
   permission java.net.SocketPermission "127.0.0.1:5432","resolve,connect"; 
};

Now, why this works and the changes I tried to 50local.policy is quite unclear to me.  I wish I knew of a manual somewhere that explains this.

---

### Post by josexato on 2009-09-27
thanks slowtrain,

this solution worked for me: 

> grant {
permission java.net.SocketPermission "127.0.0.1:5432","resolve,connect";
};

although i couldn't find more info about the reason for this.

greetings 

josexato

---

