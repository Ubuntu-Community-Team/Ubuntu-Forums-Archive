---
title: "service runas problem"
date: 2007-08-08
forum: Server Platforms
---

### Post by Obfuscator on 2007-08-08
Hi!

I've been looking around this forum and using google for several hours without finding the answer to this one.

I've installed jboss, and want to run it as a service, under the user "jboss".

I've created a script in /etc/init.d/jboss. This script does "su -l jboss -c '/opt/jboss/bin/run.sh' "

This method seems to work if its started from rc*.d, since the su works great when being root.

When I'm my default user, however, issuing /etc/init.d/jboss start prompts me with a password. I would like to avoid this.

I know that if I try to run any other init scripts that are already there, I'm not prompted with any password, even though they may run as other users
(for example apache2, which runs as www-data).

I've tried to disable password for the jboss user (bad idea?), doing a chmod u+s on the init script and also setting a blank password (did not work and definataly bad idea i think). So what do I do??? Does it make a difference if I make the jboss user a "system user"?

Thanks

---

### Post by kidders on 2007-08-10
Hi there,

In general, scripts in /etc/init.d are not intended to be executed by unprivileged users. Doing so can cause unpredictable behaviour.

> **Obfuscator said:**
> I've tried to disable password for the jboss user (bad idea?), doing a chmod u+s on the init script and also setting a blank password (did not work and definataly bad idea i think).I'm not sure why playing with the "jboss" user's password would make any difference, but I do know that Linux will ignore an SUID bit on a shell script.

---

### Post by Obfuscator on 2007-08-10
> **kidders said:**
> Hi there,

In general, scripts in /etc/init.d are not intended to be executed by unprivileged users. Doing so can cause unpredictable behaviour.

I'm not sure why playing with the "jboss" user's password would make any difference, but I do know that Linux will ignore an SUID bit on a shell script.

Thanks a lot for your answer. I was being confused. Anyway, everything works fine now. 

For anyone else that wants to set up a developer + deamon envrionment:
I figured out that I could create a user group "jbossusers", and add me and "jboss" to it. I then made sure that all files in jboss dir is owned by jboss:jbossusers. 
Lastly, I chmodded all files to g+w. Now I can run jboss as myself without pwd,
and the init.d-script can run jboss as the "jboss" user (script gets run as root, but it runs jboss as "jboss"). Sorted!

---

