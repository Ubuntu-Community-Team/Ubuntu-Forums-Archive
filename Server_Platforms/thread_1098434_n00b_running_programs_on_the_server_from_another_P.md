---
title: "n00b: running programs on the server from another PC"
date: 2009-03-17
forum: Server Platforms
---

### Post by Mawg on 2009-03-17
So, I am teaching myself from the ground up. I have reasonable Linux experience as a user & am now making a small Linux net to try to understand how it works.

I installed Ubuntu dessktop on a few PCs & ubuntu server on another.

I have used NFS to allow the clients to access a shared directory on the server.  Question: ought I to assign fixed IP address, since I am using /etc/hosts on the clients to identify the server? Seems so, just want to be sure.

I want to set up a wiki - it like that has to be in /var/www on the server. Is that really so? Is there a URL that explains that to n00bs?

Finally, I'd like to be able to keep a single copy of certain programs on the server and run it from the clients (to avoid the client versions of the program getting out of synch). Is that the correct way to do it? I presume that there will also be some server specific packages, like CVS.  Is there any URL which explains not just what to do, but why it should be done that way?

Sorry to sound so dumb. I have googled, but just couldn't see anything that explained it me in simple terms.

Thanks in advance for any help.

---

### Post by HermanAB on 2009-03-17
A server should have a fixed IP address, the clients need not.

If you NFS mount a directory with executables (and make it rwx), then anyone that can mount that directory can run those programs.  See Google for 'NFS root'.

A Wiki is a web application, so you need a web server, which is usually Apache.  So you got to install Apache first and get it to work doing something simple, before installing a Wiki.

Cheers,

Herman

---

### Post by Mawg on 2009-03-17
Danke sehr, Herman!


> **HermanAB said:**
> A server should have a fixed IP address, the clients need not.

Hmm, true - I didn't think of that. Maybe I will make all fixed, just in case they later want to share between each other. I guess that fixed loses DHCP, not sure about DNS. Probably the server doesn't need DNS as it won't ever be accessing the internet, but the clients will.

Possibilities ... I might just play around & see what I can learn, but fallback position is, as you suggest, server is fixed IP, clients are dynamic.


> **HermanAB said:**
> 
If you NFS mount a directory with executables (and make it rwx), then anyone that can mount that directory can run those programs.  See Google for 'NFS root'.

Since it's all local, I don't worry too much about security (ie., not hackers, but maybe stupid users ;-), so I currently have this in /etc/fstab
server:/server /server 		nfs	rw,hard,intr	0	0
but I will google as you suggest - this is more about learning than anything else.


> **HermanAB said:**
> 
A Wiki is a web application, so you need a web server, which is usually Apache.  So you got to install Apache first and get it to work doing something simple, before installing a Wiki.

Cheers,

Herman
I already chose the LAMP option at server install, so I have a PHP server. I'm just not sure if/why the wiki, etc has to be in /var/www on the server (I will probably mount it as /wiki or /mnt/wiki on the clients)

And, do the shared programs have to be in a particular folder, or can I put them anywhere? And how do I run them? Do I need some ssh(?) or can I just 

$/server/bin/some_program

???


Thanks again for your help!!

---

### Post by gtr32 on 2009-03-18
> **Mawg said:**
> Do I need some ssh(?) or can I just 


1) Open ssh with X11 forwarding
ssh 'server_address' -X
2) Start X application
xclock &

If that does not work out of the box, open /etc/ssh/ssh_config and set ForwardX11 line to 'ForwardX11 yes'.

---

