---
title: "Issues with maven docker plugin on Ubuntu Server 14.04"
date: 2015-02-24
forum: Ubuntu Application Development
---

### Post by daniel249 on 2015-02-24
Hello I am using Ubuntu Server 14.04 on a local virtual machine for compiling.
I have issues with the docker maven plugin when I want to compile my Java Application with `mvn clean install` resigning in a LifecycleExcepion.
 The Error Message is:
"[ERROR] Failed to execute goal org.jolokia:docker-maven-plugin:0.11.0:build (build) on project places_app: Execution build of goal org.jolokia:docker-maven-plugin:0.11.0:build failed: No url given and no DOCKER_HOST environment variable set"

I already have set my DOCKER_Hist variable as tcp://127.0.0.1:4243. I clearly don't know how to get past this issue since the variable is set and I can start the docker daemon with no problems. A 'telnet localhost 4243' on the other side doesn't seem to work. 
Has anyone a solution for this problem?

Thank you for your help!

---

