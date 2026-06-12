---
title: "Is the &quot;smb.conf&quot; file under Ubuntu different?"
date: 2005-03-02
forum: Server Platforms
---

### Post by joplass on 2005-03-02
Guys,
Is there something different one has to know about “smb.conf” under Ubuntu?  I have done everything I did before under other distros and samba does not seem to work.  For example I use: “/etc/rc.d/init.d/smb restart” to shut down and restart samba.  But I am getting back “file does not exist”.  I modified the file to something simple and I don’t know why it does not work, the machine does not even appear on the network.

# Global Parameters

workgroup  =  NETWORKNAME
netbios name  =  Ubuntu
encrypt passwords  =  yes

[home]
path  =  /home
read only  =  no
browseable  =  yes
write list  = ME
valid users  =  ME

Thank you in advance,

---

### Post by Rottweiler on 2005-03-02
The smb.conf file is exactly the same as other distros. I'd recommend you start by making small additions to the supplied /etc/samba/smb.conf file rather than rolling your own. The one you posted is a bit too stripped down for my taste.

The command should be:
 ```
sudo /etc/init.d/samba restart
``` 
The "file does not exist" is likely because you're trying to execute an init script that is not there.

Have you installed samba?
```
sudo apt-get update && sudo apt-get install samba
```

---

### Post by joplass on 2005-03-02
Yes, samba is installed.  I will try your suggestions as soon as I get home.  
Thanks for the reply.

---

### Post by joplass on 2005-03-03
Alright! Something very interesting here.  With the above smb.file I can browse, read, and write my entire network but from the other machine I can’t see the samba machine.

---

### Post by Rottweiler on 2005-03-03
"workgroup" is usually the first suspect there.

---

### Post by joplass on 2005-03-03
[QUOTE=Rottweiler]"workgroup" is usually the first suspect there.[/QUOTE]

I will check on that maybe a typo here or there.  But if that is the case I could I be able to use the rest of the network from my Ubuntu box but I can't do the same from the windows machines.

---

### Post by Rottweiler on 2005-03-03
Some troubleshoting thoughts ...

On one of the "non working" Windows boxes:

- Make sure you can ping the server
ping 192.168.0.2   (or whatever the addr is)

- Try connecting to it by ip address
Start...Run...\\192.168.0.2   (or whatever the addr is)

- Try connecting to it by name
Start...Run...\\Server   (or whatever the name is)

What versions of Windows are the clients running?

Try making a very "public" Samba share:
security = share
[Public]
   path = /path/to/somewhere
   public = yes
   writable = yes
   browseable = yes

Just some things to try.

---

### Post by joplass on 2005-03-04
[QUOTE=Rottweiler]Some troubleshoting thoughts ...

On one of the "non working" Windows boxes:

- Make sure you can ping the server
ping 192.168.0.2   (or whatever the addr is)

- Try connecting to it by ip address
Start...Run...\\192.168.0.2   (or whatever the addr is)

- Try connecting to it by name
Start...Run...\\Server   (or whatever the name is)

What versions of Windows are the clients running?

Try making a very "public" Samba share:
security = share
[Public]
   path = /path/to/somewhere
   public = yes
   writable = yes
   browseable = yes

Just some things to try.[/QUOTE]

Oh, yes I forgot the ping shish!!!

---

### Post by joplass on 2005-03-04
Ok, I am now able to see Ubuntu on the windows machine but I am not able to open it because it does not recognize the username and password I created.  To do so I used the following commands:

$ sudo useradd –d /home/username –s /bin/false/ -n username
$ sudo passwd username
$ sudo smbpasswd –a username

I have been using them under other distros like this:

# useradd –d /home/username –s /bin/false/ -n username
# passwd username
# smbpasswd –a username

Meanwhile Ubuntu does not like “-n” I get an error with it and went I take it out samba let me created a samba username and its password without a glitch.  Is there another way or a special way to add a user and its password for samba under Ubuntu?

---

### Post by Rottweiler on 2005-03-04
Not to my knowledge.

The -'n' is a RedHatism, not part of the "standard" useradd.

I'd recommend first creating a wide-open public share and make sure you can connect to it, read, and write to it. This makes sure all the "infrastructure" stuff is working right.

Also, I noticed in your first post that you're attempting to share /home. That's an odd and very dangerous thing to do. Permission problems would be innumerable.

Try a share like this:

security = share
 [Public]
    path = /home/samba/public
    public = yes
    writable = yes
    browseable = yes

Note the "security = share" line eliminates most authentication worries for now. It will replace any "security = user" line.

Create the above like this:
sudo mkdir /home/samba
sudo mkdir /home/samba/public
sudo chown -R nobody: /home/samba
sudo chmod -R 777 /home/samba

Poke samba to make sure it re-reads the new config:
sudo /etc/init.d/samba restart

If that all works you can build fancier schemes from there.

---

### Post by joplass on 2005-03-05
Thanks a lot for your assistance.  I can now browse the entire network as well as share files from one box to another.

---

