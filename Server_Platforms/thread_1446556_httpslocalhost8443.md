---
title: "https://localhost:8443"
date: 2010-04-04
forum: Server Platforms
---

### Post by patrice Madrid on 2010-04-04
Hi everybody,

I have installed a program calle "Tercompta". Everytime I try to open it, the browser goes to that direction:[https://localhost:8443/tercompta/control/main](https://localhost:8443/tercompta/control/main)

and after a while sends me the message saying that I can't connect.

I quiet sure it's a port problem with the Apache server but don't know how to fix it.

Can somebody tell me how to do it?

Thanks.

Patrice

Patrice Bertin
Ubuntu (9.10) Karmic

---

### Post by ICEB3AR on 2010-04-04
Why are you quite sure that it's an apache problem. It could be possible that Tercompta has it's own little daemon which serves the request or not?
Or Have you copied the files to your apache directory?

Are you sure the port 8443 is open? To check try the following:
```

sudo lsof -i :8443

#OR 

sudo apt-get install nmap
sudo nmap -v -A localhost
```
then there is a list of open ports and if 8443 isn't open this is the first problem.

---

### Post by patrice Madrid on 2010-04-04
Hi,

Thanks for your reply.
I am not sure at all it's an Apache problem. I was just guessing.
I didn't copied any file to the apache directories.
I have try your instructions. 
the first one didn't do anything. I then install nmap (sudo apt-get install nmap).

the result of the sudo nmap -v -A localhost gave me the following:

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-04-04 17:44 CEST
NSE: Loaded 30 scripts for scanning.
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Initiating SYN Stealth Scan at 17:44
Scanning localhost (127.0.0.1) [1000 ports]
Discovered open port 80/tcp on 127.0.0.1
Discovered open port 3306/tcp on 127.0.0.1
Discovered open port 8080/tcp on 127.0.0.1
Discovered open port 631/tcp on 127.0.0.1
Completed SYN Stealth Scan at 17:44, 0.06s elapsed (1000 total ports)
Initiating Service scan at 17:44
Scanning 4 services on localhost (127.0.0.1)
Completed Service scan at 17:44, 6.66s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against localhost (127.0.0.1)
Retrying OS detection (try #2) against localhost (127.0.0.1)
Retrying OS detection (try #3) against localhost (127.0.0.1)
Retrying OS detection (try #4) against localhost (127.0.0.1)
Retrying OS detection (try #5) against localhost (127.0.0.1)
NSE: Script scanning 127.0.0.1.
NSE: Starting runlevel 1 scan
Initiating NSE at 17:44
Completed NSE at 17:44, 0.05s elapsed
NSE: Script Scanning completed.
Host localhost (127.0.0.1) is up (0.000035s latency).
Interesting ports on localhost (127.0.0.1):
Not shown: 996 closed ports
PORT     STATE SERVICE VERSION
80/tcp   open  http    Apache httpd 2.2.12 ((Ubuntu))
|_ html-title: Site doesn't have a title (text/html).
631/tcp  open  ipp     CUPS 1.4
3306/tcp open  mysql   MySQL 5.1.37-1ubuntu5.1
|  mysql-info: Protocol: 10
|  Version: 5.1.37-1ubuntu5.1
|  Thread ID: 325
|  Some Capabilities: Long Passwords, Connect with DB, Compress, ODBC, Transactions, Secure Connection
|  Status: Autocommit
|_ Salt: hUS"M=,`$/_q<sPsvvk8
8080/tcp open  http    Apache Tomcat/Coyote JSP engine 1.1
|_ html-title: Apache Tomcat
No exact OS matches for host (If you know what OS is running on it, see [http://nmap.org/submit/](http://nmap.org/submit/) ).
TCP/IP fingerprint:
OS:SCAN(V=5.00%D=4/4%OT=80%CT=1%CU=37165%PV=N%DS=0%G=Y%TM=4BB8B3F2%P=i686-p
OS:c-linux-gnu)SEQ(SP=C6%GCD=1%ISR=C6%TI=Z%CI=Z%II=I%TS=8)OPS(O1=M400CST11N
OS:W6%O2=M400CST11NW6%O3=M400CNNT11NW6%O4=M400CST11NW6%O5=M400CST11NW6%O6=M
OS:400CST11)WIN(W1=8000%W2=8000%W3=8000%W4=8000%W5=8000%W6=8000)ECN(R=Y%DF=
OS:Y%T=40%W=8018%O=M400CNNSNW6%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%
OS:Q=)T2(R=N)T3(R=Y%DF=Y%T=40%W=8000%S=O%A=S+%F=AS%O=M400CST11NW6%RD=0%Q=)T
OS:4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+
OS:%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y
OS:%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%
OS:RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 0.203 days (since Sun Apr  4 12:52:42 2010)
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=198 (Good luck!)
IP ID Sequence Generation: All zeros

Read data files from: /usr/share/nmap
OS and Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 19.50 seconds
           Raw packets sent: 1095 (51.990KB) | Rcvd: 2209 (98.676KB)


It doesn't tell me much.


Patrice

---

### Post by ICEB3AR on 2010-04-06
so there is your problem. You try to connect to port 8443, but this port is not open and MAYBE adding to this there is no deamon serving the request at this port.
> Discovered open port 80/tcp on 127.0.0.1
Discovered open port 3306/tcp on 127.0.0.1
Discovered open port 8080/tcp on 127.0.0.1
Discovered open port 631/tcp on 127.0.0.1
there is no open port 8443, as also the first command (sudo lsof -i:8443) shows (in that way that it did nothing). To crosscheck you could try the same command with an port which is definetely open like apache
```
sudo lsof -i:80
```

I'm sorry that i can not help you any more, because i didn't know Tercompta, but so far you can not try to get something on a closed port.

---

### Post by tgalati4 on 2010-04-06
Look in your /etc/init.d:

You should have a control script to start tercompta--I have no idea what this program does.

In that directory:

sudo /.tercompta restart

Or something similar.  Installing a server-based program often requires that you manually start the service.  Once the service is running, your port should then respond to page requests.

To see if your program is running:

ps -ef | grep tercompta

---

### Post by Jive Turkey on 2010-04-06
well I don't know what terracompta is either but it sounds like you need to do one of the following.

A. Change the listening port for teracompta to one that is open.  I don't know if that's even possible.

B. open the port using ufw or iptables, your preference.

---

### Post by mbehamin on 2010-04-06
Hi
Mmm im not sure but 8443 is the default port of tomcat with ssl ! (java web server) and also based on the nmap output you have port 8080 without ssl. check the port 8080 is working or not! 

and by the way , instead of using nmap localhost you simply can use netstat -npl :) its shows what exactly process listening on which port :) test it to make sure that 8080 is opened by the java . if yes , it coud be your desire port 

im not sure . but i guess 
regards

---

### Post by mbehamin on 2010-04-06
note that use http instead of  https for using port 8080 .

---

### Post by tekkidd on 2010-04-06
hmmm i have an occasional problem with webmin where if i go to [https://localhost:10000](https://localhost:10000) it cant connect. Try to connect via https://<your ip address>:port#

---

### Post by patrice Madrid on 2010-04-07
Hi everybody,

Fisrt of all, thanks to have a look at my post and sory to respond that late. Tercompta is an free open accountancy program.

When I enter sudo lsof -i:8443, nothing happens.
If I enter sudo lsof -i:80:

COMMAND  PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
apache2 2515     root    4u  IPv6  10898      0t0  TCP *:www (LISTEN)
apache2 2521 www-data    4u  IPv6  10898      0t0  TCP *:www (LISTEN)
apache2 2522 www-data    4u  IPv6  10898      0t0  TCP *:www (LISTEN)
apache2 2523 www-data    4u  IPv6  10898      0t0  TCP *:www (LISTEN)
apache2 2524 www-data    4u  IPv6  10898      0t0  TCP *:www (LISTEN)
apache2 2525 www-data    4u  IPv6  10898      0t0  TCP *:www (LISTEN)
firefox 4553   virpat   22u  IPv4  35294      0t0  TCP virpat-desk.local:56207->ez-in-f101.1e100.net:www (ESTABLISHED)
firefox 4553   virpat   57u  IPv4  34835      0t0  TCP virpat-desk.local:36113->ew-in-f104.1e100.net:www (ESTABLISHED)
firefox 4553   virpat   61u  IPv4  34871      0t0  TCP virpat-desk.local:41506->213-248-125-120.customer.teliacarrier.com:www (ESTABLISHED)
firefox 4553   virpat   62u  IPv4  34872      0t0  TCP virpat-desk.local:41507->213-248-125-120.customer.teliacarrier.com:www (ESTABLISHED)
firefox 4553   virpat   66u  IPv4  35143      0t0  TCP virpat-desk.local:41230->ey-in-f100.1e100.net:www (ESTABLISHED)


If I enter sudo lsof -i:8080:

COMMAND  PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
jsvc    2545 tomcat6   33u  IPv6  11086      0t0  TCP *:http-alt (LISTEN)

I open the port 8443 using ufw (8443 allow anywhere) but it's still doesn't work.

doing netstat -npl, it shows this:

(No todos los procesos pueden ser identificados, no hay información de propiedad del proceso
 no se mostrarán, necesita ser superusuario para verlos todos.)
Conexiones activas de Internet (solo servidores)
Protocolo Recv-Q Send-Q Dirección Local Dirección Externa Estado       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               ESCUCHAR    -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               ESCUCHAR    -               
tcp6       0      0 :::8080                 :::*                    ESCUCHAR    -               
tcp6       0      0 :::80                   :::*                    ESCUCHAR    -               
tcp6       0      0 ::1:631                 :::*                    ESCUCHAR    -               
udp        0      0 0.0.0.0:37041           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*  

(escuchando means listen)

the README tercompta talks about this famous port but my knowledge are to limited to understand.Let's see if it gives you some more information:
"Welcome to Apache OFBiz!

If you have a release build all you need to run OFBiz is a 
1.6 (version 6) JDK (not just the JRE, the full JDK).
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

However if you have downloaded ofbiz from SVN then you should
load the demo data (strongly advised) with the following command
on the command line: (being in the OFbiz directory)

linux: ./ant run-install
windows: ant run-install 

Once that is properly setup just run the executable jar file
that comes with OFBiz, which is ofbiz.jar. To do this on the
command line you would run:

java -Xms128M -Xmx512M -jar ofbiz.jar

Even better use the startup scripts for Windows and Unix-based
operating systems, namely startofbiz.bat and startofbiz.sh.

Once OFBiz starts, you can look at the demo storefront at:
[http://localhost:8080/ecommerce](http://localhost:8080/ecommerce)

and the administration interface at:
[https://localhost:8443/webtools](https://localhost:8443/webtools)

You can log in with the user "admin" and password "ofbiz".

For more details about running a build, or for information on
getting, building, and running the source please see the
Apache OFBiz Setup Guide:

[http://cwiki.apache.org/confluence/display/OFBADMIN/Demo+and+Test+Setup+Guide](http://cwiki.apache.org/confluence/display/OFBADMIN/Demo+and+Test+Setup+Guide)

Note that running with the default configuration uses an
embedded Java database (Apache Derby), and embedded application
server components such as Tomcat, Geronimo (transaction manager), etc.

To prepare OFBiz for production use the Basic Production Setup Guide
is a great place to start. It is available here:

[http://cwiki.apache.org/confluence/display/OFBTECH/Apache+OFBiz+Technical+Production+Setup+Guide](http://cwiki.apache.org/confluence/display/OFBTECH/Apache+OFBiz+Technical+Production+Setup+Guide)

For additional resources please see the OFBiz web site.

Enjoy!"

Thanks again

Patrice

---

### Post by mattboll on 2010-04-07
Hi, you may want to ask your question directly to the tercompta community [https://lists.sourceforge.net/lists/listinfo/neogia-users](https://lists.sourceforge.net/lists/listinfo/neogia-users)  or [https://lists.sourceforge.net/lists/listinfo/neogia-ofbiz-fr](https://lists.sourceforge.net/lists/listinfo/neogia-ofbiz-fr) for french (tercompta is a piece of neogia, it's an accounting software)

btw, you don't need apache to run tercompta. 
could you find Tercompta/runtime/logs/console.log and see if there are relevant errors at the end of the file ?

It also seems that you have a tomcat running, which could make a conflict.

---

### Post by patrice Madrid on 2010-04-09
Hi mattball,

the last 2 messages sent to the Tercompta community were mine but no answer. Most of the people sent mails in 2006 (which make me think the program is quiet old but anyway)

I you want to have a lok at the logs, here there are:

Set OFBIZ_HOME to - /home/virpat/Tercompta/TerCompta/TerCompta
Admin socket configured on - /127.0.0.1:10523
Loaded ESAPI properties from classpath
  

  |   LogEncodingRequired=false
  |   LogLevel=ALL
  |   MaxUploadFileBytes=500000000
  |   ResponseContentType=text/html; charset=UTF-8
  |   ValidExtensions=.zip,.pdf,.doc,.docx,.ppt,.pptx,.tar,.gz,.tgz,.rar,.war,.jar,.ear,.xls,.rtf,.properties,.java,.class,.txt,.xml,.jsp,.jsf,.exe,.dll
  |   Validator.AccountName=^[a-zA-Z0-9]{3,20}$
  |   Validator.CreditCard=^(\d{4}[- ]?){3}\d{4}$
  |   Validator.DirectoryName=^[a-zA-Z0-9.-\_ ]{0,255}$
  |   Validator.Email=^[A-Za-z0-9._%-]+@[A-Za-z0-9.-]+\.[a-zA-Z]{2,4}$
  |   Validator.FileName=^[a-zA-Z0-9.\-_ ]{0,255}$
  |   Validator.HTTPCookieName=^[a-zA-Z0-9\-_]{0,32}$
  |   Validator.HTTPCookieValue=^[a-zA-Z0-9\-\/+=_ ]*$
  |   Validator.HTTPHeaderName=^[a-zA-Z0-9\-_]{0,32}$
  |   Validator.HTTPHeaderValue=^[a-zA-Z0-9()\-=\*\.\?;,+\/:&_ ]*$
  |   Validator.HTTPParameterName=^[a-zA-Z0-9_]{0,32}$
  |   Validator.HTTPParameterValue=^[a-zA-Z0-9.\-\/+=_ ]*$
  |   Validator.IPAddress=^(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$
  |   Validator.Redirect=^\/test.*$
  |   Validator.RoleName=^[a-z]{1,20}$
  |   Validator.SSN=^(?!000)([0-6]\d{2}|7([0-6]\d|7[012]))([ -]?)(?!00)\d\d\3(?!0000)\d{4}$
  |   Validator.SafeString=^[p{L}p{N}.]{0,1024}$
  |   Validator.SystemCommand=^[a-zA-Z\-\/]{0,64}$
  |   Validator.URL=^(ht|f)tp(s?)\:\/\/[0-9a-zA-Z]([-.\w]*[0-9a-zA-Z])*(:(0-9)*)*(\/?)([a-zA-Z0-9\-\.\?\,\:\'\/\\\+=&amp;%\$#_]*)?$
  |   event.test.actions=disable,log
  |   event.test.count=2
  |   event.test.interval=10
  |   org.owasp.esapi.errors.IntegrityException.actions=log,disable,logout
  |   org.owasp.esapi.errors.IntegrityException.count=10
  |   org.owasp.esapi.errors.IntegrityException.interval=5
  |   org.owasp.esapi.errors.IntrusionException.actions=log,disable,logout
  |   org.owasp.esapi.errors.IntrusionException.count=1
  |   org.owasp.esapi.errors.IntrusionException.interval=1
2010-04-08 02:13:06,783 (main) [ ModelEntityChecker.java:501:INFO ] [initReservedWords] array length=1023
org.ofbiz.base.start.StartupException: Cannot init() catalina-container (LifecycleException:  Protocol handler initialization failed: java.net.BindException: Address already in use:8080 (Protocol handler initialization failed: java.net.BindException: Address already in use:8080))
    at org.ofbiz.base.container.ContainerLoader.loadContainer(ContainerLoader.java:190)
    at org.ofbiz.base.container.ContainerLoader.load(ContainerLoader.java:65)
    at org.ofbiz.base.start.Start.initStartLoaders(Start.java:259)
    at org.ofbiz.base.start.Start.init(Start.java:96)
    at org.ofbiz.base.start.Start.main(Start.java:410)
org.ofbiz.base.container.ContainerException: LifecycleException:  Protocol handler initialization failed: java.net.BindException: Address already in use:8080 (Protocol handler initialization failed: java.net.BindException: Address already in use:8080)
    at org.ofbiz.catalina.container.CatalinaContainer.init(CatalinaContainer.java:220)
    at org.ofbiz.base.container.ContainerLoader.loadContainer(ContainerLoader.java:18
    at org.ofbiz.base.container.ContainerLoader.load(ContainerLoader.java:65)
    at org.ofbiz.base.start.Start.initStartLoaders(Start.java:259)
    at org.ofbiz.base.start.Start.init(Start.java:96)
    at org.ofbiz.base.start.Start.main(Start.java:410)
Caused by: LifecycleException:  Protocol handler initialization failed: java.net.BindException: Address already in use:8080
    at org.apache.catalina.connector.Connector.initialize(Connector.java:1060)
    at org.apache.catalina.core.StandardService.initialize(StandardService.java:677)
    at org.ofbiz.catalina.container.CatalinaContainer.init(CatalinaContainer.java:218)
    ... 5 more
org.ofbiz.base.container.ContainerException: LifecycleException:  Protocol handler initialization failed: java.net.BindException: Address already in use:8080 (Protocol handler initialization failed: java.net.BindException: Address already in use:8080)
    at org.ofbiz.catalina.container.CatalinaContainer.init(CatalinaContainer.java:220)
    at org.ofbiz.base.container.ContainerLoader.loadContainer(ContainerLoader.java:18
    at org.ofbiz.base.container.ContainerLoader.load(ContainerLoader.java:65)
    at org.ofbiz.base.start.Start.initStartLoaders(Start.java:259)
    at org.ofbiz.base.start.Start.init(Start.java:96)
    at org.ofbiz.base.start.Start.main(Start.java:410)
Caused by: LifecycleException:  Protocol handler initialization failed: java.net.BindException: Address already in use:80802010-04-08 02:13:25,041 (main) [     Http11Protocol.java:178:ERROR] Error initializing endpoint
java.net.BindException: Address already in use:8080
    at org.apache.tomcat.util.net.JIoEndpoint.init(JIoEndpoint.java:501)
    at org.apache.coyote.http11.Http11Protocol.init(Http11Protocol.java:176)
    at org.apache.catalina.connector.Connector.initialize(Connector.java:1058)
    at org.apache.catalina.core.StandardService.initialize(StandardService.java:677)
    at org.ofbiz.catalina.container.CatalinaContainer.init(CatalinaContainer.java:218)
    at org.ofbiz.base.container.ContainerLoader.loadContainer(ContainerLoader.java:188)
    at org.ofbiz.base.container.ContainerLoader.load(ContainerLoader.java:65)
    at org.ofbiz.base.start.Start.initStartLoaders(Start.java:259)
    at org.ofbiz.base.start.Start.init(Start.java:96)
    at org.ofbiz.base.start.Start.main(Start.java:410)

    at org.apache.catalina.connector.Connector.initialize(Connector.java:1060)
    at org.apache.catalina.core.StandardService.initialize(StandardService.java:677)
    at org.ofbiz.catalina.container.CatalinaContainer.init(CatalinaContainer.java:218)
    ... 5 more

thanks anyway

Patrice

---

### Post by mbehamin on 2010-04-11
hi again
your webserver can not start in port 8080 ! 
Address already in use:8080 (Protocol handler initialization failed: java.net.BindException: Address already in use:8080))
it mays that you have kill all previous ports which uses the 8080 port. to know what porgram uses just type netstat -npl. 
if you run your program twice, please use killall java as root user

regards

---

### Post by patrice Madrid on 2010-04-11
Hi Mehdi,

The thing I don't get is that when I try to open the Tercompta progam, it opens the mozilla browser with the following direction: [https://localhost:8443/tercompta/control/main](https://localhost:8443/tercompta/control/main) but it can't which make me think that it's trying to connect to the port 8443 in https.
I don't understand then why do I have the message saying that the 8080 port is already occupied.
Typing your command (netstat -npl) without starting the tercompta program, gives me this:
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               ESCUCHAR    -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               ESCUCHAR    -               
tcp6       0      0 :::8080                 :::*                    ESCUCHAR    -               
tcp6       0      0 :::80                   :::*                    ESCUCHAR    -               
tcp6       0      0 ::1:631                 :::*                    ESCUCHAR    -               
udp        0      0 0.0.0.0:37421           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*  


Once I have started tercompta:

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               ESCUCHAR    1166/mysqld     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               ESCUCHAR    1624/cupsd      
tcp6       0      0 :::8080                 :::*                    ESCUCHAR    1833/jsvc       
tcp6       0      0 :::80                   :::*                    ESCUCHAR    1779/apache2    
tcp6       0      0 ::1:631                 :::*                    ESCUCHAR    1624/cupsd      
udp        0      0 0.0.0.0:37421           0.0.0.0:*                           803/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           2715/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:* 

the jsvc  (the application who launch java daemon) uses the 8080 and according to the logs, this port is already in use but I don't know who uses it. Talking about the killall action, what is the exact command to kill the application? I normally use the killall -9 and the program (ex: killall -9 firefox) but in this case I don't know which application I have to kill to have the 8080 port free again.

Thanks anyway to have a look at this problem.

Patrice
[B]
[/B]

---

### Post by ICEB3AR on 2010-04-12
on your output of netstat there is: "jsvc" at the end of line 8080. 
comcluding from that fact, that port 3306 belongs to mysql and at the end of that line there is the daemon mysqld i conclude, that the service running on port 8080 is jsvc.
google delivers: 
> Jsvc is a set of libraries and applications for making Java applications run on UNIX more easily.
from [http://commons.apache.org/daemon/jsvc.html]("http://commons.apache.org/daemon/jsvc.html")

---

### Post by mbehamin on 2010-04-17
Just try to kill jsvc  process 
then start the process if its not possible ok go to your deamon configuration ita has a server.xml file try to change the 8080 port into another :)
regards

---

