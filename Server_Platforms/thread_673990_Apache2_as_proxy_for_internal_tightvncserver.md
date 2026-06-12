---
title: "Apache2 as proxy for internal tightvncserver"
date: 2008-01-21
forum: Server Platforms
---

### Post by flava8 on 2008-01-21
Hi,

I've a tightvncserver running. The JAVA port is listenning on 8888 and the tightvncserver iitself on 5901.

Accessing the tightvncserver via the tight java client applet works fine.
For instance, [http://192.168.0.8:8888](http://192.168.0.8:8888) loads the applet and I can login as usual to get the remote desktop.

The above mentioned IP is only accessible from the intranet.

What I am trying to do now is to setup Apache2 as a proxy which delegates my request to the tightvncserver.
Apache2 is accessible from the internet via http://vncapplet.<my server name>.com

The httpd.conf file entries are currently:
ProxyRequests off 
ProxyPass /vncapplet [http://192.168.0.8:8888](http://192.168.0.8:8888)
ProxyPassReverse /vncapplet  [http://192.168.0.8:8888](http://192.168.0.8:8888)

The current situation is that my request gets internally delegated correctly but the the applet doesn't  load. Basically, the returned page contains the same text as if I would take a look into the source of the html page -- so it looks like below on the browser:

<!-- 
     index.vnc - default HTML page for TightVNC Java viewer applet, to be
     used with Xvnc. On any file ending in .vnc, the HTTP server embedded in
     Xvnc will substitute the following variables when preceded by a dollar:
     USER, DESKTOP, DISPLAY, APPLETWIDTH, APPLETHEIGHT, WIDTH, HEIGHT, PORT,
     PARAMS. Use two dollar signs ($) to get a dollar sign in the generated
     HTML page.

     NOTE: the  variable is not supported by the standard VNC, so
     make sure you have TightVNC on the server side, if you're using this
     variable.
-->

<HTML>

<APPLET CODE=VncViewer.class ARCHIVE=VncViewer.jar
        WIDTH=1280 HEIGHT=1056>
<param name=PORT value=5901>

</APPLET>
<BR>
<A href="http://www.tightvnc.com/">TightVNC site</A>
</HTML> 


Does someone has a working solution for this?

Many thanks,
Nick

---

