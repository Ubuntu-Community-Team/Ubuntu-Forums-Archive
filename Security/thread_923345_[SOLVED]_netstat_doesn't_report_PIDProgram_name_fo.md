---
title: "[SOLVED] netstat doesn't report PID/Program name for some ports"
date: 2008-09-18
forum: Security
---

### Post by amac777 on 2008-09-18
Just curious, why don't the first two open ports on my machine have any PID or Program name associated with them? How can I tell what they are and what program is responsible for them?

With no programs open, the command I used was "sudo netstat -tap". It shows: 

```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 *:nfs                   *:*                     LISTEN     -                   
tcp        0      0 *:40773                 *:*                     LISTEN     -                   
tcp        0      0 *:vmware-authd          *:*                     LISTEN     5229/xinetd         
tcp        0      0 localhost:mysql         *:*                     LISTEN     4896/mysqld         
tcp        0      0 *:www                   *:*                     LISTEN     5540/apache2        
tcp        0      0 *:ipp                   *:*                     LISTEN     4819/cupsd          
tcp        0      0 *:smtp                  *:*                     LISTEN     5139/master         
tcp        0      0 *:34171                 *:*                     LISTEN     5067/rpc.mountd     
tcp6       0      0 *:ftp                   *:*                     LISTEN     5437/proftpd: (acce 
tcp6       0      0 *:ssh                   *:*                     LISTEN     4713/sshd           
tcp6       0      0 *:ipp                   *:*                     LISTEN     4819/cupsd          
tcp6       0      0 *:smtp                  *:*                     LISTEN     5139/master         

```

Also, does anyone know how I can disable the vmware-authd program? I installed vmware a long time ago to play with it but I never use it anymore so no point in having that port open for no reason.

---

### Post by beniji on 2008-09-20
This is concerning me a lot too. 

I found it on a new fully patched Hardy tonight and an older fully patched Gutsy.

**lsof** and **netstat** do not show the process owner, nor is there correct information under **/proc**.

Even worse, a new file socket descriptor is not created when connecting to the suspect port.

If you telnet into the port, what happens if you type a single character and then press enter?

PS I notice we are both using NFS.

---

### Post by amac777 on 2008-09-20
Since you said you are also running NFS and that is one of the weird ports, I tried shutting down the NFS server and the two unowned open ports closed. So I think it's something to do with NFS. To shut down NFS I typed these two commands:

sudo /etc/init.d/nfs-common stop
sudo /etc/init.d/nfs-kernel-server stop

Also, after I posted the original post, I did some more digging in the man page for netstat and found this:

>  PID/Program name
       Slash-separated pair of the process id (PID) and process name of the process that owns the  socket.   --pro&#8208;
       gram  causes this column to be included.  You will also need superuser privileges to see this information on
       sockets you don’t own.  **This identification information is not yet available for IPX sockets.** (emphasis mine)

I have no idea what an IPX socket is, but perhaps that's the problem? 

Anyway, I'm now pretty sure this is not malware, just part of NFS.

---

### Post by amac777 on 2008-09-20
Oh, to answer your question, telneting to the open port and then typing a single letter and pressing enter causes nothing to happen (I see the character I typed and the curser goes to the next line when I press enter). But if I type another character and press enter then the connection gets disconnected. I tried various characters and text and couldn't get any other reactions besides connection disconnected, either on the first time I press enter for long strings of text, or the second time I press enter for short strings. 

Also, I scanned the port with nmap and it confirmed it's open and tcp but said service was unknown.

---

### Post by njdove on 2008-10-30
The Linux kernel itself provides the NFS server (aka "knfsd"). Thus there is no associated process because the kernel is not a process.

As an aside, [IPX]("http://en.wikipedia.org/wiki/IPX") was Netware's alternative network protocol to IP.

---

### Post by amac777 on 2008-10-30
Ok, thanks for the response - Kernel provides NFS, and kernel is not a process so no PID/Program name for NFS. Makes sense. I've marked the thread as solved.

---

