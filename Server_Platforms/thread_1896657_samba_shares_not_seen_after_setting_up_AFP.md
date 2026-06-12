---
title: "samba shares not seen after setting up AFP"
date: 2011-12-17
forum: Server Platforms
---

### Post by mons00n on 2011-12-17
Hi everyone,

I'm running 10.04 as a simple file server and have ran into a slight snag.  Up until recently I was sharing my files via samba and all was well.  My shares mainly store videos and my large music collection - which posed a problem for my mac; connecting to the share via smb rendered iTunes slow when managing/browsing music.  I ran into this link:

[http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/](http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/)

which walked me through setting up AFP (Netatalk + Avahi).  My itunes works great now and the share works beautifully with all my macs, BUT now my other samba shares don't show up in explorer etc etc.  I can connect to them manually but they all require authentication when they didn't before.  Any ideas on why this might be?  I'm still fairly new to all these different protocols and how they work together.  Thanks for your time!

---

### Post by docbop on 2011-12-17
AFP != CIFS

Apple's file format is incompatible with CIFS/SMB that Windows uses. That's why switching from SaMBa format to AFP made them disappear to SaMBa and Windows clients.   That's why Apple offers CIFS/SMB to share with rest of the world.

---

### Post by mons00n on 2011-12-17
> **docbop said:**
> AFP != CIFS

Apple's file format is incompatible with CIFS/SMB that Windows uses. That's why switching from SaMBa format to AFP made them disappear to SaMBa and Windows clients.   That's why Apple offers CIFS/SMB to share with rest of the world.

ah I see, so I should only be running ONE of the two?  If so can I disable samba without removing it (just in-case, I can be paranoid)?

---

### Post by capscrew on 2011-12-17
> **mons00n said:**
> ah I see, so I should only be running ONE of the two?  If so can I disable samba without removing it (just in-case, I can be paranoid)?

In theory you should be able to run both protocols (SMB/CIFS and AFP) on the same network.  Samba uses NETBIOS naming and can be configured to broadcast that over TCP/IP without the need of /etc/hosts or DNS or mDNS (AVAHI (bonjour)).

Please post the output of this```
smbtree
```

---

### Post by mons00n on 2011-12-17
> **capscrew said:**
> Please post the output of this```
smbtree
```

```

bob@Newton:~$ smbtree
Enter bob's password: 
WORKGROUP
	\\READYSHARE     		NETGEAR WNDR3700
		\\READYSHARE\IPC$           	IPC Service (NETGEAR WNDR3700)
	\\NEWTON         		Newton server (Samba, Ubuntu)
		\\NEWTON\IPC$           	IPC Service (Newton server (Samba, Ubuntu))
		\\NEWTON\Main        

```

Thanks for the help BTW!

---

### Post by capscrew on 2011-12-17
> **mons00n said:**
> ```

bob@Newton:~$ smbtree
Enter bob's password: 
WORKGROUP
	\\READYSHARE     		NETGEAR WNDR3700
		\\READYSHARE\IPC$           	IPC Service (NETGEAR WNDR3700)
	\\NEWTON         		Newton server (Samba, Ubuntu)
		\\NEWTON\IPC$           	IPC Service (Newton server (Samba, Ubuntu))
		\\NEWTON\Main        

```

Thanks for the help BTW!

I can see you have two hosts (READYSHARE  and NEWTON).  Samba is working.  Do you have shares on READYSHARE?  It appears you have a share on NEWTON called Main.

This shows me that there is a Local Master Browser (LMB) and that it holds a working Browse List.  You can see this with the command ```
findsmb
```  Please post the results of that command,

Are you able to browse the share at all?  Are there other shares that we can't see?

---

### Post by mons00n on 2011-12-17
> **capscrew said:**
> I can see you have two hosts (READYSHARE  and NEWTON).  Samba is working.  Do you have shares on READYSHARE?  It appears you have a share on NEWTON called Main.

The readyshare is just my router - not used.  The share on NEWTON called Main is the share that should not require authentication - but does since installing AFP.

> **capscrew said:**
> 
This shows me that there is a Local Master Browser (LMB) and that it holds a working Browse List.  You can see this with the command ```
findsmb
```  Please post the results of that command,

Are you able to browse the share at all?  Are there other shares that we can't see?
I can connect to all samba shares with authentication if I try to connect directly to them, but the share "Main" is no longer browsable (it was before).  I have 2 other samba shares that are hidden and require authentication so those are still working.

```

bob@Newton:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.1     READYSHARE    +[WORKGROUP] [Unix] [Samba 3.0.24]
192.168.1.18    NEWTON         [WORKGROUP] [Unix] [Samba 3.4.7]
bob@Newton:~$ 

```

Hrm....seeing as the LMB is next to the READYSHARE I'm assuming that could cause problems (it has always been enabled, just never put to use)?

---

### Post by capscrew on 2011-12-17
> **mons00n said:**
> The readyshare is just my router - not used.  The share on NEWTON called Main is the share that should not require authentication - but does since installing AFP.
There can be several reasons for this, but I believe that you can add your name to keyring when first authenticating to the share.  Then you won't have to authenticate manually any more.  My guess is that the hostname has changed from **hostname** to **hostname.[COLOR="Red"]local[/COLOR]**.  This would mean a new entry in the keyring.

That being said, what does the share configuration look like?> 

I can connect to all samba shares with authentication if I try to connect directly to them, but the share "Main" is no longer browsable (it was before). 
Are you saying it is NOT visible in Nautilus under Places>>Network.  the command *smbtree *is the command line  equivalent of browsing the shares.  It is displaying the //HOST/share on NEWTON correctly.  
> 
I have 2 other samba shares that are hidden and require authentication so those are still working.
Like [homes] shares.  :-)> 
```

bob@Newton:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.1     READYSHARE    +[WORKGROUP] [Unix] [Samba 3.0.24]
192.168.1.18    NEWTON         [WORKGROUP] [Unix] [Samba 3.4.7]
bob@Newton:~$ 

```

Hrm....seeing as the LMB is next to the READYSHARE I'm assuming that could cause problems (it has always been enabled, just never put to use)?
No, it should not create a problem.  The router has NAS capabilities; Samba is running. READYSHARE has "won the election" in the network to be the LMB.  It is up (on) all the time, and it's at least consistent.

---

