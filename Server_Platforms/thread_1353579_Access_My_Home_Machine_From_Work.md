---
title: "Access My Home Machine From Work?"
date: 2009-12-12
forum: Server Platforms
---

### Post by Adler on 2009-12-12
Hi All,

I've been using Linux for years, and suddenly a bunch of people @ work have decided to switch to Linux e.g. Ubuntu 9.10.

Their decision has been based on the fact that they don't have original disks for either the Microsoft OS, or for things like Microsoft Office. They either installed them and then lost all the originals.

They all had purchased original systems, but Microsoft beat them down in terms of additional hardware or software requirements. Think Vista.

BTW, I've been talking about Linux there for years.

As it stands, I have access to an almost finished Ubuntu 9.10 machine - it lacks a lot of repositories. I could install them.

With this finished machine @ work, how could I access my machine @ home?

---

### Post by HighCommander540 on 2009-12-13
> **Adler said:**
> Hi All,

I've been using Linux for years, and suddenly a bunch of people @ work have decided to switch to Linux e.g. Ubuntu 9.10.

Their decision has been based on the fact that they don't have original disks for either the Microsoft OS, or for things like Microsoft Office. They either installed them and then lost all the originals.

They all had purchased original systems, but Microsoft beat them down in terms of additional hardware or software requirements. Think Vista.

BTW, I've been talking about Linux there for years.

As it stands, I have access to an almost finished Ubuntu 9.10 machine - it lacks a lot of repositories. I could install them.

With this finished machine @ work, how could I access my machine @ home?

Easy...Install SSH or VNC. Done. SSH is terminal with minimal X11 support. And VNC is full graphical forwarding.

---

### Post by staf0048 on 2009-12-13
I could be wrong, but in order to use either SSH or VNC you must have a static IP going to your home.  I say this because most people do not bother with paying for a static IP.  If there is a way around this (along with ISP port blocking) I'd love to hear about it!!!

---

### Post by HighCommander540 on 2009-12-13
> **staf0048 said:**
> I could be wrong, but in order to use either SSH or VNC you must have a static IP going to your home.  I say this because most people do not bother with paying for a static IP.  If there is a way around this (along with ISP port blocking) I'd love to hear about it!!!

Yeah, its true. Most ISP's give you dynamic IP addresses (sorry I have this issue myself, I forgot about this step). They do change , but not very often. To make up for this you need an external static IP host like no-ip.org (I use them, but there are others).

Then its easy. Just set up and account with them, and install their software. Whenever your IP address changes it will up their staic host name they gave you to route to the new IP address your home computer uses.

To connect you just use the hostname you set-up with them. ***.no-ip.org.

There is only one other thing you need to do. Make sure that you add port redirect rules on your router to send the port that SSH (port 22) or VNC (sorry don't know the port off the top of my head) to your Linux machine on your network (its IP address).

Does that make it clear?

---

### Post by Adler on 2009-12-13
Hi Guys,

Thanks for those replies!

Both the machines that I am trying to work with are running 9.10.

After reading your posts I'm thinking VNC, might be the way to go, and that a server install on my Home machine would be necessary. Am I wrong? 

Which applications from the repositories should be installed? I've amended my repositories greatly from the original 9.10 install with this [source]("http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/").

I can run [What Is My IP Address]("http://whatismyipaddress.com/"), and see my IP address. 

I run a local cable service as my ISP, and am thinking that in order to gain an additional layer of security I might need to look @ "IP Spoofing", if that is a real term. My connections are always via Ethernet cable, and have no working router. The speeds have always been better than WiFi.

Again, thanks for the responses and I look forward to hearing back from you!

Regards,

JJMacey
Phoenix, Arizona

---

### Post by Adler on 2009-12-13
Hi Again,

I've been a Googling, and ran across [this]("https://help.ubuntu.com/community/VNC")...

Accessing your desktop over the Internet

Although VNC has some optional security features, you should not run VNC directly over an untrusted network like the Internet. Instead, you should set an SSH server up as discussed in the SSH guide and configure a VNC server that you can start in so-called once mode. When you have set up your SSH and VNC servers, you can use SSH to log in to your computer over the Internet, start your VNC server, and use port-forwarding to securely access the VNC server. 

And the search goes on for the best way to do this. Honestly, I've run across a lot of outdated material / posts.

Best Regards,

JJMacey
Phoenix, Arizona

---

### Post by HighCommander540 on 2009-12-14
> **Adler said:**
> Hi Again,

I've been a Googling, and ran across [this]("https://help.ubuntu.com/community/VNC")...

Accessing your desktop over the Internet

Although VNC has some optional security features, you should not run VNC directly over an untrusted network like the Internet. Instead, you should set an SSH server up as discussed in the SSH guide and configure a VNC server that you can start in so-called once mode. When you have set up your SSH and VNC servers, you can use SSH to log in to your computer over the Internet, start your VNC server, and use port-forwarding to securely access the VNC server. 

And the search goes on for the best way to do this. Honestly, I've run across a lot of outdated material / posts.

Best Regards,

JJMacey
Phoenix, Arizona

Yeah, my opinion on the matter is no. Because I have tried to get SSH port forwarding to work and never manage to. Unless you have data that really need to be secure, just set-up VNC.

---

### Post by BkkBonanza on 2009-12-14
Using ssh for port forwarding should be very easy. Assuming you install openssh server from Synaptics then there's no need for a "full server install". The main thing here is to have ssh running at home and a dynamic ip client setup so that your dynamic ip can be updated automatically. Most good routers will have an option for a dynamic update client built in so that you can often configure your router to update using a dynamic ip. Choose a service like dyndns.com that your router has support for. If no router support then you need to run something like ddclient on your home machine. Either way you need to forward a port from your router to your computer for ssh.

Another way to do this if you have a static IP at work is to not bother with ssh server at home but just run a reverse tunnel to work. In this case you just use the ssh client installed by default in Ubuntu desktop. With one command line it connects to work and listens on a port on the work machine. Then you use VNC and connect to the local port at work, which ssh forwards home to connect to VNC at home.

I've used port forwarding a lot and never found it hard to use but if you're unsure about what parms to give ssh then it can be confusing. Not being able forward a port on my router and have a daemon listening on my home machine I tend to favour the reverse tunnel method. I happen to have a vps server out on the web with ssh server always listening anyway so using a reverse tunnel to that means I can always connect home easily.

If you want a regular tunnel home for VNC then at work you would issue something like 

ssh -f [email]user@home.com[/email] -L 5900:localhost:5900 -N

Then VNC at work is config'd to connect to localhost 5900. ssh forwards it to home 5900 where it connects to your VNC server running. 

To do similar with a reverse tunnel at home you would issue,

ssh -f [email]user@work.com[/email] -R 5900:localhost:5900 -N

Now on your work machine port 5900 is listening and forwarding to 5900 at home. At work you can connect anytime to 5900 and get your home machine. No dynamic IP hassles and doesn't require opening a port at home. 

BTW the -N parm tells ssh to not run any other commands after starting but I have found then you usually need to manually kill the process. You could replace this with a command like "sleep 60" which keeps the tunnel open for 60 seconds after use and then auto-closes it.

I use my server often for secure SOCKS proxying with ssh ( -D 8080 ) and for reverse tunnels so I have a special user on that machine for connecting with limited privileges and no shell available to prevent abuse.

Running VNC without a secure tunnel is a terrible idea. It's not just about sensitive data but all your user id / passwords being sniffable. On Ubuntu one of the common ways to get hacked is via poorly config'd VNC.

---

### Post by HighCommander540 on 2009-12-14
> **BkkBonaza said:**
> Using ssh for port forwarding should be very easy. Assuming you install openssh server from Synaptics then there's no need for a "full server install". The main thing here is to have ssh running at home and a dynamic ip client setup so that your dynamic ip can be updated automatically. Most good routers will have an option for a dynamic update client built in so that you can often configure your router to update using a dynamic ip. Choose a service like dyndns.com that your router has support for. If no router support then you need to run something like ddclient on your home machine. Either way you need to forward a port from your router to your computer for ssh.

Another way to do this if you have a static IP at work is to not bother with ssh server at home but just run a reverse tunnel to work. In this case you just use the ssh client installed by default in Ubuntu desktop. With one command line it connects to work and listens on a port on the work machine. Then you use VNC and connect to the local port at work, which ssh forwards home to connect to VNC at home.

I've used port forwarding a lot and never found it hard to use but if you're unsure about what parms to give ssh then it can be confusing. Not being able forward a port on my router and have a daemon listening on my home machine I tend to favour the reverse tunnel method. I happen to have a vps server out on the web with ssh server always listening anyway so using a reverse tunnel to that means I can always connect home easily.

If you want a regular tunnel home for VNC then at work you would issue something like 

ssh -f [email]user@home.com[/email] -L 5900:localhost:5900 -N

Then VNC at work is config'd to connect to localhost 5900. ssh forwards it to home 5900 where it connects to your VNC server running. 

To do similar with a reverse tunnel at home you would issue,

ssh -f [email]user@work.com[/email] -R 5900:localhost:5900 -N

Now on your work machine port 5900 is listening and forwarding to 5900 at home. At work you can connect anytime to 5900 and get your home machine. No dynamic IP hassles and doesn't require opening a port at home. 

BTW the -N parm tells ssh to not run any other commands after starting but I have found then you usually need to manually kill the process. You could replace this with a command like "sleep 60" which keeps the tunnel open for 60 seconds after use and then auto-closes it.

I use my server often for secure SOCKS proxying with ssh ( -D 8080 ) and for reverse tunnels so I have a special user on that machine for connecting with limited privileges and no shell available to prevent abuse.

Running VNC without a secure tunnel is a terrible idea. It's not just about sensitive data but all your user id / passwords being sniffable. On Ubuntu one of the common ways to get hacked is via poorly config'd VNC.

So wait let me get this straight? You have to do both the tunneling and reverse tunneling? Because I have never done the reverse on the server. None of the other guides out there say anything about having to do something on the server. Only on the client side.

---

### Post by BkkBonanza on 2009-12-14
No. It's a choice. You may find one more practical for you at different times or under different conditions.

With a regular tunnel you need a port forwarded on your router at home and dynamic ip updating (if not static). Some people don't have access to their router so it can't be done.

With a reverse tunnel you need ssh listening somewhere else on the net like at work or some other server somewhere. The home machine can easily connect out to it and open a tunnel that forwards back to itself. Just the opposite.

It is possible to use both. I used to reverse tunnel from my sisters machine to my server and then tunnel from my home to connect to the server (and hence her home, via my server). Many things are possible - it's very flexible and powerfull but you choose according to what you need to do.

The thing to remember about a tunnel is that once it's started you need to connect to the port on your local machine not the remote one. The tunnel transports the data to the indicated port on the remote machine.

---

### Post by Adler on 2009-12-14
Well,

I'm now confused - LOL!

Hopefully, we'll get other responses.

Best Regards,

JJMacey
Phoenix, Arizona

---

### Post by CharlesA on 2009-12-14
> **HighCommander540 said:**
> Yeah, my opinion on the matter is no. Because I have tried to get SSH port forwarding to work and never manage to. Unless you have data that really need to be secure, just set-up VNC.

Having VNC open to the internet is a really bad idea, even if you configure yer firewall to only allow access to that port from a certain IP. VNC has little to no security and sends data unencrypted over the internet. Tunneling it over SSH means that it will be sent over an encrypted tunnel, and is therefore more secure.

> **Adler said:**
> Well,

I'm now confused - LOL!

Hopefully, we'll get other responses.

Best Regards,

JJMacey
Phoenix, Arizona

What are you confused with?

I have my server set up so that I can SSH into it from work and tunnel VNC over SSH if I *really* need a desktop (which isn't that often)

```
sudo apt-get install ssh
```

I've got mine setup to not use passwords, but to use a key-pair instead. I used the page [here]("http://fosswire.com/post/2008/01/bullet-proof-your-server-2-ssh/"), to secure the ssh server. It's probably not the best, but it works for me.

---

### Post by BkkBonanza on 2009-12-14
Maybe I can make this more step by step.

For VNC using a secure tunnel - forward, normal style...

Use Synaptics to select and install openssh-server on your home machine.

Select menu System, Prefs, Remote Desktop and choose the check mark to enable.
(In Ubuntu Remote Desktop is installed by default and is VNC using vino-server. vino-server listens for a connection on port 5900 by default).

Ok. So now vnc is listening on port 5900. Ideally you should further config vino to only listen for local connections not internet connections. AFAIK this has to be done with a command,

gconftool-2 --set /desktop/gnome/remote_access/local_only --type bool true

VNC will now not accept connections from the net but only from the local LAN. In your case that should mean only your machine. That's good.

Use the command "netstat -lntp" to see that vino-server is listening on port 5900 and that sshd is listening on port 22. All OK? Hopefully. Don't continue until this part is working. Use that web page you have to get and write down your home IP address assigned by your ISP (but remember it could change so you may need to config dyndns).

Now go to work or somewhere else on the net. Open a terminal shell and type,

ssh -f user@homeip -L 5900:localhost:5900 -N

Of course, replace user with your user name and homeip with your home IP address.
It will prompt for your password and if it can login successfully then you now have a tunnel to your home machine.

So what's going on now? ssh will listen on 5900 on your work machine and direct any traffic to port 5900 on your home machine. But what's listening on 5900 at home? vino-server. Hence, any traffic to 5900 on the work machine (localhost) is tunnelled to 5900 vino-server at home.

Lastly, at work open a remote desktop viewer, menu item Applications, Internet, Remote Desktop Viewer. Choose VNC, and enter localhost and Connect. If successful then it should now show you your home desktop.

There are other ways to do this as well. But this should work and is fairly straightforward. You can make a shortcut icon for the ssh command.

If you need a reverse tunnel instead because you can't open ports at home on your ISP connection then let me know. It's only slightly different.

This first time we've done some config but after this at work you only need the ssh command (set up a shortcut icon) and then start the remote dekstop. What could be easier? You could install gSTM with Synaptics - it will give a gui interface to ssh tunnels instead of the command.

What else? After you have this working you can take the extra steps to make it more secure. The page mentioned by CharlesA above has details.

---

### Post by CharlesA on 2009-12-14
For me at least, vino would never run if I wasn't logged in. Maybe your setup is different then mine as I ended up just disabling vino and using tightvncsever (and only launching it when I needed to access the GUI for some reason, and killing it after I was done)

---

### Post by BkkBonanza on 2009-12-14
I think you're right. You likely would have to install vino server differently than the default to have it run always. It's not something I use much. I almost always just use ssh and the command line for remote access. I would just stay logged in if I needed that. Tight VNC may be better. I just wanted to get something easy going here for him.

---

### Post by CharlesA on 2009-12-14
> **BkkBonaza said:**
> I think you're right. You likely would have to install vino server differently than the default to have it run always. It's not something I use much. I almost always just use ssh and the command line for remote access. I would just stay logged in if I needed that. Tight VNC may be better. I just wanted to get something easy going here for him.

Understandable. I think I use the command-line 90% of the time I am shh'd into my machine. Faster for me to get stuff done that way, especially over a slow WAN link. :D

---

### Post by YesSir on 2009-12-14
I installed [**webmin**]("http://www.webmin.com/") on my server at home, works perfectly. I have access through firefox, myname.no-ip.org:10000. However, I did read some security problems on this forum concerning webmin, but so far so good...

---

### Post by Lars Noodén on 2009-12-14
> **Adler said:**
> ...you can use SSH to log in to your computer over the Internet, start your VNC server, and use port-forwarding to securely access the VNC server...

You'll have to know which port(s) the VNC server is listening to on your home machine and forward to those.  IIRC tightvnc-server uses ports 5900+

```

# on the machine at work
ssh \
    -L 5900:localhost:5900 \
    -L 5901:localhost:5901 \
    -L 5902:localhost:5902 \
    *xx.yy.zz.aa*

```

Then on the machine at work, connect your vnc client to 127.0.0.1.  You really only need one of the -L lines above, just make sure that it matches the one that your VNC server is listening on.  The VNC server will also see a connection from 127.0.0.1...

---

### Post by CharlesA on 2009-12-14
> **Lars Noodén said:**
> You'll have to know which port(s) the VNC server is listening to on your home machine and forward to those.  IIRC tightvnc-server uses ports 5900+

That's correct.

> ```

# on the machine at work
ssh \
    -L 5900:localhost:5900 \
    -L 5901:localhost:5901 \
    -L 5902:localhost:5902 \
    *xx.yy.zz.aa*

```

Then on the machine at work, connect your vnc client to 127.0.0.1.  You really only need one of the -L lines above, just make sure that it matches the one that your VNC server is listening on.  The VNC server will also see a connection from 127.0.0.1...

Just wanted to note, that you can map to other ports as well. e.g., -L 8080:127.0.0.1:1500.
The local and remote ports don't have to be the same.

---

### Post by HighCommander540 on 2009-12-14
> **CharlesA said:**
> Having VNC open to the internet is a really bad idea, even if you configure yer firewall to only allow access to that port from a certain IP. VNC has little to no security and sends data unencrypted over the internet. Tunneling it over SSH means that it will be sent over an encrypted tunnel, and is therefore more secure.

Except the point I was trying to make is...Unless you have some information that you really need secured. Why go through all the trouble?

---

### Post by BkkBonanza on 2009-12-14
You don't want to protect your passwords?  
With VNC it's in the clear and anyone listening in can see it.

It's one extra command to secure it, why not do that?
Use a shortcut icon to make it really easy.

---

### Post by HighCommander540 on 2009-12-15
> **BkkBonaza said:**
> You don't want to protect your passwords?  
With VNC it's in the clear and anyone listening in can see it.

It's one extra command to secure it, why not do that?
Use a shortcut icon to make it really easy.

No, I don't actually. The password for my computer is completely different than my other passwords. Yeah, it is an extra command. That doesn't always work. Like i tried to point out. By default its not an enabled option for SSH to run with TCP forwarding. And even when you have it enabled it doesn't always work.

I have tried it a million times with every possible configuration and it still doesn't work. I have tried every guide there is and nothing works. It probably has something to do with my router, but still.

---

### Post by BkkBonanza on 2009-12-15
TCP forwarding is enabled by default.
If you can't get it to work then something isn't right.

I haven't ever had times when ssh just didn't want to work for me. It's rock solid as far as I know. If you can post info about what doesn't work for you maybe we can get it going. When you run the ssh command what response do you get? This will tell us why it's not going. Maybe it's the router - you need the ssh port (22) open and forwarding to your local machine enabled for port 22 as well. If not then you will get a "connection refused" message.

For debugging you may want to not include the -f in the ssh command as that starts it in the background. It may be easier to see details when not backgrounded. Also -v could be added to get more verbose during the connection.


> 
The password for my computer is completely different than my other passwords.


But once connected remotely then if you ever do sudo or gksudo then your user password will be exposed and easily logged.

Just trying to help.

---

### Post by Adler on 2009-12-15
Hi All,

Thanks for those comments. I think I'll do a sanity check by printing all the comments so far and studying them. Then I may just bring my notebook to work and put it in a room close to the work desktop to see how things will / would work.

Again thanks!

Best Regards,

JJMacey
Phoenix, Arizona

---

### Post by noway2 on 2009-12-15
As an alternative to VNC, consider FreeNX, which I believe tunnels through an encrypted connection by default.  Search for it here on the forums, there is a wiki document on using it that will explain a lot of things.

---

### Post by HighCommander540 on 2009-12-15
> **BkkBonaza said:**
> TCP forwarding is enabled by default.
If you can't get it to work then something isn't right.

I haven't ever had times when ssh just didn't want to work for me. It's rock solid as far as I know. If you can post info about what doesn't work for you maybe we can get it going. When you run the ssh command what response do you get? This will tell us why it's not going. Maybe it's the router - you need the ssh port (22) open and forwarding to your local machine enabled for port 22 as well. If not then you will get a "connection refused" message.

For debugging you may want to not include the -f in the ssh command as that starts it in the background. It may be easier to see details when not backgrounded. Also -v could be added to get more verbose during the connection.




But once connected remotely then if you ever do sudo or gksudo then your user password will be exposed and easily logged.

Just trying to help.

Um, well. I would have to disagree. I installed SSH when I installed my server on 8.04 and I had to go and enabled TCP Forwarding.

I know about the port forwarding. I SSH into the server all the time. Its only the tunneling that doesn't work. I have my router configured to open all the ports right for a remote web server.

I don't get any errors. It just does nothing.

edit: Also, you misunderstand me for what I would use VNC for. I don't need a GUI my main Ubuntu computer is a server only accessible via SSH (which is why my ports are configured like that). So I wouldn't be using VNC onto a computer that I cared about my password. That is why I am saying this. Why take the extra setup for something I don't care about.

---

### Post by BkkBonanza on 2009-12-15
After you run the ssh tunnel command, open a second terminal and run "netstat -lntp".
You should see ssh listening on port 5900. If it is then the tunnel is open.
If it isn't then there should be some indication of why not. If you can ssh to the machine then you can open a tunnel too. If this isn't working then something is wrong.

---

### Post by HighCommander540 on 2009-12-15
> **BkkBonaza said:**
> After you run the ssh tunnel command, open a second terminal and run "netstat -lntp".
You should see ssh listening on port 5900. If it is then the tunnel is open.
If it isn't then there should be some indication of why not. If you can ssh to the machine then you can open a tunnel too. If this isn't working then something is wrong.

Hey, so I believe that I have figured out what my problem is. The machine I am trying to forward the port (ssh to). Is my web server. So to get HTTP requests I have to do "ssh user@IP -L 9001:localhost:80 -N" to use it as an internet proxy. The problem is that my server already listens on port 80 to serve my web site. So whenever I try to connect all it will ever give me is my website.

So the issue is that I can make the port and number on my side, but on the server side for HTTP it needs ot be 80. And I can't do that.

---

### Post by BkkBonanza on 2009-12-15
Your best option for using ssh as a proxy is to use the SOCKS5 option. This will open a tunnel with socks proxy that can be used for web browsing, email, skype, torrents or whatever. The command is,

ssh user@ip -D 8080   (and other options if you like)

After doing this tell your app (Firefox, TB, Skype etc) to use a SOCKS5 proxy at localhost:8080.

Your app will talk to port 8080 and ssh will forward to the remote machine where it will open connections from there just as if they were being opened locally. The IP logged by any server you connect to will be the one for your remote machine not the one local, and any local firewall blocking or filtering is bypassed.

I use this to do torrents remotely with upwards of 200 connections through the one tunnel. From the local machine there is only one connection to your ssh server. Beautiful, because the local network doesn't have any idea what's going on due to the encryption.

The -L and -R options are better suited to specific fixed application tunnels.

Another useful tidbit is that if you add a Port 443 statement to your sshd_config then ssh will listen on that port too (assuming it's not already bound to your web server). People often do this because restrictive firewalls may block ports other than 80 and 443. Since 443 is SSL it's very difficult to tell the encrypted traffic isn't SSL but SSH instead. Sort of a stealth tunnel you could say.

---

### Post by BkkBonanza on 2009-12-15
Also note that a slight confusion in your use of the -L option above.

When you use -L shh listens on the local machine and forwards to the remote machine. It doesn't listen on the remote machine so it wouldn't be getting http requests being made to your server. If an app was listening on the server then this could get data to it, like if VNC is listening you can talk to it.

To have ssh listen on the remote machine and forward it back to you locally you would need to use the -R (reverse tunnel) option. 

eg. -R 80:localhost:8080 (or whatever ports)  

would listen on your web server port 80 (if not already bound!) and bring the traffic to you where it pops out on 8080. If you ran apache listening on 8080 local then it would get the requests.

---

### Post by HighCommander540 on 2009-12-15
> **BkkBonaza said:**
> Also note that a slight confusion in your use of the -L option above.

When you use -L shh listens on the local machine and forwards to the remote machine. It doesn't listen on the remote machine so it wouldn't be getting http requests being made to your server. If an app was listening on the server then this could get data to it, like if VNC is listening you can talk to it.

To have ssh listen on the remote machine and forward it back to you locally you would need to use the -R (reverse tunnel) option. 

eg. -R 80:localhost:8080 (or whatever ports)  

would listen on your web server port 80 (if not already bound!) and bring the traffic to you where it pops out on 8080. If you ran apache listening on 8080 local then it would get the requests.

No, you just misunderstood what I was saying. I am saying that since my server listens itself on port 80 for any connections. So when SSH tries to make a connection on 80 to port forward it apache just serves up my website. No matter what address I type. And I am not just theorizing. I tried to do it, and it just gave me my website no matter what. Even if I went to google.com or anything. So for people that are running apache. You have to use -D "SOCKS5" otherwise it will just serve your web page to yourself.


Eidt: NVM , what was here.

---

### Post by BkkBonanza on 2009-12-15
Exactly right and all it should do.

I'm telling you that using the -L option forwards to your server not from your server. So it connects you to port 80 on your server. It doesn't listen on port 80 on your server. I understand exactly what you said but you're expecting it to do what it shouldn't do.

Connecting to port 80 is like browsing to port 80 with your browser. All you will ever get there is your own web site because apache is listening to you not proxying for you.

FF -> local ssh -> server ssh -> apache on 80.

If you want to proxy then you need -D option because it will open connections from your server for you to other sites or destinations. -L will not open new connection out to other places, ever.

And -R will open a listener on your server and direct any requests back to your local machine.

As far as you've described how you're using it everything is working as expected. You cannot browse other sites through a -L type tunnel - it is forwarding not proxying.

---

### Post by HighCommander540 on 2009-12-16
> **BkkBonaza said:**
> Exactly right and all it should do.

I'm telling you that using the -L option forwards to your server not from your server. So it connects you to port 80 on your server. It doesn't listen on port 80 on your server. I understand exactly what you said but you're expecting it to do what it shouldn't do.

Connecting to port 80 is like browsing to port 80 with your browser. All you will ever get there is your own web site because apache is listening to you not proxying for you.

FF -> local ssh -> server ssh -> apache on 80.

If you want to proxy then you need -D option because it will open connections from your server for you to other sites or destinations. -L will not open new connection out to other places, ever.

And -R will open a listener on your server and direct any requests back to your local machine.

As far as you've described how you're using it everything is working as expected. You cannot browse other sites through a -L type tunnel - it is forwarding not proxying.

NVM, you're not getting my point. It works so whatever.

---

### Post by BkkBonanza on 2009-12-16
I understand fully what you said and what the problem is. You don't seem to be distinguishing between "connecting to" and "listening on". Apache is already bound to port 80 so nothing else can. But you can still connect to 80 - and when you do you will only be able to talk to Apache because it's bound to it. Unless you run an apache module for proxying then apache isn't going to do anything other then give you your own site - naturally.

---

### Post by HighCommander540 on 2009-12-16
> **BkkBonaza said:**
> I understand fully what you said and what the problem is. You don't seem to be distinguishing between "connecting to" and "listening on". Apache is already bound to port 80 so nothing else can. But you can still connect to 80 - and when you do you will only be able to talk to Apache because it's bound to it. Unless you run an apache module for proxying then apache isn't going to do anything other then give you your own site - naturally.

Ok, well I am literally not going to argue with you anymore. If you would actually f***** read my post. I did differentiate between listening and connecting. I said that my server (as in apache is) is already **_*listening*_** on port 80. And so when I try to ***_connect_*** via ssh I get served my own website. (And if you go back and read my post that is exactly what I said)

I was't even arguing with you. I was pointing out what happened as ironic and then f****** thanking you for telling me about the SOCKS part.

---

### Post by BkkBonanza on 2009-12-16
YES. That's what you said and what I read and I never said different. 
Why were you expecting something other than Apache to answer you on port 80? 
So I don't know why you keep saying I don't understand...
Time to unsubscribe from this thread.

---

### Post by Adler on 2009-12-16
Hi Guys,

I'm sorry that this thread has developed to this point.

I do realize that there are differing opinions about computing, but I've yet to get a good tutorial, only opposing opinions.

Trust me, I've been Googling my brains out. But, no luck to find the truth.

I keep trying to put another nail in the Microsoft coffin that I've been building. 

Hey, I'm slowly trying to convince my circle of friends / associates to another way of doing things. 

There are future "killer apps" out there, and I think this is one of them. Hey, I can spin my Desktop with Compiz and can run Microsoft Word 2007 on 9.10.

Sorry for the rant.

Best Regards,

JJMacey
Phoenix, Arizona

---

### Post by BkkBonanza on 2009-12-16
I don't know why you can't do this.
I gave you a detailed simple step by step procedure up above.
If you can't do it then why don't you ask a question regarding what isn't working for you. Short of someone coming to do it for you how do you expect to get anywhere.
There are only a few fairly easy steps to get this going and I listed them already.
There is no opinion involved in how to do it - this works fine.
After all this effort providing a solution here you're still saying there is nothing showing you how. Tutorials for this are all over the web.
Just sit down and do it.
I'm outta here now. Tired of trying to hold baby hands.

---

### Post by CharlesA on 2009-12-16
> **Adler said:**
> 
I do realize that there are differing opinions about computing, but I've yet to get a good tutorial, only opposing opinions.

Trust me, I've been Googling my brains out. But, no luck to find the truth.

So you wanted to remotely access your PC from work, right?

Did you need a GUI or just a terminal screen?

---

