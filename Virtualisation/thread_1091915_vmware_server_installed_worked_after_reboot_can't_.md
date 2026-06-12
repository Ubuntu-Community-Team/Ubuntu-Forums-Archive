---
title: "vmware server installed worked after reboot can't reach it"
date: 2009-03-09
forum: Virtualisation
---

### Post by lawson23 on 2009-03-09
followed this guide:
Ubuntu 8.10 (VMWare Server 2.0.0 Build 122956)
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

iinnstalled perfectly as instructions say.  Once done was able to access the server.  Did a reboot of the box and now I can't connect to the web server from firefox on a remote machine.  Acts as if it isn't running.

This is not the cert issue as I already installed the cert and this is trying to hit the non https page.

I have done this:
       aptitude install xinetd
even though it isn't connection refused it is like it.

Telnet seems to fail when trying:
       telnet <ip-of-vmware-server> 902
Putty just closes out.

What I don't know is how to check the status of the services and see if they are running or not.

Tried this:
       sudo /etc/init.d/httpd.vmware status
sudo: /etc/init.d/httpd.vmware: command not found


This vmware server 2.0 install is on a mythbuntu 8.10 install.

---

### Post by veloce on 2009-03-10
> **lawson23 said:**
> 
iinnstalled perfectly as instructions say.  Once done was able to access the server.  Did a reboot of the box and now I can't connect to the web server from firefox on a remote machine.  Acts as if it isn't running.


Most common reason for not starting after rebooting is a kernel uprgrade.  You didn't have one of these waiting in the wings did you?

I any case, I'd try re-running vmware-config on the host.  That will also tell you whether it's running.

There must be an easier way to see if the services are running - anyone???

---

### Post by lawson23 on 2009-03-10
Well I just installed the box and did do all the updates and don't know if I rebooted.  The updates all applied successfully with no notification for a reboot so I don't know for sure or not on that one.

I will say I believe one of them was a kernal update.

Yes it would be nice to know how to check the services.

FYI redownloading the package now to run the config over.

---

### Post by lawson23 on 2009-03-10
Ok it is reinstalled and running.  Now I have to test the restart probably tomorrow.  Hey why does anyone know why I get these User Identification Request throughout access and using vmware?

The site has requested that you identify yourself with a certificate:

Choose a cert to present as identification:
I have some old cert i believe for allpeers which I tried out and don't use.  This is my only option for a cert so I just click cancel and it appears to work but I will get like 3 of these in a row if I click ok or cancel.

---

### Post by lawson23 on 2009-03-10
Well,
while trying to add a vm it all of a sudden got stuck on loading...

So I waited and waited and then finally refreshed the page and GUESS what.
```

Connection Interrupted

The connection to the server was reset while the page was loading.

The network link was interrupted while negotiating a connection. Please try again.
```

This is exactly what happened the first time.

---

### Post by lawson23 on 2009-03-10
Ok from looking around I found this
```

@myth:~$ sudo /etc/init.d/vmware-mgmt stop
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                            done
@myth:~$ sudo /etc/init.d/vmware-mgmt start
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access

```
When doing this I was able to hit the web page again but back to loading when trying to see the vmx of my VM.  Probably hosed again I bet if I hit refresh it would fail again and continue.

---

### Post by lawson23 on 2009-03-10
When trying this access in IE I actually get an error returned at the loading part.

```

The server could not complete a request (HTTP 12031 ).OK
The server encountered an unexpected condition that prevented it from fulfilling the request. If this problem persists, please contact your system administrator.

```

---

### Post by veloce on 2009-03-11
> **lawson23 said:**
> Well,
while trying to add a vm it all of a sudden got stuck on loading...

So I waited and waited and then finally refreshed the page and GUESS what.
```

Connection Interrupted

The connection to the server was reset while the page was loading.

The network link was interrupted while negotiating a connection. Please try again.
```

This is exactly what happened the first time.

You got this while trying to add an existing vm?  It does sound like that vm is corrupt.  Try looking in the vm's directory on the host and delete all the old log files, temporary files, lock files, and any snapshots.  (Just leave the .vmx and virtual disk files).

---

### Post by lawson23 on 2009-03-11
Well I don't believe it is the VM being corrupt but will remove all other files.  The reason I say this is that I added a new VM from 2.0 and then went to browse it and it does the same thing to this new vm it just shows loading...

---

### Post by lawson23 on 2009-03-13
Anything I would need to do to the vmx for this?

This was a version 1 server vmx?

---

### Post by lawson23 on 2009-03-13
Ok figured it out.  It ended up being a vmdk in that vm.  Not sure if it was one of the vmdk's I was no longer using or one of them that was a -pt.vmdk.

Either way I solved the issue by removing and then looking at the vmx and removing more.

also for status and restarting this command works well:

```

/etc/init.d$ sudo /etc/init.d/vmware ?
Usage: vmware {start|stop|status|restart}

```

hopefully this helps someone in the future.

And thanks to veloce for all the assistance!

---

### Post by veloce on 2009-03-15
> **lawson23 said:**
> 
also for status and restarting this command works well:

```

/etc/init.d$ sudo /etc/init.d/vmware ?
Usage: vmware {start|stop|status|restart}

```

hopefully this helps someone in the future.

And thanks to veloce for all the assistance!

No worries.

Thank you for that status command.  I think that's going to be handy.

---

### Post by brion@cbkidder.com on 2009-08-24
I had the same problem after a kernel update. I ran the update again and my virtual machine was still there. Everything works again.

sudo /usr/bin/vmware-config.pl

---

### Post by michelkogan on 2010-05-13
> **lawson23 said:**
> Ok figured it out.  It ended up being a vmdk in that vm.  Not sure if it was one of the vmdk's I was no longer using or one of them that was a -pt.vmdk.

Either way I solved the issue by removing and then looking at the vmx and removing more.

also for status and restarting this command works well:

```

/etc/init.d$ sudo /etc/init.d/vmware ?
Usage: vmware {start|stop|status|restart}

```

hopefully this helps someone in the future.

And thanks to veloce for all the assistance!

Please let me now how did you fix the problem. what is VMX ??? where did you remove vmx ???
> Either way I solved the issue by removing and then looking at the vmx and removing more.


Please ...  I have the same problem here !

---

