---
title: "installing server unable to read display"
date: 2012-09-13
forum: Server Platforms
---

### Post by micahpage on 2012-09-13
I installed ubuntu server 12.04.1. I used a monitor hooked directly to the computer for installing apps, and updating to get started. Once I complete the installation, it gives me a terminal, or so what I think is a terminal. It is pure white with some chars of the prompt but not all of them or only part of some. It also has double white lines vertical. IT is completely unreadable. 

At first I thought the old monitor was shot, so I hooked it up to my current monitor, and I got the same.

I really just want to get ssh installed and set up on it so i can use my pc to ssh into it. I cant see the output though fresh from install to be able to set up ssh on it.

Is there a trick I am missing?

---

### Post by darkod on 2012-09-14
The post is a little bit confusing.
Was the monitor unreadable right from the start, including during the install, or only after the install was finished?
If it was right from the start, how did you install?

If the install finished, the problem of not being able to read the monitor apart, you should have ssh server up and running if you selected it in the tasks during the install, so you should be able to ssh into it.

---

### Post by micahpage on 2012-09-14
it only was like that after I installed and only when I start up the server, as an ubuntu live CD still works fine.

The install is complete. 
I tried to ssh into but was unable. 
I am not sure how to properly explain it.

---

### Post by darkod on 2012-09-14
Looks like it doesn't even boot correctly, otherwise ssh should work if you installed OpenSSH Server during the install.

Are you sure you have the correct IP? You did set up a static IP right?

---

### Post by micahpage on 2012-09-14
i did add OpenSSH

I did not see an option for static IP, when it starts booting it says DHCP, which im not sure how to change without a terminal

---

### Post by darkod on 2012-09-14
Yeah, if you are not quick to Cancel it, by default it turns dhcp on. Look into your router (dhcp server) leases, it should give you the IP currently used by the server lease.

Without an IP, how do you know ssh is not working?

When you have the IP, try again ssh.

---

### Post by micahpage on 2012-09-14
> Without an IP, how do you know ssh is not working?
I was initially doing it the way I ssh into my computer from an outside pc.
like for example:
first I ssh into my own pc and then attempt to ssh into the server pc
```
metulburr@ubuntu:~$ ssh metulburr@xxx.xxx.xxx.xxx -p xxxx
Ubuntu 12.04 LTS
metulburr
metulburr@xxx.xxx.xxx.xxx's password: 
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

12 packages can be updated.
9 updates are security updates.

*** System restart required ***
Last login: Fri Sep  7 05:42:00 2012
 DISTRIBUTION:  Ubuntu 12.04.1 LTS precise
      DESKTOP:  None
       KERNAL:  3.2.0-29-generic
          BIT:  64
          CPU:  Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz [8] Core
    PARTITION:  118 / 210 GB
          RAM:  1400 / 7967 MB

metulburr@ubuntu:~$ exit
logout
Connection to xxx.xxx.xxx.xxx closed.
metulburr@ubuntu:~$ ssh server@xxx.xxx.xxx.xxx -p xxxx
ssh: connect to host xxx.xxx.xxx.xxx port xxxx: Connection refused
metulburr@ubuntu:~$
```




OK so i changed my router settings.

When I try to ssh into I get connection refused

I am still not sure though why the monitor hooked up to the server pc shows an unreadable terminal?

---

### Post by darkod on 2012-09-14
Why are you using the -p option? If you never managed to boot the server once, go in and change the ssh port, it's working on the default port 22. No need to use the -p, only the correct IP that the dhcp server says is assigned to the server you want to access.

I have no clue about the monitor, sounds like video driver.

But the ssh problem seems to be that you are not using the correct IP.

Is the server on different location, so you are trying to ssh from outside? That complicates things more.

---

### Post by micahpage on 2012-09-14
I was using the port option because that is what i had changed the port forward to in the router settings for the server.

I changed it to port 22


the server is at the same location, but i want to access from the outside

---

### Post by darkod on 2012-09-14
And you are sure the port forward points to the correct private IP of the server?

Unless you are trying to use different port from the outside for security reasons, no need to change just for a simple test.

In the port forwarding of your router you only change the destination private IP, not the port. You send it on port 22 from the outside, the router forwards it on the same port, the server receives it on the default port 22. Later for security you can change things after you have the access figured out.

I will say again, this looks more like problem with the access right now, regardless of the monitor issue. Besides you want the server to be headless, so I don't see where the monitor comes into play.

---

### Post by micahpage on 2012-09-14
> And you are sure the port forward points to the correct private IP of the server?

I am sure

> I will say again, this looks more like problem with the access right now, regardless of the monitor issue. Besides you want the server to be headless, so I don't see where the monitor comes into play.

well i assumed that if it was the output for the monitor then it would have been the output from ssh into it. 
IT doesn;t matter though to me as once i get this working I have no intention of accessing it other than ssh

Ugh, this is driving me nuts. I know how to set it up in a desktop ubuntu, but this is the first time I have ever used ubuntu server. IT almost seems easier to set up a desktop ubuntu as a server as I already know what to do.

---

### Post by darkod on 2012-09-14
If you are on the same location, try with the private IP first. On the same LAN you can use only the IP directly.

That is always the first step, and it will show you that ssh is working at least.

If you manage to access it with ssh, you can use that to change the IP to static.

Only after that you can start working on the access from outside. Make sure ssh is OK first.

Also, in some cases you can't try the public IP from the same home network. Not all home routers have the option to send back the connection once it goes out. It's better to test from another location.

---

### Post by micahpage on 2012-09-14
>  On the same LAN you can use only the IP directly.

i am not exactly sure how to connect to the IP directly

---

### Post by micahpage on 2012-09-14
OK so now I finally ssh into it from outside. I am not sure what i did exactly, lol.

Thanks by the way for all the help



EDIT:
now I actually unhooked it and hooked it back up again, with the monitor and keyboard unplugged. How am I suppose to enter in the username and password to get the server going? Now that I try to ssh into it (without itself being logged in), it just pauses on attempting to log into it, whereas before I had the server pc logged in, and it did it fine?

---

### Post by darkod on 2012-09-15
The first time you log in, I would use it to change the IP to static. That way you know at which IP to look for it.

Otherwise, using the private IP on the same LAN is the same as using the public IP:
ssh username@<private IP>

But it will work only from computers on the same LAN. For example, lets say your home router is 192.168.1.1 and the server has a static IP of 192.168.1.10.

You simply do:
ssh username@192.168.1.10

To change the IP to static, open /etc/network/interfaces with the nano editor, and change the eth0 to something like:
```
auto eth0
iface eth0 inet static
   address <server IP you want it to have>
   netmask <usually 255.255.255.0>
   gateway <router private IP>
   dns-nameservers <dns 1> <dns 2>
```

The static IP you choose for the server should be outside the range the router assigns to machines, so that it can't be assigned to another machine by chance.
After you save and close the file (in nano you do that with Ctrl + O and then Ctrl + X), reboot it and after it boots up it will have the new static IP:
sudo reboot

Then you will know at which IP to look for it always. It can't change.
For outside access you will need to do the port forwarding of the ports you want to this IP.

Right now I am really confused what are you trying, since the first rule is to set it to static IP instead of chasing it around. The check access from the local LAN, and only after that start working on outside access.

---

