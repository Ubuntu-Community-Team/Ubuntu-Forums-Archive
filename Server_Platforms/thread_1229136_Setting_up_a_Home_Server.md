---
title: "Setting up a Home Server"
date: 2009-08-01
forum: Server Platforms
---

### Post by WildcatWhiz on 2009-08-01
I don't want to thread-jacker...but. :rolleyes:

I'm a first-timer looking to set up a home server for a lot of the above reasons many of you listed. I'd *like* to use it as a desktop as well with a GUI...I need some advice.

Here's what I'd want to do (in order of importance):
1. Be able to host and send my own e-mail
2. Be able to access mail via web (maybe Squirrel mail? I've heard good things)
3. Share files, printer/scanner with another computer in the house
4. Be able to remote-in to the server from any location
5. Possibly host my own website

Wow, that's a lot! What would this take? i.e. Do I need to purchase a domain name? Would you recommend Ubuntu Server and add a GUI, etc, or Ubuntu Home and add the server apps?

Here's my rig:
Intel Core2Duo e8400 @4.0Ghz
4GB 1066 DDR2 RAM
250 GB HDD 7200rpm

---

### Post by tobiness on 2009-08-01
> **WildcatWhiz said:**
> I don't want to thread-jacker...but. :rolleyes:

I'm a first-timer looking to set up a home server for a lot of the above reasons many of you listed. I'd *like* to use it as a desktop as well with a GUI...I need some advice.

Here's what I'd want to do (in order of importance):
1. Be able to host and send my own e-mail
2. Be able to access mail via web (maybe Squirrel mail? I've heard good things)
3. Share files, printer/scanner with another computer in the house
4. Be able to remote-in to the server from any location
5. Possibly host my own website

Wow, that's a lot! What would this take? i.e. Do I need to purchase a domain name? Would you recommend Ubuntu Server and add a GUI, etc, or Ubuntu Home and add the server apps?

Here's my rig:
Intel Core2Duo e8400 @4.0Ghz
4GB 1066 DDR2 RAM
250 GB HDD 7200rpm

Hmm, To Host Your Own Email Or Website Unless U want it you@youripaddress you need to buy a domain ($10 A Year) And Setup DNS To Link It Witch Is Fairly easy, Ive never actualy tryed to share printers and scanners so i cant really help you there, i would recommend installing ubuntu server 8.10 or 9.04 then the best thing to do would be install the GUI (Gnome Or KDE From There)
You Say You Want Remote Access? This Can Be Very Unsecure But At The Same Time Good,
I Would Recommend Useing WebMin, Its Fast, Secure, You Have Complete Control With It, 
4 Ghz Intel Dual Core XD Wanna Swap I got a dual core 2.0 Ghz, pentium 3 1.3 Ghz and a 1 ghz pentium 2 ill give u the pentium 3 lol jks, but i am jealous, XD
Squirrel Mail I personaly never liked however, i supose a mail client is a mail client, i use roundcube for webmail or Eudora (Witch U Install On The Comp)

---

### Post by Sef on 2009-08-01
> I don't want to thread-jacker...but. :rolleyes:

Moved posts to their own thread because you were.

---

### Post by jamesrfla on 2009-08-02
1 and 2. Citadel Mail server is very easy to use and comes with it's own web mail interface. I think Zmail does about the same thing except a different looking web mail interface. 
3. Samba file server.
4. If you want to remote into it via command line you can use openssh-server and to get it do ```
sudo apt-get install openssh-server
``` If you want to get a GUI remotely you can use remote desktop in System>Administration>Remote Desktop I think. 
5. You can install apache2 web server and be able to host your own web server. If you don't want to buy a domain you can get a Dyndns.
Hope this helps.

---

### Post by jrollf on 2009-08-02
For remote terminal/command line access I run an SSH server and use the PuTTy client to access my server from all over the place (PuTTy works on Windows machines).

For remote GUI/Desktop access I run the NX server from [www.nomachine.com]("http://www.nomachine.com").  I also use their client software (which is available for windows and linux) to access the server from anywhere.

Both the above can be set up fairly securely if you pay attention to the various tutorials that can be found on these forums.

I've used dyndns ([www.dyndns.com]("http://www.dyndns.com")) to take care of the domain name issue.  Free for personall use.

For a mail server / web mail access I have used Citadel in the past, however I found I was just too lazy to tell everyone to change my e-mail address (Couldn't get the rest of my family to change over either).  And I decided I didn't want to have to worry about spam filtering, what happens when/if my server goes down, etc, especially since I was the only one going to use it.  Ended up sticking with Yahoo.

For a webserver, Apache works really well with Linux, in fact it will install automatically depending on the options you choose when you install Ubuntu Server edition.

That said, don't forget you will need to configure any router you might have to pass the various ports from the internet to you server.  You may want to set up some alternate ports as I have found many places (like my work) block the "standard" ports, like port 22 that ssh runs on.  Your router can usually take care of this by setting up port forwarding and re-assignments.

Have fun!

---

### Post by HermanAB on 2009-08-02
Simple really.  Just install regular Ubuntu and add Citadel and Apache.

However, to host mail, you either have to slave off your ISP mail server, or you need to get a static IP address and domain name.

---

### Post by jamesrfla on 2009-08-02
> **HermanAB said:**
> Simple really.  Just install regular Ubuntu and add Citadel and Apache.

However, to host mail, you either have to slave off your ISP mail server, or you need to get a static IP address and domain name.

I am able to host mail on a Dynamic IP address. I also don't need a domain name. I just have a Dyndns and I have my router update m DNS whenever my Dynamic IP address changes. Unless you are going to be sending out more than 600 messages a day you should be okay without those two things.

---

### Post by jrollf on 2009-08-02
> **jamesrfla said:**
> I am able to host mail on a Dynamic IP address. I also don't need a domain name. I just have a Dyndns and I have my router update m DNS whenever my Dynamic IP address changes. Unless you are going to be sending out more than 600 messages a day you should be okay without those two things.

I 2nd this comment.  I successfully set up an e-mail server in the same method.  The only extra I had to do was call my ISP (AT&T Uverse) and ask them to open up the e-mail port(s) for me. I don't remember which port it was, if I recall correctly the setup instructions for Citdel covers it.

---

### Post by jamesrfla on 2009-08-02
> **jrollf said:**
> I 2nd this comment.  I successfully set up an e-mail server in the same method.  The only extra I had to do was call my ISP (AT&T Uverse) and ask them to open up the e-mail port(s) for me. I don't remember which port it was, if I recall correctly the setup instructions for Citdel covers it.

The port for mail servers to talk to other mail servers or to send mail to server to server is port 25. The only thing I had to do with Embarq DSL was to bridge my modem and that was it.

---

