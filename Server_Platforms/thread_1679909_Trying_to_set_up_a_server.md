---
title: "Trying to set up a server"
date: 2011-02-01
forum: Server Platforms
---

### Post by stalemath on 2011-02-01
I am trying to set up a server using the tutorial here: [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

However, I am using Xubuntu 10.04 and I'm encountering some issues since this tutorial was written for an older version.

Is there any good guide that can be suggested to me for this since I am new to Linux?

---

### Post by rudelgurke on 2011-02-01
And what are the issues ? Installation, Samba, Ftp, SSH, VNC configuration or something else ?
Basically this guide should still work.

---

### Post by stalemath on 2011-02-01
Well, when I got to the 4th step (Samba), I encountered some differences in the smb.conf file, however, I think I may have done that part correctly. I am now to access my server (bottom of 4th page :  **\\(whatever the IP of the server is)\homes **) from a Mac, and can't exactly figure that out.

---

### Post by rudelgurke on 2011-02-01
And if you run "smbclient -L _the_ip_of_your_server_" your shares are correctly shown ?
If so, problem may be on the client or authentication related that your Mac can't authenticate against your Samba server.
In both cases - /var/log/samba.log - might be helpful to provide additional information what may be wrong.

---

### Post by stalemath on 2011-02-01
> **rudelgurke said:**
> And if you run "smbclient -L _the_ip_of_your_server_" your shares are correctly shown ?
If so, problem may be on the client or authentication related that your Mac can't authenticate against your Samba server.
In both cases - /var/log/samba.log - might be helpful to provide additional information what may be wrong.

I don't think anything went wrong (yet)... I am just trying to connect to the server through a Mac. I don't know how.

---

### Post by rudelgurke on 2011-02-01
[http://support.apple.com/kb/ht1568](http://support.apple.com/kb/ht1568)

Maybe helps then on how to connect via OSX to a Samba share. :)

If the problem is just related to the Mac on the client side.

---

### Post by stalemath on 2011-02-01
I figured out how to connect using this guide:  [http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173](http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173)

However, I cannot seem to figure out how to access [homes]... I enabled  it in smb.conf, but it's still only showing print$ (as was the default  option in smb.conf)

---

### Post by lisati on 2011-02-01
> **stalemath said:**
> I figured out how to connect using this guide:  [http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173](http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173)

However, I cannot seem to figure out how to access [homes]... I enabled  it in smb.conf, but it's still only showing print$ (as was the default  option in smb.conf)

This might seem like a silly question but it might be worth a shot: did you restart samba after changing the settings?

---

### Post by stalemath on 2011-02-01
> **lisati said:**
> This might seem like a silly question but it might be worth a shot: did you restart samba after changing the settings?

I thought I did, by typing **sudo /etc/init.d/samba restart** but it says: command not found

---

### Post by lisati on 2011-02-01
> **stalemath said:**
> I thought I did, by typing **sudo /etc/init.d/samba restart** but it says: command not found

In newer versions of Ubuntu, an alternative is:
```

sudo service samba restart

```

---

### Post by stalemath on 2011-02-01
I read elsewhere to type this */etc/init.d/smbd restart*

and that seemed to have an effect
It said
```

Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service smbd restart

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the restart(8) utility, e.g. restart smbd
smbd start, running process 5199

```

So I entered *service smbd restart*, and I got:
```

smbd start/running, process 5213

```

However, after I disconnected/reconnected, it still doesn't show *homes*

---

### Post by stalemath on 2011-02-01
> **lisati said:**
> In newer versions of Ubuntu, an alternative is:
```

sudo service samba restart

```

I got that, and I guess it restarted. But *homes* still isn't appearing after I disconnect/reconnect to the server

---

### Post by SeijiSensei on 2011-02-01
The [homes] share is a generic reference to all the users' home directories.  If user shirley has an account on the server, and there's a corresponding entry for shirley in smbpasswd, then connecting with shirley's username and password will result in mounting /home/shirley. 

So rather than connecting to \\server\homes or something like that, you want to connect to \\server\shirley with her username and password.

---

### Post by stalemath on 2011-02-02
> **SeijiSensei said:**
> The [homes] share is a generic reference to all the users' home directories.  If user shirley has an account on the server, and there's a corresponding entry for shirley in smbpasswd, then connecting with shirley's username and password will result in mounting /home/shirley. 

So rather than connecting to \\server\homes or something like that, you want to connect to \\server\shirley with her username and password.

It's not letting me connect that way

---

### Post by SeijiSensei on 2011-02-02
I'm sorry; you're using a Mac it appears.  Try using smb://server/username as described in the techrepublic link you posted above.  Windows uses the "\\server\share" method of naming; *nix systems like Linux and OS X use the URL style of "smb://server/share".

Just to make sure, have you [set up user accounts in Samba]("https://help.ubuntu.com/community/Samba/SambaServerGuide#File%20Sharing%20%28Basics%29") via smbpasswd as well as in Linux?

---

### Post by stalemath on 2011-02-02
> **SeijiSensei said:**
> I'm sorry; you're using a Mac it appears.  Try using smb://server/username as described in the techrepublic link you posted above.  Windows uses the "\\server\share" method of naming; *nix systems like Linux and OS X use the URL style of "smb://server/share".

Just to make sure, have you [set up user accounts in Samba]("https://help.ubuntu.com/community/Samba/SambaServerGuide#File%20Sharing%20%28Basics%29") via smbpasswd as well as in Linux?

Thanks, but I am aware of the difference, as I was able to connect by just typing smb://server, but when I did smb://server/share it said:

```

The volume [share] could not be mounted.

```

And yes I did set up my user accounts, I know because when I connected with smb://server, my username appeared and it prompted me for my password. I then connected and it only showed print$ (which is enabled by default in the smb.conf file)

---

### Post by stalemath on 2011-02-02
Nevermind, I figured out how to enable homes, but when I try to mount it, it says The volume "homes" could not be mounted.

---

