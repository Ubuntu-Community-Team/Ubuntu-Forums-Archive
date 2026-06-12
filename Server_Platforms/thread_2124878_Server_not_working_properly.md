---
title: "Server not working properly"
date: 2013-03-12
forum: Server Platforms
---

### Post by kirshnam on 2013-03-12
***** Post Updated by mod *****
*(slightly edited language for better explanation, hope that's what OP means)*

My server works okay at startup. I can access the webmin cpanel from another PC using server's IP and I can also connect to it using Putty but...

[indent]1.When server goes down - Server is physically (locally) working but I can't get the webpage on another PC using its IP.

2. Hardware : AMD Atholon 2 processer and Asus motherboard

3. I am just running the **Webmin Cpanel** for learning

4. It goes down all by itself, after a few minutes of working fine.

5. After reboot it works fine again but same problem happens again and again[/indent]

Any help would be appreciated!
---------------------------------------------------------

Hi,
I got frequently my server getting down after reboot only it will working, I am using 11.04 and upgraded to 12.04 but same problem is exit any one help me to fix 

Thanks

---

### Post by varunendra on 2013-03-12
*Thread moved to **Server Platforms**.*

---

### Post by kirshnam on 2013-03-13
Varun Please guide me how fix it. i am new in linux server

Thanks

---

### Post by varunendra on 2013-03-13
> **kirshnam said:**
> Varun Please guide me how fix it. i am new in linux server

Thanks
I am not an expert in servers. I moved your thread here so that you may get help from those who are experts.

But your original post gives no information to start with.

Explain your problem in detail. Provide as much information as you can. Some of the useful ones would be-
[LIST=1]
[*]What do you mean by "goes down"? Does it totally freeze or what?
[*]What is the hardware configuration of the server?
[*]What do you use it for?
[*]When does it 'go down'? On some particular workload or all by itself without doing anything?
[/LIST]
Plus whatever you can tell us about the problem.

With proper details and description of the problem, maybe right people will take interest and pose here.

---

### Post by kirshnam on 2013-03-14
Thanks for your information varun
My server running good when start if put the Ip address i got the webmin cpanel and if I connect the pc using putty all are working fine but  
1.When down. Server system will working but if i use the server ip in another system i am not get the webpage
2. and I am using AMD Atholon 2 processer and asus motherboard
3.I am just running the webmin cpanel for learning
4.Its down without doing anything.
5.after reboot it working fine again but same problem pressist again and again

---

### Post by kirshnam on 2013-03-15
Hi,
[COLOR=#000000]My server running good when start if put the Ip address in another pc i got the webmin cpanel and if I connect the pc using putty its working fine but 
[/COLOR]
[COLOR=#000000]1.When was server down. Server pc will working but if i use the server ip in another system i am not get the webpage
[/COLOR]
[COLOR=#000000]2. and I am using AMD Atholon 2 processer and asus motherboard
[/COLOR]
[COLOR=#000000]3.I am just running the webmin cpanel for learning
[/COLOR]
[COLOR=#000000]4.Its down without doing anything.
[/COLOR]
[COLOR=#000000]5.after reboot it working fine again but same problem pressist again and again
Any one help me to fix the problem

Thanks[/COLOR]

---

### Post by steeldriver on 2013-03-15
what exactly is "down" - the whole machine (can you ping it?) or just the web server?

---

### Post by varunendra on 2013-03-15
Duplicate threads merged.

**PS:**
Edited the first post to add relevant info.

---

### Post by kirshnam on 2013-03-17
Web server is not working

---

### Post by matt_symes on 2013-03-17
Hi

When the web server goes down, log in via putty or get a terminal locally on the PC, and type

```
ps aux | grep apache
```

Post the results back here.

Kind regards

---

### Post by kirshnam on 2013-03-17
When web server down  means i cant connect the server using putty also and i try to ping the ip i got )destination host unreachable)
Thanks

---

### Post by matt_symes on 2013-03-17
Hi

Ahh. So it's not just the web server but the server itself that goes down.

You want to look at the logs on the server to see why.

I would look at

```

/var/log/syslog
/var/log/kern.log
```

Zip them up and post them as attachments here and we'll take a look for you.

Kind regards

---

