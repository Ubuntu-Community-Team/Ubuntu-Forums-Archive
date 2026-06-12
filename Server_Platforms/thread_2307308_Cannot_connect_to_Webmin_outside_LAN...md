---
title: "Cannot connect to Webmin outside LAN..?"
date: 2015-12-23
forum: Server Platforms
---

### Post by THEKINGDOM on 2015-12-23
Hey guys so I really need a little help on this one.. I recently switched from FreeNAS (which was great btw, over to Linux-Ubuntu) because I wanted more power and the ability to be able to remotely administrate my server (outside LAN) via SSH.
I can't seem to manage to get an SSH tunnel to Webmin working from outside of the LAN.
I've got SSH connection working fine, but trying to initiate a tunnel:

Webmin port: 10000 (default) 
When trying to SSH tunnel to port 10000 I get error: "bind: address already in use"

Any experienced user input would be greatly appreciated.

Thank you

---

### Post by THEKINGDOM on 2015-12-23
anybody?

---

### Post by THEKINGDOM on 2015-12-28
seems like nobody externally runs webmin to admin

---

### Post by matt_symes on 2015-12-28
Thread move to **Server Platforms**

You may get a better answer to your query in this forum.

---

### Post by darkod on 2015-12-28
Isn't webmin accessed through http and not ssh??? You would need to open port 10000 (or which ever port webmin is running on) in your home router/firewall, and forward that port to the server private IP. That way you would be able to access it from the outside.

But note that this will probably open you up to attacks, and I'm not sure how safe and bug free webmin is. I don't use it personally.

I agree fully with your original post, to administer your server over ssh. But that's not webmin. Webmin is GUI tool, and not recommended as official tool by ubuntu/canonical by the way, and ssh administration with command line is completely different. Even if you open your ssh port from the outside, you can take measures like using only key authentication and disabling password auth, as a measure to lower attack possibility. With web interfaces and http, you are asking for trouble opening it from outside... Just my humble opinion...

---

### Post by THEKINGDOM on 2015-12-30
> **darkod said:**
> Isn't webmin accessed through http and not ssh??? You would need to open port 10000 (or which ever port webmin is running on) in your home router/firewall, and forward that port to the server private IP. That way you would be able to access it from the outside.

But note that this will probably open you up to attacks, and I'm not sure how safe and bug free webmin is. I don't use it personally.

I agree fully with your original post, to administer your server over ssh. But that's not webmin. Webmin is GUI tool, and not recommended as official tool by ubuntu/canonical by the way, and ssh administration with command line is completely different. Even if you open your ssh port from the outside, you can take measures like using only key authentication and disabling password auth, as a measure to lower attack possibility. With web interfaces and http, you are asking for trouble opening it from outside... Just my humble opinion...

I've done all that and to access webmin externally a ssh tunnel has to be created anyway, so it's ultra secure. Unfortunately I can ssh in but I can't create the ssh tunnel for webmin to open.. so I'm stuck.

---

### Post by darkod on 2015-12-30
Can you please elaborate with more details what exactly did you do, and even post relevant part of config files? As far as I am aware, by default you don't need ssh tunnel for webmin.

So, for example... The default ssh server is running on tcp port 22. Is this the connection that is working for you?

What do you mean by "I can't create the ssh tunnel for webmin to open"? And how are you trying? On port 10000? If there is no second ssh server running on tcp port 10000, of course no ssh connection to that port can be opened. Webmin by default is http on tcp port 10000. No ssh...

Anyway, since this is in part webmin specific, and since webmin is not official ubuntu tool, you might have better luck trying on the webmin forum too.

I am not using webmin but I am quite good in doing external connections and port forwarding, and I can't understand how are you trying to access it right now. Did you try forwarding port 10000 on the router and trying opening the webmin GUI from the outside? But again, not involving ssh in any way.

---

### Post by SeijiSensei on 2015-12-31
Webmin runs a HTTPS server on port 10000, so there's no need for an SSH tunnel as well.  You should be able to point a browser at [https://servername:10000/](https://servername:10000/).  Of course that assumes all the firewalls are configured to permit access to port 10000 from your client.

---

### Post by THEKINGDOM on 2015-12-31
> **SeijiSensei said:**
> Webmin runs a HTTPS server on port 10000, so there's no need for an SSH tunnel as well.  You should be able to point a browser at [https://servername:10000/](https://servername:10000/).  Of course that assumes all the firewalls are configured to permit access to port 10000 from your client.

THAT IS FOR **LOCAL ACCESS WITHIN LAN**. Which works perfectly fine, of course no issues there. That's not my objective. 
Unless of course you're talking about opening port 10000 on the router which is not secure, again not my objective.

I'm looking for access to webmin **outside** of the Local Area Network over a secure SSH. (Which is possible, many are doing it)

Yes SSH port 22, connection with password, no problem at all. 

I'm trying to make a port tunnel to 10000 using ssh command(s): 
ssh user@host -L 10000:127.0.0.1:10000 -N
**OR**
ssh -L localport:LANaddress:remoteport [EMAIL="user@example.com"]user@example.com[/EMAIL]

but I can't get it to work.. I need to speak to somebody with experience in this area.
I get error > "bind: Address already in use"


---

Read Below

---

**TCP Port Forwarding**
SSH can also forward other TCP  application level ports both forward and backwards across the SSH  session that you establish. 
For example, you can setup a port forward for your connection  from your home machine to arvo.suso.org so that it will take connections  to localhost port 3306 and forward them to the remote side  mysql.suso.org port 3306. Port 3306 is the port that the MySQL server  listens on, so this would allow you to bypass the normal host checks  that the MySQL server would make and allow you to run GUI MySQL programs  on your local computer while using the database on your suso account.  Here is the command to accomplish this:  
 ssh -L 3306:mysql.suso.org:3306 [EMAIL="username@arvo.suso.org"]username@arvo.suso.org[/EMAIL]
 The -L (which means Local port) takes one argument of 
<local-port>:<connect-to-host>:<connect-to-port> 
so you specify what host and port the connection will go to on  the other side of the SSH connection. When you make a connection to the  <local-port> port, it sends the data through the SSH connection  and then connects to <connect-to-host>:<connect-to-port> on  the other side. From the point of view of <connect-to-host>, its  as if the connection came from the SSH server that you login to. In the  case above, arvo.suso.org. 
This is much like a VPN connection allows you to act like you are making connections from the remote network that you VPN into. 
Take a moment to think of other useful connections you can make with this type of network tunnel. 
Another useful one is for when you are away from home and can't  send mail through your home ISP's mail server because it only allows  local connections to block spam. You can create an SSH tunnel to an SSH  server that is local to your ISP and then have your GUI mail client like  Thunderbird make a connection to localhost port 8025 to send the mail.  Here is the command to create the tunnel: 
 ssh -L 8025:smtp.homeisp.net:25 [EMAIL="username@shell.homeisp.net"]username@shell.homeisp.net[/EMAIL]
 One thing to note is that non-root users do not normally have the  ability to listen on network ports lower than 1024, so listening on port  25 would not work, thus we use 8025. It really doesn't matter, you can  use any port as long as your email client can connect to it.

---

### Post by darkod on 2015-12-31
In such case, why are you trying to 127.0.0.1:10000? That would be the local client and instead it needs to be the remote server IP (according to that explanation).

Also I'm not sure if this would work with password auth or only with ssh keys (because in such case it is not asking you for password when establishing the ssh tunnel).

According to that, what you need to try on the client side (with or without ssh key I don't know), is:
```
ssh -L 10000:<server public IP>:10000 username
```

Whether you will need the username or not depends on ssh key. Best to try using a key I think.

If that tunnel is established correctly, then on your client you are opening the local 10000 port:
```
https://localhost:10000
```

That should open up webmin.

On another hand, why don't you set up a simple openvpn access? That will allow you secure access to any application, like ssh, webmin, etc.

The above procedure with ssh leaves too many variables. Are you doing this from linux or windows client? Does the local user have rights to listen to local network ports like that? etc... OpenVPN is much better for remote secure connections.

---

### Post by darkod on 2015-12-31
Did you check if forwarding is enabled on the ssh server?

```
grep Forwarding /etc/ssh/sshd_config
X11Forwarding no
AllowTcpForwarding no
```

Check if it says yes or no.

Also my previous commands about extablishing the tunnel might be wrong, you might need to play with varios modifications little... I haven't used this before so I can't be sure...

---

### Post by volkswagner on 2016-01-01
Like darkod pointed out, your addressing of 127.0.0.1 in the ssh command is not correct. You are getting port in use error because
you are assigning port 10000 twice (once with -L switch and once on redirect to 127.0.0.1).

Provided you are connecting directly to the server running webmin, I think the following should work.
The following example assumes the server's public ip is 1.1.1.1 and the server's lan address is 192.168.1.20 (adjust for your setting).

```
ssh user@1.1.1.1 -L 10000:192.168.1.20:10000
``` 

once connection is established you should be able to access webmin on local machine's browser using [http://localhost:10000](http://localhost:10000) or [https://localhost:10000](https://localhost:10000) (I'm not sure on the https or not)

This should get your reverse tunnel working.

In my opinion, Webmin is more of a crutch than a tool. With a Linux server configuration is via text files. Webmin has some methods of mangling
config files. It hasn't been supported in Ubuntu for many years. I don't think most users in this forum use it, so if you need help, webmin can
be a hindrance for receiving help.

---

### Post by MAFoElffen on 2016-01-01
darkod +1

Another variation while using webmin:
```

ssh user@host -L 10000:127.0.0.1:10000 -N

```

I've used the above, but I think I originally started from instructions I had from somewhere on remotely connecting to VNC through ssh ... which had an explanation of what each part meant:
> 
Step by step procedure


You can easily tunnel VNC connections over ssh so that entire traffic get encrypted. Type the following command to tunnel VNC connections over SSH (you need to type command on your desktop computer running UNIX or Linux):
$ ssh -L 5901:localhost:5901 -N -f -l username sshserver.mydomain.com


OR
$ ssh -L 5901:127.0.0.1:5901 -N -f -l username 192.168.1.100


Where,
-L 5901:localhost:5901 : Specifies that the given port on the local (client) host is to be forwarded to the given host and port on the remote side. Here you are using port 5901 on the localhost to be forward to sshserver.mydomain.com on the 5901 port.
-N : Do not execute a remote command i.e. just forward ports.
-f : Requests ssh to go to background just before command execution. Requests ssh to go to background just before command execution. Once password supplied it will go to background and you can use prompt for type commands on local system.
-l username : username is the user to log in as on the remote machine (sshserver.mydomain.com).
sshserver.mydomain.com (192.168.1.100): Remote system with VNC server


In your localhost VNC client use 127.0.0.1:5901 for connection. Make sure you use appropriate port i.e. 5901 (VNC server running on display 1). This tunnel will provide nice enhanced security.


---

### Post by SeijiSensei on 2016-01-02
> **Robert_Matear said:**
> THAT IS FOR **LOCAL ACCESS WITHIN LAN**. Which works perfectly fine, of course no issues there. That's not my objective. 
Unless of course you're talking about opening port 10000 on the router which is not secure, again not my objective.
It can be quite secure if you limit the list of IP addresses that can gain access to the port.  I don't know why you think opening an SSH service to the outside world is any less secure than HTTPS.

---

