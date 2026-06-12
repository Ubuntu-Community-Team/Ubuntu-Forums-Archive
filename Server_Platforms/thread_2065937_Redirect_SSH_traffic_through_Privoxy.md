---
title: "Redirect SSH traffic through Privoxy"
date: 2012-10-03
forum: Server Platforms
---

### Post by Scripting22 on 2012-10-03
Hello,

I'm looking for a solution to route my SSH traffic through a proxy. Here is my setup:

Laptop --> ssh traffic --> remote ssh server (owned by me) --> privoxy (socks5) --> TOR.

As you can see, my main goal is this. I want to ssh into my remote server, and then all the outbound webtraffic generated on the remote server must go via TOR. The best way to establish this is (I think), to use a local proxy on the remote server and I choose privoxy to do this.

So when i log in to the server and browse the internet via CLI and explicitly tell to use privoxy it works. I check this by looking which IP I'm using. But I want to login to the server and then automaticly use privoxy and thus TOR. I've tried to create local forwards, extra host to set up a local ssh tunnel, give the ssh login command an extra tunnel with it but nothing works so far.

So after two days of trying I'm running out of options. If someone knows a solution, or maybe a better way to archieve my goal, please tell me. For the record, directly using TOR from laptop is NOT an option.

---

### Post by Lars Noodén on 2012-10-03
I'm not clear on what you have tried already, but tunneling should work.  What port is privoxy listening on?  Let's say 3999.  

```

ssh -L 4000:127.0.0.1:3999 server.example.org

```

So then if you connect on your laptop's browser's proxy settings to port 4000 on the local host as a socks5 proxy, you should be connected to Tor.

---

### Post by Scripting22 on 2012-10-04
> **Lars Noodén said:**
> I'm not clear on what you have tried already, but tunneling should work.  What port is privoxy listening on?  Let's say 3999.  

```

ssh -L 4000:127.0.0.1:3999 server.example.org

```So then if you connect on your laptop's browser's proxy settings to port 4000 on the local host as a socks5 proxy, you should be connected to Tor.

Yeah only it works slightly different. First I fire up a ssh connection on my laptop to the server like this:

```
ssh 2 -C -D 5000 user@IP -i ~/.ssh/key
```So there is a compressed ssh tunnel on from my laptop to the server which can be reached on the localhost (of laptop) on port 5000. So I configure firefox to use a Socks5 proxy on port 5000 of the localhost. So far so good, everything works wel.

But on the ssh server I want that incoming ssh connection from the laptop is redirected to privoxy and so through TOR.

But when I issue on the server the command:

```
ssh -L 8118:localhost:22 Ubuntu-webserver
```it says: "bind address already in use"

So  maybe, I'm missing something? I have been thinking to configure an extra ssh port (like 10000 for example) on the server, but then the problem persists I think because then there will be a ssh deamon which is using the port. So my main problem is I can't redirect the incoming ssh connection through the local proxy (and thus TOR). Any other ideas?

---

### Post by Lars Noodén on 2012-10-04
> **Scripting22 said:**
> Yeah only it works slightly different. First I fire up a ssh connection on my laptop to the server like this:

```
ssh 2 -C -D 5000 user@IP -i ~/.ssh/key
```So there is a compressed ssh tunnel on from my laptop to the server which can be reached on the localhost (of laptop) on port 5000. So I configure firefox to use a Socks5 proxy on port 5000 of the localhost. So far so good, everything works wel.


Yes, but that won't connect you to privoxy. 

> **Scripting22 said:**
> 
But on the ssh server I want that incoming ssh connection from the laptop is redirected to privoxy and so through TOR.

But when I issue on the server the command:

```
ssh -L 8118:localhost:22 Ubuntu-webserver
```it says: "bind address already in use"

...

What port number is privoxy listening on?  That's the one that you need to reach with forwarding (-L), not port 22.

---

### Post by markbl on 2012-10-04
> **Scripting22 said:**
> 
```
ssh -L 8118:localhost:22 Ubuntu-webserver
```it says: "bind address already in use"


That error means something else is already listening on port 8118 on your client side. Do a:
```

netstat -ln --inet | grep :8118

```
to see what that is.

---

### Post by Scripting22 on 2012-10-05
> **Lars Noodén said:**
> Yes, but that won't connect you to privoxy. 

What port number is privoxy listening on?  That's the one that you need to reach with forwarding (-L), not port 22.

Correct, it won't connect me to privoxy, thats the problem I'm trying to solve. Privoxy is listening on port 8118.

So my problem is, first I have to establish an ssh connection over port 22 on the ssh server, and then tunnel this ssh traffic to port 8118 of privoxy. But when I issue the command:

```
sudo ssh -L 22:localhost:8118 user@IP -i ~/.ssh/id_rsa
```it says: 

"[B]bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 22
Could not request local forwarding"

[/B]And that makes sense because the ssh daemon is listening on port 22. I'm looking for a way to redirect the ssh traffic **after** it has been accepted and processed by the ssh daemon.

Edit: I've solved the problem by issuing the following command:

```
ssh -2 -l user -L 5000:127.0.0.1:8118 192.168.1.100 -i ~/.ssh/id_rsa
```

---

