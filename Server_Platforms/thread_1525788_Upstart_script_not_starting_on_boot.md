---
title: "Upstart script not starting on boot"
date: 2010-07-07
forum: Server Platforms
---

### Post by xfcmb on 2010-07-07
Hi everyone,

First time writing a startup script in Ubuntu and I'm having some trouble. I'm having an issue with a custom init (upstart) script. Basically the script should start on boot and establish an ssh connection to a remote proxy. Unfortunately the script is not working as intended and does not automatically establish the connection at boot time. 

A query of "sudo initctl list" shows the script in the "stopped/waiting" state just after boot. Below is the contents of the /etc/init/sshproxy.conf file:

```


# sshproxy
#
# This service maintains an ssh connection to the proxy
# server. If the connection breaks it will be automatically re-established.

# start on started rcS
# start on runlevel [2345]
# start on started ssh
start on started networking
# start on started network-interface-security
# start on stopped rc RUNLEVEL=[2345]


respawn
exec /usr/bin/ssh -R 10002:localhost:22 user@proxy
console output

```I am running 10.04. As you can see I have tried a number of "start on" directives with none of them working as intended. 

I've done all the set up with SSH, shared the keys etc, so the actual connection works. If I run the script manually with "sudo start sshproxy" the connection is established and all is well. However, that's not what I want to do, this should start and establish the connection automatically on boot. 

Reading this ([http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)) lead me to believe that this was all the configuration I needed, however the script still does not start on boot. I know I am missing something fairly obvious but I'm a bit stuck...

Is there another place / file I need to configure to actually get this to start on boot?

Thanks for any help you can send my way.

---

### Post by xfcmb on 2010-07-07
Looks like if I do the following the script will work as expected. Now I just need to figure out how I get this to run in the event a network cable is pulled and reinserted after some time.

```
start on started network-manager 

pre-start script
        sleep 10        #wait some time to make sure interfaces have IPs
end script

respawn
respawn limit 1000 1
exec /usr/bin/ssh -n -N -T -R 10001:localhost:22 user@proxy
```

---

