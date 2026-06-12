---
title: "Not able to ssh into VM machines"
date: 2017-06-10
forum: Virtualisation
---

### Post by LastDino on 2017-06-10
This is the tutorial I'm following atm to create virtual lab of sort

[http://www.brianlinkletter.com/how-to-use-virtualbox-to-emulate-a-network/](http://www.brianlinkletter.com/how-to-use-virtualbox-to-emulate-a-network/)

I'm stuck at this step 

"Connect to each virtual machine"

If I type into terminal of host OS and try to ssh into VM machines running 
```
ssh -l owl -p 14501 localhost



```
I get this error


```
ssh_exchange_identification: Connection closed by remote host

```

As you can see, port forwarding settings for PC-1 machine in VM to which I'm trying to connect is

[ATTACH=CONFIG]275565[/ATTACH]


Note: Error stays the same with both "gufw" enabled or disabled on host machine. 

I'm not entirely sure what is going wrong or what to look into, can anyone shed some light on this?

New to networking, so be patient with me guys :D

Thank if anyone is willing to spend some time here with silly me

---

### Post by LastDino on 2017-06-10
solved with installing open ssh server on all the vms to be in network

this was not in guide, just tried something and it was probably what lacking

---

