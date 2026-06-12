---
title: "Ubuntu 20.04 IP Link Virtual Function command"
date: 2021-05-18
forum: Virtualisation
---

### Post by paullautier on 2021-05-18
Hi, I am running KVM on Ubuntu 20.04 & using  SR-IOV with an Intel x520 and have an issue were i trying to set Virtual  fuctions Spoof checking off & trust on.
 I should be able to use the  command "IP link set PF VF  NUM " to change these setting but VF is not  seen as an option. Is this function enabled on a specific Kernel  Version? 
i’m curently running 5.4.0 or has this funtion been moved to  NetPlan, I don’t seem to be able to find any Documentation either way.

 
Thanks in advanced.

---

### Post by MAFoElffen on 2021-06-10
> **paullautier said:**
> 
 I should be able to use the  command "IP link set PF VF  NUM " to change these setting but VF is not  seen as an option. 
You didn't type it as posted did you? You know that Linux is case sensitive... so "VF" does not exist, but "vf" does... right?
```

ip link set { DEVICE | group GROUP }
               [ vf NUM [ mac LLADDR ]
                        [ VFVLAN-LIST ]
                        [ rate TXRATE ]
                        [ max_tx_rate TXRATE ]
                        [ min_tx_rate TXRATE ]
                        [ spoofchk { on | off } ]
                        [ query_rss { on | off } ]
                        [ state { auto | enable | disable } ]
                        [ trust { on | off } ]
                        [ node_guid eui64 ]
                        [ port_guid eui64 ] ]    }
```
For example:
```

ip link set ens801f0 vf 0 trust on
ip link set ens801f0 vf 0 spoofchk off
```
Correct me if I'm mistaken... But just an observation.

---

### Post by paullautier on 2021-06-26
Hi MAFoElffen; 
Correct in the post I used captials but wasn't when using the command in Linux terminal. I did get it working though I miss understood the syntax of the command
I was putting the physical name and number of the virtual function so like  &#8220;ip link set enps50 vf enps50v3&#8221;   It should be ip link set enps50 vf 3 Not my best moment for sure felt like a bit of an idiot once i realised it [SIZE=3][IMG]https://forum.level1techs.com/images/emoji/twitter/roll_eyes.png?v=9[/IMG][/SIZE] not sure why I thought it was that in the first place the documentation is quite clear.

---

### Post by MAFoElffen on 2021-06-26
I understand. LOL. Good that it's working for you now.

---

