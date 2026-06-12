---
title: "Terminal session timeout"
date: 2011-02-11
forum: Server Platforms
---

### Post by tonkyman on 2011-02-11
I have several Ubuntu 8.04 servers. One of them will time out my SSH terminal session in 10 or 15 minutes. None of my other servers do this and they are all setup the same way. Is there a way to stop it from timing out my sessions??

Thanks,
Tony

---

### Post by Joeb454 on 2011-02-11
Try creating the file **.ssh/config** and putting something like this in

```

host tatooine
	Hostname 			myserver.com
	User	 			myuser
	Port				1234
        ServerAliveCountMax		30
        ServerAliveInterval		120

```

The last 2 are the most important to note, they determine how long the ssh client should keep the connection open.

---

### Post by tonkyman on 2011-02-11
> **Joeb454 said:**
> Try creating the file **.ssh/config** and putting something like this in

```

host tatooine
	Hostname 			myserver.com
	User	 			myuser
	Port				1234
        ServerAliveCountMax		30
        ServerAliveInterval		120

```

The last 2 are the most important to note, they determine how long the ssh client should keep the connection open.

I'm under the impression that the above combination will keep the connection active for 1 hour (30 X 120 seconds) is this correct?

Also it appears that there is a global setting for ssh located in the /etc/ssh/ssh_config file. I added the keep alive numbers you mentioned above to that file and restarted ssh (/etc/init.d/ssh restart) we'll see if that works.

Thanks for your help.

---

### Post by tonkyman on 2011-02-11
Ok, that didn't fix it..... any more ideas??

Tony

---

### Post by tonkyman on 2011-02-17
Any one have any more ideas?

---

### Post by RHAnthony on 2012-10-08
Looking at the same problem here.  I have a feeling it's something on the server side... still haven't found anything that's helped.

---

### Post by markbl on 2012-10-08
> **RHAnthony said:**
> Looking at the same problem here.  I have a feeling it's something on the server side... still haven't found anything that's helped.
Note you are in a very old thread.

95% of the time this ssh "hanging" problem is due to the NAT table overflowing in a router, usually your cheap home router. You fix it for yourself by setting ServerAliveInterval in your ~/ssh/config, or set ClientAliveInterval in your sshd server to fix it for everybody.

---

