---
title: "dyndns.org behing 2 routers"
date: 2005-12-19
forum: Server Platforms
---

### Post by timczer on 2005-12-19
I have been able to get my server working, and accessible from other computers.  I signed up for a dyndns.org account to deal with dynamic ip addresses.  

My issue is a have my cable modem going through a router(for my internet phone service) then through my wireless router and then to my computer.  I set up port forwarding on both to allow access to the apache server.  Using my current ip address and the open port ([http://111.111.11.101:2000](http://111.111.11.101:2000) for example) gets me onto the server.  Now I am trying to get the dyndns.org address to reach my server.  I have DDNS available on both routers.  I set them both up with my account information, but when I put the web address in, it only goes to the second router and enters the setup screen for the router instead of continuing through to the server.  

What do I need to change to get this to access my server with the dyndns.org address?

---

### Post by adwait on 2005-12-19
Apparently the setup of that server is also using port 80. So either change the port for the web admin of that router, or turn it off completely.

---

### Post by timczer on 2005-12-19
The webserver is set up to listen on the same port (let's say 20000), the firewall has a rule to open that port, and both routers have rules to forward to that port.   I need to have both routers as I have the internet phones as well as use the wireless router to use my laptop and my son's computer in his room.  The first router that is getting the dynamic ip is sending the connection on to the second router.  I don't know how to get the second router (which is setup with a static ip address) to send the connection on to the listening port on my computer.  I enabled DDNS on both routers, but I am not sure if I should have done this on the second router.  If not, what should I have setup on that router to get the connection through?

---

### Post by harisund on 2005-12-19
If I am not much mistaken, you must be setting up a webhop service if you are using dyndns.org. The default port when using dyndns is always 80. Look at the FAQ and the WebHop service on dyndns.org
I would also suggest a look at no-ip.org where you can set up automatically which port to forward to.

---

### Post by timczer on 2005-12-19
The webhop service seems to work.  My concern is that I was unable to enter in the webhop hostname in that field when setting up DDNS on my router.  It says it isn't valid.  So will this mean that any time my dyamic ip address changes I will need to go to the dyndns.org site and change the forwarding ip address?

---

### Post by harisund on 2005-12-19
Basically, whenever your IP adress changes (you would expect it to if it were dynamic) then you need to update the DNS records which is what dyndns.org does for you. 

I think dyndns.org does provide a dynamic update client (though I am not sure for what operating systems) which periodically checks the ip address of the machine it is running on and updates your account, so that the hostname you requested points to your current IP address. 

I use no-ip.com which I know provides a dynamic update client for Linux. It automatically updates every 30 minutes on my server (which I have behind a router and set up port forwarding, much the same way you have done.) Though 30 minutes is an overkill, considering my IP changes atmost once a month.

---

### Post by timczer on 2005-12-19
I went the no-ip.com route and set up the account and the updater they have for download.  This seems to work right now.  I will see how it works when my ip address gets updated.  Thanks for the help.

---

### Post by harisund on 2005-12-19
Sure. No problem. In fact, even I am waiting for my ip to change to make sure it gets updated. 

Regards,Hari

---

### Post by mathew.chacko on 2006-01-10
I am too in a same situation. I tried No-IP2 and dynDNS and my problem is same. when I try "mathew.zapto.org" or "mathew.homelinux.org" from my wireless notebook I get routers control pannel. Any Idea. I am not clear what to do in both the routers? Any one can help in step by step procedure? 

Till now what I did:
1. Installed apache and created an index.html, works fine with 192.168.0.2 (wireless routers reserved IP address for this notebook).
2. created an account with No-IP.com (mathew.zapto.org)
3. installed noip2 client. looks like working fine.
4. What to do in routers? not clear..... any help...

Thanks in advance.

Mathew.

---

### Post by harisund on 2006-01-10
Basically if you want to look at a website, port 80 is what your Apach listens on (by default atleast.) So when you make a request at the router for port 80, looking at your setting as of now, the router thinks it is a call to itself and opens the router control panel. 

What you could do is enter the control panel and look for an option that could be titled either "Virtual Server" or "Port forwarding" or something similar. Or look up in the internet with the search terms including your router's make / model and terms like the above. 

Make the router forward port something externally to your 192.168.0.2's internal port 80. (That is external on the WAN side, exposed to the internet and internel on the LAN side amongst your machines having 192.168.0.* addresss) 

Then type <your website name>:<the port you chose to forward> 

Hope I was clear enough !

---

### Post by mathew.chacko on 2006-01-10
Thanks its clear. The option I found under section **NAT**. But I failed to ping from my DSL router to 192.168.0.2. It only pings to wireless router 192.168.0.1. Any idea why?

NAT - Network Address Translation -	SUA Only	Edit Details

Zyxel 650ME-11

---

### Post by harisund on 2006-01-10
Yes, NAT is the option. You are right. 

Could you please explain what you mean by failed to "ping from my DSL router"? How did you ping from the DSL router? 

Also, I think it would be more clear if you could explain the setup of your house internet. For example, I have a cable connection which means a cable wire from the ISP to a modem, then a ethernet cable from the modem to my router and then router to different machines. How about yours?

---

### Post by mathew.chacko on 2006-01-10
Thanks harisund. The DSL router has a ping tool in Diagnostic option.

The setup of my house is similar to yours. cable wire from the ISP to a modem, then an ethernet cable from the modem to wireless router and my stations are wireless stations. Hope its clear.

Thanks in advance.

---

### Post by timczer on 2006-01-10
I don't know if this will help, but this is what I did.  I needed to set everything but the first router to a static address.  I then port forward from the first router to the static address of the second router.  For example I set up the forwarding as apache ports 40001 to 40010, then forward to 192.168.2.200 which is the statuc IP of the second router.  Then in the second router I set port forwarding for the same port range, but forward to the static ip in my computer, lets say 191.168.2.201.  Then in /etc/apache2/ports.conf tell apache which port to listen to (in this example, 40001).  If you have a firewall, you need to set a rule to allow that port traffic through.  

Using no-ip.org worked well because it allows you to set the port in the configuration.  You download and set up their client that supposed to let no-ip.org know when your ip changes (mine hasn't yet so I don't know if that works or not).  I switched from using port 80, which is the default as some of the advice I read on the forums said that this port is blocked by some ISP's.

---

### Post by harisund on 2006-01-10
mathew.chacko
did you get what timczer posted? What he has done is an ideal setup. 

Also, I have 3 quick questions. 

1. What is your current ip? Or output of ifconfig? I am guessing it is 192.168.0.2
2. Assuming your wireless router has a web interface, how do you access that? I am assuming through 192.168.0.1 ? 
3. Assuming your DSL router has a web interface, how do you access that? What address do you type in your browser?

Maybe that will help me understand things a bit better...

---

### Post by mathew.chacko on 2006-01-11
Yes **harisund**, you have guessed the IP address correct
DSL router has a web interface, ip address: **192.168.1.1**

Yes I tried **timczer's** method. Now I feel that I may be missing some software. Do I need BIND, resolve, etc utilities. As I have installed as **Desktop** and not as **server**. Is this is the problem? Otherwise it sould not be so difficult.... am i right?

Apache works well using IP **192.168.0.2**.

Thanks in advance.

---

### Post by harisund on 2006-01-11
[QUOTE=mathew.chacko]Thanks its clear. The option I found under section **NAT**. But I failed to ping from my DSL router to 192.168.0.2. It only pings to wireless router 192.168.0.1. Any idea why?
[/QUOTE]

Yes, your DSL router can not ping 192.168.0.2 directly. Here are a couple of points to keep in mind. .. 

1. Your wireless router acts as a firewall, effectively shielding every machine behind it. In other words, all the machines that are connected to the wireless router are hidden. The DSL router all the time thinks there is only machine connected to it, which is 192.168.0.1. That is why it can not ping 192.168.0.2 (your Apache machine) directly (as it is shielded by 192.168.0.1). Clear?
2. Your wireless router also acts as a gateway. Meaning every incoming packet to and outgoing packet from your server has to pass through the wireless router. (This is what is NAT: Network Address Translation.) 

So, if you want your no-ip to work, let's do it all on a different port 8080, since ISPs are likely to block 80. Also, both your DSL and your wireless router have web interfaces (at 192.168.1.1 and 192.168.0.1 respectively.) at port 80, let's just ignore 80. 

1. Go to no-ip and in your domain settings, do a port redirect of 80 to 8080.
2. In your DSL router interface (at 192.168.1.1) search for a NAT, virtual server or port forwarding option, and forward external port 8080 to internal port 8080 of 192.168.0.1 . If you do not find any, search for something called DMZ and make sure it has 192.168.0.1.
3. In your wireless router interface (at 192.168.0.1) search for the same NAT, virtual server or port forwarding option and forward external port 8080 to internal port 80 of 192.168.0.2. 
4. Do not change your Apache configuration, and let it continue listening to the default 80 port. 

Hope I am clear. I don't see any reason this shouldn't work .. 

As long as you have Apache2 installed and you can see it at 192.168.0.2 you don't need any other utilities.

---

### Post by mathew.chacko on 2006-01-11
Nope. message:

The connection was refused when attempting to contact 84.227.141.177:4001

What happen to 192.168.1.2, the static address assigned to wireless router by DSL router?

---

### Post by mathew.chacko on 2006-01-11
Should we need to configure dynamic DNS in both the routers?

---

### Post by timczer on 2006-01-11
The 84.227.141.177:4001 refers to you actual ip address currently assigned by your ISP.  The 4001 would be the port that is being contacted. The refusal is strange as that seems to me that the dsl router is not being reached.  Is the 84.227.141.177 your actual external ip address?  If so a couple of things to look at:

Be sure that the first router (the dsl) is forwarding the port (and from what you have, you have no-ip.org sending traffic to port 4001) to the static ip address of the wireless router, not the local ip address.  Make sure it is enabled, and the protocal is right (I can choose both).  In your wireless router, make sure you have the same thing, with the port forwarded to the static ip of your pc.  Then make sure you have apache listening to that port.  Then I would restart apache and see if it works.  

You should be able to type your actual ip address colon port into your browser and at least get to the first router.  If you can do that, if you keep working at the port forwarding you should get through into the pc.

---

### Post by mathew.chacko on 2006-01-13
Thanks for the tip. It looks like problem is in DSL router.

The web page works well using ip 192.168.1.2:4001 (static wireless router address assigned by DSL router). That means the wireless router configuration is correct. Right?
And not with 192.168.1.1:4001, which throws an error: "The connection was refused...".

The NAT configuration is:
port 4001 to 4012, ip 192.168.1.2 and also tried 192.168.0.1

Thanks in advance

---

### Post by timczer on 2006-01-16
Yes, it does seem that you are stuck at the first router.  At Dyndns.com (I think that is right, or at no-ip.org) does the ip address you get as yours match the one that is set up for your account with no-ip.org?  

Let me then go through my set up and see if you are similarily set up.  In your first router, you should have it set to obtain the ip address automatically.  You should then have a local ip address for this router, for example 192.168.2.1.  In this router you should forward to the static ip address of your second router (the wireless).  This should be of the form 192.168.2.xxx (192.168.2.100 for example, it needs to be of the same group as the first router).  In your second router, you should have the gateway set as the internal ip of the first router (192.168.2.1 in our example).  Then the static ip set as 192.168.2.100.  The internal ip address (local) then could be something like 192.168.1.1.  Set forwarding on this router to your pc static ip, which should be of the form of the second router (192.168.1.100, for example).  Then in your pc set the static ip, with the gateway as the local ip of the second router, 192.168.1.1.

Both routers should be forwarding the same port range, and apache needs to be listening on that port, and if you have a firewall, that port needs to be opened (firestarter does not have this open by default, so you will need to set a policy to allow this traffic or you will get the refused connection). 

 Remember, if you use the local ip addresses you are working within your network, not really going outside to the web and coming back in.  

Let me know if you get it working.

---

### Post by mathew.chacko on 2006-01-20
Thanks. I changed the 2 routers to 1 modem router and this worked. Just great. 
Thanks again.

---

