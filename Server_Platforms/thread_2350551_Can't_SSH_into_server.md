---
title: "Can't SSH into server"
date: 2017-01-25
forum: Server Platforms
---

### Post by Mike_Hughes on 2017-01-25
I had to rebuild my Server that has been running fine for the past 5 or so years. I installed proftpd and now I can't SSH into the server. Here is the error I am getting when I try -  
```
admin$ ssh [email]macmike@www.mikealrhughes.com[/email]
Connection closed by X.X.X.X port 22
```

---

### Post by SeijiSensei on 2017-01-25
You're sure that openssh-server is installed and running on the server?

---

### Post by darkod on 2017-01-25
In addition to Sensei's question, are you sure you have a correct firewall rule to allow ssh port 22? You seem to be accessing by public www record so having a firewall is a must. And correct config to allow ssh through for you.

Also, since you reinstalled the server it will have different thumbprint now and you will have conflicting entries in the known_hosts file on the client. But in such cases the error should be different.

---

### Post by Mike_Hughes on 2017-01-25
That is what I wondered about was the client side. At the time I had the above error my thinking was a key miss match. No it will not connect at all. Says can't connect. Before I had to rebuild SSH worked great! I could use get in through FileZilla as well. Now neither will connect. I would rather do server work through SSH or FileZilla. At some point I want to put gnome on the server. I was able to see the OpenSSH server in Webmin. When I try to get in through client terminal says can't connect try again later.

I can see the SSH server through Webmin.

---

### Post by raja.genupula on 2017-01-26
Hello,

what is the output of 

```
telnet <hostname> 22 
```

and post here output of 

```
ssh -vvvv username@hostname
```

Thank you.

---

### Post by mhpreach on 2017-01-27
Here is the telnet 

```
Trying 24.72.189.165...
Connected to mikealrhughes.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
```

Here is the results from ssh -vvv [email]macmike@www.mikealrhughes.com[/email]

```
ssh -vvvv [email]macmike@www.mikealrhughes.com[/email]
OpenSSH_7.3p1, LibreSSL 2.4.1
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 20: Applying options for *
debug2: resolving "www.mikealrhughes.com" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to [www.mikealrhughes.com](www.mikealrhughes.com) [24.72.189.165] port 22.
debug1: Connection established.
debug1: identity file /Users/admin/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/admin/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/admin/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/admin/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/admin/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/admin/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/admin/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/admin/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.1 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to [www.mikealrhughes.com:22](www.mikealrhughes.com:22) as 'macmike'
debug3: hostkeys_foreach: reading file "/Users/admin/.ssh/known_hosts"
debug3: record_hostkey: found key type RSA in file /Users/admin/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys from [www.mikealrhughes.com](www.mikealrhughes.com)
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ssh-rsa-cert-v01@openssh.com[/email],rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
Connection closed by 24.72.189.165 port 22
```

---

### Post by geeksmith on 2017-01-27
I would suggest that your sshd config is messed up, as the most basic key exchange process doesn't complete. You could rename /etc/ssh and "sudo apt-get --reinstall install openssh-server", I suppose. That's going to generate new host keys, which might make your ssh client cranky the first time you connect, but would otherwise be fairly harmless.

---

### Post by Mike_Hughes on 2017-01-27
I figured out I have to get a GUI on this server. Going from Server to a Live CD to rename and back sure takes some time! That's my next thing to do for sure. Well, take that back got to find some one to help me with some Wordpress issues.

It doesn't like the -reinstall

---

### Post by geeksmith on 2017-01-27
Did you use 2 hyphens?
```
sudo apt-get --reinstall install openssh-server
```

---

### Post by Mike_Hughes on 2017-01-27
Reply still have the message unable to connect to server try againlater

---

### Post by geeksmith on 2017-01-27
SSH isn't running on your host.
```

~/ nmap -p22 www.mikealrhughes.com

Starting Nmap 7.12 ( https://nmap.org ) at 2017-01-27 19:25 PST
Nmap scan report for www.mikealrhughes.com (24.72.189.165)
Host is up (0.19s latency).
rDNS record for 24.72.189.165: h165.189.72.24.cable.sprn.cmaaccess.com
PORT   STATE  SERVICE
22/tcp closed ssh

Nmap done: 1 IP address (1 host up) scanned in 0.54 seconds

```

This command used to show port 22 as open, now it's closed.

You need to reinstall openssh-server with the command supplied above. If it's already installed correctly, you need to restart the service like so:
```

sudo systemctl restart ssh

```

---

### Post by Mike_Hughes on 2017-01-27
Also got a message cannot create /etc/ssh/sshd_config: Directory nonexistent
dpkg package error processing package openssh-server (--configure):
subprocess installed post-installation script returned error exit status 2
subprocess /use/bin/dkpkg returned an error code (1)

I got a lot of warnings about some directories in /etc/ufw being group writable!  Some under /lib
 some under /usr being group writable as well

---

### Post by geeksmith on 2017-01-27
Earlier I asked you to rename the /etc/ssh directory, which has made the installer cranky. If you rename it back, then just rename /etc/ssh/sshd_config it might get happier when running the reinstall command.

If you paste the output you see on the screen in a "code" comment (use the advanced editor, highlight the text, and hit the '#' button above the editor box) we'll be able to help more effectively. General descriptions of what you see is never as useful the actual data.

---

### Post by Mike_Hughes on 2017-01-27
Easier said than done no GUI on the server.

How do I rename a directory and file w/o rebooting into live CD?

---

### Post by darkod on 2017-01-28
You rename with the command mv. If you use different path in the new filename the command is also used to move files, not just to rename them. It is used both for folders and files.
```
sudo mv /path/oldname /path/newname
```

I assume you are not using root directly so I used sudo in front.

You mention ufw, are you using it? You might not have configured port 22 rule correctly. It's better to use iptables directly than the ufw front that also uses iptables in the backend.

Like suggested earlier you should try reinstalling openssh-server and also you can try temporarily disabling the firewall to make sure it is not preventing you establish ssh session.

You are running the reinstall command with sudo right? If you don't run install commands with sudo it might be the reason it says it can't create folders. Otherwise it should be fine.

You need to run all system commands with your admin user and with sudo in front.

---

### Post by raja.genupula on 2017-01-28
Some where I read,  the user you are using have home directory right?

---

### Post by Mike_Hughes on 2017-01-28
> **darkod said:**
> You rename with the command mv. If you use different path in the new filename the command is also used to move files, not just to rename them. It is used both for folders and files.
```
sudo mv /path/oldname /path/newname
```

I assume you are not using root directly so I used sudo in front.

You mention ufw, are you using it? You might not have configured port 22 rule correctly. It's better to use iptables directly than the ufw front that also uses iptables in the backend.

Like suggested earlier you should try reinstalling openssh-server and also you can try temporarily disabling the firewall to make sure it is not preventing you establish ssh session.

You are running the reinstall command with sudo right? If you don't run install commands with sudo it might be the reason it says it can't create folders. Otherwise it should be fine.

You need to run all system commands with your admin user and with sudo in front.

When I changed the name back for ssh directory and changed the name of the file sshd_conf to old_sshd_conf

when I try to restart I get job for ssh. Service failed because the control process exited with error code.

---

### Post by darkod on 2017-01-28
Well if you rename the file the service won't be able to start. The suggestion was to rename the file and try to reinstall openssh-server, not to rename and try to restart the service. What are you actually trying to do? Please post commands and output so we can also see because there seems to be a lot of miscommunication and guessing around.

ssh is not workign right now, right? So you should be safe to even try purging the package completely, that will delete current config, and then install it. First try simply reinstalling, and if not, then purge and install.

Option 1:
```
sudo apt-get install --reinstall openssh-server
```

Option 2:
```
sudo apt-get purge openssh-server
sudo apt-get install openssh-server
```

---

### Post by Mike_Hughes on 2017-01-28
Ok I guess this isn't going to cooperate with me.
 Here is what I received when I ran - systemctl status ssh.serve
ssh.service - OpenBSD secure shell server
Loaded: Loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
Active inactive (dead) (Result: exit-code) since Sat 2017-01028 14:50:49 CST; 3min 54s ago
Process: 9011 ExecStart=usr/sbin/sshd -D $$SSHD_OPTS (code=exited, status-1/FAILURE)
Main PID: 9011 (code=exited, status=1/FAILURE

systems[1]: Failed to start OpenBSD Secre Shell server.
ssh.service:Unit entered failed state.
ssh.service: failed with result 'exit-code'.
ssh.service: Service hold-off time over, scheduling restart.
Stopped OpenBSD Secure Shell server.
ssh.service:Start request repeated too quickly
Failed to start OpenBSD Secure Shell server.

when i did the --reinstall install

---

### Post by Mike_Hughes on 2017-01-28
[img]img_0324.jpg[/img]

---

### Post by darkod on 2017-01-28
The images can't be seen. Go to Advanced Mode when posting and attach them as attachments. Or use Insert Image.

But attachment is better.

---

### Post by Mike_Hughes on 2017-01-28
I did a sudo apt auto remove lib-common. I had a message said didn't need to run it. After I did I was able to restart the sudo systemctl restart ssh. When I did it appeared to start. I went to terminal tried to ssh in and received this: How do I get rid of the key it is referring to?

```
Last login: Sat Jan 28 14:59:41 on console
MacBook-Pro:~ admin$ ssh macmike@www.mikealrhughes.com
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:PdooS4JnEE5jhf9uqJwM2Nr1szky8Hyx+usc6F0R/k4.
Please contact your system administrator.
Add correct host key in /Users/admin/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/admin/.ssh/known_hosts:2
RSA host key for www.mikealrhughes.com has changed and you have requested strict checking.
Host key verification failed.
MacBook-Pro:~ admin$
```

---

### Post by Mike_Hughes on 2017-01-28
Ok I was able to finally ssh on my iPad. Apparently in on my MacBook Pro. I need to go to - /Users/admin/.ssh/known_hosts
add the new key. Problem is I can't get to the .ssh directory. Apparently a hidden directory. Does anyone know how to get to a hidden directory on a Mac?

---

### Post by darkod on 2017-01-28
Adding the new key will be done automatically, usually it will ask you for confirmation and add it itself. No need for manual adding.

But you do have to manually remove the offending key because after rebuilding the server the thumbprint changed. And ssh is very careful with security and doesn't accept such changes. The message says the offending key is in /Users/admin/.ssh/known.hosts:2

How you open that file on Mac I can't tell you exactly, but google is your friend and it shouldn't be difficult to find out. Remove the key referring to your server, save and close the file and you're good to go.

---

### Post by Mike_Hughes on 2017-01-28
Thanks for you help doing the apt auto remove fixed. 
FYI on the to get to the .ssh directory I had to choose go to directory then a line came up and I typed .ssh and walla there it was. Removed two files went back in and it set me up.
Thanks to all of you fellows, I will dance at your wedding. Now to get to the Wordpress issues.

---

### Post by darkod on 2017-01-29
If you solved the issue please mark the thread as solved. You can do that in Thread Tools above the first post.

---

