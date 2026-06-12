---
title: "Can local SSH server tunnel through local proxy?"
date: 2010-09-05
forum: Security
---

### Post by wacky_sung on 2010-09-05
I just ponder that is it possible to create a SSH server and tunnel it through locally through my local proxy servers?If so, does it mean all my connections are encrypted?Beside that,how can i point my SSH server to forward it to my proxy?Thank.

---

### Post by Joe of loath on 2010-09-05
SSH server is purely a listening process. To get through the firewall you must open a port for it.

---

### Post by BkkBonanza on 2010-09-05
You're question is confused. 

SSH can be used as a proxy. And it can be used as a tunnel.
Whether you can run ssh through your current proxy depends on what kind of proxy it is.
If it's a simple http proxy then, no.
If it's a socks proxy then, yes.

SSH can be used to bypass firewalls, and it can be used in a reverse tunnel config that allows a local service to listen from outside your firewall.

But there's no point in proxying ssh through an existing proxy, unless you need to do a proxy chain. But what you described doesn't sound like that. Just use ssh as your proxy and don't bother with the other one.

Or explain more clearly what your goal is.

---

### Post by HermanAB on 2010-09-05
To answer the actual question: Yes it can.

For example, you can use corkscrew to tunnel through some darned thing and bind to a local port say 1234, then connect through it  with SSH using the home address 127.0.0.1 and port 1234.

---

### Post by wacky_sung on 2010-09-06
Currently i have configure my ubuntu system to run through a chain of servers.Below are my current configuration which run through.

[HAVP]("http://manpages.ubuntu.com/manpages/gutsy/man1/havp.1.html")->[Privoxy]("http://www.privoxy.org/")->[Polipo]("http://www.pps.jussieu.fr/~jch/software/polipo/")

or

[Dansguardian]("https://help.ubuntu.com/community/Servers/DansGuardian")->HAVP->Privoxy->Polipo


What i want the setting to be as 

SSH -> HAPV->Privoxy->Polipo

Is that possible to run it through this way?

Beside that,do i require to install SSH server to run along with corkscrew.

---

### Post by BkkBonanza on 2010-09-06
Once ssh encrypts the data the other proxies cannot manipulate the data because they cannot read it. The only way you could do this is the other way round. Run it through the others and then last hop into ssh out the tunnel to the other end.

HAVP->Privoxy->Polipo->SSH

On the browser end you just need ssh.
On the far end where ssh sends the data you need sshd.

Well you could put the chain on the other end where sshd receives the data. In that case ssh would be first, but the data would be decrypted before going into the chain. It probably makes more sense to have Polipo at the browser end though.

So you end up like this,

HAVP->Privoxy->Polipo->SSH - - - - >SSHD->Internet

or 

Polipo->SSH - - - ->SSHD->HAVP->Privoxy->Internet

But in the ssh link the data is secured/unreadable.

---

### Post by wacky_sung on 2010-09-06
> **BkkBonaza said:**
> Once ssh encrypts the data the other proxies cannot manipulate the data because they cannot read it. The only way you could do this is the other way round. Run it through the others and then last hop into ssh out the tunnel to the other end.

HAVP->Privoxy->Polipo->SSH

On the browser end you just need ssh.
On the far end where ssh sends the data you need sshd.

Well you could put the chain on the other end where sshd receives the data. In that case ssh would be first, but the data would be decrypted before going into the chain. It probably makes more sense to have Polipo at the browser end though.

So you end up like this,

HAVP->Privoxy->Polipo->SSH - - - - >SSHD->Internet

or 

Polipo->SSH - - - ->SSHD->HAVP->Privoxy->Internet

But in the ssh link the data is secured/unreadable.

HAVP->Privoxy->Polipo->SSH - - - - >SSHD->Internet

Does it mean my connection will be secured from my side to the internet even the webpage is not encrypted?Otherwise it only work from my connection to the webpage server get the encryption.

---

### Post by BkkBonanza on 2010-09-06
The bold part of this diagram is the encrypted tunnel...

HAVP->Privoxy->Polipo->**SSH - - Internet - - >SSHD**->Internet

---

### Post by wacky_sung on 2010-09-06
> **BkkBonaza said:**
> The bold part of this diagram is the encrypted tunnel...

HAVP->Privoxy->Polipo->**SSH - - Internet - - >SSHD**->Internet

Much appreciated for your clarification.I bet SSHD come along only by installing a openssh server.

---

### Post by BkkBonanza on 2010-09-06
Yes, SSHD is openssh-server.

**sudo apt-get install openssh-server**

BTW It makes more sense this way, I think,

Polipo->HAVP->Privoxy->SSH - - Internet - - >SSHD->Internet

because then the web cache stores the content already fixed up. Which I would think cuts down on work done by the other two proxies. But I could be wrong having never chained them like that.

---

### Post by wacky_sung on 2010-09-06
> **BkkBonaza said:**
> Yes, SSHD is openssh-server.

**sudo apt-get install openssh-server**

BTW It makes more sense this way, I think,

Polipo->HAVP->Privoxy->SSH - - Internet - - >SSHD->Internet

because then the web cache stores the content already fixed up. Which I would think cuts down on work done by the other two proxies. But I could be wrong having never chained them like that.

Now i face the problem of getting 
Privoxy->SSH

How shall i configure privoxy to connect to SSH?

  &

How shall i get the browser setting to listen to SSHD?
SSHD->Internet

---

### Post by BkkBonanza on 2010-09-06
Ummm. The browser should be on the left,

[COLOR="Green"]Browser->Polipo->HAVP->Privoxy->SSH[/COLOR] - - Internet - - >[COLOR="Red"]SSHD->[/COLOR]Internet

The browser accesses the internet via all these proxies...

The green programs run on your client with the browser, the red ones on your server where the http requests go out on the net.

You don't have to do anything at the [COLOR="Red"]sshd[/COLOR] side except make sure it's listening.

At the [COLOR="Green"]ssh[/COLOR] side you need to run a command to start ssh as a proxy for you. Then point privoxy at the proxy port. 

If this makes sense then I'll post the command you need. If not, then let me know.

---

### Post by BkkBonanza on 2010-09-06
I was just reading the Polipo docs. They suggest it should come after Privoxy.
So that order should be changed. I don't know if that's the best order but that's what they say. Privoxy->Polipo and stick HAVP in somewhere...

---

### Post by wacky_sung on 2010-09-07
> **BkkBonaza said:**
> I was just reading the Polipo docs. They suggest it should come after Privoxy.
So that order should be changed. I don't know if that's the best order but that's what they say. Privoxy->Polipo and stick HAVP in somewhere...

Can you give me the command as default of what i initially want it.

HAVP->Privoxy->Polipo->SSH - - - - >SSHD->Internet

Thank.

---

### Post by BkkBonanza on 2010-09-07
To start ssh as a SOCKS proxy you can use,

**ssh -fND 8080  user@server**
(you can change 8080 to whatever you like)

This places ssh running in the background much like your other proxies and it will listen on port 8080 where it will encrypt and tunnel the data over to your server. Then sshd decrypts it and sends it out.

Since Polipo is just before ssh you will want to configure Polipo with,

**socksParentProxy=localhost:8080**

So it's data is handed off to ssh.

To stop ssh after you can use **pkill ssh** 
(this kills all running ssh processes)

---

### Post by wacky_sung on 2010-09-08
Thank for help,BkkBonaza.The issue is that it still not working as i have changed my SSH port to 2222.Beside that, i have allow my username and still getting no way as the server meant to be local.

Try to get the command as below but failed.

ssh -v localhost:2222

---

### Post by BkkBonanza on 2010-09-08
For the port 2222 that's not a problem, just add the port to the command. 

ssh -p 2222 -fND 8080 user@server

The proxy runs on localhost:8080 - so that is where your other proxy needs to connect.

I don't really understand your meaning: "still getting no way as the server meant to be local."

You can read the ssh docs and solve things like this much faster than asking me, **man ssh**.

---

### Post by Yahwek on 2010-09-08
> **BkkBonaza said:**
> For the port 2222 that's not a problem, just add the port to the command. 

ssh -p 2222 -fND 8080 user@server

The proxy runs on localhost:8080 - so that is where your other proxy needs to connect.

I don't really understand your meaning: "still getting no way as the server meant to be local."

You can read the ssh docs and solve things like this much faster than asking me, **man ssh**.

Hello "Man SSH"
You can help me?
How do I connect me to a Game (port 7171) using ssh/tunnel (proxy)?
E.g.: client (me) > Proxy (tunnel) > server port 7171

Thanks

---

