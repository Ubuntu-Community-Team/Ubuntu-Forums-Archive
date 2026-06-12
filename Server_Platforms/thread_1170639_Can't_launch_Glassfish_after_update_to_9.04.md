---
title: "Can't launch Glassfish after update to 9.04"
date: 2009-05-26
forum: Server Platforms
---

### Post by Brausepaul on 2009-05-26
Hello,

my 8.10 Ubuntu install was updated to 9.04 a while ago. I have a manual glassfish 2.1 installation which I usually started via Eclipse. After the update to Jaunty, the server won't start:

Buildfile: /home/maik/workspace/.metadata/.plugins/org.eclipse.jst.server.generic.core/serverdef/sunappsrv-ant.xml undeploy.j2ee.ear: tools: undeploy: [echo] Undeploying WebServiceHostEAR. BUILD FAILED /home/maik/workspace/.metadata/.plugins/org.eclipse.jst.server.generic.core/serverdef/sunappsrv-ant.xml:145: The following error occurred while executing this line: /home/maik/workspace/.metadata/.plugins/org.eclipse.jst.server.generic.core/serverdef/sunappsrv-ant.xml:71: Execute failed: java.io.IOException: Cannot run program "${sunappserver.rootdirectory}/bin/asadmin": java.io.IOException: error=2, No such file or directory Total time: 209 milliseconds

It seems that glassfish requires an environment variable which got lost in the update process. Any ideas where to set the variable? Or which variables glassfish usually needs?

---

