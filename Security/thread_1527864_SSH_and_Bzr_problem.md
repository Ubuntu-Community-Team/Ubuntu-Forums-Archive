---
title: "SSH and Bzr problem"
date: 2010-07-09
forum: Security
---

### Post by afrodeity on 2010-07-09
I can't ssh out or pull from bzr

get this message

```

proxy could not open connnection to sdf.lonestar.org:  Unauthorized
ssh_exchange_identification: Connection closed by remote host

```

If I printenv, there is no proxy setup. Network Proxy is off. I don't have an http proxy tunnel setup either, so not sure what is going on.

---

### Post by cariboo on 2010-07-09
This is a totally different problem from the op's, moved to a thread of it's own.

---

### Post by afrodeity on 2010-07-10
I suspect it has something to do with my NX client installation, Also uses port 22 and ssh, but not sure what is going on. Tried to reinstall the ssh server and it through up a lot of NX dependencies so in the process of investigating.

---

### Post by afrodeity on 2010-07-12
Problem solved - this stumped me to the point where I purged the sshserver and reinstalled it, removing nx in the process [(see here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6690391")). But this didn't solve my problem. I was still getting the proxy authentication problem. 

Printenv showed main proxy for the system off (I had a proxy during the 12 month period in which I was capped by my ISP), what was going on?

Then I started asking myself questions about ssh, how would one setup an ssh proxy anyway? Believe it or not I eventually recalled having a similar problem about a year back. But how was it setup and where were the config files?

ls -a in my home folder revealed an .ssh folder.

There in a file was a reference to proxychains with directions to a proxy server which had now decided to shutdown port 22, thus throwing up the error.

All this time, I had been ssh-ing seamlessly via a proxy, long after getting uncapped.

Proxychains a marvelous little creature that one can easily forget exists, didn't show up in synaptic when I did a search for "proxy", or somehow I must have not seen it. But problem solved, now all I need is a patch for the old brain.

---

