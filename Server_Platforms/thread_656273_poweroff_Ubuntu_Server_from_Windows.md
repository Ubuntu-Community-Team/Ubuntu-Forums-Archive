---
title: "poweroff Ubuntu Server from Windows"
date: 2008-01-02
forum: Server Platforms
---

### Post by Carlos Pena on 2008-01-02
Hi guys,

I have a Windows Server and  an Ubuntu Server. I need to send a poweroff command to my ubuntu server from Windows. In other words i want to shutdown both servers by clicking a simple shortcut. 

Any idea?

Carlos Pena
Santo Domingo, Dominican Republic

---

### Post by andol on 2008-01-02
Well, my spontanious solution involves sending a shutdown command piped through ssh. For that you need an ssh-client which allows you to send commands. If you use the cygwin version of openssh it will look somehow like this.

```
ssh -l root ubuntuserver.domain.tld "shutdown -h now"
```

That is a line you then can wrap into a bat- or cmd-script, allow you to click on it.

For it to work without you having to type in the root-password each and every time you can set up ssh-keys which takes care of the authentication. Of course, by doing that you more or less put the security of your ubuntu-server in the hands of your Windows server. If you decide to go with the ssh-key approach I will recommend you to use a dediced key for it ( ssh -i /path/to/key ...) for which you in authorized_keys, on the ubuntu server,  can specify exactly what command it will run.

---

### Post by Brazen on 2008-01-02
I believe you can use the Putty ssh client from the command line.

---

### Post by doogy2004 on 2008-01-02
> **Brazen said:**
> I believe you can use the Putty ssh client from the command line.

by using plink.exe it is a slimmed down version of putty that runs from the command line.

---

### Post by Carlos Pena on 2008-01-07
Thank you guys!.


I did the following:


On Ubuntu server:

I installed the openssh-server

sudo apt-get install openssh-server


On Windows:

I download the plink.exe program from PuTTY Telnet client web page.

Create a shortcut to run the command:

plink -pw <user password>   <user>@ubuntuservername  sudo -S <rootpassword.dat  poweoff


The sudo parameter  "-S <rootpassword.dat " will get the root password from a ASCII file on client computer (in this case "rootpassword.dat") instead of keyboard.

This will run a fully unattended ubuntu shutdown from windows.

---

