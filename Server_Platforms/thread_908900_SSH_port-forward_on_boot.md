---
title: "SSH port-forward on boot?"
date: 2008-09-02
forum: Server Platforms
---

### Post by europa on 2008-09-02
Hello all.

I'm trying to establish an ssh tunnel on server bootup.

The tunnel goes to 2 desktop machines on my network that are both running VNC servers.  My server is in the DMZ but the desktops are not. Im using netbios names to resolve the network ips.

I placed this into the /etc/init.d/ folder

```
ssh -fNgL 5900:io:5900 localhost
sleep 2s
ssh -fNgL 5901:sparky:5901 localhost
sleep 2s
```

If I manually execute the script, it runs fine. However, if i reboot the machine, the tunnels do not re-establish.

What am i doing wrong here? Any help will be appreciated. Thank you very much.

---

### Post by europa on 2008-09-03
bump :guitar:

---

### Post by Vivaldi Gloria on 2008-09-03
Just add it to /etc/rc.local before "exit 0". Or better, create a file /etc/network/if-up.d/ssh_tunnel owned by root containing your script and make it executable. The scripts in that folder are executed when a network connection is established.

---

### Post by europa on 2008-09-03
```

jack@callisto:/etc$ sudo nano rc.local
jack@callisto:/etc$ sudo shutdown -r now
The system is going down for reboot NOW!
---------------
jack@callisto:~$ nc localhost 5900
localhost [127.0.0.1] 5900 (?) : Connection refused
jack@callisto:~$ ./sadpandaface
-bash: ./sadpandaface: No such file or directory
jack@callisto:~$ 
```

```

jack@callisto:/etc/init.d$ sudo mv vnc /etc/network/if-up.d
[sudo] password for jack:
jack@callisto:/etc/init.d$ cd /etc/network/if-up.d
jack@callisto:/etc/network/if-up.d$ ls -l
-rwxrwxrwx 1 root root   88 2008-09-02 23:12 vnc
jack@callisto:/etc/network/if-up.d$ sudo shutdown -r now
The system is going down for reboot NOW!
-------------
jack@callisto:~$ nc localhost 5900
localhost [127.0.0.1] 5900 (?) : Connection refused
jack@callisto:~$ cd /etc/network/if-up.d
jack@callisto:/etc/network/if-up.d$ ./vnc
jack@callisto:/etc/network/if-up.d$ nc localhost 5900
RFB 003.007

```

:(

---

### Post by Vivaldi Gloria on 2008-09-03
I think I got it. When you ssh from the command line you ssh as jack and ssh looks in /home/jack/.ssh. When you ssh from rc.local etc. then ssh looks in /root/.ssh and cannot find keys. 

Either copy keys to root's folder or look in the ssh options to see if there is a relevant flag. Or maybe a use of su with -c can do it.

---

### Post by europa on 2008-09-03
i don't have a root folder D:

---

### Post by Vivaldi Gloria on 2008-09-04
> **europa said:**
> i don't have a root folder D:

OK. What about my other suggestions? Try someting like

su jack -c "ssh -fNgL 5900:io:5900 localhost"

which says run the command between the quotes as jack.

---

### Post by windependence on 2008-09-04
I'm not exactly sure why you are wanting to do this. You can tunnel to whatever machine you want from the outside using PuTTY or even from the command line. Then you just use the tunnel for your VNC access. 

You should also take a look at nomachine.

-Tim

---

### Post by europa on 2008-09-04
> **Vivaldi Gloria said:**
> OK. What about my other suggestions? Try someting like

That makes me enter a password before it executes.

> **windependence said:**
> I'm not exactly sure why you are wanting to do this. You can tunnel to whatever machine you want from the outside using PuTTY or even from the command line. Then you just use the tunnel for your VNC access. 

You should also take a look at nomachine.

-Tim

I could but I'd rather not have to deal with that step.  One of the VNCs goes to my stepfathers computer and he doesn't know anything ssh nor does he have access to my server. :P

nomachine looks  interesting.  at first glance it seems like a vbox type software. i'll check it out.

---

### Post by windependence on 2008-09-04
I don't quite understand because your step father would nbot have to do anytihng at all. This can be done entirely on your end, you just have to have the VNC server running on his machine and listening. I do this all the time from my work computers to various machines on my metwork with no interaction needed on that end.

-Tim

---

### Post by Vivaldi Gloria on 2008-09-04
OK. I have found the ssh option I mentioned earlier. Add the following flag to ssh line:

```
-i /home/jack/.ssh/id_dsa
```

to use jack's identity when connecting. Or id_rsa if you use rsa keys. Here is the related part from man ssh:

>      -i identity_file
             Selects a file from which the identity (private key) for RSA or DSA authentication is read.  The default is
             ~/.ssh/identity for protocol version 1, and ~/.ssh/id_rsa and ~/.ssh/id_dsa for protocol version 2.  Identity
             files may also be specified on a per-host basis in the configuration file.  It is possible to have multiple -i
             options (and multiple identities specified in configuration files).


---

### Post by europa on 2008-09-04
> **windependence said:**
> I don't quite understand because your step father would nbot have to do anytihng at all. This can be done entirely on your end, you just have to have the VNC server running on his machine and listening. I do this all the time from my work computers to various machines on my metwork with no interaction needed on that end.

-Tim

I want to get the tunnel established on boot. If the server has to restart for whatever reason, I dont want to have to go in and run commands.  If my stepfather wants to connect to his machine from work and the connection is down, he's SOL and has to bother me.

My server does stay up most of the time, but if I am still learning and I mess around on it all the time.  I don't want to have to deal with this if i can get it to run automatically.

Unless you're trying to explain to me how to do it a diffderent way that I don't understand?

---

### Post by europa on 2008-09-04
> **Vivaldi Gloria said:**
> OK. I have found the ssh option I mentioned earlier.

That's still giving me the same problem.  I'm thinking that the script is running and establishing the tunnel but then closes the connection once it moves onto the next task.  Could this be a possibility?

---

### Post by Vivaldi Gloria on 2008-09-04
> **europa said:**
> Could this be a possibility?

Not sure now. I'm leaving now till tomorrow. I'll look into it again then.

---

### Post by europa on 2008-09-04
> **Vivaldi Gloria said:**
> Not sure now. I'm leaving now till tomorrow. I'll look into it again then.

Ok. Thanks for the help. :)

---

### Post by windependence on 2008-09-04
> **europa said:**
> I want to get the tunnel established on boot. If the server has to restart for whatever reason, I dont want to have to go in and run commands.  If my stepfather wants to connect to his machine from work and the connection is down, he's SOL and has to bother me.

My server does stay up most of the time, but if I am still learning and I mess around on it all the time.  I don't want to have to deal with this if i can get it to run automatically.

Unless you're trying to explain to me how to do it a diffderent way that I don't understand?

Well I'm still kinda confused because you could do this at the router level by forwarding a different VNC port to each PC like 5900 to yours, 5901 to his etc, and then all he would have to do is connect to the correct VNC session like xxx.xxx.xxx.xxx:1

That should be pretty simple for him. Maybe I still don't understand your problem. ;)

-Tim

---

### Post by europa on 2008-09-04
Oooh.  

Desktop computers are continuous shut off and rebooted and are using DHCP to obtain their IP addresses.  If you take a look at my first post, you'll see that i'm using netbios name instead of IP.

We don't want to setup static IPs on our desktops.

---

### Post by windependence on 2008-09-04
Why not? Security? Not much security through obscurity. Personally I don't see any reason for not doing that but you may have a good reason.

-Tim

---

### Post by europa on 2008-09-04
> **windependence said:**
> Why not? Security? Not much security through obscurity. Personally I don't see any reason for not doing that but you may have a good reason.

-Tim

Reason being that my stepdad doesn't really trust me with his computer and won't let me set it up. :P

I had static on my own PC for a while but ended up taking it off due to a conflict.

I would really like to learn how I could get around situations such as this so that I know how to get around problems in the future.  Most of the stuff I know has been learned by trying to fix problems.

---

### Post by europa on 2008-09-05
ba-ba-ba-bump

---

### Post by windependence on 2008-09-05
I'm out of ideas. This is not something that's real common so you may have to keep bumping for a bit until someone has a revelation. :)

-Tim

---

### Post by europa on 2008-09-05
Thanks for the help man. I'll checkout that nomachine. :D

---

### Post by europa on 2008-09-09
I just came across AutoSSH

[http://www.harding.motd.ca/autossh/](http://www.harding.motd.ca/autossh/)

It sounds like it will accomplish exactly what I've been trying to do. I will try it out sometime this week and post again (just incase anybody else is having a similar issue)

---

