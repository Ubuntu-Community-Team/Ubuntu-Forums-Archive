---
title: "Configuring NFS Shares"
date: 2009-03-03
forum: Server Platforms
---

### Post by crokett on 2009-03-03
My desktop at work is running Ubuntu 8.10 and after XP crashed last night and was unrecoverable, now my laptop is. :D  I have a Samba share on the desktop that I want to replace with an NFS share.  It appears to configured correctly because when I run showmount --export from the NFS server I get this:

```

greendm@hawking:~$ showmount --exports
Export list for hawking:
/home/greendm/SANCentral Copernicus

```

However when I try to mount the share on the laptop I get this:
```

greendm@Copernicus:~$ sudo mount -t nfs4 -o proto=tcp,port=2049 hawking:/home/greendm/SANCentral /home/greendm/hawkingsc/
mount.nfs4: mounting hawking:/home/greendm/SANCentral failed, reason given by server:
  No such file or directory

```

and showmount -a on the laptop shows this. It suggests the laptop is not seeing the share.  

```

greendm@Copernicus:~$ showmount -a
portmap getport: RPC: Success

```

Here is /etc/exports

```

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
# SANCentral Share
/home/greendm/SANCentral Copernicus(rw,fsid=0,no_subtree_check,sync)


```

I verified the firewall on the desktop is allowing the laptop to connect, or at least the laptop is not timing out. What else am I missing?  I tried changing permissions to allow world to read/write.  That did not work either.

---

### Post by HermanAB on 2009-03-03
Try the squash_all option and specify the anonymous UID and GID to match the share owner on the server.

Cheers,

Herman

---

### Post by crokett on 2009-03-03
Did not work.  Same error.

---

### Post by Gramps on 2009-03-03
Do you have the server name in the host file?

Here is the line from my etc/exports
```
/home 192.168.0.102(rw,no_root_squash,async)
```

To mount from my laptop I use the ip address and also make sure the directory you are trying to mount to exist.

---

### Post by Jose Catre-Vandis on 2009-03-03
A few things:

No brainer checks:
All directories actually exist
all hostnames actually exist
you have portmap and nfs-common installed on your laptop
the nfs server is up and running on your server:
```
sudo /etc/init.d/nfs-kernel-server restart
```
Check the server is serving up nfs from your client:
```
rpcinfo -p 192.168.0.11 | grep -m 1 -o nfs
```
(should give you just "nfs" back)

Try using IP addresses as opposed to hostnames (also in exports file), so for example, replace Copernicus with 192.168.0.10, hawking with 192.168.0.11 and use the full subnet in exports 192.168.0.1/24

Try with async instead of sync

Try dropping the last / after hawkingsc

Try dropping all the mount options, and some other options

Try dropping the firewall(s)

So, /etc/exports on the server to look like this:
```
/home/greendm/SANCentral 192.168.0.1/24(rw,no_subtree_check,async,no_root_squash)
```

and to mount with the laptop
```
sudo mount 192.168.0.11:/home/greendm/SANCentral /home/greendm/hawkingsc
```

If this works you can start building options from there.

---

### Post by crokett on 2009-03-03
> **Gramps said:**
> Do you have the server name in the host file?



You mean the hosts file on my laptop?  No. There is no need. The laptop can resolve the server hostname and the server can resolve the laptop. It wouldn't do much good anyway since my company uses DHCP. The directory I am exporting does exist.  I am browsing it right now. 

Just for grins I tried modifying exports to use the IP address of the laptop instead of the hostname.  That didn't work either.

---

### Post by Jose Catre-Vandis on 2009-03-03
> **crokett said:**
> You mean the hosts file on my laptop?  No. There is no need. The laptop can resolve the server hostname and the server can resolve the laptop. It wouldn't do much good anyway since my company uses DHCP. The directory I am exporting does exist.  I am browsing it right now. 

Just for grins I tried modifying exports to use the IP address of the laptop instead of the hostname.  That didn't work either.

Please ignore sorry

---

### Post by albinootje on 2009-03-03
> **crokett said:**
> 
However when I try to mount the share on the laptop I get this:
```

greendm@Copernicus:~$ sudo mount -t nfs4 -o proto=tcp,port=2049 hawking:/home/greendm/SANCentral /home/greendm/hawkingsc/
mount.nfs4: mounting hawking:/home/greendm/SANCentral failed, reason given by server:
  No such file or directory

```

Is there anything more interesting in the logfiles (like syslog,debug,kernel.log) ?
> 
and showmount -a on the laptop shows this. It suggests the laptop is not seeing the share.  

```

greendm@Copernicus:~$ showmount -a
portmap getport: RPC: Success

```

What do you mean by that ? You are only running NFS-server on 1 of your machines, no ?
If I run "showmount -a" on my desktop machine, which is only a NFS-client, it shows the same output.
> 
I verified the firewall on the desktop is allowing the laptop to connect, or at least the laptop is not timing out.
And how did you verify that exactly ?
With gufw allowing a NFS-client to connect to a NFS-server it simply opens port 2049 tcp/udp.
For the rest, you are relying on your DHCP-server to give you the 
same ip address every time (which does not always work especially when your machine boot up later than other machines), did you check the ip addresses each time before trying to use NFS though ?

---

### Post by Jose Catre-Vandis on 2009-03-03
Sorry brain not working earlier, please revisit earlier post [#5]("http://ubuntuforums.org/showpost.php?p=6831220&postcount=5")

---

### Post by crokett on 2009-03-03
> **albinootje said:**
> Is there anything more interesting in the logfiles (like syslog,debug,kernel.log) ?

What do you mean by that ? You are only running NFS-server on 1 of your machines, no ?

And how did you verify that exactly ?
With gufw allowing a NFS-client to connect to a NFS-server it simply opens port 2049 tcp/udp.
For the rest, you are relying on your DHCP-server to give you the 
same ip address every time (which does not always work especially when your machine boot up later than other machines), did you check the ip addresses each time before trying to use NFS though ?

Yes I am only running it on one machine.  I have a different command to show  the exports on the server and thought that command would show the exports from the remote machine. 

I verified it by not getting a'connection timed out' or similar verbage when trying to mount the share.  Besides which I also added a rule to the firewall on my server to allow NFS. 

I am an idiot.  I left the trailing '/' off the command as Jose suggested and now it tells me access denied.  I suspect that is because I am remoted in from home and the VPN connection is firewalled by my company.  My server can't resolve the hostname in the export.  I will try again tomorrow when I am in the office.  I think I need to modify the config file to allow a range of IPs.  If I do that, is there a way to restrict access to a specific user?

---

### Post by crokett on 2009-03-04
I am back in the office and had thesame error until I ran this command:

```
sudo mount 9.44.102.68:/home/greendm/SANCentral ~/hawkingsc

```

This one did not work:
```
sudo mount -t nfs4 9.44.102.68:/home/greendm/SANCentral ~/hawkingsc


```

So the mount command did not like the -t option apparently. I was using this page as a reference that says to use that option:
[http://www.cyberciti.biz/faq/how-to-ubuntu-nfs-server-configuration-howto/](http://www.cyberciti.biz/faq/how-to-ubuntu-nfs-server-configuration-howto/)

nfs4 is listed as a valid type in the man page for mount. I'd like to know why it failed. 

There was nothing of interest that I could see in kern.log, syslog, auth.log dmesg or messages. 

I will try this again behind the firewall at home to see if it works there too.

---

### Post by albinootje on 2009-03-04
> **crokett said:**
>  My server can't resolve the hostname in the export.  I will try again tomorrow when I am in the office.  I think I need to modify the config file to allow a range of IPs.  If I do that, is there a way to restrict access to a specific user?

As far as I know NFS is pretty primitive in its design, and also not that secure as Samba at all. (For example Samba uses passwords, NFS doesn't).

Are you sure you want to give up on Samba ? 
With Samba you have much more user/password security options (also ACLs).

---

### Post by Jose Catre-Vandis on 2009-03-04
> **crokett said:**
> nfs4 is listed as a valid type in the man page for mount. I'd like to know why it failed.

I believe you need to export as nfs4 to mount as nfs4

Look at the syntax in /etc/exports, looks like

/svr/home             provides "standard" nfs

and

/svr/nfs4/home        provides nfs4

---

### Post by crokett on 2009-03-04
> **albinootje said:**
> As far as I know NFS is pretty primitive in its design, and also not that secure as Samba at all. (For example Samba uses passwords, NFS doesn't).

Are you sure you want to give up on Samba ? 
With Samba you have much more user/password security options (also ACLs).

Good point.  Mostly I think of Samba as an attempt to play in the Windows world and since my laptop is running Linux again there is no reason to use Samba.  However, you do raise an excellent point.  Methinks I will just keep the Samba share.  

Jose,  thanks for the explanation.

---

### Post by jhwilliams on 2011-08-17
I was getting the error "No such file or directory" with NFSv4 because I mis-configured the source path.

```
hostname:/path/to/exports/
``` gets interpreted by the NFSv4 server as ```
**/path/to**/path/to/exports
```, which is not what you want. I wrote up a bit more here: [http://ubuntuforums.org/showthread.php?t=1577658](http://ubuntuforums.org/showthread.php?t=1577658).

---

