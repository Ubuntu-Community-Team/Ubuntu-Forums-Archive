---
title: "Howto Set Up a Simple SSH Server on a LAN"
date: 2014-05-28
forum: Server Platforms
---

### Post by suprleg on 2014-05-28
I've installed the latest Ubuntu openssh-server package, 6.6, and now I'm attempting  to edit both /etc/ssh/ssh_config and /etc/ssh/sshd_config. I'm just looking for a simple edit of both to allow local connections. 
If you've looked at either file recently you'll notice there are a multitude of un-commented security options. So far, with ssh -v -p 22 user/root@xxx.xxx.xxx.xxx I'm getting a reference to line 19 of the ssh_config regarding * option and "login refused".
It should be noted I'm running ssh-agent by default. Thanks for any help.

---

### Post by ian-weisser on 2014-05-28
Does openssh-server have a way to recognize local vs nonlocal connections? I have not seen one.
Usually I use the firewall for that.

I recommend against editing ssh_config. The default settings for the client should be fine. I've _never_ needed to change the client settings.

Have you read [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) ?

---

### Post by suprleg on 2014-05-28
Thanks for the response. Yes I've read that .doc, thanks. So far I'm only able to login to the openssh server if I sudo /usr/sbin/sshd to start the server, by simply issuing ssh my.server.ip.address, with no port or user. Starting openssh-server this way seems to ignore the /etc/ssh/sshd_config and /etc/ssh/ssh_config files.

---

### Post by CharlesA on 2014-05-28
Moved out of Tutorials cuz this isn't a tutorial. :)

> **suprleg said:**
> Thanks for the response. Yes I've read that .doc, thanks. So far I'm only able to login to the openssh server if I sudo /usr/sbin/sshd to start the server, by simply issuing ssh my.server.ip.address, with no port or user. Starting openssh-server this way seems to ignore the /etc/ssh/sshd_config and /etc/ssh/ssh_config files.

What? Why aren't you using:

```
sudo service ssh start
```

Or

```
sudo service ssh stop
``` 

?

See here too:
[http://charlesauer.net/tutorials/ubuntu/openssh-server-ubuntu.php](http://charlesauer.net/tutorials/ubuntu/openssh-server-ubuntu.php)

With that being said, I have never directly edited ssh_config (the client config) for openssh-server. Having a config file in ~/.ssh works wonders.

[http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/](http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/)

---

### Post by faust2 on 2014-05-28
> **suprleg said:**
> Thanks for the response. Yes I've read that  .doc, thanks. So far I'm only able to login to the openssh server if I  sudo /usr/sbin/sshd to start the server, by simply issuing ssh  my.server.ip.address, with no port or user. Starting openssh-server this  way seems to ignore the /etc/ssh/sshd_config and /etc/ssh/ssh_config  files.

I kept getting a ECONNRESET error when I was trying to set up SSH  earlier today. I set a static IP address for the machine I was trying to  connect to. I refreshed my machine's connection (Using wifi in this  situation) and it failed to connect again. I located my router's  (Linksys E2500) DHCP lease page and removed the lease to the target  machine. Tried to reconnect using SSH and it succeeded when I used the  static IP address as the hostname. 

Perhaps this would help you as well?

---

### Post by SeijiSensei on 2014-05-29
You can specify "ListenAddress" in /etc/ssh/sshd_config to bind the server to a particular interface.  So if this is a multi-homed machine, with 10.10.10.10 as the externally-facing address and 192.168.1.1 as the internally-facing address, you could use
```
ListenAddress 192.168.1.1
```
and connections to 10.10.10.10 would be ignored.

---

### Post by ian-weisser on 2014-05-29
> **SeijiSensei said:**
> You can specify "ListenAddress" in /etc/ssh/sshd_config to bind the server to a particular interface.

That is so cool.
Now I know.

---

### Post by suprleg on 2014-05-29
Thanks for that, I'll report back with any updates. They may be helpful to others.:KS

---

### Post by suprleg on 2014-05-30
Update: I've got the ssh server running on the LAN in what I'd assume is a very rudimentary configuration. I pretty much understand the contents of:/etc/ssh/ssh_config and /etc/ssh/sshd_config, however I'm having trouble  implementing the variables/switches in them to achieve good security. Also utilizing  ssh-agent is not possible as I'm unable to set up any parameters that allow me to ssh to the server with ssh-agent enabled. I always receive: "connection refused", any good tutorials around other than the few mentioned previously? I've been searching Google to no avail.
Suggestions? 
Okay, now for problem #2: I'm having no luck forwarding an X11 session to a Win7 machine using PuTTY/Xming.
[From within ssh login to server]
 suprleg@Lenovo-H520:~$ cat /etc/ssh/sshd_config | grep X
X11Forwarding yes
X11DisplayOffset 10
suprleg@Lenovo-H520:~$ cat /etc/ssh/ssh_config | grep X
    ForwardX11 yes
#   ForwardX11Trusted yes
xauth seems to be in place.
suprleg@Lenovo-H520:~$ echo $DISPLAY
localhost:11.0
I'm just looking at a terminal screen no X, any ideas?

Thanks in advance.

---

### Post by suprleg on 2014-05-30
**Embarrassment**.... once I issued a command, such as "gedit", which required X11, it magically appeared.! :rolleyes:

---

