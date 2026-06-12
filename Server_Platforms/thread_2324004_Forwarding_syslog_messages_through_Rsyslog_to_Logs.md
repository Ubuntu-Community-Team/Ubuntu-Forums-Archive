---
title: "Forwarding syslog messages through Rsyslog to Logstash"
date: 2016-05-10
forum: Server Platforms
---

### Post by brayn2 on 2016-05-10
Hi,

I have set up an [E.L.K Stack]("https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04") for capturing and visualizing Syslogs and NETFlow, but there is one slight problem.

As you know most syslogs and flows are sent by default through UDP port 514, which is a privileged port. The problem is that Logstash can not listen to any privileged ports(<1024) unless ran as root which we want to avoid doing.

I thought of setting up a Rsyslog server that listens to UDP port 514 and redirects anything that is sent to it to a higher port on lets say port 5140 to Logstash which it can listen to as it is not a privileged port.

Would anyone be able to assist me in this? Would appreciate it. I can post my current configuration if necessary.

---

### Post by Habitual on 2016-05-10
Hell yes, I'll help you.
ELK is the bomb and I think every SysAdmin needs it.
I too followed [E.L.K Stack]("https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04") to get ours up and running with Kibana4

I detoured from rsyslog forwarder agent to logstash-forwarder when our Kibana 3 took off with Raul, our pool attendant.
With Kibana4 I utilized logstash-forwarder     Version: 0.4.0

What can I help you with?

I haz recipes, so I hope your comfy with installing stuff, you should be ok if you have a working kibana dashboard.

Subscribed with interest...

References:
 [https://www.elastic.co/blog/logstash-forwarder-0-4-0-released](https://www.elastic.co/blog/logstash-forwarder-0-4-0-released)
[https://www.elastic.co/guide/en/logstash/current/deploying-and-scaling.html#deploying-and-scaling](https://www.elastic.co/guide/en/logstash/current/deploying-and-scaling.html#deploying-and-scaling)
[https://www.elastic.co/guide/en/logstash/current/multiple-input-output-plugins.html#multiple-input-output-plugins](https://www.elastic.co/guide/en/logstash/current/multiple-input-output-plugins.html#multiple-input-output-plugins)
[https://www.elastic.co/guide/en/logstash/current/input-plugins.html](https://www.elastic.co/guide/en/logstash/current/input-plugins.html)

---

### Post by brayn2 on 2016-05-10
> **Habitual said:**
> Hell yes, I'll help you.
ELK is the bomb and I think every SysAdmin needs it.
I too followed [E.L.K Stack]("https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04") to get ours up and running with Kibana4

I detoured from rsyslog forwarder agent to logstash-forwarder when our Kibana 3 took off with Raul, our pool attendant.
With Kibana4 I utilized logstash-forwarder     Version: 0.4.0

What can I help you with?

I haz recipes, so I hope your comfy with installing stuff, you should be ok if you have a working kibana dashboard.

Subscribed with interest...

Great to see a reply like this! I'll try and explain my situations and what I am working with.

I need to capture syslogs and NETFlow from mainly routers and switches(Juniper, Cisco & Huawei) to visualize them in Kibana 4 which I got working just fine, the thing is that during the implementation/deployment I can not have Logstash running as root so it is able to listen to privileged ports to receive its information directly from the devices.

Started looking for solutions and noticed that many out there use a workaround for it like [here]("http://logz.io/blog/deploy-elk-production/") where it recommends to "*place a Redis server in front of your Logstash machine that will be the entry point for all log events that are shipped to your system.*" I mentioned this to the person in charge of this project that I'm working on and he said that's something we can do.

We will have two servers which of one will be the ELK server and the other a Rsyslog server. We want all syslogs from routers and switches to be sent to the Rsyslog server on port 514 and it being redirected on a higher port to the ELK server for Logstash to play with. If there's any other solutions besides a redirection or different service, please feel free to tell me so.

I'm quite new to all of this, but am very interested in it. What do you recommend me to do? Are there any real risks having Logstash running as root?

---

### Post by Habitual on 2016-05-10
See [https://github.com/elastic/logstash-forwarder/issues/394](https://github.com/elastic/logstash-forwarder/issues/394) for possible non-root user options.
Combine with port 5000 and it seems workable, to me any way.

Seems to me, you just want to forward the rsyslog-server logs to ELK?

---

