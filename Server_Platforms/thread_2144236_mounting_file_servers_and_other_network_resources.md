---
title: "mounting file servers and other network resources"
date: 2013-05-11
forum: Server Platforms
---

### Post by Vegan on 2013-05-11
I have Windows and Linux in virtual machines, so can I get Linux to mount a file server share?

such as //fileserver1/array1

also how about dealing with credentials for the servers etc

I am using Windows Server for the file server, and I also know how to use SAMBA a bit

---

### Post by darkod on 2013-05-11
If you want to use the server name first make sure the ubuntu machine can resolve it. You can always use the server IP.

The temporary mount from command line should be something like:
```
sudo mount -t cifs //serverIP/sharename /mountpoint -o username=username,password=password
```

You can set a permanent mount in /etc/fstab which should look like:
```
//serverIP/sharename   /mountpoint   cifs   _netdev,username=username,password=password   0   0
```

I think that chould work. The _netdev option is letting the OS know it's a network resource, so it can wait a little if finding the share takes long time. If you want to, instead of putting the username and password in /etc/fstab you can put them in a file and use that with the option credentials=/path/filename

---

### Post by rubylaser on 2013-05-12
Just one other thought to add onto Darko's great directions. If you don't want to have your username and password in /etc/fstab, you can create a file that contains them and make it only readable by root.

```
nano [COLOR=#000000]/root/.smbcredentials[/COLOR]
```
Put your username and password in that file like this.
```
[COLOR=#000000]username=myusername
[/COLOR][COLOR=#000000]password=mypassword[/COLOR]
```

chmod the file like this
```
[COLOR=#000000]chmod 700 /root/.smbcredentials[/COLOR]
```

Finally, slightly modify the /etc/fstab line that Darkod gave you.
```
[COLOR=#000000][FONT=Ubuntu Mono]//serverIP/sharename   /mountpoint   cifs   _netdev,[/FONT][/COLOR][COLOR=#000000]credentials=/root/.smbcredentials[/COLOR][COLOR=#000000][FONT=Ubuntu Mono] 0   0[/FONT][/COLOR]
```

---

### Post by prodigy_ on 2013-05-12
> **darkod said:**
> ```
//serverIP/sharename   /mountpoint   cifs   _netdev,username=username,password=password   0   0
```
AFAIK, cifs doesn't honor **_netdev**. I mount cifs shares from /etc/rc.local but that's with static IP configured in /etc/network/interfaces. Not sure if that would work with Network Manager.

For Windows servers you also need to add **domain=domain_name** option if your server is in a domain or **workgroup=workgroup_name** otherwise. Substitute your actual domain or workgroup name. The **workgroup** option is rarely mentioned in HOWTOs but it's necessary.

---

