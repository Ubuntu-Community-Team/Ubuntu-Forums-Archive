---
title: "Setting VM Parameters that apt-get installed tomcat6 will use?"
date: 2009-02-27
forum: Server Platforms
---

### Post by rasta_caleb on 2009-02-27
I recently installed tomcat6/hudson/artifactory on Ubuntu 8.10 Server.

Everything works fine, but I had to do a stupid hack to make things work the way I really wanted, and I would like to avoid doing so if possible.

The problem is this: artifactory wants to use /usr/share/tomcat6/.artifactory as it's home dir, but I want it to use /opt/artifactory for it's home dir

I tried to use the JAVA_OPTS env param to make the change, and here is what I put:

JAVA_OPTS=-Dartifactory.home=/opt/artifactory

But that doesn't seem to work.  That's being set in /etc/profile, as well as in the tomcat6 user's .bashrc

The tomcat log says:
"Looking for '-Dartifactory.home=<path>' vm parameter..."
"Using artifactory.home at '/usr/share/tomcat6/.artifactory"

Not what I want.  Can anyone help?

Thank you.

PS. The "hack" that I'm using is just a symbolic link pointing /usr/share/tomcat6/.artifactory to /opt/artifactory

---

