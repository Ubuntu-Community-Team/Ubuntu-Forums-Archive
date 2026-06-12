---
title: "plymouthd takes 95% of CPU time"
date: 2010-07-08
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-08
I am having a Ubuntu 10.04 server edition and I see  a process plymouthd taking 95% of CPU what is that and how can I reduce it.

---

### Post by kemra on 2010-07-08
plymouthd is used by the OS at startup to provide the boot animation, you can find more info about it here:

[http://cgit.freedesktop.org/plymouth/tree/README]("http://cgit.freedesktop.org/plymouth/tree/README")

As to why it's using so much cpu after x is loaded I have no idea, sorry.

---

### Post by tapas_mishra on 2010-07-08
That is really funny.I do not have a GUI on the said server.It is a headless server so what animation is happening I wonder.Is there a way to disable that ?

---

### Post by flipper_r on 2010-10-06
I was looking for an answer as well.

In the meantime I found this command:

```

sudo plymouth quit --retain-splash

```

or 

```
sudo plymouth deactivate
```

However, I'm still unsure as to what these are doing to the system.

---

### Post by tapas_mishra on 2010-10-06
Well thanks for pointing it out here.
I asked this question in July it is Oct,
in this time a lot of things had happened.
I had written script which used to grep pid of plymouth and kill it.
I no more have that server as I formatted it one day.
but ur command shld help someone.

---

### Post by flipper_r on 2010-10-06
Thanks tapas_mishra!

Could you post your script, I'm sure it'll help out a lot.

There is also a "plymouth-stop" scrip that runs as part of init.
It is located in /etc/init/plymouth-stop.conf

---

### Post by tapas_mishra on 2010-10-14
Hi,its easy 
```

ps -el | grep plymouthd | kill -9 `awk {'print $4;'}`

```

---

### Post by sysconfig on 2012-08-29
[COLOR=Blue]Hi, I am using this command to kill 'plymouthd' pid:

[/COLOR][PHP]# ps -C plymouthd -o pid= | kill -9 `awk '{print $1}'`[/PHP]

---

