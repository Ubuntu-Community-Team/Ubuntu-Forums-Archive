---
title: "ssh scp help"
date: 2009-08-29
forum: Security
---

### Post by shanep-server on 2009-08-29
I have a server and a laptop connected behind my wireless router.

Server - ubuntu hardy desktop
laptop - ubuntu jaunty desktop

On the laptop i ssh into server via termial
once the connection is established I tried to move a file from the desktop on laptop called puppy.iso to the desktop on my server.

I have tried scp /home/shane/Desktop/puppy.iso user@ip:/home/shane/Desktop/ 

user@ip is obviously my actual user name an ip address of the server

it will prompt me for my password after entered it says no such file /home/shane/Desktop/puppy.iso

i've tried quite a few variations an have gotten no where. If anyone can help that would b great.

---

### Post by SoftwareExplorer on 2009-08-29
What do you get if you do ```
ls /home/shane/Desktop
```?

---

### Post by scorp123 on 2009-08-29
> **shanep-server said:**
>  it will prompt me for my password after entered it says no such file /home/shane/Desktop/puppy.iso Why not simply verify if the file is really there?
```
ls -al /home/shane/Desktop/puppy.iso
```

---

### Post by shanep-server on 2009-08-29
ls /home/shane/Desktop showed the file puppy.iso

ls -al /home/shane/Desktop/puppy.iso showed the following

-rw-r--r-- 1 shane shane 105107456 2009-08-23 16:03 /home/shane/Desktop/puppy.iso

---

### Post by DaithiF on 2009-08-29
> **shanep-server said:**
> 
On the laptop i ssh into server via termial
once the connection is established I tried to move a file from the desktop on laptop called puppy.iso to the desktop on my server.

I have tried scp /home/shane/Desktop/puppy.iso user@ip:/home/shane/Desktop/ 


a question -- you say you ssh to your server first.  And then you try the scp command?  Once you ssh to your server you are now logged in to that server, and so whatever commands you issue are executed on the server, not your laptop.  So you're trying to copy a (presumably non-existing) file on your server TO your server.

With scp you don't establish an ssh connection first, scp itself establishes the connection.  So just issue the scp command from your laptop directly, no need to 'connect' with ssh first.

Apologies if I've misunderstood.

---

### Post by shanep-server on 2009-08-29
I figured out what I was doing wrong. I was logging into ssh with ssh -l user ip then it switched from user@laptop too user@server then i tried to send the file from the laptop to the server with the server terminal prompt. Once I closed my ssh connection an was at user@laptop I entered 

scp /home/shane/Desktop/puppy.iso shane@ip:/home/shane/Desktop/
entered password

transfer is done! thanks for your help though guys.


hahah u beat me too it :D thanks 4 ur help though much appreciated.

---

### Post by SoftwareExplorer on 2009-08-29
Sorry, I didn't notice the part about already being sshed in.

---

