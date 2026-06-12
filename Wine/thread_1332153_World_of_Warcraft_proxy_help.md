---
title: "World of Warcraft proxy help"
date: 2009-11-20
forum: Wine
---

### Post by mattgwinnutt on 2009-11-20
I live in university halls of residence and have to use proxy servers to connect to world of warcraft.

I installed putty and freecaps with wine, freecaps seems to run okay but putty I get to the login screen and I cant type anything into the black box.

Is there a way to get these programs to run with wine?

Is there perhaps an alternative proxy server program(s) which I could use to connect to WoW?

I have cedega installed also and the linux version of putty.

I'm a complete begginer with linux so a nice tutuorial would be great.

Thanks, Matt

---

### Post by Filipek on 2009-11-20
> **mattgwinnutt said:**
> I live in university halls of residence and have to use proxy servers to connect to world of warcraft.

I installed putty and freecaps with wine, freecaps seems to run okay but putty I get to the login screen and I cant type anything into the black box.

Is there a way to get these programs to run with wine?

Is there perhaps an alternative proxy server program(s) which I could use to connect to WoW?

I have cedega installed also and the linux version of putty.

I'm a complete begginer with linux so a nice tutuorial would be great.

Thanks, Matt

Could you please describe the situation in more detail? Why are you using Putty in linux? Are you trying to tunnel the connection somewhere? Through the proxy server? Is SSH tunneling allowed on that server?

Without detailed description of your environment, it is hard to make up some solution.

---

### Post by mattgwinnutt on 2009-11-20
Okay i'll give as much detail as possible considering i'm pretty new at this.

Could you please describe the situation in more detail?

Okay, theres a port - 1119 which you need open to play WoW, I live in university halls and theres no way I can get this port open.  I've recently installed Ubuntu as my os as yesterday my WoW got hacked, some keylogger / trojan on my windows os.  

The way it works is Putty connects to the wowtunnels.com servers and then sets up a local proxy server on port 1080 so other applications can use this port to "tunnel" their traffic through. A windows program, either Proxycap/Freecap then "proxifies" WoW as it doesn't have proxy support out of the box, and tells it to use the local proxy server created by Putty.

Why are you using Putty in linux?

I'm new at this and it's a familiar gui.

Are you trying to tunnel the connection somewhere? Through the proxy server? 

As explained above yes.

Is SSH tunneling allowed on that server?

Yes it's made for people to connect to WoW who can't connect on there own networks.

I hope this gives more insight to the situation, sorry if I missed anything out.  If there is other programs that can do what Putty, Freecap and Proxycap did on windows but for Linux (which I believe there is, it's just insanley difficult to learn anything about this from google for a beginner like me... tried for almost 24 hours already solid) then a tutorial / beginners guide would be great on how to set it up would be appreciated.

I need to setup; 

Connection from local machine to hostname:  Proxy1.wowtunnels.com port:  80

This connects me to the remote server that has the ports I need.

Connection from wow.exe to the remote server to be tunneled through the wowtunnels.com host.

World of Warcraft does not support proxy servers so wow.exe has to be ''proxified'' and opened up through another program that allows it to be tunneled by whatever program is tunneling to the wowtunnels remote host.

These are the values I need to play WoW (the ones I used on windows proxycap program so should be the same for linux);
[I]
Type:                     Application:          IP range:                  Ports:           Transports:                     Proxy: [/I]
Proxy wow.exe     (all)             3724             TCP              127.0.0.1:1080 
Direct                      wow.exe                   (all)                                   3724                              UDP 
Proxy wow.exe     (all)             1119             TCP              127.0.0.1:1080 
Direct                      wow.exe                    (all)                                  1119                              UDP 
Proxy wow.exe     (all)             6112 - 6119   TCP              127.0.0.1:1080 
Direct                      wow.exe                    (all)                              6112 - 6119             UDP 

Currently it is port 1119 that is totally inaccessible to me.

---

### Post by mattgwinnutt on 2009-11-21
bump

---

### Post by Filipek on 2009-11-23
Hi, try to use tsocks which is the linux replacement "proxyfying applications" without native SOCKS support.

Here is some easy guide:

[http://kakku.wordpress.com/2007/11/18/proxify-any-application-tsocks-and-proxychains-force-any-program-to-communicate-through-a-socks-https-proxy-or-use-cascading-proxies/](http://kakku.wordpress.com/2007/11/18/proxify-any-application-tsocks-and-proxychains-force-any-program-to-communicate-through-a-socks-https-proxy-or-use-cascading-proxies/)

Simple video guide: [http://www.youtube.com/watch?v=VRjoq27_wTY](http://www.youtube.com/watch?v=VRjoq27_wTY)

I would probably try that for you but I have a direct connection. Let us know and if you are not successful, I will test that in some way.

The potential problem might be with wine since you will not run tsocks wow.exe but **tsocks wine wow.exe**.... We will see whether your network is able to handle that...

*Edit: and please delete that "bump" thread :-)*

---

