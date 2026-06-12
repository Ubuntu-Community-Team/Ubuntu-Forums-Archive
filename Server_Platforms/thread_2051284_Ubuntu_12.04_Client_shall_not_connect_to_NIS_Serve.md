---
title: "Ubuntu 12.04 Client shall not connect to NIS Server when it is down"
date: 2012-09-01
forum: Server Platforms
---

### Post by lobosch on 2012-09-01
Hello, 

I have a question:
I setup a nis server with different user accounts. On the client i have a lokal user (for administration when network is broken) and the nis configuration to make the nis user from the server available. Of course I also set up a nfs mount for the home directories. I changed the location of the nis user home directories to make the local client user also availble.

This works fine as long as the nis server is active. When I shut it down, the client cannot start. It does not show the login screen. I expected to be able to login than with the local account.

the error is: 
ypbind_proc: Domain not bound

do you have any idea? I think it just waits for getting the nis server available, cause when I than start the nisserver, the login is possible than.

how can I tell my client maschine not to wait for nis server...like a time out or a number of retries? or to run in background and not to block the login of local users? 

btw. I do not request by broadcasting the network. I tell my clientmaschine which ip he has to look for.

would appreciate any answer.

thank you 

robert

---

### Post by lobosch on 2012-09-03
ok, i found the problem:

/etc/nsswitch my not working version:
[I]passwd: nis compat
[/I]*shadow:[I] nis compat*[/I][I] 
group:[I] nis compat

now I changed it to
[/I][/I]
*passwd: compat*[I] nis
[/I]*shadow:[I] compat*[/I][I] nis
[/I]* group:[I] compat*[/I] nis

Now I can login. The problem is, that it takes a lot of time. Can I set a time out there when nis could not find a user, or the server is down? I use the +::: style in the passwd, group etc. files

would appreciate any help!

Robert

---

