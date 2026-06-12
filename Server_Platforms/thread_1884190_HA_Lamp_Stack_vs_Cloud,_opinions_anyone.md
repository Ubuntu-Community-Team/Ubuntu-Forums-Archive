---
title: "HA Lamp Stack vs Cloud, opinions anyone?"
date: 2011-11-20
forum: Server Platforms
---

### Post by tethlah on 2011-11-20
So I'm starting a web hosting business, and I've worked as a server admin before.  I was running (6 years ago) 2 lamps that regularly rsync'ed to each other and I would switch the interfaces file if one went down (manually after being alerted by email).  After some research these days I see how utterly stupid that is, so needless to say I'm not doing that again.

Now I'm setting up my own system, I have 2 Fortigate 60's, 2 Netgear 48p switches, and 2 Dell Poweredge 1950s.  I'm running the FWs HA to my switches (with failover) and then going to my servers.  I'm configuring the servers with a 20g OS partition and a 100g data partition that drdb will replicate between the two servers that my lamp stack will reside on (along with home folders for ftp user purposes).  As I'm doing this, I keep hearing people say to set up a cloud, but after researching VMWare (I work in a datacenter, it's what we use here), I decided not to.

However, I've just been turned on to OpenStack.  I have limited experience using cloud services, but I'm turned on by the fact that I can add more servers through virtualization and simply upgrade hardware to add resources.  2 or 3 nodes can easily give me a lamp box, sql server, and mail server and even test servers if needed.  However, I'm confused as to if this is the best option.

I know that with an HA Lamp stack, the two servers are redundant and with my redundancies all the way to the access switch in the datacenter I shouldn't ever experience downtime.  Are VMs going to give that same security?  Say I have 2 nodes and one goes down, will the other pick up right then or will the VM be crippled by half the resources suddenly disappearing?  Will going with VM be as available and redundant as having two machines running in HA?

Thanks in advance for the help.  Most of the server admin stuff I've done is all self taught and through trial and error, I guess I want to get this one done right the first time because now it's my reputation and clients on the line lol.

---

### Post by tethlah on 2011-11-21
Well I have 100 views on this thread.  Am I posting this in the wrong place?  Anyone have any opinions on this?

---

### Post by tethlah on 2011-11-25
So no one has used either high availability ubuntu servers or cloud for their stuff?  There has to be someone on this "community" with something to say about this...

---

### Post by Habitual on 2011-11-26
Although I am interested in this topic, I can only suggest checking [here]("http://www.unix.com/virtualization-cloud-computing/"), or possibly [here]("http://www.webhostingtalk.com/forumdisplay.php?f=156") and finally [https://forums.aws.amazon.com/forum.jspa?forumID=30](https://forums.aws.amazon.com/forum.jspa?forumID=30)

---

### Post by arjuntank on 2011-11-26
tethlah,

I was researching the same. This page can help: [http://openstack.org/projects/storage/](http://openstack.org/projects/storage/)

Let me know what you think. So far, I'm really liking what openstack can do.

---

