---
title: "/etc/network/interfaces"
date: 2011-05-26
forum: Server Platforms
---

### Post by wake5269 on 2011-05-26
When i type vi /etc/network/interfaces, i get a blank screen with blue dashes on the left side.  "/etc/network/interfaces/" [New DIRECTORY].  I am running Ubuntu 11.04 server and am trying to set static ip.  I found a work around but why is this happening?

---

### Post by arrrghhh on 2011-05-26
I think you need to use sudo...

Also, what is the command you entered verbatim?  If you did
```
vi /etc/network/interfaces/
```
That would be an issue - the trailing slash indicates interfaces is a directory, not a file...
```
vi /etc/network/interfaces
```
Should work.

---

### Post by wake5269 on 2011-05-26
i manually configured the ip address through ifconfig eth0 192.168.1.254 netmask 255.255.255.0

and now when i type command sudo vi /etc/network/interfaces  I get found a swap file by the name "/var/tmp/interfaces.swp"

reboot and try again and same results
i can change ip address temp but at reboot it goes back to dhcp.

---

### Post by arrrghhh on 2011-05-26
> **wake5269 said:**
> i manually configured the ip address through ifconfig eth0 192.168.1.254 netmask 255.255.255.0

and now when i type command sudo vi /etc/network/interfaces  I get found a swap file by the name "/var/tmp/interfaces.swp"

reboot and try again and same results
i can change ip address temp but at reboot it goes back to dhcp.

Edit - Wait, scratch that.  Have you used vi before?  I don't use it much, honestly not very good with it - but I googled that real quick, and found that it's related to a recovery tool built into vi.  If you don't know how to use vi, use nano - it's much easier, trust me.

---

### Post by wake5269 on 2011-05-26
tried nano, and i get blank page and it says new file at bottom

---

### Post by arrrghhh on 2011-05-26
> **wake5269 said:**
> tried nano, and i get blank page and it says new file at bottom

Uhhh...

What's the output of:
```
ls -lh /etc/network
```
Also, are you giving me the whole story or are you leaving something out - like did you perhaps accidentally wipe out this file and save it...?

Either way, you can just recreate it.  There's not much in the file, if you're putting a static IP on the box, then you know what need to go in the file right?

---

### Post by wake5269 on 2011-05-26
> **arrrghhh said:**
> Uhhh...

What's the output of:
```
ls -lh /etc/network
```Also, are you giving me the whole story or are you leaving something out - like did you perhaps accidentally wipe out this file and save it...?

Either way, you can just recreate it.  There's not much in the file, if you're putting a static IP on the box, then you know what need to go in the file right?

this is a clean install, just started and installed the os. 

output is 
ls:cannot access /ect/network: no such file or directory

---

### Post by wake5269 on 2011-05-26
it seems the entire ect directory does not exist
did i miss something in the install?

---

### Post by volkswagner on 2011-05-26
> **wake5269 said:**
> this is a clean install, just started and installed the os. 

output is 
ls:cannot access /[COLOR="Blue"]ect[/COLOR]/network: no such file or directory


You have a typo:

As the command requested is for /etc not /ect

---

### Post by wake5269 on 2011-05-26
i figured it out, the admin utilities are not installed. thanks for your time and help

---

### Post by wlraider70 on 2011-05-26
> **wake5269 said:**
> this is a clean install, just started and installed the os. 

output is 
ls:cannot access [COLOR="Red"]/ect/network[/COLOR]: no such file or directory



You wrote ect not etc did you input it correctly?

---

### Post by arrrghhh on 2011-05-26
> **wake5269 said:**
> i figured it out, the admin utilities are not installed. thanks for your time and help

Admin utilities?  What are you talking about?

As many others have pointed out, you didn't copy&paste my code and made a typo.  There is no such thing as /ect... did you even double-check my post when you got the error!?!?  Oy ve...

---

### Post by wake5269 on 2011-05-26
i typed etc in the command
i am on my laptop next to the server which is on a diff monitor and keyboard

---

### Post by arrrghhh on 2011-05-26
> **wake5269 said:**
> i typed etc in the command
i am on my laptop next to the server which is on a diff monitor and keyboard

Uhm... now you're just lying.  You said "ls:cannot access /ect/network: no such file or directory" - pretty sure you typed it in wrong on the server.

So what are you talking about "admin tools"?

---

### Post by wake5269 on 2011-05-26
> **arrrghhh said:**
> Uhm... now you're just lying.  You said "ls:cannot access /ect/network: no such file or directory" - pretty sure you typed it in wrong on the server.

So what are you talking about "admin tools"?

aptitude says administrative tools is not installed

---

### Post by wake5269 on 2011-05-26
> **arrrghhh said:**
> Uhm... now you're just lying.  You said "ls:cannot access /ect/network: no such file or directory" - pretty sure you typed it in wrong on the server.

So what are you talking about "admin tools"?
reinstalled os and added admin tools and now it is working

---

### Post by wake5269 on 2011-05-26
> **volkswagner said:**
> You have a typo:

As the command requested is for /etc not /ect
i know i wrote a typo here but i did not put the command as a typo i promise, the entire /etc/ directory was not present until i did the reinstall. it is up and working like a charm now

---

### Post by arrrghhh on 2011-05-27
> **wake5269 said:**
> i know i wrote a typo here but i did not put the command as a typo i promise, the entire /etc/ directory was not present until i did the reinstall. it is up and working like a charm now

You would've had bigger problems than networking if all of /etc were missing.  Glad it's fixed... You must've really FUBAR'd something if a complete reinstall is the solution lol.  Admin Tools or whatever you installed was entirely unnecessary.

---

### Post by koenn on 2011-05-27
> **arrrghhh said:**
> Edit - Wait, scratch that.  ...  but I googled that real quick, and found that it's related to a recovery tool built into vi.  

yes, it's a temporary file made by vi.
The OP was probably editing the file, quit vi without saving, and lost the file in the process - a hard reboot maybe ?

just renaming interfaces.swp to interfaces would have recovered the file.

---

