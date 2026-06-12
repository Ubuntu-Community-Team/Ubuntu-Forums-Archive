---
title: "SSH Listen Rule"
date: 2007-03-13
forum: Server Platforms
---

### Post by scott_ttocs46 on 2007-03-13
Hi All,

     Does anyone know how to configure openssh-server so that it only listens to network addresses (i.e. 192.168.0.*)

Thanks,
Scott

---

### Post by gostek_1 on 2007-03-13
sure :D
add ListenAddress rule to your sshd_config
i.e. 
ListenAddress 192.168.0.1

---

### Post by conjur3r on 2007-03-13
The file is in /etc/ssh and make sure you edit ssh**d**_config

After making your changes, restart the daemon with 
# sudo /etc/init.d/ssh restart

---

### Post by MJN on 2007-03-13
> **scott_ttocs46 said:**
> Hi All,
 
Does anyone know how to configure openssh-server so that it only listens to network addresses (i.e. 192.168.0.*)
 
Thanks,
Scott
 
I think you need to clarify exactly what you want to achieve. You mentioned 'listens' which, as the solutions imply, sounds like you're talking about what local address the SSH server should be listening on. Hence, as pointed out the **ListenAddress** directive is what you're after.
 
However, you've also implied a range of addresses (192.168.0.*****) which makes little sense in the context of ListenAddress (at least the extent of requiring upto 255 local network adapters) hence I'm wondering if what you're actually trying to do it restrict access to clients whose addresses fall in the 192.168.0.* range.
 
To do this, I think the easiest way is to use the the /etc/hosts.deny and /etc/hosts.allow files (OpenSSH is compiled with TCP-Wrappers support hence can utitilse this facility).
 
Firstly, add a line containing **sshd : ALL** into **/etc/hosts.deny **- this forbids any access to SSHD.
 
Secondly, add a line containing **sshd : 192.168.0.0/255.255.255.0** - this opens up access to only those in the 192.168.0.* subnet.
 
Mathew

---

### Post by victorbrca on 2007-03-13
Sorry to take a ride on your topic "scott_ttocs46", but I have a similar question....

Can I do the same as "scott_ttocs46", but instead, I would like to limit listen address per user???

Reason behind is (call me a freak if you will):

- I've set up a CHROOT user to ssh to my server over the Internet.
- I still would like to be able to manage (with a privileged account) my ssh server from within my LAN, however I do not want to leave that user open to the Internet...

Anyone know of way I could achieve this?


Thanks a lot.....  :)


Vic.

---

### Post by Nikron on 2007-03-13
> **victorbrca said:**
> Sorry to take a ride on your topic "scott_ttocs46", but I have a similar question....

Can I do the same as "scott_ttocs46", but instead, I would like to limit listen address per user???

Reason behind is (call me a freak if you will):

- I've set up a CHROOT user to ssh to my server over the Internet.
- I still would like to be able to manage (with a privileged account) my ssh server from within my LAN, however I do not want to leave that user open to the Internet...

Anyone know of way I could achieve this?


Thanks a lot.....  :)


Vic.
The way I do this is with the /etc/security/access.conf file.  Read the documentation in the file, it should tell you all need to know.

---

### Post by victorbrca on 2007-03-13
> **Nikron said:**
> The way I do this is with the /etc/security/access.conf file.  Read the documentation in the file, it should tell you all need to know.

Thanks for the reply Nikron....

  I don't wanna be a bugger... But I looked through the manual and it's very self explanatory... My only question is this... Will the following code work?

```
-:user:ALL EXCEPT LOCAL 192.168.110.0/24.
```


  All the examples I found in the access.conf file and Internet only show one location. Here I'm allowing access from my LAN and local as well....


Thanks a lot!!!  :)



Vic.

---

### Post by Nikron on 2007-03-13
> **victorbrca said:**
> Thanks for the reply Nikron....

  I don't wanna be a bugger... But I looked through the manual and it's very self explanatory... My only question is this... Will the following code work?

```
-:user:ALL EXCEPT LOCAL 192.168.110.0/24.
```


  All the examples I found in the access.conf file and Internet only show one location. Here I'm allowing access from my LAN and local as well....


Thanks a lot!!!  :)



Vic.

It didn't work for me =/  I tried that too...   It works for if you individually do every IP.  I'm sure there's an easier way though.  I'll reply back if I find out how to do a range of IP's, because I never figured it out =P .  Also, remember to edit /etc/pam.d/ssh
and uncomment

account  required     pam_access.so

Okay got it...

[http://www.netwinsite.com/dnews/access.htm](http://www.netwinsite.com/dnews/access.htm)

-:user:ALL EXCEPT LOCAL 192.168.110.*
-:user:ALL EXCEPT LOCAL 192.168.110.0-24

should work, not the / sign though

---

### Post by victorbrca on 2007-03-13
U r the man!!!! :)


Gonna try from home and see if work!!!


Vic.

---

### Post by Nikron on 2007-03-13
Also, it turns out I might have been doing it wrong because I did
192.168.2.2/100

when I had to do

192.168.2.2/99

Anyway, I suggest that you test it out on a dummy user first, to make sure you don't get locked out.

---

### Post by victorbrca on 2007-03-13
I tried 

```
-:user:ALL EXCEPT LOCAL 192.168.110.*
-:user:ALL EXCEPT LOCAL 192.168.110.0-24
```

An it did not work. I was able to login locally, but not through SSH. I also tried 

```
-:user:ALL EXCEPT LOCAL 192.168.110.*.
-:user:ALL EXCEPT LOCAL 192.168.110.0-24.
```

and no donut....  :(


The single address worked

```
-:user:ALL EXCEPT LOCAL 192.168.110.10
```


I'll keep it like that for now and try to add another address to the end of it tonite when I get home...  I really only need two PCs on my LAN to have access to it....

Not sure why it worked for you but not for me thou... Maybe the "between chair and keyboard factor"!!! lol

Thanks for the help thou!!


Vic.

---

