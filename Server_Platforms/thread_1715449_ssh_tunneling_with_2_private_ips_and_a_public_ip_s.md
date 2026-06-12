---
title: "ssh tunneling with 2 private ips and a public ip server."
date: 2011-03-27
forum: Server Platforms
---

### Post by freakish911 on 2011-03-27
Hey,
I have an OpenSSH server (private_server) running on a box that is behind a firewall and want to connect to it from any remote location (remote). I also have access to a remote server (public_server) with a public IP. This is what I do:
On the private server I create a reverse tunnel (OpenSSH is listening on port 2555) to the public_server:
private_server$ ssh -R localhost:2555:localhost:2555 user@public_server
so that the public_server sends all connections that come to it on port 2555 to port 2555 on the private_server.

Afterwards on the remote machine I open another tunnel to the public_server:
remote$ ssh -L 2555:public_server:2555 user@public_server
to send all local traffic on port 2555 to port 2555 on the public_server.

Now, my assumption would be that if I do
remote$ ssh -p 2555 private_user@localhost
the connection would be sent to the public_server which would further forward it to my private_server. I however get a message that "Connection was closed by remote host" on the remote box and a "channel 3: open failed: administratively prohibited: open failed" on the public_server.

If, however, I try to connect to the private_server by running
public_server$ ssh -p 2555 private_user@localhost 
on the public_server it works fine, Im connected. Still, this does not fix the problem, as I need to have it directly on the remote box.

I would be very grateful for any help in solving this.
I am new to forum posting and I apologize for any misconduct I might have committed.
Thanks in advance!
freak

---

