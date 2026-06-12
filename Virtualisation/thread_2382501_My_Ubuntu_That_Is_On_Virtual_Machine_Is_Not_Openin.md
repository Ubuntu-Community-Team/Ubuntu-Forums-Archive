---
title: "My Ubuntu That Is On Virtual Machine Is Not Opening"
date: 2018-01-14
forum: Virtualisation
---

### Post by joseph-hardrock on 2018-01-14
I wrote this command to terminal and pressed enter:
```

[COLOR=#ff0000]shutdown -r[/COLOR]

```


Terminal gave to me a time. I think it was almost one minute later. When I was surfing on the net, my VM closed suddenly as normal. But when the VM started , the VM said that(Actually, I can't remember well, because I closed the warning fastly):
An error occured on your CPU, if you are not in your virtual machine press Cancel to do not damage your hardware(or vice versa, I am not sure). If you are in VM then press OK. 
I pressed OK. After that VM started, but VM couldn't reach the VM starting scene. Every time VM starts VM said that:
Starting ...(When progress bar was full, it is repeated its starting process(What I mention is what I saw)). There are somethings that I can interact, but I don't know how to do:
 F2 to enter setup, F12 for Network Boot, ESC for Boot Menu.


What should I do?

---

### Post by DuckHook on 2018-01-15
It is impossible to help you with insufficient data.

[LIST=1]
[*]Before anything else, are you backed up? Not just VMs but other important data?
[*]What VM software are you using?
[*]What version of VM software are you using?
[*]What flavour and version of *buntu are you using on both host and guests?
[*]Is your host fully updated? If so, what kernel is it running?
[/LIST]
I may not be able to give you much direction, but any attempt to help you by any other forum members requires at least this minimal information.

---

### Post by joseph-hardrock on 2018-01-15
> **DuckHook said:**
> It is impossible to help you with insufficient data.

[LIST=1]
[*]Before anything else, are you backed up? Not just VMs but other important data? 
[*]What VM software are you using? 
[*]What version of VM software are you using? 
[*]What flavour and version of *buntu are you using on both host and guests? 
[*]Is your host fully updated? If so, what kernel is it running? 
[/LIST]
I may not be able to give you much direction, but any attempt to help you by any other forum members requires at least this minimal information.

I think I detect the reason of my problem. I made a partition before my boot partition. Therefore, my system can't make the boot process.  How can I delete the partition that I made? Is it possible from my choices?
My choices:
F2 to enter setup, F12 for Network Boot, ESC for Boot Menu.

---

