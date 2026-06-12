---
title: "Samba File Sharing Setup"
date: 2012-02-20
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-02-20
Hello Everyone,
   I had SAMBA setup on my server for file sharing and all of the sudden it stopped showing the server in the network. When I did the initial setup at the very end I did the "sudo restart" for both "smbd" and "nmbd" and they both restarted just fine. Now when I went back through it and tried to restart both those on the "sudo restart nmbd" I get an error. I have the screen shot attached. Can someone please help me figure out why I can't see this anymore in my network. I also have Ushare setup to stream my movies to my xbox and that is still working fine....

---

### Post by 2F4U on 2012-02-20
If this is 10.04 or later, I think you should use

sudo service smbd restart
sudo service nmbd restart

---

### Post by bab1 on 2012-02-20
> **TFroehlich3 said:**
> Hello Everyone,
   I had SAMBA setup on my server for file sharing and all of the sudden it stopped showing the server in the network. When I did the initial setup at the very end I did the "sudo restart" for both "smbd" and "nmbd" and they both restarted just fine. Now when I went back through it and tried to restart both those on the "sudo restart nmbd" I get an error. I have the screen shot attached. Can someone please help me figure out why I can't see this anymore in my network. I also have Ushare setup to stream my movies to my xbox and that is still working fine....

Check to see if both are running ```
pgrep -l mbd
```

You should have the following```
$ pgrep -l mbd
990 smbd
1039 nmbd
1214 smbd
1497 smbd

```

If there is no *nmbd daemon *running in the first place, then it's logical that you can't restart it. Try starting it with```
sudo start nmbd
```

---

### Post by TFroehlich3 on 2012-02-20
I figured it out. All I did is just uninstalled Samba

```
sudo apt-get remove samba
```

And then just re-installed it

```
sudo apt-get install samba
```

All of the config files were not deleted so I didn't have to reconfigure this file

```
/etc/samba/smb.conf
```

Thank you for all your help though! Now I can now easily add more movies to my sever without having to have SFTP on every machine on my network. :)

---

