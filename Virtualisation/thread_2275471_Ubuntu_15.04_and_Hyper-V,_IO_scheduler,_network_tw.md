---
title: "Ubuntu 15.04 and Hyper-V, IO scheduler, network tweaks and NTP timing question"
date: 2015-04-26
forum: Virtualisation
---

### Post by gijs007 on 2015-04-26
I'm using Ubuntu server 15.04 64 bit with Hyper-V generation 2 and have a few questions.

1. Which is the best IO scheduler to use? (The VM runs of a SSD) -I've read that noop and deadline are best for SSD's, are these still the best IO schedulers to use when the server runs in a VM?
I've ran: ```
cat /sys/block/sda/queue/scheduler
Which outputs: noop [deadline] cfq

```
Which scheduler is used and how can I change this?

2. I've ran ```
cat /sys/block/sda/queue/rotational
```
Which outputs 1, which means my SSD is detected as being a HDD. How can I fix this?

3. Do I need to install Hyper-V Linux Integration Services on my VM, or is this already done automatically?

4. I've noticed the following in my syslog:

```
Apr 23 22:53:04 vpn-france ntpdate[867]: step time server 91.189.94.4 offset -1.342616 sec
Apr 23 22:53:04 vpn-france systemd[1]: message repeated 6 times: [ Time has been changed]
...
Apr 23 22:56:49 vpn-france systemd[1]: message repeated 89 times: [ Time has been changed]
```

Someone suggested that I disable NTP updating in Ubuntu, but others suggest that I disable the time synchronization provided by Hyper-v.
What are the best practises for this case?

5. Are there any tweaks that can be done to reduce the ethernet (TCP and or UDP) latency, like disabling interrupt moderation on the network card?

---

### Post by firedefender1 on 2015-07-20
I don't know if you found any answers to your questions so here are some for reference.

1. The command shows that deadline is the active io scheduler.
Since the vm runs on an ssd I would use noop. noop does not really anything and lets other parts of the system handle io scheduling. Since the computer running the vm should have its own io scheduler should this do the scheduling.
You can change the io scheduler temporarly with ```
echo noop | sudo tee /sys/block/sda/queue/scheduler
```
This way you can just try out if the system responses any better.

2. Fixing this would't do anything I assume. The vm probably shows the drive as an hdd.

I don't know about the other ones, but the latency tends to be high on vm's since multiple users use the same connection. Even if you shapen your bandwidth, the other users will still cause laggs (if there are any to begin with)

---

