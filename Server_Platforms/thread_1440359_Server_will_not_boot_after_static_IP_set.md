---
title: "Server will not boot after static IP set"
date: 2010-03-27
forum: Server Platforms
---

### Post by 4msilva on 2010-03-27
I just installed sever 9.1 with webmin. Everything was working great, untill it tried to set it to a static ip address. I tried to do it thur webmin. after it rebooted the server and it now stops at this line 
 
init: network main process (618) terminated with status 1
 
Any idea what I did wrong? Or how I can fix this?

---

### Post by spynappels on 2010-03-27
Webmin does not always work correctly with Debian/Ubuntu.

If you have direct console access, edit the /etc/network/interfaces to give you a static IP.

---

### Post by datajock on 2010-03-27
You didn't really give detail as to what you mean by 'stops'. Does this drop you to a prompt and you can perform the edit as recommended in post #2 or do you not have any control to do anything?

I would suggest that if you can't even get to a prompt, that you could always boot from a Desktop Live CD without installing it, then just mount the disk and edit the file that way.

Hope that helps,
DJ

---

### Post by spynappels on 2010-03-27
Generally, in a local terminal, if the networking service fails to start, you will still be able to log in and edit files etc. You should just get an error message on the screen as each service starts.

---

### Post by 4msilva on 2010-03-28
I only gives me a _, I can not do any thing at all. no commands work.

---

### Post by 4msilva on 2010-03-28
I tried to use th boot disk and wen into rescue server. I tried to access the /etc/network/interfaces. I was able to modify it but not sure what should be inthere.

---

### Post by kevin11951 on 2010-03-29
> **4msilva said:**
> I tried to use th boot disk and wen into rescue server. I tried to access the /etc/network/interfaces. I was able to modify it but not sure what should be inthere.

this is just an example, but it should get you on your way:

```
auto eth0
iface eth0 inet static
address 192.168.1.123
netmask 255.255.255.0
gateway 192.168.1.1
```

Things you may need to change are:
change "eth0" to your interfaces name (you can find it by typing "ifconfig" at a command prompt).
Address, and gateway obviously.  and thats it... everything else should fit

---

