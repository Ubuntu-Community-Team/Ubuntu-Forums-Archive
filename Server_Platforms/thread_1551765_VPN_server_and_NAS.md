---
title: "VPN server and NAS"
date: 2010-08-12
forum: Server Platforms
---

### Post by eddawg128 on 2010-08-12
I have a VPN server setup using Lucid Lynx server edition for my office.  I am able to access the network through VPN and everything seems to be working properly on that end.  I have an NAS on the office network, but I have no idea how to get it setup for me to see it.  I am at a complete loss, since I am literally 3 days old to Linux.  The NAS is an LG N2B1DD2 with built in user control.  According to LG the NAS is compatible with Linux, Windows, and Mac OS.  I need to be able to use VPN to access the network and the NAS.  Any help would be appreciated.  Thank you.

---

### Post by arrrghhh on 2010-08-12
The NAS, it is on the same LAN as the VPN?  Can you access other things on your LAN other than the NAS?

Assuming the VPN and NAS are on the same LAN, you shouldn't really need to do much else outside of the VPN configuration which it sounds like you got working no problem...

---

### Post by eddawg128 on 2010-08-12
Yes they are on the same LAN.  I am able to ping the NAS as well, but I don't know how to access it.  Thanks for the quick response, appreciate the help.

---

### Post by arrrghhh on 2010-08-12
You don't know how to access it...?  Have you ever accessed it?

---

### Post by eddawg128 on 2010-08-12
Yes I have accessed it before.  I am able to access it from both Windows and Mac machines while on the LAN.  But this does not go through the Linux server at all.  I don't know how to access the file system from the Linux server.  And since the VPN is routed through the Linux server, I can't access the NAS remotely through that VPN tunnel.  Sorry if I am not explaining myself adequately, but I am very new to all of this.

---

### Post by arrrghhh on 2010-08-12
Hrm.  I may be the confused one, just because I don't know your network's topology.

So the VPN works.  Can you access other things within the LAN that you would normally only be able to access if you were there in the office?

If you can ping it, I'd say you should be able to access it.

---

### Post by eddawg128 on 2010-08-12
The problem with accessing other things on the network, is that there is nothing else to access.  It is the server machine, which I just setup, and the NAS.  The only other machines on the network are personal laptops that filter in and out with the employee's. So I don't know how to check.  I hate being noob, haha.

---

### Post by arrrghhh on 2010-08-12
You must have some sort of network gear - router, switch, something?

You said you can ping the NAS, but can't access it?  Can you try to nmap it to see what ports are open?  Nmap is available on both Windows and Linux.

---

### Post by dreamie on 2010-08-17
I also want to set up a configuration like this. Could it be something with your routing configuration?

---

### Post by redmk2 on 2010-08-17
@eddawg128 and @dreamie;

Do you have a GUI interface or just the CLI (terminal) at the Server when connected to the VPN?  By that I mean that is what you see on you local host from home.

---

### Post by spynappels on 2010-08-18
How do you access the share when you are on the LAN? By IP address or hostname?

Across a routed OpenVPN instance, you will need to map the NAS by IP address and then you should be able to access it.

---

### Post by eddawg128 on 2010-08-31
@redmk2 I am using the server edition of ubuntu which has no GUI.  I am doing everything off the terminal which for me is a new experience.  I am not sure if this is what you mean.

@spynappels When accessing the NAS, I use either the DNS or IP address from my windows machine. I hope this helps.  

I had to go out of town, so was unable to keep up with this thread, I apologize.

---

### Post by redmk2 on 2010-08-31
> **eddawg128 said:**
> @redmk2 I am using the server edition of ubuntu which has no GUI.  I am doing everything off the terminal which for me is a new experience.  I am not sure if this is what you mean.

@spynappels When accessing the NAS, I use either the DNS or IP address from my windows machine. I hope this helps.  

I had to go out of town, so was unable to keep up with this thread, I apologize.

I have the answer I was looking for:  your using the terminal (CLI).

I assume that you are able to browse to the shared directory on a windows machine while at your office.  Am I correct?

Can you post the output of ```
smbtree
```

---

### Post by eddawg128 on 2010-08-31
Yes I can browse the shared directory on a windows machine, while at the office. I can also browse it from an OS X machine.

---

### Post by redmk2 on 2010-08-31
> **eddawg128 said:**
> Here is the smbtree output:
```

Removed
```

Thanks for the prompt reply.

So the NAS is available to you.  It is running Samba and you can use the CLI to manipulate the data.

You can use ***smbclient ***to get to the data.  See this documentation```
man smbclient
```

Some personal observations:
[LIST=1]
[*]Smbclient is a lot like FTP from the command line.  This means it crude and cryptic, but can be done.
[*]You created the shares with a GUI interface.  It will be ugly for you to manipulate from the CLI due to the spaces and the length of the names.
[*]An alternative would be to mount all the shares to the local file system.
[/LIST]

So here we go --
To view a share we have to type the entire SMB resource at the command line.  Like this```
smbclient //LG-NAS/"volume1_public Default folder of volume1_public"   #note the quotes
```

Whew!  My fingers hurt already.  Now you know why command line geeks use short names with no spaces.  :-)  

See the command prompt ```
smb: \>
```
From there you can see what is in the share with ```
smb: \>ls
```

You can see a list of commands with ```
smb: \>?
```

To mount the shares locally you need to edit the /etc/fstab file.  See here```
man fstab
```

---

### Post by dmizer on 2010-08-31
> **redmk2 said:**
> To view a share we have to type the entire SMB resource at the command line.  Like this```
smbclient //LG-NAS/"volume1_public Default folder of volume1_public"   #note the quotes
```

In smbtree, there are two elements, the share path and the description field.

I hope that no one minds that I edited the post so that code tags are used instead of quote tags. So the ACTUAL smbtree output would look like this ...
```
WORKGROUP
        \\LG-NAS                        LG-NAS server
                \\LG-NAS\[COLOR="Red"]volume1_public[/COLOR]         [COLOR="Blue"]Default folder of volume1_public[/COLOR]

```
Where
[COLOR="Red"]volume1_public[/COLOR] is the actual share name
[COLOR="Blue"]Default folder of volume1_public[/COLOR] is the description field

Since the description field is not needed to mount the share, the actual smbmount command would look like this ...
```
smbclient //LG-NAS/volume1_public
```
Now, keep in mind that this will only work if your VPN server is forwarding your remote LAN DNS. You may also have to change your default route to the VPN connection on the client.

---

### Post by eddawg128 on 2010-08-31
I believe that the "Default folder of volume1_public" is just a comment.  That is not part of the folder name when I look it up in Windows.  In the NAS server menu, that shows up under a heading called folder description.  That is far too much to type even in a GUI in my opinion.  I will try this later tonight when I get home.  Thanks for all your help.

---

### Post by redmk2 on 2010-08-31
> **eddawg128 said:**
> I believe that the "Default folder of volume1_public" is just a comment.  That is not part of the folder name when I look it up in Windows.  In the NAS server menu, that shows up under a heading called folder description.  That is far too much to type even in a GUI in my opinion.  I will try this later tonight when I get home.  Thanks for all your help.

Yes, @dmizer is correct.  You only need the NetBIOS name and actual share name.  

I don't add a share description on my Samba shares so I missed that when looking at my output.  :redface:

---

