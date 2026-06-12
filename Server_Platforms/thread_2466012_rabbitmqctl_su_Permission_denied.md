---
title: "rabbitmqctl: su: Permission denied"
date: 2021-08-17
forum: Server Platforms
---

### Post by lacid2 on 2021-08-17
When I'm trying to run rabbitmqctl I get the following error:

```
root@landscape1:~# rabbitmqctl
su: Permission denied
```

I tried with sudo and also being logged on with root, same error - has anyone seen this before?

---

### Post by QIII on 2021-08-17
Hello.

It is not good practice to log in as root or, for the most part, issue commands as root.  There are a lot of security risks to the former and the latter tends not to leave breadcrumbs for you to follow back.

Would you please return to your normal user, try the command with sudo and post the results?

Is the server one you control?  Are you accessing it directly or remotely?  Is it on a virtual machine hosted by a provider, such as a VPS?  Do you have access rights to the server?

---

### Post by MAFoElffen on 2021-08-17
Which form of package did you install from? From where? And how did you configure it?

Did you set up users and authentication for them yet (beyond the default user)? How? (Because beyond using passwords, you can use certificates...)

Is the rabbitmq-server service started? Is the ports opened up in your firewall and SELinux is not preventing the binding of? The ports for the different tools of, are:
```
4369: epmd, a peer discovery service used by RabbitMQ nodes and CLI tools
5672, 5671: used by AMQP 0-9-1 and 1.0 clients without and with TLS
25672: used for inter-node and CLI tools communication (Erlang distribution server port) and is allocated from a dynamic range (limited to a single port by default, computed as AMQP port + 20000). Unless external connections on these ports are really necessary (e.g. the cluster uses federation or CLI tools are used on machines outside the subnet), these ports should not be publicly exposed. See networking guide for details.
35672-35682: used by CLI tools (Erlang distribution client ports) for communication with nodes and is allocated from a dynamic range (computed as server distribution port + 10000 through server distribution port + 10010). See networking guide for details.
15672: HTTP API clients, management UI and rabbitmqadmin (only if the management plugin is enabled)
61613, 61614: STOMP clients without and with TLS (only if the STOMP plugin is enabled)
1883, 8883: MQTT clients without and with TLS, if the MQTT plugin is enabled
15674: STOMP-over-WebSockets clients (only if the Web STOMP plugin is enabled)
15675: MQTT-over-WebSockets clients (only if the Web MQTT plugin is enabled)
15692: Prometheus metrics (only if the Prometheus plugin is enabled)
```
Does system user "rabbitmq" exist in users?

The default user is: guest 
The default password is: guest

Have you configured the configuration file at : /etc/systemd/system/rabbitmq-server.service.d/limits.conf

What is the results of
```
sudo systemctl status rabbitmq-server
rabbitmqctl status
sudo rabbitmq-diagnostics ping  # if no connection here, no need to go on...
sudo rabbitmq-diagnostics status
sudo rabbitmq-diagnostics environment
```

Just saying, the installation is not one of those, just install the package and it works out the box, without some configuration and setup...

---

### Post by lacid2 on 2021-08-18
I was following the instructions to deploy Landscape: [https://landscape.canonical.com/set-up-on-prem]("https://docs.ubuntu.com/landscape/en/landscape-install-manual") - all users, groups, applications are/were installed and configured by the original installer

As I said in the original post, I did try with sudo, see the result below. Thank you for the heads up about using root, I'm aware.
```
landscape1 ~ > sudo rabbitmqctl
[sudo] password for user:
su: Permission denied
```

The rabbitmq-server is running:
```
landscape1 ~ > sudo systemctl status rabbitmq-server
&#9679; rabbitmq-server.service - RabbitMQ Messaging Server
   Loaded: loaded (/lib/systemd/system/rabbitmq-server.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2021-08-17 18:42:37 GMT; 17h ago
 Main PID: 13842 (beam.smp)
   Status: "Initialized"
    Tasks: 91 (limit: 4915)
   CGroup: /system.slice/rabbitmq-server.service
           &#9500;&#9472;13830 /bin/sh /usr/sbin/rabbitmq-server
           &#9500;&#9472;13842 /usr/lib/erlang/erts-9.2/bin/beam.smp -W w -A 64 -P 1048576 -t 5000000 -stbt db -zdbbl 32000 -K true -- -root /usr/lib/erlang -progname e
           &#9500;&#9472;13927 /usr/lib/erlang/erts-9.2/bin/epmd -daemon
           &#9500;&#9472;14087 erl_child_setup 65536
           &#9500;&#9472;14115 inet_gethost 4
           &#9492;&#9472;14116 inet_gethost 4
```

rabbitmq user exists:
```

landscape1 ~ > id rabbitmq
uid=119(rabbitmq) gid=121(rabbitmq) groups=121(rabbitmq)
```

---

### Post by MAFoElffen on 2021-08-18
Please correct your link. You have an extraneous ":" character at the end of the URL...

And what step of those instructions are you up to? Because in all that (and in the upstream vendor docs)... I do not see
```
sudo rabbitmqctl
```
As a full, single command, without using other included arguments... Rather like
```
sudo rabbitmqctl add_user landscape <password>
sudo rabbitmqctl add_vhost landscape
sudo rabbitmqctl set_permissions -p landscape landscape ".*" ".*" ".*"
```
Even [Ubuntu Man rabbitmqctl]("http://manpages.ubuntu.com/manpages/trusty/man1/rabbitmqctl.1.html") doesn't have it returning anything without arguments...
Am I confused with that, or misunderstanding what you are saying?

---

### Post by lacid2 on 2021-08-19
MAFoElffen, thank you, link was fixed.

Right, I was running *[COLOR=#000000][FONT=&amp]sudo rabbitmqctl add_user landscape <password> [/FONT][/COLOR]*then I noticed it doesn't work so tried without arguments.

```
landscape1 ~ > sudo rabbitmqctl add_user landscape randompassword
su: Permission denied
```

Just for the record, on FreeBSD rabbitmqctl without any arguments outputs:
```
~ > rabbitmqctl 

Usage
rabbitmqctl [--node <node>] [--timeout <timeout>] [--longnames] [--quiet] <command> [<command options>]

```

---

### Post by MAFoElffen on 2021-08-19
In that case, I would say there was something wrong that happened in the install. If root does not have permission to use it, something went wrong. I hate to say this, but "I would" purge it and reinstall.

It's not getting a command not found. It's getting a permission problem. Something happened in the installation of that package...

---

### Post by lacid2 on 2021-08-23
I was thinking about that, probably I'll re-deploy it

---

### Post by lacid2 on 2021-08-25
By updating /etc/pam.d/su as follows I was able to fix this issue:

[HTML]#%PAM-1.0
auth        sufficient    pam_rootok.so
# Uncomment the following line to implicitly trust users in the "wheel" group.
auth        sufficient    pam_wheel.so trust use_uid
# Uncomment the following line to require a user to be in the "wheel" group.
auth        required    pam_wheel.so use_uid
auth        substack    system-auth
auth        include        postlogin
#account        sufficient    pam_succeed_if.so uid = 0 use_uid quiet
#account        include        system-auth
password    include        system-auth
#session        include        system-auth
#session        include        postlogin
session        optional    pam_xauth.so[/HTML]

---

### Post by MAFoElffen on 2021-08-26
You didn't highlight "what" you changed... But I am assuming you uncommented these two lines(?)
```
#%PAM-1.0
auth        sufficient    pam_rootok.so
# Uncomment the following line to implicitly trust users in the "wheel" group. 
[COLOR=#ff0000]auth        sufficient    pam_wheel.so trust use_uid[/COLOR]
# Uncomment the following line to require a user to be in the "wheel" group.
[COLOR=#ff0000]auth        required    pam_wheel.so use_uid[/COLOR]
auth        substack    system-auth
auth        include        postlogin
#account        sufficient    pam_succeed_if.so uid = 0 use_uid quiet
#account        include        system-auth
password    include        system-auth
#session        include        system-auth
#session        include        postlogin
session        optional    pam_xauth.so
```

---

### Post by lacid2 on 2021-11-29
That is correct MAFoElffen, thank you!

---

