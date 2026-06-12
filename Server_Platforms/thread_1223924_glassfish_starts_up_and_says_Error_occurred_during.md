---
title: "glassfish starts up and says: Error occurred during initialization of VM"
date: 2009-07-26
forum: Server Platforms
---

### Post by KewlEugene on 2009-07-26
glassfish starts up and says: Error occurred during initialization of VM. this error occurs on an jaunty 9.04 amd64 vps rented server with 768MB. (On my notebook with jaunty 9.04 amd74, glassfish takes only 205MB).

1st i did:
        apt-get install sun-java6-jdk
        apt-get install glassfishv2

then:

        root@Kewl:~# asadmin start-domain domain1
        Starting Domain domain1, please wait.
        Log redirected to /root/glassfishv2/domain1/logs/server.log.
        Please enter the admin user name>admin
        Please enter the admin password>adminadmin
        Redirecting output to /root/glassfishv2/domain1/logs/server.log
        Error occurred during initialization of VM
        Could not reserve enough space for object heap
        Could not create the Java virtual machine.

but i have enuf mem:

        root@Kewl:~# free -mt
                total       used       free     shared    buffers     cached
        Mem:           768        252        515          0          0          0
        -/+ buffers/cache:        252        515
        Swap:            0          0          0
        Total:         768        252        515

i tried removing and re-installing, updating, etc. what should i try next ?

---

