---
title: "Closed architecture for servers ??"
date: 2016-01-21
forum: Server Platforms
---

### Post by soamz on 2016-01-21
I just a service whose application is based on UbuntuServer. 
And he says, it wont work on closed architecture like Dell, IBM, HP servers, etc.
He asked to assemble a CPU yourself and install.

But I dont understand, why he says it wont work on closed architecture. 
What could be the reason ??
Is it because, we have to do RAID config in the servers before use ?

Or can we completely remove RAID control or switch it off, so the server simply works as a normal CPU and then we can install ?

Im just concerned as I already bought a Dell server for this and now he is denying to use it :(

---

### Post by nerdtron on 2016-01-21
> **soamz said:**
> 
He asked to assemble a CPU yourself and install.

  

Is he the one going to assemble the server and install Ubuntu or you're the one doing it? If he's going to assemble the server from pieces how are the parts like the RAID controller card? 

Ubuntu runs well on Dell, HP, IBM servers (Intel and AMD CPUs on most cases I've seen). What model did you bought?

---

### Post by darkod on 2016-01-21
That is a question for your developer, not for us. If he says his application cannot run on branded server he has to say why...

I do not see the RAID to be a problem but it is true that it is difficult if not impossible to "switch off" raid on branded servers. They are designed under the assumption you will use the raid and in most cases the disks are connected to the card/controller. If you switch it off, how will the system detect and use the disks?

For some models you could flash the controller to IT mode, which means no raid capability only a direct pass through of the disks. You can search on the internet if you have option to do that for your model. But even if you manage to do that, your developer still has to explain is it the raid bothering him or what...

---

### Post by soamz on 2016-01-21
> **darkod said:**
> That is a question for your developer, not for us. If he says his application cannot run on branded server he has to say why...

I do not see the RAID to be a problem but it is true that it is difficult if not impossible to "switch off" raid on branded servers. They are designed under the assumption you will use the raid and in most cases the disks are connected to the card/controller. If you switch it off, how will the system detect and use the disks?

For some models you could flash the controller to IT mode, which means no raid capability only a direct pass through of the disks. You can search on the internet if you have option to do that for your model. But even if you manage to do that, your developer still has to explain is it the raid bothering him or what...


Yes he says, raid bothering

---

