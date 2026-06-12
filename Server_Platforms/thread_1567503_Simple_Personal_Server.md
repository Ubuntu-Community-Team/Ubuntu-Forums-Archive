---
title: "Simple Personal Server"
date: 2010-09-03
forum: Server Platforms
---

### Post by ibrrfarr on 2010-09-03
System:  Ubuntu 10.04 Desktop Edition with all updates as of today's post.  Proposed server:  Acer Aspire AST180-400A.  Proposed access from Ubuntu 10.04 Desktop Edition with all updates as of today's post from a laptop:  Toshiba Satellite A200.  Router:  Netgear N300 WNR 2000v2.  Provider:  Frontier Communications.  Type:  DSL.  Both are running LAMP and I believe SSH.  Can check on the SSH, but I believe I set it up in preparation.  Additionally, there will only be ONE connection at a time EVER!

I have already set up an account at DynDNS.  That's where I am at today.  I have minimal experience in Ubuntu; am learning and LOVE this system vs. Bill Hates/MS stuff!  I am willing to read, post and whatever is necessary to get this underway and thank all, in advance for your time! ):P



With all this said, what I have on both these machines is Mediawiki 1.16.0.  I am simply wanting to access the "server" from the laptop right now to add stuff to my wiki.  It won't be a domain name (e.g.; no www. whatever.com), but rather 197.whatever.

What I need to know is:


[LIST=1]
[*]Is this possible;
[*]What is the process;
[*]Is there a step-by-step tutorial for my unique situation (as it's really *not* going to be a public web server being that I am the only one to ever access it;
[/LIST]

So, this is my first post and I apologize if I didn't include everything I was supposed to or it is in the wrong area.

---

### Post by BkkBonanza on 2010-09-04
1. yes, just about any given systems can do this.
2. too big a question to answer, so break it down into what you need to start with.
3. use google. this situation isn't unique but you'd still have to patch together info from various tutorials and sources.

---

### Post by ibrrfarr on 2010-09-04
I simply need to access my wiki on my Desktop from my Laptop.  In this I mean I want to be able to add and/or retrieve data.  It would function like a website, but I would be the only person ever doing this.  A remote desktop type of deal, maybe?  So, that's the question in a nutshell.  In the first paragraph of my original post you will note the specs I have already loaded into play.

Thanx!

---

### Post by koenn on 2010-09-04
it's a wiki, right ?
you access it with a web browser, 
and then use whatever edit functions the wiki offers.

---

### Post by ibrrfarr on 2010-09-04
OK, to clarify:  my wiki is on my desktop computer in my house and I have my laptop with me on the road.  How do I use my laptop access my desktop at home via web browser.  I am sorry if I am missing something that pros take for granted; I have only been using Ubuntu about a month now.

Thank you.

---

### Post by jeight on 2010-09-04
Easiest solution would be to install Webmin.

---

### Post by jeight on 2010-09-04
If you want a GUI to access your server then install x2go (x2go.org). That will allow you run the server from anywhere. X2go is a better alternative to freenx or nomachine and I would recommend it. Just install the standalone x2go server on your server and then install the x2go client on all other machines. Good luck!

---

### Post by BkkBonanza on 2010-09-04
I couldn't figure out what you wanted to do but your third post has finally clarified it...

You want to access your web page from outside your network, from the internet but only for your own **private access**, right?

---

### Post by ibrrfarr on 2010-09-04
First thanx for all the replies!  I will look at the platforms mentioned and reply back after I read them

> **BkkBonaza said:**
> I couldn't figure out what you wanted to do but your third post has finally clarified it...

You want to access your web page from outside your network, from the internet but only for your own **private access**, right?

To address your statement, I don't have a 'web page' per se.  What I have is a an installation of mediawiki on my desktop computer at home.  I don't have a website nor a domain.  What I want to be able to do is access my desktop to enter stuff into my mediawiki by using my laptop.  It will be the only computer to do this via the internet.

I use the wiki to track information.  So what I want to be able to do is turn on my laptop in city A and through the internet access my desktop; specifically, my wiki,  at home.

Oh. let me add this, when I enter [http://localhost/](http://localhost/) it reads IT WORKS!  This is the default web page for this server.  No content has been added yet.  This is on the desktop computer that I hope to use as I guess what everyone is calling a server.

Thanks for helping me to ALL of you!

---

### Post by BkkBonanza on 2010-09-05
Your mediawiki is a website since you access it with your browser, even if it's at localhost.

You will have to setup your router to allow outside access, and I can help you do that, but first you have to answer a question. 

Do you want access to your mediawiki to be private (restricted) or are you ok with it being visible to the public? This will determine how you go about accessing it. I know you don't *need* the public to see it, but the decision is if they can see it even if by accident or by scanning.

---

### Post by koenn on 2010-09-05
> **jeight said:**
> Easiest solution would be to install Webmin.

> **jeight said:**
> If you want a GUI to access your server then install x2go 

the OP has a network issue.
Webmin or x2go will not solve that.

---

### Post by ibrrfarr on 2010-09-05
> **BkkBonaza said:**
> Your mediawiki is a website since you access it with your browser, even if it's at localhost.

You will have to setup your router to allow outside access, and I can help you do that, but first you have to answer a question. 

Do you want access to your mediawiki to be private (restricted) or are you ok with it being visible to the public? This will determine how you go about accessing it. I know you don't *need* the public to see it, but the decision is if they can see it even if by accident or by scanning.

I have coded in the necessary scripts in the LocalSettings.php already.  In essence it is ready to rock and roll.  I can access my router through it's setup screen.  So, ask whatever you need.  On certain questions responses I may edit the answers such as specific IP.

I have Sysinfo installed if you need specific info on this. 

Really thank ya here!

---

### Post by BkkBonanza on 2010-09-05
I've been trying to find out if you want to allow the mediawiki to be visible on the internet so that I can help you expose port 80 to the web, where anyone can access it, or, set you up with ssh as a secure remote access tool that allows you and only you to access the mediawiki. 

In the first case your page is visible and you may have a login password but to secure that you need to configure SSL and install a certificate.

In the second case your page is not exposed outside your LAN, and you use ssh from your laptop to connect to your server, and view your page. This method is more secure and actually easier to setup. It also has the advantage that you can do other things that are useful from your laptop.

---

### Post by ibrrfarr on 2010-09-05
Yes, the second version is best!  I have pm'd you as well.

I have ssh running as  ps -ef |grep ssh spit out a bunch of info

---

### Post by BkkBonanza on 2010-09-05
It's actually **sshd** you'll need running on the server
but that is probably what you mean.

Have you already tried to login with ssh from your laptop to your server?
This should be easy to do. We'll test it.

With your laptop connected to the LAN, open a terminal and type,

**ssh user@server-ip**

replace user with your server login name 
replace server-ip with the ip or hostname of your server 

You should get a password prompt and then a login message, and a prompt.
You are connect to a terminal on your server now.
If this works then, great. Type **exit** and enter, to logout again.

We can move on to the next step.

---

### Post by BkkBonanza on 2010-09-05
Next, if you didn't already configure sshd to accept your key, then we'll do that.

Continuing on the laptop... 

Type,

ssh-copy-id user@server-ip

It will prompt for password as before, and copy your key over so that you can access your server with your "key" instead of password. Easier and more secure.

Now if you try to login, 

ssh user@server-ip 

it shouldn't prompt for password, it should just connect and give you the login message.

Next, lets test the SOCKS proxy mode that ssh offers us. 

Still at the laptop, type,

ssh -fND 8080 user@server-ip

This will connect and start a proxy to your server. It shouldn't show anything if it is working. It should just come back to the prompt. But it has started a background process that acts as a localhost SOCKS proxy for you.

Now, on your laptop switch to your browser and select Edit, Preferences, Advanced, Network, Connection Settings. There is options for setting a proxy.

Choose "Manual", click SOCKS v5, in SOCKS-host enter "localhost" and for port, enter 8080. Click OK. Now Firefox is using your ssh proxy.

Any pages you surf to are now being actually requested from your server, encrypted and tunnelled to your laptop and given to Firefox. So go ahead and type the address for your mediawiki page. But don't use 127.0.0.1 - use the server-ip, because the proxy is set to bypass localhost (127.0.0.1). You should get your page.

This has all been a test to make sure you can do this.

Back in the terminal, type **pkill ssh** to kill the proxy in the background. Also in Firefox you may want to revert the proxy setting to "No proxy" again for now. 

There is a nice Firefox add-on called "QuickProxy" that gives you a single-click status bar icon to toggle proxy on/off without having to go into the menus. Get it, as it'll make life easy.

Next, we configure your router so that you can do the same thing out on the internet using your public ip and/or DynDns address.

---

### Post by ibrrfarr on 2010-09-05
> **BkkBonaza said:**
> It's actually **sshd** you'll need running on the server
but that is probably what you mean.

Have you already tried to login with ssh from your laptop to your server?
This should be easy to do. We'll test it.

With your laptop connected to the LAN, open a terminal and type,

**ssh user@server-ip**

replace user with your server login name 
replace server-ip with the ip or hostname of your server 

additionally when i cd Desktop and then ls i get the files that are on my laptop and NOT on the server

You should get a password prompt and then a login message, and a prompt.
You are connect to a terminal on your server now.
If this works then, great. Type **exit** and enter, to logout again.

We can move on to the next step.

ok installed ssh on the laptop and when i do this i have to use localhost instead of the name of the server.  other than that it works.  bear in mind that the user name is the same on the laptop and the server.  dont know if that's the deal or what.

it says port 22: Connection refused when I use xxx.tfdxxxxx

---

### Post by ibrrfarr on 2010-09-05
> **BkkBonaza said:**
> Next, if you didn't already configure sshd to accept your key, then we'll do that.

Continuing on the laptop... 

Type,

ssh-copy-id user@server-ip

It will prompt for password as before, and copy your key over so that you can access your server with your "key" instead of password. Easier and more secure.

Now if you try to login, 

ssh user@server-ip 

it shouldn't prompt for password, it should just connect and give you the login message.

Next, lets test the SOCKS proxy mode that ssh offers us. 

Still at the laptop, type,

ssh -fND 8080 user@server-ip

This will connect and start a proxy to your server. It shouldn't show anything if it is working. It should just come back to the prompt. But it has started a background process that acts as a localhost SOCKS proxy for you.

Now, on your laptop switch to your browser and select Edit, Preferences, Advanced, Network, Connection Settings. There is options for setting a proxy.

Choose "Manual", click SOCKS v5, in SOCKS-host enter "localhost" and for port, enter 8080. Click OK. Now Firefox is using your ssh proxy.

Any pages you surf to are now being actually requested from your server, encrypted and tunnelled to your laptop and given to Firefox. So go ahead and type the address for your mediawiki page. But don't use 127.0.0.1 - use the server-ip, because the proxy is set to bypass localhost (127.0.0.1). You should get your page.

This has all been a test to make sure you can do this.

Back in the terminal, type **pkill ssh** to kill the proxy in the background. Also in Firefox you may want to revert the proxy setting to "No proxy" again for now. 

There is a nice Firefox add-on called "QuickProxy" that gives you a single-click status bar icon to toggle proxy on/off without having to go into the menus. Get it, as it'll make life easy.

Next, we configure your router so that you can do the same thing out on the internet using your public ip and/or DynDns address.

ssh-copy-id does not work

pkill does not work

set the proxy up as specified on firefox.  kicks a 404 error.  the wiki on each machine is http:// 127.0.0.1/mediawiki/mediawiki-1.16.0/  don't know if that's an issue.

that's where i am at.  fire any questions you may have or perhaps try a remote go?

---

### Post by BkkBonanza on 2010-09-05
localhost would connect to your own machine not the server machine.

Just to clarify, there are two separate programs,

ssh is used to connect to another machine
sshd is a server that listens for connections

on the laptop you need ssh installed but not sshd 
on the server you need sshd as well as ssh  

sshd is usually installed by default on servers
and ssh is usualy installed by default on all ubuntu machines

sshd is called openssh-server in synaptic and repos.

you will need to get the ip or hostname of your server for this test and to configure the router later too.

don't continue if a step isn't working. it has to work before the next one will.

---

### Post by ibrrfarr on 2010-09-05
> **BkkBonaza said:**
> localhost would connect to your own machine not the server machine.

Just to clarify, there are two separate programs,

ssh is used to connect to another machine
sshd is a server that listens for connections

on the laptop you need ssh installed but not sshd 
on the server you need sshd as well as ssh  

sshd is usually installed by default on servers
and ssh is usualy installed by default on all ubuntu machines

they have different hostnames, (typed hostname in term), but they both have 127.0.0.1 when i run sys-adm-network in ipv.4

sshd is called openssh-server in synaptic and repos.

you will need to get the ip or hostname of your server for this test and to configure the router later too.

don't continue if a step isn't working. it has to work before the next one will.

ok open ssh client is installed on the laptop and open ssh client and server is installed on the server.  when i type myname@tfdllc (this is the username@servername) on the laptop i get port 22:Connection refused.  

i don't believe that the ssh server is installed on the laptop, but don't know how to check to make sure - ran sudo apt-get remove openssh-server and then sudo apt-get install openssh-client to make sure

---

### Post by BkkBonanza on 2010-09-05
On the server, confirm that sshd is listening on the correct port (22),
[B]
sudo netstat -lntp[/B]

will list any listening service sshd should be there.

If you have a firewall like ufw or something else, be sure port 22 is open.

Either case above could result in connection refused.

---

### Post by ibrrfarr on 2010-09-05
success!  i am in as i ran ifconfig in the server and now am logged in from the laptop!:popcorn:  will report on the other as i perform it

---

### Post by ibrrfarr on 2010-09-05
OK.  All worked except the copy id deal.  shot back ERROR:  no identities found.  here's how i typed it:  ssh-copy-id username@myipaddress  now, i entered this AFTER i had exited ssh

everything works except that! :p  i even surfed through the wiki to make sure it was the correct one and it was!

---

### Post by BkkBonanza on 2010-09-05
Hmmm. That should work but for now it's not a big problem. You can continue to use the password.

Before we go onto the router lets do one more step to make it a bit easier. 

On the laptop,

**pkill ssh** (in case you forgot to kill the proxy you tested with)
**sudo apt-get install gstm**

This will install a nice gui ssh proxy/tunnel manager allowing you to do this from the menu rather than using commands. 

I'm not sure if this adds a menu item. If it does then it'll be in Applications, Internet. If not then you can either make a shortcut or add a menu item. The program name is gstm.

It will pop up a little window with a list of proxys/tunnels. Should be empty.

Select "Add", to add a new one. Set the values as needed for login. And select Add again and choose type to be "dynamic", and port 8080. Save.

Back on the proxy list you should see the new one listed. Select it and click "Start".
It will prompt for a password. (If you had the key set it wouldn't).

Now the proxy is going. After that works, click "Stop". 

This just makes it nicer to work with from the desktop. Combined with "QuickProxy" in Firefox this whole thing becomes very painless.

And we're ready to do your router...

---

### Post by ibrrfarr on 2010-09-05
All working!

---

### Post by BkkBonanza on 2010-09-05
Super.
Now we do the router. We're going to forward a port so that from outside on the internet any connection requests to that port get sent on to your server in the LAN.

You need to login to your router control panel and look for the section on "port fowarding". If it's unclear then let me know the model# and I can find a guide to help out.

Ideally you would be able to set a src and dest port differently but not all routers can do that. Using a port different than 22 is good on the net because it helps cut down on the "scanning traffic" to your server. So if possible forward from a high port to port 22. 

eg. forward port 2456 to port 22 - dest is your server ip

If it doesn't have src and dst options, only a single port then for now just put port 22 and the server ip.

---

### Post by ibrrfarr on 2010-09-05
not really sure how to do this so i attached a screenshot.  please advise if i need to remove the ss in case it reveals too much info.  thanx!

---

### Post by BkkBonanza on 2010-09-05
No problem on screen shot. This info is readily available online.

That's good. For custom service type in a title like "ssh".
Then select TCP (as UDP isn't needed for this).
Then for starting port enter some high number like 2345 (it's not really secret)
Then for ending port enter 22.
And for server ip enter your servers ip (not hostname, so you'll need to know that)
Click Apply.

While you're in there look for the Dynamic DNS setup page. 
And enter your DynDns info there. 
Should be an option to choose DynDns, enter the user name and password.
And maybe your domain name, not sure.
And save that too.

---

### Post by ibrrfarr on 2010-09-05
states that the ending port value should be equal to or greater than the starting port value

set up the DNS stuff.  will this affect the rest of my computers or does it matter?  i have 3 desktops and the laptop running

---

### Post by BkkBonanza on 2010-09-05
Ah, I see they mean "range". So it doesn't allow different src/dest ports.
So just enter 2345 for both then. And we'll edit the server config instead.
(You can use some other port # just remember what # you enter)

---

### Post by ibrrfarr on 2010-09-05
done  cut off the ip address as i didn't know if it's serious or not

added the firefox plugin as well

---

### Post by BkkBonanza on 2010-09-05
Great. Also DynDns? You can come back to that if you like.

Next, we edit your server sshd config to listen on port 2345 instead of 22.
On the server,

**sudo nano /etc/ssh/sshd_config**

Look for the line that says "Port 22" and change it to "Port 2345".
Use whatever port # you used in the router.

**sudo pkill -SIGHUP sshd**
To cause sshd to re-read it's config

**sudo netstat -lntp**
To verify that sshd is now listening on port 2345.

On laptop,
Change your setting in gSTM to use port 2345 as well.

Test the proxy again, as before. Should still work.

---

### Post by ibrrfarr on 2010-09-05
attached screenshot.  when i manually enter in term username@10.0.0.x i get port22:Connection refused

however, when i use the gSTM program works like a charm!  odd, 'eh?

also, by simply clicking the p from that add on you gave me allows me to access the wiki on the server as well.  i suppose that is what it's for?

---

### Post by BkkBonanza on 2010-09-05
That's correct. When using the command line now you will need to use,

ssh -p 2345 user@server-ip
or
ssh -p 2345 -fND user@server-ip

so it knows to use the obscure port #.

You're now ready for a public ip test. Some routers will not route their public IP back to the LAN, so this may not work within your LAN. But we can try.

Since you're at the laptop terminal, try,

ssh -p 2345 user@public-ip

(using the current public-ip for your router - which you can find out in your browser by going to ip-adress.com for example).

If you setup DynDns already then you can also try the same with your DynDns address.
eg.

ssh -p 2345 [email]user@mysuperdomain.dyndns.com[/email]

---

### Post by BkkBonanza on 2010-09-06
QuickProxy allows one-click toggling of Firefox's proxy mode.

When green you are using the SOCKS proxy and routing your pages through your server.
When red you are going direct out your own laptop.

This makes little difference now at home. 

Out on the road you will now have a secure encrypted tunnel back home which you can use for accessing your LAN, and for securing any network activity (like browsing). 

This is great for web cafes and airports when you don't know who may be listening in on non-secure wifi traffic, for example. 

But only traffic going through your localhost:8080 SOCKSv5 proxy is going through the tunnel. So for example, Thunderbird email won't until you also configur it to use the proxy like Firefox.

Now a simple two steps for secure surfing - gSTM to start the proxy, quickproxy to toggle FF to use it.

Also, any sites visited will log you as coming from your home not from where you really are on the road.

---

### Post by ibrrfarr on 2010-09-06
i get a connection timed out.  now the dns acct has my public ip address and we haven't done anything to the router config so i don't know if that's the reason.  average speeds here are 800 up and 250 down

---

### Post by BkkBonanza on 2010-09-06
No, it's probably just that your router won't route traffic for the public ip back into the LAN. This is common. Sometimes there is a config option to enable that "feature" but often not.

If you like you can pm me with your dyndns domain and I can test if it's reachable from here.

Otherwise you can take your laptop out somewhere and do a real remote test.

You can also use an online port checker to test your public ip.
eg. [https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2)
and choose custom scan and enter 2345 to test that port.

It should say it is open. It may even know it's ssh listening.
But if it's closed/stealth then there is a problem.

---

### Post by ibrrfarr on 2010-09-06
it's 0020EST here.  i'm gonna hit the sack.  i REALLY want to thank you for helping me along here!  this is GREAT!  i really hope it helps others as well!

i will check in the morning for anything to try from any of your suggestions for the timeout, the router config, etc.

---

### Post by BkkBonanza on 2010-09-06
There are a few small config changes that can be made to improve things but mostly it should be good to go. We can do these later if needed...

Your server could have a "static lease" set in the router to avoid it's IP changing. 

Sometimes it's nice to use port 443 for outside access because some places may block non-standard ports. The downside is some ISPs block 443 on home accounts, and that port tends to get scanned more. So it's a trade off.

---

### Post by ibrrfarr on 2010-09-06
> **BkkBonaza said:**
> No, it's probably just that your router won't route traffic for the public ip back into the LAN. This is common. Sometimes there is a config option to enable that "feature" but often not.

If you like you can pm me with your dyndns domain and I can test if it's reachable from here.

Otherwise you can take your laptop out somewhere and do a real remote test.

You can also use an online port checker to test your public ip.
eg. [https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2)
and choose custom scan and enter 2345 to test that port.

It should say it is open. It may even know it's ssh listening.
But if it's closed/stealth then there is a problem.

your link was locked down with some kind of security message, i used T1 and it replied for port 2345:  
myipaddress:  isn't responding on port 2345

open port check tool said:  myipaddress:  port 2345 isn't responding.  reason: Connection timed out

got ur link to work:  stealth

[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=courier new,courier][SIZE=3][COLOR=black]0 Ports Open
0 Ports Closed
1 Ports Stealth
---------------------
    1 Ports Tested

THE PORT tested was found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by ibrrfarr on 2010-09-06
I pm'd you on the full stats.  Wanted to keep a running log here so that others who might need the same info I do could follow along.  Contacted the ISP and they don't block much; a few in the 300s and 400s and a 4000 something.  Said I shouldn't have any issue with 2345 and I was explicit with them in what I was trying to do.  The tech said they didn't have any problems with it.

---

### Post by ibrrfarr on 2010-09-06
shots attached

---

### Post by BkkBonanza on 2010-09-06
Those settings are all fine and should not be changed if they work normally now.
The settings for each router are slightly different in wording. According to your manual you want to go to Advanced, LAN Settings and at the bottom where it says Address Reservations you want to add the IP + MAC for your server. This is a "static lease" (their name for it).

This shouldn't affect forwarding but it does need to be done anyway. It could be that this router won't forward unless a static lease is in place, so you may as well do it now.

---

### Post by ibrrfarr on 2010-09-06
done.  when i enter ssh -p 2345 username@public ip i get ssh:  connect to host xx.xx.xx.xx port xxxx:  Connection timed out

i presume the username is the name on my laptop (like john@johnlaptop)

---

### Post by BkkBonanza on 2010-09-06
Actually the username is the one on the server but I think you said they were the same anyway. It's the server account you are logging into.

That is the correct response for a port that is not listening / stealth. Which means it is not forwarding, and I get the same result from over here.

---

### Post by ibrrfarr on 2010-09-07
So, the final issue seems to be getting the laptop able to speak to the server via the public net; it talks to it via the local set up now.  And what is preventing us is this 'stealth' issue.  We can rule out my ISP, Frontier, as they say they don't block that range nor do they care.

I am guessing here, but I believe that this final issue now lies with the router in and of itself.  I am going to call them today and posit the question(s) to them.

REALLY thank ya for all the help here and hopefully we can do two things with this post:  a) chrono it from start to finish for a good example to others wanting to do what I am doing; and if it turns out to be a router issue, b) chrono what Netgear says to do.

---

### Post by ibrrfarr on 2010-09-07
Alright, the deal is that I had to configure my modem, in this case, to accept port forwarding.  So, we're back on track!  Ya! Ya! Ya!:p

Now, SSH works through the public IP address; it states that my DynDNS password is wrong.  I changed the password in DynDNS, but still doesn't like it.

Standing by for further instructions and know you're probably asleep by now.

---

### Post by BkkBonanza on 2010-09-07
Good to hear it works.
I can't really help much with the password issue. 
Verify that the pwd works on DynDns I guess. Make sure UPPERlower case is right...

---

### Post by ibrrfarr on 2010-09-07
So, now when I log via ssh -p xx username@publicip and it dumps me into my server, how do I access my wiki?  Do I simply place my public ip where I was placing the 10.0.0.x?

And are further steps I need to pursue here?

---

### Post by BkkBonanza on 2010-09-07
You just do the same as you did before on your laptop when we tested it. 

Start the proxy in gSTM, click the QuickProxy icon in FF. Then use the server ip or hostname address same as before. It doesn't matter whether you use it inside the LAN or out on the net. Your public ip is only for getting access, once in, it's the same as being at home.

You're set now unless you have other things you want to do when away from home on the LAN.

---

### Post by ibrrfarr on 2010-09-07
SIMPLY INCREDIBLE!!! :popcorn: 

 I _***really***_ appreciate all the help on this!  If I understand this correctly, once the 'tunnel' is opened my laptop is really only acting as a keyboard for the server?!  Man, simply mind boggling!  I will always be thankful for your relentless assistance!

---

### Post by BkkBonanza on 2010-09-08
Glad I could help.

It's not that your machine acts as a keyboard for the server, because your machine still does all the processing. But any program you configure to use your secure tunnel will feed the IP packets over the tunnel to your server **AS IF** it were running there.

The SOCKS proxy is powerful - it allows your machine to send & receive data on any port on the server, dynamically chosen by the local browser or other program (only if config'd to use the proxy, remember).

This secures your local web traffic when in non-secure public locations like web cafes. But I should add a couple notes...

Security wise you should set up for **key authentication** with your server. The first time you connect it will store the key fingerprints at each end to make sure that you don't get intercepted by a MITM (man in the middle attack) fake in future, which otherwise with password is potentially more vulnerable. Data is encrypted but with passwords it's possible to get intercepted by a MITM and not detect you are talking to a fake server. So for better security and ease of use - no pwd prompts, set up key auth. It should be as easy as opening a terminal on the laptop and using ssh-copy-id.

**ssh-copy-id user@server**

Last note - if you are concerned about local privacy on the road or in external business networks then you should set the **Remote DNS** option in FF to true. This is done by browsing to the internal config page **about:config** and typing "dns" in the search box. Find the option that says "network.proxy.socks_remote_dns" and double click to make it **true**.

This forces FF to do DNS lookups across the tunnel too. Otherwise it does them on the local connection outside the tunnel and this leaks info about what sites you access.

Good Luck!

---

### Post by ibrrfarr on 2010-09-08
> **BkkBonaza said:**
> Glad I could help.

It's not that your machine acts as a keyboard for the server, because your machine still does all the processing. But any program you configure to use your secure tunnel will feed the IP packets over the tunnel to your server **AS IF** it were running there.

The SOCKS proxy is powerful - it allows your machine to send & receive data on any port on the server, dynamically chosen by the local browser or other program (only if config'd to use the proxy, remember).

This secures your local web traffic when in non-secure public locations like web cafes. But I should add a couple notes...

Security wise you should set up for **key authentication** with your server. The first time you connect it will store the key fingerprints at each end to make sure that you don't get intercepted by a MITM (man in the middle attack) fake in future, which otherwise with password is potentially more vulnerable. Data is encrypted but with passwords it's possible to get intercepted by a MITM and not detect you are talking to a fake server. So for better security and ease of use - no pwd prompts, set up key auth. It should be as easy as opening a terminal on the laptop and using ssh-copy-id.

**ssh-copy-id user@server**

Last note - if you are concerned about local privacy on the road or in external business networks then you should set the **Remote DNS** option in FF to true. This is done by browsing to the internal config page **about:config** and typing "dns" in the search box. Find the option that says "network.proxy.socks_remote_dns" and double click to make it **true**.

This forces FF to do DNS lookups across the tunnel too. Otherwise it does them on the local connection outside the tunnel and this leaks info about what sites you access.

Good Luck!

Sorry to belabor things, but on the ssh-copy-id situation I get:

 /usr/bin/ssh-copy-id:  ERROR: No Identities found

This occurs whether I run server as the name of the server or the public ip addy.  I type it after I have set up the ssh connection manually.  Here is my process:  I goto terminal and set the ssh up.  Then I goto SSH Tunnel Manager and turn it on and finally I turn on the Firefox proxy plugin.  This process is how I start it all the time.  Maybe I don't have to do all this?

Changed the network.proxy.socks to **true**.

I am going on the road today to check out the set up and will report back anything *including* the big smiles on my face!

---

### Post by BkkBonanza on 2010-09-08
Ah, I guess the default install of ssh doesn't make a key for you by default.
Poor memory and no new system for years does this to you.

Try this,

**ssh-keygen -t dsa**
(asks for password but just leave blank)

which should create a key (identity), and then repeat the ssh-copy-id.

Leaving the password blank means that any user who can login to this laptop account can use your key without an additional password.

---

### Post by ibrrfarr on 2010-09-08
ok, i am doing this from the laptop *while logged in ssh into the server*, it is asking "Enter file in which to save the key (/home/xxxxx/.ssh/id_dsa):"

i didn't enter anything yet as i need to make sure i should be doing it this way and then what file to save them to or just hit the enter key

---

### Post by BkkBonanza on 2010-09-08
Do not do this while logged into the server!

You need to do this on your laptop in a regular terminal. It creates a key on your laptop and saves it in your .ssh dir on the laptop. Default values are fine. 

Same for copy cmd - on laptop. It will copy it to the server for you.

Oh no. I just read your last message above. 

Do this command local on the laptop. 

------ 
> This occurs whether I run server as the name of the server or the public ip addy. I type it after I have set up the ssh connection manually. Here is my process: I goto terminal and set the ssh up. Then I goto SSH Tunnel Manager and turn it on and finally I turn on the Firefox proxy plugin. This process is how I start it all the time. Maybe I don't have to do all this?

But also - when you use gSTM you do not have to use the command line. You use either gSTM or ssh command but not both together as then you have two tunnels open. I suggested gSTM purely to make it easier by not opening a terminal, and not having to kill the tunnel manually.

---

### Post by ibrrfarr on 2010-09-08
> **BkkBonaza said:**
> Do not do this while logged into the server!

You need to do this on your laptop in a regular terminal. It creates a key on your laptop and saves it in your .ssh dir on the laptop. Default values are fine. 

Same for copy cmd - on laptop. It will copy it to the server for you.

Oh no. I just read your last message above. 

Do this command local on the laptop. 

------ 


But also - when you use gSTM you do not have to use the command line. You use either gSTM or ssh command but not both together as then you have two tunnels open. I suggested gSTM purely to make it easier by not opening a terminal, and not having to kill the tunnel manually.

All good so far.  When I put ssh-copy-id xxx@xxx it says "ssh: connect to host xxx port 22: Connection refused"  should I add -p xxxx after the copy-id part?

---

### Post by BkkBonanza on 2010-09-08
Yes, it needs to know the port if it's non-standard.

Also, when done you need to tell gSTM to use the key file.

In gSTM,
Click the tunnel, Click Properties, for privkey enter **/home/xxxxx/.ssh/id_dsa.pub**
where xxxx is username. This tells it to use the key and not password.

---

### Post by ibrrfarr on 2010-09-08
accidentally did that but got an error anyway.

---

### Post by ibrrfarr on 2010-09-08
xxx@xxx:~$ ssh-copy-id -p 2345 xxx@xxx
Bad port 'umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_key

this occurs when i run (without the tunnel running or on the proxy internet)

---

### Post by BkkBonanza on 2010-09-08
Hmmm. I just checked the ssh-copy-id script and it's not smart enough to use an alternate port... 

Ok. Well lets do this the manual way. 

Again, from the laptop terminal in your home directory do,

**rsync -vpte "ssh -p xxxx" .ssh/id_dsa.pub user@server:~**

that copies the file over, now login and we fix it up on the server,

**ssh -p xxxx user@server**

Once logged in do, (make sure spelling is correct)

[B]mkdir .ssh
cat id_dsa.pub >> .ssh/authorized_keys
chmod 700 .ssh
chmod 600 .ssh/authorized_keys
rm id_dsa.pub[/B]

---

### Post by BkkBonanza on 2010-09-08
Actually I was just experimenting and found a way to trick it into doing the port...

Instead of all that work try this, still in laptop terminal,

**ssh-copy-id -i .ssh/id_dsa.pub "-p xxxx user@server"**
(where xxxx is port#)

That worked for me here as it plugged in the port with the user.

---

### Post by ibrrfarr on 2010-09-08
> **BkkBonaza said:**
> Hmmm. I just checked the ssh-copy-id script and it's not smart enough to use an alternate port... 

Ok. Well lets do this the manual way. 

Again, from the laptop terminal in your home directory do,

**rsync -vpte "ssh -p xxxx" .ssh/id_dsa.pub user@server:~**

that copies the file over, now login and we fix it up on the server,

**ssh -p xxxx user@server**

Once logged in do, (make sure spelling is correct)

[B]mkdir .ssh
cat id_dsa.pub >> .ssh/authorized_keys
chmod 700 .ssh
chmod 600 .ssh/authorized_keys
rm id_dsa.pub[/B]

This is the script I opted for.  Works as far as I can tell; I base this upon when I go into SSH Tunnel it does not ask for a password anymore.

Here's the road report (80 miles away using Arby's wifi):  kept getting a time out on the link to the wiki.  Now the wiki addy is still set to 10.0.0.x/mediawiki/xxx  Also, the tunnel config is still set to the Host as 10.0.0.x It has stuff under it about redirection that says type: dynamic, port 8080 to host: n/a to port: n/a   Config on the socks manual proxy is v5 selected, Host:localhost Port: 8080 no proxy for: localhost, 127.0.0.x 

Hmnn, so here is how I do things, maybe there's an error on my part --- I'm a newbie so quite possible!

[LIST=1]
[*]Power on
[*]Activate gSTM
[*]Activate proxy add on for the net in the bottom right hand corner
[*]Click the link for my wiki
[/LIST]

I did it manually and found I could access the server and use ls to verify it was the server w/o problems.

Could it be that I don't have enough bandwidth or whatever to do this?  Averages around 600 Mbits down and 250 up.

If you are comfortable I can pay the international call and we can sync a time and I can call.  If so, just pm me.

Either way, it looks like we're about there!  Thanx again!

---

### Post by BkkBonanza on 2010-09-09
I can't use intl phone very well from here. But...
I set up an experimental Help Chat Room. See my new signature.
I thought this may help with more interactive help sessions because this back and forth posting is annoying for other forum users who keep seeing the thread forced to the top.

*Ignore my last PM

---

