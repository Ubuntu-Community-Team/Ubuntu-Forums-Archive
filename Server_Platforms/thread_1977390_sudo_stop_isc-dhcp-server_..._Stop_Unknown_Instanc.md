---
title: "sudo stop isc-dhcp-server ... Stop: Unknown Instance"
date: 2012-05-10
forum: Server Platforms
---

### Post by Unisyst on 2012-05-10
Just installed Ubuntu Server 12.04. So far not bad. However I'm not liking upstart. Missing the /etc/init.d/ way, but I'm sure the new way is better somehow.

So I installed isc-dhcp-server as I want my machine to handle dhcp on my network. I configured it and was going to restart it.

isc-dhcp-server is in the /etc/init.d/ folder. Tried starting it from there but it errors out.

unisyst@:~$ service status isc-dhcp-server
status: unrecognized service

The server appears to not run at all (doesn't show up in ps aux).

 I'd usually figure this out myself, but I'm tired and having people over tomorrow for a LAN. They're not gonna be to happy with statically assigning all their PCs.

---

### Post by Unisyst on 2012-05-10
initctl start isc-dhcp-server
Job failed to start.

Any way of showing a log of why it failed?

---

### Post by Unisyst on 2012-05-10
unisyst@:~$ init-checkconf /etc/init/isc-dhcp-server.conf
ERROR: failed to ask Upstart to check conf file

-rageface.png-

---

### Post by Unisyst on 2012-05-10
unisyst@:/$ sudo start isc-dhcp-server
isc-dhcp-server start/running, process 3208


I seriously have no clue what I did. I'll read over the upstart documentation sometime soon.

---

### Post by Unisyst on 2012-05-10
HURP DURP. Is there any logs? Yeah /var/log/upstart... I'm going to bed now.

---

### Post by ralfarof on 2012-05-31
Same problem here, it won't stop using 

```
sudo service isc-dhcp-server stop
```

Instead I have to use

```
sudo /etc/init.d/isc-dhcp-server stop
```

:confused:

---

### Post by Muk on 2012-12-30
how did you solve this problem? i am currently having the same problem. isc-dhcp-server is not starting up for me and not giving out ip addresses.

---

### Post by matt_symes on 2012-12-30
HI

@Muk

Have you tried reloading the configuration file ?
```

sudo initctl reload-configuration
```

```
sudo service isc-dhcp-server start
```

If not then try this...

```
sudo /etc/init.d/isc-dhcp-server start
```

Kind regards

---

### Post by Muk on 2012-12-30
> **matt_symes said:**
> HI

@Muk

Have you tried reloading the configuration file ?
```

sudo initctl reload-configuration
```

```
sudo service isc-dhcp-server start
```

If not then try this...

```
sudo /etc/init.d/isc-dhcp-server start
```

Kind regards


```

service isc-dhcp-server start
start: Job is already running: isc-dhcp-server

/etc/init.d/isc-dhcp-server start
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service isc-dhcp-server start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start isc-dhcp-server

```
it still didn't start any dhcp servers. i tried connecting it with my other laptop, but it isn't gaining any ip addresses

---

### Post by matt_symes on 2012-12-30
Hi

> **Muk said:**
> ```

service isc-dhcp-server start
start: Job is already running: isc-dhcp-server

/etc/init.d/isc-dhcp-server start
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service isc-dhcp-server start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start isc-dhcp-server

```it still didn't start any dhcp servers. i tried connecting it with my other laptop, but it isn't gaining any ip addresses

You seem to have a different issue than the OP as your service is running, runnable and has been found by initctl.

It may be worth creating a new thread with the exact IP address dchp problems you have having and configuration you have set for for dhcp on the server.

Kind regards

---

