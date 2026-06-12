---
title: "Permission rights for socket creation?"
date: 2008-11-20
forum: Security
---

### Post by leo_unbut on 2008-11-20
I have a Java-program which launches a Server-process on a specific port (9001). While the launch for one user succeeds it fails for another one with 'java.sql.SQLException: socket creation error'.

I heavily suspect it is an issue with permission rights for the specific user. I do not wanna give them full control over the system, just to be able to launch the Server-process.

So, 

Q1) Is this related to permission rights?
Q2) Is there a way to give a programm the proper rights despite of the user-rights? If so, how?

---

### Post by stmurray on 2008-11-20
Generally on Unix anyone should be able to open a socket with a port > 1024 (ports 0 - 1024 require root access).  I can open a socket (using netcat) on my Ubuntu workstation as an ordinary user.   

I'm not sure if Ubuntu adds any security above that.  Often, when I get a "socket creation error" it's because I forgot to close the application and already have the socket (that is, port) open (doh!).  Make sure that is not happening to you.  

Have you checked the logs for any error messages?

---

