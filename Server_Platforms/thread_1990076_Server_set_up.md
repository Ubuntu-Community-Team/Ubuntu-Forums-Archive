---
title: "Server set up"
date: 2012-05-29
forum: Server Platforms
---

### Post by ATAQ on 2012-05-29
Hey, I am a little confused about cloud computing, is cloud computing basically clustering resources together, combining all resources in the pool together for any applications or is it mainly for web applications?
I want to set up a cluster, so I am thinking of migrating back to Ubuntu and installing the cloud server on my sun servers. Any info would be great.

---

### Post by spynappels on 2012-05-29
Hi ATAQ,

What are you wanting the cluster to do?

"Cloud" as used by Amazon EC2, Ubuntu Cloud Server etc generally is used where capacity needs to be ramped up to cope with spikes in load. This can be where a large amount of data needs to be processed quickly, in this case additional nodes can be spun up to do the processing and shut down when the task is finished. It can also be used when a website suddenly experiences a rise in traffic, additional webservers can be spun up and added to a load-balancer pool when traffic reaches a certain limit.

It really depends on what you need it to do.

---

### Post by ATAQ on 2012-05-29
Thanks for the reply, well I have a web server but I also want it so that I can basically pool all my computers into one, because basically what I have is 4 relatively decent machines and I want to combine them as one so I will have a quick system, because at times my server slows down due to demand both local and through the internet. and my main desktop is a little laggy at times with certain applications, would using a cloud server help me or should I be thinking along the lines of something else?

---

### Post by spynappels on 2012-05-29
That's not what the cloud will do unfortunately.

There are ways of doing this, but they wouldn't work well on consumer grade hardware.

The way these things work in the cloud is that there is a relatively small server which receives a web request or a block of data needing processing. It looks at what resources are available and spins up a new instance if required. It then sends the request or data to this new instance for processing with a request to send the result back to the initial server. When the instance is finished with the task, and there are no further tasks for it to work on, it will basically shut down.

As the instance is only up for the duration of the task, and all resources are dedicated to the task, it works out cheaper to do this where you are charged by the minute for the instances which are running.

---

### Post by ATAQ on 2012-05-29
Ok I get you,
What would the general procedure be to set up a cluster using all of my machines?
I have a Sun server with 6 Gigabit ethernet ports and 3 other machines.
Would I be able to cluster them and pool all the resources together ?

---

### Post by sj1410 on 2012-05-29
[http://www.techpage3.com/2010/03/understanding-cloud-computing.html](http://www.techpage3.com/2010/03/understanding-cloud-computing.html)

---

