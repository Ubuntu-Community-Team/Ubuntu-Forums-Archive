---
title: "Cannot mount NFS: &quot;RPC: Timed out&quot;"
date: 2006-10-04
forum: Server Platforms
---

### Post by andrewski on 2006-10-04
I'm having trouble mounting my NFS server today.  I'm getting a message that I've never gotten before: "mount: RPC: Timed out".  Googling has proven to be inconsistent.

Nothing much has changed on my client system: on Edgy, I had changed my hostname, but this isn't working in Dapper either.  I've tried rebooting both client and server.

My exact fstab line is as follows:
```
192.168.1.151:/music /home/music nfs rw,soft,intr       0 0
```Can anyone help?

---

### Post by bluefrog on 2006-10-04
to check: portmap is installed and running?

James

---

### Post by andrewski on 2006-10-07
Yes, portmap was running on server and client.  This problem seems to have resolved itself temporarily; any other reasons it may have happened that I can check to prevent it coming back?

---

### Post by andrewski on 2006-10-19
> **andrewski said:**
> Yes, portmap was running on server and client.  This problem seems to have resolved itself temporarily; any other reasons it may have happened that I can check to prevent it coming back?
Someone insisted on contacting me personally rather than on the forums to offer a bit more information.  So *I'll* post it here. :rolleyes:

[quote=Julian]What happened to you a couple of weeks ago, was maybe the result of a machine-sudden-reset or perhaps a failure dring a shutdown. The effect of that is a miscommunication between potmap and the netfs service (in charge of mounting the network file systems, like samba, nfs, etc), in the upcoming power ups.
The problem is on the client, as you suspected, and the way to deal with it is to "rpcinfo -p localhost" and to stop (not restart) every service mentioned therein and after that to start every service mentioned there.
then you have to "service netfs restart"... and nfs will mount just fine... (obviously) you have to have have your /etc/fstab nfs entry configured.[/quote]
I hope this helps anyone else who may come across this problem.

---

### Post by andrewski on 2007-05-31
This problem has come up again, and I'm not really sure what the instructions above are telling me to do.

I stopped portmap and nfs on the client and server and restarted them on both. That was the only service I could see in `rpcinfo`.

fstab hasn't changed, the client and server hostnames haven't changed... what's the deal?

---

### Post by virgiltibbs on 2007-07-17
are you still having this problem?
see
[http://ubuntuforums.org/showthread.php?t=477695](http://ubuntuforums.org/showthread.php?t=477695)
if you are for the (non) solution

---

### Post by skanchi on 2007-07-20
This happens if you have a direct link between the client and server. However, if you have a Switch/Router between the server and client, the NFS mount succeeds
You don't need any nfs related daemons running on the client end. These should be running only at the server end

I unable to debug why a direct link doesn't work!!!

---

