---
title: "NFS to slow"
date: 2012-11-26
forum: Server Platforms
---

### Post by miguelpires on 2012-11-26
Hi,
I've a server with Single-one LDAP configuration. The clients are all configurated, with sssd+Kerberos to autenticathion against the server and automount to mount the /home folders and the groups folders. My problem is this is to slow, becoming very painful,m sometimes, if you put something in recycling bin, the client freezes and takes almost 5m to finish the task.
The server is a I7 with 8GB of memory and 1TB hd
The clients are all dual cores with 4GB off memory.
Can someone help out to try to debug and correct this?
regard's
Miguel

---

### Post by papibe on 2012-11-26
Hi miguelpires.

I would start by taking some measurements. How slow? Rate?

I'd also start by testing the raw network speed, to discard hardware problems (including router setting). You can use [iperf]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes") to measure this, for instance.

Let us know how it goes.
Regards.

---

### Post by miguelpires on 2012-11-26
> **papibe said:**
> Hi miguelpires.

I would start by taking some measurements. How slow? Rate?

I'd also start by testing the raw network speed, to discard hardware problems (including router setting). You can use [iperf]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes") to measure this, for instance.

Let us know how it goes.
Regards.
Hi papibe,
thanks for the replay. I will test this in the morning, not at office. 
For us is very very slow, like, delete a file take +2m.
regards 
Miguel

---

### Post by SeijiSensei on 2012-11-28
If you're using "sync" in the list of NFS export options, try using "async".  Since sync is the default, you'll probably need to add async to the option list.  If the server is reliable and connected to a UPS, using async is perfectly safe and *much* faster than sync.

Also, if the clients are running Linux, make sure they have reasonable settings for rsize and wsize.  The defaults are quite small.  On wired networks with 100BaseT or better connections, I usually add "rsize=65536,wsize=65536" to the client options in /etc/fstab.  On 54 GHz wireless, I use 32768.

---

### Post by miguelpires on 2012-11-29
> **papibe said:**
> Hi miguelpires.

I would start by taking some measurements. How slow? Rate?

I'd also start by testing the raw network speed, to discard hardware problems (including router setting). You can use [iperf]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes") to measure this, for instance.

Let us know how it goes.
Regards.


Hi,
I've done a test with some users account and this is what I see:

  	 	 	 	 	 	   user@posto-6:~$ dd if=/dev/zero of=/home/Casimira/stuff.bin bs=1024 count=1024 && rm /home/Casimira/stuff.bin  
 1024+0 registos dentro  1024+0 registos fora  1048576 bytes (1,0 MB) copiados, 0,0147629 s, 71,0 MB/s   Strange only 71 MB/ s when both of the NIC are 1Gb/s

---

### Post by miguelpires on 2012-11-29
> **SeijiSensei said:**
> If you're using "sync" in the list of NFS export options, try using "async".  Since sync is the default, you'll probably need to add async to the option list.  If the server is reliable and connected to a UPS, using async is perfectly safe and *much* faster than sync.

Also, if the clients are running Linux, make sure they have reasonable settings for rsize and wsize.  The defaults are quite small.  On wired networks with 100BaseT or better connections, I usually add "rsize=65536,wsize=65536" to the client options in /etc/fstab.  On 54 GHz wireless, I use 32768.

Hi,
Tks for your idea. With don't use fstab but automount. 
What we have in the clients in auto.home file is something like this:

  	 	 	 	 	 	   
[LIST]
[*]-fstype=nfs4,sec=krb5,intr,rsize=8192,wsize=8192 	zsrv.zentyal.lan:/home/&  	
[/LIST]
  Soo you are sugesting to change the values?
Regard's
Miguel

---

### Post by SeijiSensei on 2012-11-29
Yes, 8192 is too small on most hardware these days.  If you're on 100BaseT or better, try 65536 as I mentioned above.

You didn't mention whether you were using "sync" or "async" on the server.  Give "async" a try.  My guess is that it will matter more than the packet sizes.

---

### Post by miguelpires on 2012-11-29
> **SeijiSensei said:**
> Yes, 8192 is too small on most hardware these days.  If you're on 100BaseT or better, try 65536 as I mentioned above.

You didn't mention whether you were using "sync" or "async" on the server.  Give "async" a try.  My guess is that it will matter more than the packet sizes.

Ok,
I will try. We use async.
regard's
Miguel

---

