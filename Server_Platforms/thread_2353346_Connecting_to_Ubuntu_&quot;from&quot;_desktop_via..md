---
title: "Connecting to Ubuntu &quot;from&quot; desktop via. remote managment using SSH."
date: 2017-02-20
forum: Server Platforms
---

### Post by daniel228 on 2017-02-20
I have just installed Ubuntu 16.04.1 LTS and rite now I'm very confused on how to connect to the server threw SSH from my Desktop Via. the remote management. I've installed SSH with the installation and I'm using bash on my local desktop but I'm really unsure on the commands or command I would have to use to get in to the server and log in remotely.

I've tried    ssh daniel@ubuntu ..

I'm really not sure how this will work as I'm trying to connect threw my router to the server and log in and then I was going to take it from their. I'm very new to Linux let alone the server variations and using SSH.

---

### Post by bearlake on 2017-02-20
Hi,

This is what I use to ssh into my server. Example only. --> ssh user@host

ssh tom@192.168.2.99

I assume you already copy the ssh keys over to the server.

---

### Post by daniel228 on 2017-02-21
> **bearlake said:**
> Hi,

This is what I use to ssh into my server. Example only. --> ssh user@host

ssh tom@192.168.2.99

I assume you already copy the ssh keys over to the server.

I have not. I dont even know what the actual IP address is of the Rack I have. I am very new to the server scene and trying my best to learn as much as I can.

---

### Post by bearlake on 2017-02-21
Here are a few reads for you.

How do I set up SSH authentication keys

[http://askubuntu.com/questions/61557/how-do-i-set-up-ssh-authentication-keys](http://askubuntu.com/questions/61557/how-do-i-set-up-ssh-authentication-keys)

and a must before you go anything.

Ubuntu Server Guide.

[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

Do a lot of reading first and maybe check out virtual machine setup.

[http://askubuntu.com/questions/771996/best-way-to-create-virtual-machine-with-16-04](http://askubuntu.com/questions/771996/best-way-to-create-virtual-machine-with-16-04)

---

### Post by daniel228 on 2017-02-21
> **bearlake said:**
> Here are a few reads for you.

How do I set up SSH authentication keys

[http://askubuntu.com/questions/61557/how-do-i-set-up-ssh-authentication-keys](http://askubuntu.com/questions/61557/how-do-i-set-up-ssh-authentication-keys)

and a must before you go anything.

Ubuntu Server Guide.

[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

Do a lot of reading first and maybe check out virtual machine setup.

[http://askubuntu.com/questions/771996/best-way-to-create-virtual-machine-with-16-04](http://askubuntu.com/questions/771996/best-way-to-create-virtual-machine-with-16-04)




I'm doing a lot of reading and I've encountered an error. connection  refused on port 22 . I've looked up the systems IP address threw my  router and thats the error I get when trying to copy the SSH keys over  to the machine.

I'm reading as much as I can and I've found as  well that port 22 is activly listening and sshd is up and running and  installed. The local address is 0.0.0.0.22 and the state is of LISTEN.

---

### Post by cariboo on 2017-02-21
You should be able to find out what your ip address is from your hosting service.

Once you've done that, then you can use your ip address to ssh into the system.

You should find out from your hosting service whether port 22 is blocked or not.

---

### Post by daniel228 on 2017-02-21
> **cariboo said:**
> You should be able to find out what your ip address is from your hosting service.

Once you've done that, then you can use your ip address to ssh into the system.

You should find out from your hosting service whether port 22 is blocked or not.

The server is mine. I have it hear at home. Port 22 is listening and I have the firewall disabled.

I think it could be a problem with DHCP as when I originally installed Ubuntu on the system I skipped that part of the installation process. I'm wanting to run the machine for the time being as a server connected to my client being my desktop and use OpenSSH to remote from the desktop to the server as I only have for the time being restricted internet access.

I ran various commands threw the actual terminal on Ubuntu and everything is checking out the only problem I can determine is the two systems are not connecting and the problems got to be with the router or swich I have in the middle. The internal IP address all check out on the router and everything is registered. I have an option for SSH on the router under the configuration of the actual server along with other settings like XBOX, DX7 DX8 and DX9 .. I'm not 100 % sure what that particular setting does if I were to change it.

---

### Post by cariboo on 2017-02-21
> **daniel228 said:**
> The server is mine. I have it hear at home. Port 22 is listening and I have the firewall disabled.

I think it could be a problem with DHCP as when I originally installed Ubuntu on the system I skipped that part of the installation process. I'm wanting to run the machine for the time being as a server connected to my client being my desktop and use OpenSSH to remote from the desktop to the server as I only have for the time being restricted internet access.

I ran various commands threw the actual terminal on Ubuntu and everything is checking out the only problem I can determine is the two systems are not connecting and the problems got to be with the router or swich I have in the middle. The internal IP address all check out on the router and everything is registered. I have an option for SSH on the router under the configuration of the actual server along with other settings like XBOX, DX7 DX8 and DX9 .. I'm not 100 % sure what that particular setting does if I were to change it.

If you can ssh in from your internal ip address that is all you need, most routers don't allow you to loop back to your external ip address.

What I do on my internal network is set aliases in /etc/hosts eg:

```
cariboo@alexis:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	alexis
192.168.0.200	likely
192.168.0.205	willy
192.168.0.104	skynet
```

then when I want to access one of the other system on my local network all I have to type is:

```
ssh willy
```

when setting up ssh access I use:

```
ssh-copy-id cariboo@willy
```

to transfer the key I created on my laptop to the other systems, substituting the server name for each one.

For more on setting up ssh private/public keys have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by daniel228 on 2017-02-21
> **cariboo said:**
> If you can ssh in from your internal ip address that is all you need, most routers don't allow you to loop back to your external ip address.

What I do on my internal network is set aliases in /etc/hosts eg:

```
cariboo@alexis:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    alexis
192.168.0.200    likely
192.168.0.205    willy
192.168.0.104    skynet
```

then when I want to access one of the other system on my local network all I have to type is:

```
ssh willy
```

when setting up ssh access I use:

```
ssh-copy-id cariboo@willy
```

to transfer the key I created on my laptop to the other systems, substituting the server name for each one.

For more on setting up ssh private/public keys have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")


I'm an absolute idiot. My apologizes in advance cariboo but their was a number of steps I did not follow and after going over them forensically I have now been able to log in to the server using SSH. Thanks for your help and everyone who has commented as it did help.

---

