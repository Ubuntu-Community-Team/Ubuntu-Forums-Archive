---
title: "LXC: Can I guarantee a certain level of CPU resources to a given container"
date: 2013-03-21
forum: Virtualisation
---

### Post by davidparks21 on 2013-03-21
[COLOR=#333333][FONT=Ubuntu Beta]We're going to use LXC to multi-purpose our hardware while keeping the various applications easy to manage, develop, upgrade, and logically segregated.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]What I want to know is if I can **guarantee certain resources**, such as CPU, **to a certain container**.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
We have one process which will run in its own container that is a critical component of our application infrastructure. I'd like to dual purpose that box and let a non-critical, but resource-intensive, component (the worker node) reside in a separate container on the same hardware, but to be safe I want to guarantee that, when the critical component needs CPU, it gets it, at the expense of the non critical component.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
I'd rather do this at the container level rather than jury-rigging the application with nice or something like that because this configuration is only valid on one piece of hardware, on other boxes the worker node stands alone.[/FONT][/COLOR]

---

### Post by davidparks21 on 2013-03-23
After further research it seems that LXC uses Control Groups, and control groups would be used to limit the cpu or IO utilization per container. It seems that these settings can be made in the LXC config file directly, though I haven't yet found a resource that calls out the exact format I should use in this file.

---

