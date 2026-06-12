---
title: "Fedora Directory Server"
date: 2008-09-30
forum: Server Platforms
---

### Post by El-Wrongo on 2008-09-30
EDIT: Edited for clarity.

I have just installed Fedora Directory Server, on a Ubuntu 8.04 Server Edition server.

I am trying to log in on the administration console, but I keep getting error messages.

I have alrady made another post about it in [this thread]("http://www.linuxforums.org/forum/servers/131338-directory-server.html#post629434") on another forum.

[This is the guide I followed during the installation of Fedora DS]("http://swik.net/Ubuntu/Only+Ubuntu/Howto+install+Fedora+Directory+Server+(DS)+1.04+on+Ubuntu+8.04+(Hardy+Heron)/b6vwe"), and I believe I followed it to the letter.

Here is my last post from the other thread, detailing the problem more.

> New problem, I have finished the tutorial I was following for installing the directory server, and it all went ok, with the exception of the part at the end where I was supposed to edit the /etc/lib.d/local, and that was mostly me left wondering why the file was empty. I added the lines it told me to add, saved it and execute the last two commands.

Anyway, the problem I am having now, is with actually logging in on the directory server. when I run

./startconsole -u admin -a [http://ubuntuFDS.******.**:*****](http://ubuntuFDS.******.**:*****)

it gives me a error.

If I use the port number in the "Administration URL:" I get this error

"Cannot connect to the Admin Server "http://blahblahblah"
The URL is not correct or the server is not running."

and if I leave the port number out it tells me

"Cannot logon because of an incorrect User ID,
Incorrect passowrd or Directory problem.

HttpException:
Response: HTTP/1.1. 404 Not Found
Status: 404
URL: http://yadayadayada:/admin-serv/authenticate"

I think the server is running, I have executed these commands:

start-slapd
start-admi

And I know the password is correct.

EDIT: Is it possible that this problem I am dealing with got something do with Java or Apache?


---

### Post by cariboo on 2008-09-30
I note at the bottom of the post you say you think the services are running, to make sure use the following commands:

```
ps ax | grep slapd
```

and

```
ps ax | grep admi
```

If you used the following commands to start the services:

> start-slapd
start-admi

Then your services may not be running, in Ubuntu all the service startup/shutdown scripts are in /etc/init.d
so to start the service you would type:

```
sudo /etc/init.d/slapd start
```

Jim

---

