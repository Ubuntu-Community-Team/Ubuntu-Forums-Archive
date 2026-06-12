---
title: "hostname or servername"
date: 2013-08-21
forum: Server Platforms
---

### Post by Rakesh_vijayan on 2013-08-21
alice@ec2-23-22-230-24.compute-1.amazonaws.com
will any body discribe the above host discription for my knowledge

---

### Post by CharlesA on 2013-08-21
It's either an email address (unlikely) or a way to log into a machine remotely.

---

### Post by bab1 on 2013-08-21
> **CharlesA said:**
> It's either an email address (unlikely) or a way to log into a machine remotely.

Actually it's an example from [**_[COLOR="#0000FF"]this article[/COLOR]_**]("http://xmodulo.com/2013/01/how-to-specify-private-key-file-in-ssh.html").  :-)

The example appears to be the prompt of a host that the user user in the example ssh'd to.  So to answer the OP's question, the prompt is broken down as follows:```

[COLOR="#008000"]alice[/COLOR] = the user
@ = at the host
[COLOR="#800080"]ec2-23-22-230-24.compute-1[/COLOR] = hostname
. = separator 
[COLOR="#FF0000"]amazonaws.com[/COLOR] = DNS domain name

[COLOR="#800080"]ec2-23-22-230-24.compute-1[/COLOR].[COLOR="#FF0000"]amazonaws.com[/COLOR] = FQDN (Fully Qualified Domain Name
 
```

---

