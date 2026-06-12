---
title: "[help] netplan config file order"
date: 2022-12-19
forum: Server Platforms
---

### Post by laxebisu on 2022-12-19
Hi all, I need a little help understanding the order in which the netplan config files are applied.
**Scenario:**
Let's say I have two config files, A and B.
Config files A and B both set the same ethernet interfaces in different ways. (different auth methods...)
Config A file name is : 01-config.yaml
Config B file name is : 99-config.yaml

**Questions:**
1. Which config file will be applied?
2. Would config B work as a fallback if config A didn't work? Or the other way around? Or neither? :confused:
3. I want to set a fallback config file in case the existing one(A) fails. Is that possible?

Thanks &#55357;&#56911;

---

### Post by MAFoElffen on 2022-12-19
00 is read first. 99 is read last. (Alpha numeric sort order)

Last out, if it resets anything, that will be what is applied.

---

### Post by TheFu on 2022-12-19
I name mine so that each interface has their own YAML file.
So, 
enp3s0-br0-static-config.yaml
enp7s0f0-SAN-static-config.yaml
enp7s0f1-mgnt-static-config.yaml
enp8s0f0-red-static-config.yaml

I don't use numbers, since they aren't related and order doesn't matter.

---

### Post by volkswagner on 2022-12-19
Perhaps offer a description of what you'd like to accomplish.

It's possible using two .yaml files for the same interface
is not the best way to offer a "failback" or redundancy?

Is this for different pppoe internet providers or WiFi SSIDs, or something else?
Do you only care if this "choice" is made during boot, or do you want to check
periodically throughout the day to verify your connection is working?

---

### Post by ian-weisser on 2022-12-19
Same question asked in AskUbuntu: [https://askubuntu.com/questions/1446282/netplan-file-order](https://askubuntu.com/questions/1446282/netplan-file-order)

---

### Post by laxebisu on 2022-12-19
Hi all, thank you for your reply. They all are very appreciated.

---

### Post by laxebisu on 2022-12-19
> **volkswagner said:**
> Perhaps offer a description of what you'd like to accomplish.


It's possible using two .yaml files for the same interface
is not the best way to offer a "failback" or redundancy?


Is this for different pppoe internet providers or WiFi SSIDs, or something else?
Do you only care if this "choice" is made during boot, or do you want to check
periodically throughout the day to verify your connection is working?


To give a bit of context, I'm working on an automated solution, and all the devices will have a pre-configured config for netplan(config A), which is temporary and will only work for an undefined small period.
So what I want to accomplish is to inject a new config file for all those devices while the device still has an internet connection. The new config(B) file would be set by puppet.
I know that I could simply remove config A and let B take care of the network settings. However, some users might have their own config on config A; therefore, if that's the case, I want to let it there untouched. If it still works, then good if not, the config B is there as a fallback.
Btw both configs are configuring IEEE 802.1x. The main diff between them would be the auth method values, different certs, and keys.. (unless the users have tweaked it for their own needs)


> **ian-weisser said:**
> Same question asked in AskUbuntu: [https://askubuntu.com/questions/1446282/netplan-file-order](https://askubuntu.com/questions/1446282/netplan-file-order)

 Thank you for your excellent explanation; I marked your answer as the solution in the link above. However, I am still figuring out how I can achieve what I described above to volkswagner.

---

### Post by TheFu on 2022-12-19
You can put 50 files in that directory. The ones that don't end in yaml will be ignored.  Don't know if this helps or not.

Puppet?  I'm so sorry.  Sometimes the solution is worse than the problem it is supposed to solve. ;)

---

### Post by laxebisu on 2022-12-19
> **TheFu said:**
> You can put 50 files in that directory. The ones that don't end in yaml will be ignored.  Don't know if this helps or not.

Yeah, that kind of does; it gives me some hackish ideas not ideal tho. Weirdly enough, I can achieve what I want in network manager by setting the priority for each connection.

> **TheFu said:**
>  Puppet? I'm so sorry. Sometimes the solution is worse than the problem it is supposed to solve. ;)
lol :cry:

---

### Post by TheFu on 2022-12-19
Well, why not use nmcli, if that's a better answer?
Also, you can still specify the metric for any connection, which is a way to provide different priorities for different interfaces and routes. Those work in netplan too.

---

