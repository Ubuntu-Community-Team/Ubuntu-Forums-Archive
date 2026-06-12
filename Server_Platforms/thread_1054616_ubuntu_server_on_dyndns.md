---
title: "ubuntu server on dyndns?"
date: 2009-01-29
forum: Server Platforms
---

### Post by audio_uphoria on 2009-01-29
Hello, I'm trying to set up a linux server at home and i dont have access to my router so I'm setting up a host name at dyndns.com. My question is do I have to use ubuntu 8.04 lts version or can I use ubuntu 8.04 desktop edition to set up a server... If so how? Thanks.

---

### Post by redroad55 on 2009-01-29
If I understand your question correctly the answer is yes the 8.04 desktop kernel and the server kernel are the same except for the gui being added to the destop version .. you will however need internet access for either in order to install the pkgs. from repositories for whatever your server environment requirements are ..If I can answer any further questions post back and I will do my best..best to you

---

### Post by hyper_ch on 2009-01-30
what do you want to do? if you really want to run a server, don't install desktop.

if you want to run a desktop with some server capabilities, install from desktop or alternate and then add whatever server services you need.

---

### Post by audio_uphoria on 2009-01-30
Thanks, I was wondering about the server and desktop versions because as of yet I'm not competant enough to navigate through the terminal. I will attempt to set up my server with the desktop version until I am more comfortable.

---

### Post by hyper_ch on 2009-01-31
if you want a server, don't install desktop on it.

---

### Post by hrod beraht on 2009-01-31
> **audio_uphoria said:**
> ...i dont have access to my router so I'm setting up a host name at dyndns.com.

Dyndns simply gives you a fixed IP address for the internet IP address that your service provider may periodically change (i.e. the external IP address of your router). You will still need access to your router to enable port forwarding to the particular computer that is your server.

For example:

You type [http://me.dyndns.com](http://me.dyndns.com) into a browser. Dyndns translates that into the internet IP address of your router, e.g. 123.456.789.001 and forwards the request there.

Your router then sees an http request (on port 80) coming in from the internet and then forwards that request to the local network address of the computer you have forwarded that port to, e.g. 192.168.1.100

The server computer on your local network at address 192.168.1.100 then receives the http request and the running Apache daemon then handles serving the web page request.

The important point I'm trying to make is that Dyndns alone won't get you there. You still need to ensure the proper forwarding by your router.

Hope that helps,
Bob

---

### Post by unixeducation on 2009-01-31
> **hyper_ch said:**
> if you want a server, don't install desktop on it.

I disagree with this approach for beginners. Especially for a small home server that you're using for learning purposes, there is absolutely nothing wrong with starting with what you're comfortable with. Hell, OpenSolaris installs the desktop by default, and a lot of folks are using that as a server platform.

Personally, I wind up running most of my servers on either Debian or Ubuntu Server, but I've also got years of experience at shell prompts. When someone is learning, it can be really beneficial to have a GUI on the same system.

---

### Post by hyper_ch on 2009-01-31
> **unixeducation said:**
> I disagree with this approach for beginners. Especially for a small home server that you're using for learning purposes, there is absolutely nothing wrong with starting with what you're comfortable with.

A desktop on a server does not help at all in learning on how to run a server. It'll just hold you back.

---

### Post by falconed7 on 2009-01-31
I made an Ubuntu home server using the server edition after only 3 weeks of using the desktop version on my notebook. It can be a little daunting but If you're following a well written guide and using the forums then nothing should go wrong.

---

### Post by drubin on 2009-01-31
> **falconed7 said:**
> I made an Ubuntu home server using the server edition after only 3 weeks of using the desktop version on my notebook. It can be a little daunting but If you're following a well written guide and using the forums then nothing should go wrong.

Things do go wrong. it is a fact of life. People make mistakes things don't always turn out the way you want them. 

But like falconed said using guides/forums will help fix them pretty easily. So don't worry about it :)

---

### Post by skunkbad on 2009-01-31
In regards to dyndns, I this you should consider zoneedit instead. Zoneedit doesn't force you to be a subdomain of their site.

DYNDNS = mydomain[COLOR="Blue"].dyndns[/COLOR].com

ZONEEDIT = mydomain.com

---

### Post by neilevan814 on 2009-02-01
Hear ye hear ye!  I would never have been able to learn to set up a LAMP server and get a free dyndns domain name without the comfort of my desktop environment.  I am learning a lot this way and have a server that is functioning on the internet and between my own computers at home.

---

### Post by Cardale on 2009-09-07
I know this thread is some what old, but how is your domain functioning working with Dyndns?  I have been having domain issues.

---

### Post by SoftwareExplorer on 2009-09-07
> **Cardale said:**
> I know this thread is some what old, but how is your domain functioning working with Dyndns?  I have been having domain issues.

What isn't working?

---

### Post by Cardale on 2009-09-07
The local lan ip is always reachable and working, but for some reason the domain will go totally unresponsive then magically go back to working all on its own.  Like something got messed up and then reset without me having to touch a thing.

---

### Post by SoftwareExplorer on 2009-09-08
Maybe you need to set your dyndns client to update more often? Is the section of times it doesn't work for consistent?

Also, what happens if you go to somewhere like whatismyip.com when it isn't working, and then lookup your website name?

---

### Post by Cardale on 2009-09-08
I've been working on security so much my domain is doesn't work at all.  Any traffic to port 80 timesout.

I have shorewall and host allow setup what other security features come enabled on Ubuntu server should I look at?

---

### Post by SoftwareExplorer on 2009-09-08
[QUOTE=Cardale;7918190]Any traffic to port 80 timesout./QUOTE]
Now thats some serious security (at the small cost of performance, err, well, working)!:) I was just thinking it might be an issue with how your dynamic dns client was set up. I have to admit that I know fairly little about security.

---

### Post by Cardale on 2009-09-08
I figured it out.  On my router I had a filter put on for multicast and NAT redirection traffic.  Once I disabled that it worked perfect.

Good to know those settings work.  Yeah dude this is a good thread - [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472) and [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

