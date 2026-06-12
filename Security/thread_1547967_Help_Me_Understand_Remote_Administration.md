---
title: "Help Me Understand Remote Administration"
date: 2010-08-07
forum: Security
---

### Post by sTpny on 2010-08-07
Hi People, 

I babysit about 20 Linux machines for total n00bs here in Penticton where I live, but I'm about to move 800kms away, and I'd really like to not leave all those people stranded without anyone to take care of their pc's, so I need to learn how to safely and securely do administrative functions on their machines remotely, which I have no clue how to do, and so I'm a n00b once again. 

So, does anyone have any helpful hints, ideas, solutions, for this old n00b?

Tony.

---

### Post by HermanAB on 2010-08-08
SSH of course.  

I live in the UAE.  My servers are in the USA, on the other side of the globe.  If I move any further away, I will be closer...

---

### Post by drdos2006 on 2010-08-08
Check out TeamViewer, it might be want you need.

[http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

regards

---

### Post by bodhi.zazen on 2010-08-08
> **sTpny said:**
> Hi People, 

I babysit about 20 Linux machines for total n00bs here in Penticton where I live, but I'm about to move 800kms away, and I'd really like to not leave all those people stranded without anyone to take care of their pc's, so I need to learn how to safely and securely do administrative functions on their machines remotely, which I have no clue how to do, and so I'm a n00b once again. 

So, does anyone have any helpful hints, ideas, solutions, for this old n00b?

Tony.

As you babysit, be sure to teach them how to sys admin for themselves. The basics are not too difficult.

SSH is by far the best solution, although this may involve teaching them to port forward. VNC is insecure and slow.

Be sure you understand how to secure any servers you install or enable, for ssh use keys and a firewall or denyhosts.

---

### Post by sTpny on 2010-08-10
Awesome link.. thats going into my bookmarks. Thanks

---

### Post by sTpny on 2010-08-10
> **bodhi.zazen said:**
> As you babysit, be sure to teach them how to sys admin for themselves. The basics are not too difficult.

SSH is by far the best solution, although this may involve teaching them to port forward. VNC is insecure and slow.

Be sure you understand how to secure any servers you install or enable, for ssh use keys and a firewall or denyhosts.
You are speaking way over my head I'm afraid. I don't know how to do any of those things you mentioned, but I'd sure like to know. Thanks for the direction.

---

### Post by bodhi.zazen on 2010-08-10
> **sTpny said:**
> You are speaking way over my head I'm afraid. I don't know how to do any of those things you mentioned, but I'd sure like to know. Thanks for the direction.

The ubuntu wiki has broken the ssh page up a bit, but you can starte her :

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

You can forward X applications over ssh, if needed, with the -X option

ssh -X user@server

If you use ssh, use keys and disable password logins.

---

### Post by sTpny on 2010-08-10
SSH does seem to be the best solution, now all I need to do is figure out how to set up my clients computers so I can SSH safely into them.. any help with that.  Everyone has a dynamic IP and most of them have a router as well. 

I should add that I'm doing this work for these people not as a favour, but as an exploration into a possible source of revenue within the open community. So far it's looking promising. Moving away is the next step, and I really haven't given it enough consideration. I'm pressed for time and I need help.

---

### Post by sTpny on 2010-08-10
Just read that SSH link.. wow.  SSH is even cooler than I thought it seems, and I now "kind of" know what port forwarding is. I should have set this up ages ago. How convenient. [I can leverage this.] Anyhow, here's my slightly flawed plan... 

  1. write a script to ..  
    a) replace the /etc/ssh/sshd_config file with one that .. 
       i)   AllowUsers adam # <--My universal admin account name *
       ii)  Port 2222 # <--a script might rotate this..[later]
       iii) LoginGraceTime 20 
       iv)  LogLevel VERBOSE # <-- I'd like to see if I'm getting pecked. 
    b) modify my `security_email_report` script to send the ssh logs.     
  2. sudo /etc/init.d/ssh restart # restart the ssh server
  3. put copies of both of these scripts into my cloud, and chmod +x.
  4. visit everyone; maintain the crafted false image of linux-guru and .. 
    a) login
    b) run the pre-made scripts from the cloud. 
    c) logout.
  5. Go Home and make sure I can administrate via the Internet. 

The trouble is that this wont work.. I won't be able to log on. The problem at this point is those damn dynamic ip's and those pesky routers.. Where do I logon to? How do I logon to a computer with a dynamic ip from over the internet? Through a router? I'm sure there is an easy solution to this.. I'm just not seeing it.

---

### Post by HermanAB on 2010-08-10
You could make each machine send you an email once a day with its public IP address.  (You will then most likely find that the addresses never change.)

---

### Post by spillage2 on 2010-08-10
sorry I too am only just dipping my toes into ssh. I am sure when you set up ssh on the clients computer (ssh server) you can deny all access apart from your own ip address to block down unwanted access.

ssh is very simple to set up initially but im still sorting out using keys rather than passwords.

I want to use ssh to run vnc through it.

sorry not much help but thought I would put my two pence in.

---

### Post by CharlesA on 2010-08-10
Look into dynamic dns if you think that the IP addresses change all the time.

If they are connected via router, you can just forward the port SSH uses and then connect via the external IP.

If all machines are running the same version of Ubuntu/Linux, you can just configure one sshd_config file and either send it to the other sysadmins or just sftp it to the server and restart sshd.

---

### Post by sTpny on 2010-08-10
> **HermanAB said:**
> You could make each machine send you an email once a day with its public IP address.  (You will then most likely find that the addresses never change.)

Yes, that would do it I think. And how would I do that exactly?  Don't I need the IP of the router that the computer is connected to (if it is), as well as the IP of the computer itself? I can get the IP of my computer, but it's just what my router calls my computer, and I have no idea how to get my routers IP address. Getting closer though.. thanks.

---

### Post by sTpny on 2010-08-10
> **spillage2 said:**
> sorry I too am only just dipping my toes into ssh. I am sure when you set up ssh on the clients computer (ssh server) you can deny all access apart from your own ip address to block down unwanted access.

My own address is also dynamic, so I think I can't use that feature, but I'm only allowing ssh access to the one administrator account, and I'm emailing hacker attempts to myself, so I'll know if anyone else is trying to break in.

> **spillage2 said:**
> ssh is very simple to set up initially but im still sorting out using keys rather than passwords.

Yes, I'd like to add keys as well, but I figure, once I get it working, I can make any additional changes via ssh. 


> **spillage2 said:**
> I want to use ssh to run vnc through it.

I have heard VNC is unsecure, but to be honest, I have no idea what it is. 

> **spillage2 said:**
> sorry not much help but thought I would put my two pence in.

All help is appreciated.. thanks.

---

### Post by sTpny on 2010-08-10
> **CharlesA said:**
> Look into dynamic dns if you think that the IP addresses change all the time.

If they are connected via router, you can just forward the port SSH uses and then connect via the external IP.

If all machines are running the same version of Ubuntu/Linux, you can just configure one sshd_config file and either send it to the other sysadmins or just sftp it to the server and restart sshd.
I'll look into Dynamic DNS, but I don't think port forwarding will work for me.. Most routers have more than one computer that I'll need access to, so forwarding a port to one of the computers won't help. (if my understanding is correct).. thanks though.  Good idea. I can set up my own pc like that.. so that I can logon to it from elsewhere, but I don't think I'll be able to use that on client pc's.  Thanks though.

---

### Post by sTpny on 2010-08-10
I haven't looked into Dynamic DNS yet, but right now, it looks like what I need is a script that will send me the ip of the computer/router whenever a change is detected, so that I've always got a complete address for the computer.. I'm sure I connect if I had that info, though I'm not exactly sure what that would look like.. something like.. 

ssh -X adam@123.234.345.456:567.678.789.901 

??? 

So, how do I find the IP of my router? 

I've determined that I could use a web-service to spit my IP out in a web-page, then grep the needed info out, but that'll break if the web-service ever changes their page too much.  There has to be a more reliable way of getting the routers IP, but what is it? 

Thanks for all the help guys.. Ubuntu is great, but people with Ubuntu are better.  You guys are all tops in my books. :)

ohh. Everyone is running ubuntu 9.04 or 10.04, except for five PCS.. Two have Netbook Ubuntu, two have Xubuntu, and one has LinuxMCE.  I always set up the latest lts Ubuntu unless there is a reason not too, but I only dist-upgrade when there is a reason too. (and actually - I always do a clean install)  I don't trust dist-upgrade on client machines, though I use it on my own.

---

### Post by bodhi.zazen on 2010-08-10
> **sTpny said:**
> I haven't looked into Dynamic DNS yet, but right now, it looks like what I need is a script that will send me the ip of the computer/router whenever a change is detected, so that I've always got a complete address for the computer.. I'm sure I connect if I had that info, though I'm not exactly sure what that would look like.. something like.. 

ssh -X adam@123.234.345.456:567.678.789.901 

??? 

So, how do I find the IP of my router? 

I've determined that I could use a web-service to spit my IP out in a web-page, then grep the needed info out, but that'll break if the web-service ever changes their page too much.  There has to be a more reliable way of getting the routers IP, but what is it? 

Thanks for all the help guys.. Ubuntu is great, but people with Ubuntu are better.  You guys are all tops in my books. :)

ohh. Everyone is running ubuntu 9.04 or 10.04, except for five PCS.. Two have Netbook Ubuntu, two have Xubuntu, and one has LinuxMCE.  I always set up the latest lts Ubuntu unless there is a reason not too, but I only dist-upgrade when there is a reason too. (and actually - I always do a clean install)  I don't trust dist-upgrade on client machines, though I use it on my own.

What you want is a service such as showmyip.com 

[http://show-my-ip.com/](http://show-my-ip.com/)

You can use curl to obtain your ipaddress

```
curl [noparse]http://show-my-ip.com/[/noparse]
```

---

### Post by CharlesA on 2010-08-10
> **sTpny said:**
> I'll look into Dynamic DNS, but I don't think port forwarding will work for me.. Most routers have more than one computer that I'll need access to, so forwarding a port to one of the computers won't help. (if my understanding is correct).. thanks though.  Good idea. I can set up my own pc like that.. so that I can logon to it from elsewhere, but I don't think I'll be able to use that on client pc's.  Thanks though.

What you could do is set up a server on each site, virtual or otherwise, that you can SSH into, then SSH from it into the other machines.

It's a bit messy but would work.

---

### Post by sTpny on 2010-08-12
Well.. I'm finished, if it works; I still need to test it.  I'll post the results and the script(s) I used to set it up once I confirm that it's working.  Thanks for all the help..

---

### Post by sTpny on 2010-08-17
Thanks for all of the help guys.. I've added what I've learned into my security and admin scripts, which aren't actually working yet, so I've started a new thread about that. 

[http://ubuntuforums.org/showthread.php?p=9728883#post9728883](http://ubuntuforums.org/showthread.php?p=9728883#post9728883)

Once that's working properly, I shouldn't have any trouble login in remotely from my new city.  Feel free to pop on over and help fix my broken scripts.

---

