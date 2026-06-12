---
title: "FTP error occurs while Opening directory"
date: 2007-08-09
forum: Server Platforms
---

### Post by mocherla14 on 2007-08-09
Please note that this happens only on ONE directory of the entir machine. We  have checked the directory ownerships and permissions, but it is not the cause  of the problem.
 A second production node called server2  also has the same 
directory /mediacao with same permissions, however the problem does not occur  there.

Therefore we suspect that it might be certain files within the /mediacao 
directory that may be causing the problem. Or perhaps something wrong with the  directory headers, but /mediacao can be accessed/copied from the OS, just not  from ACRS.

We have tried creating a new directory called /mediacao2 (with same 
permissions/owner), and copied certain files from /mediacao. The test was 
inconclusive as there is not enough space to fully do a copy and this directory  has sensitive production data. Nonetheless, ACRS did not produce any errors  when accessing /mediacao2.

We need the PDU to help in answering some questions, and providing suggestions  as to how to fix this.

1. What possible problem with the system environment could be the cause of this  error (""An error occured while speaking with the FTP server")

the error that could help you troubleshoot the problem.
I have tested, at my test server, some permission issues and the conclusion is that directory is supposed to have just permission to execution (x). If you create a directory where the owner is root and set the permission to 711 that means  it has just permission to be eXecuted by other users and try to access it, you will be successful. When I forbid the execution I get the message below:
 popup error message -> CWD:/mediacao 550/mediacao: Permisssion denied. 

In  server2 ,  /mediacao is opening from ACRS GUI.
And in these server1,  /mediacao is not opening from ACRS GUI.and the error gives as "An error occurred while speaking with the FTP server" .
please help in this issue

---

