---
title: "Jabber with external domain"
date: 2008-09-08
forum: Server Platforms
---

### Post by StefanX on 2008-09-08
I would like to use Jabber via my own Jabber server with an "external domain" (my own one). This means my Jabber server is available as jabber.example.com but I could use the JID [email]name@example.com[/email] instead of [email]name@jabber.example.com[/email]. 

I found a [_description (German)_]("https://ssl.tiggerswelt.net/wiki/jabber/externe_domains") to configure my DNS by defining SRV for _jabber._tcp.example.com _xmpp-server._tcp.example.com and _xmpp-client._tcp.example.com. 

My question is how to configure a Jabber server appropriately? I tried ejabberd but could not figure out how to configure the described scenario (also it runs well for non-external domain scenario). **I appreciate any help how to solve this scenario in general or how to configure any Jabber server (it has not to be ejabberd) specifically.**

---

### Post by regala on 2008-09-08
> **StefanX said:**
> I would like to use Jabber via my own Jabber server with an "external domain" (my own one). This means my Jabber server is available as jabber.example.com but I could use the JID [email]name@example.com[/email] instead of [email]name@jabber.example.com[/email]. 

I found a [_description (German)_]("https://ssl.tiggerswelt.net/wiki/jabber/externe_domains") to configure my DNS by defining SRV for _jabber._tcp.example.com _xmpp-server._tcp.example.com and _xmpp-client._tcp.example.com. 

My question is how to configure a Jabber server appropriately? I tried ejabberd but could not figure out how to configure the described scenario (also it runs well for non-external domain scenario). **I appreciate any help how to solve this scenario in general or how to configure any Jabber server (it has not to be ejabberd) specifically.**

By any chance, did you read ejabberd documentation on their website ?
[http://ejabberd.im](http://ejabberd.im)

---

### Post by StefanX on 2008-09-08
> **regala said:**
> By any chance, did you read ejabberd documentation on their website ?
[http://ejabberd.im](http://ejabberd.im)

Yes, I did read the documentation but don't found it helpful regarding my scenario. I defined two URLs in the "host" section: jabber.example.com and example.com but this did not work out. Any idea?

---

### Post by regala on 2008-09-08
> **StefanX said:**
> Yes, I did read the documentation but don't found it helpful regarding my scenario. I defined two URLs in the "host" section: jabber.example.com and example.com but this did not work out. Any idea?

well, what is your real issue ? When you says "external domain" scenario, do you mean that hosts outside your own network can't use it ?
Are hosts outside of your network (on the Internet) allowed to access your server on ports 5222, and 5269 ? Can they _reach_ these ports or did you have to redirect anything to achieve it ?

I personnally did this and "it just works" as soon as I changed the same piece of configuration, you, yourself changed.

Could you then be more specific about what is your problem, is it a failure from the outside and do you see anything related in your ejabberd logs ?

there can be so many sources of failure, you have to me more specific if you want us to understand your problem.

rgds

---

### Post by StefanX on 2008-09-08
> **regala said:**
> well, what is your real issue ? When you says "external domain" scenario, do you mean that hosts outside your own network can't use it ?
Are hosts outside of your network (on the Internet) allowed to access your server on ports 5222, and 5269 ? Can they _reach_ these ports or did you have to redirect anything to achieve it ?

I personnally did this and "it just works" as soon as I changed the same piece of configuration, you, yourself changed.

Could you then be more specific about what is your problem, is it a failure from the outside and do you see anything related in your ejabberd logs ?

there can be so many sources of failure, you have to me more specific if you want us to understand your problem.

rgds

The log of ejabberd tells me:

=INFO REPORT==== 2008-09-08 14:36:43 ===
I(<0.673.0>:ejabberd_listener:90): (#Port<0.812>) Accepted connection {{85,178,XXX,XXX},4468} -> {{84,19,XXX,XXX},5223}

=INFO REPORT==== 2008-09-08 14:36:43 ===
I(<0.907.0>:ejabberd_c2s:417): ({tlssock,#Port<0.812>,#Port<0.813>}) Failed legacy authentication for [email]name@example.com[/email]/Psi

(where XXX is added by me manually)

First I tried to access to ejabberd with Pidgin. Pidgin tells me "503": Service not available. So I tried instead Psi which gives me more details:

<?xml version="1.0"?>

<stream:stream xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client" to="example.com" >

<?xml version='1.0'?><stream:stream xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' id='2015691542' from='example.com' xml:lang='en'>

<iq type="get" id="auth_1" to="example.com" >
<query xmlns="jabber:iq:auth">
<username>name</username>
</query>
</iq>

<iq from="example.com" type="result" id="auth_1" >
<query xmlns="jabber:iq:auth">
<username>name</username>
<password/>
<digest/>
<resource/>
</query>
</iq>

<iq type="set" id="auth_2" to="example.com" >
<query xmlns="jabber:iq:auth">
<username>name</username>
<digest>e213d7c69c988905672a9299f5fcfa16ca68e8a9</digest>
<resource>Psi</resource>
</query>
</iq>

<iq from="example.com" type="error" id="auth_2" >
<query xmlns="jabber:iq:auth">
<username>name</username>
<digest>e213d7c69c988905672a9299f5fcfa16ca68e8a9</digest>
<resource>Psi</resource>
</query>
<error type="auth" code="401" >
<not-authorized xmlns="urn:ietf:params:xml:ns:xmpp-stanzas"/>
</error>
</iq>

Hope this helps. Please let me know which further information you need.

---

### Post by regala on 2008-09-08
> **StefanX said:**
> The log of ejabberd tells me:

=INFO REPORT==== 2008-09-08 14:36:43 ===
I(<0.673.0>:ejabberd_listener:90): (#Port<0.812>) Accepted connection {{85,178,XXX,XXX},4468} -> {{84,19,XXX,XXX},5223}

=INFO REPORT==== 2008-09-08 14:36:43 ===
I(<0.907.0>:ejabberd_c2s:417): ({tlssock,#Port<0.812>,#Port<0.813>}) Failed legacy authentication for [email]name@example.com[/email]/Psi




Why do you use port 5223 ? This is legacy SSL, you should not use it, but 5222 with TLS.

> 
First I tried to access to ejabberd with Pidgin. Pidgin tells me "503": Service not available. So I tried instead Psi which gives me more details:

<?xml version="1.0"?>

<stream:stream xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client" to="example.com" >

<?xml version='1.0'?><stream:stream xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' id='2015691542' from='example.com' xml:lang='en'>

<iq type="get" id="auth_1" to="example.com" >
<query xmlns="jabber:iq:auth">
<username>name</username>
</query>
</iq>

<iq from="example.com" type="result" id="auth_1" >
<query xmlns="jabber:iq:auth">
<username>name</username>
<password/>
<digest/>
<resource/>
</query>
</iq>

<iq type="set" id="auth_2" to="example.com" >
<query xmlns="jabber:iq:auth">
<username>name</username>
<digest>e213d7c69c988905672a9299f5fcfa16ca68e8a9</digest>
<resource>Psi</resource>
</query>
</iq>

<iq from="example.com" type="error" id="auth_2" >
<query xmlns="jabber:iq:auth">
<username>name</username>
<digest>e213d7c69c988905672a9299f5fcfa16ca68e8a9</digest>
<resource>Psi</resource>
</query>
<error type="auth" code="401" >
<not-authorized xmlns="urn:ietf:params:xml:ns:xmpp-stanzas"/>
</error>
</iq>

Hope this helps. Please let me know which further information you need.

Well seems like you fail with the password. Do you register this particular user (matt) with ejabberdctl ?
Or did you try to create a new account with account creation deactivated ?

oh and maybe could you provide (safely, by hiding sensible information) the config file for ejabberd.

rgds

---

### Post by StefanX on 2008-09-08
> **regala said:**
> Why do you use port 5223 ? This is legacy SSL, you should not use it, but 5222 with TLS.

Because Pidgin is not compatible with up to date TLS. :mad:
See [http://developer.pidgin.im/ticket/1435]("http://developer.pidgin.im/ticket/1435")
I would appreciate any fix or work around!

> **regala said:**
> Well seems like you fail with the password. Do you register this particular user (matt) with ejabberdctl ?
Or did you try to create a new account with account creation deactivated ?

oh and maybe could you provide (safely, by hiding sensible information) the config file for ejabberd.

rgds

You are right. There was a mistake with the user account because in the meanwhile I configured ejabberd from scratch (dpkg-reconfigure) and forgot to define the new user correctly. I assume this fixed my original problem and added the problem with the user. Now it works. Thank you! :-)

To sum up:
*  When configuring initially with dpkg-reconfigure I defined jabber.example.com as the host. (Initially it seems that I defined in this step a wrong host)
* Afterwards I added "example.com" to the "host" section of /etc/ejabberd/ejabberd.cfg
* and added the user [email]name@example.com[/email] via ejabberdctl.

Now I am trying to disable the web interface because of security reasons and try to give my new user [email]name@example.com[/email] administrator rights. Don't know yet how to...

---

### Post by regala on 2008-09-09
> **StefanX said:**
> Now I am trying to disable the web interface because of security reasons and try to give my new user [email]name@example.com[/email] administrator rights. Don't know yet how to...

Add this in your ejabberd.cfg and that should do this trickery :)
{acl, admin, {user, "name", "example.com"}}.
(do not forget the '.' at the eol)

and to disable the web interface, comment the service section ejabberd_http, with the port 5280 and that same config file. Restart ejabberd, you're done.

---

